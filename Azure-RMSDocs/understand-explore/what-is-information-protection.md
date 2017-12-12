---
title: Co to jest Azure Information Protection?
description: "Omówienie usługi Azure Information Protection."
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 12/08/2017
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: cd8a88e2-3555-4be2-9637-3cdee992f2c8
ms.openlocfilehash: 18ec6241d09eb8de2417dd939237de0544a401e8
ms.sourcegitcommit: 9b229852c59441f9387bab1d5f28a3c5d9017696
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/11/2017
---
# <a name="what-is-azure-information-protection"></a>Co to jest Azure Information Protection?

>*Dotyczy: Azure Information Protection*

Azure Information Protection to rozwiązanie chmurowe ułatwiające klasyfikowanie, etykietowanie i ochronę dokumentów oraz wiadomości e-mail w firmie. Czynności te mogą być wykonywane automatycznie przez administratorów definiujących reguły i warunki, ręcznie przez użytkowników bądź wspólnie — użytkownicy otrzymują wówczas zalecenia. 

Na poniższej ilustracji przedstawiono przykładowe zastosowanie usługi Azure Information Protection. Administrator skonfigurował reguły wykrywania poufnych danych (w tym przypadku informacji o karcie kredytowej). Podczas zapisywania przez użytkownika dokumentu programu Word zawierającego dane karty kredytowej zostaje wyświetlona niestandardowa etykietka narzędzia z zaleceniem, aby użytkownik zastosował konkretną, skonfigurowaną przez administratora etykietę. Etykieta ta klasyfikuje i — opcjonalnie, w zależności od konfiguracji — chroni dokument. 

![Przykład zalecanej klasyfikacji w usłudze Azure Information Protection](../media/info-protect-recommend-calloutsv2.png)

Po sklasyfikowaniu (i opcjonalnym zabezpieczeniu) całej zawartości można śledzić i kontrolować sposób jej użycia. Na przykład można analizować przepływ danych w celu uzyskania wglądu w procesy biznesowe, wykrywać niebezpieczne zachowania i podejmować działania naprawcze, śledzić dostęp do dokumentów czy zapobiegać wyciekom lub nieprawidłowemu użyciu danych.

## <a name="how-labels-apply-classification"></a>Na czym polega klasyfikacja przy użyciu etykiet

Etykiety usługi Azure Information Protection służą do klasyfikowania dokumentów i wiadomości e-mail. Dzięki zastosowaniu tej metody klasyfikację można zawsze rozpoznać, niezależnie od tego, gdzie dane są przechowywane lub komu zostały udostępnione. Etykiety zawierają oznaczenia wizualne, takie jak nagłówek, stopka lub znak wodny. Metadane dodawane do plików i nagłówków wiadomości e-mail mają postać zwykłego tekstu. Dzięki temu inne usługi (takie jak rozwiązania do zapobiegania utracie danych) mogą rozpoznać klasyfikację i podjąć odpowiednie działania. 

Na przykład poniższa wiadomość e-mail została sklasyfikowana jako ogólna. Etykieta jest dodawana jako stopkę do wiadomości e-mail. Ta stopka jest wizualnej dla wszystkich adresatów, które jest przeznaczone do danych biznesowych ogólnych, które nie mają być wysyłane poza organizację. Etykieta jest również osadzona w nagłówkach wiadomości e-mail, aby usługi poczty e-mail mogły sprawdzić tę wartość i utworzyć wpis inspekcji lub uniemożliwić wysłanie wiadomości poza firmę.

![Przykład stopki i nagłówków wiadomości e-mail z wyświetloną klasyfikacją usługi Azure Information Protection](../media/example-email-footerv2.png)


## <a name="how-data-is-protected"></a>Sposób ochrony danych

