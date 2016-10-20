---
title: "Często zadawane pytania dotyczące klasyfikacji i etykietowania | Azure Information Protection"
description: "Masz pytanie dotyczące wersji zapoznawczej usługi Azure Information Protection? Zobacz, czy nie znajdziesz tutaj odpowiedzi."
author: cabailey
manager: mbaldwin
ms.date: 09/25/2016
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: 4b595b6a-7eb0-4438-b49a-686431f95ddd
ms.reviewer: adhall
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: ce4fc256cf80fdd2e4a8212e2f64ffc6ca6a3964
ms.openlocfilehash: 9b341a53a85242839d737bc36c90a8f94637bae1


---

# Często zadawane pytania dotyczące klasyfikacji i etykietowania w usłudze Azure Information Protection

>*Dotyczy: Azure Information Protection, Office 365*

Masz pytanie związane z usługą Azure Information Protection, które dotyczy klasyfikacji i etykietowania?  Zobacz, czy nie znajdziesz tutaj odpowiedzi. 

## Jakie czynności mogę wykonywać za pomocą funkcji klasyfikacji w usłudze Azure Information Protection?

Ten klient usługi Azure Information Protection dodaje do aplikacji pakietu Microsoft Office pasek Information Protection, który umożliwia wyświetlanie i modyfikowanie przypisanych etykiet klasyfikacji danych. Klasyfikacja może być wykonywana ręcznie, zalecana użytkownikom lub stosowana automatycznie. W przypadku klasyfikacji określonych przez Ciebie dane mogą być chronione przy użyciu usługi Rights Management.  

Etykiety i zachowanie klasyfikacji są skonfigurowane w portalu Azure. Wbudowane zasady domyślne mogą służyć do szybkiej oceny usługi Azure Information Protection lub do pełnego dostosowania własnych zasad. Można zmienić kolory, nazwy i kolejność etykiet klasyfikacji widocznych dla użytkowników. Można również skonfigurować etykietki narzędzi i wizualne oznaczenia klasyfikacji, takie jak nagłówek, stopka lub znak wodny.

Kilka minut wystarczy do zapoznania się z naszym samouczkiem Szybki start: [Samouczek Szybki start dla usługi Azure Information Protection](infoprotect-quick-start-tutorial.md).

