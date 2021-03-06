---
title: Aplikacja RMS sharing dla systemu Windows i platform urządzeń przenośnych — AIP
description: Informacje dotyczące sposobu, w jaki aplikacja RMS sharing obsługuje usługi Azure RMS jako bezpłatna aplikacja do pobrania, która jest wymagana w celu obsługi pakietu Office 2010, ale jest także zalecana dla komputerów z systemem Windows, komputerów Mac i urządzeń przenośnych.
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 08/22/2018
ms.topic: conceptual
ms.service: information-protection
ms.assetid: 1da6e372-2b3f-4af7-80f7-6b9073dff7f5
ms.reviewer: esaggese
ms.suite: ems
ms.openlocfilehash: 16110efd8d0874ba1235cc02576848d122203ea8
ms.sourcegitcommit: 5b4eb0e17fb831d338d8c25844e9e6f4ca72246d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/10/2018
ms.locfileid: "53173445"
---
# <a name="rms-sharing-application-for-windows-and-mobile-platforms"></a>Aplikacja RMS sharing dla systemu Windows i platform urządzeń przenośnych

>*Dotyczy: [Usługa Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection), [usługi Office 365](https://download.microsoft.com/download/E/C/F/ECF42E71-4EC0-48FF-AA00-577AC14D5B5C/Azure_Information_Protection_licensing_datasheet_EN-US.pdf)*

> [!IMPORTANT]
> **Koniec obsługi powiadomień**: Rights Management sharing application for Windows jest zastępowany przez [klienta Azure Information Protection](./rms-client/aip-client.md). Obsługa tej starszej aplikacji zakończy 31 stycznia 2019 r. 
 
Aplikacja do udostępniania usługi RMS jest dostępny do pobrania aplikacja, która obsługuje pakiet Office 2010 na komputerach Windows i używana zaleca się dla wszystkich komputerów Windows i urządzeniach przenośnych. Nadal zaleca się korzystanie z niej na komputerach Mac i urządzeniach z systemem Windows Phone. Jedną z jej zalet jest możliwość stosowania ogólnej ochrony dla aplikacji i plików, które nie obsługują natywnie usługi Azure Rights Management, co oznacza, że wszystkie pliki mogą być chronione. Aby uzyskać więcej informacji na temat różnych poziomów ochrony, zobacz sekcję [Poziom ochrony — natywny i ogólny](./rms-client/sharing-app-admin-guide-technical.md#levels-of-protection--native-and-generic) w [Przewodniku administratora aplikacji do udostępniania usługi Rights Management](./rms-client/sharing-app-admin-guide.md).

Gdy użytkownicy chronią swoje pliki przy użyciu aplikacji RMS sharing, mogą również śledzić chronione dokumenty i odwoływać dostęp do nich, jeśli jest to konieczne. Służy do tego [witryna śledzenia dokumentów](https://go.microsoft.com/fwlink/?LinkId=529562).

W przypadku komputerów z systemem Windows aplikacja RMS sharing dyskretnie integruje się z aplikacjami już używanymi przez użytkowników i ulepsza te aplikacje:

-   Instalowany jest dodatek pakietu Office dla programów Word, Excel, PowerPoint i Outlook. Zapewnia to użytkownikom dostęp do przycisku **Udostępnij chronione** na wstążce, służącego do otwierania łatwego w użyciu okna dialogowego ustawień, które są najczęściej używane do ochrony plików przeznaczonych do przesyłania pocztą e-mail. Ten przycisk pozwala również szybko uzyskać dostęp do witryny śledzenia dokumentów.

-   Nowa opcja wyświetlana po kliknięciu prawym przyciskiem myszy w Eksploratorze plików. Zapewnia to użytkownikom dostęp do opcji **Włącz ochronę miejscową**, służącej do otwierania łatwego w użyciu okna dialogowego ustawień, które są najczęściej używane do ochrony plików przechowywanych na dysku.

-   Przeglądarka umożliwiająca otwieranie plików chronionych przez usługę Azure Rights Management. Ta przeglądarka jest wywoływana automatycznie, gdy nie zainstalowano innej aplikacji umożliwiającej otworzenie pliku.

-   Konfiguracja zaplecza pakietu Office 2010, która umożliwia programu Word, Excel, PowerPoint i Outlook z tego pakietu sprawne bezproblemowo z usługą Azure Rights Management.

Aplikację RMS sharing dla systemu Windows można pobrać i zainstalować na pojedynczym komputerze przy użyciu [strony usługi Microsoft Rights Management](https://go.microsoft.com/fwlink/?LinkId=303970), jednak obsługuje ona również wdrażanie w przedsiębiorstwie w trybie instalacji dyskretnej i konfiguracji niestandardowej. Aby uzyskać więcej informacji, zobacz następujące zasoby:

-   [Przewodnik administratora aplikacji do udostępniania usługi Rights Management](./rms-client/sharing-app-admin-guide.md)

-   [Podręcznik użytkownika aplikacji do udostępniania usługi Rights Management](./rms-client/sharing-app-user-guide.md)

Aplikacja RMS sharing dla urządzeń przenośnych obsługuje najczęściej używane urządzenia przenośne, takie jak tablety iPad, telefony iPhone oraz urządzenia z systemem Android, Windows Phone i Windows RT. Użytkownicy mogą pobrać tę aplikację z odpowiedniego sklepu, a linki prowadzące do aplikacji znajdują się dodatkowo na [stronie usługi Microsoft Rights Management](https://go.microsoft.com/fwlink/?LinkId=303970).

**Jeśli masz Microsoft Intune**: Aplikacja RMS sharing zawiera Microsoft Intune App Software Development Kit, można użyć następujących opcji:

-   Wdrażanie aplikacji dla urządzeń z systemem iOS lub Android, zarejestrowanych w usłudze Intune, i zarządzanie tą aplikacją.

-   Zarządzanie aplikacją dla urządzeń z systemem Android, które nie zostały zarejestrowane w usłudze Intune.


## <a name="next-steps"></a>Następne kroki
Aby dowiedzieć się, jak inne aplikacje i usługi obsługują usługę Azure Rights Management w ramach usługi Azure Information Protection, zobacz [Jak aplikacje obsługują usługę Azure Rights Management](applications-support.md).

