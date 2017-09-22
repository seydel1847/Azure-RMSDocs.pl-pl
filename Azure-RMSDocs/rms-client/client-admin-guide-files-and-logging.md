---
title: "Pliki i dzienniki użycia klienta usługi Azure Information Protection"
description: "Informacje na temat plików i dzienników użycia klienta usługi Azure Information Protection dla systemu Windows."
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 09/18/2017
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: 5a34ab85-773f-4782-ba09-c321cddf5bc0
ms.reviewer: eymanor
ms.suite: ems
ms.openlocfilehash: d1802fbd3c659b154d585224a3f7b412b8995e5b
ms.sourcegitcommit: 2f1936753adf8d2fbea780d0a3878afa621daab5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2017
---
# <a name="azure-information-protection-client-files-and-client-usage-logging"></a>Pliki i dzienniki użycia klienta usługi Azure Information Protection

>*Dotyczy: usługi Active Directory Rights Management, Azure Information Protection, Windows 10, Windows 8.1, Windows 8, Windows 7 z dodatkiem SP1, Windows Server 2016, Windows Server 2012 R2, Windows Server 2012, Windows Server 2008 R2*

Po zainstalowaniu klienta usługi Azure Information Protection przydatna może być informacja o lokalizacji plików. Może też zajść potrzeba monitorowania sposobu korzystania z klienta.

## <a name="file-locations-for-the-azure-information-protection-client"></a>Lokalizacja plików klienta usługi Azure Information Protection

Pliki klienta:   

- Dla 64-bitowych systemów operacyjnych: **\ProgramFiles (x86)\Microsoft Azure Information Protection**

- Dla 32-bitowych systemów operacyjnych: **\Program Files\Microsoft Azure Information Protection**

Pliki dziennika klienta i plik obecnie zainstalowanych zasad:

- Dla 64- i 32-bitowych systemów operacyjnych: **%localappdata%\Microsoft\MSIP**

## <a name="usage-logging-for-the-azure-information-protection-client"></a>Dzienniki użycia klienta usługi Azure Information Protection

Klient rejestruje aktywność użytkowników w lokalnym dzienniku zdarzeń **aplikacji i usług** systemu Windows, **Azure Information Protection**. Zdarzenia obejmują następujące informacje:

- Data, wersja klienta, identyfikator zasad

- Nazwa zalogowanego użytkownika, nazwa komputera

- Nazwa i lokalizacja pliku

- Działanie:

    - Ustawienie etykiety: identyfikator informacji 101
    
    - Ustawienie etykiety (niższej): identyfikator informacji 102
    
    - Ustawienie etykiety (wyższej): identyfikator informacji 103
    
    - Usunięcie etykiety: identyfikator informacji 104
   
    - Zalecane: identyfikator informacji 105
    
    - Zastosowanie niestandardowej ochrony: identyfikator informacji 201
    
    - Zastosowanie niestandardowej ochrony: identyfikator informacji 202
    
    - Logowanie (operacyjne): identyfikator informacji 902
    
    - Zasady pobierania (operacyjne): identyfikator informacji 901
    
- Źródło akcji:
    
    - Ręczny 
    
    - Zalecane
    
    - Automatyczny  
    
    - System (dla zasad logowania i pobierania)
    
    - DefaultAutomatic
        
        To **DefaultAutomatic** Akcja źródłowa jest przeznaczona tylko klient w wersji zapoznawczej i odwołuje się do etykiety, którą można ustawić za pomocą **wybierz etykietę domyślną** w zasadach usługi Azure Information Protection.

    
- Etykieta przed akcją i po niej 
    
- Ochrona przed akcją i po niej
    
- Uzasadnienie użytkownika (jeśli ma zastosowanie)
    

Aby uzyskać informacje na temat dzienników użycia usługi Azure Rights Management, zobacz artykuł [Rejestrowanie i analizowanie użycia usługi Azure Rights Management](../deploy-use/log-analyze-usage.md)



## <a name="next-steps"></a>Następne kroki
Po zidentyfikowaniu wszystkich plików dziennika skojarzonych z klientem usługi Azure Information Protection zapoznaj się z poniższymi informacjami dodatkowymi przydatnymi przy obsłudze tego klienta:

- [Dostosowania](client-admin-guide-customizations.md)

- [Śledzenie dokumentów](client-admin-guide-document-tracking.md)

- [Obsługiwane typy plików](client-admin-guide-file-types.md)

- [Polecenia programu PowerShell](client-admin-guide-powershell.md)

[!INCLUDE[Commenting house rules](../includes/houserules.md)]
