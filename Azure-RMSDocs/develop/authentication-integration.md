---
# required metadata

title: Porady&#58; Dodawanie uwierzytelniania do aplikacji | Azure RMS
description: W tym artykule opisano podstawy uwierzytelniania użytkowników w aplikacji z włączoną obsługą usługi RMS
keywords:
author: bruceperlerms
manager: mbaldwin
ms.date: 04/28/2016
ms.topic: article
ms.prod: azure
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: 200D9B23-F35D-4165-9AC4-C482A5CE1D28
# optional metadata

#ROBOTS:
audience: developer
#ms.devlang:
ms.reviewer: shubhamp
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# Porady: Dodawanie uwierzytelniania do aplikacji

W tym artykule opisano podstawy uwierzytelniania użytkowników w aplikacji z włączoną obsługą usługi RMS

## Czym jest uwierzytelnianie użytkownika
Uwierzytelnianie użytkownika to kluczowy etap nawiązywania komunikacji między aplikacją urządzenia i infrastrukturą usługi RMS. Ten proces uwierzytelniania używa standardowego protokołu OAuth 2.0, który wymaga następujących fragmentów informacji dotyczących bieżącego użytkownika i jego żądania uwierzytelnienia: **urząd**, **zasób** i **identyfikator użytkownika**.

**Uwaga**  Zakres nie jest obecnie używany, ale może być, w związku z czym jest zarezerwowany do użytku w przyszłości.

 

**Wywołanie zwrotne uwierzytelniania użytkownika** — zestaw SDK 4.2 usługi Microsoft Rights Management korzysta z Twojego wdrożenia wywołania zwrotnego uwierzytelniania w przypadku niepodania tokenu dostępu, jeśli konieczne jest odświeżenie tokenu dostępu lub w przypadku wygaśnięcia tego tokenu.

Każdy z interfejsów API usługi RMS platformy dysponuje wywołaniem zwrotnym, które należy wdrożyć w celu umożliwienia uwierzytelniania użytkownika.

