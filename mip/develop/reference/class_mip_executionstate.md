---
title: Klasa mip ExecutionState
description: Odwołanie do klasy mip ExecutionState
author: BryanLa
ms.service: information-protection
ms.topic: reference
ms.date: 09/27/2018
ms.author: bryanla
ms.openlocfilehash: 976bca60f3f494a0fbf196e6512b00bdcdd63992
ms.sourcegitcommit: 1cf14852cd14ea91ac964fb03a901238455ffdff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/28/2018
ms.locfileid: "47446315"
---
# <a name="class-mipexecutionstate"></a>Klasa mip::ExecutionState 
Interfejs dla wszystkich stanów, które są wymagane do wykonania z aparatem.
Klienci powinny wywoływać tylko metody, które można uzyskać stanu, który jest potrzebny. W związku z tym w w celu zwiększenia wydajności klientów można implementować ten interfejs w taki sposób, że odpowiadający mu stan jest dynamicznie obliczana zamiast z góry obliczeń.
  
## <a name="summary"></a>Podsumowanie
 Elementy członkowskie                        | Opisy                                
--------------------------------|---------------------------------------------
 publiczne std::string GetNewLabelId() const  |  Pobiera identyfikator etykiety ważności, który ma zostać zastosowany do dokumentu.
 publiczne ActionSource GetNewLabelActionSource() const  |  Pobiera źródło dla nowej akcji etykietę.
 publiczne std::string GetContentIdentifier() const  |  Pobiera identyfikator zawartości, który opisuje dokumentu. przykład dla pliku: [ścieżka] przykład wiadomości e-mail: [podmiotu: nadawcy].
 publiczne ContentState GetContentState() const  |  Pobiera stan zawartości, gdy aplikacja prowadzi interakcję z nią.
publiczne std::pair < wartość logiczna, std::string > IsDowngradeJustified() const  |  Jeśli podano uzasadnienie, aby obniżyć istniejącej etykiety, powinna przekazać implementacji.
 publiczne AssignmentMethod GetNewLabelAssignmentMethod() const  |  Uzyskaj metodę przypisywania nową etykietę.
publiczne std::vector < std::pair < std::string, std::string >> GetNewLabelExtendedProperties() const  |  Zwraca właściwości rozszerzone nową etykietę.
publiczne std::vector < std::pair < std::string, std::string >> GetContentMetadata (const std::vector < std::string > & nazwy, const std::vector < std::string > & namePrefixes) const  |  Pobierz elementy meta-data, od zawartości.
publiczne std::shared_ptr<ProtectionDescriptor> GetProtectionDescriptor() const  |  Pobieranie deskryptora ochrony.
 publiczne ContentFormat GetContentFormat() const  |  Pobiera format zawartości.
 publiczne ActionType GetSupportedActions() const  |  Pobiera maskowanego wyliczenia, zawierająca opis wszystkich typów obsługiwanych akcji.
publiczne wirtualne std::map < std::string, std::shared_ptr<ClassificationResult>> GetClassificationResults (const std::vector < std::string > &) const  |  Zwraca mapę wyniki klasyfikacji.
  
## <a name="members"></a>Elementy członkowskie
  
### <a name="getnewlabelid"></a>GetNewLabelId
Pobiera identyfikator etykiety ważności, który ma zostać zastosowany do dokumentu.

  
**Zwraca**: identyfikator etykiety ważności mają być stosowane do zawartości if else istnieje pozostawić puste, aby usunąć etykietę.
  
### <a name="getnewlabelactionsource"></a>GetNewLabelActionSource
Pobiera źródło dla nowej akcji etykietę.

  
**Zwraca**: źródło akcji.
  
### <a name="getcontentidentifier"></a>GetContentIdentifier
Pobiera identyfikator zawartości, który opisuje dokumentu. przykład dla pliku: [ścieżka] przykład wiadomości e-mail: [podmiotu: nadawcy].

  
**Zwraca**: Identyfikator zawartości, które mają być stosowane do zawartości.
Ta wartość jest używana przez przeprowadzanie inspekcji jako zrozumiałą dla użytkownika opis zawartości
  
### <a name="getcontentstate"></a>GetContentState
Pobiera stan zawartości, gdy aplikacja prowadzi interakcję z nią.

  
**Zwraca**: stan danych zawartości
  
### <a name="isdowngradejustified"></a>IsDowngradeJustified
Jeśli podano uzasadnienie, aby obniżyć istniejącej etykiety, powinna przekazać implementacji.

  
**Zwraca**: True, jeśli justifiedalong o wartości FAŁSZ messageelse uzasadnienie obniżenia poziomu 
  
**Zobacz też**: [mip::JustifyAction](class_mip_justifyaction.md)
  
### <a name="getnewlabelassignmentmethod"></a>GetNewLabelAssignmentMethod
Uzyskaj metodę przypisywania nową etykietę.

  
**Zwraca**: metody przypisywania STANDARD, UPRZYWILEJOWANY, AUTO. 
  
**Zobacz też**: mip::AssignmentMethod
  
### <a name="getnewlabelextendedproperties"></a>GetNewLabelExtendedProperties
Zwraca właściwości rozszerzone nową etykietę.

  
**Zwraca**: rozszerzone właściwości, które są stosowane do zawartości.
  
### <a name="getcontentmetadata"></a>GetContentMetadata
Pobierz elementy meta-data, od zawartości.

  
**Zwraca**: metadane stosowane do zawartości. Każdy element metadanych jest pary nazw i wartości.
  
### <a name="protectiondescriptor"></a>ProtectionDescriptor
Pobieranie deskryptora ochrony.

  
**Zwraca**: deskryptor ochrony
  
### <a name="getcontentformat"></a>GetContentFormat
Pobiera format zawartości.

  
**Zwraca**: domyślne, adres E-mail 
  
**Zobacz też**: mip::ContentFormat
  
### <a name="actiontype"></a>ActionType
Pobiera maskowanego wyliczenia, zawierająca opis wszystkich typów obsługiwanych akcji.

  
**Zwraca**: maskowanego wyliczenia, zawierająca opis wszystkich typów obsługiwanych akcji.
ActionType::Justify muszą być obsługiwane. Jeśli zmiany zasad i etykiet wymaga uzasadnienia, akcja uzasadnienie zawsze zostaną zwrócone.
  
### <a name="classificationresult"></a>ClassificationResult
Zwraca mapę wyniki klasyfikacji.

Parametry:  
* **classificationId**: Lista klasyfikacji identyfikatorów. 



  
**Zwraca**: lista wyników klasyfikacji.