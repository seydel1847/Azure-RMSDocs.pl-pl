---
title: Klasa mip AddContentHeaderAction
description: Odwołanie do klasy mip AddContentHeaderAction
author: BryanLa
ms.service: information-protection
ms.topic: reference
ms.date: 09/27/2018
ms.author: bryanla
ms.openlocfilehash: bc60fe32005a0c6bc8088ab7687a3f711ae7a99a
ms.sourcegitcommit: 1cf14852cd14ea91ac964fb03a901238455ffdff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/28/2018
ms.locfileid: "47445652"
---
# <a name="class-mipaddcontentheaderaction"></a>Klasa mip::AddContentHeaderAction 
Klasa akcji, która określa Dodawanie nagłówka zawartości.
  
## <a name="summary"></a>Podsumowanie
 Elementy członkowskie                        | Opisy                                
--------------------------------|---------------------------------------------
 publiczne std::string const & GetUIElementName()  |  Interfejs API jest używany do oznaczania element zawartości nagłówka.
 publiczne std::string const & GetText() const  |  Pobierz tekst, który jest przeznaczony do przejdź do zawartości nagłówka.
 publiczne std::string const & GetFontName() const  |  Pobierz nazwę czcionki używany do wyświetlania zawartości nagłówka.
 publiczne int GetFontSize() const  |  Pobierz rozmiar czcionki używany do wyświetlania zawartości nagłówka.
 publiczne std::string const & GetFontColor() const  |  Pobierz kolor czcionki używany do wyświetlania zawartości nagłówka.
 publiczne ContentMarkAlignment GetAlignment() const  |  Uzyskaj wyrównanie nagłówka.
 publiczne int GetMargin() const  |  Pobierz margines nagłówka z dołu.
 publiczne wartości GetType() obiektu ActionType const  |  Pobierz typ [akcji](class_mip_action.md).
  
## <a name="members"></a>Elementy członkowskie
  
### <a name="getuielementname"></a>GetUIElementName
Interfejs API jest używany do oznaczania element zawartości nagłówka.

  
**Zwraca**: nazwa, która powinna być używana dla elementu interfejsu użytkownika, który zawiera nagłówek zawartości. Tej samej nazwie, zostaną zwrócone w [RemoveContentHeaderAction](class_mip_removecontentheaderaction.md) w przypadku, gdy konieczne jest usunięcie zawartości nagłówka.
  
### <a name="gettext"></a>GetText
Pobierz tekst, który jest przeznaczony do przejdź do zawartości nagłówka.

  
**Zwraca**: zawartości tekst nagłówka.
  
### <a name="getfontname"></a>GetFontName
Pobierz nazwę czcionki używany do wyświetlania zawartości nagłówka.

  
**Zwraca**: Nazwa czcionki. Wartość domyślna to Calibri, jeśli nic nie jest ustawiony przez zasady.
  
### <a name="getfontsize"></a>GetFontSize
Pobierz rozmiar czcionki używany do wyświetlania zawartości nagłówka.

  
**Zwraca**: rozmiar czcionki jako liczba całkowita.
  
### <a name="getfontcolor"></a>GetFontColor
Pobierz kolor czcionki używany do wyświetlania zawartości nagłówka.

  
**Zwraca**: kolor czcionki jako ciąg (na przykład, #000000 ").
  
### <a name="getalignment"></a>GetAlignment
Uzyskaj wyrównanie nagłówka.

  
**Zwraca**: moduł wyliczający ContentMarkAlignment: po lewej stronie | PO PRAWEJ STRONIE | CENTRUM. 
  
**Zobacz też**: ContentMarkAlignment
  
### <a name="getmargin"></a>GetMargin
Pobierz margines nagłówka z dołu.

  
**Zwraca**: marginesy w dolnej części dokumentu (na przykład 10 mm).
  
### <a name="actiontype"></a>ActionType
Pobierz typ [akcji](class_mip_action.md).

  
**Zwraca**: ActionType typu pochodnego akcji mogą być rzutowane tej klasy bazowej.