-   Interfejs API systemu Android wykorzystuje interfejsy [**AuthenticationRequestCallback**](/rights-management/sdk/4.2/api/android/com.microsoft.rightsmanagement#msipcthin2_authenticationrequestcallback_interface_java) i [**AuthenticationCompletionCallback**](/rights-management/sdk/4.2/api/android/authenticationcompletioncallback#msipcthin2_authenticationcompletioncallback_interface_java)
-   Interfejs API systemów iOS/OS X wykorzystuje protokół [**MSAuthenticationCallback**](/rights-management/sdk/4.2/api/iOS/iOS#msipcthin2_msauthenticationcallback_protocol_objc).
-   Interfejs API systemu WinPhone wykorzystuje interfejs [**IAuthenticationCallback**](/rights-management/sdk/4.2/api/winrt/Microsoft.RightsManagement#msipcthin2_iauthenticationcallback).
-   Interfejs API systemu Linux wykorzystuje interfejs [IAuthenticationCallback](http://azuread.github.io/rms-sdk-for-cpp/classrmscore_1_1modernapi_1_1IAuthenticationCallback.html).

## Jakiej biblioteki użyć podczas uwierzytelniania

W celu wdrożenia wywołania zwrotnego uwierzytelniania należy pobrać odpowiednią bibliotekę i skonfigurować środowisko deweloperskie do korzystania z niej. W witrynie GitHub są dostępne biblioteki ADAL dla tych platform. Każdy z poniższych zasobów zawiera wskazówki dotyczące konfiguracji środowiska i korzystania z biblioteki.

-   [Biblioteka Windows Azure Active Directory Authentication Library (ADAL) dla systemu iOS](https://github.com/MSOpenTech/azure-activedirectory-library-for-ios/)
-   [Biblioteka Windows Azure Active Directory Authentication Library (ADAL) dla komputerów Mac](https://github.com/MSOpenTech/azure-activedirectory-library-for-ios/)
-   [Biblioteka Windows Azure Active Directory Authentication Library (ADAL) dla systemu Android](https://github.com/MSOpenTech/azure-activedirectory-library-for-android)
-   [Biblioteka Windows Azure Active Directory Authentication Library (ADAL) dla platformy dotnet](https://github.com/AzureAD/azure-activedirectory-library-for-dotnet)
-   W przypadku zestawu SDK dla systemu Linux biblioteka ADAL jest spakowana ze źródłem SDK, dostępnym w witrynie [Github](https://github.com/AzureAD/rms-sdk-for-cpp).

**Uwaga**  Zalecamy korzystanie z jednej z powyższych bibliotek Active Directory Authentication Library (ADAL), choć można też korzystać z innych bibliotek uwierzytelniania.

## Dane wejściowe uwierzytelniania przy użyciu biblioteki Azure Active Directory Authentication Library (ADAL)

Biblioteka ADAL wymaga kilku parametrów w celu pomyślnego uwierzytelnienia użytkownika w usłudze Azure RMS (lub AD RMS). Są to standardowe parametry protokołu OAuth 2.0, wymagane generalnie od wszystkich aplikacji usługi Azure AD, jak również aplikacji z obsługą usługi RMS. Bieżące wytyczne dotyczące korzystania z biblioteki ADAL zamieszczono w plikach README odpowiednich repozytoriów Github wymienionych powyżej.

Poniższe parametry i zalecenia są wymagane dla przepływów pracy usługi RMS:

-   **Urząd** — adres URL punktu końcowego uwierzytelniania, zazwyczaj AAD lub ADFS. Parametr ten jest dostarczany aplikacji przez wywołanie zwrotne uwierzytelniania zestawu SDK usługi RMS.
-   **Zasób** — adres URL/identyfikator URI aplikacji usługi, do której próbujesz uzyskać dostęp, zazwyczaj Azure RMS lub AD RMS. Parametr ten jest dostarczany aplikacji przez wywołanie zwrotne uwierzytelniania zestawu SDK usługi RMS.
-   **Identyfikator użytkownika** — nazwa UPN, zwykle adres e-mail użytkownika, który próbuje uzyskać dostęp do aplikacji. Parametr ten może być pusty, jeśli użytkownik nie jest jeszcze znany. Jest używany także do buforowania tokenu użytkownika i żądania tokenu z pamięci podręcznej. Wartość ta jest używana zazwyczaj także jako wskazówka do monitowania użytkownika.
-   **Identyfikator klienta** — identyfikator aplikacji klienta. Musi to być poprawny identyfikator aplikacji usługi Azure AD. Aby uzyskać więcej informacji, zobacz Porady: Uzyskiwanie identyfikatora aplikacji Azure.
-   **Identyfikator Uri przekierowania** — podaje bibliotekę uwierzytelniania z celem URI dla kodu uwierzytelniania. Należy pamiętać, że systemy iOS i Android wymagają określonych formatów, które zostały opisane w plikach README odpowiednich repozytoriów GitHub biblioteki ADAL.

    Android: `msauth://packagename/Base64UrlencodedSignature`

    iOS: `<app-scheme>://<bundle-id>`

**Uwaga**  Jeśli aplikacja nie jest zgodna z tymi wytycznymi, przepływy pracy usług Azure RMS i Azure AD zakończą się prawdopodobnie niepowodzeniem i nie będą obsługiwane przez witrynę Microsoft.com. Dodatkowo użycie nieprawidłowego identyfikatora klienta w aplikacji produkcyjnej może oznaczać naruszenie umowy licencyjnej usługi Rights Management (RMLA).

## Jak powinno wyglądać wdrożenie wywołania zwrotnego uwierzytelniania

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


**Uwierzytelnianie użytkownika systemu iOS/OS X** — więcej informacji znajduje się w części [Przykłady kodu dla systemu iOS/OS X](ios-os-x-code-examples.md),

**Krok 2** pierwszego scenariusza, „Korzystanie z pliku chronionego usługi RMS”.


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



**Uwierzytelnianie użytkownika systemu Linux/języka C++** — więcej informacji znajduje się w sekcji [Przykłady kodu dla systemu Linux](linux-c-code-examples.md).



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



 

 


<!--HONumber=Apr16_HO4-->


