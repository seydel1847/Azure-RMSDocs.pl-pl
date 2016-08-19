---
title: "Krok 2&colon; Migracja klucza chronionego przez oprogramowanie do klucza chronionego przez moduł HSM | Azure RMS"
description: 
keywords: 
author: cabailey
manager: mbaldwin
ms.date: 04/28/2016
ms.topic: article
ms.prod: azure
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: c5f4c6ea-fd2a-423a-9fcb-07671b3c2f4f
ms.reviewer: esaggese
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 7a9c8b531ec342e7d5daf0cbcacd6597a79e6a55
ms.openlocfilehash: 173641b9dada2673b48a1c210419cb933cdd9f13


---

# Krok 2. Migracja klucza chronionego przez oprogramowanie do klucza chronionego przez moduł HSM

*Dotyczy usług: Active Directory Rights Management Services, Azure Rights Management*


Te instrukcje są częścią [ścieżki migracji z usług AD RMS do usługi Azure Rights Management](migrate-from-ad-rms-to-azure-rms.md) oraz są stosowane tylko wtedy, gdy klucz usług AD RMS jest chroniony przez oprogramowanie, a użytkownik chce migrować klucz do usługi Azure Rights Management z wykorzystaniem klucza dzierżawy chronionego przez moduł HSM. 

