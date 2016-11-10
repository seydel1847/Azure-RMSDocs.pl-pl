---
title: "Krok 2&colon; Migracja klucza chronionego przez oprogramowanie do klucza chronionego przez moduł HSM | Azure Information Protection"
description: "Instrukcje będące częścią ścieżki migracji z usługi AD RMS do usługi Azure Information Protection, stosowane tylko wtedy, gdy klucz usługi AD RMS jest chroniony przez oprogramowanie, a użytkownik chce migrować klucz do usługi Azure Information Protection z wykorzystaniem klucza dzierżawy chronionego przez moduł HSM w usłudze Azure Key Vault."
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 11/03/2016
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: c5f4c6ea-fd2a-423a-9fcb-07671b3c2f4f
ms.reviewer: esaggese
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 1fcebaaa2fbe1479e83c232d51013341977796fc
ms.openlocfilehash: 54e759108ecca7a049190823c3874451d7104fc4


---

# <a name="step-2-softwareprotected-key-to-hsmprotected-key-migration"></a>Krok 2. Migracja klucza chronionego przez oprogramowanie do klucza chronionego przez moduł HSM

>*Dotyczy: Active Directory Rights Management Services, Azure Information Protection*


Są to instrukcje będące częścią [ścieżki migracji z usługi AD RMS do usługi Azure Information Protection](migrate-from-ad-rms-to-azure-rms.md) i są stosowane tylko wtedy, gdy klucz usługi AD RMS jest chroniony przez oprogramowanie, a użytkownik chce migrować klucz do usługi Azure Information Protection z wykorzystaniem klucza dzierżawy chronionego przez moduł HSM w usłudze Azure Key Vault. 

