# <a name="summary"></a>Podsumowanie
 Elementy członkowskie                        | Opisy                                
--------------------------------|---------------------------------------------
 Wyliczenie zgody       |  Reprezentuje użytkownika decyzji zgody, aby nawiązać połączenie z punktu końcowego usługi.
 Struktura ApplicationInfo  |  Identyfikator aplikacji ustawione w portalu usługi Azure AD.
**mipmapy** |
 Wyliczenie ActionType       |  Typy różne akcje.
 Wyliczenie ErrorType       | _Jeszcze nie udokumentowano._
 Wyliczenie LogLevel       |  Poziomy dziennika używane w całym zestawie sdk mip.
 enum ProtectionHandlerCreationOptions       |  Flagi bitowe, które wymuszają zachowanie tworzenia dodatkowych zasad.
 Wyliczenie ProtectionType       |  Opisuje, czy ochrona na podstawie szablonu lub ad-hoc (niestandardowy)

  
## <a name="enumerations-common"></a>Wyliczenia (wspólna)
  
### <a name="consent"></a>Wyrażenie zgody
Reprezentuje użytkownika decyzji zgody, aby nawiązać połączenie z punktu końcowego usługi.

 Wartości                         | Opisy                                
--------------------------------|---------------------------------------------
AcceptAlways            | Zgoda i pamiętać tej decyzji
Zaakceptuj            | Zgodę, tylko jeden raz
Odrzuć            | Nie zgadza się
  
## <a name="enumerations-mip"></a>Wyliczenia (mip)

### <a name="actiontype"></a>ActionType

 Wartości                         | Opisy                                
--------------------------------|---------------------------------------------
ADD_CONTENT_FOOTER            | Dodaj stopkę zawartości do akcji typu dokumentu.
ADD_CONTENT_HEADER            | Dodaj nagłówek zawartości do akcji typu dokumentu.
ADD_WATERMARK            | Dodaj znacznik limitu górnego typem akcji całego dokumentu.
NIESTANDARDOWE            | Typ akcji niestandardowej zdefiniowane.
WYJUSTUJ DO            | Wyjustuj typ akcji.
METADANE            | Metadane zmienić typ akcji.
PROTECT_ADHOC            | Chroń według typu działania zasad ad hoc.
PROTECT_BY_TEMPLATE            | Chroń przez typ akcji szablonu.
PROTECT_DO_NOT_FORWARD            | Chroń przez nie przesyłaj dalej typ akcji.
REMOVE_CONTENT_FOOTER            | Usuń typ akcji stopki zawartości.
REMOVE_CONTENT_HEADER            | Usuń typ akcji nagłówka zawartości.
REMOVE_PROTECTION            | Usuń typ akcji ochrony.
REMOVE_WATERMARK            | Usuń znaki wodne typ akcji.
APPLY_LABEL            | Zastosuj etykietę typ akcji.
RECOMMEND_LABEL            | Zaleca się typ akcji etykietę.
Typy różne akcje.
NIESTANDARDOWA jest typ ogólny akcji. Każdy typ działania jest określoną akcję przy użyciu określone znaczenie.
  
**ActionType** wartości obsługuje następujące operatory:

* Lub (|||) — operator dla [akcji](class_mip_action.md) typu wyliczenia.  
* I (&) operator [akcji](class_mip_action.md) typu wyliczenia.  
* Operator XOR (^) [akcji](class_mip_action.md) typu wyliczenia.  

### <a name="errortype"></a>ErrorType

 Wartości                         | Opisy                                
--------------------------------|---------------------------------------------
BAD_INPUT_ERROR            | Obiekt wywołujący przekazane nieprawidłowe dane wejściowe.
FILE_IO_ERROR            | Błąd We/Wy ogólne pliku.
NETWORK_ERROR            | Problemy z siecią ogólne; np. usługa jest nieosiągalny.
INTERNAL_ERROR            | Nieoczekiwane błędy wewnętrzne. np. w protokole klient serwer (Odebrano nieoczekiwaną odpowiedź).
JUSTIFICATION_REQUIRED            | Do ukończenia działania pliku należy podać uzasadnienie.
NOT_SUPPORTED_OPERATION            | Żądana operacja nie jest jeszcze obsługiwana.
PRIVILEGED_REQUIRED            | Nie można zastąpić uprzywilejowanych etykiety, gdy nowa metoda etykiety jest standardowa.
ACCESS_DENIED            | Użytkownik nie można uzyskać dostępu do zawartości. np. Brak uprawnień zawartości odwołany itp.
  
### <a name="loglevel"></a>LogLevel

 Wartości                         | Opisy                                
--------------------------------|---------------------------------------------
Śledzenia            | 
Informacje o            | 
Ostrzeżenie            | 
Błąd            | 
Poziomy dziennika używane w całym zestawie sdk mip.
  
### <a name="protectionhandlercreationoptions"></a>ProtectionHandlerCreationOptions

 Wartości                         | Opisy                                
--------------------------------|---------------------------------------------
Brak            | Brak
OfflineOnly            | Nie zezwalaj na operacje interfejsu użytkownika i sieci.
AllowAuditedExtraction            | Zawartość będzie można otworzyć w app protection sdk — nieobsługującą
PreferDeprecatedAlgorithms            | Użyj przestarzałe algorytmów kryptograficznych (ECB) dla zapewnienia zgodności
Flagi bitowe, które wymuszają zachowanie tworzenia dodatkowych zasad.
  
### <a name="protectiontype"></a>ProtectionType

 Wartości                         | Opisy                                
--------------------------------|---------------------------------------------
TemplateBased            | Uchwyt został utworzony na podstawie szablonu
Niestandardowe            | Dojście zostało utworzone ad-hoc
Opisuje, czy ochrona na podstawie szablonu lub ad-hoc (niestandardowy)
  
### <a name="protectionhandlercreationoptions"></a>ProtectionHandlerCreationOptions

Bitowy operator OR ProtectionHandlerCreationOptions.

Parametry: 
 
* ****: Left wartość 

* **b**: kliknij prawym przyciskiem myszy wartość
  
**Zwraca**: bitowe lub parametrów
  


## <a name="structures"></a>Struktury

### <a name="applicationinfo"></a>ApplicationInfo 
Identyfikator aplikacji ustawione w portalu usługi Azure AD.
  
 Pola                        | Opisy                                
--------------------------------|---------------------------------------------
 Identyfikator publiczny std::string aplikacji  | Identyfikator aplikacji w portalu usługi Azure AD.
 friendlyName std::string publiczne  | Przyjazna nazwa aplikacji, jak to określono w portalu.
  
