# <a name="class-mipcustomprotectedstream"></a>Klasa mip::CustomProtectedStream 
Opakowuje strumienia, aby zapewnić przezroczystego szyfrowania i odszyfrowywania na odczyt i zapis.
## <a name="summary"></a>Podsumowanie
 Elementy członkowskie                        | Opisy                                
--------------------------------|---------------------------------------------
publiczny std::shared_future < int64_t > ReadAsync | Asynchronicznie odczytuje blok danych ze strumienia.
publiczny std::shared_future < int64_t > WriteAsync | Zapisuje asynchronicznie bloku danych do strumienia.
publiczny std::future < bool > FlushAsync | Opróżnień wyjściowej asynchronicznie buforu strumienia.
Przeczytaj int64_t publiczny | Odczytuje synchronicznie bloku danych ze strumienia.
Przeczytaj wbudowanego publiczny wirtualny std::vector < uint8_t > | Odczytuje synchronicznie bloku danych ze strumienia.
publiczny int64_t zapisu | Zapisuje synchronicznie bloku danych do strumienia.
publiczny bool opróżniania | Opróżnień wyjściowej synchronicznie buforu strumienia.
publiczny SharedStream klonowania | Klony strumienia.
publiczny typ void wyszukiwania | Ma na celu pozycji w strumieniu.
publiczny bool CanRead | Pobiera lub nie można odczytać strumienia.
publiczny bool CanWrite | Pobiera lub nie można zapisać strumienia.
publiczny uint64_t pozycji | Pobiera bieżącą pozycję strumienia od początku (w bajtach)
publiczny uint64_t rozmiaru | Pobiera rozmiar strumienia (w bajtach)
Rozmiar publicznego typu void | Ustawia rozmiar strumienia (w bajtach)
## <a name="members"></a>Elementy członkowskie
### <a name="readasync"></a>ReadAsync
Asynchronicznie odczytuje blok danych ze strumienia.
#### <a name="parameters"></a>Parametry
* Bufor pbBuffer, w którym można odczytać strumienia 
* Rozmiar buforu cbBuffer 
* cbOffset przesunięcie od początku którym powinny one zacząć odczytu strumienia wejściowego 
* launchType typu uruchamiania Async
#### <a name="returns"></a>Zwraca
Asynchroniczne przyszłych zawierający rzeczywista liczba bajtów odczytanych buforu upewnij się, że istnieje dopóki wynik jest pobranych z std::future
### <a name="writeasync"></a>WriteAsync
Zapisuje asynchronicznie bloku danych do strumienia.
#### <a name="parameters"></a>Parametry
* cpbBuffer buforu danych do zapisania 
* Rozmiar buforu cbBuffer 
* Przesunięcie od początku strumienia wyjściowego, do której należy rozpocząć pisanie cbOffset 
* launchType typu uruchamiania Async
#### <a name="returns"></a>Zwraca
Asynchroniczne przyszłych zawierający rzeczywista liczba bajtów zapisanych buforu upewnij się, że istnieje dopóki wynik jest pobranych z std::future
### <a name="flushasync"></a>FlushAsync
Opróżnień wyjściowej asynchronicznie buforu strumienia.
#### <a name="parameters"></a>Parametry
* launchType typu uruchamiania Async
#### <a name="returns"></a>Zwraca
Przyszłe zawierających lub nie powiodło się opróżnienie Async
### <a name="read"></a>Odczyt
Odczytuje synchronicznie bloku danych ze strumienia.
#### <a name="parameters"></a>Parametry
* Bufor pbBuffer, w którym można odczytać strumienia 
* Rozmiar buforu cbBuffer
#### <a name="returns"></a>Zwraca
Rzeczywista liczba odczytanych bajtów
### <a name="read"></a>Odczyt
Odczytuje synchronicznie bloku danych ze strumienia.
#### <a name="parameters"></a>Parametry
* u64size rozmiar danych do odczytu (w bajtach)
#### <a name="returns"></a>Zwraca
Wektor rzeczywiste dane do odczytu
### <a name="write"></a>Zapis
Zapisuje synchronicznie bloku danych do strumienia.
#### <a name="parameters"></a>Parametry
* cpbBuffer buforu danych do zapisania 
* Rozmiar buforu cbBuffer
#### <a name="returns"></a>Zwraca
Rzeczywista liczba zapisanych bajtów
### <a name="flush"></a>Flush
Opróżnień wyjściowej synchronicznie buforu strumienia.
#### <a name="returns"></a>Zwraca
Określa, czy opróżniania zakończyło się pomyślnie
### <a name="sharedstream"></a>SharedStream
Klony strumienia.
#### <a name="returns"></a>Zwraca
Sklonowany strumienia
### <a name="seek"></a>Wyszukiwanie
Ma na celu pozycji w strumieniu.
#### <a name="parameters"></a>Parametry
* Przesunięcie bajtów u64Position od początku strumienia
### <a name="canread"></a>Właściwość CanRead
Pobiera lub nie można odczytać strumienia.
#### <a name="returns"></a>Zwraca
Czy można odczytać strumienia
### <a name="canwrite"></a>Właściwość CanWrite
Pobiera lub nie można zapisać strumienia.
#### <a name="returns"></a>Zwraca
Określa, czy strumień mogą być zapisywane.
### <a name="position"></a>Stanowisko
Pobiera bieżącą pozycję strumienia od początku (w bajtach)
#### <a name="returns"></a>Zwraca
Bieżący positition strumienia od początku (w bajtach)
### <a name="size"></a>Size
Pobiera rozmiar strumienia (w bajtach)
#### <a name="returns"></a>Zwraca
Rozmiar strumienia (w bajtach)
### <a name="size"></a>Size
Ustawia rozmiar strumienia (w bajtach)
#### <a name="parameters"></a>Parametry
* Rozmiar u64Value strumienia (w bajtach)