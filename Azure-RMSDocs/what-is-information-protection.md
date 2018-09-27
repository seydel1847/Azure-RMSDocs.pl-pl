---
title: Co to jest Azure Information Protection?
description: Omówienie usługi Azure Information Protection.
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 09/27/2018
ms.topic: conceptual
ms.service: information-protection
ms.assetid: cd8a88e2-3555-4be2-9637-3cdee992f2c8
ms.openlocfilehash: 2d2996d89e7f8574d1dba7544474c18ad28c0de9
ms.sourcegitcommit: 4bc807177cf6c284f673cea667b6086121d69231
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/26/2018
ms.locfileid: "47233766"
---
# <a name="what-is-azure-information-protection"></a>Co to jest Azure Information Protection?

>*Dotyczy: [usługi Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection)*

Usługa Azure Information Protection (czasami określane jako AIP) to rozwiązanie chmurowe, które ułatwia klasyfikowanie i ewentualnie chronić swoje dokumenty i wiadomości e-mail, stosując etykiety. Etykiety mogą być stosowane automatycznie przez administratorów definiujących reguły i warunki, ręcznie przez użytkowników lub kombinacji, w którym użytkownicy otrzymują wówczas zalecenia. 

Na poniższej ilustracji przedstawiono przykład usługi Azure Information Protection działa na komputerze użytkownika. Administrator skonfigurował etykietę, za pomocą reguł, które wykrywają poufnych danych i w tym przykładzie, to dane karty kredytowej. Gdy użytkownik zapisze dokument programu Word, który zawiera numer karty kredytowej, zostaje wyświetlona niestandardowa etykietka narzędzia z zaleceniem etykiety, która została skonfigurowana przez administratora. Etykieta ta klasyfikuje dokumentu i chroniona przez usługę. 

![Przykład zalecanej klasyfikacji w usłudze Azure Information Protection](./media/info-protect-recommend-calloutsv2.png)

Po sklasyfikowaniu (i opcjonalnym zabezpieczeniu) całej zawartości można śledzić i kontrolować sposób jej użycia. Na przykład można analizować przepływ danych w celu uzyskania wglądu w procesy biznesowe, wykrywać niebezpieczne zachowania i podejmować działania naprawcze, śledzić dostęp do dokumentów czy zapobiegać wyciekom lub nieprawidłowemu użyciu danych.

## <a name="how-labels-apply-classification"></a>Na czym polega klasyfikacja przy użyciu etykiet

Etykiety usługi Azure Information Protection służą do klasyfikowania dokumentów i wiadomości e-mail. Gdy to zrobisz, klasyfikacji jest do zidentyfikowania, niezależnie od tego, gdzie dane są przechowywane lub komu zostały udostępnione. Etykiety można zawierają oznaczenia wizualne, takie jak nagłówek, stopka lub znak wodny. Metadane dodawane do plików i nagłówków wiadomości e-mail mają postać zwykłego tekstu. Dzięki temu inne usługi (takie jak rozwiązania do zapobiegania utracie danych) mogą rozpoznać klasyfikację i podjąć odpowiednie działania. 

Na przykład poniższa wiadomość e-mail została sklasyfikowana jako ogólna. Etykieta została dodana stopkę "Czułości: Ogólne" do wiadomości e-mail. Ta stopka jest wizualny wskaźnik informujący wszystkich adresatów, jest przeznaczony dla danych biznesowych ogólnego, który nie należy jej wysyłać poza organizację. Etykieta jest osadzona w nagłówkach wiadomości e-mail, tak aby usługi poczty e-mail można sprawdzić tę wartość i może utworzyć wpis inspekcji lub uniemożliwić wysyłanie spoza organizacji.

![Przykład stopki i nagłówków wiadomości e-mail z wyświetloną klasyfikacją usługi Azure Information Protection](./media/example-email-footerv2.png)


## <a name="how-data-is-protected"></a>Sposób ochrony danych

Stosowana technologia ochrony korzysta z usługi o nazwie *Azure Rights Management* (często skracanej do postaci Azure RMS). Technologia ta jest zintegrowana z innymi usługami i aplikacjami chmurowymi firmy Microsoft, takimi jak Office 365 czy Azure Active Directory. Można jej również używać razem z własnymi aplikacjami biznesowymi oraz rozwiązaniami do ochrony informacji dostarczanymi przez producentów oprogramowania, zarówno w przypadku aplikacji i rozwiązań hostowanych lokalnie, jak i w chmurze.

