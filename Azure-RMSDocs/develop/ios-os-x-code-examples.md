---
title: Przykłady kodu dla systemu iOS/OS X | Azure RMS
description: W tym temacie przedstawiono ważne elementy kodu dla zestawu RMS SDK w wersji dla systemu iOS/OS X.
keywords: ''
author: lleonard-msft
ms.author: alleonar
manager: mbaldwin
ms.date: 02/23/2017
ms.topic: article
ms.prod: ''
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: 7E12EBF2-5A19-4A8D-AA99-531B09DA256A
audience: developer
ms.reviewer: shubhamp
ms.suite: ems
ms.openlocfilehash: 121296ed8d2e160bd602ae9d88843eb1580f17f6
ms.sourcegitcommit: 8e622a93ff8d07a180e3be6e8b14748354e640bd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/29/2018
---
# <a name="iosos-x-code-examples"></a>Przykłady kodu dla systemu iOS/OS X

W tym temacie przedstawiono ważne elementy kodu dla zestawu RMS SDK w wersji dla systemu iOS/OS X.

**Uwaga**: w przykładzie kodu i opisach używany jest termin MSIPC (Microsoft Information Protection and Control) jako odwołanie do procesu klienta.



## <a name="using-the-microsoft-rights-management-sdk-42---key-scenarios"></a>Korzystanie z zestawu Microsoft Rights Management SDK 4.2 — najważniejsze scenariusze


Poniżej podano przykłady kodu w języku **Objective C** z większej aplikacji przykładowej, reprezentujące scenariusze programowania ważne dla orientacji w zestawie SDK. Pokazują one korzystanie z formatu Microsoft Protected File (nazywanego plikiem chronionym), niestandardowych formatów plików chronionych oraz niestandardowych kontrolek interfejsu użytkownika.

### <a name="scenario-consume-an-rms-protected-file"></a>Scenariusz: korzystanie z pliku chronionego przez usługę RMS


