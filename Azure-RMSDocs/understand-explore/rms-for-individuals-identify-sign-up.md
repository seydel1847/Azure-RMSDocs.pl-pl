---
title: "Sprawdzanie, czy użytkownicy utworzyli konto w usłudze RMS dla użytkowników indywidualnych — AIP"
description: "Być może zastanawiasz się, w jaki sposób administrator może sprawdzić, czy użytkownicy utworzyli konta usługi RMS dla użytkowników indywidualnych. Można zastosować dowolną metodę opisaną w tym artykule lub kombinację różnych metod."
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 02/08/2017
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: a36c3d99-a794-4f7a-aafb-64a950f1fcf9
ms.reviewer: esaggese
ms.suite: ems
ms.openlocfilehash: 10dfa64146587fe816df6a555e0a3b43c1290c45
ms.sourcegitcommit: 31e128cc1b917bf767987f0b2144b7f3b6288f2e
translationtype: HT
---
# <a name="how-to-find-out-if-your-users-have-signed-up-for-rms-for-individuals"></a>Jak sprawdzić, czy użytkownicy utworzyli konto usługi RMS dla użytkowników indywidualnych

>*Dotyczy: Azure Information Protection*

Być może zastanawiasz się, w jaki sposób administrator może sprawdzić, czy użytkownicy utworzyli konta usługi RMS dla użytkowników indywidualnych. W tym celu można użyć jednej z poniższych metod lub ich dowolnej kombinacji:

-   Zapytaj użytkowników, jak chronią poufne pliki, zwłaszcza gdy współpracują z osobami spoza organizacji.

-   Jeśli Twoja organizacja ma subskrypcję platformy Azure, użyj polecenia cmdlet [Get-MsolAccountSku](https://msdn.microsoft.com/library/azure/dn194118.aspx) i sprawdź, czy którykolwiek użytkownik ma przypisaną licencję **RIGHTSMANAGEMENT_ADHOC**. Licencja ta pochodzi z przyznanej organizacji subskrypcji usługi RMS dla użytkowników indywidualnych obejmującej pulę aktywnych jednostek, z których użytkownicy mogą korzystać w celu samodzielnej rejestracji.

-   Sporządź spis zainstalowanego i używanego oprogramowania za pomocą rozwiązania do zarządzania systemem, takiego jak program System Center Configuration Manager. Możesz na przykład wyszukać plik **MSIP. App.exe**, który jest używany przez klienta usługi Azure Information Protection, lub plik **ipviewer.exe** używany przez aplikację RMS sharing. Możesz pobrać i zainstalować tego klienta i aplikację za darmo, aby zidentyfikować inne cechy, których użyjesz następnie na potrzeby spisu oprogramowania.

-   Zwróć uwagę na rozszerzenia nazw plików utworzone przez klienta usługi Azure Information Protection lub aplikację do tworzenia i przetwarzania dokumentów chronionych usługami Rights Management. Najbardziej typowe przykłady rozszerzeń nazw plików to pfile i ppdf, ale w przypadku innych plików ich rozszerzenia również są zmieniane, gdy pliki te są natywnie chronione przez usługę Rights Management. Aby uzyskać więcej informacji, zobacz sekcję [Typy plików, dla których obsługiwana jest ochrona](../rms-client/client-admin-guide-file-types.md#file-types-supported-for-protection) w podręczniku administratora klienta usługi Azure Information Protection.

[!INCLUDE[Commenting house rules](../includes/houserules.md)]