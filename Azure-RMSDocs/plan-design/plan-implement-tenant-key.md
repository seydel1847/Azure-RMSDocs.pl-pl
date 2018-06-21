---
title: Klucz dzierżawy usługi Azure Information Protection
description: Informacje ułatwiające zaplanowanie użycia klucza dzierżawy usługi Azure Information Protection oraz zarządzanie nim. Domyślne ustawienie zakłada, że to firma Microsoft zarządza kluczem dzierżawy. Ustawienie to można zmienić, aby zarządzać własnym kluczem dzierżawy w celu zachowania zgodności z konkretnymi przepisami mającymi zastosowanie w danej organizacji. Samodzielne zarządzanie kluczem dzierżawy określa się także mianem strategii BYOK (Bring Your Own Key), czyli „Przynieś własny klucz”.
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 03/05/2018
ms.topic: article
ms.prod: ''
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: f0d33c5f-a6a6-44a1-bdec-5be1bc8e1e14
ms.reviewer: esaggese
ms.suite: ems
ms.openlocfilehash: 714d00036d263cc64e44b67b547d743ff4cbab4b
ms.sourcegitcommit: dbbfadc72f4005f81c9f28c515119bc3098201ce
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/28/2018
ms.locfileid: "30208655"
---
# <a name="planning-and-implementing-your-azure-information-protection-tenant-key"></a>Planowanie i wdrażanie klucza dzierżawy usługi Azure Information Protection

