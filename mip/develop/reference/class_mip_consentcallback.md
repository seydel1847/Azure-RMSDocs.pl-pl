# <a name="class-mipconsentcallback"></a>Klasa mip::ConsentCallback 
Interfejs do wyrażania zgody żądania powiadomienia.
To wywołanie zwrotne jest implementowany przez aplikację kliencką, aby dowiedzieć się, kiedy zgłoszenie zgody powinna być wyświetlana użytkownikowi.
  
## <a name="summary"></a>Podsumowanie
 Elementy członkowskie                        | Opisy                                
--------------------------------|---------------------------------------------
 publiczne ConsentList Consents(ConsentList& consents)  |  Wywołuje się, gdy zestaw SDK wymaga zgody użytkownika dla danej operacji.
  
## <a name="members"></a>Elementy członkowskie
  
### <a name="consentlist"></a>ConsentList
Wywołuje się, gdy zestaw SDK wymaga zgody użytkownika dla danej operacji.

Parametry:  
* **wyraża zgodę**: Lista zgody, żądane przez zestaw SDK



  
**Zwraca**: [zgody](class_mip_consent.md) wyniki zleconą zgody przez zestaw SDK, aplikacja kliencka powinna uzyskać zgodę od użytkownika, wyniki każdego zgody powinny znajdować się za pośrednictwem [Consent::Result (const ConsentResult &)](class_mip_consent.md#result), i listę rozpoznać zgody ma zostać zwrócony.