Jeśli nie jest to wybrany scenariusz konfiguracji, wróć do [Kroku 2. Eksportowanie danych konfiguracji z usługi AD RMS i importowanie ich do usługi Azure RMS](migrate-from-ad-rms-phase1.md#step-2-export-configuration-data-from-ad-rms-and-import-it-to-azure-information-protection) i wybierz inną konfigurację.

Jest to składająca się z czterech części procedura, która umożliwia zaimportowanie konfiguracji usługi AD RMS do usługi Azure Information Protection i zastosowanie w ten sposób zarządzanego przez Ciebie klucza dzierżawy usługi Azure Information Protection w usłudze Azure Key Vault.

Należy najpierw wyodrębnić klucz certyfikatu licencjodawcy serwera (SLC, Server Licensor Certificate) z danych konfiguracji usługi AD RMS i przenieść klucz do lokalnego modułu HSM firmy Thales, następnie spakować klucz HSM i przenieść go do usługi Azure Key Vault, autoryzować usługi Azure Rights Management z usługi Azure Information Protection do dostępu do magazynu kluczy, a na koniec zaimportować dane konfiguracji.

Ponieważ klucz dzierżawy usługi Azure Information Protection będzie przechowywany i zarządzany przez usługę Azure Key Vault, ta część migracji wymaga administracji w usłudze Azure Key Vault poza administracją w usłudze Azure Information Protection. Jeśli usługa Azure Key Vault jest zarządzana przez innego administratora w Twojej organizacji, musisz skoordynować pracę z tym administratorem, aby zakończyć procedurę.

Przed rozpoczęciem upewnij się, że Twoja organizacja ma magazyn kluczy utworzony w usłudze Azure Key Vault oraz że obsługuje klucze chronione przez moduł HSM. Chociaż nie jest to wymagane, zaleca się posiadanie dedykowanego magazynu kluczy dla usługi Azure Information Protection. Ten magazyn kluczy zostanie skonfigurowany tak, aby usługa Azure Rights Management z usługi Azure Information Protection mogła uzyskać do niego dostęp, dlatego klucze przechowywane w tym magazynie kluczy powinny być ograniczone wyłącznie do kluczy usługi Azure Information Protection.


> [!TIP]
> Jeśli chcesz przeprowadzić konfigurację usługi Azure Key Vault, a nie masz doświadczenia z tą usługą platformy Azure, przydatne może okazać się przeczytanie artykułu [Wprowadzenie do usługi Azure Key Vault](https://azure.microsoft.com/documentation/articles/key-vault-get-started/). 


## <a name="part-1-extract-your-slc-key-from-the-configuration-data-and-import-the-key-to-your-onpremises-hsm"></a>Część 1. Wyodrębnianie klucza SLC z danych konfiguracji i importowanie klucza do lokalnego modułu HSM

1.  Administrator usługi Azure Key Vault: użyj następujących kroków w sekcji [Implementowanie funkcji BYOK dla usługi Azure Key Vault](https://azure.microsoft.com/documentation/articles/key-vault-hsm-protected-keys/#implementing-bring-your-own-key-byok-for-azure-key-vault) w dokumentacji usługi Azure Key Vault:

    -   **Generowanie i przenoszenie klucza do modułu HSM usługi Azure Key Vault**: Krok 1. [Przygotowanie stacji roboczej połączonej z Internetem](https://azure.microsoft.com/documentation/articles/key-vault-hsm-protected-keys/#step-1-prepare-your-internet-connected-workstation)

    -   **Generowanie i przenoszenie klucza dzierżawy — przez Internet**: Krok 2. [Przygotowanie rozłączonej stacji roboczej](https://azure.microsoft.com/documentation/articles/key-vault-hsm-protected-keys/#step-2-prepare-your-disconnected-workstation)

    Nie wykonuj kroków procedury generowania klucza dzierżawy, ponieważ jego odpowiednik już istnieje w wyeksportowanym pliku (XML) danych konfiguracji. Zamiast tego uruchom narzędzie, aby wyodrębnić ten klucz z pliku i zaimportować go do lokalnego modułu HSM. Po uruchomieniu narzędzie utworzy dwa pliki:

    - Nowy plik danych konfiguracji bez klucza, który jest gotowy do zaimportowania do dzierżawy usługi Azure Information Protection.

    - Plik PEM (kontener klucza) z kluczem, który jest gotowy do zaimportowania do lokalnego modułu HSM.

2. Administrator usługi Azure Information Protection lub administrator usługi Azure Key Vault: na rozłączonej stacji roboczej uruchom narzędzie TpdUtil z [zestawu narzędzi do migracji usługi Azure RMS](https://go.microsoft.com/fwlink/?LinkId=524619). Jeśli na przykład narzędzie jest zainstalowane na dysku E, na który skopiowano plik danych konfiguracji o nazwie ContosoTPD.xml:

    ```
        E:\TpdUtil.exe /tpd:ContosoTPD.xml /otpd:ContosoTPD.xml /opem:ContosoTPD.pem
    ```

    Jeśli masz więcej niż jeden plik danych konfiguracji usługi RMS, uruchom to narzędzie dla pozostałych plików.

    Aby wyświetlić pomoc dla tego narzędzia, która zawiera opis, użycie i przykłady, uruchom plik TpdUtil.exe bez żadnych parametrów

    Dodatkowe informacje dotyczące tego polecenia:

    - **/tpd**: określa pełną ścieżkę i nazwę wyeksportowanego pliku danych konfiguracji usługi AD RMS. Pełna nazwa parametru to **TpdFilePath**.

    - **/otpd**: określa nazwę pliku wyjściowego dla pliku danych konfiguracji bez klucza. Pełna nazwa parametru to **OutPfxFile**. Jeśli ten parametr nie zostanie określony, plik wyjściowy zostanie nazwany domyślnie tak jak oryginalny plik z sufiksem **_keyless** i będzie przechowany w bieżącym folderze.

    - **/opem**: określa nazwę pliku wyjściowego dla pliku PEM, który zawiera wyodrębniony klucz. Pełna nazwa parametru to **OutPemFile**. Jeśli ten parametr nie zostanie określony, plik wyjściowy zostanie nazwany domyślnie tak jak oryginalny plik z sufiksem **_key** i będzie przechowany w bieżącym folderze.

    - Jeśli nie określisz hasła podczas wykonywania tego polecenia (przy użyciu pełnej nazwy parametru **TpdPassword** lub krótkiej nazwy parametru **pwd**), zostanie wyświetlony monit o określenie hasła.

3. Na tej samej rozłączonej stacji roboczej dołącz i skonfiguruj moduł HSM firmy Thales zgodnie z dokumentacją firmy Thales. Teraz możesz zaimportować klucz do dołączonego modułu HSM firmy Thales, korzystając z następującego polecenia, w którym musisz zastąpić nazwę pliku ContosoTPD.pem nazwą własnego pliku:

        generatekey --import simple pemreadfile=e:\ContosoTPD.pem plainname=ContosoBYOK protect=module ident=contosobyok type=RSA

    > [!NOTE]
    >Jeśli masz więcej niż jeden plik, wybierz plik, który odpowiada kluczowi HSM, którego chcesz użyć w usłudze Azure RMS na potrzeby ochrony zawartości po migracji.

    Zostanie wygenerowany ekran danych wyjściowych podobny do następującego:

    **parametry generowania klucza:**

    **operation &nbsp;&nbsp;&nbsp;&nbsp;&nbsp; Operacja do wykonania &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; importowanie**

    **application &nbsp;&nbsp;&nbsp;&nbsp;Aplikacja&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; prosta**

    **verify &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; Weryfikacja zabezpieczeń klucza konfiguracji &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; tak**

    **type &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; Typ klucza &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; RSA**

    **pemreadfile &nbsp;&nbsp; Plik PEM zawierający klucz RSA &nbsp;&nbsp; e:\ContosoTPD.pem**

    **ident &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; Identyfikator klucza &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; contosobyok**

    **plainname &nbsp;&nbsp;&nbsp;&nbsp;&nbsp; Nazwa klucza &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; ContosoBYOK**

    **Klucz zaimportowany pomyślnie.**

    **Ścieżka do klucza: C:\ProgramData\nCipher\Key Management Data\local\key_simple_contosobyok**

Te dane wyjściowe potwierdzają migrację klucza prywatnego do lokalnego urządzenia HSM firmy Thales z zaszyfrowaną kopią zapisaną w kluczu (w tym przykładzie „key_simple_contosobyok”). 

Teraz, skoro klucz SLC został wyodrębniony i zaimportowany do lokalnego modułu HSM, możesz spakować klucz chroniony przez moduł HSM i przenieść go do usługi Azure Key Vault.

> [!IMPORTANT]
> Po wykonaniu tego kroku usuń te pliki PEM z rozłączonej stacji roboczej, aby upewnić się, że nie będą dostępne dla nieautoryzowanych osób. Przykładowo uruchom polecenie „cipher /w:E”, aby bezpiecznie usunąć wszystkie pliki z dysku E:.

## <a name="part-2-package-and-transfer-your-hsm-key-to-azure-key-vault"></a>Część 2. Tworzenie pakietu klucza HSM i przenoszenie go do usługi Azure Key Vault

1.  Administrator usługi Azure Key Vault: wykonaj następujące kroki z sekcji [Implementowanie funkcji BYOK dla usługi Azure Key Vault](https://azure.microsoft.com/documentation/articles/key-vault-hsm-protected-keys/#implementing-bring-your-own-key-byok-for-azure-key-vault) w dokumentacji usługi Azure Key Vault:

    -   [Krok 4. Przygotowanie klucza do przesłania](https://azure.microsoft.com/documentation/articles/key-vault-hsm-protected-keys/#step-4-prepare-your-key-for-transfer)

    -   [Krok 5. Przesłanie klucza do usługi Azure Key Vault](https://azure.microsoft.com/documentation/articles/key-vault-hsm-protected-keys/#step-5-transfer-your-key-to-azure-key-vault)

    Nie wykonuj kroków służących do generowania pary klucza, ponieważ masz już klucz. Zamiast tego uruchom polecenie, aby przesłać ten klucz (w tym przykładzie parametr KeyIdentifier używa nazwy „contosobyok”) z lokalnego modułu HSM.

    Przed przeniesieniem klucza do usługi Azure Key Vault upewnij się, że narzędzie KeyTransferRemote.exe zwraca wartość **Result: SUCCESS** (Wynik: POWODZENIE), gdy tworzysz kopię klucza ze zmniejszonymi uprawnieniami (krok 4.1) i gdy szyfrujesz klucz (krok 4.3).

    Gdy klucz zostanie przekazany do usługi Azure Key Vault, zostaną wyświetlone właściwości klucza zawierające identyfikator klucza. Identyfikator będzie wyglądać podobnie do następującego: **https://contosorms-kv.vault.azure.net/keys/contosorms-byok/aaaabbbbcccc111122223333**. Zanotuj ten adres URL, ponieważ administrator usługi Azure Information Protection będzie go potrzebować, aby skonfigurować usługę Azure Rights Management z usługi Azure Information Protection do użycia tego klucza jako klucza dzierżawy.

    Teraz klucz HSM jest już przesłany z modułu HSM do usługi Azure Key Vault, a Ty możesz importować dane konfiguracji usługi AD RMS.

## <a name="part-3-import-the-configuration-data-to-azure-information-protection"></a>Część 3. Importowanie danych konfiguracji do usługi Azure Information Protection

1.  Administrator usługi Azure Information Protection: na stacji roboczej podłączonej do Internetu i w sesji programu PowerShell skopiuj nowe pliki danych konfiguracji (xml), z których usunięto klucz SLC po uruchomieniu narzędzia TpdUtil.

2. Przekaż pierwszy plik XML za pomocą polecenia cmdlet [Import-AadrmTpd](https://msdn.microsoft.com/library/dn857523.aspx). Jeśli masz więcej niż jeden taki plik z powodu użycia wielu zaufanych domen publikacji, wybierz plik odpowiadający kluczowi HSM, który chcesz zastosować w usłudze Azure Information Protection do ochrony zawartości po migracji.

    Aby uruchomić to polecenie cmdlet, wymagany jest adres URL dla klucza zidentyfikowany w poprzednim kroku.

    Przykładowo, używając naszej wartości adresu URL klucza z poprzedniego kroku i pliku danych konfiguracji C:\contoso_keyless.xml, należy uruchomić następujące polecenie:

    ```
    Import-AadrmTpd -TpdFile "C:\contoso_keyless.xml" -ProtectionPassword –KeyVaultStringUrl https://contoso-byok-kv.vault.azure.net/keys/contosorms-byok/aaaabbbbcccc111122223333 -Active $True -Verbose
    ```

    Po wyświetleniu monitu wprowadź określone wcześniej hasło dla pliku danych konfiguracji i potwierdź, że chcesz wykonać tę akcję.

    Jeśli masz więcej niż jeden plik danych konfiguracji, powtórz to polecenie dla pozostałych plików. Dla tych plików ustaw opcję **-Active** na wartość **false** podczas uruchamiania polecenia Import.



3.  Użyj polecenia cmdlet [Disconnect-AadrmService](https://msdn.microsoft.com/library/azure/dn629416.aspx), aby zakończyć połączenie z usługą Azure Rights Management:

    ```
    Disconnect-AadrmService
    ```

    > [!NOTE]
    > Jeśli chcesz później potwierdzić, którego klucza używa Twój klucz dzierżawy usługi Azure Rights Management w usłudze Azure Key Vault, użyj polecenia cmdlet usługi Azure RMS [Get-AadrmKeys](https://msdn.microsoft.com/library/dn629420.aspx).


Teraz możesz wykonać [Krok 3. Aktywowanie dzierżawy usługi Azure Information Protection](migrate-from-ad-rms-phase1.md#step-3-activate-your-azure-information-protection-tenant).






<!--HONumber=Nov16_HO1-->


