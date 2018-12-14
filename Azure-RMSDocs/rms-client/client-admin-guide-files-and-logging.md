---
title: Pliki i dzienniki użycia klienta usługi Azure Information Protection
description: Informacje na temat plików i dzienników użycia klienta usługi Azure Information Protection dla systemu Windows.
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 12/12/2018
ms.topic: conceptual
ms.service: information-protection
ms.assetid: 5a34ab85-773f-4782-ba09-c321cddf5bc0
ms.reviewer: eymanor
ms.suite: ems
ms.openlocfilehash: 2aa0e470d9a2801b695c6b2c9d922836c010690c
ms.sourcegitcommit: 1d2912b4f0f6e8d7596cbf31e2143a783158ab11
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/12/2018
ms.locfileid: "53304914"
---
# <a name="admin-guide-azure-information-protection-client-files-and-client-usage-logging"></a>Podręcznik administratora: Pliki i dzienniki użycia klienta usługi Azure Information Protection

>*Dotyczy: Usługi Active Directory Rights Management Services, [usługi Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection), Windows 10, Windows 8.1, Windows 8, Windows 7 z dodatkiem SP1, systemu Windows Server 2016, Windows Server 2012 R2, systemu Windows Server 2012, Windows Server 2008 R2*

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

- Akcja:

    - Ustawienie etykiety:  Identyfikator informacji 101
    
    - Ustawienie etykiety (niższe):  Identyfikator informacji 101
    
    - Ustawienie etykiety (wyższej): Identyfikator informacji 101
    
    - Usuń etykietę: Identyfikator informacji 104
   
    - Porada zalecane: Identyfikator informacji 105
    
    - Zastosowanie niestandardowej ochrony: Identyfikator informacji 201
    
    - Usunąć ochronę niestandardową: Identyfikator informacji 202
    
    - Zaloguj się w (operacyjne): Identyfikator informacji 902
    
    - Zasady pobierania (operacyjne): Identyfikator informacji 901
    
- Źródło akcji:
    
    - Ręczny 
    
    - Zalecane
    
    - Automatyczny  
    
    - System (dla zasad logowania i pobierania)
    
    - Domyślny
    
- Etykieta przed akcją i po niej 
    
- Ochrona przed akcją i po niej
    
- Uzasadnienie użytkownika (jeśli ma zastosowanie)

- Uprawnienia niestandardowe (jeśli ma zastosowanie), który zawiera [prawa użytkowania według nazwy kodowania](../configure-usage-rights.md#usage-rights-and-descriptions) dla określonych użytkowników, grupy lub organizacje
    
Aby uzyskać informacje na temat rejestrowania użycia usługi ochrony, zobacz [rejestrowanie i analizowanie użycia usługi Azure Rights Management](../log-analyze-usage.md)

## <a name="next-steps"></a>Następne kroki
Po zidentyfikowaniu wszystkich plików dziennika skojarzonych z klientem usługi Azure Information Protection zapoznaj się z poniższymi informacjami dodatkowymi przydatnymi przy obsłudze tego klienta:

- [Dostosowania](client-admin-guide-customizations.md)

- [Śledzenie dokumentów](client-admin-guide-document-tracking.md)

- [Obsługiwane typy plików](client-admin-guide-file-types.md)

- [Polecenia programu PowerShell](client-admin-guide-powershell.md)

