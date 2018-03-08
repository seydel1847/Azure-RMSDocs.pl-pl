---
title: "Zarządzane przez klienta w Efektywnych operacje cyklu życia klucza dzierżawy"
description: "Informacji na temat operacji cyklu życia, które są istotne, jeśli zarządzasz kluczem dzierżawy usługi Azure Information Protection (Przynieś własny klucz lub BYOK, scenariusz)."
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 03/07/2018
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: c5b19c59-812d-420c-9c54-d9776309636c
ms.reviewer: esaggese
ms.suite: ems
ms.openlocfilehash: 70d34253300e2bef442cdd7d8cf2c06ac8a9fd88
ms.sourcegitcommit: dd53f3dc2ea2456ab512e3a541d251924018444e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/08/2018
---
# <a name="customer-managed-tenant-key-life-cycle-operations"></a>Zarządzany przez klienta: Operacje cyklu życia klucza dzierżawy

>*Dotyczy: Azure Information Protection, Office 365*

Jeśli zarządzasz kluczem dzierżawy usługi Azure Information Protection (Przynieś własny klucz lub BYOK, scenariusz), użyj poniższych sekcji, aby uzyskać więcej informacji na temat operacji cyklu życia związanych z tą topologią.

## <a name="revoke-your-tenant-key"></a>Odwołanie klucza dzierżawy
W usłudze Azure Key Vault można zmienić uprawnienia dotyczące magazynu kluczy, który zawiera klucz dzierżawy usługi Azure Information Protection, aby usługa Azure Rights Management nie mogła już uzyskać dostępu do tego klucza. Niemniej po wykonaniu tej czynności nikt nie będzie w stanie otworzyć dokumentów i wiadomości e-mail, które zostały wcześniej zabezpieczone przez usługę Azure Rights Management.

Po anulowaniu subskrypcji usługi Azure Information Protection usługa ta wstrzymuje korzystanie z klucza dzierżawy, co nie wymaga żadnej akcji ze strony użytkownika.

## <a name="rekey-your-tenant-key"></a>Wymiana klucza dzierżawy
Wymiana klucza jest także określana jako uaktualnianie klucza. Po wykonaniu tej operacji usługi Azure Information Protection przestanie używać istniejącego klucza dzierżawy do ochrony dokumentów i wiadomości e-mail i rozpoczyna się użyć innego klucza. Zasady i szablony są natychmiast ponownie podpisane, ale tego przejścia jest stopniowego dla istniejących klientów i usług przy użyciu usługi Azure Information Protection. Dlatego przez pewien czas część nowej zawartości nadal ma być chroniona przez stary klucz dzierżawy.

Do ponownego generowania kluczy należy skonfigurować obiekt klucza dzierżawy i określ alternatywny klucz do użycia. Następnie, wcześniej używany klucz automatycznie jest oznaczony jako zarchiwizowane usługi Azure Information Protection. Ta konfiguracja zapewnia tej zawartości, która była chroniona za pomocą tego klucza pozostaną dostępne.

Przykłady gdy może być konieczne ponowne generowanie kluczy dla usługi Azure Information Protection:

- Firma została podzielona na dwie lub więcej firm. Po wymianie klucza dzierżawy nowa firma nie będzie miała dostępu do nowej zawartości publikowanej przez pracowników. Mogą oni uzyskać dostęp do starej zawartości, jeśli dysponują kopią starego klucza dzierżawy.

- Chcesz przenieść od jednego topologii zarządzania kluczami do innego. 

- Uważasz, że zostanie naruszone bezpieczeństwo kopii głównej klucza dzierżawy (będącej w Twoim posiadaniu).

Aby ponowne tworzenie klucza do innego klucza, którą zarządzasz, musisz utworzyć nowy klucz w usłudze Azure Key Vault lub użyć innego klucza, który jest już w usłudze Azure Key Vault. Następnie wykonaj te same procedury, które zostało do zaimplementowania BYOK usługi Azure Information Protection.

1. Tylko wtedy, gdy nowy klucz znajduje się w innym magazynie kluczy do tego, już używasz usługi Azure Information Protection: autoryzowanie usługi Azure Information Protection do używania magazynu kluczy, za pomocą [Set-AzureRmKeyVaultAccessPolicy](/powershell/module/azurerm.keyvault/set-azurermkeyvaultaccesspolicy) polecenia cmdlet.

2. Jeśli usługi Azure Information Protection już nie ma informacji dotyczących klucz chcesz używać, uruchom [AadrmKeyVaultKey użyj](/powershell/module/aadrm/use-aadrmkeyvaultkey) polecenia cmdlet.

3. Konfigurowanie obiektu klucza dzierżawy, za pomocą opcji Uruchom [AadrmKeyProperties zestaw](/powershell/module/aadrm/set-aadrmkeyproperties) polecenia cmdlet.

Aby uzyskać więcej informacji na temat każdego z następujących czynności:

