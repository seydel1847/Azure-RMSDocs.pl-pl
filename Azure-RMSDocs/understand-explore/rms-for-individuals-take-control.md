---
title: "Kontrolowanie kont utworzonych w usłudze RMS dla użytkowników indywidualnych — AIP"
description: "Sposób kontrolowania kont użytkowników w usłudze Azure Active Directory, jeśli nie chcesz przekształcać subskrypcji usług RMS dla użytkowników indywidualnych organizacji na subskrypcję płatną."
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 02/23/2017
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: a83880d0-f0f9-4a32-9e00-2f6635d7cc8d
ms.reviewer: esaggese
ms.suite: ems
ms.openlocfilehash: 666408da3bfa0095db1cb6ff956c9a118201cefb
ms.sourcegitcommit: 31e128cc1b917bf767987f0b2144b7f3b6288f2e
translationtype: HT
---
# <a name="how-administrators-can-control-the-accounts-created-for-rms-for-individuals"></a>Metody kontrolowania przez administratorów kont utworzonych dla usługi RMS dla użytkowników indywidualnych

>*Dotyczy: Azure Information Protection*


Jeśli nie chcesz przekształcać subskrypcji usługi RMS dla użytkowników indywidualnych organizacji na subskrypcję płatną, możesz nadal kontrolować konta użytkowników w katalogu Azure utworzonym dla organizacji przy użyciu następujących metod:

-   Wdrożenie rozwiązań integracji katalogów dla usługi Azure Active Directory i infrastruktury Usług domenowych Active Directory. Możesz zsynchronizować konta i hasła, tak aby użytkownicy nie musieli tworzyć nowych kont w celu korzystania z usługi Rights Management. Lokalne zasady haseł będą stosować się do nowych kont użytkowników platformy Azure. Możesz także zsynchronizować hasła, aby użytkownicy nie musieli pamiętać różnych haseł w celu korzystania z usługi Rights Management.

-   Możesz zablokować rejestrację użytkowników w celu korzystania z usługi Azure Rights Management przy użyciu subskrypcji usługi RMS dla użytkowników indywidualnych. W większości przypadków korzyści z tego są niewielkie, ponieważ użytkownicy udostępniają pliki bez zabezpieczeń (co może narażać firmę na ryzyko) lub korzystają z innego mechanizmu ochrony plików, który nie zapewnia działowi IT opcji dostępu do danych. Jeśli jednak chcesz zapobiec rejestrowaniu się użytkowników w celu korzystania z usługi RMS dla użytkowników indywidualnych, wykonaj jedno z poniższych działań po przejęciu praw własności do katalogu organizacji na platformie Azure:

    -   Zablokuj rejestrację wszystkich użytkowników do subskrypcji samoobsługowych, w tym usługi RMS dla użytkowników indywidualnych.  Obecnie nie można wykonać tego działania dla poszczególnych usług. Ustawienie obowiązuje dla wszystkich subskrypcji platformy Azure, które korzystają z samoobsługi. W tym celu ustaw wartość false dla parametru **AllowAdHocSubscriptions** przy użyciu polecenia cmdlet [Set-MsolCompanySettings](http://technet.microsoft.com/library/dn194127.aspx) w module PowerShell dla usługi Azure Active Directory. Na przykład: **Set-MsolCompanySettings -AllowAdHocSubscriptions $false**

    -   Zablokuj tworzenie nowych kont użytkowników na platformie Azure. Oznacza to, że tylko użytkownicy mający już konto na platformie Azure mogą zarejestrować się do subskrypcji samoobsługowych, w tym usługi RMS dla użytkowników indywidualnych.  W tym celu ustaw wartość false dla parametru **AllowEmailVerifiedUsers** przy użyciu polecenia cmdlet [Set-MsolCompanySettings](http://technet.microsoft.com/library/dn194127.aspx) w module PowerShell dla usługi Azure Active Directory. Na przykład: **Set-MsolCompanySettings -AllowEmailVerifiedUsers $false -AllowAdHocSubscriptions $true**

    -   Zsynchronizuj infrastrukturę Usług domenowych Active Directory z usługą Azure Active Directory. Ta akcja uniemożliwia tworzenie nowych kont przy rejestrowaniu użytkowników do subskrypcji samoobsługowych, takich jak usługa RMS dla użytkowników indywidualnych, a także pozwala na usuwanie i wyłączanie kont utworzonych wcześniej w katalogu platformy Azure.

Aby kontrolować konta użytkowników w katalogu platformy Azure lub zapobiec rejestrowaniu użytkowników w usługach RMS dla użytkowników indywidualnych, należy mieć subskrypcję platformy Azure i prawa własności do katalogu. Jeśli nie masz jeszcze subskrypcji platformy Azure, możesz uzyskać ją bezpłatnie. Jeśli Twój katalog został utworzony automatycznie podczas procesu samoobsługowego, przejmij prawa własności do domeny użytej do jego utworzenia. Jeśli masz już katalog na platformie Azure, ale użytkownicy określili nową domenę używaną w organizacji, połącz tę domenę z istniejącym katalogiem. Aby uzyskać więcej informacji, zapoznaj się z instrukcjami w temacie [Czym jest rejestracja samoobsługowa na platformie Azure?](https://azure.microsoft.com/documentation/articles/active-directory-self-service-signup/)


## <a name="next-steps"></a>Następne kroki

Jeśli to użytkownicy, a nie administratorzy, mogą tworzyć swoje konta w usłudze Azure Active Directory dla usługi RMS dla użytkowników indywidualnych, jak można sprawdzić, czy wykonali te działania?  Zobacz [Jak sprawdzić, czy użytkownicy utworzyli konto usługi RMS dla użytkowników indywidualnych](rms-for-individuals-identify-sign-up.md).

[!INCLUDE[Commenting house rules](../includes/houserules.md)]