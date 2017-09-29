---
title: "Wyświetlanie i używanie dokumentów chronionych przy użyciu klienta usługi AIP"
description: "Instrukcje dotyczące wyświetlania i używania dokumentu chronionego, wymagającego posiadania zainstalowanego klienta usługi Azure Information Protection."
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 09/22/2017
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: ce1c7d4c-b5ff-4672-8b9a-a72129bac992
ms.reviewer: esaggese
ms.suite: ems
ms.openlocfilehash: 8ed2480892d5a48075d986ee64733b0144bbc5b4
ms.sourcegitcommit: cd3320fa34acb90f05d5d3e0e83604cdd46bd9a9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/23/2017
---
# <a name="view-and-use-files-that-have-been-protected-by-rights-management"></a>Wyświetlanie i używanie plików chronionych przez usługę Rights Management

>*Dotyczy: usługi Active Directory Rights Management, Azure Information Protection, Windows 10, Windows 8.1, Windows 8, Windows 7 z dodatkiem SP1*

Chronione dokumenty można często wyświetlić, otwierając je w zwykły sposób. Na przykład można kliknąć dwukrotnie załącznik w wiadomości e-mail lub plik w Eksploratorze plików bądź kliknąć link do pliku.

Jeśli pliki nie otwierają się natychmiast, prawdopodobnie będzie można je otworzyć za pomocą **przeglądarki usługi Azure Information Protection**. Ten program może otworzyć chronione pliki tekstowe, chronione pliki obrazów, chronione pliki PDF i wszystkie pliki z rozszerzeniem **pfile**.

