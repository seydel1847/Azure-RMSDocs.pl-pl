---
title: Śledzenie dokumentów w usłudze Azure Information Protection
description: Instrukcje i informacje dla administratorów dotyczące konfigurowania i używania śledzenia dokumentów w usłudze Azure Information Protection.
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 04/13/2018
ms.topic: article
ms.prod: ''
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: 983ecdc9-5631-48b8-8777-f4cbbb4934e8
ms.reviewer: eymanor
ms.suite: ems
ms.openlocfilehash: e24d91f04dc3186a9451546c8a962c49129f326b
ms.sourcegitcommit: affda7572064edaf9e3b63d88f4a18d0d6932b13
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
ms.locfileid: "31008985"
---
# <a name="admin-guide-configuring-and-using-document-tracking-for-azure-information-protection"></a>Podręcznik administratora: Konfigurowanie i używanie śledzenia dokumentów dla usługi Azure Information Protection

>*Dotyczy: [Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection), Windows 10, Windows 8.1, Windows 8, Windows 7 z dodatkiem SP1, Windows Server 2016, systemu Windows Server 2012 R2, systemu Windows Server 2012, Windows Server 2008 R2*

Jeśli Twoja [subskrypcja obejmuje obsługę śledzenia dokumentów](https://www.microsoft.com/en-us/cloud-platform/azure-information-protection-features), witryna śledzenia dokumentów jest domyślnie włączona dla wszystkich użytkowników w organizacji. Śledzenia dokumentów dostarcza użytkownikom i administratorom informacji o dostępach do chronionego dokumentu i w razie potrzeby umożliwia odwołanie śledzonego dokumentu.

## <a name="using-powershell-to-manage-the-document-tracking-site"></a>Zarządzanie witryny śledzenia dokumentów za pomocą programu PowerShell

Poniższe sekcje zawierają informacje dotyczące sposobu zarządzania witryny śledzenia dokumentów za przy użyciu programu PowerShell. Aby uzyskać instrukcje instalacji modułu programu PowerShell, zobacz [Instalowanie modułu programu PowerShell AADRM](../deploy-use/install-powershell.md). Jeśli moduł został wcześniej pobrany i zainstalowany, sprawdź numer wersji, uruchamiając polecenie: `(Get-Module aadrm –ListAvailable).Version`

Aby uzyskać więcej informacji na temat poszczególnych poleceń cmdlet należy użyć linków dostępnych.

### <a name="privacy-controls-for-your-document-tracking-site"></a>Kontrola prywatności w witrynie śledzenia dokumentów

Jeśli wyświetlanie informacji o śledzeniu dokumentów jest w organizacji zabronione ze względu na wymagania ochrony prywatności, możesz wyłączyć śledzenie dokumentów za pomocą polecenia cmdlet [Disable-AadrmDocumentTrackingFeature](/powershell/module/aadrm/disable-aadrmdocumenttrackingfeature). 

To polecenie cmdlet powoduje wyłączenie dostępu do witryny śledzenia, tak aby żaden użytkownik w organizacji nie mógł śledzić ani odwołać dostępu do chronionych dokumentów. W dowolnym momencie możesz ponownie włączyć śledzenie dokumentów za pomocą polecenia [Enable-AadrmDocumentTrackingFeature](/powershell/module/aadrm/enable-aadrmdocumenttrackingfeature) i sprawdzić, czy śledzenie dokumentów jest aktualnie włączone, czy wyłączone, za pomocą polecenia [Get-AadrmDocumentTrackingFeature](/powershell/module/aadrm/get-aadrmdocumenttrackingfeature). Aby uruchomić te polecenia cmdlet, musisz mieć co najmniej wersji **2.3.0.0** AADRM modułu środowiska PowerShell. 

Gdy witryna śledzenia dokumentów jest włączona, domyślnie są udostępniane informacje takie jak adresy e-mail osób, które próbowały uzyskać dostęp do chronionych dokumentów, czas podjęcia takich prób oraz lokalizacja tych osób. Takie informacje mogą być przydatne do określenia sposobu korzystania z udostępnionych dokumentów oraz ustalenia, czy dokumenty powinny zostać odwołane w przypadku wystąpienia podejrzanych działań. Jednak z uwagi na konieczność zachowania prywatności może okazać się konieczne wyłączenie informacji dotyczących niektórych lub wszystkich użytkowników. 

Jeśli masz użytkowników, którzy nie powinny mieć tego działania śledzone przez innych użytkowników, dodaj je do grupy, który jest przechowywany w usłudze Azure AD i określić tę grupę [AadrmDoNotTrackUserGroup zestaw](/powershell/module/aadrm/Set-AadrmDoNotTrackUserGroup) polecenia cmdlet. W tym poleceniu cmdlet należy określić pojedynczą grupę. Taka grupa może jednak zawierać grupy zagnieżdżone. 

Dla tych członków grupy Użytkownicy nie widzą żadnych działań w dokumencie witryny śledzenia, gdy dokumenty udostępnione z nimi dotyczące tego działania. Ponadto do użytkowników, którzy udostępnili dokument, nie są wysyłane powiadomienia e-mail.

Podczas używania tej konfiguracji wszyscy użytkownicy mogą nadal używać witryny śledzenia dokumentów i odwoływać dostęp do dokumentów, które zostały objęte ochroną. Jednak nie jest widoczna aktywność użytkowników, którzy zostali zdefiniowani za pomocą polecenia cmdlet Set-AadrmDoNotTrackUserGroup.

To ustawienie dotyczy tylko użytkowników końcowych. Administratorzy usługi Azure Information Protection zawsze można śledzić działania wszystkich użytkowników, nawet wtedy, gdy ci użytkownicy są określane przy użyciu zestawu AadrmDoNotTrackUserGroup. Aby uzyskać więcej informacji o sposobie Administratorzy mogą śledzić dokumenty dla użytkowników, zobacz [śledzenie i odwoływanie dokumentów dla użytkowników](#tracking-and-revoking-documents-for-users) sekcji.


### <a name="logging-information-from-the-document-tracking-site"></a>Rejestrowanie informacji z witryny śledzenia dokumentów

Jeśli masz minimalnej wersji **2.13.0.0** modułu AADRM pobierania rejestrowanie informacji z witryny śledzenia dokumentów można użyć następujących poleceń cmdlet:

- [Get-AadrmTrackingLog](/powershell/module/aadrm/Get-AadrmTrackingLog)
    
    To polecenie cmdlet zwraca informacje o chronionych dokumentów dla określonego użytkownika, który chronionych dokumentów (Wystawca Rights Management) lub kto uzyskiwał dostęp do chronionych dokumentów. Użyj następującego polecenia cmdlet, aby odpowiedzieć na pytanie "chronionych dokumentów, czy określony użytkownik śledzić lub dostęp?"

- [Get-AadrmDocumentLog](/powershell/module/aadrm/Get-AadrmDocumentLog)
    
    To polecenie cmdlet zwraca ochrony informacji o śledzonych dokumentów dla określonego użytkownika, jeśli użytkownik chronionych dokumentów (Wystawca Rights Management) lub będący właścicielem usługi Rights Management dla dokumentów lub chronionych dokumentów zostały skonfigurowane w celu udzielenia dostępu bezpośrednio do użytkownika. Użyj następującego polecenia cmdlet aby odpowiedzieć na pytanie "Jak są dokumenty chronione dla określonego użytkownika?"
 
## <a name="destination-urls-used-by-the-document-tracking-site"></a>Docelowe adresy URL używane przez witryny śledzenia dokumentów

Następujące adresy URL są używane do śledzenia dokumentów i należy zezwalać na dostęp do nich na wszystkich urządzeniach i w usługach między klientami korzystającymi z klienta usługi Azure Information Protection a Internetem. Na przykład te adresy URL należy dodać do zapór lub do zaufanych witryn, jeśli używasz programu Internet Explorer ze zwiększonymi zabezpieczeniami.

-  `https://*.azurerms.com`

- `https://*.microsoftonline.com`

- `https://*.microsoftonline-p.com`

- `https://ecn.dev.virtualearth.net`

Te adresy URL są standardowe dla usługi Azure Rights Management, z wyjątkiem adresu URL virtualearth.net, który jest używany przez mapy Bing do wyświetlania lokalizacji użytkownika.

## <a name="tracking-and-revoking-documents-for-users"></a>Śledzenie i odwoływanie dokumentów dla użytkowników

Użytkownicy po zalogowaniu się do witryny śledzenia dokumentów mogą śledzić i odwoływać dokumenty objęte ochroną za pomocą klienta usługi Azure Information Protection lub udostępnione za pomocą aplikacji Rights Management. Po zalogowaniu się jako administrator usługi Azure Information Protection (administrator globalny) możesz kliknąć ikonę administratora, aby przełączyć się do trybu administratora. Tryb ten umożliwia wyświetlenie dokumentów, dla których użytkownicy w organizacji włączyli śledzenie przy użyciu klienta usługi Azure Information Protection lub które udostępnili za pomocą aplikacji do udostępniania Rights Management:

![Ikona administratora w witrynie śledzenia dokumentów](../media/tracking-site-admin-icon.png)

> [!NOTE] 
> Jeśli nie widzisz tę ikonę, mimo iż administratora globalnego, jest on, ponieważ nie jeszcze udostępniasz żadnych dokumentów samodzielnie. W takim przypadku należy użyć następującego adresu URL dostęp do witryny śledzenia dokumentów: https://portal.azurerms.com/#/admin

Akcje wykonywane w trybie administratora są poddawane inspekcji i rejestrowane w plikach dziennika użycia. Musisz potwierdzić, aby kontynuować. Aby uzyskać więcej informacji na temat tego rejestrowania, zobacz następną sekcję.

W trybie administratora możesz wyszukiwać według użytkownika lub dokumentu. Wyszukiwanie według użytkownika umożliwia wyświetlenie wszystkich dokumentów, dla których ten użytkownik włączył śledzenie przy użyciu klienta usługi Azure Information Protection lub które udostępnił za pomocą aplikacji do udostępniania Rights Management. 

Wyszukiwanie według dokumentów umożliwia wyświetlenie wszystkich użytkowników w organizacji, którzy włączyli śledzenie danego dokumentu przy użyciu klienta usługi Azure Information Protection lub udostępnili dany dokument za pomocą aplikacji do udostępniania Rights Management. Następnie możesz przejść do szczegółów wyników wyszukiwania, aby śledzić dokumenty chronione przez użytkowników i w razie potrzeby odwołać dostęp do tych dokumentów. 

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

- [Dostosowania](client-admin-guide-customizations.md)

- [Rejestrowanie plików i użycia klienta](client-admin-guide-files-and-logging.md)

- [Obsługiwane typy plików](client-admin-guide-file-types.md)

- [Polecenia programu PowerShell](client-admin-guide-powershell.md)

[!INCLUDE[Commenting house rules](../includes/houserules.md)]
