# <a name="class-miploggerdelegate"></a>Klasa mip::LoggerDelegate 
Klasa, która definiuje interfejs do rejestratora sdk mip.
  
## <a name="summary"></a>Podsumowanie
 Elementy członkowskie                        | Opisy                                
--------------------------------|---------------------------------------------
 publiczne Init void (const std::string & storagePath, LogLevel logLevel)  |  Inicjowanie rejestratora.
 publiczne LogLevel GetLogLevel() const  |  Uzyskaj loglevel minimalne, które będą wyzwalać zdarzenia rejestrowania.
 publiczne Flush() void  |  Usuń z rejestratora.
 publiczne WriteToLog void (const poziom LogLevel const std::string & wiadomości, const std::string & — funkcja, const std::string & pliku, const wiersza int32_t)  |  Napisz instrukcję dziennik do pliku dziennika.
  
## <a name="members"></a>Elementy członkowskie
  
### <a name="init"></a>Init
Inicjowanie rejestratora.

Parametry:  
* **storagePath**: ścieżka do lokalizacji, w których trwały stan, w tym dzienniki, mogą być przechowywane. 


* **logLevel**: loglevel minimalne, które będą wyzwalać zdarzenia rejestrowania.


  
### <a name="loglevel"></a>LogLevel
Uzyskaj loglevel minimalne, które będą wyzwalać zdarzenia rejestrowania.

  
**Zwraca**: loglevel minimalne, które będą wyzwalać zdarzenia rejestrowania.
  
### <a name="flush"></a>Flush
Usuń z rejestratora.
  
### <a name="writetolog"></a>WriteToLog
Napisz instrukcję dziennik do pliku dziennika.

Parametry:  
* **poziom**: loglevel dla instrukcji dziennika. 


* **komunikat**: komunikat dla instrukcji dziennika. 


* **Funkcja**: Nazwa funkcji dla instrukcji dziennika. 


* **plik**: Nazwa pliku, w której instrukcję log został wygenerowany. 


* **wiersz**: numer wiersza, w którym został wygenerowany instrukcję log.

