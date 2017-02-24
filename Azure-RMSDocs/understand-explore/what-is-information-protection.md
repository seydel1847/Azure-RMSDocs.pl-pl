---
title: Co to jest Azure Information Protection? | Azure Information Protection
description: "Omówienie usługi Azure Information Protection."
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 02/16/2017
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: cd8a88e2-3555-4be2-9637-3cdee992f2c8
translationtype: Human Translation
ms.sourcegitcommit: 4d20462f190042e1ac8d674123296f65c66d9921
ms.openlocfilehash: 50b83f165dfbcf9b5f66ae8bfc596d1aa910f10d


---

# <a name="what-is-azure-information-protection"></a>Co to jest Azure Information Protection?

>*Dotyczy: Azure Information Protection*

Azure Information Protection to rozwiązanie chmurowe ułatwiające klasyfikowanie, etykietowanie i ochronę dokumentów oraz wiadomości e-mail w firmie. Czynności te mogą być wykonywane automatycznie przez administratorów definiujących reguły i warunki, ręcznie przez użytkowników bądź wspólnie — użytkownicy otrzymują wówczas zalecenia. 

Na poniższej ilustracji przedstawiono przykładowe zastosowanie usługi Azure Information Protection. Administrator skonfigurował reguły wykrywania poufnych danych (w tym przypadku informacji o karcie kredytowej). Podczas zapisywania przez użytkownika dokumentu programu Word zawierającego dane karty kredytowej zostaje wyświetlona niestandardowa etykietka narzędzia z zaleceniem, aby użytkownik zastosował konkretną, skonfigurowaną przez administratora etykietę, która klasyfikuje i — opcjonalnie — chroni dokument. 

![Przykład zalecanej klasyfikacji w usłudze Azure Information Protection](../media/info-protect-recommend-callouts.png)

Po sklasyfikowaniu (i opcjonalnym zabezpieczeniu) całej zawartości można śledzić i kontrolować sposób jej użycia. Na przykład można analizować przepływ danych w celu uzyskania wglądu w procesy biznesowe, wykrywać niebezpieczne zachowania i podejmować działania naprawcze, śledzić dostęp do dokumentów czy zapobiegać wyciekom lub nieprawidłowemu użyciu danych.

## <a name="how-labels-apply-classification"></a>Na czym polega klasyfikacja przy użyciu etykiet

Etykiety usługi Azure Information Protection służą do klasyfikowania dokumentów i wiadomości e-mail. Dzięki zastosowaniu tej metody klasyfikację można zawsze rozpoznać, niezależnie od tego, gdzie dane są przechowywane lub komu zostały udostępnione. Trwałe etykiety zawierają oznaczenia wizualne, takie jak nagłówek, stopka lub znak wodny. Metadane dodawane do plików i nagłówków wiadomości e-mail mają postać zwykłego tekstu, dzięki czemu inne usługi (takie jak rozwiązania do zapobiegania utracie danych) mogą rozpoznać klasyfikację i podjąć odpowiednie działania. 

Przykładowo poniższa wiadomość e-mail została sklasyfikowana jako wewnętrzna. Etykieta ta jest dodana w stopce wiadomości e-mail jako wizualny wskaźnik informujący wszystkich adresatów, że wiadomość jest przeznaczona do użytku wewnętrznego i nie należy jej wysyłać poza organizację. Etykieta jest również osadzona w nagłówkach wiadomości e-mail, aby usługi poczty e-mail mogły sprawdzić tę wartość i utworzyć wpis inspekcji lub uniemożliwić wysłanie wiadomości poza firmę.

![Przykład stopki i nagłówków wiadomości e-mail z wyświetloną klasyfikacją usługi Azure Information Protection](../media/example-email-footer-header.png)


## <a name="how-data-is-protected"></a>Sposób ochrony danych

Stosowana technologia ochrony korzysta z usługi o nazwie *Azure Rights Management* (często skracanej do postaci Azure RMS). Technologia ta jest zintegrowana z innymi usługami i aplikacjami chmurowymi firmy Microsoft, takimi jak Office 365 czy Azure Active Directory. Można jej również używać razem z własnymi aplikacjami biznesowymi oraz rozwiązaniami do ochrony informacji dostarczanymi przez producentów oprogramowania, zarówno w przypadku aplikacji i rozwiązań hostowanych lokalnie, jak i w chmurze.

