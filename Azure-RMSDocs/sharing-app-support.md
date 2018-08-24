---
title: Aplikacja RMS sharing dla systemu Windows i platform urządzeń przenośnych — AIP
description: Informacje dotyczące sposobu, w jaki aplikacja RMS sharing obsługuje usługi Azure RMS jako bezpłatna aplikacja do pobrania, która jest wymagana w celu obsługi pakietu Office 2010, ale jest także zalecana dla komputerów z systemem Windows, komputerów Mac i urządzeń przenośnych.
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 08/22/2018
ms.topic: article
ms.service: information-protection
ms.assetid: 1da6e372-2b3f-4af7-80f7-6b9073dff7f5
ms.reviewer: esaggese
ms.suite: ems
ms.openlocfilehash: f950e2a8ac15a073a5edc960d49ab4e21c14bfbe
ms.sourcegitcommit: 7ba9850e5bb07b14741bb90ebbe98f1ebe057b10
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/23/2018
ms.locfileid: "42806592"
---
# <a name="rms-sharing-application-for-windows-and-mobile-platforms"></a>Aplikacja RMS sharing dla systemu Windows i platform urządzeń przenośnych

>*Dotyczy: [usługi Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection), [usługi Office 365](http://download.microsoft.com/download/E/C/F/ECF42E71-4EC0-48FF-AA00-577AC14D5B5C/Azure_Information_Protection_licensing_datasheet_EN-US.pdf)*

> [!IMPORTANT]
> **Powiadomienie o zakończeniu świadczenia pomocy technicznej**: aplikację RMS sharing dla systemu Windows zastąpi [klient usługi Azure Information Protection](./rms-client/aip-client.md). Obsługa tej starszej aplikacji zakończy 31 stycznia 2019 r. 
 
RMS sharing to dostępna do pobrania aplikacja, która obsługuje pakiet Office 2010 dla systemu Windows i której stosowanie zalecano zwykle także w przypadku wszystkich komputerów z systemem Windows oraz urządzeń przenośnych. Nadal zaleca się korzystanie z niej na komputerach Mac i urządzeniach z systemem Windows Phone. Jedną z jej zalet jest możliwość stosowania ogólnej ochrony dla aplikacji i plików, które nie obsługują natywnie usługi Azure Rights Management, co oznacza, że wszystkie pliki mogą być chronione. Aby uzyskać więcej informacji na temat różnych poziomów ochrony, zobacz sekcję [Poziom ochrony — natywny i ogólny](./rms-client/sharing-app-admin-guide-technical.md#levels-of-protection--native-and-generic) w [Przewodniku administratora aplikacji do udostępniania usługi Rights Management](./rms-client/sharing-app-admin-guide.md).

Gdy użytkownicy chronią swoje pliki przy użyciu aplikacji RMS sharing, mogą również śledzić chronione dokumenty i odwoływać dostęp do nich, jeśli jest to konieczne. Służy do tego [witryna śledzenia dokumentów](http://go.microsoft.com/fwlink/?LinkId=529562).

W przypadku komputerów z systemem Windows aplikacja RMS sharing dyskretnie integruje się z aplikacjami już używanymi przez użytkowników i ulepsza te aplikacje:

-   Instalowany jest dodatek pakietu Office dla programów Word, Excel, PowerPoint i Outlook. Zapewnia to użytkownikom dostęp do przycisku **Udostępnij chronione** na wstążce, służącego do otwierania łatwego w użyciu okna dialogowego ustawień, które są najczęściej używane do ochrony plików przeznaczonych do przesyłania pocztą e-mail. Ten przycisk pozwala również szybko uzyskać dostęp do witryny śledzenia dokumentów.

-   Nowa opcja wyświetlana po kliknięciu prawym przyciskiem myszy w Eksploratorze plików. Zapewnia to użytkownikom dostęp do opcji **Włącz ochronę miejscową**, służącej do otwierania łatwego w użyciu okna dialogowego ustawień, które są najczęściej używane do ochrony plików przechowywanych na dysku.

-   Przeglądarka umożliwiająca otwieranie plików chronionych przez usługę Azure Rights Management. Ta przeglądarka jest wywoływana automatycznie, gdy nie zainstalowano innej aplikacji umożliwiającej otworzenie pliku.

-   Konfiguracja zaplecza pakietu Office 2010, która umożliwia programom Word, Excel, PowerPoint i Outlook sprawną współpracę z usługą Azure Rights Management.

Aplikację RMS sharing dla systemu Windows można pobrać i zainstalować na pojedynczym komputerze przy użyciu [strony usługi Microsoft Rights Management](http://go.microsoft.com/fwlink/?LinkId=303970), jednak obsługuje ona również wdrażanie w przedsiębiorstwie w trybie instalacji dyskretnej i konfiguracji niestandardowej. Więcej informacji można znaleźć w następujących zasobach:

-   [Przewodnik administratora aplikacji do udostępniania usługi Rights Management](./rms-client/sharing-app-admin-guide.md)

-   [Podręcznik użytkownika aplikacji do udostępniania usługi Rights Management](./rms-client/sharing-app-user-guide.md)

Aplikacja RMS sharing dla urządzeń przenośnych obsługuje najczęściej używane urządzenia przenośne, takie jak tablety iPad, telefony iPhone oraz urządzenia z systemem Android, Windows Phone i Windows RT. Użytkownicy mogą pobrać tę aplikację z odpowiedniego sklepu, a linki prowadzące do aplikacji znajdują się dodatkowo na [stronie usługi Microsoft Rights Management](http://go.microsoft.com/fwlink/?LinkId=303970).

**Jeśli masz usługę Microsoft Intune**: aplikacja RMS sharing zawiera zestaw Software Development Kit aplikacji usługi Microsoft Intune, dlatego dostępne są następujące opcje:

-   Wdrażanie aplikacji dla urządzeń z systemem iOS lub Android, zarejestrowanych w usłudze Intune, i zarządzanie tą aplikacją.

-   Zarządzanie aplikacją dla urządzeń z systemem Android, które nie zostały zarejestrowane w usłudze Intune.


## <a name="next-steps"></a>Kolejne kroki
Aby dowiedzieć się, jak inne aplikacje i usługi obsługują usługę Azure Rights Management w ramach usługi Azure Information Protection, zobacz [Jak aplikacje obsługują usługę Azure Rights Management](applications-support.md).

