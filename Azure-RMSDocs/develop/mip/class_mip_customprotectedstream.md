# <a name="class-mipcustomprotectedstream"></a>Klasa mip::CustomProtectedStream 
Opakowuje strumienia, aby zapewnić przezroczystego szyfrowania i odszyfrowywania na odczyt i zapis.
  
## <a name="summary"></a>Podsumowanie
 Elementy członkowskie                        | Opisy                                
--------------------------------|---------------------------------------------
publiczny std::shared_future < int64_t > ReadAsync (uint8_t * pbBuffer, int64_t cbBuffer, int64_t cbOffset, std::launch launchType)  |  Asynchronicznie odczytuje blok danych ze strumienia.
publiczny std::shared_future < int64_t > WriteAsync (const uint8_t * cpbBuffer, int64_t cbBuffer, int64_t cbOffset, std::launch launchType)  |  Zapisuje asynchronicznie bloku danych do strumienia.
publiczny std::future<bool> FlushAsync (std::launch launchType)  |  Opróżnień wyjściowej asynchronicznie buforu strumienia.
 publiczny odczytu int64_t (uint8_t * pbBuffer, int64_t cbBuffer)  |  Odczytuje synchronicznie bloku danych ze strumienia.
publiczny wirtualny std::vector < uint8_t > odczytu (uint64_t u64size)  |  Odczytuje synchronicznie bloku danych ze strumienia.
 publiczny int64_t zapisu (const uint8_t * cpbBuffer, int64_t cbBuffer)  |  Zapisuje synchronicznie bloku danych do strumienia.
 publiczny bool Flush()  |  Opróżnień wyjściowej synchronicznie buforu strumienia.
 publiczny SharedStream Clone()  |  Klony strumienia.
 publiczny Seek void (uint64_t u64Position)  |  Ma na celu pozycji w strumieniu.
 publiczny bool CanRead() const  |  Pobiera lub nie można odczytać strumienia.
 publiczny bool CanWrite() const  |  Pobiera lub nie można zapisać strumienia.
 publiczny uint64_t Position()  |  Pobiera bieżącą pozycję strumienia od początku (w bajtach)
 publiczny uint64_t Size()  |  Pobiera rozmiar strumienia (w bajtach)
 Rozmiar publicznego void (uint64_t u64Value)  |  Ustawia rozmiar strumienia (w bajtach)
  
## <a name="members"></a>Elementy członkowskie
  
### <a name="readasync"></a>ReadAsync
Asynchronicznie odczytuje blok danych ze strumienia.

Parametry:  
* **pbBuffer**: buforu, w którym można odczytać strumienia 


* **cbBuffer**: rozmiar buforu 


* **cbOffset**: Przesunięcie od początku którym powinny one zacząć odczytu strumienia wejściowego 


* **launchType**: typ uruchamiania Async



  
**Zwraca**: asynchroniczne przyszłych zawierający rzeczywistą liczbę bajtów do odczytu buforu upewnij się, że istnieje dopóki wynik jest pobranych z std::future
  
### <a name="writeasync"></a>WriteAsync
Zapisuje asynchronicznie bloku danych do strumienia.

Parametry:  
* **cpbBuffer**: bufor danych do zapisu 


* **cbBuffer**: rozmiar buforu 


* **cbOffset**: Przesunięcie od początku strumienia wyjściowego do której należy rozpocząć pisanie 


* **launchType**: typ uruchamiania Async



  
**Zwraca**: asynchroniczne przyszłych zawierający rzeczywista liczba bajtów zapisanych buforu upewnij się, że istnieje dopóki wynik jest pobranych z std::future
  
### <a name="flushasync"></a>FlushAsync
Opróżnień wyjściowej asynchronicznie buforu strumienia.

Parametry:  
* **launchType**: typ uruchamiania Async



  
**Zwraca**: asynchroniczne przyszłych zawierających lub nie powiodło się opróżnienie
  
### <a name="read"></a>Odczyt
Odczytuje synchronicznie bloku danych ze strumienia.

Parametry:  
* **pbBuffer**: buforu, w którym można odczytać strumienia 


* **cbBuffer**: rozmiar buforu



  
**Zwraca**: rzeczywista liczba bajtów odczytanych
  
### <a name="read"></a>Odczyt
Odczytuje synchronicznie bloku danych ze strumienia.

Parametry:  
* **u64size**: rozmiar danych do odczytu (w bajtach)



  
**Zwraca**: rzeczywiste wektor odczytanie danych
  
### <a name="write"></a>Zapis
Zapisuje synchronicznie bloku danych do strumienia.

Parametry:  
* **cpbBuffer**: bufor danych do zapisu 


* **cbBuffer**: rozmiar buforu



  
**Zwraca**: rzeczywista liczba zapisanych bajtów
  
### <a name="flush"></a>Flush
Opróżnień wyjściowej synchronicznie buforu strumienia.

  
**Zwraca**: Określa, czy opróżniania zakończyło się pomyślnie
  
### <a name="sharedstream"></a>SharedStream
Klony strumienia.

  
**Zwraca**: sklonowany strumienia
  
### <a name="seek"></a>Wyszukiwanie
Ma na celu pozycji w strumieniu.

Parametry:  
* **u64Position**: Przesunięcie bajtów od początku strumienia


  
### <a name="canread"></a>Właściwość CanRead
Pobiera lub nie można odczytać strumienia.

  
**Zwraca**: czy nie można odczytać strumienia
  
### <a name="canwrite"></a>Właściwość CanWrite
Pobiera lub nie można zapisać strumienia.

  
**Zwraca**: czy nie mogą być zapisywane strumienia
  
### <a name="position"></a>Stanowisko
Pobiera bieżącą pozycję strumienia od początku (w bajtach)

  
**Zwraca**: bieżąca positition strumienia od początku (w bajtach)
  
### <a name="size"></a>Size
Pobiera rozmiar strumienia (w bajtach)

  
**Zwraca**: rozmiar strumienia (w bajtach)
  
### <a name="size"></a>Size
Ustawia rozmiar strumienia (w bajtach)

Parametry:  
* **u64Value**: rozmiar strumienia (w bajtach)

