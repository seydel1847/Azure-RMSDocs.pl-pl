---
title: Jak zarejestrować aplikację w usłudze Azure AD — AIP
description: W tym artykule opisano podstawy uwierzytelniania użytkowników w aplikacji z włączoną obsługą usługi RMS
keywords: ''
author: bryanla
ms.author: bryanla
manager: mbaldwin
ms.date: 03/13/2017
ms.topic: conceptual
ms.service: information-protection
ms.assetid: 200D9B23-F35D-4165-9AC4-C482A5CE1D28
audience: developer
ms.reviewer: kartikk
ms.suite: ems
ms.openlocfilehash: 2cdd5f88edd8cad446ebaecbdd4065fdc18de51e
ms.sourcegitcommit: 9dc6da0fb7f96b37ed8eadd43bacd1c8a1a55af8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/18/2019
ms.locfileid: "54394112"
---
# <a name="how-to-register-and-rms-enable-your-app-with-azure-ad"></a>Jak zarejestrować aplikację w usłudze Azure AD i włączyć dla niej obsługę usługi RMS

W tym temacie przedstawiono podstawowe informacje dotyczące rejestracji aplikacji i włączania obsługi usługi RMS za pośrednictwem Portalu Azure oraz uwierzytelniania użytkowników za pomocą biblioteki Azure Active Directory Authentication Library (ADAL).

## <a name="what-is-user-authentication"></a>Czym jest uwierzytelnianie użytkownika
Uwierzytelnianie użytkownika to kluczowy etap nawiązywania komunikacji między aplikacją urządzenia i infrastrukturą usługi RMS. Ten proces uwierzytelniania używa standardowego protokołu OAuth 2.0, który wymaga kluczowych informacji dotyczących bieżącego użytkownika i jego żądania uwierzytelnienia.

## <a name="registration-via-azure-portal"></a>Rejestracja za pośrednictwem Portalu Azure
Najpierw wykonaj czynności przedstawione w tym przewodniku konfigurowania rejestracji aplikacji za pomocą Portalu Azure [Konfigurowanie usługi Azure RMS na potrzeby uwierzytelniania ADAL](adal-auth.md). Skopiuj i zapisz **identyfikator klienta** oraz **identyfikator URI przekierowania** z tego procesu do użycia w przyszłości.

## <a name="complete-your-information-protection-integration-agreement-ipia"></a>Uzupełnij umowę integracyjną usługi Information Protection (IPIA, Information Protection Integration Agreement)
Przed wdrożeniem aplikacji musisz uzupełnić umowę IPIA zawartą z zespołem Microsoft Information Protection. Aby uzyskać szczegółowe informacje, zapoznaj się z pierwszą sekcją w temacie, [Wdrażanie w środowisku produkcyjnym](deploying-your-application.md).

## <a name="implement-user-authentication-for-your-app"></a>Implementowanie uwierzytelniania użytkowników w aplikacji
Każdy z interfejsów API usługi RMS dysponuje wywołaniem zwrotnym, które należy zaimplementować w celu umożliwienia uwierzytelniania użytkownika. Zestaw SDK 4.2 usługi RMS użyje Twojego wdrożenia wywołania zwrotnego w przypadku niepodania tokenu dostępu, gdy konieczne jest odświeżenie tokenu dostępu lub wygaśnięcia tokenu dostępu.

