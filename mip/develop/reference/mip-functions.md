---
title: Funkcje
description: Funkcje
author: BryanLa
ms.service: information-protection
ms.topic: reference
ms.date: 09/27/2018
ms.author: bryanla
ms.openlocfilehash: 3bb9cd594022085c24c45bde428cb11f6734caab
ms.sourcegitcommit: 1cf14852cd14ea91ac964fb03a901238455ffdff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/28/2018
ms.locfileid: "47446519"
---
# <a name="functions"></a>Funkcje

| Funkcje (zasięg)              | Opisy                                |
|--------------------------------|---------------------------------------------|
**Wspólne** |
publiczne std::string const & GetCustomSettingPolicyDataName()       |  Nazwa ustawienia jawnie określić dane zasad.
publiczne std::string const & GetCustomSettingExportPolicyFileName()       |  Nazwa ustawienia jawnie określić ścieżkę pliku do wyeksportowania danych zasad SCC.
publiczne std::string const & GetCustomSettingPolicyDataFile()       |  Nazwa ustawienia jawnie określić ścieżkę pliku danych zasad.
 **Funkcje mipmapy** |
publiczne std::shared_ptr < mip::Stream > CreateStreamFromBuffer (uint8_t * buforu, const rozmiar int64_t)       |  Tworzy [Stream](class_mip_stream.md) buforu.
publiczne std::shared_ptr < mip::Stream > CreateStreamFromStdStream (const std::shared_ptr < std::iostream > & stdIOStream)       |  Tworzy [Stream](class_mip_stream.md) z std::iostream.
publiczne std::shared_ptr < mip::Stream > CreateStreamFromStdStream (const std::shared_ptr < std::istream > & stdIStream)       |  Tworzy [Stream](class_mip_stream.md) z std::istream.
publiczne std::shared_ptr < mip::Stream > CreateStreamFromStdStream (const std::shared_ptr < std::ostream > & stdOStream)       |  Tworzy [Stream](class_mip_stream.md) z std::ostream.
publiczne ReleaseAllResources() void       |  Zwolnij wszystkie zasoby (wątków itp.), przed zamknięciem.
**Funkcje MIP::Rights**|
publiczne std::string AuditedExtract()       |  Pobiera identyfikator ciągu dla "inspekcji wyodrębniania" po prawej.
publiczne std::string Comment()       |  Pobiera identyfikator ciągu dla "comment" po prawej.
publiczne std::vector < std::string > CommonRights()       |  Pobiera listę praw, które są stosowane we wszystkich scenariuszach.
publiczne std::string Edit()       |  Pobiera identyfikator ciągu dla "Edytuj" prawa.
publiczne std::vector < std::string > EditableDocumentRights()       |  Pobiera listę praw, które są stosowane do dokumentów.
publiczne std::vector < std::string > EmailRights()       |  Pobiera listę praw, które są stosowane do wiadomości e-mail.
publiczne std::string Export()       |  Pobiera identyfikator ciągu dla "Eksportuj" po prawej.
publiczne std::string Extract()       |  Pobiera identyfikator ciągu dla '' prawo wyodrębniania.
publiczne std::string Forward()       |  Pobiera identyfikator ciągu dla "do przodu" po prawej stronie.
publiczne std::string Owner()       |  Pobiera identyfikator ciągu dla 'owner' prawo.
std::string publicznego Print()       |  Pobiera identyfikator ciągu dla "drukowania" po prawej stronie.
publiczne std::string Reply()       |  Pobiera identyfikator ciągu dla "Odpowiedz" po prawej.
publiczne std::string ReplyAll()       |  Pobiera identyfikator ciągu dla prawa "Odpowiedz wszystkim".
publiczne std::string View()       |  Pobiera identyfikator ciągu dla "Widok" po prawej.
**Funkcje MIP::Roles**|
publiczne std::string Author()       |  Pobiera identyfikator ciągu dla roli "Autor".
publiczne std::string CoOwner()       |  Pobiera identyfikator ciągu dla roli "współwłaściciel".
publiczne std::string Reviewer()       |  Pobiera identyfikator ciągu dla roli "reviewer".
publiczne std::string Viewer()       |  Pobiera identyfikator ciągu dla roli "Podgląd".

  
## <a name="functions-common"></a>Funkcje (wspólna)

### <a name="getcustomsettingpolicydataname"></a>GetCustomSettingPolicyDataName
Nazwa ustawienia jawnie określić dane zasad.

  
**Zwraca**: klucz Ustawienia niestandardowe.
  
### <a name="getcustomsettingexportpolicyfilename"></a>GetCustomSettingExportPolicyFileName
Nazwa ustawienia jawnie określić ścieżkę pliku do wyeksportowania danych zasad SCC.

  
**Zwraca**: klucz Ustawienia niestandardowe.
  
### <a name="getcustomsettingpolicydatafile"></a>GetCustomSettingPolicyDataFile
Nazwa ustawienia jawnie określić ścieżkę pliku danych zasad.

  
**Zwraca**: klucz Ustawienia niestandardowe.

## <a name="functions-mip"></a>Funkcje (mip)

### <a name="mipcreatestreamfrombufferbuffer"></a>MIP::CreateStreamFromBuffer(buffer)

Tworzy [Stream](class_mip_stream.md) buforu.

Parametry:  
* **Bufor**: wskaźnik do buforu

**Zwraca**: **rozmiar** buforu
  

### <a name="mipcreatestreamfromstdstreamistream"></a>MIP::CreateStreamFromStdStream(IStream)

Tworzy [Stream](class_mip_stream.md) z std::istream.

Parametry:  

* **stdIStream**: tworzenie kopii std::istream
  
**Zwraca**: [Stream](class_mip_stream.md) zawijania std::istream
  