Stosowana technologia ochrony korzysta z usługi o nazwie *Azure Rights Management* (często skracanej do postaci Azure RMS). Technologia ta jest zintegrowana z innymi usługami i aplikacjami chmurowymi firmy Microsoft, takimi jak Office 365 czy Azure Active Directory. Można jej również używać razem z własnymi aplikacjami biznesowymi oraz rozwiązaniami do ochrony informacji dostarczanymi przez producentów oprogramowania, zarówno w przypadku aplikacji i rozwiązań hostowanych lokalnie, jak i w chmurze.

Ta technologia ochrony używa zasad szyfrowania, tożsamości i autoryzacji. Podobnie jak w przypadku stosowanych etykiet, ochrona stosowana przy użyciu usługi Rights Management obejmuje dokumenty i wiadomości e-mail niezależnie od lokalizacji — wewnątrz organizacji, w sieciach, na serwerach plików, w aplikacjach i poza nimi. To rozwiązanie ochrony informacji zapewnia kontrolę nad danymi nawet wtedy, gdy są one udostępniane innym osobom.

Na przykład można tak skonfigurować dokument z raportem lub arkusz kalkulacyjny zawierający prognozę sprzedaży, aby był on dostępny tylko dla osób z danej organizacji. Ponadto można określić, czy dany dokument ma być dostępny do edycji lub ograniczyć jego właściwości tylko do odczytu albo uniemożliwić jego drukowanie. Na podobnej zasadzie można skonfigurować wiadomości e-mail, a ponadto uniemożliwić ich przesyłanie dalej lub uniemożliwić korzystanie z opcji Odpowiedz wszystkim. 

Te ustawienia ochrony może być częścią konfigurację etykiety, dzięki czemu użytkownicy klasyfikować i chronić dokumenty i wiadomości e-mail po prostu, stosując etykiety. Jednak takie same ustawienia ochrony można również używane przez aplikacje i usługi, które obsługują ochronę, ale nie etykietowania. Dla tych aplikacji i usług, ustawienia ochrony staną się dostępne jako *szablony usługi Rights Management*.

### <a name="rights-management-templates"></a>Szablony zarządzania prawami

Jak aktywować usługę Azure Rights Management, dwa szablony domyślne są dostępne dla Ciebie, który ogranicza dostęp do danych użytkownikom w organizacji. Za pomocą tych szablonów można od razu przystąpić do ochrony danych przed wyciekiem poza organizację. Można również uzupełnić te szablony domyślne, konfigurując własne ustawienia ochrony, które mają zastosowanie bardziej restrykcyjnych formantów.

Podczas tworzenia etykiety dla usługi Azure Information Protection, zawierający ustawienia ochrony w obszarze obejmuje, ta akcja tworzy odpowiedni szablon usługi Rights Management. Możesz można również skorzystać z tego szablonu z aplikacjami i usługami, które obsługują usługę Azure Rights Management.

Na przykład w Centrum administracyjnym programu Exchange, można skonfigurować usługi Exchange Online reguły przepływu poczty używać tych szablonów:

![Przykład wybierania szablonów dla usługi Exchange Online](../media/templates-exchangeonline-callouts.png)

Aby uzyskać więcej informacji na temat mechanizmów ochrony w usłudze Azure Rights Management, zobacz [Co to jest usługa Azure Rights Management?](what-is-azure-rms.md)

## <a name="integration-with-end-user-workflows-for-documents-and-emails"></a>Integracja z przepływami pracy użytkowników końcowych dla dokumentów i wiadomości e-mail

Podczas instalowania klienta usługi Azure Information Protection usługa ta zostaje zintegrowana z istniejącymi przepływami pracy użytkowników końcowych. Klient instaluje w aplikacjach pakietu Office pasek usługi Information Protection, który był widoczny na pierwszej ilustracji, przedstawiającej ten pasek w programie Word. Taki sam pasek jest dodawany do programów Excel, PowerPoint i Outlook. Na przykład:

![Przykład przedstawiający pasek usługi Azure Information Protection w programie Excel](../media/excel2016-infoprotect-barv2.png)