Ta technologia ochrony używa zasad szyfrowania, tożsamości i autoryzacji. Podobnie jak w przypadku stosowanych etykiet, ochrona stosowana przy użyciu usługi Rights Management obejmuje dokumenty i wiadomości e-mail niezależnie od lokalizacji — wewnątrz organizacji, w sieciach, na serwerach plików, w aplikacjach i poza nimi. To rozwiązanie ochrony informacji zapewnia kontrolę nad danymi nawet wtedy, gdy są one udostępniane innym osobom.

Na przykład można tak skonfigurować dokument z raportem lub arkusz kalkulacyjny zawierający prognozę sprzedaży, aby był on dostępny tylko dla osób z danej organizacji. Ponadto można określić, czy dany dokument ma być dostępny do edycji lub ograniczyć jego właściwości tylko do odczytu albo uniemożliwić jego drukowanie. Na podobnej zasadzie można skonfigurować wiadomości e-mail, a ponadto uniemożliwić ich przesyłanie dalej lub uniemożliwić korzystanie z opcji Odpowiedz wszystkim. 

Te ustawienia ochrony może być częścią konfiguracji etykiety, dzięki czemu użytkownicy klasyfikować i chronić dokumenty i wiadomości e-mail po prostu stosując etykiety. Jednak takie same ustawienia ochrony można również przez aplikacje i usługi, które obsługują ochronę, ale nie etykietowania. Dla tych aplikacji i usług, ustawienia ochrony stają się dostępne jako *szablony usługi Rights Management*.

### <a name="rights-management-templates"></a>Szablony usługi Rights Management

Tak szybko, jak usługa Azure Rights Management została aktywowana, dwa szablony domyślne są dostępne dla Ciebie, która ograniczania dostępu do danych dla użytkowników w Twojej organizacji. Za pomocą tych szablonów można od razu przystąpić do ochrony danych przed wyciekiem poza organizację. Można również uzupełnienie szablonów domyślnych, konfigurując własne ustawienia ochrony, które są stosowane bardziej restrykcyjne mechanizmy kontroli.

Podczas tworzenia etykiety usługi Azure Information Protection, który zawiera ustawienia ochrony w sposób niewidoczny, ta akcja powoduje utworzenie odpowiedniego szablonu usługi Rights Management. Możesz następnie również użyć tego szablonu za pomocą aplikacji i usług, które obsługują usługę Azure Rights Management.

Na przykład w Centrum administracyjnym programu Exchange, można skonfigurować usługi Exchange Online reguły przepływu poczty, za pomocą tych szablonów:

![Przykład wybierania szablonów dla usługi Exchange Online](./media/templates-exchangeonline-callouts.png)

Aby uzyskać więcej informacji na temat ochrony usługi Azure Rights Management, zobacz [co to jest Azure Rights Management?](what-is-azure-rms.md)

## <a name="integration-with-end-user-workflows-for-documents-and-emails"></a>Integracja z przepływami pracy użytkownika końcowego dla dokumentów i wiadomości e-mail

Podczas instalowania klienta usługi Azure Information Protection usługa ta zostaje zintegrowana z istniejącymi przepływami pracy użytkowników końcowych. Klient instaluje w aplikacjach pakietu Office pasek usługi Information Protection, który był widoczny na pierwszej ilustracji, przedstawiającej ten pasek w programie Word. Taki sam pasek jest dodawany do programów Excel, PowerPoint i Outlook. Przykład:

![Przykład przedstawiający pasek usługi Azure Information Protection w programie Excel](./media/excel2016-infoprotect-barv2.png)

Pasek usługi Information Protection ułatwia użytkownikom końcowym wybieranie etykiet w celu prawidłowej klasyfikacji. W razie potrzeby etykiety mogą być również stosowane automatycznie, aby pomóc użytkownikom pozbyć się wątpliwości lub zapewnić zgodność z zasadami firmy.

Aby sklasyfikować i objąć ochroną dodatkowe typy plików oraz zapewnić obsługę wielu plików jednocześnie, kliknij prawym przyciskiem myszy pliki lub foldery w Eksploratorze plików systemu Windows:

![Kliknięcie prawym przyciskiem myszy w oknie Eksploratora plików — klasyfikowanie i ochrona za pomocą usługi Azure Information Protection](./media/right-click-classify-protect-folder.png)

Po wybraniu opcji menu **Klasyfikuj i chroń** w oknie Eksploratora plików użytkownicy mogą wybrać etykietę w sposób przypominający korzystanie z paska usługi Information Protection w aplikacjach klasycznych pakietu Office. Użytkownicy mogą również ustawić w razie potrzeby własne uprawnienia niestandardowe.

