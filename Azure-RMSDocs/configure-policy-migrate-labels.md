---
title: Migrowanie etykiety usługi Azure Information Protection do Centrum zgodności i zabezpieczeń usługi Office 365
description: Migrowanie etykiety usługi Azure Information Protection do Centrum zgodności i zabezpieczeń usługi Office 365 dla klienta, który obsługuje jednolitego etykietowania.
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 09/28/2018
ms.topic: article
ms.service: information-protection
ms.reviewer: demizets
ms.suite: ems
ms.openlocfilehash: 64063af186f01a5829b7aa668260928e3b13656d
ms.sourcegitcommit: 304702a3f2f2ab2b32493c4aedeb5ee8424b925c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/27/2018
ms.locfileid: "47415013"
---
# <a name="how-to-migrate-azure-information-protection-labels-to-the-office-365-security--compliance-center"></a>Jak przeprowadzić migrację etykiety usługi Azure Information Protection do Centrum zgodności i zabezpieczeń usługi Office 365

>*Dotyczy: [usługi Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection), [usługi Office 365](http://download.microsoft.com/download/E/C/F/ECF42E71-4EC0-48FF-AA00-577AC14D5B5C/Azure_Information_Protection_licensing_datasheet_EN-US.pdf)*

> [!IMPORTANT]
> Ta funkcja jest dostępna w wersji zapoznawczej i migruje dzierżawy na nową platformę, która jest również dostępna w wersji zapoznawczej. Nie można cofnąć migrację. Nowa platforma obsługuje ujednoliconego etykietowania, tak aby etykiety, które umożliwiają tworzenie i zarządzanie nimi może służyć przez wielu klientów i usług.

Migrowanie etykiet, jeśli chcesz można było korzystać z nich w Office 365 Centrum zabezpieczeń i zgodności, gdzie mogą być publikowane i następnie pobrane przez [klientów, którzy obsługują ujednoliconego etykietowania](#clients-that-support-unified-labeling). Klient usługi Azure Information Protection w dalszym ciągu pobierania etykiety z ich zasadami usługi Azure Information Protection w witrynie Azure portal. 

Po przeprowadzeniu migracji etykiet, następnie można wprowadzić zmiany do nich w portalu Azure lub Office 365 Centrum zabezpieczeń i zgodności, a odpowiednich klientów będą pobierać tę samą zmianę.

## <a name="considerations-for-unified-labels"></a>Zagadnienia dotyczące ujednoliconego etykiety

Przed przeprowadzeniem migracji etykiet, upewnij się, że masz świadomość następujących zmian i okoliczności:

- Nie wszyscy klienci nie obsługują obecnie ujednoliconego etykiety. Upewnij się, że masz [obsługiwani klienci](#clients-that-support-unified-labeling) i przygotować się do administrowania w zarówno witryny Azure portal (dla klientów, którzy nie obsługują ujednoliconego etykiety) oraz Centrum zabezpieczeń i zgodności (dla klienta, który obsługuje jednolitego etykiety ).

- Jeśli jesteś w trakcie definiowania i konfigurowania etykiet, które chcesz użyć, zaleca się ukończyć ten proces, za pomocą witryny Azure portal, a następnie przeprowadzić migrację etykiet. Ta strategia pozwala na uniknięcie duplikowania etykiety podczas procesu migracji, że konieczne będzie można edytować w Centrum zabezpieczeń i zgodności.

- Zasady, w tym ustawień zasad i kto ma dostęp do nich (zasad o określonym zakresie), a wszystkie zaawansowane ustawienia klienta nie są migrowane. Aby te zmiany, które nie są migrowane należy skonfigurować odpowiednie opcje w Centrum zabezpieczeń i zgodności, po etykiety są migrowane.
    
    Spójniejsze środowisko pracy użytkownika firma Microsoft zaleca publikowania tej samej etykiety w tych samych zakresów w Centrum zabezpieczeń i zgodności.

- Nie wszystkie ustawienia z migrowanych etykiety są obsługiwane przez Centrum zabezpieczeń i zgodności. Skorzystaj z tabeli w [etykiety ustawienia, które nie są obsługiwane w Centrum zabezpieczeń i zgodności](#label-settings-that-are-not-supported-in-the-security--compliance-center) sekcji, aby pomóc w zidentyfikowaniu tych ustawień i tego, czy należy wyłączyć migrowanych etykiety z publikacji w zabezpieczeniach & Centrum zgodności.

- Szablony ochrony:
    
    - Szablony, które używają klucza oparta na chmurze i które są częścią konfiguracji etykiety również zostały zmigrowane z etykietą. Inne szablony ochrony nie są migrowane. 
    
    - Po przeprowadzeniu migracji etykiety za pomocą ustawień ochrony opartej na chmurze wynikowy zakres szablonu ochrony jest objętych zakresem, który jest zdefiniowany w witrynie Azure portal (lub przy użyciu modułu ADDRM PowerShell) i zakres, który jest zdefiniowany w zabezpieczeniach & Centrum zgodności. 

- Podczas migracji etykiet, pojawi się migracji wyświetlanie wyników, czy etykieta była **utworzone**, **zaktualizowane**, lub **zmieniona** z powodu dublowania:

    - Po utworzeniu etykiety, należy opublikować ją w Centrum zabezpieczeń i zgodności, aby był dostępny do aplikacji i usług.
    
    - Jeśli etykieta została zmieniona, możesz następnie edytować go, co można zrobić w bezpieczeństwo & Centrum zgodności lub witryny Azure portal. 

- Dla każdej etykiety witryny Azure portal wyświetla tylko nazwa wyświetlana etykiety, który można edytować. Centrum zabezpieczeń i zgodności zawiera zarówno ta nazwa wyświetlana dla etykiety, jak i nazwę etykiety. Nazwa etykiety jest nazwa początkowego, który określiłeś, podczas pierwszego tworzenia etykiety i ta właściwość jest używana przez usługę zaplecza w celach identyfikacyjnych.

- Wszelkie zlokalizowanych ciągów dla etykiety nie są migrowane. Należy zdefiniować nowe zlokalizowanych ciągów dla migrowanych etykiet w Centrum zabezpieczeń i zgodności.

- Po migracji gdy edytujesz migrowanych etykiety w witrynie Azure portal, tę samą zmianę jest automatycznie odzwierciedlane w Centrum zabezpieczeń i zgodności. Jednak podczas edycji migrowanych etykiety w Centrum zabezpieczeń i zgodności, następnie należy zaktualizować etykiety w witrynie Azure portal dla etykiety wczytać zmiany. Na przykład edytować **Dodaj notatki przeznaczone dla administratorów** polu na **etykiety** bloku. 

- Ujednolicone etykietowania nadal wprowadza dzierżawcom. Jeśli jeszcze nie jest obsługiwana dla Twojej dzierżawy, migracji nie powiedzie się i bez problemu zmieniała cofnąć wszystkie zmiany. Dopóki nie jest obsługiwany dla wszystkich dzierżaw, należy użyć specjalnego linku dostępu możliwość migracji dzierżawy i etykiet do. Ten link znajduje się w instrukcji.

### <a name="label-settings-that-are-not-supported-in-the-security--compliance-center"></a>Ustawienia etykiet, które nie są obsługiwane w Centrum zabezpieczeń i zgodności

Skorzystaj z poniższej tabeli, aby zidentyfikować ustawienia konfiguracji, które migrowanych etykiety nie są obsługiwane dla klientów korzystających z tych etykiet i tego, czy należy edytować i publikowanie migrowanych etykiety w Centrum zabezpieczeń i zgodności. W przypadku publikowania etykiety, które są identyfikowane, które mają być wykluczone z publikacji bez etykiet są wyświetlane dla klientów, którzy obsługują ujednoliconego etykietowania.

Klienci usługi Azure Information Protection można użyć tych ustawień etykiety bez problemów, ponieważ kontynuują próby pobierania etykiety w witrynie Azure portal.

|Konfiguracja etykiet|Obsługiwane w Centrum zabezpieczeń i zgodności|Wyklucz z edycji i publikowania w Centrum zabezpieczeń i zgodności|
|-------------------|---------------------------------------------|-------------------------|
|Stan włączony lub wyłączony<br /><br />Uwagi: Nie jest synchronizowany Centrum zabezpieczeń i zgodności |Nie dotyczy|Nie dotyczy|
|Kolor etykiety: Wybierz z listy lub określ przy użyciu kodu RGB<br /><br />Uwagi: Kolory nie są obsługiwane przez Centrum zabezpieczeń i zgodności |Nie dotyczy|Nie dotyczy|
|Ochrona oparta na chmurze lub na podstawie HYOK ochrony za pomocą wstępnie zdefiniowany szablon |Nie|Tak|
|Ochrona oparta na chmurze, przy użyciu uprawnienia zdefiniowane przez użytkownika w programie Word, Excel i PowerPoint |Nie|Tak|
|Ochrona oparta na funkcji HYOK, przy użyciu uprawnienia zdefiniowane przez użytkownika w programie Outlook dla nie przesyłaj dalej |Nie|Tak|
|Usuwanie ochrony |Nie|Tak|
|Oznaczenia wizualne (nagłówek, stopka, znak wodny): niestandardowe czcionki i niestandardowej czcionki kolorów RGB kodu|Nie|Zalecane, jeśli w przypadku używania zmiennych<br /><br />-Na klientach zmienne są wyświetlane jako tekst, zamiast wyświetlania wartości dynamiczne|
|Oznaczenia wizualne dla aplikacji|Nie|Zalecane, jeśli w przypadku używania zmiennych<br /><br />-Na klientach zmienne są wyświetlane jako tekst, zamiast wyświetlania wartości dynamiczne|
|Warunki i skojarzone ustawienia <br /><br />Uwagi: Obejmuje automatyczne i zalecane etykietowanie i ich etykietek narzędzi|Nie dotyczy|Nie|


## <a name="to-migrate-azure-information-protection-labels"></a>Aby przeprowadzić migrację etykiety usługi Azure Information Protection

> [!IMPORTANT]
> Etykiet nie są migrowane, dopóki nie została potwierdzona, edytować i opublikować etykiety czułości w Centrum zgodności i zabezpieczeń usługi Office 365. Czułość etykiety coraz częściej wprowadzane do dzierżawy usługi Office 365, ale nie są jeszcze dostępne dla wszystkich dzierżaw.
> 
> Aby sprawdzić: Z pakietu Office 365 Centrum zabezpieczeń i zgodności, przejdź do **klasyfikacje** > **etykiety**i sprawdzić, czy masz **czułości** kartę. Jeśli nie ma na tej karcie, dzierżawy nie jest jeszcze gotowy etykiet ważność i nie należy zmigrować etykiet usługi Azure Information Protection, w tym momencie.

Po potwierdzeniu, że dzierżawa usługi obsługuje etykiety ważności w Centrum zabezpieczeń i zgodności, wykonaj następujące instrukcje do migracji dzierżawy i etykiet usługi Azure Information Protection.

1. Otwórz nowe okno przeglądarki i zaloguj się do witryny Azure portal, korzystając z następującego linku: https://portal.azure.com/?ActivateMigration=true#blade/Microsoft_Azure_InformationProtection/DataClassGroupEditBlade/migrationActivationBlade 

2. Na **usługi Azure Information Protection — Unified etykietowania** bloku wybierz **Aktywuj** i postępuj zgodnie z wyświetlanymi instrukcjami.

Dla etykiet, które pomyślnie przeprowadzić migrację, można teraz nimi przez [klientów, którzy obsługują ujednoliconego etykietowania](#clients-that-support-unified-labeling) gdy etykiety są publikowane w Centrum zabezpieczeń i zgodności.


### <a name="clients-that-support-unified-labeling"></a>Klienci, którzy obsługują ujednoliconego etykietowania

Klienci, którzy obecnie obsługuje etykietowania ujednoliconego obejmują:

- Aplikacje z programu osób znających zagadnienia Office. Aby uzyskać więcej informacji, zobacz [których ta funkcja jest dostępna już dzisiaj?](https://support.office.com/article/2f96e7cd-d5a4-403b-8bd7-4cc636bae0f9?ad=US#bkmk_whereavailable) sekcji w dokumentacji pakietu Office.
    
- Klienci od dostawców oprogramowania i deweloperów, które używają [MIP SDK](https://docs.microsoft.com/azure/information-protection/develop/mip/mip-sdk-reference).


## <a name="next-steps"></a>Następne kroki

Aby uzyskać więcej informacji o konfigurowaniu etykiet zmigrowane w Centrum zgodności i zabezpieczeń usługi Office 365, zobacz w blogu, [informuje o dostępności unified etykietowania management w Centrum zabezpieczeń i zgodności](https://techcommunity.microsoft.com/t5/Security-Privacy-and-Compliance/Announcing-the-availability-of-unified-labeling-management-in/ba-p/262492) .