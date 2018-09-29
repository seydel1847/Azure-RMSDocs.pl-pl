---
title: Klasa mip FileProfile
description: Odwołanie do klasy mip FileProfile
author: BryanLa
ms.service: information-protection
ms.topic: reference
ms.date: 09/27/2018
ms.author: bryanla
ms.openlocfilehash: f317f1eff0266db1da211e164ec5e427ba7ce17d
ms.sourcegitcommit: 1cf14852cd14ea91ac964fb03a901238455ffdff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/28/2018
ms.locfileid: "47445890"
---
# <a name="class-mipfileprofile"></a>Klasa mip::FileProfile 
[FileProfile](class_mip_fileprofile.md) klasy jest klasą głównego dla przy użyciu operacji Microsoft Information Protection.
Typowa aplikacja musi jedynie jeden profil.
  
## <a name="summary"></a>Podsumowanie
 Elementy członkowskie                        | Opisy                                
--------------------------------|---------------------------------------------
 publiczne ustawienia const & GetSettings() const  |  Zwraca ustawień profilu.
publiczne ListEnginesAsync void (const std::shared_ptr<void>& kontekstu)  |  Rozpoczyna się listy aparatów operacji.
publiczne UnloadEngineAsync void (const std::string & identyfikator, const std::shared_ptr<void>& kontekstu)  |  Rozpoczyna się zwalnianie aparatu plików o podanym identyfikatorze.
publiczne AddEngineAsync void (const FileEngine::Settings & Ustawienia, const std::shared_ptr<void>& kontekstu)  |  Rozpoczyna się dodanie nowego aparatu pliku do tego profilu.
publiczne DeleteEngineAsync void (const std::string & identyfikator, const std::shared_ptr<void>& kontekstu)  |  Rozpoczyna się usuwanie aparatu plików o podanym identyfikatorze. Zostaną usunięte wszystkie dane dla danego profilu.
  
## <a name="members"></a>Elementy członkowskie
  
### <a name="settings"></a>Ustawienia
Zwraca ustawień profilu.
  
### <a name="listenginesasync"></a>ListEnginesAsync
Rozpoczyna się listy aparatów operacji.
[FileProfile::Observer](class_mip_fileprofile_observer.md) zostanie wywołana na powodzenie lub niepowodzenie.
  
### <a name="unloadengineasync"></a>UnloadEngineAsync
Rozpoczyna się zwalnianie aparatu plików o podanym identyfikatorze.
[FileProfile::Observer](class_mip_fileprofile_observer.md) zostanie wywołana na powodzenie lub niepowodzenie.
  
### <a name="addengineasync"></a>AddEngineAsync
Rozpoczyna się dodanie nowego aparatu pliku do tego profilu.
[FileProfile::Observer](class_mip_fileprofile_observer.md) zostanie wywołana na powodzenie lub niepowodzenie.
  
### <a name="deleteengineasync"></a>DeleteEngineAsync
Rozpoczyna się usuwanie aparatu plików o podanym identyfikatorze. Zostaną usunięte wszystkie dane dla danego profilu.
[FileProfile::Observer](class_mip_fileprofile_observer.md) zostanie wywołana na powodzenie lub niepowodzenie.