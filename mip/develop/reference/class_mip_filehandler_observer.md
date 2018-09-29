---
title: Klasa mip FileHandler obserwatora
description: Odwołanie do klasy mip FileHandler obserwatora
author: BryanLa
ms.service: information-protection
ms.topic: reference
ms.date: 09/27/2018
ms.author: bryanla
ms.openlocfilehash: a587107afc2b8963d64c31ad47af81761bf2b9f8
ms.sourcegitcommit: 1cf14852cd14ea91ac964fb03a901238455ffdff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/28/2018
ms.locfileid: "47446186"
---
# <a name="class-mipfilehandlerobserver"></a>Klasa mip::FileHandler::Observer 
[Obserwator](class_mip_filehandler_observer.md) interfejsu, aby klienci mogli odbierać powiadomienia zdarzenia związane z obsługi plików.
Wszystkie błędy dziedziczyć [mip::Error](class_mip_error.md). Klient nie powinien wywoływać aparat Wstecz w wątku, który wywołuje obserwatora.
  
## <a name="summary"></a>Podsumowanie
 Elementy członkowskie                        | Opisy                                
--------------------------------|---------------------------------------------
publiczne wirtualne OnCreateFileHandlerSuccess void (const std::shared_ptr<FileHandler>& fileHandler, const std::shared_ptr<void>& kontekstu)  |  Wywołuje się, gdy program obsługi został utworzony pomyślnie.
publiczne wirtualne OnCreateFileHandlerFailure void (const std::exception_ptr & błąd, const std::shared_ptr<void>& kontekstu)  |  Wywołuje się, gdy nie można utworzyć programu obsługi.
publiczne wirtualne OnGetLabelSuccess void (const std::shared_ptr<ContentLabel>& etykiety, const std::shared_ptr<void>& kontekstu)  |  Wywołuje się, gdy etykiety są pomyślnie pobrane.
publiczne wirtualne OnGetLabelFailure void (const std::exception_ptr & błąd, const std::shared_ptr<void>& kontekstu)  |  Metoda wywoływana podczas pobierania etykiety nie powiodło się.
publiczne wirtualne OnGetProtectionSuccess void (const std::shared_ptr<ProtectionHandler>& protectionHandler, const std::shared_ptr<void>& kontekstu)  |  Wywołuje się, gdy zasady ochrony jest pomyślnie pobrane.
publiczne wirtualne OnGetProtectionFailure void (const std::exception_ptr & błąd, const std::shared_ptr<void>& kontekstu)  |  Wywołuje się, gdy zasady ochrony pobieranie nie powiodło się.
publiczne wirtualne OnCommitSuccess void (została zatwierdzona, bool const std::shared_ptr<void>& kontekstu)  |  Wywoływane, gdy zatwierdzania zmian do pliku zakończyły się pomyślnie.
publiczne wirtualne OnCommitFailure void (const std::exception_ptr & błąd, const std::shared_ptr<void>& kontekstu)  |  Wywołuje się, gdy zatwierdzania zmian do pliku nie powiodło się.
  
## <a name="members"></a>Elementy członkowskie
  
### <a name="oncreatefilehandlersuccess"></a>OnCreateFileHandlerSuccess
Wywołuje się, gdy program obsługi został utworzony pomyślnie.
  
### <a name="oncreatefilehandlerfailure"></a>OnCreateFileHandlerFailure
Wywołuje się, gdy nie można utworzyć programu obsługi.
  
### <a name="ongetlabelsuccess"></a>OnGetLabelSuccess
Wywołuje się, gdy etykiety są pomyślnie pobrane.
  
### <a name="ongetlabelfailure"></a>OnGetLabelFailure
Metoda wywoływana podczas pobierania etykiety nie powiodło się.
  
### <a name="ongetprotectionsuccess"></a>OnGetProtectionSuccess
Wywołuje się, gdy zasady ochrony jest pomyślnie pobrane.
  
### <a name="ongetprotectionfailure"></a>OnGetProtectionFailure
Wywołuje się, gdy zasady ochrony pobieranie nie powiodło się.
  
### <a name="oncommitsuccess"></a>OnCommitSuccess
Wywoływane, gdy zatwierdzania zmian do pliku zakończyły się pomyślnie.
  
### <a name="oncommitfailure"></a>OnCommitFailure
Wywołuje się, gdy zatwierdzania zmian do pliku nie powiodło się.