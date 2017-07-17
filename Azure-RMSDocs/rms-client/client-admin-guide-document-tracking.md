---
title: "Śledzenie dokumentów w usłudze Azure Information Protection"
description: "Instrukcje i informacje dla administratorów dotyczące konfigurowania i używania śledzenia dokumentów w usłudze Azure Information Protection."
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 07/10/2017
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: 983ecdc9-5631-48b8-8777-f4cbbb4934e8
ms.reviewer: eymanor
ms.suite: ems
ms.openlocfilehash: 2f8e3310eee90f3e81da4f513d795af478015222
ms.sourcegitcommit: ea03477312b64c0a846701e46d991fe2c85b3a1f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2017
---
# Konfigurowanie i używanie śledzenia dokumentów w usłudze Azure Information Protection
<a id="configuring-and-using-document-tracking-for-azure-information-protection" class="xliff"></a>

>*Dotyczy: usługi zarządzania prawami dostępu w usłudze Active Directory, Azure Information Protection, Windows 10, Windows 8.1, Windows 8, Windows 7 z dodatkiem SP1, Windows Server 2016, Windows Server 2012 R2, Windows Server 2012*

Jeśli Twoja [subskrypcja obejmuje obsługę śledzenia dokumentów](https://www.microsoft.com/en-us/cloud-platform/azure-information-protection-features), witryna śledzenia dokumentów jest domyślnie włączona dla wszystkich użytkowników w organizacji. Śledzenia dokumentów dostarcza użytkownikom i administratorom informacji o dostępach do chronionego dokumentu i w razie potrzeby umożliwia odwołanie śledzonego dokumentu.

## Kontrola prywatności w witrynie śledzenia dokumentów
<a id="privacy-controls-for-your-document-tracking-site" class="xliff"></a>

Jeśli wyświetlanie informacji o śledzeniu dokumentów jest w organizacji zabronione ze względu na wymagania ochrony prywatności, możesz wyłączyć śledzenie dokumentów za pomocą polecenia cmdlet [Disable-AadrmDocumentTrackingFeature](/powershell/module/aadrm/disable-aadrmdocumenttrackingfeature). 

To polecenie cmdlet powoduje wyłączenie dostępu do witryny śledzenia, tak aby żaden użytkownik w organizacji nie mógł śledzić ani odwołać dostępu do chronionych dokumentów. W dowolnym momencie możesz ponownie włączyć śledzenie dokumentów za pomocą polecenia [Enable-AadrmDocumentTrackingFeature](/powershell/module/aadrm/enable-aadrmdocumenttrackingfeature) i sprawdzić, czy śledzenie dokumentów jest aktualnie włączone, czy wyłączone, za pomocą polecenia [Get-AadrmDocumentTrackingFeature](/powershell/module/aadrm/get-aadrmdocumenttrackingfeature). Aby uruchomić te polecenia cmdlet, musisz mieć co najmniej wersję **2.3.0.0** modułu Azure Rights Management (AADRM) dla programu PowerShell. 

Gdy witryna śledzenia dokumentów jest włączona, domyślnie są udostępniane informacje takie jak adresy e-mail osób, które próbowały uzyskać dostęp do chronionych dokumentów, czas podjęcia takich prób oraz lokalizacja tych osób. Takie informacje mogą być przydatne do określenia sposobu korzystania z udostępnionych dokumentów oraz ustalenia, czy dokumenty powinny zostać odwołane w przypadku wystąpienia podejrzanych działań. Jednak z uwagi na konieczność zachowania prywatności może okazać się konieczne wyłączenie informacji dotyczących niektórych lub wszystkich użytkowników. 

Jeśli istnieją użytkownicy, których aktywność nie powinna być śledzona, dodaj ich do grupy przechowywanej w usłudze Azure AD i podaj tę grupę przy użyciu polecenia cmdlet [Set-AadrmDoNotTrackUserGroup](/powershell/module/aadrm/Set-AadrmDoNotTrackUserGroup). W tym poleceniu cmdlet należy określić pojedynczą grupę. Taka grupa może jednak zawierać grupy zagnieżdżone. 

Aktywność członków tej grupy związana z dokumentami współdzielonymi z nimi przez innych użytkowników nie jest rejestrowana przez witrynę śledzenia dokumentów. Ponadto do użytkowników, którzy udostępnili dokument, nie są wysyłane powiadomienia e-mail.

Podczas używania tej konfiguracji wszyscy użytkownicy mogą nadal używać witryny śledzenia dokumentów i odwoływać dostęp do dokumentów, które zostały objęte ochroną. Jednak nie jest widoczna aktywność użytkowników, którzy zostali zdefiniowani za pomocą polecenia cmdlet Set-AadrmDoNotTrackUserGroup.

Jeśli ta opcja nie jest już potrzebna, można użyć polecenia [Clear-AadrmDoNotTrackUserGroup](/powershell/module/aadrm/Clear-AadrmDoNotTrackUserGroup). Aby wybiórczo usunąć użytkowników, usuń ich z grupy, pamiętając o [buforowaniu grupy](../plan-design/prepare.md#group-membership-caching-by-azure-rights-management). Można sprawdzić, czy ta opcja jest obecnie używana, używając polecenia [Get-AadrmDoNotTrackUserGroup](/powershell/module/aadrm/get-AadrmDoNotTrackUserGroup). Aby uruchomić te polecenia cmdlet dla danej konfiguracji grupy, musisz mieć co najmniej wersję **2.10.0.0** modułu Azure Rights Management (AADRM) dla programu PowerShell.

Aby uzyskać więcej informacji na temat każdego z tych poleceń cmdlet, należy użyć podanych linków. Aby uzyskać instrukcje instalacji modułu PowerShell, zobacz temat [Instalowanie programu Windows PowerShell dla usługi Azure Rights Management](../deploy-use/install-powershell.md). Jeśli moduł został wcześniej pobrany i zainstalowany, sprawdź numer wersji, uruchamiając polecenie: `(Get-Module aadrm –ListAvailable).Version`


## Docelowe adresy URL używane przez witryny śledzenia dokumentów
<a id="destination-urls-used-by-the-document-tracking-site" class="xliff"></a>

Następujące adresy URL są używane do śledzenia dokumentów i należy zezwalać na dostęp do nich na wszystkich urządzeniach i w usługach między klientami korzystającymi z klienta usługi Azure Information Protection a Internetem. Na przykład te adresy URL należy dodać do zapór lub do zaufanych witryn, jeśli używasz programu Internet Explorer ze zwiększonymi zabezpieczeniami.

-  `https://*.azurerms.com`

- `https://*.microsoftonline.com`

- `https://*.microsoftonline-p.com`

- `https://ecn.dev.virtualearth.net`

Te adresy URL są standardowe dla usługi Azure Rights Management, z wyjątkiem adresu URL virtualearth.net, który jest używany przez mapy Bing do wyświetlania lokalizacji użytkownika.

## Śledzenie i odwoływanie dokumentów dla użytkowników
<a id="tracking-and-revoking-documents-for-users" class="xliff"></a>

Użytkownicy po zalogowaniu się do witryny śledzenia dokumentów mogą śledzić i odwoływać dokumenty objęte ochroną za pomocą klienta usługi Azure Information Protection lub udostępnione za pomocą aplikacji Rights Management. Po zalogowaniu się jako administrator usługi Azure Information Protection (administrator globalny) możesz kliknąć ikonę administratora, aby przełączyć się do trybu administratora. Tryb ten umożliwia wyświetlenie dokumentów, dla których użytkownicy w organizacji włączyli śledzenie przy użyciu klienta usługi Azure Information Protection lub które udostępnili za pomocą aplikacji do udostępniania Rights Management:

![Ikona administratora w witrynie śledzenia dokumentów](../media/tracking-site-admin-icon.png)

Akcje wykonywane w trybie administratora są poddawane inspekcji i rejestrowane w plikach dziennika użycia. Musisz potwierdzić, aby kontynuować. Aby uzyskać więcej informacji na temat tego rejestrowania, zobacz następną sekcję.

W trybie administratora możesz wyszukiwać według użytkownika lub dokumentu. Wyszukiwanie według użytkownika umożliwia wyświetlenie wszystkich dokumentów, dla których ten użytkownik włączył śledzenie przy użyciu klienta usługi Azure Information Protection lub które udostępnił za pomocą aplikacji do udostępniania Rights Management. 

Wyszukiwanie według dokumentów umożliwia wyświetlenie wszystkich użytkowników w organizacji, którzy włączyli śledzenie danego dokumentu przy użyciu klienta usługi Azure Information Protection lub udostępnili dany dokument za pomocą aplikacji do udostępniania Rights Management. Następnie możesz przejść do szczegółów wyników wyszukiwania, aby śledzić dokumenty chronione przez użytkowników i w razie potrzeby odwołać dostęp do tych dokumentów. 

Aby wyjść z trybu administratora, kliknij przycisk **X** obok pozycji **Wyjdź z trybu administratora**:

![Wyjście z trybu administratora w witrynie śledzenia dokumentów](../media/tracking-site-exit-admin-icon.png)

Aby uzyskać instrukcje dotyczące sposobu korzystania z witryny śledzenia dokumentów, zobacz sekcję [Śledzenie i odwoływanie dokumentów](client-track-revoke.md) w podręczniku użytkownika.

## Rejestrowanie użycia dla witryny śledzenia dokumentów
<a id="usage-logging-for-the-document-tracking-site" class="xliff"></a>

Dwa pola w plikach dziennika użycia mają zastosowanie do śledzenia dokumentów: **AdminAction** i **ActingAsUser**.

**AdminAction** — to pole ma wartość true, gdy administrator używa witryny śledzenia dokumentów w trybie administratora, na przykład w celu odwołania dokumentu w imieniu użytkownika lub sprawdzenia, kiedy dokument został udostępniony. To pole jest puste w przypadku, gdy użytkownik loguje się do witryny śledzenia dokumentów.

**ActingAsUser** — jeśli pole AdminAction ma wartość true, to pole zawiera nazwę użytkownika, w imieniu którego administrator działa (wyszukiwanego użytkownika lub właściciela dokumentu). To pole jest puste w przypadku, gdy użytkownik loguje się do witryny śledzenia dokumentów. 

Istnieją również typy żądań, które rejestrują sposób, w jaki użytkownicy i administratorzy korzystają z witryny śledzenia dokumentu. Na przykład typ żądania **RevokeAccess** dotyczy sytuacji, gdy użytkownik lub administrator w imieniu użytkownika odwołał dokument w witrynie śledzenia dokumentów. Użyj tego typu żądania w połączeniu z polem AdminAction, aby określić, czy użytkownik odwołał własny dokument (pole AdminAction jest puste), czy też administrator odwołał dokument w imieniu użytkownika (pole AdminAction ma wartość true).


Aby uzyskać więcej informacji na temat rejestrowania użycia, zobacz [Rejestrowanie i analizowanie użycia usługi Azure Rights Management](../deploy-use/log-analyze-usage.md)



## Następne kroki
<a id="next-steps" class="xliff"></a>
Po skonfigurowaniu witryny śledzenia dokumentów klienta usługi Azure Information Protection zapoznaj się z poniższymi informacjami dodatkowymi przydatnymi przy obsłudze tego klienta:

- [Dostosowania](client-admin-guide-customizations.md)

- [Rejestrowanie plików i użycia klienta](client-admin-guide-files-and-logging.md)

- [Obsługiwane typy plików](client-admin-guide-file-types.md)

- [Polecenia programu PowerShell](client-admin-guide-powershell.md)

[!INCLUDE[Commenting house rules](../includes/houserules.md)]
