---
title: "Klucz dzierżawy usługi Azure Information Protection"
description: "Informacje ułatwiające zaplanowanie użycia klucza dzierżawy usługi Azure Information Protection oraz zarządzanie nim. Domyślne ustawienie zakłada, że to firma Microsoft zarządza kluczem dzierżawy. Ustawienie to można zmienić, aby zarządzać własnym kluczem dzierżawy w celu zachowania zgodności z konkretnymi przepisami mającymi zastosowanie w danej organizacji. Samodzielne zarządzanie kluczem dzierżawy określa się także mianem strategii BYOK (Bring Your Own Key), czyli „Przynieś własny klucz”."
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 06/07/2017
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: f0d33c5f-a6a6-44a1-bdec-5be1bc8e1e14
ms.reviewer: esaggese
ms.suite: ems
ms.openlocfilehash: e14a57a8bd8343113e2bfc3f71835f55f0ee2dee
ms.sourcegitcommit: 04eb4990e2bf0004684221592cb93df35e6acebe
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/30/2017
---
# <a name="planning-and-implementing-your-azure-information-protection-tenant-key"></a>Planowanie i wdrażanie klucza dzierżawy usługi Azure Information Protection

>*Dotyczy: Azure Information Protection, Office 365*

Informacje zawarte w tym artykule ułatwiają zaplanowanie użycia klucza dzierżawy usługi Azure Information Protection oraz zarządzanie nim. Domyślne ustawienie zakłada, że to firma Microsoft zarządza kluczem dzierżawy. Ustawienie to można zmienić, aby zarządzać własnym kluczem dzierżawy w celu zachowania zgodności z konkretnymi przepisami mającymi zastosowanie w danej organizacji. Samodzielne zarządzanie kluczem dzierżawy określa się także mianem strategii BYOK (Bring Your Own Key), czyli „Przynieś własny klucz”.

> [!NOTE]
> Lokalny odpowiednik klucza dzierżawy usługi Azure Information Protection jest określany jako klucz certyfikatu licencjodawcy serwera (klucz SLC). Usługa Azure Information Protection obsługuje co najmniej jeden klucz dla każdej organizacji, która ją subskrybuje. Za każdym razem, gdy na potrzeby usługi Azure Information Protection używanej w obrębie organizacji są wykorzystywane klucze (np. klucze użytkownika, klucze komputera lub klucze szyfrowania dokumentu), ma miejsce szyfrowane połączenie użytego klucza z kluczem dzierżawy usługi Azure Information Protection.

**Krótki przegląd:** poniższa tabela pełni rolę przewodnika po zalecanych topologiach klucza dzierżawy. Więcej informacji można znaleźć w dodatkowej dokumentacji.

|Wymaganie biznesowe|Zalecana topologia klucza dzierżawy|
|------------------------|-----------------------------------|
|Skorzystaj z możliwości szybkiego wdrożenia usługi Azure Information Protection — proces nie wymaga użycia żadnego specjalnego sprzętu|Klucz zarządzany przez firmę Microsoft|
|Wymagana pełna funkcjonalność IRM w usłudze Exchange Online z usługą Azure Rights Management|Klucz zarządzany przez firmę Microsoft|
|Klucze są tworzone przez użytkownika i bezpiecznie przechowywane w sprzętowym module zabezpieczeń (HSM)|BYOK<br /><br />Obecnie wybór tej konfiguracji powoduje ograniczenie funkcjonalności IRM w usłudze Exchange Online. Aby uzyskać więcej informacji, zobacz [Cennik i ograniczenia dotyczące funkcji BYOK](byok-price-restrictions.md).|

W razie potrzeby można zmienić topologię klucza dzierżawy po wdrożeniu, używając polecenia cmdlet [Set-AadrmKeyProperties](/powershell/module/aadrm/set-aadrmkeyproperties).


## <a name="choose-your-tenant-key-topology-managed-by-microsoft-the-default-or-managed-by-you-byok"></a>Wybierz topologię klucza dzierżawy: klucz zarządzany przez firmę Microsoft (ustawienie domyślne) lub klucz zarządzany przez użytkownika (BYOK)
Zdecyduj, która topologia klucza dzierżawy jest najodpowiedniejsza dla Twojej organizacji. Domyślnie usługa Azure Information Protection generuje klucz dzierżawy i zarządza większością aspektów cyklu jego życia. Jest to najprostsza opcja, która wiąże się z najmniejszą liczbą obowiązków administracyjnych użytkownika. W większości przypadków użytkownik nie musi nawet wiedzieć, że ma klucz dzierżawy. Wystarczy, że zarejestruje się w usłudze Azure Information Protection — resztą procesu zarządzania kluczem zajmie się firma Microsoft.

