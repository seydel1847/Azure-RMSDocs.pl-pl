---
title: "Przewodnik dewelopera — AIP"
description: "Deweloperzy mogą korzystać z usługi Azure Information Protection do ochrony plików każdego typu oraz zarządzania nimi"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.date: 03/13/2017
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: a53c2df2-a0a2-4f1f-995b-75ba55e4489b
ms.suite: ems
ms.reviewer: kartikk
ms.openlocfilehash: fbd76e377c8b11b8e64187685144010dce9bbb25
ms.sourcegitcommit: ee432bdb6783bfe311a7ebbc9a5f20a7c2ae759c
translationtype: HT
---
# <a name="azure-information-protection-developers-guide"></a>Przewodnik dewelopera usługi Azure Information Protection

Ten przewodnik pozwala zapoznać się z narzędziami zwiększającymi możliwości usługi zarządzania prawami usługi Azure Information Protection i umożliwiającymi integrację z nią. Celem tego przewodnika jest umożliwienie deweloperom, którzy chcą korzystać z systemu zarządzania prawami, tworzenia różnych typów aplikacji dla szeregu obsługiwanych platform.

>Bieżący zestaw SDK usługi Azure Information Protection jest wyposażony w składnik do zarządzania prawami; składniki do obsługi klasyfikacji i etykiet są w fazie projektowej.

## <a name="service-applications"></a>Aplikacje usług

Aplikacje usług zapewniają możliwość ochrony informacji podczas eksportu z systemu zarządzania zawartością w przedsiębiorstwie, aplikacji biznesowych lub rozwiązań biznesowych opartych na chmurze. Mogą to być na przykład aplikacje do ochrony przed utratą danych (DLP) i zapewniania bezpieczeństwa aplikacji chmurowych (CAS). Nasz zestaw SDK do tworzenia aplikacji usług jest dostępny w dwóch modelach programowania.

- [C++](https://www.microsoft.com/en-us/download/details.aspx?id=38397)
- [Interfejs API zarządzany z użyciem języka C#](https://github.com/Azure-Samples/Azure-Information-Protection-Samples/tree/master/IpcManagedAPI)

### <a name="examples-of-service-applications"></a>Przykłady aplikacji usług

- [IpcDlp](https://github.com/Azure-Samples/active-directory-dotnet-rms) to przykładowa aplikacja DLP obsługująca usługę RMS, prezentująca podstawowe kroki, które każda aplikacja obsługująca usługę RMS powinna wykonywać przy użyciu interfejsu API plików usługi RMS w celu ochrony i wykorzystywania zawartości ograniczonej restrykcjami.
- [IpcAzureApp](https://github.com/Azure-Samples/active-directory-dotnet-rms) to przykład przedstawiający zastosowanie zestawu SDK usługi RMS w aplikacjach Azure do ochrony danych w usłudze Magazyn obiektów blob Azure.
- [RmsFileWatcher](https://github.com/Azure-Samples/active-directory-dotnet-rms) to przykład, który demonstruje sposób tworzenia aplikacji systemu Windows, która prowadzi obserwację katalogów w systemie plików i stosuje zasady ochrony usługi RMS dla każdej zmiany, na przykład dodania lub modyfikacji pliku.
- [ProtectFilesInDir](https://github.com/Azure-Samples/Azure-Information-Protection-Samples/tree/master/ProtectFilesInDir) to przykład prostej aplikacji konsoli, która obsługuje wskazany katalog i nierekursywnie chroni wszystkie pliki tylko w tym katalogu.

## <a name="powershell-guides"></a>Przewodniki po programie PowerShell

Te skrypty, powszechnie wykorzystywane przez administratorów usługi Azure Rights Management, przydają się do tworzenia i testowania aplikacji usług.

- [Polecenia cmdlet usługi Azure Rights Management](https://msdn.microsoft.com/library/azure/dn629398.aspx) umożliwiają administrowanie usługą Azure RMS z poziomu wiersza polecenia. Mimo że pozwala to na automatyzację, umożliwia również obsługę niezawodnych i powtarzanych procesów w celu zmniejszenia kosztów administracyjnych. Ponadto niektóre zaawansowane konfiguracje i operacje usługi Azure RMS wymagają programu Azure PowerShell.
- [Polecenia cmdlet ochrony usługi RMS](https://msdn.microsoft.com/library/azure/mt433195.aspx) mogą być używane z ochroną danych usługi Azure Rights Management (Azure RMS) z poziomu usługi Azure Information Protection lub z usługą Active Directory Rights Management Services (AD RMS) w celu uzupełnienia innych modułów programu PowerShell na potrzeby wdrożeń usługi Rights Management. Użyj tych poleceń cmdlet ochrony usługi RMS, aby łącznie objąć ochroną pliki dowolnego typu lub anulować tę ochronę

## <a name="user-applications"></a>Aplikacje użytkownika

Aplikacje użytkownika można tworzyć za pomocą zestawów SDK RMS 2.1 lub RMS 4.2.
Wersja 4.2 to klient REST z interfejsami API odpowiednimi dla popularnych systemów operacyjnych, takich jak iOS/OSX, Android, Linux czy Windows. Wersja 2.1 jest wykorzystywana do tworzenia aplikacji natywnych systemu Windows.

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

Dan Plastina z firmy Microsoft przedstawia: [Usługa Azure Information Protection — wprowadzenie](https://www.microsoft.com/en-us/cloud-platform/azure-information-protection)

Te filmy wideo pochodzą z konferencji Microsoft 2016 Ignite

- [Email security inside your org](https://myignite.microsoft.com/videos/2787) (Zabezpieczenia poczty e-mail w organizacji)
- [Adopt a comprehensive identity-driven solution for protecting and sharing data securely](https://myignite.microsoft.com/videos/2784) (Wdrażanie kompleksowego rozwiązania opartego na tożsamościach służącego do ochrony i bezpiecznego udostępniania danych)
- [Learn how classification, labeling, and protection delivers persistent data protection](https://myignite.microsoft.com/videos/2786) (Dowiedz się, jak klasyfikacja, etykietowanie i ochrona w trwały sposób zabezpieczają dane)

## <a name="other-resources"></a>Inne zasoby

- [Przewodnik po najlepszych rozwiązaniach w zakresie zabezpieczeń](security-guidelines.md)
- [RMS Developer's Corner (blog)](https://blogs.msdn.microsoft.com/rms/) (Blog kącika deweloperów usług RMS)
- [Często zadawane pytania dotyczące usługi Azure Information Protection](https://docs.microsoft.com/en-us/information-protection/get-started/faqs)

### <a name="support-articles"></a>Artykuły pomocy technicznej

- [Obsługiwane formaty plików](supported-file-formats.md)
- [Obsługiwane platformy](supported-platforms.md)
- [Opis ograniczeń użycia](understanding-usage-restrictions.md)

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

- [Terminologia dla deweloperów](terms.md)
- [Terminologia dotycząca usługi Azure Information Protection — ITPro](../get-started/terminology.md)

[!INCLUDE[Commenting house rules](../includes/houserules.md)]