>*Dotyczy: [Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection), [usługi Office 365](http://download.microsoft.com/download/E/C/F/ECF42E71-4EC0-48FF-AA00-577AC14D5B5C/Azure_Information_Protection_licensing_datasheet_EN-US.pdf)*

Informacje zawarte w tym artykule ułatwiają zaplanowanie użycia klucza dzierżawy usługi Azure Information Protection oraz zarządzanie nim. Domyślne ustawienie zakłada, że to firma Microsoft zarządza kluczem dzierżawy. Ustawienie to można zmienić, aby zarządzać własnym kluczem dzierżawy w celu zachowania zgodności z konkretnymi przepisami mającymi zastosowanie w danej organizacji. Samodzielne zarządzanie kluczem dzierżawy określa się także mianem strategii BYOK (Bring Your Own Key), czyli „Przynieś własny klucz”.

Co to jest klucz dzierżawy usługi Azure Information Protection?

- Klucz dzierżawy usługi Azure Information Protection jest klucz główny dla Twojej organizacji. Inne klucze mogą pochodzić z tego klucza głównego, takie jak klucze użytkownika, kluczy komputera i kluczy szyfrowania dokumentu. Zawsze, gdy usługi Azure Information Protection używa tych kluczy w organizacji, szyfrowane połączenie użytego klucza dzierżawy usługi Azure Information Protection.

- Klucz dzierżawy usługi Azure Information Protection jest odpowiednikiem online klucza certyfikatu licencjodawcy serwera (SLC) z Active Directory Rights Management Services (AD RMS). 

**Krótki przegląd:** poniższa tabela pełni rolę przewodnika po zalecanych topologiach klucza dzierżawy. Więcej informacji można znaleźć w dodatkowej dokumentacji.

|Wymaganie biznesowe|Zalecana topologia klucza dzierżawy|
|------------------------|-----------------------------------|
|Wdrażanie usługi Azure Information Protection szybko i bez specjalnego sprzętu, oprogramowania dodatkowe lub subskrypcji platformy Azure.<br /><br />Na przykład: testowanie środowisk i gdy Twoja organizacja nie ma przepisami dotyczącymi zarządzania kluczami.|Klucz zarządzany przez firmę Microsoft|
|Przepisy dotyczące zgodności, dodatkowych zabezpieczeń i kontroli nad wszystkie operacje cyklu życia. <br /><br />Na przykład: klucz musi być chroniony przez sprzętowy moduł zabezpieczeń (HSM).|BYOK [[1]](#footnote-1)|


W razie potrzeby można zmienić topologię klucza dzierżawy po wdrożeniu, używając polecenia cmdlet [Set-AadrmKeyProperties](/powershell/module/aadrm/set-aadrmkeyproperties).


## <a name="choose-your-tenant-key-topology-managed-by-microsoft-the-default-or-managed-by-you-byok"></a>Wybierz topologię klucza dzierżawy: klucz zarządzany przez firmę Microsoft (ustawienie domyślne) lub klucz zarządzany przez użytkownika (BYOK)
Zdecyduj, która topologia klucza dzierżawy jest najodpowiedniejsza dla Twojej organizacji. Domyślnie usługa Azure Information Protection generuje klucz dzierżawy i zarządza większością aspektów cyklu jego życia. Jest to najprostsza opcja, która wiąże się z najmniejszą liczbą obowiązków administracyjnych użytkownika. W większości przypadków użytkownik nie musi nawet wiedzieć, że ma klucz dzierżawy. Wystarczy, że zarejestruje się w usłudze Azure Information Protection — resztą procesu zarządzania kluczem zajmie się firma Microsoft.

Zdecyduj, która topologia klucza dzierżawy jest najodpowiedniejsza dla Twojej organizacji:

- **Zarządzany przez firmę Microsoft**: Microsoft automatycznie generuje klucz dzierżawy dla Twojej organizacji i ten klucz służy wyłącznie do usługi Azure Information Protection. Domyślnie firma Microsoft używa tego klucza dzierżawy i zarządza większością aspektów cyklu życia klucza Twojej dzierżawy. 
    
    Jest to najprostsza opcja, która wiąże się z najmniejszą liczbą obowiązków administracyjnych użytkownika. W większości przypadków użytkownik nie musi nawet wiedzieć, że ma klucz dzierżawy. Wystarczy, że zarejestruje się w usłudze Azure Information Protection — resztą procesu zarządzania kluczem zajmie się firma Microsoft.

- **Zarządzany przez użytkownika (BYOK)**: pełną kontrolę nad kluczem dzierżawy, można użyć [usługi Azure Key Vault](https://azure.microsoft.com/services/key-vault/) z usługi Azure Information Protection. Dla tej topologii klucza dzierżawy tworzenia klucza, bezpośrednio w magazynie kluczy, lub utworzyć ją lokalnie. Jeśli ją utworzyć w infrastrukturze lokalnej, następnego przeniesienia lub zaimportować ten klucz do magazynu kluczy. Następnie skonfiguruj usługi Azure Information Protection, aby użyć tego klucza i nim zarządzać w usłudze Azure Key Vault.
    

### <a name="more-information-about-byok"></a>Więcej informacji na temat funkcji BYOK
Aby utworzyć własny klucz, masz następujące opcje:

- **Klucz, możesz utworzyć lokalną i przenieść lub zaimportować do magazynu kluczy**:
    
    - Klucza chronionego przez tworzenie lokalnych, a następnie przenieść do magazynu kluczy jako klucza chronionego przez moduł HSM.
    
    - Klucza chronionego przez oprogramowanie, utworzyć w infrastrukturze lokalnej, przekonwertować, a następnie przenieść magazyn kluczy jako klucza chronionego przez moduł HSM. Ta opcja jest obsługiwana tylko wtedy, gdy użytkownik [migracji z Active Directory Rights Management Services (AD RMS)](migrate-from-ad-rms-to-azure-rms.md).
    
    - Klucza chronionego przez oprogramowanie tworzenia lokalnego, a następnie zaimportować do magazynu kluczy jako klucza chronionego przez oprogramowanie. Ta opcja wymaga. Plik certyfikatu PFX.
    
- **Klucz, który można utworzyć w Key Vault**:
    
    - Klucza chronionego przez moduł HSM utworzonego w magazynie kluczy.
    
    - Klucza chronionego przez oprogramowanie utworzyć w magazynie kluczy.

Z tych opcji BYOK najbardziej typowe jest klucza chronionego przez tworzenie lokalnych, a następnie przenieść do magazynu kluczy jako klucza chronionego przez moduł HSM. Mimo że ta opcja ma największy ogólne koszty administracyjne, może być wymagane dla Twojej organizacji w celu zachowania zgodności z konkretnymi przepisami. Moduły HSM, które są używane przez usługi Azure Key Vault są FIPS 140-2 poziom 2 zweryfikowany.

Po wybraniu tej opcji:

1. Klucz dzierżawy jest generowany lokalnie przez użytkownika w sposób zgodny z zasadami dotyczącymi infrastruktury IT i zasadami dotyczącymi zabezpieczeń obowiązującymi w organizacji. Ten klucz jest kopii głównej. Pozostaje lokalnie i za jego kopii zapasowej.

2. Utwórz kopię tego klucza, a następnie bezpiecznie przenieść tej kopii z modułu HSM do usługi Azure Key Vault. W trakcie tego procesu kopii głównej klucza nigdy nie przekracza granic zabezpieczeń sprzętowych.

3. Kopia klucza jest chroniona przez usługi Azure Key Vault.

> [!NOTE]

> Dodatkowym środkiem ochrony dostępnym w usłudze Azure Key Vault są wykorzystywane w jej ramach oddzielne domeny zabezpieczeń dla centrów danych w regionach, takich jak Ameryka Północna; Europa, Bliski Wschód i Afryka (EMEA) oraz Azja. Usługa Azure Key Vault używa również innych wystąpień programu Azure, takich jak Microsoft platformy Azure w Niemczech i Azure dla instytucji rządowych. 

Choć generowane niemalże w czasie rzeczywistym dzienniki z usługi Azure Information Protection są opcjonalne, warto z nich skorzystać, aby przekonać się, kiedy i w jaki sposób jest używany klucz dzierżawy.

### <a name="when-you-have-decided-your-tenant-key-topology"></a>Jeśli zdecydujesz się topologii klucza dzierżawy

Jeśli użytkownik zdecyduje się powierzyć firmie Microsoft Zarządzanie kluczem dzierżawy: 

- Jeśli nie są migrowane z usług AD RMS, żadne dalsze akcje nie są wymagane do wygenerowania klucza dzierżawy i można przejść bezpośrednio do [następne kroki](plan-implement-tenant-key.md#next-steps).

- Jeśli obecnie korzystasz z usług AD RMS i chcesz przeprowadzić migrację do usługi Azure Information Protection, skorzystaj z instrukcji migracji: Migracja z usług AD RMS do usługi Azure Information Protection. 

Jeśli użytkownik zdecyduje się samodzielnie zarządzać kluczem dzierżawy, powinien przeczytać poniższe sekcje, aby uzyskać więcej informacji.

## <a name="implementing-byok-for-your-azure-information-protection-tenant-key"></a>Implementowanie funkcji BYOK dla klucza dzierżawy usługi Azure Information Protection

Użyj zawartych w tej sekcji informacji oraz procedur, aby wygenerować klucz dzierżawy i samodzielnie nim zarządzać; scenariusz BYOK:

> [!NOTE]
> Jeśli rozpoczęto używanie usługi Azure Information Protection z kluczem dzierżawy, który jest zarządzany przez firmę Microsoft, a teraz chcesz samodzielnie zarządzać kluczem dzierżawy (w ramach rozwiązania BYOK), wcześniej zabezpieczone dokumenty i wiadomości będą nadal dostępne przy użyciu zarchiwizowanego klucza. 

### <a name="prerequisites-for-byok"></a>Wymagania wstępne dotyczące funkcji BYOK
Poniższa tabela zawiera listę wymagań wstępnych, które należy spełnić, aby móc korzystać z funkcji BYOK.

|Wymaganie|Więcej informacji|
|---------------|--------------------|
|Dzierżawy usługi Azure Information Protection musi mieć subskrypcję platformy Azure. Jeśli nie masz, możesz zarejestrować się w celu [bezpłatne konto](https://azure.microsoft.com/pricing/free-trial/). <br /><br /> Aby użyć klucza chronionego przez moduł HSM, musi mieć warstwę Premium magazynu kluczy Azure.|Bezpłatna subskrypcja platformy Azure, która zapewnia dostęp do konfigurowania usługi Azure Active Directory i konfiguracji szablonów niestandardowych usługi Azure Rights Management (**Dostęp do usługi Azure Active Directory**) jest niewystarczająca, aby używać usługi Azure Key Vault. Aby sprawdzić, czy masz subskrypcję platformy Azure umożliwiającą korzystanie z funkcji BYOK, użyj poleceń cmdlet programu PowerShell dla usługi [Azure Resource Manager](https://msdn.microsoft.com/library/azure/mt786812\(v=azure.300\).aspx): <br /><br /> 1. Uruchom sesję programu Azure PowerShell za pomocą opcji **Uruchom jako administrator** i zaloguj się jako administrator globalny dzierżawcy usługi Azure Information Protection przy użyciu następującego polecenia: `Login-AzureRmAccount`<br /><br />2. Wpisz następujące polecenie i upewnij się, że widzisz wartości nazwy i identyfikatora subskrypcji oraz identyfikatora dzierżawy usługi Azure Information Protection oraz że stan został włączony: `Get-AzureRmSubscription`<br /><br />Jeśli wartości nie zostaną wyświetlone i nastąpi powrót do wiersza polecenia, nie masz subskrypcji platformy Azure umożliwiającej korzystanie z funkcji BYOK. <br /><br />**Uwaga**: oprócz wymagań wstępnych funkcji BYOK do przeprowadzenia migracji z usług AD RMS do usługi Azure Information Protection przy użyciu klucza oprogramowania i klucza sprzętowego wymagane jest oprogramowanie układowe firmy Thales w wersji 11.62 lub nowszej.|
|Aby użyć klucza chronionego przez moduł HSM, utworzyć lokalnego: wymienione wszystkie wymagania wstępne dotyczące funkcji BYOK magazynu kluczy. |Zobacz [Wymagania wstępne dla funkcji BYOK](https://azure.microsoft.com/documentation/articles/key-vault-hsm-protected-keys/#prerequisites-for-byok) w dokumentacji usługi Azure Key Vault. <br /><br /> **Uwaga**: oprócz wymagań wstępnych funkcji BYOK do przeprowadzenia migracji z usług AD RMS do usługi Azure Information Protection przy użyciu klucza oprogramowania i klucza sprzętowego wymagane jest oprogramowanie układowe firmy Thales w wersji 11.62 lub nowszej.|
|Moduł administracyjny usługi Azure Rights Management dla programu Windows PowerShell.|Aby uzyskać instrukcje instalacji, zobacz [Instalowanie modułu programu PowerShell AADRM](../deploy-use/install-powershell.md). <br /><br />Jeśli ten moduł programu Windows PowerShell został już wcześniej zainstalowany, uruchom następujące polecenie, aby sprawdzić, czy numer wersji to co najmniej **2.9.0.0**: `(Get-Module aadrm -ListAvailable).Version`|

Aby uzyskać więcej informacji o modułach HSM firmy Thales i sposobie ich wykorzystania w usłudze Azure Key Vault, zobacz [witrynę sieci Web firmy Thales](https://www.thales-esecurity.com/msrms/cloud).

### <a name="choosing-your-key-vault-location"></a>Wybieranie lokalizacji magazynu kluczy

Po utworzeniu magazynu kluczy zawiera klucz do użycia jako klucz dzierżawy Azure informacji należy określić lokalizację. Ta lokalizacja jest region platformy Azure lub wystąpienia platformy Azure.

Dokonać wyboru pierwszego zgodności, a następnie, aby zminimalizować opóźnienie sieci:

- Jeśli wybrano topologii klucza BYOK wymaganiami dotyczącymi zgodności te wymagania zgodności mogą wprowadzić region platformy Azure lub Azure wystąpienia, która przechowuje klucz dzierżawy usługi Azure Information Protection.

- Ponieważ wszystkie wywołania kryptograficznych dla ochrony powiązane z klucza dzierżawy usługi Azure Information Protection, należy zminimalizować opóźnienia sieci, które ponoszą tych wywołań. W tym celu należy utworzyć magazynu kluczy w tym samym regionie Azure lub wystąpienia jako dzierżawy usługi Azure Information Protection.

Aby określić lokalizację dzierżawy usługi Azure Information Protection, użyj [Get-AadrmConfiguration](/powershell/module/aadrm/get-aadrmconfiguration) polecenia cmdlet programu PowerShell i zidentyfikować region z adresów URL. Przykład:

    LicensingIntranetDistributionPointUrl : https://5c6bb73b-1038-4eec-863d-49bded473437.rms.na.aadrm.com/_wmcs/licensing

Region jest do zidentyfikowania z **rms.na.aadrm.com**, a w tym przykładzie jest w Ameryce Północnej.

Poniższa tabela umożliwia zidentyfikowanie, które region platformy Azure lub wystąpienia jest zalecane, aby zminimalizować opóźnienie sieci.

|Region platformy Azure lub wystąpienia|Zalecana lokalizacja magazynu kluczy|
|---------------|--------------------|
|rms.**na**.aadrm.com|**Środkowe stany USA Północna** lub **wschodnie stany USA**|
|rms.**eu**.aadrm.com|**Europa Północna, Europa** lub **Europa Zachodnia**|
|rms.**ap**.aadrm.com|**Azja Wschodnia** lub **Azja południowo-wschodnia**|
|rms.**sa**.aadrm.com|**Zachodnie stany USA** lub **wschodnie stany USA**|
|rms.**govus**.aadrm.com|**Środkowe stany USA** lub **wschodnie stany USA 2**|


### <a name="instructions-for-byok"></a>Instrukcje dotyczące strategii BYOK

Dokumentacja usługi Azure Key Vault umożliwia utworzenie magazynu kluczy oraz klucz, który ma być używany dla usługi Azure Information Protection. Na przykład, zobacz [wprowadzenie do usługi Azure Key Vault](/azure/key-vault/key-vault-get-started).

Upewnij się, że długość klucza to 2048 bitów (zalecane) lub 1024 bity. Inne długości kluczy nie są obsługiwane przez usługę Azure Information Protection.

Aby utworzyć chronionego przez moduł HSM klucza lokalnie i przenieś ją do magazynu kluczy jako klucza chronionego przez moduł HSM, wykonaj procedury opisane w [jak Generowanie i przenoszenie kluczy chronionych modułem HSM dla usługi Azure Key Vault](https://azure.microsoft.com/documentation/articles/key-vault-hsm-protected-keys/).

Klucz, który jest przechowywany w magazynie kluczy ma klucz identyfikatora. Klucz ten identyfikator jest adres URL, który zawiera nazwę magazynu kluczy, kontener kluczy, nazwę klucza i wersji klucza. Na przykład: **https://contosorms-kv.vault.azure.net/keys/contosorms-byok/aaaabbbbcccc111122223333**. Należy skonfigurować usługę Azure Information Protection, aby użyć tego klucza, podając jego adres URL magazynu kluczy.

Przed usługi Azure Information Protection można użyć klucza, usługa Azure Rights Management musi być autoryzowany do użycia klucza w magazynie kluczy w organizacji. Aby to zrobić, administrator usługi Azure Key Vault używa polecenia cmdlet programu PowerShell dla usługi Key Vault, [Set-AzureRmKeyVaultAccessPolicy](/powershell/module/azurerm.keyvault/set-azurermkeyvaultaccesspolicy), i przydziela uprawnienia głównej nazwie usługi Azure Rights Management, używając identyfikatora GUID 00000012-0000-0000-c000-000000000000. Przykład:

    Set-AzureRmKeyVaultAccessPolicy -VaultName 'ContosoRMS-kv' -ResourceGroupName 'ContosoRMS-byok-rg' -ServicePrincipalName 00000012-0000-0000-c000-000000000000 -PermissionsToKeys decrypt,sign,get

Teraz możesz przystąpić do konfigurowania usługi Azure Information Protection do użycia tego klucza jako klucza dzierżawy usługi Azure Information Protection w organizacji. Korzystając z poleceń cmdlet usługi Azure RMS, nawiąż połączenie z usługą Azure Rights Management i zaloguj się:

    Connect-AadrmService

Następnie uruchom polecenie [cmdlet Use-AadrmKeyVaultKey](/powershell/module/aadrm/use-aadrmkeyvaultkey), określając adres URL klucza. Przykład:

    Use-AadrmKeyVaultKey -KeyVaultKeyUrl "https://contosorms-kv.vault.azure.net/keys/contosorms-byok/aaaabbbbcccc111122223333"

> [!IMPORTANT]
> W tym przykładzie wersja klucza do użycia to „aaaabbbbcccc111122223333”. Jeśli nie określisz wersji, bieżąca wersja klucza jest używana bez ostrzeżenia, a polecenie działa prawidłowo. Jeśli jednak klucz w usłudze Key Vault zostanie później zaktualizowany (odnowiony), usługa Azure Rights Management nie będzie działać w dzierżawie nawet po ponownym uruchomieniu polecenia Use-AadrmKeyVaultKey.
>
>Upewnij się, że w przypadku uruchamiania tego polecenia oprócz nazwy klucza zostanie określona również jego wersja. Aby uzyskać numer wersji bieżącego klucza, można użyć polecenia [Get-AzureKeyVaultKey](/powershell/module/azurerm.keyvault\get-azurekeyvaultkey) usługi Azure Key Vault. Na przykład: `Get-AzureKeyVaultKey -VaultName 'contosorms-kv' -KeyName 'contosorms-byok'`

Jeśli musisz potwierdzić, że klucz adres URL jest ustawione prawidłowo dla usługi Azure Information Protection: W usłudze Azure Key Vault, uruchom [Get-AzureKeyVaultKey](/powershell/module/azurerm.keyvault\get-azurekeyvaultkey) Aby wyświetlić klucz adresu URL.

Ponadto jeśli usługi Azure Rights Management została już aktywowana, uruchom [AadrmKeyProperties zestaw](/powershell/module/aadrm/set-aadrmkeyproperties) mówić usługi Azure Information Protection, aby użyć tego klucza jako klucza aktywne dzierżawy usługi Azure Rights Management. Po wykonaniu tego kroku usługi Azure Information Protection będzie używać domyślnego zarządzany przez firmę Microsoft klucza, który został utworzony automatycznie dla dzierżawy.


## <a name="next-steps"></a>Następne kroki

Teraz, gdy zaplanowaniu dla, a jeśli to konieczne, utworzone i skonfigurowane z kluczem dzierżawy, wykonaj następujące czynności:

1.  Rozpocznij korzystanie z klucza dzierżawy:
    
    - Jeśli jeszcze nie zostało to zrobione, należy teraz aktywować usługę Rights Management, aby organizacja mogła zacząć korzystać z usługi Azure Information Protection. Użytkownicy natychmiast otrzymują możliwość korzystania z klucza dzierżawy (zarządzany przez firmę Microsoft lub zarządzany przez użytkownika w usłudze Azure Key Vault).
    
        Aby uzyskać więcej informacji o aktywacji, zobacz [Aktywacja usługi Azure Rights Management](../deploy-use/activate-service.md).
        
    - Jeśli usługa Rights Management została już aktywowana, a następnie podjęto decyzję o samodzielnym zarządzaniu kluczem dzierżawy, użytkownicy stopniowo przechodzą ze starego klucza dzierżawy na nowy. Okres przejściowy może trwać do kilku tygodni. Dokumenty i pliki, które były chronione przy użyciu starego klucza dzierżawy, pozostają dostępne dla użytkowników upoważnionych do dostępu do nich.
        
2. Rozważ włączenie funkcji rejestrowania użycia, która tworzy dzienniki uwzględniające każdą czynność wykonywaną w ramach usługi Azure Rights Management.
    
    Użytkownik samodzielnie zarządzający kluczem dzierżawy może uzyskać dostęp do rejestrów uwzględniających informacje o użyciu jego własnego klucza dzierżawy. Poniżej znajduje się fragment kodu z pliku dziennika wyświetlany w programie Excel. Typy żądań **KeyVaultDecryptRequest** i **KeyVaultSignRequest** pokazują, że klucz dzierżawy jest w użyciu.
    
    ![Plik dziennika wyświetlony w programie Excel, pokazujący, że klucz dzierżawy jest w użyciu](../media/RMS_Logging.png)
    
    Aby uzyskać więcej informacji na temat rejestrowania użycia, zobacz [Rejestrowanie i analizowanie danych użycia usługi Azure Rights Management](../deploy-use/log-analyze-usage.md).
    
3.  Zarządzanie kluczem dzierżawy.
    
    Aby uzyskać więcej informacji na temat operacji cyklu życia klucza dzierżawy, zobacz [operacje związane z kluczem dzierżawy usługi Azure Information Protection](../deploy-use/operations-tenant-key.md).

[!INCLUDE[Commenting house rules](../includes/houserules.md)]