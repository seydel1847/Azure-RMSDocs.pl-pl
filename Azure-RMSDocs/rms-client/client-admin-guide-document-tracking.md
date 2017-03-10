---
title: "Śledzenie dokumentów w usłudze Azure Information Protection"
description: "Instrukcje i informacje dla administratorów dotyczące konfigurowania i używania śledzenia dokumentów w usłudze Azure Information Protection."
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 02/08/2017
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: 983ecdc9-5631-48b8-8777-f4cbbb4934e8
ms.reviewer: eymanor
ms.suite: ems
ms.openlocfilehash: f47b177ece91f775d53c72d379d6ffa3a2f3c98b
ms.sourcegitcommit: 31e128cc1b917bf767987f0b2144b7f3b6288f2e
translationtype: HT
---
# <a name="configuring-and-using-document-tracking-for-azure-information-protection"></a>Konfigurowanie i używanie śledzenia dokumentów w usłudze Azure Information Protection

>*Dotyczy: usługi Active Directory Rights Management, Azure Information Protection, Windows 10, Windows 8.1, Windows 8, Windows 7 z dodatkiem SP1*

Jeśli Twoja [subskrypcja obejmuje obsługę śledzenia dokumentów](https://www.microsoft.com/en-us/cloud-platform/azure-information-protection-features), witryna śledzenia dokumentów jest domyślnie włączona dla wszystkich użytkowników w organizacji. Podczas śledzenia dokumentów pokazywane są informacje, takie jak adresy e-mail osób, które próbowały uzyskać dostęp do chronionych dokumentów udostępnionych przez użytkowników, czas podjęcia takich prób oraz lokalizacja tych osób. Jeśli wyświetlanie tych informacji jest w organizacji zabronione ze względu na wymagania ochrony prywatności, możesz wyłączyć dostęp do witryny śledzenia dokumentów za pomocą polecenia cmdlet [Disable-AadrmDocumentTrackingFeature](http://go.microsoft.com/fwlink/?LinkId=623032). W dowolnym momencie możesz ponownie włączyć dostęp do witryny za pomocą polecenia [Enable-AadrmDocumentTrackingFeature](http://go.microsoft.com/fwlink/?LinkId=623037) i sprawdzić, czy dostęp jest aktualnie włączony, czy wyłączony, za pomocą polecenia [Get-AadrmDocumentTrackingFeature](http://go.microsoft.com/fwlink/?LinkId=623037).

Aby uruchomić te polecenia cmdlet, musisz mieć co najmniej wersję **2.3.0.0** modułu Azure Rights Management dla programu Windows PowerShell. Instrukcje instalacji znajdują się w sekcji [Instalowanie programu Windows PowerShell dla usługi Azure Rights Management](../deploy-use/install-powershell.md).

> [!TIP]
> Jeśli moduł został wcześniej pobrany i zainstalowany, sprawdź numer wersji, uruchamiając polecenie: `(Get-Module aadrm –ListAvailable).Version`

Następujące adresy URL są używane do śledzenia dokumentów i muszą być dozwolone (można je na przykład dodać do zaufanych witryn w przypadku korzystania z programu Internet Explorer ze zwiększonymi zabezpieczeniami):

-   https://&#42;.azurerms.com

-   https://ecn.dev.virtualearth.net

    > [!NOTE]
    > Ten adres URL jest przeznaczony dla usługi Mapy Bing.

-   https://&#42;.microsoftonline.com

-   https://&#42;.microsoftonline-p.com

## <a name="tracking-and-revoking-documents-for-users"></a>Śledzenie i odwoływanie dokumentów dla użytkowników

Użytkownicy po zalogowaniu się do witryny śledzenia dokumentów mogą śledzić i odwoływać dokumenty objęte ochroną za pomocą klienta usługi Azure Information Protection lub udostępnione za pomocą aplikacji Rights Management. Po zalogowaniu się jako administrator usługi Azure Information Protection (administrator globalny) możesz kliknąć ikonę administratora, aby przełączyć się do trybu administratora i wyświetlić dokumenty udostępnione przez użytkowników w organizacji:

![Ikona administratora w witrynie śledzenia dokumentów](../media/tracking-site-admin-icon.png)

Akcje wykonywane w trybie administratora są poddawane inspekcji i rejestrowane w plikach dziennika użycia. Musisz potwierdzić, aby kontynuować. Aby uzyskać więcej informacji na temat tego rejestrowania, zobacz następną sekcję.

W trybie administratora możesz wyszukiwać według użytkownika lub dokumentu. Wyszukiwanie według użytkownika umożliwia wyświetlenie wszystkich dokumentów udostępnionych przez określonego użytkownika. W przypadku wyszukiwania według dokumentu zostaną wyświetleni wszyscy użytkownicy w organizacji, którzy udostępnili dany dokument. Następnie możesz przejść do szczegółów wyników wyszukiwania, aby śledzić dokumenty udostępnione przez użytkowników i w razie potrzeby odwołać te dokumenty. 

Aby wyjść z trybu administratora, kliknij przycisk **X** obok pozycji **Wyjdź z trybu administratora**:

![Wyjście z trybu administratora w witrynie śledzenia dokumentów](../media/tracking-site-exit-admin-icon.png)

Aby uzyskać instrukcje dotyczące sposobu korzystania z witryny śledzenia dokumentów, zobacz sekcję [Śledzenie i odwoływanie dokumentów](client-track-revoke.md) w podręczniku użytkownika.

## <a name="usage-logging-for-the-document-tracking-site"></a>Rejestrowanie użycia dla witryny śledzenia dokumentów

Dwa pola w plikach dziennika użycia mają zastosowanie do śledzenia dokumentów: **AdminAction** i **ActingAsUser**.

**AdminAction** — to pole ma wartość true, gdy administrator używa witryny śledzenia dokumentów w trybie administratora, na przykład w celu odwołania dokumentu w imieniu użytkownika lub sprawdzenia, kiedy dokument został udostępniony. To pole jest puste w przypadku, gdy użytkownik loguje się do witryny śledzenia dokumentów.

**ActingAsUser** — jeśli pole AdminAction ma wartość true, to pole zawiera nazwę użytkownika, w imieniu którego administrator działa (wyszukiwanego użytkownika lub właściciela dokumentu). To pole jest puste w przypadku, gdy użytkownik loguje się do witryny śledzenia dokumentów. 

Istnieją również typy żądań, które rejestrują sposób, w jaki użytkownicy i administratorzy korzystają z witryny śledzenia dokumentu. Na przykład typ żądania **RevokeAccess** dotyczy sytuacji, gdy użytkownik lub administrator w imieniu użytkownika odwołał dokument w witrynie śledzenia dokumentów. Użyj tego typu żądania w połączeniu z polem AdminAction, aby określić, czy użytkownik odwołał własny dokument (pole AdminAction jest puste), czy też administrator odwołał dokument w imieniu użytkownika (pole AdminAction ma wartość true).


Aby uzyskać więcej informacji na temat rejestrowania użycia, zobacz [Rejestrowanie i analizowanie użycia usługi Azure Rights Management](../deploy-use/log-analyze-usage.md)



## <a name="next-steps"></a>Następne kroki
Po skonfigurowaniu witryny śledzenia dokumentów klienta usługi Azure Information Protection zapoznaj się z poniższymi informacjami dodatkowymi przydatnymi przy obsłudze tego klienta:

- [Rejestrowanie plików i użycia klienta](client-admin-guide-files-and-logging.md)

- [Obsługiwane typy plików](client-admin-guide-file-types.md)

- [Polecenia programu PowerShell](client-admin-guide-powershell.md)

[!INCLUDE[Commenting house rules](../includes/houserules.md)]
