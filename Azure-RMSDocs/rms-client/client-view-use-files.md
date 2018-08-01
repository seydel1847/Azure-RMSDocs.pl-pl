---
title: Wyświetlanie i używanie dokumentów chronionych przy użyciu klienta usługi AIP
description: Instrukcje dotyczące wyświetlania i używania dokumentu chronionego, wymagającego posiadania zainstalowanego klienta usługi Azure Information Protection.
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 04/17/2018
ms.topic: article
ms.prod: ''
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: ce1c7d4c-b5ff-4672-8b9a-a72129bac992
ms.reviewer: esaggese
ms.suite: ems
ms.openlocfilehash: cfeeb1f9519b94657499be06e448f0eb726a741f
ms.sourcegitcommit: 44ff610dec678604c449d42cc0b0863ca8224009
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/31/2018
ms.locfileid: "39371819"
---
# <a name="user-guide-view-and-use-files-that-have-been-protected-by-rights-management"></a>Podręcznik użytkownika: Wyświetlanie i używanie plików chronionych przez usługę Rights Management

>*Dotyczy: Active Directory Rights Management Services, [usługi Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection), system Windows 10, Windows 8.1, Windows 8, Windows 7 z dodatkiem SP1*

Chronione dokumenty można często wyświetlić, otwierając je w zwykły sposób. Na przykład można kliknąć dwukrotnie załącznik w wiadomości e-mail lub plik w Eksploratorze plików bądź kliknąć link do pliku.

Jeśli pliki nie otwierają się natychmiast, prawdopodobnie będzie można je otworzyć za pomocą **przeglądarki usługi Azure Information Protection**. Ten program może otworzyć chronione pliki tekstowe, chronione pliki obrazów, chronione pliki PDF i wszystkie pliki z rozszerzeniem **pfile**.

