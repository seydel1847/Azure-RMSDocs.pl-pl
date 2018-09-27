# <a name="class-mipprotectionhandler"></a>Klasa mip::ProtectionHandler 
Wykonuje akcje dotyczące ochrony dla konfiguracji ochrony określonych (czyli użytkowników, prawa, role itp.)
  
## <a name="summary"></a>Podsumowanie
 Elementy członkowskie                        | Opisy                                
--------------------------------|---------------------------------------------
publiczne std::shared_ptr<Stream> CreateProtectedStream (const std::shared_ptr<Stream>& backingStream, contentSize int64_t int64_t contentStartPosition)  |  Utwórz chroniony strumienia, który będzie zezwalał dla operacji szyfrowania i odszyfrowywania zawartości.
 publiczne EncryptBuffer int64_t (int64_t offsetFromStart inputBuffer uint8_t * const, int64_t inputBufferSize, uint8_t * outputBuffer, int64_t outputBufferSize, bool isFinal)  |  Szyfrowanie buforu.
 publiczne DecryptBuffer int64_t (int64_t offsetFromStart inputBuffer uint8_t * const, int64_t inputBufferSize, uint8_t * outputBuffer, int64_t outputBufferSize, bool isFinal)  |  Odszyfrować bufora.
 publiczne GetProtectedContentLength int64_t (int64_t unprotectedLength, bool includesFinalBlock)  |  Oblicza rozmiar zawartości (w bajtach), gdyby były szyfrowane, w tym [ProtectionHandler](class_mip_protectionhandler.md).
 publiczne int64_t GetBlockSize()  |  Pobiera rozmiar bloku (w bajtach) dla trybu szyfrowania używanych przez to [ProtectionHandler](class_mip_protectionhandler.md).
publiczne std::vector < std::string > GetRights() const  |  Pobiera prawa użytkownika tożsamości skojarzonych z tym [ProtectionHandler](class_mip_protectionhandler.md).
 publiczne bool AccessCheck (const std::string & po prawej stronie) const  |  Sprawdza, jeśli program obsługi ochrony udziela użytkownikowi dostępu do określonego prawa.
 publiczne std::string const GetIssuedTo()  |  Pobiera użytkownika skojarzonego z obsługi ochrony.
 publiczne std::string const GetOwner()  |  Pobiera wiadomość e-mail adres właściciela zawartości.
 publiczne bool IsIssuedToOwner()  |  Pobiera informację określającą, czy bieżący użytkownik jest właścicielem zawartości.
publiczne std::shared_ptr<ProtectionDescriptor> GetProtectionDescriptor()  |  Pobiera szczegóły ochrony.
 publiczne std::string const GetContentId()  |  Pobiera unikatowy identyfikator dla dokumentu/zawartości.
 publiczne bool DoesUseDeprecatedAlgorithms()  |  Pobiera informację określającą, czy ochrona program obsługi używa przestarzałego algorytmów kryptograficznych (ECB) zgodności z poprzednimi wersjami.
 publiczne bool IsAuditedExtractAllowed()  |  Pobiera informację określającą, czy program obsługi ochrony udziela prawa "inspekcji wyodrębniania" użytkownika.
publiczne std::vector const < uint8_t > GetSerializedPublishingLicense()  |  Serializowanie [ProtectionHandler](class_mip_protectionhandler.md) w licencji publikowania (PL)
  
## <a name="members"></a>Elementy członkowskie
  
### <a name="stream"></a>Stream
Utwórz chroniony strumienia, który będzie zezwalał dla operacji szyfrowania i odszyfrowywania zawartości.

Parametry:  
* **backingStream**: zapasowego strumienia, z którego ma zostać odczytu/zapisu 


* **contentStartPosition**: od pozycji (w bajtach) w ramach zapasowego strumienia, gdzie rozpoczyna się w chronionej zawartości 


* **contentSize**: rozmiar (w bajtach) chronionej zawartości w ramach tworzenia kopii strumienia



  
**Zwraca**: strumień chronionych
  
### <a name="encryptbuffer"></a>EncryptBuffer
Szyfrowanie buforu.

Parametry:  
* **offsetFromStart**: względne położenie inputBuffer od samego początku treści jako zwykły tekst 


* **inputBuffer**: buforu zawartości jako zwykły tekst, które będą szyfrowane 


* **inputBufferSize**: rozmiar (w bajtach) buforu wejściowego 


* **outputBuffer**: bufor, do którego zostaną skopiowane zaszyfrowaną zawartość 


* **outputBufferSize**: rozmiar (w bajtach) buforu danych wyjściowych 


