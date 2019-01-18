---
title: Migrowanie etykiety usługi Azure Information Protection do pakietu Office 365 Centrum zabezpieczeń i zgodności — AIP
description: Migrowanie etykiety usługi Azure Information Protection do Centrum zgodności i zabezpieczeń usługi Office 365 dla klienta, który obsługuje jednolitego etykietowania.
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 01/17/20198
ms.topic: article
ms.service: information-protection
ms.reviewer: demizets
ms.suite: ems
ms.openlocfilehash: 221b503fa3621e51c4822a6ad5a6d08fae4f1bad
ms.sourcegitcommit: 8dec864bf25c7da62b9e0f628f1bf673c81c15ae
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/16/2019
ms.locfileid: "54356015"
---
# <a name="how-to-migrate-azure-information-protection-labels-to-the-office-365-security--compliance-center"></a>Jak przeprowadzić migrację etykiety usługi Azure Information Protection do Centrum zgodności i zabezpieczeń usługi Office 365

>*Dotyczy: [Usługa Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection), [usługi Office 365](https://download.microsoft.com/download/E/C/F/ECF42E71-4EC0-48FF-AA00-577AC14D5B5C/Azure_Information_Protection_licensing_datasheet_EN-US.pdf)*

> [!IMPORTANT]
> Ta funkcja jest dostępna w wersji zapoznawczej i migruje dzierżawy na nową platformę, która jest również dostępna w wersji zapoznawczej. Nie można cofnąć migrację. Nowa platforma obsługuje ujednoliconego etykietowania, tak aby etykiety, które umożliwiają tworzenie i zarządzanie nimi może służyć przez wielu klientów i usług.

Migrowanie etykiet, jeśli chcesz można było korzystać z nich w Office 365 Centrum zabezpieczeń i zgodności, gdzie mogą być publikowane i następnie pobrane przez [klientów, którzy obsługują ujednoliconego etykietowania](#clients-that-support-unified-labeling). Klient usługi Azure Information Protection w dalszym ciągu pobierania etykiety z ich zasadami usługi Azure Information Protection w witrynie Azure portal. 

Po przeprowadzeniu migracji etykiet, następnie można wprowadzić zmiany do nich w portalu Azure lub Office 365 Centrum zabezpieczeń i zgodności, a odpowiednich klientów będą pobierać tę samą zmianę.

### <a name="important-information-about-administrative-roles"></a>Ważne informacje o rolach administracyjnych

[Ról usługi Azure AD](/azure/active-directory/active-directory-assign-admin-roles-azure-portal) z **Administrator zabezpieczeń** i **Administrator usługi Information Protection** nie są obsługiwane przez ujednolicona platforma etykietowania. Jeśli tych ról administracyjnych są używane w Twojej organizacji, przed przeprowadzeniem migracji etykiety, należy dodać użytkowników, którzy mają te role do **Administrator do spraw zgodności** lub **Zarządzanie organizacją** roli grupy zabezpieczeń usługi Office 365 i Centrum zgodności. Alternatywnie, można utworzyć nową grupę ról dla tych użytkowników i dodać albo **zarządzania przechowywania** lub **Konfiguracja organizacji** ról do tej grupy. Aby uzyskać instrukcje, zobacz [daje użytkownikom dostęp do Centrum zgodności i zabezpieczeń usługi Office 365](https://docs.microsoft.com/office365/securitycompliance/grant-access-to-the-security-and-compliance-center).

Jeśli nie udzielisz tych użytkowników dostępu do Centrum zabezpieczeń i zgodności przy użyciu jednej z tych konfiguracji, sposób utracą dostęp do etykiet i zasady w witrynie Azure portal po migracji etykiet.

Administratorzy globalni dla dzierżawy mogą w dalszym ciągu Zarządzaj etykiety i zasady w zarówno witryny Azure portal i Centrum zabezpieczeń i zgodności po etykiety są migrowane.


## <a name="considerations-for-unified-labels"></a>Zagadnienia dotyczące ujednoliconego etykiety

Przed przeprowadzeniem migracji etykiet, upewnij się, że masz świadomość następujących zmian i okoliczności:

- Nie wszyscy klienci nie obsługują obecnie ujednoliconego etykiety. Upewnij się, że masz [obsługiwani klienci](#clients-that-support-unified-labeling) i przygotować się do administrowania w zarówno witryny Azure portal (dla klientów, którzy nie obsługują ujednoliconego etykiety) oraz Centrum zabezpieczeń i zgodności (dla klienta, który obsługuje jednolitego etykiety ).

- Jeśli jesteś w trakcie definiowania i konfigurowania etykiet, które chcesz użyć, zaleca się ukończyć ten proces, za pomocą witryny Azure portal, a następnie przeprowadzić migrację etykiet. Ta strategia pozwala na uniknięcie duplikowania etykiety podczas procesu migracji, że konieczne będzie można edytować w Centrum zabezpieczeń i zgodności.

- Zasady, w tym ustawień zasad i kto ma dostęp do nich (zasad o określonym zakresie), a wszystkie zaawansowane ustawienia klienta nie są migrowane. Aby te zmiany, które nie są migrowane należy skonfigurować odpowiednie opcje w Centrum zabezpieczeń i zgodności, po etykiety są migrowane.
    
    Spójniejsze środowisko pracy użytkownika firma Microsoft zaleca publikowania tej samej etykiety w tych samych zakresów w Centrum zabezpieczeń i zgodności.

- Nie wszystkie ustawienia z migrowanych etykiety są obsługiwane przez Centrum zabezpieczeń i zgodności. Skorzystaj z tabeli w [etykiety ustawienia, które nie są obsługiwane w Centrum zabezpieczeń i zgodności](#label-settings-that-are-not-supported-in-the-security--compliance-center) sekcji, aby pomóc w zidentyfikowaniu ustawienia, które nie są obsługiwane przez Centrum zabezpieczeń i zgodności.

- Szablony ochrony:
    
    - Szablony, które używają klucza oparta na chmurze i które są częścią konfiguracji etykiety również zostały zmigrowane z etykietą. Inne szablony ochrony nie są migrowane. 
    
    - Po przeprowadzeniu migracji etykiety za pomocą ustawień ochrony opartej na chmurze wynikowy zakres szablonu ochrony jest objętych zakresem, który jest zdefiniowany w witrynie Azure portal (lub za pomocą modułu AADRM programu PowerShell) i zakres, który jest zdefiniowany w zabezpieczeniach & Centrum zgodności. 

- Podczas migracji etykiet, pojawi się migracji wyświetlanie wyników, czy etykieta była **utworzone**, **zaktualizowane**, lub **zmieniona** z powodu dublowania:

    - Po utworzeniu etykiety, należy opublikować ją w Centrum zabezpieczeń i zgodności, aby był dostępny do aplikacji i usług.
    
    - Jeśli etykieta została zmieniona, możesz następnie edytować go, co można zrobić w bezpieczeństwo & Centrum zgodności lub witryny Azure portal. 

- Dla każdej etykiety witryny Azure portal wyświetla tylko nazwa wyświetlana etykiety, który można edytować. Centrum zabezpieczeń i zgodności zawiera zarówno ta nazwa wyświetlana dla etykiety, jak i nazwę etykiety. Nazwa etykiety jest nazwa początkowego, który określiłeś, podczas pierwszego tworzenia etykiety i ta właściwość jest używana przez usługę zaplecza w celach identyfikacyjnych.

- Wszelkie zlokalizowanych ciągów dla etykiety nie są migrowane. Należy zdefiniować nowe zlokalizowanych ciągów dla migrowanych etykiet w Centrum zabezpieczeń i zgodności.

- Po migracji gdy edytujesz migrowanych etykiety w witrynie Azure portal, tę samą zmianę jest automatycznie odzwierciedlane w Centrum zabezpieczeń i zgodności. Jednak podczas edycji migrowanych etykiety w Centrum zabezpieczeń i zgodności, wróć do witryny Azure portal **usługi Azure Information Protection — Unified etykietowania** bloku, a następnie wybierz **Publikuj**. To dodatkowe działania jest wymagane w przypadku klientów usługi Azure Information Protection zmian etykiety.

### <a name="label-settings-that-are-not-supported-in-the-security--compliance-center"></a>Ustawienia etykiet, które nie są obsługiwane w Centrum zabezpieczeń i zgodności

Użyj poniższej tabeli, aby zidentyfikować ustawienia konfiguracji, które migrowanych etykiety nie są obsługiwane przez ujednolicony klientów etykietowania lub są obsługiwane z ograniczeniami. Aby uniknąć nieporozumień, zaleca się, nie Konfiguruj ustawienia, które nie mają wpływu na ujednoliconego etykietowania klientów.

Klienci usługi Azure Information Protection można użyć tych ustawień etykiety bez problemów, ponieważ kontynuują próby pobierania etykiety w witrynie Azure portal.

|Konfiguracja etykiet|Obsługiwane przez ujednolicony etykietowania klientów|Wyklucz z edycji w Centrum zabezpieczeń i zgodności|
|-------------------|---------------------------------------------|-------------------------|
|Stan włączony lub wyłączony<br /><br />Uwagi: Nie są synchronizowane z Centrum zabezpieczeń i zgodności |Nie dotyczy|Nie dotyczy|
|Kolor etykiety: Wybierz z listy lub określ przy użyciu kodu RGB<br /><br />Uwagi: Kolory nie są obsługiwane przez Centrum zabezpieczeń i zgodności |Nie dotyczy|Nie dotyczy|
|Ochrona oparta na chmurze lub na podstawie HYOK ochrony za pomocą wstępnie zdefiniowany szablon |Nie|Tak|
|Ochrona oparta na chmurze, przy użyciu uprawnienia zdefiniowane przez użytkownika w programie Word, Excel i PowerPoint |Nie|Tak|
|Ochrona oparta na funkcji HYOK, przy użyciu uprawnienia zdefiniowane przez użytkownika w programie Outlook dla nie przesyłaj dalej |Nie|Tak|
|Usuwanie ochrony |Nie|Tak|
|Oznaczenia wizualne (nagłówek, stopka, znak wodny): Niestandardowe czcionek i kolorów czcionki niestandardowe przez kod RGB|Nie|Zalecane, jeśli w przypadku używania zmiennych<br /><br />-Na klientach zmienne są wyświetlane jako tekst, zamiast wyświetlania wartości dynamiczne|
|Oznaczenia wizualne dla aplikacji|Nie|Zalecane, jeśli w przypadku używania zmiennych<br /><br />-Na klientach zmienne są wyświetlane jako tekst, zamiast wyświetlania wartości dynamiczne|
|Warunki i skojarzone ustawienia <br /><br />Uwagi: Obejmuje automatyczne i zalecane etykietowanie i ich etykietek narzędzi|Nie dotyczy|Nie|


## <a name="to-migrate-azure-information-protection-labels"></a>Aby przeprowadzić migrację etykiety usługi Azure Information Protection

Użyj poniższych instrukcji migracji dzierżawy i etykiet usługi Azure Information Protection do użycia nowego etykietowania ujednoliconego przechowywania.

Musi być administratorem globalnym, aby migrować etykiet.

1. Jeśli jeszcze tego nie zrobiono, Otwórz nowe okno przeglądarki i [Zaloguj się do witryny Azure portal](configure-policy.md#signing-in-to-the-azure-portal). Następnie przejdź do bloku **Azure Information Protection**.
    
    Na przykład w menu Centrum kliknij pozycję **wszystkich usług** i zacznij wpisywać **informacji** w polu filtru. Wybierz pozycję **Azure Information Protection**.

2. Z **Zarządzaj** opcji menu, wybierz opcję **Unified etykietowania (wersja zapoznawcza)**.

3. Na **usługi Azure Information Protection — Unified etykietowania** bloku wybierz **Aktywuj** i postępuj zgodnie z wyświetlanymi instrukcjami.

Dla etykiet, które pomyślnie przeprowadzono migrację, ich można teraz używać przez [klientów, którzy obsługują ujednoliconego etykietowania](#clients-that-support-unified-labeling). Jednakże należy najpierw go opublikować te etykiety w Centrum zabezpieczeń i zgodności.

> [!IMPORTANT]
> Jeśli edytujesz etykiet poza portalem Azure dla klientów usługi Azure Information Protection, wróć do tego **usługi Azure Information Protection — Unified etykietowania** bloku, a następnie wybierz **Publikuj**.

### <a name="clients-that-support-unified-labeling"></a>Klienci, którzy obsługują ujednoliconego etykietowania

Klienci, którzy obecnie obsługuje etykietowania ujednoliconego obejmują:

- [Usługi Azure Information Protection unified etykietowania klienta Windows](./rms-client/unifiedlabelingclient-version-release-history.md) — w wersji zapoznawczej

- Aplikacje z programu osób znających zagadnienia Office. Aby uzyskać więcej informacji, zobacz [których ta funkcja jest dostępna już dzisiaj?](https://support.office.com/article/2f96e7cd-d5a4-403b-8bd7-4cc636bae0f9?ad=US#bkmk_whereavailable) sekcji w dokumentacji pakietu Office.
    
- Klienci od dostawców oprogramowania i deweloperów, które używają [MIP SDK](https://docs.microsoft.com/azure/information-protection/develop/mip/mip-sdk-reference).


## <a name="next-steps"></a>Następne kroki

Aby uzyskać więcej informacji na temat migrowanych etykiet, które można teraz konfigurować i opublikowane w Centrum zgodności i zabezpieczeń usługi Office 365, zobacz [Przegląd etykiety ważności](/Office365/SecurityCompliance/sensitivity-labels).

Aby przeczytaj wpis w blogu anonsu: [Ogłoszenie dostępności unified etykietowania management w Centrum zabezpieczeń i zgodności](https://techcommunity.microsoft.com/t5/Security-Privacy-and-Compliance/Announcing-the-availability-of-unified-labeling-management-in/ba-p/262492).