Obecna wersja ma następujące ograniczenia: W blogu [dotyczącym pakietu Enterprise Mobility i zabezpieczeń](https://blogs.technet.microsoft.com/enterprisemobility/?product=azure-information-protection) i witrynie [Yammer](https://www.yammer.com/askipteam/#/threads/inGroup?type=in_group&feedId=8652489&view=all) będą się pojawiać ogłoszenia o dostępności dodatkowych funkcji i możliwości:

- Brak centralnego rejestrowania dla funkcji klasyfikacji i etykietowania.

- Nazwy etykiet i etykietki narzędzi są obsługiwane tylko w jednym języku.

- Warunkami klasyfikacji automatycznej muszą być frazy lub wzorce.

- Pliki nie mogą być klasyfikowane w Eksploratorze plików systemu Windows.

- Aplikacje pakietu Office dla komputerów Mac i urządzeń przenośnych (iOS i Android) ani aplikacje sieci Web pakietu Office (Office Online) nie są jeszcze obsługiwane.

- Brak integracji z programem Exchange Online i usługą SharePoint Online.

- Zestaw SDK dla deweloperów i partnerów nie jest dostępny.

## Czy muszę być administratorem globalnym, aby wypróbować usługę Azure Information Protection?

Aby skonfigurować zasady usługi Azure Information Protection, musisz zalogować się do portalu Azure jako administrator globalny usługi Azure Active Directory.

Jeśli jednak w trakcie instalacji [klienta usługi Azure Information Protection](https://www.microsoft.com/en-us/download/details.aspx?id=53018) wybrano opcję zainstalowania zasad demonstracyjnych, zalogowanie się do portalu nie jest konieczne do wyświetlenia i wypróbowania funkcji etykietowania. Zasada demonstracyjna instaluje lokalnie zasadę domyślną usługi Azure Information Protection, co umożliwia próby etykietowania dokumentów i wiadomości e-mail, ale nie pozwala na zmianę ani dodanie nowej etykiety bez rejestrowania się w portalu Azure. 

## Czy usługa Azure Information Protection obsługuje scenariusze lokalne i hybrydowe?

Usługa Azure Information Protection to rozwiązanie oparte na chmurze. Jeśli interesuje Cię wdrożenie usługi Azure Information Protection dla scenariusza hybrydowego, skontaktuj się z zespołem usługi Information Protection, wysyłając wiadomość e-mail na adres askipteam@microsoft.com.

## Jak komputery uzyskują informacje o zasadach od usługi Azure Information Protection i jak często są one odświeżane?

Przy każdym otwarciu aplikacji pakietu Office klient usługi Azure Information Protection sprawdza, czy jest dostępna nowsza wersja zasad usługi. Ponadto aplikacje pakietu Office przeprowadzają sprawdzanie co 24 godziny. Jeśli istnieje nowsza wersja, klient pobiera ją za pomocą łącza HTTPS w celu zabezpieczenia danych. 

Jeśli podczas publikowania nowych zasad usługi Azure Information Protection załadowanych jest wiele wystąpień aplikacji pakietu Office, musisz zamknąć wszystkie instancje, aby pobrać najnowszą wersję zasad. Przykładowo, jeśli masz otwarte dwa dokumenty programu Word i chcesz przetestować zaktualizowane zasady usługi Azure Information Protection tylko w jednym dokumencie: zamknij oba dokumenty programu Word i otwórz ponownie dokument, którego chcesz użyć wraz z najnowszymi zasadami.

## Gdzie mogą być przechowywane pliki korzystające z usługi Azure Information Protection? 

Ponieważ usługa Azure Information Protection nadaje trwałe etykiety i chroni pliki oraz wiadomości e-mail, nie ma znaczenia, gdzie są przechowywane pliki.

## Czy mogę klasyfikować tylko nowe dane, czy też również dane istniejące?

Akcje zasady usługi Azure Information Protection stają się aktywne przy zapisywaniu dokumentów i wysyłaniu wiadomości e-mail, zarówno w przypadku nowej zawartości, jak i zmian w zawartości istniejącej. 

Jeśli pliki, które chcesz sklasyfikować, zostały już zapisane, wystarczy je otworzyć i zapisać w aplikacji pakietu Office. 

Obecnie nie można skanować i klasyfikować dokumentów zbiorczo, gdyż każdy dokument musi zostać otwarty i zapisany w aplikacji pakietu Office. 

## Czy usługi Azure Information Protection można używać wyłącznie do klasyfikowania, bez wymuszania szyfrowania i ograniczania prawa użytkowania?

Tak. Można tak skonfigurować zasadę usługi Azure Information Protection, aby wyłącznie nadawała etykiety. W zasadzie można oczekiwać, że będzie się tak dziać w większości już wdrożonych sieci, w których należy chronić tylko podzbiór dokumentów lub wiadomości e-mail wymagających specjalnego zarządzania danymi.

## Jak działa automatyczna klasyfikacja?

W portalu Azure można użyć wstępnie zdefiniowanych wzorców, takich jak numer karty kredytowej lub numer ubezpieczenia społecznego w USA. Możesz zdefiniować niestandardowy ciąg lub szablon będący warunkiem automatycznej klasyfikacji.

Podobny przykład pojawia się w [samouczku Szybki start dla usługi Azure Information Protection](infoprotect-quick-start-tutorial.md). 

Dokładność klasyfikacji zależy od sposobu skonfigurowania reguły klasyfikacji, która opiera się na warunkach. Obecnie warunki obsługują wzorce tekstu i wyrażenia regularne. Aby uzyskać informacje o wszystkich opcjach dostępnych podczas używania wersji zapoznawczej wraz z sugerowanymi przykładami do testowania, zobacz [Konfigurowanie warunków klasyfikacji automatycznej i zalecanej dla usługi Azure Information Protection](../deploy-use/configure-policy-classification.md). Wykrywanie jest uruchamiane przy zapisywaniu dokumentu lub wysyłaniu wiadomości e-mail.

Aby zapewnić najlepszą jakość obsługi i ciągłość prowadzenia działalności biznesowej, warto rozpocząć od wydawania zaleceń użytkownikom, a nie od wprowadzania czynności w pełni zautomatyzowanych. Dzięki temu użytkownicy mają wybór pomiędzy akceptacją etykietowania lub akcji ochronnych a odrzuceniem takiego zalecenia.   

## Czy usługa Azure Information Protection monituje użytkowników o samodzielne klasyfikowanie plików zamiast używania automatycznej klasyfikacji? 

Tak. Użyj portalu Azure, aby skonfigurować, czy używać automatycznej klasyfikacji, czy wydawać zalecenie użytkownikom, nadając opcji **Wybierz sposób stosowania etykiet: automatycznie lub zalecając użytkownikowi ** wartość **Zalecenie**.

Podobny przykład pojawia się w [samouczku Szybki start dla usługi Azure Information Protection](infoprotect-quick-start-tutorial.md).  

## Czy można wymusić klasyfikowania wszystkich dokumentów?

Tak. Jeśli wymagasz, aby użytkownicy klasyfikowali wszystkie zapisywane pliki, w portalu Azure należy opcji **Wszystkie dokumenty i wiadomości e-mail muszą mieć etykietę** nadać wartość **Wł.**. 

## Czy można usunąć klasyfikację z pliku?

Tak. Aby usunąć klasyfikację z pliku, otwórz plik w aplikacji pakietu Office, kliknij ikonę **Edytuj etykietę** na pasku Information Protection, kliknij ikonę **Usuń etykietę**, a następnie kliknij przycisk **OK**, aby potwierdzić operację. 


## Czy można monitować użytkowników o uzasadnienie, dlaczego zmieniają poziom klasyfikacji?

Tak. Aby się upewnić, że użytkownicy uzasadniają swoje zmiany klasyfikacji, w witrynie Azure Portal należy opcji **Użytkownik musi podać uzasadnienie, aby ustawić niższą etykietę klasyfikacji, usunąć etykietę lub usunąć ochronę** nadać wartość **Włączone**. W takim przypadku wykonywana czynność oraz stosowne uzasadnienie zostaną zapisane w ich lokalnym dzienniku zdarzeń systemu Windows: **Application**  >  **Microsoft Azure Information Protection**.

## Jak automatycznie chronić zawartość po jej zakwalifikowaniu?

W portalu Azure można wybrać szablon usługi Rights Management, aby automatycznie chronić zawartość zgodnie z określonym poziomem klasyfikacji.

Podobny przykład pojawia się w [samouczku Szybki start dla usługi Azure Information Protection](infoprotect-quick-start-tutorial.md). Aby uzyskać więcej informacji, zobacz [Konfigurowanie etykiety w celu zastosowania ochrony usługi Rights Management](../deploy-use/configure-policy-protection.md).

## Czy plik może mieć dwie różne klasyfikacje?

W razie potrzeby można utworzyć etykiety podrzędne, aby lepiej opisać podkategorie konkretnej etykiety ważności. Na przykład etykieta główna **Tajne** może zawierać etykiety podrzędne, takie jak **Tajne\prawne** i **Tajne\finanse**. Różnym etykietom podrzędnym można przypisać różne wizualne oznaczenia klasyfikacji i różne szablony usługi Rights Management.

Chociaż obecnie można ustawić oznaczenia wizualne, ochronę i warunki na obu poziomach, przy korzystaniu z poziomów podrzędnych te ustawienia należy konfigurować tylko dla poziomów podrzędnych. W przypadku skonfigurowania tych samych ustawień na etykiecie nadrzędnej i jej etykiecie podrzędnej ustawienia na poziomie podrzędnym mają pierwszeństwo.

## Czy gdy wiadomość e-mail jest oznaczona, pewne załączniki automatycznie uzyskają tę samą etykietę?

Nie. Jeśli wiadomość e-mail zawierająca załączniki zostanie oznaczona, załączniki te nie odziedziczą tej samej etykiety. Załączniki pozostaną bez etykiety lub zachowają oddzielnie przydzieloną etykietę. Jednak jeśli etykieta wiadomości e-mail zawiera ochronę, ochrona ta jest stosowana także do załączników.

## Jak rozwiązania DLP i inne aplikacje integrują się z usługą Azure Information Protection?

Ponieważ usługa Azure Information Protection używa do klasyfikacji trwałych metadanych, w tym etykiety w postaci zwykłego tekstu, te informacje są odczytywane przez rozwiązania DLP i inne aplikacje. W plikach metadane te są przechowywane we właściwościach niestandardowych; w wiadomościach e-mail znajdują się one w nagłówkach.

## Jak działa śledzenie i odwoływanie dokumentów w usłudze Azure Information Protection?

Śledzenie dokumentów w przypadku plików sklasyfikowanych i chronionych za pomocą usługi Azure Information Protection współdziała z ochroną usługi Azure Rights Management i aplikacją RMS sharing. Możesz także uzyskać dostęp do witryny śledzenia dokumentów, używając klienta usługi Azure Information Protection (w wersji 1.0.233 lub nowszej): 

- W aplikacji pakietu Office na karcie **Narzędzia główne** w grupie **Ochrona** kliknij kolejno pozycje **Chroń** > **Śledź użycie**. 

Aby uzyskać więcej informacji, zobacz artykuł [Śledzenie i odwoływanie dokumentów podczas używania aplikacji RMS sharing](../rms-client/sharing-app-track-revoke.md).

## Czy można kontrolować, którzy użytkownicy mogą używać usługi Azure Information Protection do klasyfikowania i ochrony zawartości?

Można ograniczyć grono użytkowników, którzy mogą klasyfikować i chronić dane, kontrolując dystrybucję klienta usługi Azure Information Protection. 

Pliki i wiadomości e-mail sklasyfikowane przez usługę Azure Information Protection mogą być używane lub edytowane przez dowolnego użytkownika, z użyciem lub bez zainstalowanego klienta usługi Azure Information Protection. 

## Jak zgłosić problem lub wysłać opinię dotyczącą usługi Azure Information Protection?

Jeśli występuje problem z usługą Azure Information Protection i jest używana bieżąca wersja klienta: w aplikacji pakietu Office na karcie **Narzędzia główne** w grupie **Ochrona** kliknij pozycję **Chroń**, a następnie kliknij pozycję **Pomoc i opinia**. W oknie dialogowym **Microsoft Azure Information Protection** kliknij przycisk **Wyślij opinię**. Spowoduje to wysłanie wiadomości e-mail do zespołu Information Protection i automatyczne dołączenie plików dziennika z Twojego komputera służących do zdiagnozowania problemu. 

Jeśli masz pytania lub opinie, użyj witryny usługi Yammer [Azure Information Protection](https://www.yammer.com/askipteam/). 


<!--HONumber=Sep16_HO4-->