Ta technologia ochrony używa zasad szyfrowania, tożsamości i autoryzacji. Podobnie jak w przypadku trwałych etykiet, ochrona stosowana przy użyciu usługi Rights Management pozostaje z dokumentami i wiadomościami e-mail niezależnie od lokalizacji — wewnątrz organizacji, sieci, serwerów plików i aplikacji lub poza nimi. To rozwiązanie ochrony informacji zapewnia kontrolę nad danymi nawet wtedy, gdy są one udostępniane innym osobom.

Na przykład można tak skonfigurować dokument z raportem lub arkusz kalkulacyjny zawierający prognozę sprzedaży, aby był on dostępny tylko dla osób z danej organizacji. Ponadto można określić, czy dany dokument ma być dostępny do edycji lub ograniczyć jego właściwości tylko do odczytu albo uniemożliwić jego drukowanie. Na podobnej zasadzie można skonfigurować wiadomości e-mail, a ponadto uniemożliwić ich przesyłanie dalej lub uniemożliwić korzystanie z opcji Odpowiedz wszystkim. Te zadania ochrony można uprościć i usprawnić przy użyciu *szablonów usługi Rights Management*.

### <a name="rights-management-templates"></a>Szablony usługi Rights Management

Po aktywowaniu usługi Azure Rights Management zostają automatycznie utworzone dwa szablony domyślne, ograniczające dostęp do danych do użytkowników w ramach organizacji. Za pomocą tych szablonów można od razu przystąpić do ochrony danych przed wyciekiem poza organizację. Jako uzupełnienie szablonów domyślnych można skonfigurować własne szablony niestandardowe, stosujące bardziej restrykcyjne mechanizmy kontroli.

Szablony te mogą być częścią konfiguracji etykiety — zastosowanie konkretnej etykiety do dokumentu (lub wiadomości e-mail) spowoduje zarówno sklasyfikowanie, jak i automatyczne zabezpieczenie danych. Szablony mogą być również wybierane przez użytkowników lub administratorów w produktach i usługach, które obsługują technologię Azure Rights Management.

W tym przykładzie pokazano, jak można wybrać szablon dla etykiety podczas konfigurowania zasad usługi Azure Information Protection w witrynie Azure Portal:

![Przykład przedstawiający wybieranie szablonów w witrynie Azure Portal](../media/info-protect-template-callout.png)

Te same szablony można też wybierać z poziomu centrum administracyjnego programu Exchange w celu skonfigurowania reguł przepływu poczty usługi Exchange Online, które obsługują technologię Azure Rights Management:

![Przykład wybierania szablonów dla usługi Exchange Online](../media/templates-exchangeonline-callouts.png)

Aby uzyskać więcej informacji na temat mechanizmów ochrony w usłudze Azure Rights Management, zobacz [Co to jest usługa Azure Rights Management?](what-is-azure-rms.md)

## <a name="integration-with-end-user-workflows"></a>Integracja z przepływami pracy użytkownika końcowego

Podczas instalowania klienta usługi Azure Information Protection usługa ta zostaje zintegrowana z istniejącymi przepływami pracy użytkowników końcowych. Klient instaluje w aplikacjach pakietu Office pasek usługi Information Protection, który był widoczny na pierwszej ilustracji. Taki sam pasek jest dodawany do programów Excel, PowerPoint i Outlook. Na przykład:

![Przykład przedstawiający pasek usługi Azure Information Protection w programie Excel](../media/excel2016-infoprotect-bar.png)

Pasek usługi Information Protection ułatwia użytkownikom końcowym wybieranie etykiet w celu prawidłowej klasyfikacji. Jeśli to konieczne, etykiety te mogą również automatycznie chronić dokumenty i wiadomości e-mail użytkowników.

Aby sklasyfikować i objąć ochroną dodatkowe typy plików oraz zapewnić obsługę wielu plików jednocześnie, kliknij prawym przyciskiem myszy pliki lub foldery w Eksploratorze plików systemu Windows:

![Kliknięcie prawym przyciskiem myszy w oknie Eksploratora plików — klasyfikowanie i ochrona za pomocą usługi Azure Information Protection](../media/right-click-classify-protect-folder.png)

