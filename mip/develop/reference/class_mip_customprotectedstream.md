# <a name="class-mipcustomprotectedstream"></a>Klasa mip::CustomProtectedStream 
Opakowuje strumienia do udostępniania przezroczyste szyfrowanie i odszyfrowywanie na odczyt i zapis.
  
## <a name="summary"></a>Podsumowanie
 Elementy członkowskie                        | Opisy                                
--------------------------------|---------------------------------------------
publiczne std::shared_future < int64_t > ReadAsync (uint8_t * pbBuffer int64_t cbBuffer, int64_t cbOffset, std::launch launchType)  |  Asynchronicznie odczytuje bloku danych ze strumienia.
publiczne std::shared_future < int64_t > WriteAsync (const uint8_t * cpbBuffer int64_t cbBuffer, int64_t cbOffset, std::launch launchType)  |  Zapisuje asynchronicznie bloku danych w strumieniu.
publiczne std::future<bool> FlushAsync (std::launch launchType)  |  Opróżnienia danych wyjściowych bufor strumienia asynchronicznego.
 publiczne odczytu int64_t (uint8_t * pbBuffer, int64_t cbBuffer)  |  Wykonuje synchroniczny odczyt bloku danych ze strumienia.
publiczne wirtualne std::vector < uint8_t > odczytu (uint64_t u64size)  |  Wykonuje synchroniczny odczyt bloku danych ze strumienia.
 publiczne int64_t zapisu (const uint8_t * cpbBuffer, int64_t cbBuffer)  |  Zapisuje synchronicznie bloku danych w strumieniu.
 publiczne bool Flush()  |  Opróżnienia wyjściowe bufor strumienia, synchronicznie.
 publiczne SharedStream Clone()  |  Klony strumień.
 publiczne Seek void (uint64_t u64Position)  |  Szuka do pozycji w strumieniu.
 publiczne bool CanRead() const  |  Pobiera informację określającą, czy można odczytać strumienia.
 publiczne bool CanWrite() const  |  Pobiera informację określającą, czy mogą być zapisywane strumienia.
 publiczne uint64_t Position()  |  Pobiera bieżącą pozycję strumień od początku (w bajtach)
 publiczne uint64_t Size()  |  Pobiera rozmiar strumienia (w bajtach)
 publiczne rozmiar void (uint64_t u64Value)  |  Ustawia rozmiar strumienia (w bajtach)
  
## <a name="members"></a>Elementy członkowskie
  
### <a name="readasync"></a>ReadAsync
Asynchronicznie odczytuje bloku danych ze strumienia.

Parametry:  
* **pbBuffer**: bufor, do którego można odczytać strumienia 


* **cbBuffer**: rozmiar buforu 


* **cbOffset**: Przesunięcie od początku strumienia wejściowego, w którym ma się zacząć odczytu 


* **launchType**: typ uruchamiania Async



  
**Zwraca**: Async przyszłych, zawierający faktyczną liczbę bajtów odczytu buforu upewnij się, że istnieje do czasu pobranych z std::future wynik
  
### <a name="writeasync"></a>WriteAsync
Zapisuje asynchronicznie bloku danych w strumieniu.

Parametry:  
* **cpbBuffer**: bufor danych do zapisu 


* **cbBuffer**: rozmiar buforu 


* **cbOffset**: Przesunięcie od początku strumienia wyjściowego, do której ma się zacząć zapisu 


* **launchType**: typ uruchamiania Async



  
**Zwraca**: Async przyszłych, zawierający rzeczywista liczba bajtów zapisanych w buforze upewnij się, że istnieje, dopóki wynik jest pobranych z std::future
  
### <a name="flushasync"></a>FlushAsync
Opróżnienia danych wyjściowych bufor strumienia asynchronicznego.

Parametry:  
* **launchType**: typ uruchamiania Async



  
**Zwraca**: Async przyszłych zawierający informację określającą, czy opróżniania zakończyło się pomyślnie
  
### <a name="read"></a>Odczyt
Wykonuje synchroniczny odczyt bloku danych ze strumienia.

Parametry:  
* **pbBuffer**: bufor, do którego można odczytać strumienia 


* **cbBuffer**: rozmiar buforu



  
**Zwraca**: rzeczywista liczba odczytanych bajtów
  
### <a name="read"></a>Odczyt
Wykonuje synchroniczny odczyt bloku danych ze strumienia.

Parametry:  
* **u64size**: rozmiar danych do odczytu (w bajtach)



  
**Zwraca**: rzeczywiste wektor odczytywanie danych
  
### <a name="write"></a>Zapis
Zapisuje synchronicznie bloku danych w strumieniu.

Parametry:  
* **cpbBuffer**: bufor danych do zapisu 


* **cbBuffer**: rozmiar buforu



  
**Zwraca**: rzeczywista liczba zapisanych bajtów
  
### <a name="flush"></a>Flush
Opróżnienia wyjściowe bufor strumienia, synchronicznie.

  
**Zwraca**: Określa, czy opróżniania zakończyło się pomyślnie
  
### <a name="sharedstream"></a>SharedStream
Klony strumień.

  
**Zwraca**: sklonowany strumienia
  
### <a name="seek"></a>Wyszukiwanie
Szuka do pozycji w strumieniu.

Parametry:  
* **u64Position**: przesunięcie w bajtach od początku strumienia


  
### <a name="canread"></a>Parametr CanRead
Pobiera informację określającą, czy można odczytać strumienia.

  
**Zwraca**: czy nie można odczytać strumienia
  
### <a name="canwrite"></a>CanWrite
Pobiera informację określającą, czy mogą być zapisywane strumienia.

  
**Zwraca**: czy nie mogą być zapisywane strumienia
  
### <a name="position"></a>Stanowisko
Pobiera bieżącą pozycję strumień od początku (w bajtach)

  
**Zwraca**: bieżąca positition strumienia od początku (w bajtach)
  
### <a name="size"></a>Size
Pobiera rozmiar strumienia (w bajtach)

  
**Zwraca**: rozmiar strumienia (w bajtach)
  
### <a name="size"></a>Size
Ustawia rozmiar strumienia (w bajtach)

Parametry:  
* **u64Value**: rozmiar strumienia (w bajtach)

