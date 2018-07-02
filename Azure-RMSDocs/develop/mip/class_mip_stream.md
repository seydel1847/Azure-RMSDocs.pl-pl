# <a name="class-mipstream"></a>Klasa mip::Stream 
Klasa, która definiuje interfejs między mip zestawu sdk i strumieni na podstawie zawartości.
  
## <a name="summary"></a>Podsumowanie
 Elementy członkowskie                        | Opisy                                
--------------------------------|---------------------------------------------
 publiczne odczytu int64_t (uint8_t * buforu, int64_t bufferLength)  |  Przeczytaj do buforu strumienia.
 publiczne int64_t zapisu (const uint8_t * bufor, int64_t bufferLength)  |  Zapis w strumieniu buforu.
 publiczne bool Flush()  |  Flush strumienia.
 publiczne Seek void (uint64_t pozycji)  |  Wyszukiwanie określonej pozycji w strumieniu.
 publiczne bool CanRead() const  |  Sprawdź, czy strumień jest do odczytu.
 publiczne bool CanWrite() const  |  Sprawdź, czy strumień jest zapisywalna.
 publiczne uint64_t Position()  |  Pobierz bieżącą pozycję w strumieniu.
 publiczne uint64_t Size()  |  Pobieranie rozmiaru zawartości w strumieniu.
 publiczne rozmiar void (uint64_t wartość)  |  Ustaw rozmiar strumienia.
  
## <a name="members"></a>Elementy członkowskie
  
### <a name="read"></a>Odczyt
Przeczytaj do buforu strumienia.

Parametry:  
* **Bufor**: wskaźnik do buforu 


* **bufferLength**: rozmiar buforu. 



  
**Zwraca**: liczba bajtów odczytanych w rzeczywistości.
  
### <a name="write"></a>Zapis
Zapis w strumieniu buforu.

Parametry:  
* **Bufor**: wskaźnik do buforu 


* **bufferLength**: rozmiar buforu. 



  
**Zwraca**: liczba bajtów zapisanych w rzeczywistości.
  
### <a name="flush"></a>Flush
Flush strumienia.

  
**Zwraca**: wartość True, jeśli to się powiedzie, else wartość false.
  
### <a name="seek"></a>Wyszukiwanie
Wyszukiwanie określonej pozycji w strumieniu.

Parametry:  
* **pozycja**: do wyszukania w strumieniu.


  
### <a name="canread"></a>Parametr CanRead
Sprawdź, czy strumień jest do odczytu.

  
**Zwraca**: wartość True, jeśli jest to czytelny else wartość false.
  
### <a name="canwrite"></a>CanWrite
Sprawdź, czy strumień jest zapisywalna.

  
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

