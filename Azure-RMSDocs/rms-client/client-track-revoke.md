---
title: "Śledzenie i odwoływanie dokumentów chronionych podczas korzystania z usługi Azure Information Protection | Azure Information Protection"
description: "Po włączeniu ochrony dokumentów można śledzić ich użycie. W razie potrzeby można również odwołać dostęp do tych dokumentów, jeśli pewne osoby stracą prawo do ich czytania."
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 12/07/2016
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: 643c762e-23ca-4b02-bc39-4e3eeb657a1d
ms.reviewer: esaggese
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 7068e0529409eb783f16bc207a17be27cd5d82a8
ms.openlocfilehash: 54abc32a6065bb3863cf55b42466250f8fc9c634


---

# <a name="track-and-revoke-your-documents-when-you-use-azure-information-protection"></a>Śledzenie i odwoływanie dokumentów podczas korzystania z usługi Azure Information Protection

>*Dotyczy: Azure Information Protection, Windows 10, Windows 8.1, Windows 8, Windows 7 z dodatkiem SP1*

**[Ta wersja klienta jest w wersji zapoznawczej i może ulec zmianie.]**

Po włączeniu ochrony dokumentów za pomocą usługi Azure Information Protection można śledzić użycie tych dokumentów. W razie potrzeby można również odwołać dostęp do nich, jeśli pewne osoby stracą prawo do ich czytania. W tym celu należy użyć **witryny śledzenia dokumentów** dostępnej z komputerów z systemem Windows, komputerów Mac, a nawet tabletów i telefonów.

<div style="padding-top: 56.25%; position: relative; width: 100%;">
<iframe style="position: absolute;top: 0;left: 0;right: 0;bottom: 0;" width="100%" height="100%" src="https://channel9.msdn.com/Series/Information-Protection/Azure-RMS-Document-Tracking-and-Revocation/player" frameborder="0" allowfullscreen></iframe>
</div>

Po uzyskaniu dostępu do tej witryny zaloguj się, aby śledzić swoje dokumenty. Jeśli Twoja organizacja ma [subskrypcję obsługującą śledzenie i odwoływanie dokumentów](https://www.microsoft.com/en-us/cloud-platform/azure-information-protection-features) oraz masz licencję na tę subskrypcję, możesz sprawdzić, kto próbował otworzyć zabezpieczone pliki i czy próba ta zakończyła się powodzeniem (nastąpiło pomyślne uwierzytelnienie). Widoczna jest także data i godzina próby otwarcia dokumentu oraz lokalizacja tego zdarzenia. Ponadto:

-   Jeśli chcesz zatrzymać udostępnianie dokumentu: kliknij pozycję **Odwołaj dostęp**, podaj okres, przez jaki dokument będzie jeszcze dostępny, i zdecyduj, czy chcesz powiadomić o odwołaniu dostępu osoby, którym dokument był wcześniej udostępniony. Jeśli się na to zdecydujesz, przygotuj niestandardową wiadomość dla nich. Odwołanie dokumentu nie powoduje jego usunięcia, ale blokuje możliwość otwierania go przez autoryzowanych użytkowników.

-   Jeśli chcesz wyeksportować plik do programu Excel: kliknij pozycję **Eksportuj do pliku CSV**, aby móc modyfikować dane i tworzyć własne widoki oraz wykresy.

-   Jeśli chcesz skonfigurować powiadomienia e-mail: kliknij pozycję **Ustawienia** i zdecyduj, czy chcesz otrzymywać pocztą e-mail powiadomienia o dostępie do dokumentu.

- Jeśli chcesz śledzić i odwoływać dokumenty udostępnione innym: administratorzy usługi Azure Information Protection mogą śledzić i odwoływać dokumenty chronione dla innych użytkowników, klikając ikonę administratora. Ta ikona jest widoczna tylko dla administratorów.

-   Jeśli masz pytania lub chcesz wyrazić swoją opinię na temat witryny śledzenia dokumentów: kliknij ikonę Pomoc, aby uzyskać dostęp do artykułu [Często zadawane pytania dotyczące śledzenia dokumentów](http://go.microsoft.com/fwlink/?LinkId=523977).

## <a name="using-office-to-access-the-document-tracking-site"></a>Dostęp do witryny śledzenia dokumentów za pomocą pakietu Office

-   W przypadku aplikacji pakietu Office (Word, Excel, PowerPoint i Outlook): na karcie **Narzędzia główne** w grupie **Ochrona** kliknij pozycję **Chroń** > **Śledź użycie**.

Jeśli opcje ochrony nie są wyświetlone, możliwe, że klient usługi Azure Information Protection nie jest zainstalowany na danym komputerze, Twoje aplikacje pakietu Office muszą zostać uruchomione ponownie albo trzeba ponownie uruchomić komputer w celu ukończenia instalacji. Aby uzyskać więcej informacji o sposobie instalowania klienta usługi Azure Information Protection, zobacz temat [Pobieranie i instalowanie klienta usługi Azure Information Protection](install-client-app.md).


### <a name="other-ways-to-track-and-revoke-your-documents"></a>Inne metody śledzenia i odwoływania dokumentów
Oprócz śledzenia dokumentów na komputerach z systemem Windows przy użyciu aplikacji pakietu Office można użyć także następujących opcji alternatywnych:

-   **W przeglądarce sieci Web**: ta metoda działa w przypadku wszystkich obsługiwanych urządzeń.

-   **W Eksploratorze plików**: ta metoda działa na komputerach z systemem Windows.

#### <a name="using-a-web-browser-to-access-the-doc-tracking-site"></a>Otwieranie witryny śledzenia dokumentów za pomocą przeglądarki sieci Web

-   Przy użyciu obsługiwanej przeglądarki przejdź do [witryny śledzenia dokumentów](https://go.microsoft.com/fwlink/?LinkId=529562).

    Obsługiwane przeglądarki: zaleca się korzystanie z przeglądarki Internet Explorer w wersji 10 lub nowszej, jednak dostęp do witryny śledzenia dokumentów można uzyskać przy użyciu dowolnej z poniższych przeglądarek:

    -   Internet Explorer: wersja 10 lub nowsza

    -   Internet Explorer 9 z poprawką MS12-037: zbiorcza aktualizacja zabezpieczeń programu Internet Explorer z 12 czerwca 2012 r.

    -   Mozilla Firefox: wersja 12 lub nowsza

    -   Apple Safari 5: wersja 5 lub nowsza

    -   Google Chrome: wersja 18 lub nowsza

#### <a name="using-file-explorer-to-access-the-doc-tracking-site"></a>Otwieranie witryny śledzenia dokumentów za pomocą Eksploratora plików

-   Kliknij plik prawym przyciskiem myszy, wybierz opcję **Klasyfikuj i chroń (wersja zapoznawcza)**, a następnie w **przeglądarce usługi Azure Information Protection** wybierz ikonę Śledź użycie.


## <a name="other-instructions"></a>Inne instrukcje
Aby uzyskać instrukcje dotyczące wykonywania określonych czynności, zobacz następujące sekcje z podręcznika użytkownika usługi Azure Information Protection:

-   [Co chcesz zrobić?](client-user-guide.md#what-do-you-want-to-do)

[!INCLUDE[Commenting house rules](../includes/houserules.md)]


<!--HONumber=Jan17_HO4-->