Pasek usługi Information Protection ułatwia użytkownikom końcowym wybieranie etykiet w celu prawidłowej klasyfikacji. W razie potrzeby etykiety mogą być również stosowane automatycznie, aby pomóc użytkownikom pozbyć się wątpliwości lub zapewnić zgodność z zasadami firmy.

Aby sklasyfikować i objąć ochroną dodatkowe typy plików oraz zapewnić obsługę wielu plików jednocześnie, kliknij prawym przyciskiem myszy pliki lub foldery w Eksploratorze plików systemu Windows:

![Kliknięcie prawym przyciskiem myszy w oknie Eksploratora plików — klasyfikowanie i ochrona za pomocą usługi Azure Information Protection](../media/right-click-classify-protect-folder.png)

Po wybraniu opcji menu **Klasyfikuj i chroń** w oknie Eksploratora plików użytkownicy mogą wybrać etykietę w sposób przypominający korzystanie z paska usługi Information Protection w aplikacjach klasycznych pakietu Office. Użytkownicy mogą również ustawić w razie potrzeby własne uprawnienia niestandardowe.

W przypadku użytkowników zaawansowanych (oraz administratorów) wydajniejszym sposobem na zarządzanie wieloma plikami oraz ustawianie ich klasyfikacji i ochrony może okazać się skorzystanie z poleceń programu PowerShell. Chociaż polecenia programu PowerShell umożliwiające wykonywanie tych czynności są automatycznie zawarte w kliencie, moduł PowerShell można także zainstalować oddzielnie.

Po objęciu dokumentu ochroną użytkownicy i administratorzy mogą monitorować, kto i kiedy uzyskuje dostęp do tych plików, za pomocą witryny śledzenia dokumentów. W przypadku podejrzenia nieprawidłowego użycia użytkownicy mogą również odwołać dostęp do dokumentów:

![Ikona funkcji Odwołaj dostęp w witrynie śledzenia dokumentów](../media/tracking-site-revoke-access-icon.png)

### <a name="additional-integration-for-email"></a>Dodatkowe integracji do obsługi poczty e-mail

Gdy używasz usługi Azure Information Protection z usługą Exchange Online, możesz uzyskać dodatkową korzyścią: umożliwia wysyłanie chronionych wiadomości e-mail z żadnym użytkownikiem, z gwarantują, że może go odczytać na dowolnym urządzeniu.

Na przykład użytkownicy musieli przesyłają poufne informacje osobiste konta e-mail używane przez **Gmail**, **Hotmail**, lub **Microsoft** konta. Lub użytkownikom który nie ma konta usługi Office 365 lub w usłudze Azure AD. Te wiadomości e-mail powinny być szyfrowane podczas przechowywania i podczas przesyłania i zostać odczytana tylko przez Pierwotni adresaci.

