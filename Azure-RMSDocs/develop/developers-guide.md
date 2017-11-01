---
title: "Przewodnik dewelopera usługi Azure Information Protection"
description: "Deweloperzy mogą korzystać z usługi Azure Information Protection do ochrony plików każdego typu oraz zarządzania nimi"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.date: 10/11/2017
ms.topic: article
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: a53c2df2-a0a2-4f1f-995b-75ba55e4489b
ms.suite: ems
ms.reviewer: kartikk
ms.openlocfilehash: a9a94744aa2eacb3ddb4bbda3989ae857ff708fd
ms.sourcegitcommit: 965108d50739148864b2ae7dcc661ae65f1b154c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/17/2017
---
# <a name="azure-information-protection-developers-guide"></a>Przewodnik dewelopera usługi Azure Information Protection

Ten przewodnik pozwala zapoznać się z narzędziami zwiększającymi możliwości usługi zarządzania prawami usługi Azure Information Protection i umożliwiającymi integrację z nią.

>Bieżący zestaw SDK ochrony informacji Azure ma składnik zarządzania prawami. Opracowywane są klasyfikacji i etykietowania składnika.

## <a name="service-applications"></a>Aplikacje usług

Aplikacje usług zapewniają możliwości ochrony informacji podczas eksportowania z system zarządzania zawartością w przedsiębiorstwie, aplikacji biznesowych lub rozwiązanie oparte na chmurze biznesowe. Mogą to być na przykład aplikacje do ochrony przed utratą danych (DLP) i zapewniania bezpieczeństwa aplikacji chmurowych (CAS). Nasz zestaw SDK do tworzenia aplikacji usług jest dostępny w dwóch modelach programowania.

