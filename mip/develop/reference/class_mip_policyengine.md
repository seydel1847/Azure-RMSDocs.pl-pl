# <a name="class-mippolicyengine"></a>Klasa mip::PolicyEngine 
Ta klasa udostępnia interfejs dla wszystkich funkcji aparatu.
  
## <a name="summary"></a>Podsumowanie
 Elementy członkowskie                        | Opisy                                
--------------------------------|---------------------------------------------
 publiczne ustawienia const & GetSettings() const  |  Aparat zasad [ustawienia](class_mip_policyengine_settings.md).
publiczne std::vector const < std::shared_ptr<Label>> & ListSensitivityLabels()  |  Lista etykiet czułości skojarzone z aparatu zasad.
 publiczne std::string const & GetMoreInfoUrl() const  |  Podaj adres url dla wyszukiwania więcej informacji na temat zasad/etykiety.
 publiczne bool IsLabelingRequired() const  |  Sprawdza, czy zasady mówią, dokument musi mieć etykietę.
publiczne std::shared_ptr<Label> GetDefaultSensitivityLabel()  |  Pobierz domyślny etykieta poufności.
publiczne std::shared_ptr<PolicyHandler> CreatePolicyHandler (const std::string & contentIdentifier)  |  Utwórz procedurę obsługi zasad wykonywanie zasadach powiązanych z funkcji na stan wykonywania pliku.
  
## <a name="members"></a>Elementy członkowskie
  
### <a name="settings"></a>Ustawienia
Aparat zasad [ustawienia](class_mip_policyengine_settings.md).

  
**Zwraca**: ustawienia aparatu zasad. 
  
**Zobacz też**: [mip::PolicyEngine::Settings](class_mip_policyengine_settings.md)
  
### <a name="label"></a>Etykieta
Lista etykiet czułości skojarzone z aparatu zasad.

  
**Zwraca**: Lista etykiety ważności.
  
### <a name="getmoreinfourl"></a>GetMoreInfoUrl
Podaj adres url dla wyszukiwania więcej informacji na temat zasad/etykiety.

  
**Zwraca**: adres url w formacie ciągu.
  
### <a name="islabelingrequired"></a>IsLabelingRequired
Sprawdza, czy zasady mówią, dokument musi mieć etykietę.

  
**Zwraca**: wartość True, jeśli etykietowanie jest obowiązkowy, wartość false.
  
### <a name="label"></a>Etykieta
Pobierz domyślny etykieta poufności.

  
**Zwraca**: sensitivy etykiety domyślne, jeśli istnieje nullptr Jeśli nie ustawiono etykiety domyślnej.
  
### <a name="policyhandler"></a>PolicyHandler
Utwórz procedurę obsługi zasad wykonywanie zasadach powiązanych z funkcji na stan wykonywania pliku.

Parametry:  
* **contentIdentifier**: unikatowy ciąg, który identyfikuje plik {zawartości}. przykład dla pliku: "C:\mip-sdk-for-cpp\files\audit.docx" [ścieżka: nazwa_pliku] przykład wiadomości e-mail: "RE: inspekcji design:user1@contoso.com" [podmiotu: nadawcy]



  
**Zwraca**: program obsługi zasad.