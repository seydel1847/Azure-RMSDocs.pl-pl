# <a name="class-mipremovewatermarkaction"></a>Klasa mip::RemoveWatermarkAction 
Klasy akcji, która określa usuwanie znaki wodne z dokumentu.
  
## <a name="summary"></a>Podsumowanie
 Elementy członkowskie                        | Opisy                                
--------------------------------|---------------------------------------------
publiczny std::vector const < std::string > & GetUIElementNames()  |  Pobiera listę nazw, które powinny być używane, aby znaleźć elementy interfejsu użytkownika, które powinny zostać usunięte.
 publicznych ActionType GetType() const  |  Wybrany typ [akcji](class_mip_action.md).
  
## <a name="members"></a>Elementy członkowskie
  
### <a name="getuielementnames"></a>GetUIElementNames
Pobiera listę nazw, które powinny być używane, aby znaleźć elementy interfejsu użytkownika, które powinny zostać usunięte.

  
**Zwraca**: Lista nazw elementów interfejsu użytkownika.
  
### <a name="actiontype"></a>ActionType
Wybrany typ [akcji](class_mip_action.md).

  
**Zwraca**: ActionType typu pochodnego akcji mogą być rzutowane tej klasy podstawowej.