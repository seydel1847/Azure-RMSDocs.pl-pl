# <a name="class-miprecommendlabelaction"></a>Klasa mip::RecommendLabelAction 
Zaleca się etykieta działania jest przeznaczona do zasugerować etykiet do użytkowników. Pominięcie tego wywołania po użytkownik ignoruje zalecana etykieta powinna być podejmowana za pośrednictwem obsługiwanych akcji dla stanu wykonywania.
  
## <a name="summary"></a>Podsumowanie
 Elementy członkowskie                        | Opisy                                
--------------------------------|---------------------------------------------
 publiczne std::string const & GetLabelId() const  |  Pobierz etykietę identyfikator sugerowane.
 publiczne wartości GetType() obiektu ActionType const  |  Pobierz typ [akcji](class_mip_action.md).
  
## <a name="members"></a>Elementy członkowskie
  
### <a name="getlabelid"></a>GetLabelId
Pobierz etykietę identyfikator sugerowane.

  
**Zwraca**: Etykieta identyfikatora.
  
### <a name="actiontype"></a>ActionType
Pobierz typ [akcji](class_mip_action.md).

  
**Zwraca**: ActionType typu pochodnego akcji mogą być rzutowane tej klasy bazowej.