Ten scenariusz wymaga [nowe funkcje z szyfrowanie wiadomości usługi Office 365](https://techcommunity.microsoft.com/t5/Security-Privacy-and-Compliance/Email-Encryption-and-Rights-Protection/ba-p/110801). Jeśli adresaci nie może otworzyć chronioną wiadomość e-mail w swoich klientów natywnych poczty e-mail, może użyć jednorazowy kod dostępu do odczytu poufnych informacji w przeglądarce.

Na przykład usługi Gmail jest widoczny poniżej w wiadomości e-mail:

![Odbiorcy obsługi OME i Efektywnych Gmail](../media/ome-message.png)

Dla użytkowników podczas wysyłania wiadomości e-mail, ich przepływu pracy nie różni się od wysyłanie chronionych wiadomości e-mail do użytkownika w ich własnej organizacji. Na przykład można wybrać **nie przesyłaj dalej** przycisku, który klient usługi Azure Information Protection można dodać do Wstążki programu Outlook. Lub tej funkcji nie przesyłaj dalej można zintegrować etykiety, który użytkownicy wybiorą, dzięki czemu wiadomości e-mail jest klasyfikowany, jak również chronione:

![Wybranie etykiety skonfigurowane dla czy nie do przodu o](../media/recipients-only-label.png)

Alternatywnie można automatycznie udostępnić ochrony dla użytkowników, przy użyciu reguły przepływu poczty, które mają zastosowanie ochrony praw. 

Po dołączeniu dokumentów pakietu Office do tych wiadomości e-mail, te dokumenty są chronione automatycznie również.

## <a name="resources-for-azure-information-protection"></a>Zasoby dotyczące usługi Azure Information Protection

- Bezpłatna wersja próbna: [Enterprise Mobility + Security E5](https://portal.office.com/Signup/Signup.aspx?OfferId=87dd2714-d452-48a0-a809-d2f58c4f68b7)

- Pobierz klienta: [Klient usługi Azure Information Protection](https://www.microsoft.com/en-us/download/details.aspx?id=53018)

- Pobierz Podręcznik użytkownika można dostosowywać: [przewodnik dotyczący wdrażania użytkownika końcowego ochrony informacji Azure](https://download.microsoft.com/download/7/1/2/712A280C-1C66-4EF9-8DC3-88EE43BEA3D4/Azure_Information_Protection_End_User_Adoption_Guide_EN_US.pdf)

- Często zadawane pytania: [Często zadawane pytania dotyczące usługi Azure Information Protection](../get-started/faqs.md)

- Yammer: [Azure Information Protection](https://www.yammer.com/AskIPTeam)


Ponadto **Microsoft Ignite 2017** ma wiele sesji dla usługi Azure Information Protection, które są dostępne na żądanie. Podsumowanie anonsów, które zostały dokonane na tej konferencji, zobacz [What's new in Azure Information Protection @ Ignite 2017](https://blogs.technet.microsoft.com/enterprisemobility/2017/09/27/whats-new-in-azure-information-protection-ignite-2017/). 

Możesz [Wyszukaj i Znajdź](https://myignite.microsoft.com/videos?q=%2522azure%2520information%2520protection%2522) sesji, które są oznaczone dla usługi Azure Information Protection na Ignite witryny sieci Web. Firma Microsoft zaleca jednak zaczynać następujące sesje:

- [Ochrona cyklu życia pełnych danych przy użyciu funkcji ochrony informacji firmy Microsoft](https://myignite.microsoft.com/videos/55397)

- [Przyspieszenie Azure information protection wdrożenia i przyjęcia](https://myignite.microsoft.com/videos/53454)

- [Odkryj nowości w usłudze Azure Information Protection i Dowiedz się więcej o plan i strategii](https://myignite.microsoft.com/videos/53453)

- [Strategie zarządzania kluczami szyfrowania, zgodności](https://myignite.microsoft.com/videos/53455)

- [Chroń i kontroluj poufne wiadomości e-mail z nowych funkcji szyfrowanie wiadomości usługi Office 365](https://myignite.microsoft.com/videos/53230)


## <a name="next-steps"></a>Następne kroki

Przeczytaj wpis w blogu: [Azure Information Protection: Ready, set, protect!](https://blogs.technet.microsoft.com/enterprisemobility/2017/02/21/azure-information-protection-ready-set-protect/) (Azure Information Protection: przygotowanie, ustawianie, ochrona)

Samodzielnie skonfiguruj i poznaj usługę Azure Information Protection w pięciu krokach z naszym [Samouczkiem Szybki start dla usługi Azure Information Protection](../get-started/infoprotect-quick-start-tutorial.md).

Być może znasz usługę Azure Information Protection bądź Azure Rights Management pod inną nazwą? Zobacz [naszą listę alternatywnej terminologii usługi](azure-rms-aka.md).

[!INCLUDE[Commenting house rules](../includes/houserules.md)]