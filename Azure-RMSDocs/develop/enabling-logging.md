---
title: Porady&#58; włączanie rejestrowania błędów i wydajności | Azure RMS
description: Zestaw Microsoft Rights Management SDK 4.2 zarządza przekazywaniem dzienników diagnostyki i wydajności za pośrednictwem pojedynczej właściwości urządzenia.
keywords: ''
author: lleonard-msft
ms.author: alleonar
manager: mbaldwin
ms.date: 02/23/2017
ms.topic: article
ms.prod: ''
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: F5AD3826-2292-4A25-AF5C-D17D083F5742
audience: developer
ms.reviewer: shubhamp
ms.suite: ems
ms.openlocfilehash: 906746990fd08a749d2879fbc04b054e49e65f01
ms.sourcegitcommit: 93124ef58e471277c7793130f1a82af33dabcea9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/11/2018
ms.locfileid: "27764489"
---
# <a name="how-to-enable-error-and-performance-logging"></a>Porady: włączanie rejestrowania błędów i wydajności
Zestaw Microsoft Rights Management SDK 4.2 zarządza przekazywaniem dzienników diagnostyki i wydajności za pośrednictwem pojedynczej właściwości urządzenia.

## <a name="overview"></a>Przegląd ##
Włączenie automatycznego przekazywania danych dzienników diagnostyki, wydajności i telemetrii do firmy Microsoft pozwala zwiększyć komfort pracy użytkowników i usprawnić rozwiązywanie problemów. 

> [!IMPORTANT] 
> Aby chronić prywatność użytkowników, przed włączeniem automatycznego rejestrowania deweloper aplikacji musi poprosić użytkownika o zgodę.

> [!NOTE]
> Poniżej jako przykład przedstawiamy standardową wiadomość używaną przez firmę Microsoft w przypadku powiadamiania o rejestrowaniu: 
>
> *Włączając rejestrowanie błędów i wydajności, zgadzasz na wysyłanie do firmy Microsoft informacji o błędach i wydajności.  Firma Microsoft będzie automatycznie zbierać dane dotyczące błędów i wydajności w Internecie („Dane”).  Firma Microsoft używa tych Danych w celu zapewniania i zwiększania jakości, bezpieczeństwa i integralności swoich produktów i usług.  Na przykład analizujemy wydajność i niezawodność, sprawdzając, jakich funkcji używasz, jak szybko funkcje reagują, jaka jest wydajność urządzenia, jakie są interakcje z interfejsem użytkownika oraz jakie problemy wystąpiły podczas pracy z produktem.  Dane będą również zawierać informacje o konfiguracji oprogramowania, takie jak aktualnie działające oprogramowanie i adres IP.*  

Do zarządzania rejestrowaniem służą dwie właściwości.

-   Można włączyć rejestrowanie za pośrednictwem właściwości **IpcCustomerExperienceDataCollectionEnabled**. To ustawienie jest zachowywane po zresetowaniu urządzenia.
-   Poziomem rejestrowania można sterować za pośrednictwem właściwości **IpcLogLevel** przy użyciu poniższych ustawień.

    * 1 — pełny
    * 2 — informacyjny
    * 3 — ostrzeżenie
    * 4 — błąd
    * 5 — krytyczny

W każdym z poniższych przykładowych fragmentów kodu aplikacja wywołująca może ustawić właściwość lub wykonać zapytanie dotyczące tej właściwości.

### <a name="android"></a>Android ###
Włączanie automatycznego rejestrowania

    SharedPreferences preferences = PreferenceManager.getDefaultSharedPreferences(context);
    SharedPreferences.Editor editor = preferences.edit();
    editor.putBoolean(&quot;IpcCustomerExperienceDataCollectionEnabled&quot;, true);
    editor.commit();

Pobieranie bieżącego ustawienia flagi kontroli rejestrowania

    SharedPreferences preferences = PreferenceManager.getDefaultSharedPreferences(context);
    Boolean isLogUploadEnabled = preferences.getBoolean(&quot;IpcCustomerExperienceDataCollectionEnabled&quot;, false);

## <a name="ios"></a>iOS ##
Włączanie automatycznego rejestrowania

    NSUserDefaults \*prefs = [NSUserDefaults standardUserDefaults];
        [prefs setBool:FALSE forKey:@&quot;IpcCustomerExperienceDataCollectionEnabled”];
        [[NSUserDefaults standardUserDefaults] synchronize];

Pobieranie bieżącego ustawienia flagi kontroli rejestrowania

    [[NSUserDefaults standardUserDefaults] boolForKey:@&quot;IpcCustomerExperienceDataCollectionEnabled&quot;];

Ustawianie kontroli poziomu dziennika

    NSUserDefaults \*prefs = [NSUserDefaults standardUserDefaults];
      [prefs setInteger:1 forKey:@&quot;IpcLogLevel”];
      [[NSUserDefaults standardUserDefaults] synchronize];

Pobieranie ustawienia kontroli poziomu dziennika

    [[NSUserDefaults standardUserDefaults] boolForKey:@&quot;IpcLogLevel&quot;];
 

## <a name="windows"></a>Windows ##
Włączanie automatycznego rejestrowania

    CustomerExperienceConfiguration::Option = CustomerExperienceOptions::LoggingEnabledNow;

Więcej informacji o ustawieniach opcjonalnych można znaleźć w sekcji dotyczącej elementu [CustomerExperienceOptions](https://msdn.microsoft.com/library/microsoft.rightsmanagement.customerexperienceoptions.aspx).

Pobieranie bieżącego ustawienia flagi kontroli rejestrowania

    CustomerExperienceOptions loggingOption = CustomerExperienceConfiguration::Option;


**Uwaga:** kod przedstawiony powyżej jest napisany w języku C++. Dla języka C\# uaktualnij składnię, używając „.” zamiast „::”.

**Linux / C++:** ten zestaw SDK udostępnia podstawowe funkcje rejestrowania, ale nie są one tak zaawansowane jak w przypadku innych platform. Aby uzyskać więcej informacji, zobacz sekcję dotyczącą **rozwiązywania problemów** związanych z plikiem „README.md” na stronie [RMS SDK for portable C++](https://github.com/AzureAD/rms-sdk-for-cpp#troubleshooting) (Zestaw RMS SDK dla przenośnego kodu C++).

[!INCLUDE[Commenting house rules](../includes/houserules.md)]