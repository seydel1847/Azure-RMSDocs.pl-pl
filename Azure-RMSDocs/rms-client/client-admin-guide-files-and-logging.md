---
title: Pliki i dzienniki użycia klienta usługi Azure Information Protection
description: Informacje na temat plików i dzienników użycia klienta usługi Azure Information Protection dla systemu Windows.
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 08/06/2018
ms.topic: conceptual
ms.service: information-protection
ms.assetid: 5a34ab85-773f-4782-ba09-c321cddf5bc0
ms.reviewer: eymanor
ms.suite: ems
ms.openlocfilehash: 7e72aa9af0d248f54880f8b5bb6df0ce75018f2b
ms.sourcegitcommit: bf58c5d94eb44a043f53711fbdcf19ce503f8aab
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/26/2018
ms.locfileid: "47211228"
---
# <a name="admin-guide-azure-information-protection-client-files-and-client-usage-logging"></a>Podręczniku administratora: Pliki klienta usługi Azure Information Protection i dzienniki użycia klienta

>*Dotyczy: Active Directory Rights Management Services, [usługi Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection), Windows 10, Windows 8.1, Windows 8, Windows 7 z dodatkiem SP1, systemu Windows Server 2016, Windows Server 2012 R2, Windows Server 2012, systemu Windows Server 2008 R2*

Po zainstalowaniu klienta usługi Azure Information Protection przydatna może być informacja o lokalizacji plików. Może też zajść potrzeba monitorowania sposobu korzystania z klienta.

## <a name="file-locations-for-the-azure-information-protection-client"></a>Lokalizacja plików klienta usługi Azure Information Protection

Pliki klienta:   

- Dla 64-bitowych systemów operacyjnych: **\ProgramFiles (x86)\Microsoft Azure Information Protection**

- Dla 32-bitowych systemów operacyjnych: **\Program Files\Microsoft Azure Information Protection**

Pliki dziennika klienta i plik obecnie zainstalowanych zasad:

- Dla 64- i 32-bitowych systemów operacyjnych: **%localappdata%\Microsoft\MSIP**

## <a name="usage-logging-for-the-azure-information-protection-client"></a>Dzienniki użycia klienta usługi Azure Information Protection

Klient rejestruje aktywność użytkownika w lokalnym dzienniku zdarzeń Windows **Dzienniki aplikacji i usług** > **usługi Azure Information Protection**. Zdarzenia obejmują następujące informacje:

- Wersja klienta, identyfikator zasad

- Adresy IP zalogowanego użytkownika

- Nazwa i lokalizacja pliku

- Działanie:

    - Ustawienie etykiety: identyfikator informacji 101
    
    - Ustawienie etykiety (niższej): informacje o identyfikatorze 101
    
    - Ustawienie etykiety (wyższej): informacje o identyfikatorze 101
    
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
    
    - Wartość domyślna
    
- Etykieta przed akcją i po niej 
    
- Ochrona przed akcją i po niej
    
- Uzasadnienie użytkownika (jeśli ma zastosowanie)

- Uprawnienia niestandardowe (jeśli ma zastosowanie), który zawiera [prawa użytkowania według nazwy kodowania](../configure-usage-rights.md#usage-rights-and-descriptions) dla określonych użytkowników, grupy lub organizacje
    
Aby uzyskać informacje na temat rejestrowania użycia usługi ochrony, zobacz [rejestrowanie i analizowanie użycia usługi Azure Rights Management](../log-analyze-usage.md)

Aby uzyskać informacje na temat rejestrowania użycia usługi ochrony, zobacz [rejestrowanie i analizowanie użycia usługi Azure Rights Management](../log-analyze-usage.md)

## <a name="next-steps"></a>Kolejne kroki
Po zidentyfikowaniu wszystkich plików dziennika skojarzonych z klientem usługi Azure Information Protection zapoznaj się z poniższymi informacjami dodatkowymi przydatnymi przy obsłudze tego klienta:

- [Dostosowania](client-admin-guide-customizations.md)

- [Śledzenie dokumentów](client-admin-guide-document-tracking.md)

- [Obsługiwane typy plików](client-admin-guide-file-types.md)

- [Polecenia programu PowerShell](client-admin-guide-powershell.md)

