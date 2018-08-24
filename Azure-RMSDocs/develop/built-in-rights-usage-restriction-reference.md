---
title: 'Porady& #58; korzystanie z praw wbudowanych | Azure RMS'
description: W temacie omówiono prawa wbudowane zapewniane w ramach zestawu RMS SDK 4.2 oraz ograniczenia użycia, które aplikacja powinna wymuszać.
keywords: ''
author: lleonard-msft
ms.author: alleonar
manager: mbaldwin
ms.date: 02/23/2017
ms.topic: article
ms.service: information-protection
ms.assetid: 9142dd29-f1f4-4c2f-82ac-534f14b8bba1
audience: developer
ms.reviewer: shubhamp
ms.suite: ems
ms.openlocfilehash: dad70106d7a170dc91c2f0160d2f9f6a978862af
ms.sourcegitcommit: 7ba9850e5bb07b14741bb90ebbe98f1ebe057b10
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/23/2018
ms.locfileid: "42808262"
---
# <a name="how-to-use-built-in-rights"></a>Porady: korzystanie z praw wbudowanych

W temacie omówiono prawa wbudowane zapewniane w ramach zestawu Microsoft Rights Management SDK 4.2 oraz ograniczenia użycia, które aplikacja powinna wymuszać. Poniżej przedstawiono prawa wbudowane: prawa wspólne, prawa dotyczące dokumentów edytowalnych i prawa dotyczące wiadomości e-mail oraz ich opisy i wartości według systemu operacyjnego.

**Uwaga** — szczegółowe informacje dotyczące zestawu SDK dla systemu Linux zawiera plik źródłowy *rights.h*.

## <a name="common-rights"></a>Prawa wspólne

