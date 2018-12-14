---
title: Konfiguracja systemu Android | Azure RMS
description: Aplikacje systemu android mogą korzystać Microsoft Rights Management SDK 4.2 do włączenia zintegrowanej ochrony informacji w swoich aplikacjach.
keywords: ''
author: lleonard-msft
ms.author: alleonar
manager: mbaldwin
ms.date: 02/23/2017
ms.topic: conceptual
ms.service: information-protection
ms.assetid: 986f6932-159b-4791-bd1a-7640a83ee792
audience: developer
ms.reviewer: shubhamp
ms.suite: ems
ms.openlocfilehash: 242700c089e34bc69eef10a45ea761f9668f4a42
ms.sourcegitcommit: 1cd4edd4ba1eb5e10cb61628029213eda316783a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/11/2018
ms.locfileid: "53266651"
---
# <a name="android-setup"></a>Konfiguracja systemu Android

Aplikacje systemu android mogą korzystać Microsoft Rights Management SDK 4.2 do włączenia zintegrowanej ochrony informacji w swoich aplikacjach za pomocą usługi Azure Active Directory Rights Management (AAD RM).

Ten temat zawiera informacje pomocne przy konfigurowaniu środowiska do tworzenia nowych własnych aplikacji.

-   [Wymagania wstępne](#prerequisites)
-   [Opcjonalne](#optional)
-   [Konfigurowanie środowiska deweloperskiego](#configuring-your-development-environment)
-   [Zobacz też](#see-also)

## <a name="prerequisites"></a>Wymagania wstępne

Zalecamy stosowanie następującego oprogramowania w systemie deweloperskim:

-   System operacyjny Windows lub OS X, umożliwiający uruchamianie środowiska deweloperskiego [Eclipse](https://www.oracle.com/technetwork/java/javase/downloads/jre7-downloads-1880261.html).
-   W tym przewodniku założono, że korzystasz z zestawu Eclipse SDK w wersji Eclipse Juno 4.2 lub nowszej i instalacji domyślnej.
-   Środowisko Java 1.6 lub nowsze.
-   [Dodatek Android Developer Tools (ADT) Plugin](https://developer.android.com/studio/install). UWAGA — Ukończenie instalacji może wymagać ponownego uruchomienia aplikacji Eclipse.

     

-   Pakiet MS RMS SDK 4.2 dla systemu Android. Aby uzyskać więcej informacji, zobacz [Rozpoczynanie pracy](get-started.md).

    Ten zestaw SDK umożliwia tworzenie aplikacji dla systemu Android 4.0.3 (API level 15) i nowszych.

-   Biblioteka uwierzytelniania: Firma Microsoft zaleca użycie [usługi Azure AD Authentication Library (ADAL)](https://msdn.microsoft.com/library/jj573266.aspx). Można jednak stosować także inne biblioteki uwierzytelniania obsługujące protokół OAuth 2.0.

    Aby uzyskać więcej informacji, zobacz [Biblioteka ADAL dla systemu Android](https://github.com/MSOpenTech/azure-activedirectory-library-for-android)

    **Uwaga**  Jeśli aplikacja nie będzie korzystać z biblioteki ADAL jako biblioteki uwierzytelniania OAuth 2.0, należy przejrzeć te wskazówki dla systemu Android, [niektóre uwag SecureRandom](https://android-developers.blogspot.com/2013/08/some-securerandom-thoughts.html).

     

Temat [Nowości](release-notes.md) zawiera informacje na temat aktualizacji interfejsu API, informacje o wersji i często zadawane pytania.

## <a name="optional"></a>Optional

Nasza biblioteka interfejsów użytkownika udostępnia interfejs wielokrotnego użytku do operacji konsumenckich i zabezpieczających dla deweloperów, którzy nie chcą tworzyć własnego interfejsu użytkownika — [Biblioteka interfejsów użytkownika i przykładowa aplikacja dla systemu Android](https://github.com/AzureAD/rms-sdk-ui-for-android).

## <a name="configuring-your-development-environment"></a>Konfigurowanie środowiska deweloperskiego

**Uwaga**  zestaw MS RMS SDK 4.2 w wersji zapoznawczej: W tej wersji zapoznawczej Aby wyświetlić zmiany w zmieniono nazw ścieżek z com/microsoft/protection na com/microsoft/rightsmanagment nie zostały zaktualizowane zrzuty ekranu. Tekst został jednak zaktualizowany.

 
-   Otwórz środowisko deweloperskie Eclipse.
-   Aby utworzyć nowy projekt aplikacji systemu Android, w menu **Plik** kliknij pozycję **New** (Nowy), kliknij pozycję **Project** (Projekt), a następnie wybierz pozycję **Android Application Project** (Projekt aplikacji dla systemu Android).

    ![Utwórz nową aplikację dla systemu Android](../media/Android-setup-01c.png)

-   Wpisz nazwę aplikacji. Nazwa projektu i pakietu jest wypełniana zgodnie z nazwą aplikacji.
-   Kliknij przycisk **Next** (Dalej) i wybierz miejsce utworzenia obszaru roboczego.

    ![Wpisz nazwę aplikacji](../media/Android-setup-02a.jpg)

-   Kliknij przycisk **Next** (Dalej) i wybierz ikonę aplikacji.

    ![Wybierz ikonę dla aplikacji](../media/Android-setup-03.png)

-   Kliknij przycisk **Next** (Dalej) i wybierz pozycję **Blank Activity** (Puste działanie), aby utworzyć działanie.

    ![Utwórz działanie](../media/Android-setup-04.png)

-   Kliknij przycisk **Next** (Dalej) i podaj nazwę działania. Możesz pozostawić nazwę domyślną *MainActivity* i nazwę układu *activity\_main*.

    ![Podaj nazwę działania](../media/Android-setup-05a.jpg)

-   Kliknij przycisk **Finish** (Zakończ).

    ![Zakończ tworzenie](../media/Android-setup-06.jpg)

-   Projekt zostanie utworzony wraz z klasą działania głównego *MainActivity.java*.

**Odwołania do zestawu SDK**

-   Przejdź do folderu, w którym wyodrębniono plik *adrms\_android\_sdk.zip*. W folderze „SDK > com > microsoft > rightsmanagement” upewnij się, że pliki *.classpath*, *.project* i *project.properties* nie są oznaczone jako tylko do odczytu.
-   Aby odwoływać się do zestawu SDK, należy zaimportować go do obszaru roboczego.

    W środowisku Eclipse kliknij pozycję **File** (Plik). W menu **File** (Plik) kliknij pozycję **Import** (Importuj). W oknie dialogowym **Import** wybierz opcję **Android / Existing Android Code into Workspace** (Android / istniejący kod Android do obszaru roboczego).

    ![Zaimportuj kod do obszaru roboczego](../media/Android-setup-07.png)

-   Kliknij przycisk **Dalej**. Przejdź do folderu, w którym wyodrębniono plik *adrms\_android\_sdk.zip*. Zestaw SDK powinien być wyświetlany na liście jako **com.microsoft.rightsmanagement**.

    ![Przejdź do folderu](../media/Android-setup-08c.jpg)

-   Po kliknięciu przycisku **Finish** (Zakończ) projekt zestawu SDK jest wyświetlany jako element równorzędny utworzonej wcześniej aplikacji.

    ![Projekt zestawu SDK jest wyświetlany jako element równorzędny aplikacji](../media/Android-setup-09.jpg)

-   Kliknij prawym przyciskiem myszy ikonę **Project** (Projekt) i wyświetl właściwości projektu.
-   Przejdź na kartę **Android**.
-   Kliknij przycisk **Add** (Dodaj), a następnie wybierz bibliotekę *com.microsoft.rightsmanagement* z obszaru roboczego.

    ![Dodaj bibliotekę](../media/Android-setup-10b.jpg)

-   Kliknij przycisk **OK**.

    Ponieważ zestaw SDK 4.2 usługi MS RMS łączy się z usługi AAD RM, aplikacja musi mieć uprawnienia **INTERNET** i **dostępu\_sieci\_stanu**. W tym celu otwórz plik *AndroidManifest.xml* w folderze głównym projektu.

    Aby dodać uprawnienia, kliknij przycisk **Add** (Dodaj) i wybierz pozycję **Uses Permissions** (Używa uprawnień).

    ![Dodaj uprawnienia](../media/Android-setup-11d.jpg)

-   Krok manifestu można sprawdzić, wyświetlając manifest w widoku edytora tekstu. Upewnij się, że są wyświetlane następujące wiersze:

   ```
    <uses-sdk
         android:minSdkVersion="15"
         android:targetSdkVersion="19"/>
    <uses-permission android:name="android.permission.INTERNET"/>
    <uses-permission android:name="android.permission.ACCESS_NETWORK_STATE"/>
    <uses-permission/>
   ```

**Uwaga**  zestaw SDK używa *android.support.v4*

-   Teraz można przystąpić do tworzenia własnych nowych aplikacji dla systemu Android.

### <a name="see-also"></a>Zobacz też

[Wprowadzenie](get-started.md)

[Co nowego](release-notes.md)

[Terminy i pojęcia dla deweloperów](core-concepts.md)

[Dokumentacja interfejsu API systemu Android](https://msdn.microsoft.com/library/dn758245.aspx)


