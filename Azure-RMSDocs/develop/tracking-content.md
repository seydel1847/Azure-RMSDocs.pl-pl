---
title: Jak włączyć śledzenie i odwoływanie dokumentów | Azure RMS
description: Podstawowe wskazówki dotyczące implementowania śledzenia dokumentu z zawartością oraz przykładowy kod służący do aktualizacji metadanych i kod przycisku Śledź użycie na potrzeby aplikacji.
keywords: ''
author: bryanla
ms.author: bryanla
manager: mbaldwin
ms.date: 02/23/2017
ms.topic: conceptual
ms.service: information-protection
ms.assetid: F5089765-9D94-452B-85E0-00D22675D847
audience: developer
ms.reviewer: shubhamp
ms.suite: ems
ms.openlocfilehash: 8794d0f7413941573484c7f9509f5be5e2aa2414
ms.sourcegitcommit: bd2b31dd97c8ae08c28b0f5688517110a726e3a1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/08/2019
ms.locfileid: "54071696"
---
# <a name="how-to-enable-document-tracking-and-revocation"></a>Instrukcje: włączanie śledzenia i odwoływania dokumentów

W tym temacie przedstawiono podstawowe wskazówki dotyczące implementowania śledzenia dokumentu z zawartością oraz przykładowy kod służący do aktualizacji metadanych i tworzenia przycisku **Śledź użycie** na potrzeby aplikacji.

## <a name="steps-to-implement-document-tracking"></a>Procedura implementacji śledzenia dokumentów

Kroki 1 i 2 umożliwiają włączenie śledzenia dokumentów. Krok 3 umożliwia użytkownikom aplikacji przejście do witryny śledzenia dokumentów, w której można śledzić i odwoływać chronione dokumenty.

1. Dodawanie metadanych śledzenia dokumentów
2. Rejestrowanie dokumentu za pomocą usługi RMS
3. Dodawanie przycisku Śledź użycie do aplikacji

Szczegóły implementacji dla tej procedury.

## <a name="1-add-document-tracking-metadata"></a>1. Dodawanie metadanych śledzenia dokumentów

Śledzenie dokumentów jest funkcją systemu Rights Management. Przez dodanie określonych metadanych podczas procesu włączania ochrony dokumentu można zarejestrować dokument w portalu usługi śledzenia, który zapewnia kilka opcji śledzenia.

Korzystając z poniższych interfejsów API, można dodać/zaktualizować licencję na zawartość przy użyciu metadanych śledzenia dokumentów.


Z perspektywy operacyjnej śledzenie dokumentów wymaga tylko właściwości **nazwy zawartości** i **typu powiadomienia**.