**Wszystkie** — kolekcja wszystkich praw wspólnych.
- Android: [CommonRights.All](https://msdn.microsoft.com/library/dn758258.aspx)
- iOS i OS X: [MSCommonRights](https://msdn.microsoft.com/library/dn758314.aspx) — właściciel i widok użytkownika, aby zaimplementować **Wszystko**
- Sklep Windows i Windows Phone: [CommonRights.All</strong>](https://msdn.microsoft.com/library/microsoft.rightsmanagement.commonrights.all.aspx)
- Linux: [CommonRights::All](http://azuread.github.io/rms-sdk-for-cpp/classrmscore_1_1modernapi_1_1CommonRights.html)

**Właściciel** — prawo właściciela umożliwiające pełną kontrolę nad chronioną zawartością.
- Android: [<strong>CommonRights.Owner](https://msdn.microsoft.com/library/dn758258.aspx)
- iOS i OS X: [MSCommonRights owner](https://msdn.microsoft.com/library/dn758314.aspx)
- Sklep Windows i Windows Phone: [CommonRights.Owner](https://msdn.microsoft.com/library/microsoft.rightsmanagement.commonrights.owner.aspx)
- Linux: [CommonRights::Owner](http://azuread.github.io/rms-sdk-for-cpp/classrmscore_1_1modernapi_1_1CommonRights.html)

**Widok** — prawo do wyświetlania zawartości chronionej. Zwykle po udzieleniu tego prawa aplikacja umożliwia użytkownikowi otwieranie i wyświetlanie chronionej zawartości, jednak modyfikowanie, wyodrębnianie, przesyłanie dalej lub zapisywanie zawartości wymaga dodatkowych praw.

- Android: [CommonRights.View](https://msdn.microsoft.com/library/dn758258.aspx)
- iOS i OS X: [MSCommonRights view](https://msdn.microsoft.com/library/dn758314.aspx)
- Sklep Windows i Windows Phone: [CommonRights.View](https://msdn.microsoft.com/library/microsoft.rightsmanagement.commonrights.view.aspx)
- Linux: [CommonRights::View](http://azuread.github.io/rms-sdk-for-cpp/classrmscore_1_1modernapi_1_1CommonRights.html)</li>

 

## <a name="editable-document-rights"></a>Prawa dotyczące dokumentów edytowalnych
**Wszystkie** — kolekcja zawierająca wszystkie prawa dotyczące dokumentów edytowalnych.
- Android: [EditableDocumentRights.All](https://msdn.microsoft.com/library/dn758284.aspx)
- iOS i OS X: [MSEditableDocumentRights all](https://msdn.microsoft.com/library/dn758318.aspx)
- Sklep Windows i Windows Phone: [EditableDocumentRights.All](https://msdn.microsoft.com/library/microsoft.rightsmanagement.editabledocumentrights.all.aspx)
- Linux: [EditableDocumentRights::All](http://azuread.github.io/rms-sdk-for-cpp/classrmscore_1_1modernapi_1_1EditableDocumentRights.html)

**Komentarz** — prawo do wprowadzania komentarzy w dokumencie.
- Android: [EditableDocumentRights.Comment](https://msdn.microsoft.com/library/dn758284.aspx)
- iOS i OS X: [MSEditableDocumentRights comment](https://msdn.microsoft.com/library/dn758318.aspx)
- Sklep Windows i Windows Phone: [EditableDocumentRights.Comment](https://msdn.microsoft.com/library/microsoft.rightsmanagement.editabledocumentrights.comment.aspx)
- Linux: [EditableDocumentRights::Comment](http://azuread.github.io/rms-sdk-for-cpp/classrmscore_1_1modernapi_1_1EditableDocumentRights.html)

**Edycja** — prawo do edytowania zawartości chronionej i zapisywania jej w tym samym formacie chronionym. Zwykle po udzieleniu tego prawa aplikacja umożliwia użytkownikowi zmianę zawartości chronionej, a następnie zapisanie jej w tym samym pliku.
- Android: [EditableDocumentRights.Edit](https://msdn.microsoft.com/library/dn758284.aspx)
- iOS i OS X: [MSEditableDocumentRights edit](https://msdn.microsoft.com/library/dn758318.aspx)
- Sklep Windows i Windows Phone: [EditableDocumentRights.Edit](https://msdn.microsoft.com/library/microsoft.rightsmanagement.editabledocumentrights.edit.aspx)
- Linux: [EditableDocumentRights::Edit](http://azuread.github.io/rms-sdk-for-cpp/classrmscore_1_1modernapi_1_1EditableDocumentRights.html)

**Eksport** — prawo do wyodrębniania zawartości z formatu chronionego i umieszczania jej w innym formacie chronionym usługami AD RMS. Zwykle po udzieleniu tego prawa aplikacja umożliwia użytkownikowi zapisywanie chronionej zawartości w innych formatach chronionych usługami AD RMS, na przykład przy użyciu funkcji *Zapisz jako* aplikacji.

- Android: [EditableDocumentRights.Export](https://msdn.microsoft.com/library/dn758284.aspx)
- iOS i OS X: [MSEditableDocumentRights exportable](https://msdn.microsoft.com/library/dn758318.aspx)
- Sklep Windows i Windows Phone: [EditableDocumentRights.Export](https://msdn.microsoft.com/library/microsoft.rightsmanagement.editabledocumentrights.export.aspx)
- Linux: [EditableDocumentRights::Export](http://azuread.github.io/rms-sdk-for-cpp/classrmscore_1_1modernapi_1_1EditableDocumentRights.html)

**Wyodrębnianie** — prawo do wyodrębniania zawartości z formatu chronionego i umieszczania jej w formacie niechronionym. Zwykle po udzieleniu tego prawa aplikacja umożliwia użytkownikowi kopiowanie i wklejanie informacji z chronionej zawartości. Jeśli aplikacja korzysta z funkcji <em>Zapisz jako</em>, może również umożliwiać użytkownikowi zapisywanie zawartości chronionej w formatach niechronionych i innych formatach chronionych. To prawo ma taką samą wartość, jak prawo Extract w odniesieniu do wiadomości e-mail.

- Android: [EditableDocumentRights.Extract](https://msdn.microsoft.com/library/dn758284.aspx)
- iOS i OS X: [MSEditableDocumentRights extract](https://msdn.microsoft.com/library/dn758318.aspx)
- Sklep Windows i Windows Phone: [EditableDocumentRights.Extract](https://msdn.microsoft.com/library/microsoft.rightsmanagement.editabledocumentrights.extract.aspx)
- Linux: [EditableDocumentRights::Extract](http://azuread.github.io/rms-sdk-for-cpp/classrmscore_1_1modernapi_1_1EditableDocumentRights.html)

**Drukowanie** — prawo do drukowania zawartości chronionej. Zwykle po udzieleniu tego prawa aplikacja umożliwia użytkownikowi drukowanie chronionej zawartości. To prawo ma taką samą wartość, jak prawo Print w odniesieniu do wiadomości e-mail.

- Android: [EditableDocumentRights.Print](https://msdn.microsoft.com/library/dn758284.aspx)
- iOS i OS X: [MSEditableDocumentRights print](https://msdn.microsoft.com/library/dn758318.aspx)
- Sklep Windows i Windows Phone: [EditableDocumentRights.Print](https://msdn.microsoft.com/library/microsoft.rightsmanagement.editabledocumentrights.print.aspx)
- Linux: [EditableDocumentRights::Print](http://azuread.github.io/rms-sdk-for-cpp/classrmscore_1_1modernapi_1_1EditableDocumentRights.html)

 

## <a name="email-rights"></a>Prawa dotyczące wiadomości e-mail

**Wszystkie** — kolekcja zawierająca wszystkie prawa dotyczące wiadomości e-mail.
- Android: [EmailRights.All](https://msdn.microsoft.com/library/dn758285.aspx)
- iOS i OS X: [MSEmailRights all](https://msdn.microsoft.com/library/dn758319.aspx)
- Sklep Windows i Windows Phone: [EmailRights.All](https://msdn.microsoft.com/library/microsoft.rightsmanagement.emailrights.all.aspx)
- Linux: [EmailRights::All](http://azuread.github.io/rms-sdk-for-cpp/classrmscore_1_1modernapi_1_1EmailRights.html)

**Wyodrębnianie** — prawo do wyodrębniania zawartości z formatu chronionego i umieszczania jej w formacie niechronionym. Zwykle po udzieleniu tego prawa aplikacja umożliwia użytkownikowi kopiowanie i wklejanie informacji z chronionej wiadomości. Jeśli aplikacja korzysta z funkcji <em>Zapisz jako</em>, może również umożliwiać odbiorcy zapisywanie zawartości chronionej w formatach niechronionych i innych formatach chronionych. To prawo ma taką samą wartość, jak prawo Extract w odniesieniu do dokumentów edytowalnych.

- Android: [EmailRights.Extract](https://msdn.microsoft.com/library/dn758285.aspx)
- iOS i OS X: [MSEmailRights extract](https://msdn.microsoft.com/library/dn758319.aspx)
- Sklep Windows i Windows Phone: [EmailRights.Extract</strong>](https://msdn.microsoft.com/library/microsoft.rightsmanagement.emailrights.extract.aspx)
- Linux: [EmailRights::Extract](http://azuread.github.io/rms-sdk-for-cpp/classrmscore_1_1modernapi_1_1EmailRights.html)

**Przesyłanie dalej** — prawo do przesyłania dalej wiadomości chronionych. Zwykle po udzieleniu tego prawa aplikacja umożliwia odbiorcy chronionej wiadomości e-mail przesłanie jej dalej.
- Android: [<strong>EmailRights.Forward</strong>](https://msdn.microsoft.com/library/dn758285.aspx)
- iOS i OS X: [MSEmailRights forward](https://msdn.microsoft.com/library/dn758319.aspx)
- Sklep Windows i Windows Phone: [EmailRights.Forward](https://msdn.microsoft.com/library/microsoft.rightsmanagement.emailrights.forward.aspx)
- Linux: [EmailRights::Forward](http://azuread.github.io/rms-sdk-for-cpp/classrmscore_1_1modernapi_1_1EmailRights.html)

**Drukowanie** — prawo do drukowania zawartości chronionej. Zwykle po udzieleniu tego prawa aplikacja umożliwia odbiorcy wydrukowanie chronionej wiadomości e-mail. To prawo ma taką samą wartość, jak prawo Print w odniesieniu do dokumentów edytowalnych.

- Android: [EmailRights.Print](https://msdn.microsoft.com/library/dn758285.aspx)
- iOS i OS X: [MSEmailRights print](https://msdn.microsoft.com/library/dn758319.aspx)
- Sklep Windows i Windows Phone: [EmailRights.Print](https://msdn.microsoft.com/library/microsoft.rightsmanagement.emailrights.print.aspx)
- Linux: [EmailRights::Print](http://azuread.github.io/rms-sdk-for-cpp/classrmscore_1_1modernapi_1_1EmailRights.html)

**Odpowiadanie** — zwykle po udzieleniu tego prawa aplikacja umożliwia odbiorcy wiadomości e-mail udzielenie odpowiedzi na wiadomość chronioną i dołączenie kopii oryginalnej wiadomości.

- Android: [EmailRights.Reply](https://msdn.microsoft.com/library/dn758285.aspx)
- iOS i OS X: [MSEmailRights reply](https://msdn.microsoft.com/library/dn758319.aspx)
- Sklep Windows i Windows Phone: [EmailRights.Reply](https://msdn.microsoft.com/library/microsoft.rightsmanagement.emailrights.reply.aspx)
- Linux: [EmailRights::Reply](http://azuread.github.io/rms-sdk-for-cpp/classrmscore_1_1modernapi_1_1EmailRights.html)

**OdpowiadanieWszystkim** — zwykle po udzieleniu tego prawa aplikacja umożliwia odbiorcy wiadomości e-mail udzielenie odpowiedzi wszystkim odbiorcom wiadomości chronionej i dołączenie kopii oryginalnej wiadomości.

- Android: [EmailRights.ReplyAll</strong>](https://msdn.microsoft.com/library/dn758285.aspx)
- iOS i OS X: [MSEmailRights replyAll](https://msdn.microsoft.com/library/dn758319.aspx)
- Sklep Windows i Windows Phone: [EmailRights.ReplyAll](https://msdn.microsoft.com/library/microsoft.rightsmanagement.emailrights.replyall.aspx)
- Linux: [EmailRights::ReplyAll](http://azuread.github.io/rms-sdk-for-cpp/classrmscore_1_1modernapi_1_1EmailRights.html)