- Aby ponowne tworzenie klucza do innego klucza, którymi można zarządzać, zobacz [BYOK wdrażanie klucza dzierżawy usługi Azure Information Protection](../plan-design/plan-implement-tenant-key.md#implementing-byok-for-your-azure-information-protection-tenant-key).

- Ponowne tworzenie klucza, zmiana z kluczem programu Microsoft zarządza dla Ciebie, zobacz [ponowne tworzenie klucza z kluczem dzierżawy](operations-microsoft-managed-tenant-key.md#rekey-your-tenant-key) sekcji operacjach zarządzany przez firmę Microsoft.

## <a name="backup-and-recover-your-tenant-key"></a>Tworzenie kopii zapasowej i odzyskiwanie klucza dzierżawy
Ponieważ użytkownik zarządza kluczem dzierżawy, jest odpowiedzialny za tworzenie kopii zapasowej klucza, który używa usługi Azure Information Protection. 

Jeśli klucz dzierżawy lokalnie, jest generowany w module HSM firmy Thales: Aby utworzyć kopię zapasową klucza, należy utworzyć kopię zapasową tokenami plik klucza, pliku środowiska zabezpieczeń oraz kart administratora. Podczas przenoszenia klucza do usługi Azure Key Vault, usługa zapisuje tokenami pliku klucza w celu ochrony przed awarią węzły usługi. Ten plik jest powiązany ze środowiskiem zabezpieczeń dla konkretnego regionu lub wystąpienia platformy Azure. Jednak nie należy traktować tego tokenami plik klucza do pełnej kopii zapasowej. Na przykład, jeśli kiedykolwiek zajdzie zwykły tekst kopię klucza, aby używać poza HSM firmy Thales, usługi Azure Key Vault nie można pobrać go, ponieważ ma ona tylko nieodwracalny kopii.

Usługa Azure Key Vault ma [kopii zapasowej polecenia cmdlet](/powershell/module/azurerm.keyvault/Backup-AzureKeyVaultKey) której można utworzyć kopię zapasową klucza ją pobrać i przechowywanie ich w pliku. Ponieważ pobieranej zawartości jest zaszyfrowany, nie można używać poza usługą Azure Key Vault. 

## <a name="export-your-tenant-key"></a>Eksport klucza dzierżawy
W przypadku korzystania z rozwiązania BYOK nie można wyeksportować klucza dzierżawy ani z usługi Azure Key Vault, ani z usługi Azure Information Protection. Przywrócenie kopii klucza znajdującej się w usłudze Azure Key Vault nie jest możliwe. 

## <a name="respond-to-a-breach"></a>Reakcja na naruszenie zabezpieczeń
Żaden system zabezpieczeń, niezależnie od jego siły, nie jest kompletny bez procedur reakcji na naruszenie zabezpieczeń. Klucz dzierżawy może zostać naruszony lub skradziony. Nawet wtedy, gdy jest on chroniony dobrze, mogą występować luki w obecnej generacji technologii klucza i algorytmy i długości kluczy.

Firma Microsoft ma dedykowany zespół, który reaguje na przypadki naruszenia zabezpieczeń produktów i usług. Bezpośrednio po uzyskaniu wiarygodnego raportu o incydencie zespół ten bada jego zakres, przyczynę i środki naprawcze. Jeśli to zdarzenie dotyczy Twoich zasobów, firma Microsoft poinformowała administratorami dzierżawy usługi Azure Information Protection pocztą e-mail za pomocą adresu podanego podczas subskrybowania.

W przypadku naruszenia zabezpieczeń najlepsze działanie, które może podjąć użytkownik lub firma Microsoft, jest zależne od zakresu naruszenia. Firma Microsoft zapewnia wsparcie w tym procesie. Poniższa tabela przedstawia typowe sytuacje i prawdopodobne reakcje, choć dokładna reakcja jest zależna od informacji uzyskanych w trakcie badania.

|Opis zdarzenia|Prawdopodobna reakcja|
|------------------------|-------------------|
|Przeciek klucza dzierżawy.|Wymień klucz dzierżawy. Zobacz sekcję [Wymiana klucza dzierżawy](#rekey-your-tenant-key).|
|Nieautoryzowana osoba lub złośliwe oprogramowanie uzyskało prawa do korzystania z klucza dzierżawy, ale nie nastąpił przeciek samego klucza.|Wymiana klucza dzierżawy nie jest w tym przypadku pomocna, a problem wymaga analizy przyczyny. Jeśli za uzyskanie dostępu przez nieautoryzowaną osobę odpowiada proces lub błąd oprogramowania, sytuację należy rozwiązać.|
|Odkryto lukę w zabezpieczeniach obecnej generacji technologii sprzętowych modułów zabezpieczeń.|Firma Microsoft musi zaktualizować sprzętowe moduły zabezpieczeń. W przypadku podejrzeń, że usterka spowodowała ujawnienie kluczy, Microsoft wyśle instrukcje do wszystkich klientów do ponowne tworzenie klucza kluczy dzierżawy.|
|Odkryto lukę w zabezpieczeniach algorytmu RSA lub długości klucza albo ataki siłowe stały się wykonalne.|Firma Microsoft musi zaktualizować magazynu kluczy Azure lub usługi Azure Information Protection do obsługi nowych algorytmów i długości kluczy dłużej, które są odporne i poinstruować wszystkich klientów do ponowne tworzenie klucza swój klucz dzierżawy.|

[!INCLUDE[Commenting house rules](../includes/houserules.md)]

