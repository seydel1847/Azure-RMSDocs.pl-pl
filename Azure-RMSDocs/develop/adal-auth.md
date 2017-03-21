---
title: "Konfigurowanie aplikacji do uwierzytelniania ADAL — AIP"
description: "Czynności służące do konfigurowania aplikacji usług Azure Information Protection na potrzeby uwierzytelniania na podstawie biblioteki Azure ADAL"
keywords: uwierzytelnianie, RMS, ADAL, Information Protection,
author: bruceperlerms
ms.author: bruceper
manager: mbaldwin
ms.date: 03/13/2017
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: f89f59b7-33d1-4ab3-bb64-1e9bda269935
audience: developer
ms.reviewer: shubhamp
ms.suite: ems
ms.openlocfilehash: 27674aac7962c7a2f79fda8ccd6f90c366574b9b
ms.sourcegitcommit: 262f88c4f46e29f3747271276c62913b4cefe4f7
translationtype: HT
---
# <a name="configure-your-app-for-adal-authentication"></a>Konfigurowanie aplikacji do uwierzytelniania ADAL

W tym temacie opisano procedurę konfigurowania aplikacji do uwierzytelniania na podstawie biblioteki Azure Active Directory Authentication Library (ADAL).

## <a name="azure-authentication-setup"></a>Konfigurowanie uwierzytelniania na platformie Azure

Potrzebne są następujące elementy:

- [Subskrypcja usługi Microsoft Azure](https://azure.microsoft.com/en-us/) (wystarczy bezpłatna wersja próbna). Aby uzyskać więcej informacji, zobacz [Jak użytkownicy rejestrują się w usłudze RMS dla użytkowników indywidualnych](../understand-explore/rms-for-individuals-user-sign-up.md)
- Subskrypcja usługi Microsoft Azure Rights Management (wystarczy bezpłatne konto w [usłudze RMS dla użytkowników indywidualnych](https://technet.microsoft.com/en-us/library/dn592127.aspx)).

> [!NOTE]
> Zapytaj administratora IT, czy jest dostępna subskrypcja usługi Microsoft Azure Rights Management, i poproś go o wykonanie poniższych czynności. Jeśli organizacja nie ma subskrypcji, administrator IT powinien ją utworzyć. Ponadto administrator IT powinien uzyskać subskrypcję dla *konta służbowego*, a nie *konta Microsoft* (na przykład usługi Hotmail).

Po zarejestrowaniu się w usłudze Microsoft Azure:

- Zaloguj się w [portalu zarządzania Azure](https://manage.windowsazure.com) organizacji przy użyciu konta z uprawnieniami administracyjnymi.

![Logowanie w usłudze Azure](../media/AzurePortalLogin.png)

- Przejdź do aplikacji **Active Directory** po lewej stronie portalu.

![Wybierz opcję Active Directory](../media/AzureADPick.png)

- Jeśli nie utworzono jeszcze katalogu, kliknij przycisk **Nowy** w lewym dolnym rogu portalu.

![Wybierz opcję NOWY](../media/AzureNewBtn.png)

- Wybierz kartę **Rights Management** i upewnij się, że **stan usługi Rights Management** ma wartość **Aktywny**, **Nieznany** lub **Bez autoryzacji**. Jeśli bieżący stan to **Nieaktywny**, kliknij przycisk **Aktywuj** znajdujący się na środku w dolnej części portalu i potwierdzić wybór.

![Wybierz opcję AKTYWUJ](../media/RMTab.png)

- Następnie utwórz nową *aplikację natywną* w katalogu, wybierając katalog i opcję Aplikacje.

![Wybierz opcję APLIKACJE](../media/CreateNativeApp.png)

- Następnie kliknij przycisk **Dodaj** znajdujący się na środku w dolnej części portalu.

![Wybierz opcję DODAJ](../media/AddAppBtn.png)

- Po wyświetleniu monitu wybierz opcję **Dodaj aplikację opracowywaną przez moją organizację**.

![Wybierz opcję Dodaj aplikację opracowywaną przez moją organizację.](../media/AddAnAppPick.png)

- Określ nazwę aplikacji, zaznaczając **NATYWNĄ APLIKACJĘ KLIENCKĄ** i klikając przycisk **Dalej**.

![Określ nazwę aplikacji](../media/TellUsInput.png)

- Dodaj identyfikator URI przekierowania i wybierz opcję Dalej.
  Identyfikator URI przekierowania musi być prawidłowym identyfikatorem URI unikatowym dla danego katalogu. Można na przykład użyć ciągu `https://contoso.azurewebsites.net/.auth/login/done`.

![Dodaj identyfikator URI przekierowania](../media/RedirectURI.png)

- Wybierz aplikację z katalogu i wybierz polecenie **KONFIGURUJ**.

![Wybierz opcję KONFIGURUJ](../media/ConfigYourApp.png)

>[!NOTE]
> Skopiuj **IDENTYFIKATOR KLIENTA** i **IDENTYFIKATOR URI PRZEKIEROWANIA** i zapisz je do użycia w przyszłości podczas konfigurowania klienta usługi RMS.

- Przejdź do dolnej części obszaru ustawień aplikacji i kliknij przycisk **Dodaj aplikację** w obszarze **uprawnień dotyczących innych aplikacji**.

>[!NOTE]
> **Delegowane uprawnienia** wyświetlone dla usługi Microsoft Azure Active Directory są poprawne domyślnie — należy wybrać tylko jedną opcję — **Loguj się i odczytuj profil użytkownika**.

![Wybierz opcję Dodaj aplikację](../media/PermissionsToOtherBtn.png)

- Kliknij przycisk plus (+) obok pozycji **Microsoft Rights Management**.

![Kliknij przycisk +](../media/ChoosePlusBtn.png)

- Następnie kliknij znacznik wyboru znajdujący się w lewym dolnym rogu okna dialogowego.

![Kliknij znacznik wyboru](../media/choosecheck01.png)

- Możesz teraz dodać do aplikacji zależność dotyczącą usługi Azure RMS. Aby dodać zależność, wybierz nową pozycję **Microsoft Rights Management Services** w obszarze **uprawnień dotyczących innych aplikacji** i zaznacz pole wyboru **Tworzenie i uzyskiwanie dostępu do chronionej zawartości dla użytkowników** w polu listy rozwijanej **Delegowane uprawnienia**.

![Uprawnienia do konfiguracji](../media/AddDependency.png)

- Zapisz aplikację, aby zachować zmiany, wybierając ikonę **Zapisz** znajdującą się na środku w dolnej części portalu.

![Wybierz opcję ZAPISZ](../media/SaveApplication.png)

[!INCLUDE[Commenting house rules](../includes/houserules.md)]