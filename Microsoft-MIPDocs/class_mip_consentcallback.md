# <a name="class-mipconsentcallback"></a>Klasa mip::ConsentCallback 
Interfejs na potrzeby powiadomień żądania zgody.
To wywołanie zwrotne jest zaimplementowana przez aplikację klienta, należy wiedzieć, kiedy wyświetlone powiadomienie zgody użytkownika.
## <a name="summary"></a>Podsumowanie
 Elementy członkowskie                        | Opisy                                
--------------------------------|---------------------------------------------
publiczny ConsentList ConsentsConsentList & zgody) | Wywoływane, gdy zestaw SDK wymaga zgody użytkownika dla danej operacji.
## <a name="members"></a>Elementy członkowskie
### <a name="consentlist"></a>ConsentList
Wywoływane, gdy zestaw SDK wymaga zgody użytkownika dla danej operacji.
#### <a name="parameters"></a>Parametry
* wyraża zgodę na liście zgody wymagane przez zestaw SDK
#### <a name="returns"></a>Zwraca
[Zgoda](#classmip_1_1_consent) wyniki zleconą zgody przez zestaw SDK, aplikacja kliencka powinna uzyskać zgodę od użytkownika, wyniki każdego zgody powinny być przechowywane za pomocą [Consent::Result(const ConsentResult&)](#classmip_1_1_consent_1ad6c17d9af548a40b2fe854fe0d9bca64), a powinna być zwrócona lista rozpoznać zgody.