Przeglądarka jest instalowana automatycznie podczas instalacji klienta usługi Azure Information Protection, ale można ją także zainstalować oddzielnie. Zarówno klienta, jak i przeglądarkę można zainstalować ze strony usługi [Microsoft Azure Information Protection](https://go.microsoft.com/fwlink/?LinkId=303970) w witrynie internetowej firmy Microsoft. Aby uzyskać więcej informacji dotyczących instalowania klienta, zobacz temat [Pobieranie i instalowanie klienta usługi Azure Information Protection](install-client-app.md).

> [!NOTE]
> Chociaż po zainstalowaniu klienta dostępnych jest więcej funkcji, wymaga to uprawnień administratora lokalnego, a dodatkowo — w celu zapewnienia pełnej funkcjonalności — wymaga także odpowiednich usług dla organizacji:
> 
> - Azure Information Protection
> 
> - Azure Rights Management
> 
> - Usługi Active Directory Rights Management 
> 
> Zainstaluj przeglądarkę, jeśli otrzymany przez Ciebie chroniony dokument został wysłany przez osobę z innej organizacji lub jeśli nie masz na komputerze uprawnień administratora lokalnego.

Aby można było otworzyć dokument chroniony, aplikacja musi być oznaczona jako „obsługująca usługę RMS”. Aplikacje pakietu Office i przeglądarka usługi Azure Information Protection stanowią przykład aplikacji obsługujących usługę RMS. Aby wyświetlić listę aplikacji według typu i obsługiwanych urządzeń, zobacz tabelę [aplikacji obsługujących usługę RMS](../get-started/requirements-applications.md#rms-enlightened-applications).  
## <a name="messagerpmsg-as-an-email-attachment"></a>Message.rpmsg jako załącznik wiadomości e-mail

Jeśli załącznikiem do wiadomości e-mail jest plik **message.rpmsg**, ten plik nie jest dokumentem chronionym, lecz chronioną wiadomością e-mail, która jest wyświetlana jako załącznik. Do wyświetlenia takiej chronionej wiadomości e-mail na komputerze PC z systemem Windows nie można użyć przeglądarki usługi Azure Information Protection. Zamiast tego należy użyć aplikacji poczty e-mail dla systemu Windows, która obsługuje ochronę usługi Rights Management, takiej jak Outlook z pakietu Office. Alternatywą jest skorzystanie z programu Outlook w sieci Web.

Jednak jeśli masz urządzenie z systemem iOS lub Android, można użyć aplikacji usługi Azure Information Protection do otwierania chronionych wiadomości e-mail. Aplikację dla takich urządzeń przenośnych można pobrać ze strony usługi [Microsoft Azure Information Protection](https://go.microsoft.com/fwlink/?LinkId=303970) w witrynie internetowej firmy Microsoft.

## <a name="prompts-for-authentication"></a>Monity o uwierzytelnienie

Zanim będzie można wyświetlić chroniony plik, użyta usługa Rights Management musi potwierdzić, że masz uprawnienia do wyświetlenia pliku. W tym celu usługa sprawdza Twoją nazwę użytkownika i hasło. W niektórych sytuacjach te dane są buforowane, w związku z czym monit o podanie poświadczeń nie zostanie wyświetlony. W pozostałych przypadkach jest wyświetlany monit o podanie poświadczeń.

Jeśli Twoja organizacja ma konto oparte na chmurze, można użyć (dla usługi Office 365 lub Azure) i nie korzysta z wersji lokalnej równoważne (AD RMS), masz dwie opcje:

- Jeśli zostały wysłane chronioną wiadomość e-mail, postępuj zgodnie z instrukcjami, aby zalogować się przy użyciu dostawcy tożsamości społecznościowych (takich jak Google dla konta usługi Gmail) lub o jednorazowy kod dostępu.

- Możesz poprosić o utworzenie bezpłatnego konta z wykorzystaniem Twoich poświadczeń, dzięki czemu mogą otwierać dokumenty, które są chronione przez usługę Rights Management. Aby zastosować dla tego konta, kliknij łącze, aby zastosować dla [RMS dla użytkowników indywidualnych](http://go.microsoft.com/fwlink/?LinkId=309469) i użyj swojego służbowego adresu e-mail, a nie adresu prywatnego. 

## <a name="to-view-and-use-a-protected-document"></a>Aby wyświetlić dokument chroniony i korzystać z niego

1. Otwórz plik chroniony (na przykład przez dwukrotne kliknięcie pliku lub załącznika bądź kliknięcie linku do pliku). Jeśli zostanie wyświetlony monit o wybranie aplikacji, wybierz opcję **Przeglądarka usługi Azure Information Protection**. 

2. Jeśli zostanie wyświetlona strona do **logowania** lub **rejestrowania**, kliknij opcję **Zaloguj** i wprowadź swoje poświadczenia. Jeśli plik chroniony został wysłany do Ciebie jako załącznik, musisz określić ten sam adres e-mail, który został użyty przez nadawcę do wysłania pliku do Ciebie.
    
    Jeśli nie masz konta spełniającego wymagania, zapoznaj się z sekcją [Monity o uwierzytelnienie](#prompts-for-authentication) na tej stronie.

3. Wersja pliku tylko do odczytu zostanie otwarta w **Przeglądarce usługi Azure Information Protection**. Jeśli masz wystarczające uprawnienia, możesz wydrukować plik i go edytować. 

    Swoje uprawnienia do pliku możesz sprawdzić, klikając opcję **Uprawnienia**. Jeśli chcesz poprosić o nową wersję pliku z dodatkowymi uprawnieniami, w oknie dialogowym **Uprawnienia** możesz również zidentyfikować właściciela pliku do kontaktu.
    
    Aby uzyskać bardziej szczegółowe informacje o uprawnieniach i prawach użytkowania, które każde z nich zawiera, zobacz temat [Prawa uwzględnione w poziomach uprawnień](../deploy-use/configure-usage-rights.md#rights-included-in-permissions-levels).

4. Aby edytować plik, kliknij opcję **Zapisz jako**, która pozwala zapisać plik bez ochrony z jego oryginalnym rozszerzeniem nazwy pliku. Następnie plik można edytować za pomocą aplikacji skojarzonej z tym typem pliku.

5. Jeśli masz do otwarcia dodatkowe pliki chronione, możesz przejść do nich bezpośrednio z przeglądarki, korzystając z opcji **Otwórz**. Wybrane przez Ciebie pliki zastępują w przeglądarce oryginalny plik. 

> [!TIP]
> Jeśli nie można otworzyć pliku chronionego, można użyć **Uruchom diagnostykę** opcję **Chroń** > **Pomoc i opinie** usługi Azure Information Protection Klient do sprawdzania problemów występujących na komputerze, który może uniemożliwić chronionego dokumentu otwierania.

## <a name="other-instructions"></a>Inne instrukcje
Więcej instrukcji z podręcznika użytkownika usługi Azure Information Protection:

-   [Co chcesz zrobić?](client-user-guide.md#what-do-you-want-to-do)


[!INCLUDE[Commenting house rules](../includes/houserules.md)]