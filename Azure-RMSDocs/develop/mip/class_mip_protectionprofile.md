# <a name="class-mipprotectionprofile"></a>Klasa mip::ProtectionProfile 
[ProtectionProfile](class_mip_protectionprofile.md) jest klasy głównym dla operacji ochrony.
Aplikacja, należy utworzyć [ProtectionProfile](class_mip_protectionprofile.md) przed wykonaniem jakichkolwiek działań ochrony
  
## <a name="summary"></a>Podsumowanie
 Elementy członkowskie                        | Opisy                                
--------------------------------|---------------------------------------------
 Ustawienia publicznego const & GetSettings() const  |  Pobiera ustawienia używane przez [ProtectionProfile](class_mip_protectionprofile.md) podczas jego inicjowania i przez cały cykl jej życia.
 publiczny ClearCaches() void  |  Usuwa pamięci podręcznych (np. baz danych zgody, itp.)
  
## <a name="members"></a>Elementy członkowskie
  
### <a name="settings"></a>Ustawienia
Pobiera ustawienia używane przez [ProtectionProfile](class_mip_protectionprofile.md) podczas jego inicjowania i przez cały cykl jej życia.

  
**Zwraca**: [ustawienia](class_mip_protectionprofile_settings.md) używane przez [ProtectionProfile](class_mip_protectionprofile.md) podczas jego inicjowania i w całym cyklu eksploatacji
  
### <a name="clearcaches"></a>ClearCaches
Usuwa pamięci podręcznych (np. baz danych zgody, itp.) Przydatna do debugowania testowania