- [C++](https://www.microsoft.com/en-us/download/details.aspx?id=38397)
- [Interfejs API zarządzany z użyciem języka C#](https://github.com/Azure-Samples/Azure-Information-Protection-Samples/tree/master/IpcManagedAPI)

### <a name="examples-of-service-applications"></a>Przykłady aplikacji usług

- [IpcDlp](https://github.com/Azure-Samples/active-directory-dotnet-rms) to przykładowa aplikacja DLP obsługująca usługę RMS, prezentująca podstawowe kroki, które każda aplikacja obsługująca usługę RMS powinna wykonywać przy użyciu interfejsu API plików usługi RMS w celu ochrony i wykorzystywania zawartości ograniczonej restrykcjami.
- [IpcAzureApp](https://github.com/Azure-Samples/active-directory-dotnet-rms) to przykład przedstawiający zastosowanie zestawu SDK usługi RMS w aplikacjach Azure do ochrony danych w usłudze Magazyn obiektów blob Azure.
- [RmsFileWatcher](https://github.com/Azure-Samples/active-directory-dotnet-rms) to przykład, który demonstruje sposób tworzenia aplikacji systemu Windows, która prowadzi obserwację katalogów w systemie plików i stosuje zasady ochrony usługi RMS dla każdej zmiany, na przykład dodania lub modyfikacji pliku.
- [ProtectFilesInDir](https://github.com/Azure-Samples/Azure-Information-Protection-Samples/tree/master/ProtectFilesInDir) to przykład prostej aplikacji konsoli, która obsługuje wskazany katalog i nierekursywnie chroni wszystkie pliki tylko w tym katalogu.

## <a name="powershell-guides"></a>Przewodniki po programie PowerShell

Używany przez usługę Azure Rights management Administratorzy, poleceń cmdlet programu PowerShell są także przydatne do tworzenia i testowania aplikacji usługi. Aby uzyskać więcej informacji, zobacz temat [Używanie środowiska PowerShell z klientem usługi Azure Information Protection](/information-protection/rms-client/client-admin-guide-powershell).

## <a name="user-applications"></a>Aplikacje użytkownika

Aplikacje użytkownika można tworzyć za pomocą zestawów SDK RMS 2.1 lub RMS 4.2.
Wersja 4.2 to klient REST z interfejsami API odpowiednimi dla popularnych systemów operacyjnych, takich jak iOS/OSX, Android, Linux czy Windows. W wersji 2.1 służy do tworzenia natywnych aplikacji systemu Windows.

### <a name="user-application-development-guides"></a>Przewodniki po projektowaniu aplikacji użytkownika

- [Tworzenie aplikacji](developing-your-application.md)
- [Testowanie aplikacji](how-to-set-up-your-test-environment.md)
- [Wdrażanie aplikacji](deploying-your-application.md)

### <a name="user-application-samples"></a>Przykłady aplikacji użytkownika

- [AzureIP Test](https://github.com/Azure-Samples/Azure-Information-Protection-Samples/tree/master/AzureIP_Test) stanowi przykład aplikacji konsoli umożliwiającej szyfrowanie dokumentów z wykorzystaniem szablonu usługi Azure lub zasad ad hoc.
- [IPCNotepad](https://github.com/Azure-Samples/Azure-Information-Protection-Samples/tree/master/AzureIP_Test) to przykładowa aplikacja obsługująca usługę RMS, prezentująca podstawowe kroki, które każda aplikacja obsługująca usługę RMS powinna wykonywać podczas chronienia i wykorzystywania zawartości ograniczonej.
- [RmsDocumentInspector](https://github.com/Azure-Samples/active-directory-dotnet-rms) to narzędzie dostarczające informacji takich jak identyfikator zawartości i uprawnienia użytkownika na temat dowolnego pliku chronionego przez usługę RMS.

## <a name="development-environment-setup"></a>Konfiguracja środowiska deweloperskiego

Następujące przewodniki przeprowadzą Cię przez kolejne kroki konfiguracji środowiska programowania aplikacji przy użyciu standardowych narzędzi w poszczególnych systemach operacyjnych.

[![Konfiguracja w systemie iOS/OSX](../media/develop/ios-icon.png)](ios-sdk.md)
[![Konfiguracja w systemie Android](../media/develop/android-icon.png)](android-sdk.md)
[![Konfiguracja w systemie Windows Phone](../media/develop/windows-phone-icon.png)](windows-phone-apps.md)
[![Konfiguracja usługi systemu Windows](../media/develop/windows-icon.png)](install-the-rms-sdk.md)
[![Konfiguracja w systemie Linux](../media/develop/linux-icon.png)](linux-setup.md)


## <a name="how-tos"></a>Instrukcje

Każdy z poniższych tematów przedstawia konkretne wskazówki dotyczące poszczególnych aspektów wdrażania aplikacji. Aplikacje usług tworzy się z użyciem zestawu SDK usług RMS 2.x. Aplikacje użytkownika tworzy się z użyciem zestawu SDK RMS 4.x. Link do artykułu jest powiązany z konkretnym atrybutem: typem aplikacji, usługą lub użytkownikiem.

### <a name="general"></a>Ogólne

- [Włączanie śledzenia i odwoływania dokumentów (usługa)](tracking-content.md)
- [Jak wdrożyć klienta](../rms-client/client-deployment-notes.md)
- [Sposoby wdrażania aplikacji usługi w ramach innej dzierżawy] (how-to-deploy-app.md)
- [Instalowanie i konfigurowanie serwera usługi RMS (usługa)](how-to-install-and-configure-an-rms-server.md)
- [Korzystanie ze śledzenia dokumentów (użytkownik)](how-to-use-document-tracking.md)
- [Odnawianie klucza symetrycznego w usłudze Azure Information Protection](how-to-renew-symmetric-key.md)

### <a name="security-and-authentication"></a>Tożsamość i uwierzytelnianie

- [Konfigurowanie aplikacji usługi programu na potrzeby logowania do usługi Azure Active Directory](https://docs.microsoft.com/en-us/azure/app-service-mobile/app-service-mobile-how-to-configure-active-directory-authentication)
- [Korzystanie z uwierzytelniania usługi Azure Active Directory (ADAL)](how-to-use-adal-authentication.md)
- [Konfigurowanie usług Azure RMS na potrzeby uwierzytelniania (usługa)](adal-auth.md)
- [Ustawianie trybu zabezpieczeń interfejsu API (usługa)](setting-the-api-security-mode-api-mode.md)
- [Włączanie obsługi usług Azure RMS aplikacji (usługa)](how-to-use-file-api-with-aadrm-cloud.md)
- [Jak zarejestrować aplikację w usłudze Azure AD i włączyć dla niej obsługę usługi RMS (użytkownik)](authentication-integration.md)

### <a name="configuration-and-performance-management"></a>Konfiguracja i zarządzanie wydajnością

- [Dodawanie jawnych praw właściciela (usługa)](add-explicit-owner-rights.md)
- [Konfiguracja interfejsu API plików (usługa)](file-api-configuration.md)
- [Korzystanie z praw wbudowanych (użytkownik)](built-in-rights-usage-restriction-reference.md)
- [Włączanie rejestrowania błędów i wydajności (użytkownik)](enabling-logging.md)

## <a name="videos"></a>Filmy

[Wprowadzenie do usługi Azure Information Protection](https://www.microsoft.com/cloud-platform/azure-information-protection)

Są następujące filmy wideo z konferencji Microsoft 2016 Ignite

- [Email security inside your org](https://myignite.microsoft.com/videos/2787) (Zabezpieczenia poczty e-mail w organizacji)
- [Adopt a comprehensive identity-driven solution for protecting and sharing data securely](https://myignite.microsoft.com/videos/2784) (Wdrażanie kompleksowego rozwiązania opartego na tożsamościach służącego do ochrony i bezpiecznego udostępniania danych)
- [Dowiedz się, jak klasyfikacji, etykietowania i, ochrona zapewnia ochronę danych trwałych](https://myignite.microsoft.com/videos/2786)

## <a name="other-resources"></a>Inne zasoby

- [Przewodnik po najlepszych rozwiązaniach w zakresie zabezpieczeń](security-guidelines.md)
- [RMS Developer's Corner (blog)](https://blogs.msdn.microsoft.com/rms/) (Blog kącika deweloperów usług RMS)
- [Często zadawane pytania dotyczące usługi Azure Information Protection](https://docs.microsoft.com/en-us/information-protection/get-started/faqs)

### <a name="support-articles"></a>Artykuły pomocy technicznej

- [Obsługiwane formaty plików](supported-file-formats.md)
- [Obsługiwane platformy](supported-platforms.md)
- [Opis ograniczeń użycia](understanding-usage-restrictions.md)

### <a name="message-protocol-and-file-formats"></a>Formaty wiadomości protokołu i plików

- [Protokół klient serwer](https://msdn.microsoft.com/library/cc243191.aspx)
- [Protokół obiektu zarządzania prawami poczty E-mail](https://msdn.microsoft.com/library/cc463909(v=EXCHG.80).aspx)
- [Złożone plik binarny Format pliku](https://msdn.microsoft.com/library/dd942138.aspx)

#### <a name="rights-managed-email-message"></a>Wiadomość e-mail zarządzanego prawa

- [. Format pliku MSG (część 1)](https://blogs.msdn.microsoft.com/openspecification/2009/11/06/msg-file-format-part-1/)
- [. Format pliku MSG (część 2)](https://blogs.msdn.microsoft.com/openspecification/2010/06/20/msg-file-format-rights-managed-email-message-part-2/)

### <a name="api-reference"></a>Dokumentacja interfejsu API

- [Dokumentacja interfejsu API systemu Windows](https://msdn.microsoft.com/en-us/library/hh535292.aspx)
  - [Kody błędów zestawu SDK Windows ](https://msdn.microsoft.com/library/hh535248.aspx)
- [Dokumentacja interfejsu API systemu Windows Phone i Sklepu Windows](https://msdn.microsoft.com/library/dn891914.aspx)
- [Dokumentacja interfejsu API systemu iOS/OSX](https://msdn.microsoft.com/en-us/library/dn758306.aspx)
- [Dokumentacja interfejsu API systemu Android](https://msdn.microsoft.com/en-us/library/dn758245.aspx)
- [Dokumentacja interfejsu API systemu Linux](http://azuread.github.io/rms-sdk-for-cpp/annotated.html)

### <a name="previous-versions"></a>Poprzednie wersje

- [AD RMS SDK](https://msdn.microsoft.com/en-us/library/cc530379.aspx) to pierwsza wersja zestawu SDK usług RMS.
- [AD RMS Scripting Tool](https://msdn.microsoft.com/en-us/library/bb968797.aspx) to narzędzie administracyjne służące do instalacji usług AD RMS.

### <a name="see-also"></a>Zobacz także

- [Terminologia Developer](terms.md)
- [Terminologia dotycząca usługi Azure Information Protection — ITPro](../get-started/terminology.md)

[!INCLUDE[Commenting house rules](../includes/houserules.md)]