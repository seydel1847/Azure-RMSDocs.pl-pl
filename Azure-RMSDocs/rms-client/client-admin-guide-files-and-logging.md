---
title: "Pliki i dzienniki użycia klienta usługi Azure Information Protection"
description: "Informacje na temat plików i dzienników użycia klienta usługi Azure Information Protection dla systemu Windows."
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 05/23/2017
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: 5a34ab85-773f-4782-ba09-c321cddf5bc0
ms.reviewer: eymanor
ms.suite: ems
ms.openlocfilehash: bf695772d545daca602903e156903da2aadaae7a
ms.sourcegitcommit: 04eb4990e2bf0004684221592cb93df35e6acebe
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/30/2017
---
# Pliki i dzienniki użycia klienta usługi Azure Information Protection
<a id="azure-information-protection-client-files-and-client-usage-logging" class="xliff"></a>

>*Dotyczy: usługi zarządzania prawami dostępu w usłudze Active Directory, Azure Information Protection, Windows 10, Windows 8.1, Windows 8, Windows 7 z dodatkiem SP1, Windows Server 2016, Windows Server 2012 R2, Windows Server 2012*

Po zainstalowaniu klienta usługi Azure Information Protection przydatna może być informacja o lokalizacji plików. Może też zajść potrzeba monitorowania sposobu korzystania z klienta.

## Lokalizacja plików klienta usługi Azure Information Protection
<a id="file-locations-for-the-azure-information-protection-client" class="xliff"></a>

Pliki klienta:   

- Dla 64-bitowych systemów operacyjnych: **\ProgramFiles (x86)\Microsoft Azure Information Protection**

- Dla 32-bitowych systemów operacyjnych: **\Program Files\Microsoft Azure Information Protection**

Pliki dziennika klienta i plik obecnie zainstalowanych zasad:

- Dla 64- i 32-bitowych systemów operacyjnych: **%localappdata%\Microsoft\MSIP**

## Dzienniki użycia klienta usługi Azure Information Protection
<a id="usage-logging-for-the-azure-information-protection-client" class="xliff"></a>

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
    
- Etykieta przed akcją i po niej 
    
- Ochrona przed akcją i po niej
    
- Uzasadnienie użytkownika (jeśli ma zastosowanie)
    

Aby uzyskać informacje na temat dzienników użycia usługi Azure Rights Management, zobacz artykuł [Rejestrowanie i analizowanie użycia usługi Azure Rights Management](../deploy-use/log-analyze-usage.md)



## Następne kroki
<a id="next-steps" class="xliff"></a>
Po zidentyfikowaniu wszystkich plików dziennika skojarzonych z klientem usługi Azure Information Protection zapoznaj się z poniższymi informacjami dodatkowymi przydatnymi przy obsłudze tego klienta:

- [Dostosowania](client-admin-guide-customizations.md)

- [Śledzenie dokumentów](client-admin-guide-document-tracking.md)

- [Obsługiwane typy plików](client-admin-guide-file-types.md)

- [Polecenia programu PowerShell](client-admin-guide-powershell.md)

[!INCLUDE[Commenting house rules](../includes/houserules.md)]