* **isFinal**: Określa, czy bufor wejściowy zawiera bajtów końcowego jako zwykły tekst



  
**Zwraca**: rzeczywisty rozmiar (w bajtach) zaszyfrowaną zawartość
  
### <a name="decryptbuffer"></a>DecryptBuffer
Odszyfrować bufora.

Parametry:  
* **offsetFromStart**: względne położenie inputBuffer od samego początku zaszyfrowaną zawartość 


* **inputBuffer**: buforu zaszyfrowaną zawartość, która zostanie odszyfrowany 


* **inputBufferSize**: rozmiar (w bajtach) buforu wejściowego 


* **outputBuffer**: bufor, do którego zostaną skopiowane odszyfrowania zawartości 


* **outputBufferSize**: rozmiar (w bajtach) buforu danych wyjściowych 


* **isFinal**: Określa, czy bufor wejściowy zawiera końcowe bajty szyfrowane



  
**Zwraca**: rzeczywisty rozmiar (w bajtach) zawartości odszyfrowany
  
### <a name="getprotectedcontentlength"></a>GetProtectedContentLength
Oblicza rozmiar zawartości (w bajtach), gdyby były szyfrowane, w tym [ProtectionHandler](class_mip_protectionhandler.md).

Parametry:  
* **unprotectedLength**: rozmiar (w bajtach) zawartości niechronione 


* **includesFinalBlock**: Opisuje, czy niechronione zawartości w danym zawiera blok końcowy. Na przykład w trybie szyfrowania CBC4k bloki chronionych-ostateczna to taki sam rozmiar jak bloki niechronione, ale końcowego chronionych bloki są większe niż ich odpowiedniki niechronione.



  
**Zwraca**: rozmiar (w bajtach) chronionej zawartości
  
### <a name="getblocksize"></a>GetBlockSize
Pobiera rozmiar bloku (w bajtach) dla trybu szyfrowania używanych przez to [ProtectionHandler](class_mip_protectionhandler.md).

  
**Zwraca**: Blokuj rozmiar (w bajtach)
  
### <a name="getrights"></a>GetRights
Pobiera prawa użytkownika tożsamości skojarzonych z tym [ProtectionHandler](class_mip_protectionhandler.md).

  
**Zwraca**: przyznano prawa użytkownika
  
### <a name="accesscheck"></a>AccessCheck
Sprawdza, jeśli program obsługi ochrony udziela użytkownikowi dostępu do określonego prawa.

Parametry:  
* **prawy**: po prawej stronie, aby sprawdzić



  
**Zwraca**: Określa, czy program obsługi ochrony udziela użytkownikowi dostępu do określonego prawa
  
### <a name="getissuedto"></a>GetIssuedTo
Pobiera użytkownika skojarzonego z obsługi ochrony.

  
**Zwraca**: użytkownika skojarzonego z obsługi ochrony
  
### <a name="getowner"></a>GetOwner —
Pobiera wiadomość e-mail adres właściciela zawartości.

  
**Zwraca**: wiadomości E-mail adres właściciela zawartości
  
### <a name="isissuedtoowner"></a>IsIssuedToOwner
Pobiera informację określającą, czy bieżący użytkownik jest właścicielem zawartości.

  
**Zwraca**: Określa, czy bieżący użytkownik jest właścicielem zawartości
  
### <a name="protectiondescriptor"></a>ProtectionDescriptor
Pobiera szczegóły ochrony.

  
**Zwraca**: ochrona informacji
  
### <a name="getcontentid"></a>GetContentId
Pobiera unikatowy identyfikator dla dokumentu/zawartości.

  
**Zwraca**: Unikatowy identyfikator zawartości
  
### <a name="doesusedeprecatedalgorithms"></a>DoesUseDeprecatedAlgorithms
Pobiera informację określającą, czy ochrona program obsługi używa przestarzałego algorytmów kryptograficznych (ECB) zgodności z poprzednimi wersjami.

  
**Zwraca**: niezależnie od tego czy program obsługi ochrony używa przestarzałych algorytmów kryptograficznych
  
### <a name="isauditedextractallowed"></a>IsAuditedExtractAllowed
Pobiera informację określającą, czy program obsługi ochrony udziela prawa "inspekcji wyodrębniania" użytkownika.

  
**Zwraca**: Określa, czy program obsługi ochrony przyznaje uprawnienie "inspekcji extract"
  
### <a name="getserializedpublishinglicense"></a>GetSerializedPublishingLicense
Serializowanie [ProtectionHandler](class_mip_protectionhandler.md) w licencji publikowania (PL)

  
**Zwraca**: serializowaną licencją publikowania