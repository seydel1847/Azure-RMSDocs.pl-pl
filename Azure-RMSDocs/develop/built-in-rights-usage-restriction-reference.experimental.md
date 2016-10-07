---
title: Porady&#58; korzystanie z praw wbudowanych | Azure RMS
description: "W temacie omówiono prawa wbudowane zapewniane w ramach zestawu RMS SDK 4.2 oraz ograniczenia użycia, które aplikacja powinna wymuszać."
keywords: 
author: bruceperlerms
manager: mbaldwin
ms.date: 09/25/2016
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: 9142dd29-f1f4-4c2f-82ac-534f14b8bba1
audience: developer
ms.reviewer: shubhamp
ms.suite: ems
experiment_id: priyamo-TableVsFlatList-20160805
translationtype: Human Translation
ms.sourcegitcommit: b4abffcbe6e49ea25f3cf493a1e68fcd6ea25b26
ms.openlocfilehash: a8a513260dde6047c95c52c48217b7b4d8466cbc


---

# Porady: korzystanie z praw wbudowanych

W temacie omówiono prawa wbudowane zapewniane w ramach zestawu Microsoft Rights Management SDK 4.2 oraz ograniczenia użycia, które aplikacja powinna wymuszać. W poniższej tabeli przedstawiono prawa wbudowane: prawa wspólne, prawa dotyczące dokumentów edytowalnych i prawa dotyczące wiadomości e-mail oraz ich opisy i wartości według systemu operacyjnego.

**Uwaga** — szczegółowe informacje dotyczące zestawu SDK dla systemu Linux zawiera plik źródłowy *rights.h*.

## Prawa wspólne ##