- **Krok 1**. Utworzenie obiektu [MSProtectedData](https://msdn.microsoft.com/library/dn758348.aspx)

 **Opis**: Utworzenie wystąpienia obiektu [MSProtectedData](https://msdn.microsoft.com/library/dn758348.aspx) za pomocą metody create, która implementuje uwierzytelnianie usługi przy użyciu interfejsu [MSAuthenticationCallback](https://msdn.microsoft.com/library/dn758312.aspx) w celu pobrania tokenu przez przekazanie wystąpienia interfejsu **MSAuthenticationCallback** jako parametru *authenticationCallback* do interfejsu API klienta MSIPC. Zobacz wywołanie metody [MSProtectedData protectedDataWithProtectedFile](https://msdn.microsoft.com/library/dn758351.aspx) w poniższej sekcji z przykładowym kodem.

        + (void)consumePtxtFile:(NSString *)path authenticationCallback:(id<MSAuthenticationCallback>)authenticationCallback
        {
            // userId can be provided as a hint for authentication
            [MSProtectedData protectedDataWithProtectedFile:path
                                                 userId:nil
                                 authenticationCallback:authenticationCallback
                                                options:Default
                                        completionBlock:^(MSProtectedData *data, NSError *error)
            {
                //Read the content from the ProtectedData, this will decrypt the data
                NSData *content = [data retrieveData];
            }];
        }

- **Krok 2**. Skonfigurowanie uwierzytelniania przy użyciu biblioteki Active Directory Authentication Library (ADAL)

  **Opis**: W tym kroku zobaczysz bibliotekę ADAL używaną do zaimplementowania interfejsu [MSAuthenticationCallback](https://msdn.microsoft.com/library/dn758312.aspx) z przykładowymi parametrami uwierzytelniania. Aby uzyskać więcej informacji na temat używania biblioteki ADAL, zobacz Biblioteka Azure AD Authentication Library (ADAL).

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
          ADAuthenticationContext* context = [
              ADAuthenticationContext authenticationContextWithAuthority:authenticationParameters.authority
                                                                error:&error
          ];
          NSString *appClientId = @”com.microsoft.sampleapp”;
          NSURL *redirectURI = [NSURL URLWithString:@"local://authorize"];
          // Retrieve token using ADAL
          [context acquireTokenWithResource:authenticationParameters.resource
                                 clientId:appClientId
                              redirectUri:redirectURI
                                   userId:authenticationParameters.userId
                          completionBlock:^(ADAuthenticationResult *result) {
                              if (result.status != AD_SUCCEEDED)
                              {
                                  NSLog(@"Auth Failed");
                                  completionBlock(nil, result.error);
                              }
                              else
                              {
                                  completionBlock(result.accessToken, result.error);
                              }
                          }];
       }

-   **Krok 3**. Sprawdzenie, czy dla tego użytkownika z tą zawartością istnieje prawo Edycja za pomocą metody [MSUserPolicy accessCheck](https://msdn.microsoft.com/library/dn790789.aspx) obiektu [MSUserPolicy](https://msdn.microsoft.com/library/dn790796.aspx).

        - (void)accessCheckWithProtectedData:(MSProtectedData *)protectedData
        {
            //check if user has edit rights and apply enforcements
            if (!protectedData.userPolicy.accessCheck(EditableDocumentRights.Edit))
            {
                // enforce on the UI
                textEditor.focusableInTouchMode = NO;
                textEditor.focusable = NO;
                textEditor.enabled = NO;
            }
        }

### <a name="scenario-create-a-new-protected-file-using-a-template"></a>Scenariusz: tworzenie nowego pliku chronionego z wykorzystaniem szablonu

Ten scenariusz rozpoczyna się od pobrania listy szablonów — interfejsu [MSTemplateDescriptor](https://msdn.microsoft.com/library/dn790785.aspx) — i wybrania pierwszego szablonu w celu utworzenia zasady. Następnie jest tworzony i zapisywany nowy plik chroniony.

-   **Krok 1**. Pobranie listy szablonów

        + (void)templateListUsageWithAuthenticationCallback:(id<MSAuthenticationCallback>)authenticationCallback
        {
            [MSTemplateDescriptor templateListWithUserId:@"user@domain.com"
                            authenticationCallback:authenticationCallback
                                   completionBlock:^(NSArray/*MSTemplateDescriptor*/ *templates, NSError *error)
                                   {
                                     // use templates array of MSTemplateDescriptor (Note: will be nil on error)
                                   }];
        }

-   **Krok 2**. Utworzenie obiektu [MSUserPolicy](https://msdn.microsoft.com/library/dn790796.aspx) przy użyciu pierwszego szablonu na liście.

        + (void)userPolicyCreationFromTemplateWithAuthenticationCallback:(id<MSAuthenticationCallback>)authenticationCallback
        {
            [MSUserPolicy userPolicyWithTemplateDescriptor:[templates objectAtIndex:0]
                                            userId:@"user@domain.com"
                                     signedAppData:nil
                            authenticationCallback:authenticationCallback
                                           options:None
                                   completionBlock:^(MSUserPolicy *userPolicy, NSError *error)
            {
            // use userPolicy (Note: will be nil on error)
            }];
        }

-   **Krok 3**. Utworzenie obiektu [MSMutableProtectedData](https://msdn.microsoft.com/library/dn758325.aspx) i zapisanie w nim zawartości.

        + (void)createPtxtWithUserPolicy:(MSUserPolicy *)userPolicy contentToProtect:(NSData *)contentToProtect
        {
            // create an MSMutableProtectedData to write content
            [contentToProtect protectedDataInFile:filePath
                        originalFileExtension:kDefaultTextFileExtension
                               withUserPolicy:userPolicy
                              completionBlock:^(MSMutableProtectedData *data, NSError *error)
            {
             // use data (Note: will be nil on error)
            }];
        }

### <a name="scenario-open-a-custom-protected-file"></a>Scenariusz: otwieranie niestandardowego pliku chronionego


-   **Krok 1**. Utworzenie obiektu [MSUserPolicy](https://msdn.microsoft.com/library/dn790796.aspx) z elementu *serializedContentPolicy*.

        + (void)userPolicyWith:(NSData *)protectedData
        authenticationCallback:(id<MSAuthenticationCallback>)authenticationCallback
        {
            // Read header information from protectedData and extract the  PL
            /*-------------------------------------------
            | PL length | PL | ContetSizeLength |
            -------------------------------------------*/
            NSUInteger serializedPolicySize;
            NSMutableData *serializedPolicy;
            [protectedData getBytes:&serializedPolicySize length:sizeof(serializedPolicySize)];
            [protectedData getBytes:[serializedPolicy mutableBytes] length:serializedPolicySize];

            // Get the user policy , this is an async method as it hits the REST service
            // for content key and usage restrictions
            // userId provided as a hint for authentication
            [MSUserPolicy userPolicyWithSerializedPolicy:serializedPolicy
                                              userId:@"user@domain.com"
                              authenticationCallback:authenticationCallback
                                             options:Default
                                     completionBlock:^(MSUserPolicy *userPolicy,
                                                       NSError *error)
            {

            }];
         }

-   **Krok 2**. Utworzenie interfejsu [MSCustomProtectedData](https://msdn.microsoft.com/library/dn758321.aspx) za pomocą obiektu [MSUserPolicy](https://msdn.microsoft.com/library/dn790796.aspx) utworzonego w **kroku 1** i odczytanie z niego danych.

        + (void)customProtectedDataWith:(NSData *)protectedData
        {
            // Read header information from protectedData and extract the  protectedContentSize
            /*-------------------------------------------
            | PL length | PL | ContetSizeLength |
            -------------------------------------------*/
            NSUInteger protectedContentSize;
            [protectedData getBytes:&protectedContentSize
                         length:sizeof(protectedContentSize)];

            // Create the MSCustomProtector used for decrypting the content
            // The content start position is the header length
            [MSCustomProtectedData customProtectedDataWithPolicy:userPolicy
                                               protectedData:protectedData
                                        contentStartPosition:sizeof(NSUInteger) + serializedPolicySize
                                                 contentSize:protectedContentSize
                                             completionBlock:^(MSCustomProtectedData *customProtector,
                                                               NSError *error)
            {
             //Read the content from the custom protector, this will decrypt the data
             NSData *content = [customProtector retrieveData];
             NSLog(@"%@", content);
            }];
         }

### <a name="scenario-create-a-custom-protected-file-using-a-custom-ad-hoc-policy"></a>Scenariusz: tworzenie niestandardowego pliku chronionego za pomocą zasad niestandardowych (ad hoc)


-   **Krok 1**. Utworzenie deskryptora zasad przy użyciu adresu e-mail podanego przez użytkownika.

    **Opis**: W praktyce następujące obiekty zostałyby utworzone przy użyciu danych wprowadzonych przez użytkownika z interfejsu urządzenia: [MSUserRights](https://msdn.microsoft.com/library/dn790811.aspx) i [MSPolicyDescriptor](https://msdn.microsoft.com/library/dn758339.aspx).

        + (void)policyDescriptor
        {
            MSUserRights *userRights = [[MSUserRights alloc] initWithUsers:[NSArray arrayWithObjects: @"user1@domain.com", @"user2@domain.com", nil] rights:[MSEmailRights all]];

            MSPolicyDescriptor *policyDescriptor = [[MSPolicyDescriptor alloc] initWithUserRights:[NSArray arrayWithObjects:userRights, nil]];
            policyDescriptor.contentValidUntil = [[NSDate alloc] initWithTimeIntervalSinceNow:NSTimeIntervalSince1970 + 3600.0];
            policyDescriptor.offlineCacheLifetimeInDays = 10;
        }

-   **Krok 2**. Utworzenie niestandardowego obiektu [MSUserPolicy](https://msdn.microsoft.com/library/dn790796.aspx) z deskryptora zasad *selectedDescriptor*.

        + (void)userPolicyWithPolicyDescriptor:(MSPolicyDescriptor *)policyDescriptor
        {
            [MSUserPolicy userPolicyWithPolicyDescriptor:policyDescriptor
                                          userId:@"user@domain.com"
                          authenticationCallback:authenticationCallback
                                         options:None
                                 completionBlock:^(MSUserPolicy *userPolicy, NSError *error)
            {
              // use userPolicy (Note: will be nil on error)
            }];
        }

-   **Krok 3**. Utworzenie obiektu [MSMutableCustomProtectedData](https://msdn.microsoft.com/library/dn758321.aspx) i zapisanie zawartości do niego, a następnie zamknięcie.

        + (void)mutableCustomProtectedData:(NSMutableData *)backingData policy:(MSUserPolicy *)policy contentToProtect:(NSString *)contentToProtect
        {
            //Get the serializedPolicy from a given policy
            NSData *serializedPolicy = [policy serializedPolicy];

            // Write header information to backing data including the PL
            // ------------------------------------
            // | PL length | PL | ContetSizeLength |
            // -------------------------------------
            NSUInteger serializedPolicyLength = [serializedPolicy length];
            [backingData appendData:[NSData dataWithBytes:&serializedPolicyLength length:sizeof(serializedPolicyLength)]];
            [backingData appendData:serializedPolicy];
            NSUInteger protectedContentLength = [MSCustomProtectedData getEncryptedContentLengthWithPolicy:policy contentLength:unprotectedData.length];
            [backingData appendData:[NSData dataWithBytes:&protectedContentLength length:sizeof(protectedContentLength)]];

            NSUInteger headerLength = sizeof(serializedPolicyLength) + serializedPolicyLength + sizeof(protectedContentLength);

            // Create the MSMutableCustomProtector used for encrypting content
            // The content start position is the current length of the backing data
            // The encryptedContentSize content size is 0 since there is no content yet
            [MSMutableCustomProtectedData customProtectorWithUserPolicy:policy
                                                        backingData:backingData
                                             protectedContentOffset:headerLength
                                                    completionBlock:^(MSMutableCustomProtectedData *customProtector,
                                                                      NSError *error)
            {
                //Append data to the custom protector, this will encrypt the data and write it to the backing data
                [customProtector appendData:[contentToProtect dataUsingEncoding:NSUTF8StringEncoding] error:&error];

                //close the custom protector so it will flush and finalise encryption
                [customProtector close:&error];

            }];
          }

[!INCLUDE[Commenting house rules](../includes/houserules.md)]