---
# required metadata

title: Śledzenie zawartości | Azure RMS
description: Podstawowe wskazówki dotyczące implementowania śledzenia dokumentów
keywords:
author: bruceperlerms
manager: mbaldwin
ms.date: 04/28/2016
ms.topic: article
ms.prod: azure
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: F5089765-9D94-452B-85E0-00D22675D847
# optional metadata

#ROBOTS:
audience: developer
#ms.devlang:
ms.reviewer: shubhamp
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# Śledzenie zawartości

W tym temacie podano podstawowe wskazówki dotyczące implementowania śledzenia dokumentów z zawartością chronioną przy użyciu zestawu Rights Management Services SDK 2.1.

Śledzenie dokumentów jest funkcją systemu Rights Management. Dodając określone metadane podczas procesu włączania ochrony dokumentu, można zarejestrować dokument w portalu usługi śledzenia, który następnie zapewnia kilka opcji śledzenia.

Korzystając z poniższych interfejsów API, można dodać/zaktualizować licencję na zawartość przy użyciu metadanych śledzenia dokumentów.

-   [**IpcCreateLicenseMetadataHandle**](/rights-management/sdk/2.1/api/win/functions#msipc_ipccreatelicensemetadatahandle)
-   [**IpcSetLicenseMetadataProperty**](/rights-management/sdk/2.1/api/win/functions#msipc_ipcsetlicensemetadataproperty)

    Oczekujemy, że ustawisz wszystkie właściwości metadanych. Oto one, posortowane według typu.

    Aby uzyskać więcej informacji, zobacz [**Typy właściwości metadanych licencji**](/rights-management/sdk/2.1/api/win/license%20metadata%20property%20types#msipc_license_metadata_property_types).

    -   **IPC\_MD\_CONTENT\_PATH**

        Ta właściwość umożliwia zidentyfikowanie śledzonego dokumentu. Jeśli nie można podać pełnej ścieżki, wystarczy podać nazwę pliku.

    -   **IPC\_MD\_CONTENT\_NAME**

        Ta właściwość umożliwia zidentyfikowanie nazwy śledzonego dokumentu.

    -   **IPC\_MD\_NOTIFICATION\_TYPE**

        Ta właściwość umożliwia określenie, kiedy powiadomienie zostanie wysłane. Aby uzyskać więcej informacji, zobacz [**Typ powiadomienia**](/rights-management/sdk/2.1/api/win/notification%20type#msipc_notification_type).

    -   **IPC\_MD\_NOTIFICATION\_PREFERENCE**

        Ta właściwość umożliwia określenie typu powiadomienia. Aby uzyskać więcej informacji, zobacz [**Preferencje powiadamiania**](/rights-management/sdk/2.1/api/win/constants#msipc_notification_preference).

    -   **IPC\_MD\_DATE\_MODIFIED**

        Zalecamy ustawienie tej daty za każdym razem, gdy użytkownik kliknie pozycję **Zapisz**.

    -   **IPC\_MD\_DATE\_CREATED**

        Data utworzenia pliku.

-   [**IpcSerializeLicenseWithMetadata**](/rights-management/sdk/2.1/api/win/functions#msipc_ipcserializelicensemetadata)

Dodaj metadane do pliku lub strumienia za pomocą odpowiedniego z poniższych interfejsów API.

-   [**IpcfEncryptFileWithMetadata**](/rights-management/sdk/2.1/api/win/functions#msipc_ipcfencryptfilewithmetadata)
-   [**IpcfEncryptFileStreamWithMetadata**](/rights-management/sdk/2.1/api/win/functions#msipc_ipcfencryptfilestreamwithmetadata)

Na koniec zarejestruj śledzony dokument w systemie śledzenia przy użyciu poniższego interfejsu API.

-   [**IpcRegisterLicense**](/rights-management/sdk/2.1/api/win/functions#msipc_ipcregisterlicense)

Oto fragment kodu będący przykładem ustawienia metadanych śledzenia dokumentu i wywołania w celu zarejestrowania w systemie śledzenia.



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

    LOGSTATUS_EX(L&quot;Encrypt file with official template...&quot;);

    hr =IpcfEncryptFileWithMetadata(  wszWorkingFile.c_str(),
                                       m_wszTestTemplateID.c_str(),
                                       IPCF_EF_TEMPLATE_ID,
                                       0,
                                       NULL,
                                       NULL,
                                       &amp;md,
                                       &amp;wszOutputFile);

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


## Tematy pokrewne


* [**Typy właściwości metadanych licencji**](/rights-management/sdk/2.1/api/win/license%20metadata%20property%20types#msipc_license_metadata_property_types)
* [**Preferencje powiadamiania**](/rights-management/sdk/2.1/api/win/constants#msipc_notification_preference)
* [**Typ powiadomienia**](/rights-management/sdk/2.1/api/win/notification%20type#msipc_notification_type)
* [**IpcCreateLicenseMetadataHandle**](/rights-management/sdk/2.1/api/win/functions#msipc_ipccreatelicensemetadatahandle)
* [**IpcSetLicenseMetadataProperty**](/rights-management/sdk/2.1/api/win/functions#msipc_ipcsetlicensemetadataproperty)
* [**IpcSerializeLicenseWithMetadata**](/rights-management/sdk/2.1/api/win/functions#msipc_ipcserializelicensemetadata)
* [**IpcfEncryptFileWithMetadata**](/rights-management/sdk/2.1/api/win/functions#msipc_ipcfencryptfilewithmetadata)
* [**IpcfEncryptFileStreamWithMetadata**](/rights-management/sdk/2.1/api/win/functions#msipc_ipcfencryptfilestreamwithmetadata)
* [**IpcRegisterLicense**](/rights-management/sdk/2.1/api/win/functions#msipc_ipcregisterlicense)
 

 


<!--HONumber=May16_HO2-->