- Android — interfejsy [AuthenticationRequestCallback](https://msdn.microsoft.com/library/dn758255.aspx) i [AuthenticationCompletionCallback](https://msdn.microsoft.com/library/dn758250.aspx).
- iOS/OS X — protokół [MSAuthenticationCallback](https://msdn.microsoft.com/library/dn758312.aspx).
-  Windows Phone/Window RT — interfejs [IAuthenticationCallback](https://msdn.microsoft.com/library/microsoft.rightsmanagement.iauthenticationcallback.aspx).
- Linux — interfejs [IAuthenticationCallback](https://azuread.github.io/rms-sdk-for-cpp/classrmscore_1_1modernapi_1_1IAuthenticationCallback.html).

### <a name="what-library-to-use-for-authentication"></a>Jakiej biblioteki użyć podczas uwierzytelniania
W celu wdrożenia wywołania zwrotnego uwierzytelniania należy pobrać odpowiednią bibliotekę i skonfigurować środowisko deweloperskie do korzystania z niej. W witrynie GitHub są dostępne biblioteki ADAL dla tych platform.

Każdy z poniższych zasobów zawiera wskazówki dotyczące konfiguracji środowiska i korzystania z biblioteki.

-   [Biblioteka Windows Azure Active Directory Authentication Library (ADAL) dla systemu iOS](https://github.com/MSOpenTech/azure-activedirectory-library-for-ios/)
-   [Biblioteka Windows Azure Active Directory Authentication Library (ADAL) dla komputerów Mac](https://github.com/MSOpenTech/azure-activedirectory-library-for-ios/)
-   [Biblioteka Windows Azure Active Directory Authentication Library (ADAL) dla systemu Android](https://github.com/MSOpenTech/azure-activedirectory-library-for-android)
-   [Biblioteka Windows Azure Active Directory Authentication Library (ADAL) dla platformy dotnet](https://github.com/AzureAD/azure-activedirectory-library-for-dotnet)
-   W przypadku zestawu SDK dla systemu Linux biblioteka ADAL jest spakowana ze źródłem SDK, dostępnym w witrynie [Github](https://github.com/AzureAD/rms-sdk-for-cpp).

> [!NOTE]
> Zalecamy korzystanie z jednej z bibliotek ADAL, choć można też korzystać z innych bibliotek uwierzytelniania.

### <a name="authentication-parameters"></a>Parametry uwierzytelniania

Biblioteka ADAL wymaga kilku informacji w celu pomyślnego uwierzytelnienia użytkownika w usłudze Azure RMS (lub AD RMS). Są to standardowe parametry protokołu OAuth 2.0, wymagane zwykle od wszystkich aplikacji usługi Azure AD. Bieżące wytyczne dotyczące korzystania z biblioteki ADAL zamieszczono w plikach README odpowiednich repozytoriów Github wymienionych powyżej.

- **Urząd** — adres URL punktu końcowego uwierzytelniania, zazwyczaj AAD lub ADFS.
- **Zasób** — adres URL/identyfikator URI aplikacji usługi, do której próbujesz uzyskać dostęp, zazwyczaj Azure RMS lub AD RMS.
- **Identyfikator użytkownika** — nazwa UPN, zwykle adres e-mail użytkownika, który próbuje uzyskać dostęp do aplikacji. Parametr ten może być pusty, jeśli użytkownik nie jest jeszcze znany. Jest używany także do buforowania tokenu użytkownika i żądania tokenu z pamięci podręcznej. Ta wartość jest używana zazwyczaj także jako *wskazówka* do monitowania użytkownika.
- **Identyfikator klienta** — identyfikator aplikacji klienta. Musi to być poprawny identyfikator aplikacji usługi Azure AD.
i pochodzi z poprzedniego kroku rejestracji w Portalu Azure.
- **Identyfikator Uri przekierowania** — podaje bibliotekę uwierzytelniania z celem URI dla kodu uwierzytelniania. Systemy iOS i Android wymagają określonych formatów. Omówiono je w plikach README odpowiednich repozytoriów GitHub biblioteki ADAL. Ta wartość pochodzi z poprzedniego kroku rejestracji w Portalu Azure.

> [!NOTE]
> **Zakres** nie jest obecnie używany, ale może być używany, w związku z czym jest zarezerwowany do użycia w przyszłości.

    Android: `msauth://packagename/Base64UrlencodedSignature`

    iOS: `<app-scheme>://<bundle-id>`

> [!NOTE]
> Jeśli aplikacja nie jest zgodna z tymi wytycznymi, przepływy pracy usług Azure RMS i Azure AD zakończą się prawdopodobnie niepowodzeniem i nie będą obsługiwane przez witrynę Microsoft.com. Dodatkowo użycie nieprawidłowego identyfikatora klienta w aplikacji produkcyjnej może oznaczać naruszenie umowy licencyjnej usługi Rights Management (RMLA).

### <a name="what-should-an-authentication-callback-implementation-look-like"></a>Jak powinno wyglądać wdrożenie wywołania zwrotnego uwierzytelniania
**Przykłady kodu uwierzytelniania** — ten zestaw SDK zawiera przykładowy kod, przedstawiający zastosowanie wywołań zwrotnych uwierzytelniania. Dla wygody te przykłady kodu przedstawiono w tym miejscu, jak również we wszystkich powiązanych tematach.

**Uwierzytelnianie użytkownika systemu Android** — więcej informacji znajduje się w części [Przykłady kodu dla systemu Android](android-code.md), **Krok 2** pierwszego scenariusza, „Korzystanie z pliku chronionego usługi RMS”.


    class MsipcAuthenticationCallback implements AuthenticationRequestCallback
    {
    ...

    @Override
    public void getToken(Map<String, String> authenticationParametersMap,
                         final AuthenticationCompletionCallback authenticationCompletionCallbackToMsipc)
    {
        String authority = authenticationParametersMap.get("oauth2.authority");
        String resource = authenticationParametersMap.get("oauth2.resource");
        String userId = authenticationParametersMap.get("userId");
        mClientId = “12345678-ABCD-ABCD-ABCD-ABCDEFGHIJ”; // get your registered Azure AD application ID here
        mRedirectUri = “urn:ietf:wg:oauth:2.0:oob”;
        final String userHint = (userId == null)? "" : userId;
        AuthenticationContext authenticationContext = App.getInstance().getAuthenticationContext();
        if (authenticationContext == null || !authenticationContext.getAuthority().equalsIgnoreCase(authority))
        {
            try
            {
                authenticationContext = new AuthenticationContext(App.getInstance().getApplicationContext(), authority, …);
                App.getInstance().setAuthenticationContext(authenticationContext);
            }
            catch (NoSuchAlgorithmException e)
            {
                …
                authenticationCompletionCallbackToMsipc.onFailure();
            }
            catch (NoSuchPaddingException e)
            {
                …
                authenticationCompletionCallbackToMsipc.onFailure();
            }
       }
        App.getInstance().getAuthenticationContext().acquireToken(mParentActivity, resource, mClientId, mRedirectURI, userId, mPromptBehavior,
                       "&USERNAME=" + userHint, new AuthenticationCallback<AuthenticationResult>()
                        {
                            @Override
                            public void onError(Exception exc)
                            {
                                …
                                if (exc instanceof AuthenticationCancelError)
                                {
                                     …
                                    authenticationCompletionCallbackToMsipc.onCancel();
                                }
                                else
                                {
                                     …
                                    authenticationCompletionCallbackToMsipc.onFailure();
                                }
                            }

                            @Override
                            public void onSuccess(AuthenticationResult result)
                            {
                                …
                                if (result == null || result.getAccessToken() == null
                                        || result.getAccessToken().isEmpty())
                                {
                                     …
                                }
                                else
                                {
                                    // request is successful
                                    …
                                    authenticationCompletionCallbackToMsipc.onSuccess(result.getAccessToken());
                                }
                            }
                        });
                         }


**Uwierzytelnianie użytkownika systemu iOS/OS X** — więcej informacji znajduje się w części [Przykłady kodu dla systemu iOS/OS X](ios-os-x-code-examples.md), *Krok 2 pierwszego scenariusza, „Korzystanie z pliku chronionego usługi RMS”*.


    // AuthenticationCallback holds the necessary information to retrieve an access token.
    @interface MsipcAuthenticationCallback : NSObject<MSAuthenticationCallback>

    @end

    @implementation MsipcAuthenticationCallback

    - (void)accessTokenWithAuthenticationParameters:
         (MSAuthenticationParameters *)authenticationParameters
                                completionBlock:
         (void(^)(NSString *accessToken, NSError *error))completionBlock
    {
    ADAuthenticationError *error;
    ADAuthenticationContext* context = [ADAuthenticationContext authenticationContextWithAuthority:authenticationParameters.authority error:&error];

    NSString *appClientId = @”12345678-ABCD-ABCD-ABCD-ABCDEFGHIJ”;

    // get your registered Azure AD application ID here

    NSURL *redirectURI = [NSURL URLWithString:@”ms-sample://com.microsoft.sampleapp”];

    // get your <app-scheme>://<bundle-id> here
    // Retrieve token using ADAL
    [context acquireTokenWithResource:authenticationParameters.resource
                             clientId:appClientId
                          redirectUri:redirectURI
                               userId:authenticationParameters.userId
                      completionBlock:^(ADAuthenticationResult *result)
                      {
                          if (result.status != AD_SUCCEEDED)
                          {
                              NSLog(@"Auth Failed");
                              completionBlock(nil, result.error);
                          }
                          else
                          {
                              completionBlock(result.accessToken, result.error);
                          }
                      }

        ];
    }



**Uwierzytelnianie użytkownika systemu Linux** — więcej informacji znajduje się w sekcji [Przykłady kodu dla systemu Linux](linux-c-code-examples.md).



    // Class Header
    class AuthCallback : public IAuthenticationCallback {
    private:

      std::shared_ptr<rmsauth::FileCache> FileCachePtr;
      std::string clientId_;
      std::string redirectUrl_;

      public:

      AuthCallback(const std::string& clientId,
               const std::string& redirectUrl);
      virtual std::string GetToken(shared_ptr<AuthenticationParameters>& ap) override;
    };

    class ConsentCallback : public IConsentCallback {
      public:

      virtual ConsentList Consents(ConsentList& consents) override;
    };

    // Class Implementation
    AuthCallback::AuthCallback(const string& clientId, const string& redirectUrl)
    : clientId_(clientId), redirectUrl_(redirectUrl) {
      FileCachePtr = std::make_shared<FileCache>();
    }

    string AuthCallback::GetToken(shared_ptr<AuthenticationParameters>& ap)
    {
      string redirect =
      ap->Scope().empty() ? redirectUrl_ : ap->Scope();

      try
      {
        if (redirect.empty()) {
        throw rmscore::exceptions::RMSInvalidArgumentException(
              "redirect Url is empty");
      }

      if (clientId_.empty()) {
      throw rmscore::exceptions::RMSInvalidArgumentException("client Id is empty");
      }

      AuthenticationContext authContext(
        ap->Authority(), AuthorityValidationType::False, FileCachePtr);

      auto result = authContext.acquireToken(ap->Resource(),
                                           clientId_, redirect,
                                           PromptBehavior::Auto,
                                           ap->UserId());
      return result->accessToken();
      }

      catch (const rmsauth::Exception& ex)
      {
        // out logs
        throw;
      }
    }
