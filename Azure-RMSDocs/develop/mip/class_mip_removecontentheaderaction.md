# <a name="class-mipremovecontentheaderaction"></a>Klasa mip::RemoveContentHeaderAction 
Klasy akcji, która określa usunięcie nagłówka zawartości z dokumentu.
  
## <a name="summary"></a>Podsumowanie
 Elementy członkowskie                        | Opisy                                
--------------------------------|---------------------------------------------
publiczny std::vector const < std::string > & GetUIElementNames()  |  Pobiera listę nazw, które powinny być używane, aby znaleźć elementy interfejsu użytkownika, które powinny zostać usunięte.
publicznych ActionType GetType() const  |  Wybrany typ [akcji](#classmip_1_1_action).
  
## <a name="members"></a>Elementy członkowskie
  
### <a name="getuielementnames"></a>GetUIElementNames
Pobiera listę nazw, które powinny być używane, aby znaleźć elementy interfejsu użytkownika, które powinny zostać usunięte.
  
#### <a name="returns"></a>Zwraca
Lista nazw elementów interfejsu użytkownika.
  
### <a name="actiontype"></a>ActionType
Wybrany typ [akcji](#classmip_1_1_action).
  
#### <a name="returns"></a>Zwraca
Typ pochodny akcji ActionType ta klasa podstawowa mogą być rzutowane na.