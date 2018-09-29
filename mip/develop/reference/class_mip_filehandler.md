---
title: Klasa mip FileHandler
description: Odwołanie do klasy mip FileHandler
author: BryanLa
ms.service: information-protection
ms.topic: reference
ms.date: 09/27/2018
ms.author: bryanla
ms.openlocfilehash: efae18bdc10f8878f255f35c608a50482a29887b
ms.sourcegitcommit: 1cf14852cd14ea91ac964fb03a901238455ffdff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/28/2018
ms.locfileid: "47446128"
---
# <a name="class-mipfilehandler"></a>Klasa mip::FileHandler 
Interfejs dla wszystkich plików, funkcje obsługi.
  
## <a name="summary"></a>Podsumowanie
 Elementy członkowskie                        | Opisy                                
--------------------------------|---------------------------------------------
publiczne GetLabelAsync void (const std::shared_ptr<void>& kontekstu)  |  Rozpoczyna się podczas pobierania etykiety ważności z pliku.
publiczne GetProtectionAsync void (const std::shared_ptr<void>& kontekstu)  |  Zostanie uruchomiony, pobieranie zasad ochrony z pliku.
 publiczne SetLabel void (const std::string & etykiety, const LabelingOptions & labelingOptions)  |  Ustawia etykieta poufności do pliku.
 publiczne DeleteLabel void (const LabelingOptions & labelingOptions)  |  Usunięcie etykiety ważności z pliku.
publiczne SetProtection void (const std::shared_ptr<ProtectionDescriptor>& protectionDescriptor)  |  Ustawia uprawnienia niestandardowe lub oparte na szablonach (zgodnie z protectionDescriptor -> GetProtectionType) do pliku.
 publiczne RemoveProtection() void  |  Usuwa ochronę z pliku. Jeśli ten plik został oznaczony, etykieta zostaną utracone.
publiczne CommitAsync void (const std::string & outputFilePath, const std::shared_ptr<void>& kontekstu) | Zapisuje zmiany w pliku określonym przez \|outputFilePath\ |  parametr.
publiczne CommitAsync void (const std::shared_ptr<Stream>& outputStream, const std::shared_ptr<void>& kontekstu) | Zapisuje zmiany w strumieniu określonego przez \|outputStream\ |  parametr.
 publiczne NotifyCommitSuccessful void (const std::string & contentIdentifier)  |  Wywoływana, gdy zmiany zostały zatwierdzone na dysku.
 publiczne std::string GetOutputFileName()  |  Oblicza rozszerzenia na podstawie oryginalna nazwa pliku i zmiany narastająco i nazwa pliku wyjściowego.
  
## <a name="members"></a>Elementy członkowskie
  
### <a name="getlabelasync"></a>GetLabelAsync
Rozpoczyna się podczas pobierania etykiety ważności z pliku.
[FileHandler::Observer](class_mip_filehandler_observer.md) zostanie wywołana na powodzenie lub niepowodzenie.

Parametry:  
* **kontekst**: kontekst klienta, który zostanie przekazany obraz nieprzezroczysty do obserwatora.


  
### <a name="getprotectionasync"></a>GetProtectionAsync
Zostanie uruchomiony, pobieranie zasad ochrony z pliku.
[FileHandler::Observer](class_mip_filehandler_observer.md) zostanie wywołana na powodzenie lub niepowodzenie.

Parametry:  
* **kontekst**: kontekst klienta, który zostanie przekazany obraz nieprzezroczysty do obserwatora.


  
### <a name="setlabel"></a>SetLabel
Ustawia etykieta poufności do pliku.
Zmiany nie będą zapisywane do pliku, do momentu CommitAsync jest wywoływana. Uprzywilejowany i metoda automatycznie umożliwia interfejsu API zastąpić wszelkie istniejące zgłasza etykiety [JustificationRequiredError](class_mip_justificationrequirederror.md) kiedy ustawienie etykiety wymaga operację, aby mieć uzasadnienie (za pośrednictwem parametru labelingOptions).
  
### <a name="deletelabel"></a>DeleteLabel
Usunięcie etykiety ważności z pliku.
Zmiany nie będą zapisywane do pliku, do momentu CommitAsync jest wywoływana. Uprzywilejowany i metoda automatycznie umożliwia interfejsu API zastąpić wszelkie istniejące zgłasza etykiety [JustificationRequiredError](class_mip_justificationrequirederror.md) kiedy ustawienie etykiety wymaga operację, aby mieć uzasadnienie (za pośrednictwem parametru labelingOptions).
  
### <a name="setprotection"></a>SetProtection
Ustawia uprawnienia niestandardowe lub oparte na szablonach (zgodnie z protectionDescriptor -> GetProtectionType) do pliku.
Zmiany nie będą zapisywane do pliku, do momentu CommitAsync jest wywoływana.
  
### <a name="removeprotection"></a>RemoveProtection
Usuwa ochronę z pliku. Jeśli ten plik został oznaczony, etykieta zostaną utracone.
Zmiany nie będą zapisywane do pliku, do momentu CommitAsync jest wywoływana.
  
### <a name="commitasync"></a>CommitAsync
Zapisuje zmiany w pliku określonym przez | outputFilePath | parametr.
[FileHandler::Observer](class_mip_filehandler_observer.md) zostanie wywołana na powodzenie lub niepowodzenie.
  
### <a name="commitasync"></a>CommitAsync
Zapisuje zmiany w strumieniu określonego przez | outputStream | parametr.
[FileHandler::Observer](class_mip_filehandler_observer.md) zostanie wywołana na powodzenie lub niepowodzenie.
  
### <a name="notifycommitsuccessful"></a>NotifyCommitSuccessful
Wywoływana, gdy zmiany zostały zatwierdzone na dysku.

Parametry:  
* **contentIdentifier**: przykład dla pliku: "C:\mip-sdk-for-cpp\files\audit.docx" [path] na przykład wiadomości e-mail: "RE: inspekcji design:user1@contoso.com" [podmiotu: nadawcy] 


Uruchamia zdarzenie inspekcji
  
### <a name="getoutputfilename"></a>GetOutputFileName
Oblicza rozszerzenia na podstawie oryginalna nazwa pliku i zmiany narastająco i nazwa pliku wyjściowego.