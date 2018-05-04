# <a name="class-mipprotectionprofile"></a>Klasa mip::ProtectionProfile 
[ProtectionProfile](#classmip_1_1_protection_profile) jest klasy głównym dla operacji ochrony.
Aplikacja, należy utworzyć [ProtectionProfile](#classmip_1_1_protection_profile) przed wykonaniem jakichkolwiek działań ochrony
  
## <a name="summary"></a>Podsumowanie
 Elementy członkowskie                        | Opisy                                
--------------------------------|---------------------------------------------
Ustawienia publicznego const & GetSettings() const  |  Pobiera ustawienia używane przez [ProtectionProfile](#classmip_1_1_protection_profile) podczas jego inicjowania i przez cały cykl jej życia.
publiczny ClearCaches() void  |  Usuwa pamięci podręcznych (np. baz danych zgody, itp.)
  
## <a name="members"></a>Elementy członkowskie
  
### <a name="settings"></a>Ustawienia
Pobiera ustawienia używane przez [ProtectionProfile](#classmip_1_1_protection_profile) podczas jego inicjowania i przez cały cykl jej życia.
  
#### <a name="returns"></a>Zwraca
[Ustawienia](#classmip_1_1_protection_profile_1_1_settings) używane przez [ProtectionProfile](#classmip_1_1_protection_profile) podczas jego inicjowania i w całym cyklu eksploatacji
  
### <a name="clearcaches"></a>ClearCaches
Usuwa pamięci podręcznych (np. baz danych zgody, itp.) Przydatna do debugowania testowania