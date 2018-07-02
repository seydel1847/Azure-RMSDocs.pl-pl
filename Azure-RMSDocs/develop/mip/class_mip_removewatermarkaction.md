# <a name="class-mipremovewatermarkaction"></a>Klasa mip::RemoveWatermarkAction 
Klasa akcji, który określa, usuwając znaki wodne z dokumentu.
  
## <a name="summary"></a>Podsumowanie
 Elementy członkowskie                        | Opisy                                
--------------------------------|---------------------------------------------
publiczne std::vector const < std::string > & GetUIElementNames()  |  Pobiera listę nazw, które powinny być używane, aby znaleźć elementy interfejsu użytkownika, które powinny zostać usunięte.
 publiczne wartości GetType() obiektu ActionType const  |  Pobierz typ [akcji](class_mip_action.md).
  
## <a name="members"></a>Elementy członkowskie
  
### <a name="getuielementnames"></a>GetUIElementNames
Pobiera listę nazw, które powinny być używane, aby znaleźć elementy interfejsu użytkownika, które powinny zostać usunięte.

  
**Zwraca**: Lista nazw elementów interfejsu użytkownika.
  
### <a name="actiontype"></a>ActionType
Pobierz typ [akcji](class_mip_action.md).

  
**Zwraca**: ActionType typu pochodnego akcji mogą być rzutowane tej klasy bazowej.