---
title: "Klient usługi Azure Information Protection"
description: "Usługa Microsoft Azure Information Protection dostarcza rozwiązanie klient-serwer ułatwiające ochronę danych organizacji. Klient (klient usługi Azure Information Protection lub klient usługi Rights Management) jest zintegrowany z aplikacjami uruchamianymi na komputerach i urządzeniach przenośnych."
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 02/08/2017
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: a6fa85be-f92a-4e00-9efc-9dbfd4dfbfcb
ROBOTS: noindex,nofollow
ms.reviewer: esaggese
ms.suite: ems
ms.openlocfilehash: cee5b0499a434894e284d4cc8157af962ade99cb
ms.sourcegitcommit: 31e128cc1b917bf767987f0b2144b7f3b6288f2e
translationtype: HT
---
# <a name="the-client-side-of-azure-information-protection"></a>Strona klienta usługi Azure Information Protection

>*Dotyczy: Active Directory Rights Management, Azure Rights Management, Windows 10, Windows 8.1, Windows 8, Windows 7 z dodatkiem SP1*

Usługa Azure Information Protection dostarcza rozwiązanie klient-serwer ułatwiające ochronę dokumentów i wiadomości e-mail organizacji:

- Klient, który może być klientem usługi Azure Information Protection lub klientem usługi Rights Management, integruje się z aplikacjami uruchamianymi na komputerach i urządzeniach przenośnych. 

- Usługa jest dostępna w chmurze (usługa Azure Information Protection używająca usługi Azure Rights Management do ochrony danych) lub lokalnie (usługi Active Directory Rights Management). 

Klient usługi Azure Information Protection oprócz ochrony obsługuje klasyfikację i etykietowanie. Ten klient integruje się z aplikacjami pakietu Office i musi być instalowany oddzielnie.

Klient usługi Rights Management (RMS) jest automatycznie instalowany z niektórymi aplikacjami, takimi jak aplikacje pakietu Office, klient usługi Azure Information Protection i aplikacje do obsługi funkcji RMS pochodzące od dostawców oprogramowania. Klienta można jednak zainstalować niezależnie, co przydaje się w scenariuszach zakładających np. integrację ochrony usług Rights Management z aplikacjami biznesowymi (LOB) przeprowadzaną przez deweloperów.

Korzystając z poniższej dokumentacji, można uzyskać więcej informacji na temat sposobu wdrażania i użycia tych klientów, których można używać razem z usługami Azure Information Protection oraz Active Directory Rights Management do ochrony danych organizacji:

- [Klient usługi Azure Information Protection](AIP-client.md)

- [Uwagi dotyczące wdrażania klienta usługi RMS](client-deployment-notes.md)

- [Ochrona za pomocą usług RMS z użyciem infrastruktury klasyfikacji plików (FCI, File Classification Infrastructure) w systemie Windows Server](configure-fci.md)

- [Aplikacja do udostępniania usługi Rights Management dla systemu Windows](sharing-app-windows.md)

Aplikacja do tworzenia i przetwarzania dokumentów chronionych usługami Rights Management oraz narzędzie RMS Protection Tool zostały obecnie zastąpione przez klienta usługi Azure Information Protection. 


## <a name="see-also"></a>Zobacz także
[Porównanie usług Azure Information Protection i AD RMS](../understand-explore/compare-azure-rms-ad-rms.md)

[!INCLUDE[Commenting house rules](../includes/houserules.md)]