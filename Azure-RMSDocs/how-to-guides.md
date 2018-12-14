---
title: Instrukcji dla typowych scenariuszy korzystających z usługi Azure Information Protection.
description: Zidentyfikować przypadki użycia klasyfikować i chronić dane Twojej organizacji za pomocą usługi Azure Information Protection.
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 12/08/2018
ms.topic: conceptual
ms.service: information-protection
ms.reviewer: eymanor
ms.suite: ems
ms.openlocfilehash: 7986648999a830985c4dbd1f31855bb222a443c2
ms.sourcegitcommit: 2a1c0882d2b0400f4da6370dbc1830df09867e3d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/11/2018
ms.locfileid: "53218378"
---
# <a name="how-to-guides-for-common-scenarios-that-use-azure-information-protection"></a>Przewodniki z instrukcjami dla typowych scenariuszy korzystających z usługi Azure Information Protection

>*Dotyczy: [Usługa Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection)*

Istnieje wiele sposobów, w których można użyć usługi Azure Information Protection do klasyfikowania i ewentualnie chronić dokumenty i wiadomości e-mail w organizacji. 

Najbardziej pomyślnych wdrożeniach są tymi, które identyfikują wybrane przypadki użycia, które zapewniają największe korzyści biznesowych w organizacji. Użyj poniższej listy typowe scenariusze i instrukcje, aby uzyskać wdrożenia na wyższy.

## <a name="common-scenarios"></a>Typowe scenariusze

|Scenariusz: Chcę...|Instrukcje|
|----------------|---------------|
|Znajdź jakie wrażliwych informacji w mojej organizacji są przechowywane w środowisku lokalnym|[Szybki start: Znajdź jakie poufne informacje, które masz w plików przechowywanych w środowisku lokalnym](quickstart-findsensitiveinfo.md)|
|Ułatwienia dla użytkowników dotyczące ochrony wiadomości e-mail zawierające informacje poufne|[Szybki start: Konfigurowanie etykiety w celu użytkownikom łatwy sposób chronić wiadomości e-mail zawierające poufne informacje](quickstart-label-dnf-protectedemail.md)|
|Ułatw służący do klasyfikowania danych, ponieważ ma ona utworzonym lub edytowanym etykietami oraz chronienia ich, jeśli zawiera on informacji poufnych| [Samouczek: Edytuj zasady i Utwórz nową etykietę](infoprotect-quick-start-tutorial.md)|
|Ułatwiają użytkownikom współpracę w chronionym dokumencie|[Konfigurowanie bezpiecznej współpracy nad dokumentami za pomocą usługi Azure Information Protection](secure-collaboration-documents.md)|
|Automatyczna ochrona wiadomości e-mail użytkowników, które są wysyłane poza organizację| [Konfigurowanie reguł przepływu poczty e-mail na potrzeby etykiet usługi Azure Information Protection](configure-exo-rules.md)
|Automatycznie klasyfikować i chronić dane w moich lokalnych magazynów danych|[Wdrażanie skanera usługi Azure Information Protection](deploy-aip-scanner.md)|
|Użyj własnego klucza w celu ochrony danych organizacji| [Planowanie i wdrażanie klucza dzierżawy](plan-implement-tenant-key.md)|
|Migrowanie z usług AD RMS|[Migrowanie z usług AD RMS do usługi Azure Information Protection](migrate-from-ad-rms-to-azure-rms.md)|

## <a name="additional-deployment-instructions"></a>Instrukcje dotyczące wdrażania dodatkowych

Nasze [blog techniczny usługi Azure Information Protection](https://aka.ms/AIPblog) ma dodatkowe instrukcje od naszego zespołu inżynieryjnego środowiska klienta. Przykład:

- [Za pomocą usługi Azure Information Protection do ochrony dokumentu PDF i Adobe Acrobat Reader, aby je wyświetlić](https://techcommunity.microsoft.com/t5/Azure-Information-Protection/Using-Azure-Information-Protection-to-protect-PDF-s-and-Adobe/ba-p/282010)

- [Katalogowanie poufnych danych za pomocą usługi AIP, nawet przed rozpoczęciem konfigurowania etykiet!](https://techcommunity.microsoft.com/t5/Azure-Information-Protection/Cataloging-your-Sensitive-Data-with-AIP-Even-Before-Configuring/ba-p/267241)

- [Instalacji ekspresowej skanera usługi Azure Information Protection](https://techcommunity.microsoft.com/t5/Azure-Information-Protection/Azure-Information-Protection-Scanner-Express-Installation/ba-p/265424)

- [Odnajdywanie poufnych danych za pomocą skanera usługi AIP (usługi AIP — wersja Premium P1)](https://techcommunity.microsoft.com/t5/Azure-Information-Protection/Discovery-of-Sensitive-Data-Using-the-AIP-Scanner-AIP-Premium-P1/ba-p/252040)

## <a name="next-steps"></a>Następne kroki

Nie widzisz danego scenariusza, na liście? Sprawdź [plan wdrożenia](deployment-roadmap.md) pełną listę kroków planowania i wdrażania.

Jeśli jesteś nowym użytkownikiem usługi Azure Information Protection, zapoznaj się z [co to jest Azure Information Protection?](what-is-information-protection.md) szybkie wprowadzenie do usługi, przed rozpoczęciem wdrażania.
