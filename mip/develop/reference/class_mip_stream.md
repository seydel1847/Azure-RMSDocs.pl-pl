---
title: Klasa mip Stream
description: Dokumentacja dotycząca Stream mip klasy
author: BryanLa
ms.service: information-protection
ms.topic: reference
ms.date: 09/27/2018
ms.author: bryanla
ms.openlocfilehash: e6296c5e15590741e008979dcf12373ff5fcdf00
ms.sourcegitcommit: 1cf14852cd14ea91ac964fb03a901238455ffdff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/28/2018
ms.locfileid: "47445227"
---
# <a name="class-mipstream"></a>Klasa mip::Stream 
Klasa, która definiuje interfejs między MIP zestaw SDK, na podstawie strumienia zawartości.
  
## <a name="summary"></a>Podsumowanie
 Elementy członkowskie                        | Opisy                                
--------------------------------|---------------------------------------------
 publiczne odczytu int64_t (uint8_t * buforu, int64_t bufferLength)  |  Przeczytaj do buforu strumienia.
 publiczne int64_t zapisu (const uint8_t * bufor, int64_t bufferLength)  |  Zapis w strumieniu buforu.
 publiczne bool Flush()  |  Flush strumienia.
 publiczne Seek void (int64_t pozycji)  |  Wyszukiwanie określonej pozycji w strumieniu.
 publiczne bool CanRead() const  |  Sprawdź, czy strumień może odczytywać.
 publiczne bool CanWrite() const  |  Sprawdź, czy można zapisać w strumieniu.
 publiczne int64_t Position()  |  Pobierz bieżącą pozycję w strumieniu.
 publiczne int64_t Size()  |  Pobieranie rozmiaru zawartości w strumieniu.
 publiczne rozmiar void (int64_t wartość)  |  Ustaw rozmiar strumienia.
  
## <a name="members"></a>Elementy członkowskie
  
### <a name="read"></a>Odczyt
Przeczytaj do buforu strumienia.

Parametry:  
* **Bufor**: wskaźnik do buforu 


* **bufferLength**: rozmiar buforu. 



  
**Zwraca**: Liczba odczytanych bajtów.
  
### <a name="write"></a>Zapis
Zapis w strumieniu buforu.

Parametry:  
* **Bufor**: wskaźnik do buforu 


* **bufferLength**: rozmiar buforu. 



  
**Zwraca**: liczba zapisanych bajtów.
  
### <a name="flush"></a>Flush
Flush strumienia.

  
**Zwraca**: wartość True, jeśli to się powiedzie, else wartość false.
  
### <a name="seek"></a>Wyszukiwanie
Wyszukiwanie określonej pozycji w strumieniu.

Parametry:  
* **pozycja**: do wyszukania w strumieniu.


  
### <a name="canread"></a>Parametr CanRead
Sprawdź, czy strumień może odczytywać.

  
**Zwraca**: wartość True, jeśli jest to czytelny else wartość false.
  
### <a name="canwrite"></a>CanWrite
Sprawdź, czy można zapisać w strumieniu.

  
**Zwraca**: wartość True, jeśli jest zapisywalny else wartość false.
  
### <a name="position"></a>Stanowisko
Pobierz bieżącą pozycję w strumieniu.

  
**Zwraca**: pozycji w strumieniu.
  
### <a name="size"></a>Size
Pobieranie rozmiaru zawartości w strumieniu.

  
**Zwraca**: rozmiar strumienia.
  
### <a name="size"></a>Size
Ustaw rozmiar strumienia.

Parametry:  
* **strumień**: rozmiar.