W przypadku użytkowników zaawansowanych (oraz administratorów) wydajniejszym sposobem na zarządzanie wieloma plikami oraz ustawianie ich klasyfikacji i ochrony może okazać się skorzystanie z poleceń programu PowerShell. Polecenia programu PowerShell umożliwia wykonywanie tych czynności są automatycznie dołączane za pomocą klienta programu, ale możesz także zainstalować moduł PowerShell oddzielnie.

Po objęciu dokumentu ochroną użytkownicy i administratorzy mogą monitorować, kto i kiedy uzyskuje dostęp do tych plików, za pomocą witryny śledzenia dokumentów. W przypadku podejrzenia nieprawidłowego użycia użytkownicy mogą również odwołać dostęp do dokumentów:

![Ikona funkcji Odwołaj dostęp w witrynie śledzenia dokumentów](./media/tracking-site-revoke-access-icon.png)

### <a name="additional-integration-for-email"></a>Dodatkowa integracja do obsługi poczty e-mail

Gdy używasz usługi Azure Information Protection z usługą Exchange Online, jest uzyskasz następującą dodatkową korzyść: możliwość wysyłania chronionych wiadomości e-mail z żadnym użytkownikiem, mając pewność, że może go odczytać na dowolnym urządzeniu.

Na przykład, użytkownicy muszą wysyłać poufne informacje osobiste adresy e-mail używających **Gmail**, **Hotmail**, lub **Microsoft** konta. Lub dla użytkowników, którzy nie mają konta usługi Office 365 lub Azure AD. Te wiadomości e-mail mają być szyfrowane podczas przechowywania i podczas przesyłania i odczytać tylko Pierwotni adresaci.