Przeglądarka jest instalowana automatycznie podczas instalacji klienta usługi Azure Information Protection, ale można ją także zainstalować oddzielnie. Zarówno klienta, jak i przeglądarkę można zainstalować ze strony usługi [Microsoft Azure Information Protection](https://go.microsoft.com/fwlink/?LinkId=303970) w witrynie internetowej firmy Microsoft. Aby uzyskać więcej informacji dotyczących instalowania klienta, zobacz temat [Pobieranie i instalowanie klienta usługi Azure Information Protection](install-client-app.md).

> [!NOTE]
> Chociaż po zainstalowaniu klienta dostępnych jest więcej funkcji, wymaga to uprawnień administratora lokalnego, a dodatkowo — w celu zapewnienia pełnej funkcjonalności — wymaga także odpowiednich usług dla organizacji:
> 
>-Azure Information Protection
> 
>— Usługi azure Rights Management
> 
>-Active Directory Rights Management Services 
> 
> Zainstaluj przeglądarkę, jeśli otrzymany przez Ciebie chroniony dokument został wysłany przez osobę z innej organizacji lub jeśli nie masz na komputerze uprawnień administratora lokalnego.

Aby można było otworzyć dokument chroniony, aplikacja musi być oznaczona jako „obsługująca usługę RMS”. Aplikacje pakietu Office i przeglądarka usługi Azure Information Protection stanowią przykład aplikacji obsługujących usługę RMS. Aby wyświetlić listę aplikacji według typu i obsługiwanych urządzeń, zobacz tabelę [aplikacji obsługujących usługę RMS](../get-started/requirements-applications.md#rms-enlightened-applications).  
## <a name="messagerpmsg-as-an-email-attachment"></a>Message.rpmsg jako załącznik wiadomości e-mail

Jeśli załącznikiem do wiadomości e-mail jest plik **message.rpmsg**, ten plik nie jest dokumentem chronionym, lecz chronioną wiadomością e-mail, która jest wyświetlana jako załącznik. Do wyświetlenia takiej chronionej wiadomości e-mail na komputerze PC z systemem Windows nie można użyć przeglądarki usługi Azure Information Protection. Zamiast tego potrzebujesz aplikacji poczty e-mail dla Windows, która obsługuje ochronę usługi Rights Management, takich jak Outlook pakietu Office. Alternatywą jest skorzystanie z programu Outlook w sieci Web.

Jednak jeśli masz urządzenie z systemem iOS lub Android, można użyć aplikacji usługi Azure Information Protection do otwierania chronionych wiadomości e-mail. Aplikację dla takich urządzeń przenośnych można pobrać ze strony usługi [Microsoft Azure Information Protection](https://go.microsoft.com/fwlink/?LinkId=303970) w witrynie internetowej firmy Microsoft.

## <a name="prompts-for-authentication"></a>Monity o uwierzytelnienie

Zanim będzie można wyświetlić chroniony plik, użyta usługa Rights Management musi potwierdzić, że masz uprawnienia do wyświetlenia pliku. Usługa ma to potwierdzenie, sprawdzając nazwę użytkownika i hasło. W niektórych przypadkach te poświadczenia mogą być buforowane, a nie zobaczysz monit z pytaniem, możesz się zalogować. W innych przypadkach wyświetlany jest monit o podanie poświadczeń.

Jeśli Twoja organizacja nie ma konta oparte na chmurze do użycia (dla usługi Office 365 lub Azure) i nie korzystają z wersji równoważne lokalnie (AD RMS), masz dwie opcje:

- Jeśli zostały wysłane chronioną wiadomość e-mail, postępuj zgodnie z instrukcjami, aby zalogować się przy użyciu dostawcy tożsamości społecznościowych (np. Google, aby utworzyć konto usługi Gmail) lub poprosić o jednorazowy kod dostępu.

- Możesz poprosić o utworzenie bezpłatnego konta z wykorzystaniem Twoich poświadczeń, tak aby mogli otworzyć dokumentów, które są chronione przez usługę Rights Management. Aby zastosować dla tego konta, kliknij link, aby poprosić o [RMS dla użytkowników indywidualnych](http://go.microsoft.com/fwlink/?LinkId=309469) i użyj swój adres e-mail firmy, a nie osobistego adresu e-mail. 

## <a name="to-view-and-use-a-protected-document"></a>Aby wyświetlić dokument chroniony i korzystać z niego

1. Otwórz plik chroniony (na przykład przez dwukrotne kliknięcie pliku lub załącznika bądź kliknięcie linku do pliku). Jeśli zostanie wyświetlony monit o wybranie aplikacji, wybierz opcję **Przeglądarka usługi Azure Information Protection**. 

2. Jeśli zostanie wyświetlona strona do **logowania** lub **rejestrowania**, kliknij opcję **Zaloguj** i wprowadź swoje poświadczenia. Jeśli plik chroniony został wysłany do Ciebie jako załącznik, musisz określić ten sam adres e-mail, który został użyty przez nadawcę do wysłania pliku do Ciebie.
    
    Jeśli nie masz konta spełniającego wymagania, zapoznaj się z sekcją [Monity o uwierzytelnienie](#prompts-for-authentication) na tej stronie.

3. Wersja pliku tylko do odczytu zostanie otwarta w **Przeglądarce usługi Azure Information Protection**. Jeśli masz wystarczające uprawnienia, możesz wydrukować plik i go edytować. 

    Swoje uprawnienia do pliku możesz sprawdzić, klikając opcję **Uprawnienia**. Jeśli chcesz poprosić o nową wersję pliku z dodatkowymi uprawnieniami, w oknie dialogowym **Uprawnienia** możesz również zidentyfikować właściciela pliku do kontaktu.
    
    Aby uzyskać bardziej szczegółowe informacje o uprawnieniach i prawach użytkowania, które każde z nich zawiera, zobacz temat [Prawa uwzględnione w poziomach uprawnień](../deploy-use/configure-usage-rights.md#rights-included-in-permissions-levels).

4. Aby edytować plik, kliknij przycisk **Zapisz jako**, która pozwala zapisać plik bez etykiety i brak ochrony do jego oryginalne rozszerzenie nazwy pliku. Następnie plik można edytować za pomocą aplikacji skojarzonej z tym typem pliku. 
    
    Po zakończeniu edycji pliku w Eksploratorze plików kliknij prawym przyciskiem myszy plik, aby ponownie zastosować etykietę, która z kolei ponowne zastosowanie ochrony.

5. Jeśli masz do otwarcia dodatkowe pliki chronione, możesz przejść do nich bezpośrednio z przeglądarki, korzystając z opcji **Otwórz**. Wybrane przez Ciebie pliki zastępują w przeglądarce oryginalny plik. 

> [!TIP]
> Jeśli nie można otworzyć pliku chronionego, a pełna zainstalowanego klienta usługi Azure Information Protection, spróbuj **Resetowanie ustawień** opcji. Dostęp do tej opcji z aplikacji pakietu Office, wybierz **Chroń** przycisk > **Pomoc i opinie** > **Resetowanie ustawień**. 
> 
> [Więcej informacji na temat opcji resetowania ustawień](client-admin-guide.md#more-information-about-the-reset-settings-option)

## <a name="other-instructions"></a>Inne instrukcje
Więcej instrukcji z podręcznika użytkownika usługi Azure Information Protection:

-   [Co chcesz zrobić?](client-user-guide.md#what-do-you-want-to-do)

