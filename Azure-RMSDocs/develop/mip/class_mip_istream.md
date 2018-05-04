# <a name="class-mipistream"></a>Klasa mip::IStream 
Podstawowy interfejs dla strumieni chronionych.
Przeniesione z Windows::Storage::Streams::IRandomAccessStream::IRandomAccessStream i Windows::Storage::Streams::FileRandomAccessStream::FileRandomAccessStream. [https://msdn.microsoft.com/en-us/library/windows/apps/windows.storage.streams.irandomaccessstream.aspx](https://msdn.microsoft.com/en-us/library/windows/apps/windows.storage.streams.irandomaccessstream.aspx)[https://msdn.microsoft.com/en-us/library/windows/apps/windows.storage.streams.filerandomaccessstream.aspx](https://msdn.microsoft.com/en-us/library/windows/apps/windows.storage.streams.filerandomaccessstream.aspx)
  
## <a name="summary"></a>Podsumowanie
 Elementy członkowskie                        | Opisy                                
--------------------------------|---------------------------------------------
publiczny std::shared_future < int64_t > ReadAsync (uint8_t * pbBuffer, int64_t cbBuffer, int64_t cbOffset, std::launch launchType)  |  Asynchronicznie odczytuje blok danych ze strumienia.
publiczny std::shared_future < int64_t > WriteAsync (const uint8_t * cpbBuffer, int64_t cbBuffer, int64_t cbOffset, std::launch launchType)  |  Zapisuje asynchronicznie bloku danych do strumienia.
publiczny std::future<bool> FlushAsync (std::launch launchType)  |  Opróżnień wyjściowej asynchronicznie buforu strumienia.
publiczny odczytu int64_t (uint8_t * pbBuffer, int64_t cbBuffer)  |  Odczytuje synchronicznie bloku danych ze strumienia.
publiczny int64_t zapisu (const uint8_t * cpbBuffer, int64_t cbBuffer)  |  Zapisuje synchronicznie bloku danych do strumienia.
publiczny bool Flush()  |  Opróżnień wyjściowej synchronicznie buforu strumienia.
publiczny SharedStream Clone()  |  Klony strumienia.
publiczny Seek void (uint64_t u64Position)  |  Ma na celu pozycji w strumieniu.
publiczny bool CanRead() const  |  Pobiera lub nie można odczytać strumienia.
publiczny bool CanWrite() const  |  Pobiera lub nie można zapisać strumienia.
publiczny uint64_t Position()  |  Pobiera bieżącą pozycję strumienia od początku (w bajtach)
publiczny uint64_t Size()  |  Pobiera rozmiar strumienia (w bajtach)
Rozmiar publicznego void (uint64_t u64Value)  |  Ustawia rozmiar strumienia (w bajtach)
wbudowany publiczny wirtualny std::vector < uint8_t > odczytu (uint64_t u64size)  |  Odczytuje synchronicznie bloku danych ze strumienia.
  
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
  
### <a name="read"></a>Odczyt
Odczytuje synchronicznie bloku danych ze strumienia.
  
#### <a name="parameters"></a>Parametry
* u64size rozmiar danych do odczytu (w bajtach)
  
#### <a name="returns"></a>Zwraca
Wektor rzeczywiste dane do odczytu