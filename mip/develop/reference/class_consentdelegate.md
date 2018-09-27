# <a name="class-consentdelegate"></a>Klasa ConsentDelegate 
Delegat o zgodę operacji związanych z.
Ten delegat jest implementowany przez aplikację kliencką, aby dowiedzieć się, kiedy powiadomienie żądanie zgody powinna być wyświetlana użytkownikowi.
  
## <a name="summary"></a>Podsumowanie
 Elementy członkowskie                        | Opisy                                
--------------------------------|---------------------------------------------
 publiczne GetUserConsent(const std::string& url) zgody  |  Wywołuje się, gdy zestaw SDK wymaga zgody użytkownika, aby nawiązać połączenie z punktu końcowego usługi.
  
## <a name="members"></a>Elementy członkowskie
  
### <a name="consent"></a>Wyrażenie zgody
Wywołuje się, gdy zestaw SDK wymaga zgody użytkownika, aby nawiązać połączenie z punktu końcowego usługi.

Parametry:  
* **adres URL**: adres URL, dla której zestaw SDK wymaga zgody użytkownika



  
**Zwraca**: wyliczenia zgody użytkownika decyzji.
Gdy zestaw SDK zażąda zgody użytkownika przy użyciu tej metody, aplikacja kliencka powinni przedstawić potwierdzenie odpowiedniego adresu URL dla użytkownika. Aplikacje klienckie należy podać kilka sposobów uzyskiwania zgody użytkownika i ponownie odpowiednie wyliczenia zgody, który odpowiada decyzja użytkownika.