### <a name="mipcreatestreamfromstdstreamiostream"></a>MIP::CreateStreamFromStdStream(iostream)

Tworzy [Stream](class_mip_stream.md) z std::iostream.

Parametry:  
* **stdIOStream**: tworzenie kopii std::iostream
  
**Zwraca**: [Stream](class_mip_stream.md) zawijania std::iostream
  
### <a name="mipcreatestreamfromstdstreamostream"></a>MIP::CreateStreamFromStdStream(ostream)

Tworzy [Stream](class_mip_stream.md) z std::ostream.

Parametry:  
* **stdOStream**: tworzenie kopii std::ostream
  
**Zwraca**: [Stream](class_mip_stream.md) zawijania std::ostream
  
### <a name="mipreleaseallresources"></a>MIP::ReleaseAllResources

Zwolnij wszystkie zasoby (wątków itp.), przed zamknięciem.  

W przypadku MIP dynamicznych bibliotek ładowanych z opóźnieniem przez aplikację, ta funkcja musi zostać wywołana przed aplikacji jawne zwalnianie tych bibliotek MIP w celu uniknięcia zakleszczenia. Na przykład na win32, ta funkcja musi być wywoływana przed wszelkie wywołania jawnie zwolnić biblioteki DLL MIP, za pośrednictwem FreeLibrary lub \__FUnloadDelayLoadedDLL2. Aplikacje muszą Zwolnij odwołania do wszystkich obiektów MIP (na przykład, profile, aparatów, obsługi) przed wywołaniem tej funkcji.

## <a name="functions-miprights"></a>Funkcje (mip::rights)

### <a name="owner"></a>Właściciel
Pobiera identyfikator ciągu dla 'owner' prawo.

  
**Zwraca**: identyfikator ciągu "właściciel" prawej
  
### <a name="auditedextract"></a>AuditedExtract
Pobiera identyfikator ciągu dla "inspekcji wyodrębniania" po prawej.

  
**Zwraca**: identyfikator ciągu dla "inspekcji wyodrębniania" po prawej
  
### <a name="comment"></a>Komentarz
Pobiera identyfikator ciągu dla "comment" po prawej.

  
**Zwraca**: identyfikator ciągu dla "comment" po prawej
  
### <a name="commonrights"></a>CommonRights
Pobiera listę praw, które są stosowane we wszystkich scenariuszach.

  
**Zwraca**: listę praw, które są stosowane we wszystkich scenariuszach

### <a name="edit"></a>Edytowanie
Pobiera identyfikator ciągu dla "Edytuj" prawa.

  
**Zwraca**: identyfikator ciągu "Edytuj" po prawej stronie
  
### <a name="editabledocumentrights"></a>EditableDocumentRights
Pobiera listę praw, które są stosowane do dokumentów.

  
**Zwraca**: listę praw, które są stosowane do dokumentów
  
### <a name="emailrights"></a>EmailRights
Pobiera listę praw, które są stosowane do wiadomości e-mail.

  
**Zwraca**: listę praw, które są stosowane do wiadomości e-mail
  
### <a name="export"></a>Eksportowanie
Pobiera identyfikator ciągu dla "Eksportuj" po prawej.

  
**Zwraca**: identyfikator ciągu dla "Eksportuj" po prawej
  
### <a name="extract"></a>Wyodrębnianie
Pobiera identyfikator ciągu dla '' prawo wyodrębniania.

  
**Zwraca**: identyfikator ciągu "wyciąg" po prawej stronie
  
### <a name="forward"></a>Prześlij dalej
Pobiera identyfikator ciągu dla "do przodu" po prawej stronie.

  
**Zwraca**: identyfikator ciągu dla "do przodu" po prawej stronie.
  
### <a name="print"></a>Drukowanie
Pobiera identyfikator ciągu dla "drukowania" po prawej stronie.

  
**Zwraca**: identyfikator ciągu dla "drukowania" po prawej stronie.
  
### <a name="reply"></a>Odpowiedz
Pobiera identyfikator ciągu dla "Odpowiedz" po prawej.

  
**Zwraca**: identyfikator ciągu dla "Odpowiedz" po prawej
  
### <a name="replyall"></a>Odpowiadanie wszystkim
Pobiera identyfikator ciągu dla prawa "Odpowiedz wszystkim".

  
**Zwraca**: identyfikator ciągu dla prawa "Odpowiedz wszystkim"
  
### <a name="view"></a>Wyświetl
Pobiera identyfikator ciągu dla "Widok" po prawej.

  
**Zwraca**: identyfikator ciągu dla "Widok" po prawej
  

## <a name="functions-miproles"></a>Funkcje (mip::roles)

### <a name="author"></a>Autor
Pobiera identyfikator ciągu dla roli "Autor".

Autor może wyświetlanie, edytowanie, kopiowanie i drukowanie zawartości.
  
**Zwraca**: identyfikator ciągu dla roli "Autor"
  
### <a name="coowner"></a>CoOwner
Pobiera identyfikator ciągu dla roli "współwłaściciel".

Współwłaściciela ma wszystkie uprawnienia
  
**Zwraca**: identyfikator ciągu dla roli "współwłaściciel"

### <a name="reviewer"></a>Recenzent
Pobiera identyfikator ciągu dla roli "reviewer".

Osoba dokonująca przeglądu można wyświetlać i edytować zawartość. One nie można skopiować lub wydrukować.
  
**Zwraca**: identyfikator ciągu dla roli "reviewer"
  
### <a name="viewer"></a>Przeglądanie
Pobiera identyfikator ciągu dla roli "Podgląd".

Przeglądarka może wyświetlać tylko zawartość. One nie można edytować, skopiować ani wydrukować.
  
**Zwraca**: identyfikator ciągu dla roli "Przeglądarka"
  
