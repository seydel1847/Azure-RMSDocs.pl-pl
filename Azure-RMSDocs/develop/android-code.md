---
title: "Przykłady kodu dla systemu Android | Azure RMS"
description: "W tym temacie przedstawiono ważne elementy kodu dla zestawu RMS SDK w wersji dla systemu Android."
keywords: 
author: lleonard-msft
ms.author: alleonar
manager: mbaldwin
ms.date: 02/23/2017
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: 58CC2E50-1E4D-4621-A947-25312C3FF519
audience: developer
ms.reviewer: shubhamp
ms.suite: ems
ms.openlocfilehash: f23f8d1d4deddb1a0ee70a755cf94637396337c0
ms.sourcegitcommit: dca4534a0aa7f63c0c525c9a3ce445088d1362bb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/19/2018
---
# <a name="android-code-examples"></a>Przykłady kodu dla systemu Android

W tym artykule przedstawiono sposób code elementy dla systemu Android wersji zestawu RMS SDK.

**Uwaga** w tym artykule określenie _MSIPC_ (Microsoft Information Protection i sterowania) odwołuje się do procesu klienta.


## <a name="using-the-microsoft-rights-management-sdk-42---key-scenarios"></a>Korzystanie z zestawu Microsoft Rights Management SDK 4.2 — najważniejsze scenariusze

Te przykłady kodu są pobierane z większej aplikacji przykładowej, reprezentujące scenariusze programowania ważne dla orientacji w zestawie SDK. Pokazywały sposób użycia:

- Format Microsoft Protected File, nazywany również _pliku chronionego_.
- Formaty plików chroniony niestandardowo
- Formanty niestandardowego interfejsu użytkownika (UI)