Możesz też skorzystać z pełnej kontroli nad swoim kluczem dzierżawy, używając usługi [Azure Key Vault](https://azure.microsoft.com/services/key-vault/). Ten scenariusz obejmuje utworzenie klucza dzierżawy i lokalne przechowywanie kopii głównej. Ten model jest często określany mianem BYOK (ang. Bring Your Own Key), czyli „Przynieś własny klucz”. Po wybraniu tej opcji:

1.  Klucz dzierżawy jest generowany lokalnie przez użytkownika w sposób zgodny z zasadami dotyczącymi infrastruktury IT i zasadami dotyczącymi zabezpieczeń obowiązującymi w organizacji.

2.  Przechowywany lokalnie klucz jest bezpiecznie przesyłany z lokalnego sprzętowego modułu zabezpieczeń (HSM, Hardware Security Module) do należących do firmy Microsoft i zarządzanych przez nią modułów HSM, przy użyciu usługi Azure Key Vault. W toku całego tego procesu klucz dzierżawy nigdy nie przekracza granic zabezpieczeń sprzętowych.

3.  W przypadku przeniesienia klucza dzierżawy do firmy Microsoft pozostaje on objęty ochroną usługi Azure Key Vault.

Choć generowane niemalże w czasie rzeczywistym dzienniki z usługi Azure Information Protection są opcjonalne, warto z nich skorzystać, aby przekonać się, kiedy i w jaki sposób jest używany klucz dzierżawy.

> [!NOTE]
> Dodatkowym środkiem ochrony dostępnym w usłudze Azure Key Vault są wykorzystywane w jej ramach oddzielne domeny zabezpieczeń dla centrów danych w regionach, takich jak Ameryka Północna; Europa, Bliski Wschód i Afryka (EMEA) oraz Azja. Ponadto dotyczy to różnych wystąpień platformy Azure, np. Microsoft Azure Germany i Azure Government. Klucz dzierżawy, którym zarządza użytkownik, jest powiązany z domeną zabezpieczeń odpowiadającą regionowi lub wystąpieniu, w którym jest zarejestrowana dzierżawa usługi Azure Information Protection. Na przykład klucz dzierżawy europejskiego klienta nie może zostać użyty w centrach danych w Ameryce Północnej ani Azji.

## <a name="the-tenant-key-lifecycle"></a>Cykl życia klucza dzierżawy
Jeśli użytkownik zdecyduje, że to firma Microsoft ma zarządzać kluczem dzierżawy, będzie ona obsługiwać większość operacji związanych z cyklem życia klucza. Jeśli jednak użytkownik chce zarządzać kluczem dzierżawy, będzie odpowiadać za wiele operacji związanych z cyklem życia klucza oraz za niektóre dodatkowe procedury w usłudze Azure Key Vault.

Na poniższych diagramach omówiono te dwie opcje i przedstawiono ich porównanie. Na pierwszym diagramie pokazano, jak niskie są koszty administracyjne ponoszone przez użytkownika w przypadku konfiguracji domyślnej, gdy to firma Microsoft zarządza kluczem dzierżawy.

![Cykl życia klucza dzierżawy usługi Azure Information Protection w przypadku zarządzania kluczem przez firmę Microsoft (konfiguracja domyślna)](../media/RMS_BYOK_cloud.png)

Drugi diagram przedstawia dodatkowe kroki wymagane w przypadku, gdy za zarządzanie kluczem dzierżawy odpowiada użytkownik.

![Cykl życia klucza dzierżawy usługi Azure Information Protection w przypadku zarządzania kluczem przez użytkownika (konfiguracja BYOK)](../media/RMS_BYOK_onprem4.png)

Jeśli zdecydujesz się powierzyć firmie Microsoft zarządzanie kluczem dzierżawy, w celu wygenerowania klucza nie są wymagane żadne dalsze działania — można przejść bezpośrednio do sekcji [Następne kroki](plan-implement-tenant-key.md#next-steps).  

Jeśli użytkownik zdecyduje się samodzielnie zarządzać kluczem dzierżawy, powinien przeczytać poniższe sekcje, aby uzyskać więcej informacji.

## <a name="implementing-your-azure-information-protection-tenant-key"></a>Wdrażanie klucza dzierżawy usługi Azure Information Protection

Użyj zawartych w tej sekcji informacji oraz procedur, aby wygenerować klucz dzierżawy i samodzielnie nim zarządzać; scenariusz BYOK:


> [!IMPORTANT]
> Jeśli rozpoczęto używanie usługi Azure Information Protection z kluczem dzierżawy, który jest zarządzany przez firmę Microsoft, a teraz chcesz samodzielnie zarządzać kluczem dzierżawy (w ramach rozwiązania BYOK), wcześniej zabezpieczone dokumenty i wiadomości będą nadal dostępne przy użyciu zarchiwizowanego klucza. Jeśli jednak istnieją użytkownicy korzystający z pakietu Office 2010, [skontaktuj się z pomocą techniczną firmy Microsoft](../get-started/information-support.md#to-contact-microsoft-support) przed uruchomieniem tych procedur. W przypadku tych komputerów konieczne będzie wykonanie dodatkowych czynności konfiguracyjnych.
> 
> [Skontaktuj się z pomocą techniczną firmy Microsoft](../get-started/information-support.md#to-contact-microsoft-support) także wtedy, gdy w Twojej organizacji obowiązują konkretne zasady dotyczące postępowania z kluczami.

### <a name="prerequisites-for-byok"></a>Wymagania wstępne dotyczące funkcji BYOK
Poniższa tabela zawiera listę wymagań wstępnych, które należy spełnić, aby móc korzystać z funkcji BYOK.

|Wymaganie|Więcej informacji|
|---------------|--------------------|
|Subskrypcja zawierająca usługę Azure Information Protection|Dodatkowe informacje o dostępnych subskrypcjach znajdują się na [stronie z cennikiem](https://go.microsoft.com/fwlink/?LinkId=827589) usługi Azure Information Protection.|
|Nie należy używać usługi Exchange Online.<br /><br /> Użytkownicy, którzy zdecydują się korzystać z usługi Exchange Online, muszą zrozumieć i zaakceptować ograniczenia związane z korzystaniem z funkcji BYOK w tej konfiguracji.|Aby uzyskać więcej informacji na temat ogólnych i bieżących ograniczeń dotyczących korzystania z funkcji BYOK, zobacz [Cennik i ograniczenia dotyczące funkcji BYOK](byok-price-restrictions.md).<br /><br />**Ważne**: funkcja BYOK nie jest obecnie zgodna z usługą Exchange Online.|
|Wszystkie wymagania wstępne dla funkcji BYOK usługi Key Vault uwzględniającej płatną lub próbną wersję subskrypcji platformy Azure dla istniejącego dzierżawcy usługi Azure Information Protection. |Zobacz [Wymagania wstępne dla funkcji BYOK](https://azure.microsoft.com/documentation/articles/key-vault-hsm-protected-keys/#prerequisites-for-byok) w dokumentacji usługi Azure Key Vault. <br /><br /> Bezpłatna subskrypcja platformy Azure, która zapewnia dostęp do konfigurowania usługi Azure Active Directory i konfiguracji szablonów niestandardowych usługi Azure Rights Management (**Dostęp do usługi Azure Active Directory**) jest niewystarczająca, aby używać usługi Azure Key Vault. Aby sprawdzić, czy masz subskrypcję platformy Azure umożliwiającą korzystanie z funkcji BYOK, użyj poleceń cmdlet programu PowerShell dla usługi [Azure Resource Manager](https://msdn.microsoft.com/library/azure/mt786812\(v=azure.300\).aspx): <br /><br /> 1. Uruchom sesję programu Azure PowerShell za pomocą opcji **Uruchom jako administrator** i zaloguj się jako administrator globalny dzierżawcy usługi Azure Information Protection przy użyciu następującego polecenia: `Login-AzureRmAccount`<br /><br />2. Wpisz następujące polecenie i upewnij się, że widzisz wartości nazwy i identyfikatora subskrypcji oraz identyfikatora dzierżawy usługi Azure Information Protection oraz że stan został włączony: `Get-AzureRmSubscription`<br /><br />Jeśli wartości nie zostaną wyświetlone i nastąpi powrót do wiersza polecenia, nie masz subskrypcji platformy Azure umożliwiającej korzystanie z funkcji BYOK. <br /><br />**Uwaga**: oprócz wymagań wstępnych funkcji BYOK do przeprowadzenia migracji z usług AD RMS do usługi Azure Information Protection przy użyciu klucza oprogramowania i klucza sprzętowego wymagane jest oprogramowanie układowe firmy Thales w wersji 11.62 lub nowszej.|
|Moduł administracyjny usługi Azure Rights Management dla programu Windows PowerShell.|Instrukcje instalacji znajdują się w sekcji [Instalowanie programu Windows PowerShell dla usługi Azure Rights Management](../deploy-use/install-powershell.md). <br /><br />Jeśli ten moduł programu Windows PowerShell został już wcześniej zainstalowany, uruchom następujące polecenie, aby sprawdzić, czy numer wersji to co najmniej **2.9.0.0**: `(Get-Module aadrm -ListAvailable).Version`|

Aby uzyskać więcej informacji o modułach HSM firmy Thales i sposobie ich wykorzystania w usłudze Azure Key Vault, zobacz [witrynę sieci Web firmy Thales](https://www.thales-esecurity.com/msrms/cloud).

### <a name="instructions-for-byok"></a>Instrukcje dotyczące strategii BYOK

Aby wygenerować i przenieść własny klucz dzierżawy do usługi Azure Key Vault, wykonaj procedury opisane w temacie [Jak wygenerować i przenieść klucze chronione przy użyciu modułu HSM do usługi Azure Key Vault](https://azure.microsoft.com/documentation/articles/key-vault-hsm-protected-keys/) w dokumentacji usługi Azure Key Vault.

Gdy klucz jest przesyłany do usługi Key Vault, otrzymuje identyfikator klucza w usłudze Key Vault, który jest adresem URL zawierającym nazwę magazynu kluczy, kontener kluczy, nazwę klucza i wersję klucza. Na przykład: **https://contosorms-kv.vault.azure.net/keys/contosorms-byok/aaaabbbbcccc111122223333**. Usługa Azure Rights Management z usługi Azure Information Protection będzie potrzebować tego adresu URL do skonfigurowania użycia klucza.

Zanim usługa Azure Information Protection będzie mogła użyć tego klucza, należy autoryzować usługę Azure Rights Management do używania kluczy znajdujących się w magazynie kluczy organizacji. Aby to zrobić, administrator usługi Azure Key Vault używa polecenia cmdlet programu PowerShell dla usługi Key Vault, [Set-AzureRmKeyVaultAccessPolicy](/powershell/module/azurerm.keyvault/set-azurermkeyvaultaccesspolicy), i przydziela uprawnienia głównej nazwie usługi Azure Rights Management, używając identyfikatora GUID 00000012-0000-0000-c000-000000000000. Na przykład:

    Set-AzureRmKeyVaultAccessPolicy -VaultName 'ContosoRMS-kv' -ResourceGroupName 'ContosoRMS-byok-rg' -ServicePrincipalName 00000012-0000-0000-c000-000000000000 -PermissionsToKeys decrypt,encrypt,unwrapkey,wrapkey,verify,sign,get

Teraz możesz przystąpić do konfigurowania usługi Azure Information Protection do użycia tego klucza jako klucza dzierżawy usługi Azure Information Protection w organizacji. Korzystając z poleceń cmdlet usługi Azure RMS, nawiąż połączenie z usługą Azure Rights Management i zaloguj się:

    Connect-AadrmService

Następnie uruchom polecenie [cmdlet Use-AadrmKeyVaultKey](/powershell/module/aadrm/use-aadrmkeyvaultkey), określając adres URL klucza. Na przykład:

    Use-AadrmKeyVaultKey -KeyVaultKeyUrl "https://contosorms-kv.vault.azure.net/keys/contosorms-byok/aaaabbbbcccc111122223333"

> [!IMPORTANT]
> W tym przykładzie wersja klucza do użycia to „aaaabbbbcccc111122223333”. Jeśli nie określisz wersji, bieżąca wersja klucza jest używana bez ostrzeżenia, a polecenie działa prawidłowo. Jeśli jednak klucz w usłudze Key Vault zostanie później zaktualizowany (odnowiony), usługa Azure Rights Management nie będzie działać w dzierżawie nawet po ponownym uruchomieniu polecenia Use-AadrmKeyVaultKey.
>
>Upewnij się, że w przypadku uruchamiania tego polecenia oprócz nazwy klucza zostanie określona również jego wersja. Aby uzyskać numer wersji bieżącego klucza, można użyć polecenia [Get-AzureKeyVaultKey](/powershell/resourcemanager/azurerm.keyvault\get-azurekeyvaultkey) usługi Azure Key Vault. Na przykład: `Get-AzureKeyVaultKey -VaultName 'contosorms-kv' -KeyName 'contosorms-byok'`

Jeśli chcesz potwierdzić, że adres URL klucza jest skonfigurowany prawidłowo w usłudze Azure RMS, możesz uruchomić polecenie cmdlet [Get-AzureKeyVaultKey](/powershell/resourcemanager/azurerm.keyvault\get-azurekeyvaultkey) w usłudze Azure Key Vault, aby zobaczyć adres URL klucza.

Jeśli usługa Azure Rights Management została już aktywowana, uruchom polecenie [Set-AadrmKeyProperties](/powershell/module/aadrm/set-aadrmkeyproperties), aby poinformować usługę Azure Rights Management, że ma używać tego klucza jako aktywnego klucza dzierżawy dla usługi Azure Rights Management. Jeśli tego nie zrobisz, usługa Azure Rights Management będzie nadal używać domyślnego klucza zarządzanego przez firmę Microsoft, który został automatycznie utworzony w ramach aktywowania usługi.


## <a name="next-steps"></a>Następne kroki

Gdy udało się już zaplanować używanie klucza dzierżawy i w razie potrzeby wygenerować go, wykonaj następujące czynności:

1.  Rozpocznij korzystanie z klucza dzierżawy:
    
    - Jeśli jeszcze nie zostało to zrobione, należy teraz aktywować usługę Rights Management, aby organizacja mogła zacząć korzystać z usługi Azure Information Protection. Użytkownicy natychmiast otrzymują możliwość korzystania ze swojego klucza dzierżawy (zarządzanego przez firmę Microsoft lub przez użytkownika w usłudze Azure Key Vault).
    
        Aby uzyskać więcej informacji o aktywacji, zobacz [Aktywacja usługi Azure Rights Management](../deploy-use/activate-service.md).
        
    - Jeśli usługa Rights Management została już aktywowana, a następnie podjęto decyzję o samodzielnym zarządzaniu kluczem dzierżawy, użytkownicy stopniowo przechodzą ze starego klucza dzierżawy na nowy. Okres przejściowy może trwać do kilku tygodni. Dokumenty i pliki, które były chronione przy użyciu starego klucza dzierżawy, pozostają dostępne dla użytkowników upoważnionych do dostępu do nich.
        
2. Rozważ włączenie funkcji rejestrowania użycia, która tworzy dzienniki uwzględniające każdą czynność wykonywaną w ramach usługi Azure Rights Management.
    
    Użytkownik samodzielnie zarządzający kluczem dzierżawy może uzyskać dostęp do rejestrów uwzględniających informacje o użyciu jego własnego klucza dzierżawy. Poniżej znajduje się fragment kodu z pliku dziennika wyświetlany w programie Excel. Typy żądań **KeyVaultDecryptRequest** i **KeyVaultSignRequest** pokazują, że klucz dzierżawy jest w użyciu.
    
    ![Plik dziennika wyświetlony w programie Excel, pokazujący, że klucz dzierżawy jest w użyciu](../media/RMS_Logging.png)
    
    Aby uzyskać więcej informacji na temat rejestrowania użycia, zobacz [Rejestrowanie i analizowanie danych użycia usługi Azure Rights Management](../deploy-use/log-analyze-usage.md).
    
3.  Wykonuj czynności związane z obsługą klucza dzierżawy.
    
    Aby uzyskać więcej informacji, zobacz [Operacje związane z kluczem dzierżawy usługi Azure Rights Management](../deploy-use/operations-tenant-key.md).

[!INCLUDE[Commenting house rules](../includes/houserules.md)]
