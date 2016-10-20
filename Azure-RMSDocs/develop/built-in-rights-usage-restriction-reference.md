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
experimental: true
experiment_id: priyamo-TableVsFlatList-20160805
translationtype: Human Translation
ms.sourcegitcommit: b4abffcbe6e49ea25f3cf493a1e68fcd6ea25b26
ms.openlocfilehash: d8fb04fd80e9a84bd7784e48b77e3aa8b045bf2d


---

# Porady: korzystanie z praw wbudowanych

W temacie omówiono prawa wbudowane zapewniane w ramach zestawu Microsoft Rights Management SDK 4.2 oraz ograniczenia użycia, które aplikacja powinna wymuszać. Poniżej przedstawiono prawa wbudowane: prawa wspólne, prawa dotyczące dokumentów edytowalnych i prawa dotyczące wiadomości e-mail oraz ich opisy i wartości według systemu operacyjnego.

**Uwaga** — szczegółowe informacje dotyczące zestawu SDK dla systemu Linux zawiera plik źródłowy *rights.h*.

## Prawa wspólne ##

**Wszystkie** — kolekcja wszystkich praw wspólnych.
- Android: [CommonRights.All](/information-protection/sdk/4.2/api/android/commonrights#msipcthin2_commonrights_class_java_ALL)
- iOS i OS X: [MSCommonRights owner](/information-protection/sdk/4.2/api/iOS/mscommonrights#msipcthin2_mscommonrights_interface_objc___NSString__owner_)
- Sklep Windows i Windows Phone: [CommonRights.All</strong>](/information-protection/sdk/4.2/api/winrt/commonrights#msipcthin2_commonrights)
- Linux: [CommonRights::All](http://azuread.github.io/rms-sdk-for-cpp/classrmscore_1_1modernapi_1_1CommonRights.html)

** Właściciel** — prawo właściciela umożliwiające pełną kontrolę nad chronioną zawartością.
- Android: [<strong>CommonRights.Owner](/information-protection/sdk/4.2/api/android/commonrights#msipcthin2_commonrights_class_java_Owner)
- iOS i OS X: [MSCommonRights owner](/information-protection/sdk/4.2/api/iOS/mscommonrights#msipcthin2_mscommonrights_interface_objc___NSString__owner_)
- Sklep Windows i Windows Phone: [CommonRights.Owner](/information-protection/sdk/4.2/api/winrt/commonrights#msipcthin2_commonrights_owner)
- Linux: [CommonRights::Owner](http://azuread.github.io/rms-sdk-for-cpp/classrmscore_1_1modernapi_1_1CommonRights.html)

**Widok** — prawo do wyświetlania zawartości chronionej. Zwykle po udzieleniu tego prawa aplikacja umożliwia użytkownikowi otwieranie i wyświetlanie chronionej zawartości, jednak modyfikowanie, wyodrębnianie, przesyłanie dalej lub zapisywanie zawartości wymaga dodatkowych praw.

- Android: [CommonRights.View](/information-protection/sdk/4.2/api/android/commonrights#msipcthin2_commonrights_class_java_View)
- iOS i OS X: [MSCommonRights view](/information-protection/sdk/4.2/api/iOS/mscommonrights#msipcthin2_mscommonrights_interface_objc___NSString__owner_)
- Sklep Windows i Windows Phone: [CommonRights.View](/information-protection/sdk/4.2/api/android/commonrights#msipcthin2_commonrights_class_java_View)
- Linux: [CommonRights::View](http://azuread.github.io/rms-sdk-for-cpp/classrmscore_1_1modernapi_1_1CommonRights.html)</li>

 

## Prawa dotyczące dokumentów edytowalnych ##
**Wszystkie** — kolekcja zawierająca wszystkie prawa dotyczące dokumentów edytowalnych.
- Android:[EditableDocumentRights.All](/information-protection/sdk/4.2/api/android/editabledocumentrights#msipcthin2_editabledocumentrights_class_java_ALL)
- iOS i OS X: [MSEditableDocumentRights all](/information-protection/sdk/4.2/api/iOS/mseditabledocumentrights#msipcthin2_mseditabledocumentrights_interface_objc)
- Sklep Windows i Windows Phone: [EditableDocumentRights.All](/information-protection/sdk/4.2/api/winrt/editabledocumentrights#msipcthin2_editabledocumentrights_all)
- Linux: [EditableDocumentRights::All](http://azuread.github.io/rms-sdk-for-cpp/classrmscore_1_1modernapi_1_1EditableDocumentRights.html)

**Komentarz** — prawo do wprowadzania komentarzy w dokumencie.
- Android: [EditableDocumentRights.Comment](/information-protection/sdk/4.2/api/android/editabledocumentrights#msipcthin2_editabledocumentrights_class_java_Comment)
- iOS i OS X: [MSEditableDocumentRights comment](/information-protection/sdk/4.2/api/iOS/mseditabledocumentrights#msipcthin2_mseditabledocumentrights_interface_objc)
- Sklep Windows i Windows Phone: [EditableDocumentRights.Comment](/information-protection/sdk/4.2/api/winrt/editabledocumentrights#msipcthin2_editabledocumentrights__comment)
- Linux: [EditableDocumentRights::Comment](http://azuread.github.io/rms-sdk-for-cpp/classrmscore_1_1modernapi_1_1EditableDocumentRights.html)

**Edycja** — prawo do edytowania zawartości chronionej i zapisywania jej w tym samym formacie chronionym. Zwykle po udzieleniu tego prawa aplikacja umożliwia użytkownikowi zmianę zawartości chronionej, a następnie zapisanie jej w tym samym pliku.
- Android: [EditableDocumentRights.Edit](/information-protection/sdk/4.2/api/android/editabledocumentrights#msipcthin2_editabledocumentrights_class_java_Edit)
- iOS i OS X: [MSEditableDocumentRights edit](/information-protection/sdk/4.2/api/iOS/mseditabledocumentrights#msipcthin2_mseditabledocumentrights_interface_objc)
- Sklep Windows i Windows Phone: [EditableDocumentRights.Edit](/information-protection/sdk/4.2/api/winrt/editabledocumentrights#msipcthin2_editabledocumentrights_edit)
- Linux: [EditableDocumentRights::Edit](http://azuread.github.io/rms-sdk-for-cpp/classrmscore_1_1modernapi_1_1EditableDocumentRights.html)

**Eksport** — prawo do wyodrębniania zawartości z formatu chronionego i umieszczania jej w innym formacie chronionym usługami AD RMS. Zwykle po udzieleniu tego prawa aplikacja umożliwia użytkownikowi zapisywanie chronionej zawartości w innych formatach chronionych usługami AD RMS, na przykład przy użyciu funkcji *Zapisz jako* aplikacji.

- Android: [EditableDocumentRights.Export](/information-protection/sdk/4.2/api/android/editabledocumentrights#msipcthin2_editabledocumentrights_class_java_Export)
- iOS i OS X: [MSEditableDocumentRights exportable](/information-protection/sdk/4.2/api/iOS/mseditabledocumentrights#msipcthin2_mseditabledocumentrights_interface_objc)
- Sklep Windows i Windows Phone: [EditableDocumentRights.Export](/information-protection/sdk/4.2/api/winrt/editabledocumentrights#msipcthin2_editabledocumentrights_export)
- Linux: [EditableDocumentRights::Export](http://azuread.github.io/rms-sdk-for-cpp/classrmscore_1_1modernapi_1_1EditableDocumentRights.html)

**Wyodrębnianie** — prawo do wyodrębniania zawartości z formatu chronionego i umieszczania jej w formacie niechronionym. Zwykle po udzieleniu tego prawa aplikacja umożliwia użytkownikowi kopiowanie i wklejanie informacji z chronionej zawartości. Jeśli aplikacja korzysta z funkcji <em>Zapisz jako</em>, może również umożliwiać użytkownikowi zapisywanie zawartości chronionej w formatach niechronionych i innych formatach chronionych. To prawo ma taką samą wartość, jak prawo Extract w odniesieniu do wiadomości e-mail.

- Android: [EditableDocumentRights.Extract](/information-protection/sdk/4.2/api/android/editabledocumentrights#msipcthin2_editabledocumentrights_class_java_Extract)
- iOS i OS X: [MSEditableDocumentRights extract](/information-protection/sdk/4.2/api/iOS/mseditabledocumentrights#msipcthin2_mseditabledocumentrights_interface_objc)
- Sklep Windows i Windows Phone: [EditableDocumentRights.Extract](/information-protection/sdk/4.2/api/winrt/editabledocumentrights#msipcthin2_editabledocumentrights_extract)
- Linux: [EditableDocumentRights::Extract](http://azuread.github.io/rms-sdk-for-cpp/classrmscore_1_1modernapi_1_1EditableDocumentRights.html)

**Drukowanie** — prawo do drukowania zawartości chronionej. Zwykle po udzieleniu tego prawa aplikacja umożliwia użytkownikowi drukowanie chronionej zawartości. To prawo ma taką samą wartość, jak prawo Print w odniesieniu do wiadomości e-mail.

- Android: [EditableDocumentRights.Print](/information-protection/sdk/4.2/api/android/editabledocumentrights#msipcthin2_editabledocumentrights_class_java_Print)
- iOS i OS X: [MSEditableDocumentRights print](/information-protection/sdk/4.2/api/iOS/mseditabledocumentrights#msipcthin2_mseditabledocumentrights_interface_objc)
- Sklep Windows i Windows Phone: [EditableDocumentRights.Print](/information-protection/sdk/4.2/api/winrt/editabledocumentrights#msipcthin2_editabledocumentrights_print)
- Linux: [EditableDocumentRights::Print](http://azuread.github.io/rms-sdk-for-cpp/classrmscore_1_1modernapi_1_1EditableDocumentRights.html)

 

## Prawa dotyczące wiadomości e-mail ##

**Wszystkie** — kolekcja zawierająca wszystkie prawa dotyczące wiadomości e-mail.
- Android: [EmailRights.All](/information-protection/sdk/4.2/api/android/emailrights#msipcthin2_emailrights_class_java_ALL)
- iOS i OS X: [MSEmailRights all](/information-protection/sdk/4.2/api/iOS/msemailrights#msipcthin2_msemailrights_interface_objc)
- Sklep Windows i Windows Phone: [EmailRights.All](/information-protection/sdk/4.2/api/winrt/emailrights#msipcthin2_emailrights_all)
- Linux: [EmailRights::All](http://azuread.github.io/rms-sdk-for-cpp/classrmscore_1_1modernapi_1_1EmailRights.html)

**Wyodrębnianie** — prawo do wyodrębniania zawartości z formatu chronionego i umieszczania jej w formacie niechronionym. Zwykle po udzieleniu tego prawa aplikacja umożliwia użytkownikowi kopiowanie i wklejanie informacji z chronionej wiadomości. Jeśli aplikacja korzysta z funkcji <em>Zapisz jako</em>, może również umożliwiać odbiorcy zapisywanie zawartości chronionej w formatach niechronionych i innych formatach chronionych. To prawo ma taką samą wartość, jak prawo Extract w odniesieniu do dokumentów edytowalnych.

- Android: [EmailRights.Extract](/information-protection/sdk/4.2/api/android/emailrights#msipcthin2_emailrights_class_java_Extract)
- iOS i OS X: [MSEmailRights extract](/information-protection/sdk/4.2/api/iOS/msemailrights#msipcthin2_msemailrights_interface_objc)
- Sklep Windows i Windows Phone: [EmailRights.Extract</strong>](/information-protection/sdk/4.2/api/winrt/emailrights#msipcthin2_emailrights_extract)
- Linux: [EmailRights::Extract](http://azuread.github.io/rms-sdk-for-cpp/classrmscore_1_1modernapi_1_1EmailRights.html)

**Przesyłanie dalej** — prawo do przesyłania dalej wiadomości chronionych. Zwykle po udzieleniu tego prawa aplikacja umożliwia odbiorcy chronionej wiadomości e-mail przesłanie jej dalej.
- Android: [<strong>EmailRights.Forward</strong>](/information-protection/sdk/4.2/api/android/emailrights#msipcthin2_emailrights_class_java_Forward)
- iOS i OS X: [MSEmailRights forward](/information-protection/sdk/4.2/api/iOS/msemailrights#msipcthin2_msemailrights_interface_objc)
- Sklep Windows i Windows Phone: [EmailRights.Forward](/information-protection/sdk/4.2/api/winrt/emailrights#msipcthin2_emailrights_forward)
- Linux: [EmailRights::Forward](http://azuread.github.io/rms-sdk-for-cpp/classrmscore_1_1modernapi_1_1EmailRights.html)

**Drukowanie** — prawo do drukowania zawartości chronionej. Zwykle po udzieleniu tego prawa aplikacja umożliwia odbiorcy wydrukowanie chronionej wiadomości e-mail. To prawo ma taką samą wartość, jak prawo Print w odniesieniu do dokumentów edytowalnych.

- Android: [EmailRights.Print](/information-protection/sdk/4.2/api/android/emailrights#msipcthin2_emailrights_class_java_Print)
- iOS i OS X: [MSEmailRights print](/information-protection/sdk/4.2/api/iOS/msemailrights#msipcthin2_msemailrights_interface_objc)
- Sklep Windows i Windows Phone: [EmailRights.Print](/information-protection/sdk/4.2/api/winrt/emailrights#msipcthin2_emailrights_print)
- Linux: [EmailRights::Print](http://azuread.github.io/rms-sdk-for-cpp/classrmscore_1_1modernapi_1_1EmailRights.html)

**Odpowiadanie** — zwykle po udzieleniu tego prawa aplikacja umożliwia odbiorcy wiadomości e-mail udzielenie odpowiedzi na wiadomość chronioną i dołączenie kopii oryginalnej wiadomości.

- Android: [EmailRights.Reply](/information-protection/sdk/4.2/api/android/emailrights#msipcthin2_emailrights_class_java_Reply)
- iOS i OS X: [MSEmailRights reply](/information-protection/sdk/4.2/api/iOS/msemailrights#msipcthin2_msemailrights_interface_objc)
- Sklep Windows i Windows Phone: [EmailRights.Reply](/information-protection/sdk/4.2/api/winrt/emailrights#msipcthin2_emailrights_reply)
- Linux: [EmailRights::Reply](http://azuread.github.io/rms-sdk-for-cpp/classrmscore_1_1modernapi_1_1EmailRights.html)

**OdpowiadanieWszystkim** — zwykle po udzieleniu tego prawa aplikacja umożliwia odbiorcy wiadomości e-mail udzielenie odpowiedzi wszystkim odbiorcom wiadomości chronionej i dołączenie kopii oryginalnej wiadomości.

- Android: [EmailRights.ReplyAll</strong>](/information-protection/sdk/4.2/api/android/emailrights#msipcthin2_emailrights_class_java_ReplyAll)
- iOS i OS X: [MSEmailRights replyAll](/information-protection/sdk/4.2/api/iOS/msemailrights#msipcthin2_msemailrights_interface_objc)
- Sklep Windows i Windows Phone: [EmailRights.ReplyAll](/information-protection/sdk/4.2/api/winrt/emailrights#msipcthin2_emailrights_replyall)
- Linux: [EmailRights::ReplyAll](http://azuread.github.io/rms-sdk-for-cpp/classrmscore_1_1modernapi_1_1EmailRights.html)

 

 

 



<!--HONumber=Oct16_HO1-->


