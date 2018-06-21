# <a name="class-mipconsentcallback"></a>Klasa mip::ConsentCallback 
Interfejs na potrzeby powiadomień żądania zgody.
To wywołanie zwrotne jest zaimplementowana przez aplikację klienta, należy wiedzieć, kiedy wyświetlone powiadomienie zgody użytkownika.
  
## <a name="summary"></a>Podsumowanie
 Elementy członkowskie                        | Opisy                                
--------------------------------|---------------------------------------------
 publiczny ConsentList Consents(ConsentList& consents)  |  Wywoływane, gdy zestaw SDK wymaga zgody użytkownika dla danej operacji.
  
## <a name="members"></a>Elementy członkowskie
  
### <a name="consentlist"></a>ConsentList
Wywoływane, gdy zestaw SDK wymaga zgody użytkownika dla danej operacji.

Parametry:  
* **zgadza**: Lista zgody wymagane przez zestaw SDK



  
**Zwraca**: [zgody](class_mip_consent.md) wyniki zleconą zgody przez zestaw SDK, aplikacja kliencka powinna uzyskać zgodę od użytkownika, wyniki każdego zgody powinny być przechowywane za pomocą [Consent::Result (const ConsentResult &)](class_mip_consent.md#result), i powinna być zwracana lista rozpoznać zgody.