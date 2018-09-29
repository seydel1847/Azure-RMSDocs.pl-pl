---
title: Klasa mip AddContentFooterAction
description: Odwołanie do klasy mip AddContentFooterAction
author: BryanLa
ms.service: information-protection
ms.topic: reference
ms.date: 09/27/2018
ms.author: bryanla
ms.openlocfilehash: 73f641d965c3cf0236919557128af2ed07705672
ms.sourcegitcommit: 1cf14852cd14ea91ac964fb03a901238455ffdff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/28/2018
ms.locfileid: "47445839"
---
# <a name="class-mipaddcontentfooteraction"></a>Klasa mip::AddContentFooterAction 
Klasa akcji, która określa Dodawanie zawartości stopki do dokumentu.
  
## <a name="summary"></a>Podsumowanie
 Elementy członkowskie                        | Opisy                                
--------------------------------|---------------------------------------------
 publiczne std::string const & GetUIElementName()  |  Interfejs API jest używany do oznaczania element footer zawartości.
 publiczne std::string const & GetText() const  |  Pobierz tekst, który jest przeznaczony do Przejdź w stopce zawartości.
 publiczne std::string const & GetFontName() const  |  Pobierz nazwę czcionki używany do wyświetlania zawartości stopki.
 publiczne int GetFontSize() const  |  Pobierz rozmiar czcionki używany do wyświetlania zawartości stopki.
 publiczne std::string const & GetFontColor() const  |  Pobierz kolor czcionki używany do wyświetlania zawartości stopki.
 publiczne ContentMarkAlignment GetAlignment() const  |  Uzyskaj wyrównanie stopki.
 publiczne int GetMargin() const  |  Pobierz margines stopki z dołu.
 publiczne wartości GetType() obiektu ActionType const  |  Pobierz typ [akcji](class_mip_action.md).
  
## <a name="members"></a>Elementy członkowskie
  
### <a name="getuielementname"></a>GetUIElementName
Interfejs API jest używany do oznaczania element footer zawartości.

  
**Zwraca**: nazwa, która powinna być używana dla elementu interfejsu użytkownika, który zawiera stopkę zawartości. Tej samej nazwie, zostaną zwrócone w [RemoveContentFooterAction](class_mip_removecontentfooteraction.md) w przypadku, gdy zawartość stopki musi zostać usunięte.
  
### <a name="gettext"></a>GetText
Pobierz tekst, który jest przeznaczony do Przejdź w stopce zawartości.

  
**Zwraca**: zawartości tekst stopki.
  
### <a name="getfontname"></a>GetFontName
Pobierz nazwę czcionki używany do wyświetlania zawartości stopki.

  
**Zwraca**: Nazwa czcionki. Wartość domyślna to Calibri, jeśli nic nie jest ustawiony przez zasady.
  
### <a name="getfontsize"></a>GetFontSize
Pobierz rozmiar czcionki używany do wyświetlania zawartości stopki.

  
**Zwraca**: rozmiar czcionki jako liczba całkowita.
  
### <a name="getfontcolor"></a>GetFontColor
Pobierz kolor czcionki używany do wyświetlania zawartości stopki.

  
**Zwraca**: kolor czcionki jako ciąg (na przykład, "#000000").
  
### <a name="getalignment"></a>GetAlignment
Uzyskaj wyrównanie stopki.

  
**Zwraca**: moduł wyliczający ContentMarkAlignment: po lewej stronie | PO PRAWEJ STRONIE | CENTRUM. 
  
**Zobacz też**: ContentMarkAlignment
  
### <a name="getmargin"></a>GetMargin
Pobierz margines stopki z dołu.

  
**Zwraca**: marginesy w dolnej części dokumentu (na przykład 10 mm).
  
### <a name="actiontype"></a>ActionType
Pobierz typ [akcji](class_mip_action.md).

  
**Zwraca**: ActionType typu pochodnego akcji mogą być rzutowane tej klasy bazowej.