*MSIPCSampleApp* Przykładowa aplikacja jest dostępna do użycia z tym zestawem SDK dla systemu operacyjnego Android. Aby dowiedzieć się więcej, zobacz [rms-zestawu sdk-ui-for-android](https://github.com/AzureAD/rms-sdk-ui-for-android).

### <a name="scenario-consume-an-rms-protected-file"></a>Scenariusz: korzystanie z pliku chronionego przez usługę RMS

- **Krok 1**: tworzenie [ProtectedFileInputStream](https://msdn.microsoft.com/library/dn790851.aspx).

    **Źródło**: *MsipcAuthenticationCallback.java*

    **Opis elementu**: Utwórz wystąpienie [ProtectedFileInputStream](https://msdn.microsoft.com/library/dn790851.aspx) obiektu i implementuje uwierzytelnianie usługi.  Użyj [AuthenticationRequestCallback](https://msdn.microsoft.com/library/dn758250.aspx) do pobrania tokenu przez przekazanie wystąpienia **AuthenticationRequestCallback**, jako parametr *mRmsAuthCallback*, aby MSIPC INTERFEJS API. Zobacz wywołanie [ProtectedFileInputStream.create](https://msdn.microsoft.com/library/dn790851.aspx) pod koniec sekcji przykładu kodu poniżej.

    ``` java
        public void startContentConsumptionFromPtxtFileFormat(InputStream inputStream)
        {
            CreationCallback<ProtectedFileInputStream> protectedFileInputStreamCreationCallback =
              new CreationCallback<ProtectedFileInputStream>()
            {
                @Override
                public Context getContext()
                {
                   …
               }

                @Override
                public void onCancel()
                {
                   …
                }

                @Override
                public void onFailure(ProtectionException e)
                {
                   …
                }

                @Override
                public void onSuccess(ProtectedFileInputStream protectedFileInputStream)
                {
                   …
                   …
                    byte[] dataChunk = new byte[16384];
                    try
                    {
                        while ((nRead = protectedFileInputStream.read(dataChunk, 0,
                                dataChunk.length)) != -1)
                        {
                            …
                        }
                         …
                        protectedFileInputStream.close();
                    }
                    catch (IOException e)
                    {
                      …
                    }  
              }
            };
            try
            {
               …
                ProtectedFileInputStream.create(inputStream, null, mRmsAuthCallback,
                                                PolicyAcquisitionFlags.NONE,
                                                protectedFileInputStreamCreationCallback);
            }
            catch (com.microsoft.rightsmanagement.exceptions.InvalidParameterException e)
            {
                …
            }
        }
    ```

- **Krok 2**: Konfigurowanie uwierzytelniania przy użyciu biblioteki uwierzytelniania usługi Active Directory (ADAL).

    **Źródło**: *MsipcAuthenticationCallback.java*.

    **Opis elementu**: ten krok używa biblioteki ADAL do zaimplementowania [AuthenticationRequestCallback](https://msdn.microsoft.com/library/dn758255.aspx) z przykładowymi parametrami uwierzytelniania. Aby dowiedzieć się więcej, zobacz [Azure AD Authentication Library (ADAL)](https://msdn.microsoft.com/library/jj573266.aspx).


    ``` java
        class MsipcAuthenticationCallback implements AuthenticationRequestCallback
        {

        …

        @Override
        public void getToken(Map<String, String> authenticationParametersMap,
                             final AuthenticationCompletionCallback authenticationCompletionCallbackToMsipc)
        {
            String authority = authenticationParametersMap.get("oauth2.authority");
            String resource = authenticationParametersMap.get("oauth2.resource");
            String userId = authenticationParametersMap.get("userId");
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
                            }

                            );
                      }
    ```

- **Krok 3**. Sprawdzenie, czy dla tego użytkownika z tą zawartością istnieje prawo **Edycja** za pomocą metody [UserPolicy.accessCheck](https://msdn.microsoft.comlibrary/dn790885.aspx).

    **Źródło**: *TextEditorFragment.java*

    ``` java
         //check if user has edit rights and apply enforcements
                if (!mUserPolicy.accessCheck(EditableDocumentRights.Edit))
                {
                    mTextEditor.setFocusableInTouchMode(false);
                    mTextEditor.setFocusable(false);
                    mTextEditor.setEnabled(false);
                    …
                }
    ```


### <a name="scenario-create-a-new-protected-file-using-a-template"></a>Scenariusz: tworzenie nowego pliku chronionego z wykorzystaniem szablonu

Ten scenariusz rozpoczyna się od pobrania listy szablonów, wybrania pierwszego w celu utworzenia zasady, a następnie tworzony i zapisywany jest nowy plik chroniony.

- **Krok 1**. Pobranie listy szablonów za pomocą obiektu [TemplateDescriptor](https://msdn.microsoft.com/library/dn790871.aspx).

    **Źródło**: *MsipcTaskFragment.java*

    ``` java
    CreationCallback<List<TemplateDescriptor>> getTemplatesCreationCallback = new CreationCallback<List<TemplateDescriptor>>()
      {
          @Override
          public Context getContext()
          {
              …
          }

          @Override
          public void onCancel()
          {
              …
          }

          @Override
          public void onFailure(ProtectionException e)
          {
              …
          }

          @Override
          public void onSuccess(List<TemplateDescriptor> templateDescriptors)
          {
             …
          }
      };
      try
      {
              …
          mIAsyncControl = TemplateDescriptor.getTemplates(emailId, mRmsAuthCallback, getTemplatesCreationCallback);
      }
      catch (com.microsoft.rightsmanagement.exceptions.InvalidParameterException e)
      {
              …
      }
    ```

- **Krok 2**. Utworzenie obiektu [UserPolicy](https://msdn.microsoft.com/library/dn790887.aspx) przy użyciu pierwszego szablonu na liście.

    **Źródło**: *MsipcTaskFragment.java*

    ``` java
      CreationCallback<UserPolicy> userPolicyCreationCallback = new CreationCallback<UserPolicy>()
      {
          @Override
          public Context getContext()
          {
              …
          }

          @Override
          public void onCancel()
          {
              …
          }

          @Override
          public void onFailure(ProtectionException e)
          {
              …
          }

          @Override
          public void onSuccess(final UserPolicy item)
          {
              …
          }
      };
      try
      {
           …
          mIAsyncControl = UserPolicy.create((TemplateDescriptor)selectedDescriptor, mEmailId, mRmsAuthCallback,
                            UserPolicyCreationFlags.NONE, userPolicyCreationCallback);
           …
      }
      catch (InvalidParameterException e)
      {
              …
      }
    ```

-  **Krok 3**. Utworzenie obiektu [ProtectedFileOutputStream](https://msdn.microsoft.com/library/dn790855.aspx) i zapisanie w nim zawartości.

    **Źródło**: *MsipcTaskFragment.java*

    ``` java
    private void createPTxt(final byte[] contentToProtect)
        {
             …
            CreationCallback<ProtectedFileOutputStream> protectedFileOutputStreamCreationCallback = new CreationCallback<ProtectedFileOutputStream>()
            {
                @Override
                public Context getContext()
                {
                 …
                }

                @Override
                public void onCancel()
                {
                 …
                }

                @Override
                public void onFailure(ProtectionException e)
                {
                 …
                }

                @Override
                public void onSuccess(ProtectedFileOutputStream protectedFileOutputStream)
                {
                    try
                    {
                        // write to this stream
                        protectedFileOutputStream.write(contentToProtect);
                        protectedFileOutputStream.flush();
                        protectedFileOutputStream.close();
                        …
                    }
                    catch (IOException e)
                    {
                        …
                    }
                }
            };
            try
            {
                File file = new File(filePath);
                outputStream = new FileOutputStream(file);
                mIAsyncControl = ProtectedFileOutputStream.create(outputStream, mUserPolicy, originalFileExtension,
                        protectedFileOutputStreamCreationCallback);
            }
            catch (FileNotFoundException e)
            {
                 …
            }
            catch (InvalidParameterException e)
            {
                 …
            }
        }
    ```


### <a name="scenario-open-a-custom-protected-file"></a>Scenariusz: otwieranie niestandardowego pliku chronionego

- **Krok 1**. Utworzenie obiektu [UserPolicy](https://msdn.microsoft.com/library/dn790887.aspx) z elementu *serializedContentPolicy*.

    **Źródło**: *MsipcTaskFragment.java*

    ``` java
    CreationCallback<UserPolicy> userPolicyCreationCallbackFromSerializedContentPolicy = new CreationCallback<UserPolicy>()
            {
                @Override
                public void onSuccess(UserPolicy userPolicy)
                {
                  …
                }

                @Override
                public void onFailure(ProtectionException e)
                {
                  …
                }

                @Override
                public void onCancel()
                {
                  …
                }

                @Override
                public Context getContext()
                {
                  …
                }
            };


    try
    {
      ...

      // Read the serializedContentPolicyLength from the inputStream.
      long serializedContentPolicyLength = readUnsignedInt(inputStream);

      // Read the PL bytes from the input stream using the PL size.
      byte[] serializedContentPolicy = new byte[(int)serializedContentPolicyLength];
      inputStream.read(serializedContentPolicy);

      ...

      UserPolicy.acquire(serializedContentPolicy, null, mRmsAuthCallback, PolicyAcquisitionFlags.NONE,
              userPolicyCreationCallbackFromSerializedContentPolicy);
    }
    catch (com.microsoft.rightsmanagement.exceptions.InvalidParameterException e)
    {
      ...
    }
    catch (IOException e)
    {
      ...
    }
    ```


- **Krok 2**. Utworzenie obiektu [CustomProtectedInputStream](https://msdn.microsoft.com/library/dn758271.aspx) za pomocą obiektu [UserPolicy](https://msdn.microsoft.com/library/dn790887.aspx) z **Kroku 1**.

    **Źródło**: *MsipcTaskFragment.java*

    ``` java
      CreationCallback<CustomProtectedInputStream> customProtectedInputStreamCreationCallback = new CreationCallback<CustomProtectedInputStream>()
      {
         @Override
         public Context getContext()
         {
             …
         }

         @Override
         public void onCancel()
         {
             …
         }

         @Override
         public void onFailure(ProtectionException e)
         {
             …
         }

         @Override
         public void onSuccess(CustomProtectedInputStream customProtectedInputStream)
         {
            …

             byte[] dataChunk = new byte[16384];
             try
             {
                 while ((nRead = customProtectedInputStream.read(dataChunk, 0, dataChunk.length)) != -1)
                 {
                      …
                 }
                  …
                 customProtectedInputStream.close();
             }
             catch (IOException e)
             {
                …
             }
             …
         }
     };

    try
    {
      ...

      // Retrieve the encrypted content size.
      long encryptedContentLength = readUnsignedInt(inputStream);

      updateTaskStatus(new TaskStatus(TaskState.Starting, "Consuming content", true));

      CustomProtectedInputStream.create(userPolicy, inputStream,
                                     encryptedContentLength,
                                     customProtectedInputStreamCreationCallback);
    }
    catch (com.microsoft.rightsmanagement.exceptions.InvalidParameterException e)
    {
      ...
    }
    catch (IOException e)
    {
      ...
    }
    ```

- **Krok 3**. Odczyt zawartości z obiektu [CustomProtectedInputStream](https://msdn.microsoft.com/library/dn758271.aspx) do parametru *mDecryptedContent*, a następnie zamknięcie.

    **Źródło**: *MsipcTaskFragment.java*

    ``` java
    @Override
    public void onSuccess(CustomProtectedInputStream customProtectedInputStream)
    {
      mUserPolicy = customProtectedInputStream.getUserPolicy();
      ByteArrayOutputStream buffer = new ByteArrayOutputStream();

      int nRead;                      
      byte[] dataChunk = new byte[16384];

      try
      {
        while ((nRead = customProtectedInputStream.read(dataChunk, 0,
                                                            dataChunk.length)) != -1)
        {
           buffer.write(dataChunk, 0, nRead);
        }

        buffer.flush();
        mDecryptedContent = new String(buffer.toByteArray(), Charset.forName("UTF-8"));

        buffer.close();
        customProtectedInputStream.close();
      }
      catch (IOException e)
      {
        ...
      }
    }
    ```

### <a name="scenario-create-a-custom-protected-file-using-a-custom-policy"></a>Scenariusz: Tworzenie niestandardowego pliku chronionego za pomocą zasad niestandardowych

- **Krok 1**. Utworzenie deskryptora zasad przy użyciu adresu e-mail podanego przez użytkownika.

    **Źródło**: *MsipcTaskFragment.java*

    **Opis elementu**: W praktyce następujące obiekty zostałyby utworzone przy użyciu danych wprowadzonych przez użytkownika z interfejsu urządzenia; [UserRights](https://msdn.microsoft.com/library/dn790911.aspx) i [PolicyDescriptor](https://msdn.microsoft.com/library/dn790843.aspx).

    ``` java
      // create userRights list
      UserRights userRights = new UserRights(Arrays.asList("consumer@domain.com"),
        Arrays.asList( CommonRights.View, EditableDocumentRights.Print));
      ArrayList<UserRights> usersRigthsList = new ArrayList<UserRights>();
      usersRigthsList.add(userRights);

      // Create PolicyDescriptor using userRights list
      PolicyDescriptor policyDescriptor = PolicyDescriptor.createPolicyDescriptorFromUserRights(
                                                             usersRigthsList);
      policyDescriptor.setOfflineCacheLifetimeInDays(10);
      policyDescriptor.setContentValidUntil(new Date());
    ```


- **Krok 2**. Utworzenie niestandardowego obiektu [UserPolicy](https://msdn.microsoft.com/library/dn790887.aspx) z deskryptora zasad *selectedDescriptor*.

    **Źródło**: *MsipcTaskFragment.java*

    ``` java
       mIAsyncControl = UserPolicy.create((PolicyDescriptor)selectedDescriptor,
         mEmailId, mRmsAuthCallback, UserPolicyCreationFlags.NONE, userPolicyCreationCallback);
    ```


- **Krok 3**. Utworzenie i zapisanie zawartości do obiektu [CustomProtectedOutputStream](https://msdn.microsoft.com/library/dn758274.aspx), a następnie zamknięcie.

    **Źródło**: *MsipcTaskFragment.java*

    ``` java
    File file = new File(filePath);
        final OutputStream outputStream = new FileOutputStream(file);
        CreationCallback<CustomProtectedOutputStream> customProtectedOutputStreamCreationCallback = new CreationCallback<CustomProtectedOutputStream>()
        {
            @Override
            public Context getContext()
            {
              …
            }

            @Override
            public void onCancel()
            {
              …
            }

            @Override
            public void onFailure(ProtectionException e)
            {
              …
            }

            @Override
            public void onSuccess(CustomProtectedOutputStream protectedOutputStream)
            {
                try
                {
                    // write serializedContentPolicy
                    byte[] serializedContentPolicy = mUserPolicy.getSerializedContentPolicy();
                    writeLongAsUnsignedIntToStream(outputStream, serializedContentPolicy.length);
                    outputStream.write(serializedContentPolicy);
                    // write encrypted content
                    if (contentToProtect != null)
                    {
                        writeLongAsUnsignedIntToStream(outputStream,
                                CustomProtectedOutputStream.getEncryptedContentLength(contentToProtect.length,
                                        protectedOutputStream.getUserPolicy()));
                        protectedOutputStream.write(contentToProtect);
                        protectedOutputStream.flush();
                        protectedOutputStream.close();
                    }
                    else
                    {
                        outputStream.flush();
                        outputStream.close();
                    }
                    …
                }
                catch (IOException e)
                {
                  …
                }
            }
        };
        try
        {
            mIAsyncControl = CustomProtectedOutputStream.create(outputStream, mUserPolicy,
                    customProtectedOutputStreamCreationCallback);
        }
        catch (InvalidParameterException e)
        {
          …
        }
    ```

[!INCLUDE[Commenting house rules](../includes/houserules.md)]