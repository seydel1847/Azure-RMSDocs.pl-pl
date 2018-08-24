---
title: Zarządzane przez klienta operacje cykl życia klucza dzierżawy usługi AIP
description: Informacje na temat operacji cyklu życia, które są istotne, jeśli zarządzasz swoim kluczem dzierżawy usługi Azure Information Protection (bring your own key, byok, scenariusz).
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 03/07/2018
ms.topic: article
ms.service: information-protection
ms.assetid: c5b19c59-812d-420c-9c54-d9776309636c
ms.reviewer: esaggese
ms.suite: ems
ms.openlocfilehash: e910ad5226310f0c76de437c30e95fb7f6ba8f87
ms.sourcegitcommit: 7ba9850e5bb07b14741bb90ebbe98f1ebe057b10
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/23/2018
ms.locfileid: "42804057"
---
# <a name="customer-managed-tenant-key-life-cycle-operations"></a>Zarządzany przez klienta: Operacje cykl życia klucza dzierżawy

>*Dotyczy: [usługi Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection), [usługi Office 365](http://download.microsoft.com/download/E/C/F/ECF42E71-4EC0-48FF-AA00-577AC14D5B5C/Azure_Information_Protection_licensing_datasheet_EN-US.pdf)*

Jeśli samodzielnie zarządzasz swoim kluczem dzierżawy dla usługi Azure Information Protection (bring your own key, byok, scenariusz), użyj poniższych sekcji, aby uzyskać więcej informacji na temat operacji cyklu życia, które mają zastosowanie w tej topologii.

## <a name="revoke-your-tenant-key"></a>Odwołanie klucza dzierżawy
W usłudze Azure Key Vault można zmienić uprawnienia dotyczące magazynu kluczy, który zawiera klucz dzierżawy usługi Azure Information Protection, aby usługa Azure Rights Management nie mogła już uzyskać dostępu do tego klucza. Niemniej po wykonaniu tej czynności nikt nie będzie w stanie otworzyć dokumentów i wiadomości e-mail, które zostały wcześniej zabezpieczone przez usługę Azure Rights Management.

Po anulowaniu subskrypcji usługi Azure Information Protection usługa ta wstrzymuje korzystanie z klucza dzierżawy, co nie wymaga żadnej akcji ze strony użytkownika.

## <a name="rekey-your-tenant-key"></a>Wymiana klucza dzierżawy
Wymiana klucza jest także określana jako uaktualnianie klucza. Po wykonaniu tej operacji usługi Azure Information Protection ta wstrzymuje korzystanie z istniejącego klucza dzierżawy do ochrony dokumentów i wiadomości e-mail, a następnie zaczyna używać innego klucza. Zasady i szablony są natychmiast ponownie podpisane, ale tej zmiany jest stopniowe dla istniejących klientów i usług przy użyciu usługi Azure Information Protection. Dlatego przez pewien czas część nowej zawartości w dalszym ciągu być chronione przy użyciu starego klucza dzierżawy.

Do ponownego generowania kluczy należy skonfigurować obiekt klucza dzierżawy i określić alternatywne klucza do użycia. Następnie wcześniej używany klucz jest automatycznie oznaczony jako zarchiwizowane usługi Azure Information Protection. Ta konfiguracja zapewnia tę zawartość, która była chroniona za pomocą tego klucza będą nadal dostępne.

Przykładem może być konieczność wymiany klucza usługi Azure Information Protection:

- Firma została podzielona na dwie lub więcej firm. Po wymianie klucza dzierżawy nowa firma nie będzie miała dostępu do nowej zawartości publikowanej przez pracowników. Mogą oni uzyskać dostęp do starej zawartości, jeśli dysponują kopią starego klucza dzierżawy.

- Chcesz przenieść z jednej topologię zarządzania kluczami do innego. 

- Uważasz, że zostanie naruszony kopii głównej klucza dzierżawy (kopia przesyłany).

Aby wymienić na inny klucz, którymi zarządza użytkownik, możesz utworzyć nowy klucz w usłudze Azure Key Vault lub użyć innego klucza, który jest już w usłudze Azure Key Vault. Następnie wykonaj te same procedury, których nie było Implementowanie funkcji BYOK dla usługi Azure Information Protection.

1. Tylko wtedy, gdy nowy klucz w innym magazynie kluczy do tego, którego już używasz usługi Azure Information Protection: autoryzowania usługi Azure Information Protection do użycia magazynu kluczy przy użyciu [Set-AzureRmKeyVaultAccessPolicy](/powershell/module/azurerm.keyvault/set-azurermkeyvaultaccesspolicy) polecenia cmdlet.

2. Jeśli usługi Azure Information Protection nie jest już znany o kluczu, którą chcesz użyć, uruchom [Use-AadrmKeyVaultKey](/powershell/module/aadrm/use-aadrmkeyvaultkey) polecenia cmdlet.

3. Skonfigurować obiekt klucza dzierżawy za pomocą opcji Uruchom [Set-AadrmKeyProperties](/powershell/module/aadrm/set-aadrmkeyproperties) polecenia cmdlet.

Aby uzyskać więcej informacji na temat każdego z następujących czynności:

- Aby wymienić na inny klucz, który można zarządzać, zobacz [Implementowanie funkcji BYOK dla klucza dzierżawy usługi Azure Information Protection](plan-implement-tenant-key.md#implementing-byok-for-your-azure-information-protection-tenant-key).

- Wymiany, zmiana z kluczem przez firmę Microsoft zarządza dla Ciebie, zobacz [Wymień klucz dzierżawy](operations-microsoft-managed-tenant-key.md#rekey-your-tenant-key) sekcji dla operacji zarządzanych przez firmę Microsoft.

## <a name="backup-and-recover-your-tenant-key"></a>Tworzenie kopii zapasowej i odzyskiwanie klucza dzierżawy
Ponieważ zarządzasz swoim kluczem dzierżawy, ponosisz odpowiedzialność za tworzenie kopii zapasowej klucza, który korzysta z usługi Azure Information Protection. 

Jeśli klucz dzierżawy w środowisku lokalnym, jest generowany w module HSM firmy Thales: Aby utworzyć kopię zapasową klucza, należy utworzyć kopię zapasową tokenami plik klucza, pliku środowiska zabezpieczeń oraz kart administratora. W przypadku przeniesienia klucza do usługi Azure Key Vault, usługa zapisuje tokenami pliku klucza w celu zapewnienia ochrony przed awariami jakichkolwiek węzłów usługi. Ten plik jest powiązany ze środowiskiem zabezpieczeń dla konkretnego regionu lub wystąpienia platformy Azure. Jednak nie należy traktować tego tokenami klucza pliku pełnej kopii zapasowej. Na przykład, jeśli potrzebujesz wsparcia kopię klucza, aby używać poza modułem zabezpieczeń firmy Thales w zwykły tekst, usługi Azure Key Vault nie można pobrać go, ponieważ ma on przywrócenie kopii.

Usługa Azure Key Vault ma [kopii zapasowej polecenia cmdlet](/powershell/module/azurerm.keyvault/Backup-AzureKeyVaultKey) służące do tworzenia kopii zapasowych klucza, pobierając go i zapisanie go w pliku. Ponieważ pobranej zawartości jest zaszyfrowany, nie można używać poza usługi Azure Key Vault. 

## <a name="export-your-tenant-key"></a>Eksport klucza dzierżawy
W przypadku korzystania z rozwiązania BYOK nie można wyeksportować klucza dzierżawy ani z usługi Azure Key Vault, ani z usługi Azure Information Protection. Przywrócenie kopii klucza znajdującej się w usłudze Azure Key Vault nie jest możliwe. 

## <a name="respond-to-a-breach"></a>Reakcja na naruszenie zabezpieczeń
Żaden system zabezpieczeń, niezależnie od jego siły, nie jest kompletny bez procedur reakcji na naruszenie zabezpieczeń. Klucz dzierżawy może zostać naruszony lub skradziony. Nawet wtedy, gdy jest on chroniony dobrze, mogą występować luki w obecnej generacji technologii klucza lub w bieżącym długości kluczy i algorytmów.

Firma Microsoft ma dedykowany zespół, który reaguje na przypadki naruszenia zabezpieczeń produktów i usług. Bezpośrednio po uzyskaniu wiarygodnego raportu o incydencie zespół ten bada jego zakres, przyczynę i środki naprawcze. Jeśli dane zdarzenie dotyczy Twoich zasobów, firma Microsoft poinformowała administratorów dzierżawy usługi Azure Information Protection za pośrednictwem poczty e-mail, korzystając z adresu podanego podczas rejestrowania subskrypcji.

W przypadku naruszenia zabezpieczeń najlepsze działanie, które może podjąć użytkownik lub firma Microsoft, jest zależne od zakresu naruszenia. Firma Microsoft zapewnia wsparcie w tym procesie. Poniższa tabela przedstawia typowe sytuacje i prawdopodobne reakcje, choć dokładna reakcja jest zależna od informacji uzyskanych w trakcie badania.

|Opis zdarzenia|Prawdopodobna reakcja|
|------------------------|-------------------|
|Przeciek klucza dzierżawy.|Wymień klucz dzierżawy. Zobacz sekcję [Wymiana klucza dzierżawy](#rekey-your-tenant-key).|
|Nieautoryzowana osoba lub złośliwe oprogramowanie uzyskało prawa do korzystania z klucza dzierżawy, ale nie nastąpił przeciek samego klucza.|Wymiana klucza dzierżawy nie jest w tym przypadku pomocna, a problem wymaga analizy przyczyny. Jeśli za uzyskanie dostępu przez nieautoryzowaną osobę odpowiada proces lub błąd oprogramowania, sytuację należy rozwiązać.|
|Odkryto lukę w zabezpieczeniach obecnej generacji technologii sprzętowych modułów zabezpieczeń.|Firma Microsoft musi zaktualizować sprzętowe moduły zabezpieczeń. W przypadku podejrzeń, że spowodowała ujawnienie kluczy firmy Microsoft będą poinstruować wszystkich klientów wymiany kluczy dzierżawy.|
|Odkryto lukę w zabezpieczeniach algorytmu RSA lub długości klucza albo ataki siłowe stały się wykonalne.|Firma Microsoft musi zaktualizować usługę Azure Key Vault lub Azure Information Protection, obsługę nowych algorytmów i dłuższych kluczy o większej odporności i poinstruować wszystkich klientów, aby wymienić klucz dzierżawy.|