- [IpcCreateLicenseMetadataHandle](https://msdn.microsoft.com/library/dn974050.aspx)
- [IpcSetLicenseMetadataProperty](https://msdn.microsoft.com/library/dn974059.aspx)

  Oczekujemy, że ustawisz wszystkie właściwości metadanych. Poniżej przedstawiono właściwości posortowane według typu.

  Aby uzyskać więcej informacji, zobacz [License metadata property types](https://msdn.microsoft.com/library/dn974062.aspx) (Typy właściwości metadanych licencji).

  - **IPC_MD_CONTENT_PATH**

    Ta właściwość umożliwia zidentyfikowanie śledzonego dokumentu. Jeśli nie można podać pełnej ścieżki, wystarczy podać nazwę pliku.

  - **IPC_MD_CONTENT_NAME**

    Ta właściwość umożliwia zidentyfikowanie nazwy śledzonego dokumentu.

  - **IPC_MD_NOTIFICATION_TYPE**

    Ta właściwość umożliwia określenie, kiedy powiadomienie zostanie wysłane. Aby uzyskać więcej informacji, zobacz Typ powiadomienia.

  - **IPC_MD_NOTIFICATION_PREFERENCE**

    Ta właściwość umożliwia określenie typu powiadomienia. Aby uzyskać więcej informacji, zobacz Preferencje powiadamiania.

  - **IPC_MD_DATE_MODIFIED**

    Zalecamy ustawienie tej daty za każdym razem, gdy użytkownik kliknie pozycję Zapisz.

  - **IPC_MD_DATE_CREATED**

    Ta właściwość umożliwia ustawienie daty utworzenia pliku.

- [IpcSerializeLicenseWithMetadata](https://msdn.microsoft.com/library/dn974058.aspx)

Dodaj metadane do pliku lub strumienia za pomocą odpowiedniego z poniższych interfejsów API.

- [IpcfEncryptFileWithMetadata](https://msdn.microsoft.com/library/dn974052.aspx)
- [IpcfEncryptFileStreamWithMetadata](https://msdn.microsoft.com/library/dn974051.aspx)

Na koniec zarejestruj śledzony dokument w systemie śledzenia przy użyciu poniższego interfejsu API.

- [IpcRegisterLicense](https://msdn.microsoft.com/library/dn974057.aspx)


## <a name="2-register-the-document-with-the-rms-service"></a>2. Rejestrowanie dokumentu za pomocą usługi RMS

Oto fragment kodu będący przykładem ustawienia metadanych śledzenia dokumentu i wywołania w celu przeprowadzenia rejestracji w systemie śledzenia.

      C++
      HRESULT hr = S_OK;
      LPCWSTR wszOutputFile = NULL;
      wstring wszWorkingFile;
      IPC_LICENSE_METADATA md = {0};

      md.cbSize = sizeof(IPC_LICENSE_METADATA);
      md.dwNotificationType = IPCD_CT_NOTIFICATION_TYPE_ENABLED;
      md.dwNotificationPreference = IPCD_CT_NOTIFICATION_PREF_DIGEST;
      //file origination date, current time for this example
      md.ftDateCreated = GetCurrentTime();
      md.ftDateModified = GetCurrentTime();

      LOGSTATUS_EX(L"Encrypt file with official template...");

      hr =IpcfEncryptFileWithMetadata( wszWorkingFile.c_str(),
                               m_wszTestTemplateID.c_str(),
                               IPCF_EF_TEMPLATE_ID,
                               0,
                               NULL,
                               NULL,
                               &md,
                               &wszOutputFile);

     /* This will contain the serialized license */
     PIPC_BUFFER pSerializedLicense;

     /* the context to use for the call */
     PCIPC_PROMPT_CTX pContext;

     wstring wstrContentName(“MyDocument.txt”);
     bool sendLicenseRegistrationNotificationEmail = FALSE;

     hr = IpcRegisterLicense( pSerializedLicense,
                        0,
                        pContext,
                        wstrContentName.c_str(),
                        sendLicenseRegistrationNotificationEmail);

## <a name="add-a-track-usage-button-to-your-app"></a>Dodawanie przycisku **Śledź użycie** do aplikacji

Aby dodać element interfejsu użytkownika **Śledź użycie** do aplikacji, wystarczy użyć jednego z następujących formatów adresów URL:

- Używanie identyfikatora zawartości
  - Pobierz identyfikator zawartości przy użyciu elementu [IpcGetLicenseProperty](https://msdn.microsoft.com/library/hh535265.aspx) lub [IpcGetSerializedLicenseProperty](https://msdn.microsoft.com/library/hh995038.aspx), jeśli licencja jest zserializowana, i użyj właściwości licencji **IPC_LI_CONTENT_ID**. Aby uzyskać więcej informacji, zobacz [License property types](https://msdn.microsoft.com/library/hh535287.aspx) (Typy właściwości licencji).
  - W przypadku metadanych **ContentId** i **Issuer** użyj następującego formatu: `https://track.azurerms.com/#/{ContentId}/{Issuer}`

    Przykład — `https://track.azurerms.com/#/summary/05405df5-8ad6-4905-9f15-fc2ecbd8d0f7/janedoe@microsoft.com`

- Jeśli nie masz dostępu do tych metadanych (tj. sprawdzasz niechronioną wersję dokumentu), możesz użyć elementu **Content_Name** w następującym formacie: `https://track.azurerms.com/#/?q={ContentName}`

  Przykład — https://track.azurerms.com/#/?q=Secret!. txt

Klient musi otworzyć odpowiedni adres URL w przeglądarce. Uwierzytelnianie i przekierowanie zostanie przeprowadzone przez portal śledzenia dokumentów usługi RMS.

## <a name="related-topics"></a>Tematy pokrewne

* [Typy właściwości metadanych licencji](https://msdn.microsoft.com/library/dn974062.aspx)
* [Preferencje powiadamiania](https://msdn.microsoft.com/library/dn974063.aspx)
* [Typ powiadomienia](https://msdn.microsoft.com/library/dn974064.aspx)
* [IpcCreateLicenseMetadataHandle](https://msdn.microsoft.com/library/dn974050.aspx)
* [IpcSetLicenseMetadataProperty](https://msdn.microsoft.com/library/dn974059.aspx)
* [IpcSerializeLicenseWithMetadata](https://msdn.microsoft.com/library/dn974058.aspx)
* [IpcfEncryptFileWithMetadata](https://msdn.microsoft.com/library/dn974052.aspx)
* [IpcfEncryptFileStreamWithMetadata](https://msdn.microsoft.com/library/dn974051.aspx)
* [IpcRegisterLicense](https://msdn.microsoft.com/library/dn974057.aspx)

