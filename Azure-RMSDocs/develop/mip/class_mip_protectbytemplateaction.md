# <a name="class-mipprotectbytemplateaction"></a>Klasa mip::ProtectByTemplateAction 
Klasy akcji, która określa dodawania ochrony za pomocą szablonu do dokumentu.
  
## <a name="summary"></a>Podsumowanie
 Elementy członkowskie                        | Opisy                                
--------------------------------|---------------------------------------------
 publiczne std::string const & GetTemplateId() const  |  Uzyskaj identyfikator szablonu ochrony, które są skojarzone z akcją.
 publiczne wartości GetType() obiektu ActionType const  |  Pobierz typ [akcji](class_mip_action.md).
  
## <a name="members"></a>Elementy członkowskie
  
### <a name="gettemplateid"></a>GetTemplateId
Uzyskaj identyfikator szablonu ochrony, które są skojarzone z akcją.

  
**Zwraca**: ciąg zawierający identyfikator szablonu ochrony.
  
### <a name="actiontype"></a>ActionType
Pobierz typ [akcji](class_mip_action.md).

  
**Zwraca**: ActionType typu pochodnego akcji mogą być rzutowane tej klasy bazowej.