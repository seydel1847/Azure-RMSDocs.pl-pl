# <a name="class-mipstream"></a>Klasa mip::Stream 
Klasa, która definiuje interfejs między MCI sdk i strumieni na podstawie zawartości.
  
## <a name="summary"></a>Podsumowanie
 Elementy członkowskie                        | Opisy                                
--------------------------------|---------------------------------------------
 publiczny odczytu int64_t (uint8_t * buforu, int64_t bufferLength)  |  Przeczytaj w buforze ze strumienia.
 publiczny int64_t zapisu (const uint8_t * buforu, int64_t bufferLength)  |  Zapis ino strumienia z buforu.
 publiczny bool Flush()  |  opróżnienia strumienia.
 publiczny Seek void (uint64_t pozycji)  |  Wyszukiwanie określonej pozycji w strumieniu.
 publiczny bool CanRead() const  |  Sprawdź, czy strumień jest możliwy do odczytu.
 publiczny bool CanWrite() const  |  Sprawdź, czy strumień jest zapisywalna.
 publiczny uint64_t Position()  |  Pobierz bieżącą pozycję w strumieniu.
 publiczny uint64_t Size()  |  Uzyskaj informacje o rozmiarze zawartości w strumieniu.
 Rozmiar publicznego void (uint64_t wartość)  |  Ustaw rozmiar strumienia.
publiczny std::shared_ptr<Stream> Clone()  |  Sklonować strumienia.
  
## <a name="members"></a>Elementy członkowskie
  
### <a name="read"></a>Odczyt
Przeczytaj w buforze ze strumienia.

Parametry:  
* **Bufor**: wskaźnik do buforu 


* **bufferLength**: rozmiar buforu. 



  
**Zwraca**: liczba bajtów odczytanych w rzeczywistości.
  
### <a name="write"></a>Zapis
Zapis ino strumienia z buforu.

Parametry:  
* **Bufor**: wskaźnik do buforu 


* **bufferLength**: rozmiar buforu. 



  
**Zwraca**: liczba bajtów odczytanych w rzeczywistości.
  
### <a name="flush"></a>Flush
opróżnienia strumienia.

  
**Zwraca**: wartość True, jeśli pomyślnie else wartość false.
  
### <a name="seek"></a>Wyszukiwanie
Wyszukiwanie określonej pozycji w strumieniu.

Parametry:  
* **pozycja**: do wyszukania w strumieniu.


  
### <a name="canread"></a>Właściwość CanRead
Sprawdź, czy strumień jest możliwy do odczytu.

  
**Zwraca**: wartość True, jeśli można odczytać else wartość false.
  
### <a name="canwrite"></a>Właściwość CanWrite
Sprawdź, czy strumień jest zapisywalna.

  
**Zwraca**: wartość True, jeśli zapisywalny else wartość false.
  
### <a name="position"></a>Stanowisko
Pobierz bieżącą pozycję w strumieniu.

  
**Zwraca**: pozycja w strumieniu.
  
### <a name="size"></a>Size
Uzyskaj informacje o rozmiarze zawartości w strumieniu.

  
**Zwraca**: rozmiar strumienia.
  
### <a name="size"></a>Size
Ustaw rozmiar strumienia.

Parametry:  
* **strumień**: rozmiar.


  
### <a name="stream"></a>Strumień
Sklonować strumienia.

  
**Zwraca**: nowego strumienia.