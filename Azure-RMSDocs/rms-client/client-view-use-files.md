---
title: "Wyświetlanie i używanie plików chronionych przez usługę Rights Management | Azure Information Protection"
description: "Instrukcje dotyczące wyświetlania i używania pliku chronionego, wymagającego posiadania zainstalowanego klienta usługi Azure Information Protection."
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 12/07/2016
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: ce1c7d4c-b5ff-4672-8b9a-a72129bac992
ms.reviewer: esaggese
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 5d1a5e3b85d5450bcb2064a6c3b95e6ad802eea3
ms.openlocfilehash: b08b7e055f05729057f5137a7d523ff452a58f48


---

# <a name="view-and-use-files-that-have-been-protected-by-rights-management"></a>Wyświetlanie i używanie plików chronionych przez usługę Rights Management

>*Dotyczy: usługi Active Directory Rights Management, Azure Information Protection, Windows 10, Windows 8.1, Windows 8, Windows 7 z dodatkiem SP1*

**[Ta wersja klienta jest w wersji zapoznawczej i może ulec zmianie.]**

Gdy [klient usługi Azure Information Protection jest zainstalowany na komputerze](install-client-app.md), można wyświetlić plik chroniony, po prostu otwierając go. Na przykład można kliknąć dwukrotnie załącznik w wiadomości e-mail lub plik w Eksploratorze plików bądź kliknąć link do pliku.

> [!NOTE]
> Zanim będzie można wyświetlić chroniony plik, usługa Rights Management musi potwierdzić, że masz uprawnienia do wyświetlenia pliku (sprawdzana jest nazwa użytkownika i hasło). W niektórych sytuacjach te dane są buforowane, w związku z czym monit o podanie poświadczeń nie zostanie wyświetlony. W pozostałych przypadkach jest wyświetlany monit o podanie poświadczeń.
>
> Jeśli Twoja organizacja nie ma konta opartego na chmurze, z którego możesz skorzystać (dla usługi Office 365 lub Azure), ani nie używa usług AD RMS, możesz poprosić o utworzenie bezpłatnego konta z wykorzystaniem Twoich poświadczeń, co umożliwi Ci otwieranie plików chronionych za pomocą usług Rights Management:
>
> -   Aby poprosić o utworzenie konta, kliknij link [usług RMS dla użytkowników indywidualnych](http://go.microsoft.com/fwlink/?LinkId=309469).
>
>     Podczas tworzenia konta użyj swojego służbowego adresu e-mail, a nie adresu prywatnego. Jeśli tworzysz konto w związku z otrzymaniem chronionego załącznika pocztą e-mail, użyj tego samego adresu e-mail, który został użyty przez nadawcę do wysłania tej wiadomości e-mail do Ciebie.
> -   Aby uzyskać więcej informacji, zobacz [Usługa RMS dla użytkowników indywidualnych i usługa Azure Rights Management](../understand-explore/rms-for-individuals.md).

## <a name="to-view-and-use-a-protected-file"></a>Aby wyświetlić plik chroniony i skorzystać z niego

1. Otwórz plik chroniony (na przykład przez dwukrotne kliknięcie pliku lub załącznika bądź kliknięcie linku do pliku). Jeśli zostanie wyświetlony monit o wybranie aplikacji, wybierz opcję **Przeglądarka usługi Azure Information Protection (wersja zapoznawcza)**. 

2. Jeśli zostanie wyświetlona strona do **logowania** lub **rejestrowania**, kliknij opcję **Zaloguj** i wprowadź swoje poświadczenia. Jeśli plik chroniony został wysłany do Ciebie jako załącznik, musisz określić ten sam adres e-mail, który został użyty przez nadawcę do wysłania pliku do Ciebie.
    
    Jeśli nie masz zaakceptowanego konta, zobacz Uwagi w górnej części strony. Utwórz bezpłatne konto i wróć do niniejszych instrukcji.

3. Wersja pliku tylko do odczytu zostanie otwarta w **Przeglądarce usługi Azure Information Protection**. Jeśli masz wystarczające uprawnienia, możesz wydrukować plik i go edytować. 

    Swoje uprawnienia do pliku możesz sprawdzić, klikając opcję **Uprawnienia**. Jeśli chcesz poprosić o nową wersję pliku z dodatkowymi uprawnieniami, w oknie dialogowym **Uprawnienia** możesz również zidentyfikować właściciela pliku do kontaktu.
    
    Aby uzyskać bardziej szczegółowe informacje o uprawnieniach i prawach użytkowania, które każde z nich zawiera, zobacz temat [Prawa uwzględnione w poziomach uprawnień](../deploy-use/configure-usage-rights.md#rights-included-in-permissions-levels).

4. Aby edytować plik, kliknij opcję **Zapisz jako**, która pozwala zapisać plik bez ochrony z jego oryginalnym rozszerzeniem nazwy pliku. Następnie plik można edytować za pomocą aplikacji skojarzonej z tym typem pliku.

5. Jeśli masz do otwarcia dodatkowe pliki chronione, możesz przejść do nich bezpośrednio z przeglądarki, korzystając z opcji **Otwórz**. Wybrane przez Ciebie pliki zastępują w przeglądarce oryginalny plik. 

> [!TIP]
> Jeśli nie można otworzyć pliku chronionego, pobierz [narzędzie Analizator RMS](https://www.microsoft.com/en-us/download/details.aspx?id=46437) i skorzystaj z niego. Postępuj zgodnie z instrukcjami wyświetlanymi w narzędziu, aby sprawdzić komputer pod kątem problemów, które mogą uniemożliwić otwarcie chronionego dokumentu.


## <a name="other-instructions"></a>Inne instrukcje
Aby uzyskać instrukcje dotyczące wykonywania określonych czynności, zobacz następujące sekcje z podręcznika użytkownika usługi Azure Information Protection:

-   [Co chcesz zrobić?](client-user-guide.md#what-do-you-want-to-do)



<!--HONumber=Dec16_HO1-->


