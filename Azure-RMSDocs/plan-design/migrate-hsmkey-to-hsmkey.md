---
title: "Krok 2&colon; Migracja klucza chronionego przez moduł HSM do klucza chronionego przez moduł HSM | Azure RMS"
description: 
keywords: 
author: cabailey
manager: mbaldwin
ms.date: 04/28/2016
ms.topic: article
ms.prod: azure
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: c5bbf37e-f1bf-4010-a60f-37177c9e9b39
ms.reviewer: esaggese
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 7a9c8b531ec342e7d5daf0cbcacd6597a79e6a55
ms.openlocfilehash: 7b531ebba1923653cb37c70a02fa888a40e96528


---

# Krok 2. Migracja klucza chronionego przez moduł HSM do klucza chronionego przez moduł HSM

*Dotyczy usług: Active Directory Rights Management Services, Azure Rights Management*


Te instrukcje są częścią [ścieżki migracji z usług AD RMS do usługi Azure Rights Management](migrate-from-ad-rms-to-azure-rms.md) oraz są stosowane tylko wtedy, gdy klucz usług AD RMS jest chroniony przez moduł HSM, a użytkownik chce migrować klucz do usługi Azure Rights Management z wykorzystaniem klucza dzierżawy chronionego przez moduł HSM. 

Jeśli nie jest to wybrany scenariusz konfiguracji, wróć do [Kroku 2. Eksportowanie danych konfiguracji z usług AD RMS i importowanie ich do usługi Azure RMS](migrate-from-ad-rms-phase1.md#step-2-export-configuration-data-from-ad-rms-and-import-it-to-azure-rms) i wybierz inną konfigurację.

> [!NOTE]
> W tych instrukcjach przyjęto założenie, że klucz usługi AD RMS jest chroniony przez moduł. Jest to sytuacja często spotykana. Jeśli klucz usług AD RMS jest chroniony przez moduł OCS, wyślij wiadomość e-mail na adres [AskIPTeam@microsoft.com](mailto: askipteam@microsoft.com?subject=AD%20RMS%20migration%20with%20OCS-protected%20key) przed wykonaniem tych instrukcji.

Jest to składająca się z dwóch części procedura, która umożliwia zaimportowanie klucza HSM i konfiguracji usług AD RMS do usługi Azure RMS i zastosowanie w ten sposób klucza dzierżawy usługi Azure RMS zarządzanego przez użytkownika (BYOK).

Najpierw należy utworzyć pakiet klucza HSM gotowy do przeniesienia do usługi Azure RMS, a następnie importować go razem z danymi konfiguracji.

## Część 1. Tworzenie pakietu klucza HSM gotowego do przeniesienia do usługi Azure RMS

1.  Postępuj zgodnie z instrukcjami w sekcji dotyczącej [wdrażania scenariusza BYOK („użyj własnego klucza”)](plan-implement-tenant-key.md#implementing-your-azure-rights-management-tenant-key) w temacie [Planowanie i wdrażanie klucza dzierżawy usługi Azure Rights Management](plan-implement-tenant-key.md). Wykonaj kroki procedury **Generowanie i przenoszenie klucza dzierżawy — przez Internet** z następującymi wyjątkami:

    -   Nie wykonuj kroków procedury **Generowanie klucza dzierżawy**, ponieważ istnieje już jego odpowiednik pochodzący z wdrożenia usług AD RMS. Zidentyfikuj klucz używany na serwerze usług AD RMS z instalacji firmy Thales i użyj go podczas migracji. Zaszyfrowane pliki klucza firmy Thales mają przeważnie nazwę **key_(keyAppName)_(keyIdentifier)** i są przechowywane lokalnie na serwerze.

    -   Nie wykonuj kroków procedury **Przenoszenie klucza dzierżawy do usługi Azure RMS**, w ramach której jest używane polecenie Add-AadrmKey.  Zamiast tego przenieś przygotowany klucz HSM podczas przekazywania wyeksportowanej zaufanej domeny publikacji przy użyciu polecenia Import-AadrmTpd.

2.  Na połączonej z Internetem stacji roboczej w sesji programu Windows PowerShell ponownie nawiąż połączenie z usługą Azure RMS.

Teraz klucz HSM jest już gotowy do użycia w usłudze Azure RMS, a Ty możesz importować plik klucza HSM i dane konfiguracji usług AD RMS.

## Część 2. Importowanie klucza HSM i danych konfiguracji do usługi Azure RMS

1.  Pracując nadal na stacji roboczej połączonej z Internetem i w sesji programu Windows PowerShell, przekaż pierwszy wyeksportowany plik (XML) zaufanej domeny publikacji. Jeśli masz więcej niż jeden plik XML z powodu użycia wielu zaufanych domen publikacji, wybierz plik zawierający wyeksportowaną zaufaną domenę publikacji odpowiadającą kluczowi HSM, który chcesz zastosować w usłudze Azure RMS do ochrony zawartości po migracji. Użyj następującego polecenia:

    ```
    Import-AadrmTpd -TpdFile <PathToTpdPackageFile> -ProtectionPassword -HsmKeyFile <PathToBYOKPackage> -Active $True -Verbose
    ```
    Na przykład: **Import -TpdFile E:\no_key_tpd_contosokey1.xml  -HsmKeyFile E:\KeyTransferPackage-contosokey.byok -ProtectionPassword -Active $true -Verbose**

    Po wyświetleniu monitu wprowadź określone wcześniej hasło i potwierdź, że chcesz wykonać tę akcję.

2.  Po zakończeniu wykonywania polecenia powtórz krok 1 dla każdego z pozostałych plików XML, który został utworzony przez wyeksportowanie zaufanej domeny publikacji. Dla tych plików ustaw opcję **-Active** na wartość **false** podczas uruchamiania polecenia Import.  Na przykład: **Import -TpdFile E:\contosokey2.xml -HsmKeyFile E:\KeyTransferPackage-contosokey.byok -ProtectionPassword -Active $false -Verbose**

3.  Użyj polecenia cmdlet [Disconnect-AadrmService](http://msdn.microsoft.com/library/windowsazure/dn629416.aspx), aby zakończyć połączenie z usługą Azure RMS:

    ```
    Disconnect-AadrmService
    ```

Teraz możesz wykonać [Krok 3. Aktywowanie dzierżawy usługi RMS](migrate-from-ad-rms-phase1.md#step-3-activate-your-rms-tenant).




<!--HONumber=Jun16_HO4-->