| Prawe | Opis | Android | iOS i OS X | Windows Phone i Sklep Windows | Linux |
|-------|-------------|---------|-------------|---------------------------------|-------|
| **Wszystkie** | Kolekcja wszystkich praw wspólnych. | [CommonRights.All](/information-protection/sdk/4.2/api/android/commonrights#msipcthin2_commonrights_class_java_ALL) | [MSCommonRights owner](/information-protection/sdk/4.2/api/iOS/mscommonrights#msipcthin2_mscommonrights_interface_objc___NSString__owner_)| [CommonRights.All</strong>](/information-protection/sdk/4.2/api/winrt/commonrights#msipcthin2_commonrights)| [CommonRights::All](http://azuread.github.io/rms-sdk-for-cpp/classrmscore_1_1modernapi_1_1CommonRights.html)|
| **Właściciel**| Przyznaje pełną kontrolę nad chronioną zawartością. |  [CommonRights.Owner](/information-protection/sdk/4.2/api/android/commonrights#msipcthin2_commonrights_class_java_Owner) |[MSCommonRights owner](/information-protection/sdk/4.2/api/iOS/mscommonrights#msipcthin2_mscommonrights_interface_objc___NSString__owner_) |[CommonRights.Owner](/information-protection/sdk/4.2/api/winrt/commonrights#msipcthin2_commonrights_owner) |  [CommonRights::Owner](http://azuread.github.io/rms-sdk-for-cpp/classrmscore_1_1modernapi_1_1CommonRights.html)|
| **Wyświetl** | Prawo do wyświetlania zawartości chronionej. Zwykle po udzieleniu tego prawa aplikacja umożliwia użytkownikowi otwieranie i wyświetlanie chronionej zawartości, jednak modyfikowanie, wyodrębnianie, przesyłanie dalej lub zapisywanie zawartości wymaga dodatkowych praw. |  [CommonRights.View](/information-protection/sdk/4.2/api/android/commonrights#msipcthin2_commonrights_class_java_View) | [MSCommonRights view](/information-protection/sdk/4.2/api/iOS/mscommonrights#msipcthin2_mscommonrights_interface_objc___NSString__owner_)|[CommonRights.View](/information-protection/sdk/4.2/api/android/commonrights#msipcthin2_commonrights_class_java_View) | [CommonRights::View](http://azuread.github.io/rms-sdk-for-cpp/classrmscore_1_1modernapi_1_1CommonRights.html) |


## Prawa dotyczące dokumentów edytowalnych ##

| Prawe | Opis | Android | iOS i OS X | Windows Phone i Sklep Windows | Linux |
|-------|-------------|---------|-------------|---------------------------------|-------|
| **Wszystkie** | Kolekcja zawierająca wszystkie prawa dotyczące dokumentów edytowalnych.| [EditableDocumentRights.All](/information-protection/sdk/4.2/api/android/editabledocumentrights#msipcthin2_editabledocumentrights_class_java_ALL) | [MSEditableDocumentRights all](/information-protection/sdk/4.2/api/iOS/mseditabledocumentrights#msipcthin2_mseditabledocumentrights_interface_objc) | [EditableDocumentRights.All](/information-protection/sdk/4.2/api/winrt/editabledocumentrights#msipcthin2_editabledocumentrights_all) |[EditableDocumentRights::All](http://azuread.github.io/rms-sdk-for-cpp/classrmscore_1_1modernapi_1_1EditableDocumentRights.html)|
| **Komentarz** | Prawo do wprowadzania komentarzy w dokumencie. | [EditableDocumentRights.Comment](/information-protection/sdk/4.2/api/android/editabledocumentrights#msipcthin2_editabledocumentrights_class_java_Comment)|[MSEditableDocumentRights comment](/information-protection/sdk/4.2/api/iOS/mseditabledocumentrights#msipcthin2_mseditabledocumentrights_interface_objc) |[EditableDocumentRights.Comment](/information-protection/sdk/4.2/api/winrt/editabledocumentrights#msipcthin2_editabledocumentrights__comment)| [EditableDocumentRights::Comment](http://azuread.github.io/rms-sdk-for-cpp/classrmscore_1_1modernapi_1_1EditableDocumentRights.html)|
| **Edytowanie** | Prawo do edytowania zawartości chronionej i zapisywania jej w tym samym formacie chronionym. Zwykle po udzieleniu tego prawa aplikacja umożliwia użytkownikowi zmianę zawartości chronionej, a następnie zapisanie jej w tym samym pliku. | [EditableDocumentRights.Edit](/information-protection/sdk/4.2/api/android/editabledocumentrights#msipcthin2_editabledocumentrights_class_java_Edit) | [MSEditableDocumentRights edit](/information-protection/sdk/4.2/api/iOS/mseditabledocumentrights#msipcthin2_mseditabledocumentrights_interface_objc) | [EditableDocumentRights.Edit](/information-protection/sdk/4.2/api/winrt/editabledocumentrights#msipcthin2_editabledocumentrights_edit) | [EditableDocumentRights::Edit](http://azuread.github.io/rms-sdk-for-cpp/classrmscore_1_1modernapi_1_1EditableDocumentRights.html) |
| **Eksportowanie** | Prawo do wyodrębniania zawartości z formatu chronionego i umieszczanie jej w innym formacie chronionym przez usługi AD RMS. Zwykle po udzieleniu tego prawa aplikacja umożliwia użytkownikowi zapisywanie chronionej zawartości w innych formatach chronionych usługami AD RMS, na przykład przy użyciu funkcji *Zapisz jako* aplikacji. | [EditableDocumentRights.Export](/information-protection/sdk/4.2/api/android/editabledocumentrights#msipcthin2_editabledocumentrights_class_java_Export) | [MSEditableDocumentRights exportable](/information-protection/sdk/4.2/api/iOS/mseditabledocumentrights#msipcthin2_mseditabledocumentrights_interface_objc) |[EditableDocumentRights.Export](/information-protection/sdk/4.2/api/winrt/editabledocumentrights#msipcthin2_editabledocumentrights_export) | [EditableDocumentRights::Export](http://azuread.github.io/rms-sdk-for-cpp/classrmscore_1_1modernapi_1_1EditableDocumentRights.html)|
| **Wyodrębnianie** | Prawo do wyodrębniania zawartości z formatu chronionego i umieszczanie jej w formacie niechronionym. Zwykle po udzieleniu tego prawa aplikacja umożliwia użytkownikowi kopiowanie i wklejanie informacji z chronionej zawartości. Jeśli aplikacja korzysta z funkcji <em>Zapisz jako</em>, może również umożliwiać użytkownikowi zapisywanie zawartości chronionej w formatach niechronionych i innych formatach chronionych. To prawo ma taką samą wartość, jak prawo Extract w odniesieniu do wiadomości e-mail. |  [EditableDocumentRights.Extract](/information-protection/sdk/4.2/api/android/editabledocumentrights#msipcthin2_editabledocumentrights_class_java_Extract) |[MSEditableDocumentRights extract](/information-protection/sdk/4.2/api/iOS/mseditabledocumentrights#msipcthin2_mseditabledocumentrights_interface_objc) | [EditableDocumentRights.Extract](/information-protection/sdk/4.2/api/winrt/editabledocumentrights#msipcthin2_editabledocumentrights_extract) |  [EditableDocumentRights::Extract](http://azuread.github.io/rms-sdk-for-cpp/classrmscore_1_1modernapi_1_1EditableDocumentRights.html)|
| **Drukowanie** | Prawo do drukowania zawartości chronionej. Zwykle po udzieleniu tego prawa aplikacja umożliwia użytkownikowi drukowanie chronionej zawartości. To prawo ma taką samą wartość, jak prawo Print w odniesieniu do wiadomości e-mail. | [EditableDocumentRights.Print](/information-protection/sdk/4.2/api/android/editabledocumentrights#msipcthin2_editabledocumentrights_class_java_Print) |  [MSEditableDocumentRights print](/information-protection/sdk/4.2/api/iOS/mseditabledocumentrights#msipcthin2_mseditabledocumentrights_interface_objc)| [EditableDocumentRights.Print](/information-protection/sdk/4.2/api/winrt/editabledocumentrights#msipcthin2_editabledocumentrights_print) | [EditableDocumentRights::Print](http://azuread.github.io/rms-sdk-for-cpp/classrmscore_1_1modernapi_1_1EditableDocumentRights.html)|
 

## Prawa dotyczące wiadomości e-mail ##

| Prawe | Opis | Android | iOS i OS X | Windows Phone i Sklep Windows | Linux |
|-------|-------------|---------|-------------|---------------------------------|-------|
| **Wszystkie** |Kolekcja zawierająca wszystkie prawa dotyczące wiadomości e-mail. |  [EmailRights.All](/information-protection/sdk/4.2/api/android/emailrights#msipcthin2_emailrights_class_java_ALL) | [MSEmailRights all](/information-protection/sdk/4.2/api/iOS/msemailrights#msipcthin2_msemailrights_interface_objc) | [EmailRights.All](/information-protection/sdk/4.2/api/winrt/emailrights#msipcthin2_emailrights_all)|[EmailRights::All](http://azuread.github.io/rms-sdk-for-cpp/classrmscore_1_1modernapi_1_1EmailRights.html)|
| **Wyodrębnianie** | Prawo do wyodrębniania zawartości z formatu chronionego i umieszczanie jej w formacie niechronionym. Zwykle po udzieleniu tego prawa aplikacja umożliwia użytkownikowi kopiowanie i wklejanie informacji z chronionej wiadomości. Jeśli aplikacja korzysta z funkcji <em>Zapisz jako</em>, może również umożliwiać odbiorcy zapisywanie zawartości chronionej w formatach niechronionych i innych formatach chronionych. To prawo ma taką samą wartość, jak prawo Extract w odniesieniu do dokumentów edytowalnych. | [EmailRights.Extract](/information-protection/sdk/4.2/api/android/emailrights#msipcthin2_emailrights_class_java_Extract) | [MSEmailRights extract](/information-protection/sdk/4.2/api/iOS/msemailrights#msipcthin2_msemailrights_interface_objc) | [EmailRights.Extract</strong>](/information-protection/sdk/4.2/api/winrt/emailrights#msipcthin2_emailrights_extract) | [EmailRights::Extract](http://azuread.github.io/rms-sdk-for-cpp/classrmscore_1_1modernapi_1_1EmailRights.html) |
|**Prześlij dalej**| Prawo do przesyłania dalej wiadomości chronionych. Zwykle po udzieleniu tego prawa aplikacja umożliwia odbiorcy chronionej wiadomości e-mail przesłanie jej dalej.| [<strong>EmailRights.Forward</strong>](/information-protection/sdk/4.2/api/android/emailrights#msipcthin2_emailrights_class_java_Forward) | [MSEmailRights forward](/information-protection/sdk/4.2/api/iOS/msemailrights#msipcthin2_msemailrights_interface_objc) | [EmailRights.Forward](/information-protection/sdk/4.2/api/winrt/emailrights#msipcthin2_emailrights_forward) | [EmailRights::Forward](http://azuread.github.io/rms-sdk-for-cpp/classrmscore_1_1modernapi_1_1EmailRights.html) |
|**Drukowanie** | Prawo do drukowania zawartości chronionej. Zwykle po udzieleniu tego prawa aplikacja umożliwia odbiorcy wydrukowanie chronionej wiadomości e-mail. To prawo ma taką samą wartość, jak prawo Print w odniesieniu do dokumentów edytowalnych. | [EmailRights.Print](/information-protection/sdk/4.2/api/android/emailrights#msipcthin2_emailrights_class_java_Print) |[MSEmailRights print](/information-protection/sdk/4.2/api/iOS/msemailrights#msipcthin2_msemailrights_interface_objc) | [EmailRights.Print](/information-protection/sdk/4.2/api/winrt/emailrights#msipcthin2_emailrights_print) | [EmailRights::Print](http://azuread.github.io/rms-sdk-for-cpp/classrmscore_1_1modernapi_1_1EmailRights.html)|
| **Odpowiedz** | Zwykle po udzieleniu tego prawa aplikacja umożliwia odbiorcy wiadomości e-mail udzielenie odpowiedzi na wiadomość chronioną i dołączenie kopii oryginalnej wiadomości. | [EmailRights.Reply](/information-protection/sdk/4.2/api/android/emailrights#msipcthin2_emailrights_class_java_Reply) | [MSEmailRights reply](/information-protection/sdk/4.2/api/iOS/msemailrights#msipcthin2_msemailrights_interface_objc) | [EmailRights.Reply](/information-protection/sdk/4.2/api/winrt/emailrights#msipcthin2_emailrights_reply) | [EmailRights::Reply](http://azuread.github.io/rms-sdk-for-cpp/classrmscore_1_1modernapi_1_1EmailRights.html)|
| **Odpowiadanie wszystkim** | Zwykle po udzieleniu tego prawa aplikacja umożliwia odbiorcy wiadomości e-mail udzielenie odpowiedzi wszystkim odbiorcom wiadomości chronionej i dołączenie kopii oryginalnej wiadomości. | [EmailRights.ReplyAll</strong>](/information-protection/sdk/4.2/api/android/emailrights#msipcthin2_emailrights_class_java_ReplyAll) | [MSEmailRights replyAll](/information-protection/sdk/4.2/api/iOS/msemailrights#msipcthin2_msemailrights_interface_objc) | [EmailRights.ReplyAll](/information-protection/sdk/4.2/api/winrt/emailrights#msipcthin2_emailrights_replyall) | [EmailRights::ReplyAll](http://azuread.github.io/rms-sdk-for-cpp/classrmscore_1_1modernapi_1_1EmailRights.html)|



<!--HONumber=Oct16_HO1-->