Jeśli nie jest to wybrany scenariusz konfiguracji, wróć do [Kroku 2. Eksportowanie danych konfiguracji z usług AD RMS i importowanie ich do usługi Azure RMS](migrate-from-ad-rms-phase1.md#step-2-export-configuration-data-from-ad-rms-and-import-it-to-azure-rms) i wybierz inną konfigurację.

Jest to składająca się z trzech części procedura, która umożliwia importowanie konfiguracji usług AD RMS do usługi Azure RMS i zastosowanie w ten sposób klucza dzierżawy usługi Azure RMS zarządzanego przez użytkownika (BYOK).

Należy najpierw wyodrębnić klucz certyfikatu licencjodawcy serwera (SLC) z danych konfiguracji i przenieść klucz do lokalnego modułu HSM firmy Thales, następnie spakować klucz HSM i przenieść go do usługi Azure RMS, a na koniec importować dane konfiguracji.

## Część 1. Wyodrębnianie certyfikatu SLC z danych konfiguracji i importowanie klucza do lokalnego modułu HSM

1.  Postępuj zgodnie z instrukcjami w sekcji dotyczącej [wdrażania scenariusza BYOK („użyj własnego klucza”)](plan-implement-tenant-key.md#implementing-your-azure-rights-management-tenant-key) w temacie [Planowanie i wdrażanie klucza dzierżawy usługi Azure Rights Management](plan-implement-tenant-key.md). Wykonaj kroki procedury **Generowanie i przenoszenie klucza dzierżawy — przez Internet** z następującymi wyjątkami:

    -   **Generowanie i przenoszenie klucza dzierżawy — przez Internet**: **przygotowanie stacji roboczej połączonej z Internetem**

    -   **Generowanie i przenoszenie klucza dzierżawy — przez Internet**: **przygotowanie rozłączonej stacji roboczej**

    Nie wykonuj kroków procedury generowania klucza dzierżawy, ponieważ jego odpowiednik już istnieje w wyeksportowanym pliku (XML) danych konfiguracji. Zamiast tego uruchom polecenie, aby wyodrębnić ten klucz z pliku i zaimportować go do lokalnego modułu HSM.

2.  Na rozłączonej stacji roboczej uruchom następujące polecenie:

    ```
    KeyTransferRemote.exe -ImportRmsCentrallyManagedKey -TpdFilePath <TPD> -ProtectionPassword -KeyIdentifier <KeyID> -ExchangeKeyPackage <BYOK-KEK-pka-Region> -NewSecurityWorldPackage <BYOK-SecurityWorld-pkg-Region>
    ```
    Na przykład dla Ameryki Północnej: **KeyTransferRemote.exe -ImportRmsCentrallyManagedKey -TpdFilePath E:\contosokey1.xml -ProtectionPassword -KeyIdentifier contosorms1key –- -ExchangeKeyPackage &lt;BYOK-KEK-pka-NA-1&gt; -NewSecurityWorldPackage &lt;BYOK-SecurityWorld-pkg-NA-1&gt;**

    Informacje dodatkowe:

    -   Parametr ImportRmsCentrallyManagedKey wskazuje, że celem operacji jest zaimportowanie klucza SLC.

    -   Jeśli w poleceniu nie zostanie określone hasło, pojawi się monit o jego określenie.

    -   Parametr KeyIdentifier jest przyjazną nazwą klucza, która służy do tworzenia nazwy pliku klucza. Można używać tylko małych liter należących do zestawu znaków ASCII.

    -   Parametr ExchangeKeyPackage określa przeznaczony dla konkretnego regionu pakiet klucza wymiany klucza (KEK) o nazwie rozpoczynającej od BYOK-KEK-pkg-.

    -   Parametr NewSecurityWorldPackage określa przeznaczony dla określonego regionu globalny pakiet zabezpieczeń o nazwie rozpoczynającej się od BYOK-SecurityWorld-pkg-.

    Wyniki użycia tego polecenia będą następujące:

    -   Plik klucza HSM: %NFAST_KMDATA%\local\key_mscapi_&lt;KeyID&gt;

    -   Plik danych konfiguracji usługi RMS z usuniętym certyfikatem SLC: %NFAST_KMDATA%\local\no_key_tpd_&lt;KeyID&gt;.xml

3.  Jeśli masz więcej niż jeden plik danych konfiguracji usługi RMS, powtórz krok 2 dla pozostałych plików.

Teraz po wyodrębnieniu certyfikatu SLC i przekształceniu go w klucz oparty na module HSM możesz przystąpić do tworzenia pakietu tego klucza i przenoszenia go do usługi Azure RMS.

## Część 2. Tworzenie pakietu klucza HSM i przenoszenie go do usługi Azure RMS

1.  Wykonaj kroki opisane w sekcji dotyczącej [wdrażania scenariusza BYOK („użyj własnego klucza”)](plan-implement-tenant-key.md#implementing-your-azure-rights-management-tenant-key) w temacie [Planowanie i wdrażanie klucza dzierżawy usługi Azure Rights Management](plan-implement-tenant-key.md):

    -   **Generowanie i przenoszenie klucza dzierżawy — przez Internet**: **przygotowanie klucza dzierżawy do transferu**

    -   **Generowanie i przenoszenie klucza dzierżawy — przez Internet**: **przenoszenie klucza dzierżawy do usługi Azure RMS**

Po przeniesieniu klucza HSM do usługi Azure RMS możesz zaimportować dane konfiguracji usług AD RMS, które zawierają tylko wskaźnik do nowo transferowanego klucza dzierżawy.

## Część 3. Importowanie danych konfiguracji do usługi Azure RMS

1.  Pracując nadal na stacji roboczej połączonej z Internetem i w sesji programu Windows PowerShell, skopiuj pliki konfiguracji usługi RMS z usuniętym certyfikatem SLC (z rozłączonej stacji roboczej, %NFAST_KMDATA%\local\no_key_tpd_&lt;KeyID&gt;.xml)

2.  Przekaż pierwszy plik. Jeśli masz więcej niż jeden plik XML z powodu użycia wielu zaufanych domen publikacji, wybierz plik zawierający wyeksportowaną zaufaną domenę publikacji odpowiadającą kluczowi HSM, który chcesz zastosować w usłudze Azure RMS do ochrony zawartości po migracji. Użyj następującego polecenia:

    ```
    Import-AadrmTpd -TpdFile <PathToNoKeyTpdPackageFile> -ProtectionPassword -HsmKeyFile <PathToKeyTransferPackage> -Active $true -Verbose
    ```
    Na przykład: **Import -TpdFile E:\no_key_tpd_contosorms1key.xml -ProtectionPassword -HsmKeyFile E:\KeyTransferPackage-contosorms1key.byok -Active $true -Verbose**

    Po wyświetleniu monitu wprowadź określone wcześniej hasło i potwierdź, że chcesz wykonać tę akcję.

3.  Po zakończeniu wykonywania polecenia powtórz krok 2 dla każdego z pozostałych plików XML, które zostały utworzone przez wyeksportowanie zaufanej domeny publikacji. Dla tych plików ustaw opcję **-Active** na wartość **false** podczas uruchamiania polecenia Import. Na przykład: **Import -TpdFile E:\no_key_tpd_contosorms2key.xml -ProtectionPassword -HsmKeyFile E:\KeyTransferPackage-contosorms1key.byok -Active $false -Verbose**

4.  Użyj polecenia cmdlet [Disconnect-AadrmService](http://msdn.microsoft.com/library/windowsazure/dn629416.aspx), aby zakończyć połączenie z usługą Azure RMS:

    ```
    Disconnect-AadrmService
    ```

Teraz możesz wykonać [Krok 3. Aktywowanie dzierżawy usługi RMS](migrate-from-ad-rms-phase1.md#step-3-activate-your-rms-tenant).





<!--HONumber=Jun16_HO4-->


