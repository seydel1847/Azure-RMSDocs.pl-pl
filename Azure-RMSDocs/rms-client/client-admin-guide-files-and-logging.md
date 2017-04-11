---
title: "Pliki i dzienniki użycia klienta usługi Azure Information Protection"
description: "Informacje na temat plików i dzienników użycia klienta usługi Azure Information Protection dla systemu Windows."
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 02/08/2017
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: 5a34ab85-773f-4782-ba09-c321cddf5bc0
ms.reviewer: eymanor
ms.suite: ems
ms.openlocfilehash: 78c355acd1bc87347ef2d4b02ffbb24f2c08bc70
ms.sourcegitcommit: 31e128cc1b917bf767987f0b2144b7f3b6288f2e
translationtype: HT
---
# <a name="azure-information-protection-client-files-and-client-usage-logging"></a>Pliki i dzienniki użycia klienta usługi Azure Information Protection

>*Dotyczy: usługi Active Directory Rights Management, Azure Information Protection, Windows 10, Windows 8.1, Windows 8, Windows 7 z dodatkiem SP1*

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
    
- Etykieta przed akcją i po niej 
    
- Ochrona przed akcją i po niej
    
- Uzasadnienie użytkownika (jeśli ma zastosowanie)
    

Aby uzyskać informacje na temat dzienników użycia usługi Azure Rights Management, zobacz artykuł [Rejestrowanie i analizowanie użycia usługi Azure Rights Management](../deploy-use/log-analyze-usage.md)



## <a name="next-steps"></a>Następne kroki
Po zidentyfikowaniu wszystkich plików dziennika skojarzonych z klientem usługi Azure Information Protection zapoznaj się z poniższymi informacjami dodatkowymi przydatnymi przy obsłudze tego klienta:


- [Śledzenie dokumentów](client-admin-guide-document-tracking.md)

- [Obsługiwane typy plików](client-admin-guide-file-types.md)

- [Polecenia programu PowerShell](client-admin-guide-powershell.md)

[!INCLUDE[Commenting house rules](../includes/houserules.md)]