Ten scenariusz wymaga [nowe możliwości z szyfrowanie wiadomości usługi Office 365](https://techcommunity.microsoft.com/t5/Security-Privacy-and-Compliance/Email-Encryption-and-Rights-Protection/ba-p/110801). Adresaci nie może otworzyć chronioną wiadomość e-mail w ich natywnego klienta poczty e-mail, można korzystać jednorazowy kod dostępu do poufnych informacji w przeglądarce.

Na przykład użytkownik Gmail zobaczy następujące informacje w wiadomości e-mail:

![Środowisko adresata poczty Gmail NIEKTÓ i AIP](./media/ome-message.png)

Dla użytkowników, wysyłając wiadomość e-mail przepływu pracy nie różni się od wysyłania chronionych wiadomości e-mail do użytkowników w swojej organizacji. Na przykład, można wybrać **nie przesyłaj dalej** przycisku, który klient usługi Azure Information Protection można dodać do Wstążki programu Outlook. Lub ta funkcja nie przesyłaj dalej można zintegrować etykiety, który użytkownicy wybiorą, dzięki czemu wiadomości e-mail są klasyfikowane, jak również chronione:

![Wybieranie etykiety skonfigurowane dla nie przesyłaj dalej](./media/recipients-only-label.png)

Alternatywnie można automatycznie udostępnić ochrony dla użytkowników, przy użyciu reguły przepływu poczty, informujące o objęciu ochroną praw. 

Po dołączeniu dokumentów pakietu Office do tych wiadomości e-mail, dokumenty te są automatycznie chronione także.

## <a name="classifying-and-protecting-existing-documents"></a>Klasyfikowanie i ochrona istniejących dokumentów

W idealnym przypadku dokumentów i wiadomości e-mail są oznaczone po uprzednim utworzeniu. Jednak prawdopodobnie ma wiele istniejących dokumentów w magazynach danych i Aby sklasyfikować i objąć ochroną także te dokumenty. Te magazyny danych może być konfigurowane lokalnie lub w chmurze.

Dla swoich lokalnych magazynów danych należy użyć skanera usługi Azure Information Protection do odnajdywania, klasyfikowania i ochrony dokumentów na foldery lokalne, udziały sieciowe i witryny programu SharePoint Server i bibliotek. Skaner działa jako usługa w systemie Windows Server. Te same reguły w ramach zasad służy do wykrywania poufnych informacji i dotyczą konkretnych etykiet dokumentów. Lub etykiety domyślnej można zastosować do wszystkich dokumentów w repozytorium danych, bez sprawdzania zawartości pliku. Skaner w trybie tylko raportowania umożliwia również pomóc odkryć, poufne informacje, które może nie wiesz, że masz. 

Aby uzyskać więcej informacji na temat wdrażania i przy użyciu skanera zobacz [wdrażanie skanera usługi Azure Information Protection do automatycznego klasyfikowania i ochrony plików](deploy-rms-connector.md).

Dla Twojej magazynami danych w chmurze należy użyć Microsoft Cloud App Security do zastosowania etykiet do dokumentów, Box, SharePoint Online i OneDrive dla firm. Aby uzyskać więcej informacji, zobacz [automatyczne stosowanie etykiet klasyfikacji usługi Azure Information Protection](/cloud-app-security/use-case-information-protection) i [integracji usługi Azure Information Protection](/cloud-app-security/azip-integration).


## <a name="resources-for-azure-information-protection"></a>Zasoby dotyczące usługi Azure Information Protection

- Bezpłatna wersja próbna: [Enterprise Mobility + Security E5](https://portal.office.com/Signup/Signup.aspx?OfferId=87dd2714-d452-48a0-a809-d2f58c4f68b7)

- Opcji i cen subskrypcji: [cennik usługi Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection)

- Pobierz klienta: [Klient usługi Azure Information Protection](https://www.microsoft.com/en-us/download/details.aspx?id=53018)

- Pobierz Podręcznik użytkownika można dostosowywać: [przewodnika wdrażania użytkownika końcowego platformy Azure Information Protection](https://download.microsoft.com/download/7/1/2/712A280C-1C66-4EF9-8DC3-88EE43BEA3D4/Azure_Information_Protection_End_User_Adoption_Guide_EN_US.pdf)

- Często zadawane pytania: [Często zadawane pytania dotyczące usługi Azure Information Protection](faqs.md)

- Yammer: [Azure Information Protection](https://www.yammer.com/AskIPTeam)

Dodatkowe zasoby: [informacje i pomoc techniczna dla usługi Azure Information Protection](information-support.md)

### <a name="microsoft-ignite"></a>Na konferencji Microsoft Ignite

2018 r. Microsoft Ignite w Orlando ma wiele sesji, które są oznaczone [usługi Azure Information Protection](https://myignite.techcommunity.microsoft.com/sessions?q=Azure%2520Information%2520Protection). Wszystkie sesje są rejestrowane, więc jeśli nie dołączysz do nas istnieje, możesz nadal obejrzeć sesje później. Nasze pierwszych pięć sesji, które są zalecane:

- [BRK2006 — Użyj Microsoft informacji ochrony (MIP) w celu ochrony danych poufnych w dowolnym miejscu, przez cały cykl życia](https://myignite.techcommunity.microsoft.com/sessions/64297)
 
- [BRK3002 - zrozumienie, jak możliwości Microsoft Information Protection współpracują ze sobą, aby chronić poufne informacje z różnych urządzeń, aplikacji i usług](https://myignite.techcommunity.microsoft.com/sessions/64299)

- [BRK3009 - przyspieszenia wdrożenia i przyjęcia rozwiązania Microsoft Information Protection](https://myignite.techcommunity.microsoft.com/sessions/64283)

- [BRK3397 — ochrona i kontrola poufnych wiadomości e-mail przy użyciu szyfrowanie wiadomości usługi Office 365](https://myignite.techcommunity.microsoft.com/sessions/64327)

- [THR2003 — odnajdywanie danych raportowania użycia i analizy wszystkich danych z usługą Microsoft Information Protection](https://myignite.techcommunity.microsoft.com/sessions/64301)

Do zestawienia anonsów, które zostały wprowadzone podczas tej konferencji Ignite, zobacz wpis w blogu [ogłaszamy dostępność funkcji ochrony informacji w celu ochrony danych poufnych](https://techcommunity.microsoft.com/t5/Enterprise-Mobility-Security/Announcing-availability-of-information-protection-capabilities/ba-p/261967).


## <a name="next-steps"></a>Kolejne kroki

Przeczytaj wpis w blogu: [Azure Information Protection: Ready, set, protect!](https://cloudblogs.microsoft.com/enterprisemobility/2017/02/21/azure-information-protection-ready-set-protect/) (Azure Information Protection: przygotowanie, ustawianie, ochrona)

Konfigurowanie i sprawdź osobiście, usługi Azure Information Protection przy użyciu naszego kroku 5 [— samouczek szybki start](infoprotect-quick-start-tutorial.md). Lub, jeśli wszystko będzie gotowe do wdrożenia tej usługi dla swojej organizacji, zobacz [planu wdrożenia usługi Azure Information Protection](deployment-roadmap.md).

Być może znasz usługę Azure Information Protection pod inną nazwą? Zobacz nasze [listę alternatywnej terminologii usługi](aka.md).