Po wybraniu opcji menu **Klasyfikuj i chroń** w oknie Eksploratora plików użytkownicy mogą wybrać etykietę w sposób przypominający korzystanie z paska usługi Information Protection w aplikacjach klasycznych pakietu Office. Użytkownicy mogą również ustawić w razie potrzeby własne uprawnienia niestandardowe.

W przypadku użytkowników zaawansowanych (oraz administratorów) wydajniejszym sposobem na zarządzanie wieloma plikami oraz ustawianie ich klasyfikacji i ochrony może okazać się skorzystanie z poleceń programu PowerShell. Chociaż polecenia programu PowerShell umożliwiające wykonywanie tych czynności są automatycznie zawarte w kliencie, moduł PowerShell można także zainstalować oddzielnie.

Po objęciu dokumentu ochroną użytkownicy i administratorzy mogą monitorować, kto i kiedy uzyskuje dostęp do tych plików, za pomocą witryny śledzenia dokumentów. W przypadku podejrzenia nieprawidłowego użycia użytkownicy mogą również odwołać dostęp do dokumentów:

![Ikona funkcji Odwołaj dostęp w witrynie śledzenia dokumentów](../media/tracking-site-revoke-access-icon.png)


## <a name="resources-for-azure-information-protection"></a>Zasoby dotyczące usługi Azure Information Protection

- Zawiadomienie: [Usługa Azure Information jest teraz ogólnie dostępna](https://blogs.technet.microsoft.com/enterprisemobility/2016/10/04/azure-information-protection-is-now-generally-available/)

- Bezpłatna wersja próbna: [Enterprise Mobility + Security E5](https://portal.office.com/Signup/Signup.aspx?OfferId=87dd2714-d452-48a0-a809-d2f58c4f68b7)

- Pobierz klienta: [Klient usługi Azure Information Protection](https://www.microsoft.com/en-us/download/details.aspx?id=53018)

- Często zadawane pytania: [Często zadawane pytania dotyczące usługi Azure Information Protection](../get-started/faqs.md)

- Yammer: [Azure Information Protection](https://www.yammer.com/askipteam/#/threads/inGroup?type=in_group&feedId=8652489&view=all)

- Przegląd wideo

    <iframe width="560" height="315" src="https://www.youtube.com/embed/N9Ip0m6d3G0" frameborder="0" allowfullscreen></iframe>

    Dodatkowo Microsoft Ignite 2016 oferuje wiele sesji na żądanie dotyczących usługi Azure Information Protection:

    - [BRK2127: Adopt a comprehensive identity-driven solution for protecting and sharing data securely](https://myignite.microsoft.com/videos?q=BRK2127) (Wdrażanie kompleksowego rozwiązania opartego na tożsamościach służącego do ochrony i bezpiecznego udostępniania danych)
    
    - [THR2107: Collaborate securely using Azure Information Protection](https://myignite.microsoft.com/videos?q=THR2107) (Bezpieczna współpraca przy użyciu Azure Information Protection)
    
    - [THR2108: Ensure comprehensive protection of your data with Azure Information Protection](https://myignite.microsoft.com/videos?q=THR2108) (Zapewnianie kompleksowej ochrony danych dzięki usłudze Azure Information Protection)
    
    - [BRK3095: Learn how classification, labeling, and protection delivers persistent data protection (Dowiedz się, jak klasyfikacja, etykietowanie i ochrona zapewniają trwałą ochronę danych)](https://myignite.microsoft.com/videos?q=BRK3095)
    
    - [BRK2128: Send secure email to anyone with the power of Microsoft Office 365 and Azure Information Protection](https://myignite.microsoft.com/videos?q=BRK2128) (Wysyłanie zabezpieczonej poczty e-mail do wszystkich odbiorców za pomocą usług Microsoft Office 365 i Azure Information Protection)


## <a name="next-steps"></a>Następne kroki

Samodzielnie skonfiguruj i poznaj usługę Azure Information Protection w pięciu krokach z naszym [Samouczkiem Szybki start dla usługi Azure Information Protection](../get-started/infoprotect-quick-start-tutorial.md).

Znasz usługę Azure Information Protection bądź Azure Rights Management pod inną nazwą? Zobacz [naszą listę alternatywnej terminologii usługi](azure-rms-aka.md).

[!INCLUDE[Commenting house rules](../includes/houserules.md)]


<!--HONumber=Feb17_HO2-->


