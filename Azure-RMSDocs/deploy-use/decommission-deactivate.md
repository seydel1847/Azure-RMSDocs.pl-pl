---
title: "Likwidacja i dezaktywacja usługi Azure RMS"
description: "Informacje i instrukcje dotyczące sytuacji, gdy nie chcesz już używać tego rozwiązania ochrony informacji w ramach usługi Azure Information Protection."
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 05/30/2017
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: 0b1c2064-0d01-45ae-a541-cebd7fd762ad
ms.reviewer: esaggese
ms.suite: ems
ms.openlocfilehash: 6dc6a42cf6d4a5e7a2768c927a75522a265432f7
ms.sourcegitcommit: 04eb4990e2bf0004684221592cb93df35e6acebe
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/30/2017
---
# <a name="decommissioning-and-deactivating-azure-rights-management"></a>Likwidowanie i dezaktywowanie usługi Azure Rights Management

>*Dotyczy: Azure Information Protection, Office 365*

To Ty masz zawsze kontrolę nad tym, czy organizacja chroni zawartość za pomocą usługi Azure Rights Management w ramach usługi Azure Information Protection. Jeśli nie chcesz już korzystać z tej usługi do ochrony informacji, możesz mieć pewność, że poprzednio chroniona zawartość nie zostanie zablokowana. Jeśli nie musisz mieć ciągłego dostępu do wcześniej chronionej zawartości, możesz po prostu dezaktywować usługę i zaczekać, aż subskrypcja usługi Azure Information Protection wygaśnie. Takie rozwiązanie byłoby na przykład odpowiednie w sytuacji, gdy testowanie usługi Azure Information Protection zakończyło się przed wdrożeniem jej w środowisku produkcyjnym.

Jeśli jednak usługa Azure Information Protection została wdrożona do produkcji i chroniła dokumenty oraz wiadomości e-mail, przed dezaktywowaniem usługi Azure Rights Management upewnij się, że masz kopię klucza dzierżawy usługi Azure Information Protection. Zrób to przed wygaśnięciem subskrypcji — dzięki temu zachowasz dostęp do zawartości, która była chroniona przez usługę Azure Rights Management, po dezaktywowaniu tej usługi. W przypadku użycia rozwiązania BYOK (Bring Your Own Key) umożliwiającego generowanie własnego klucza i zarządzanie nim w module HSM będziesz już mieć klucz dzierżawy usługi Azure Information Protection. Jeśli jednak był to klucz zarządzany przez firmę Microsoft (opcja domyślna), zapoznaj się z instrukcjami dotyczącymi eksportowania klucza dzierżawy w artykule [Operacje dotyczące klucza dzierżawy usługi Azure Rights Management](operations-tenant-key.md).

> [!TIP]
> Nawet po wygaśnięciu subskrypcji dzierżawa usługi Azure Information Protection pozostaje dostępna, co umożliwia korzystanie z zawartości przez dłuższy czas. Nie można już jednak eksportować klucza dzierżawy.

Jeśli masz klucz dzierżawy usługi Azure Information Protection, możesz wdrożyć usługę Rights Management (AD RMS) lokalnie i zaimportować klucz dzierżawy jako zaufaną domenę publikacji (TPD, Trusted Publishing Domain). Następnie możesz wybrać następujące opcje likwidowania wdrożenia usługi Azure Information Protection:

|Jeśli dotyczy to Ciebie...|… Czynności|
|----------------------------|--------------|
|Chcesz, aby wszyscy użytkownicy nadal używali usługi Rights Management, ale za pomocą rozwiązania lokalnego, a nie usługi Azure Information Protection    →|Użyj polecenia cmdlet [Set-AadrmMigrationUrl](/powershell/module/aadrm/Set-AadrmMigrationUrl), aby przekierować istniejących użytkowników do wdrożenia lokalnego, jeśli używają oni zawartości chronionej po tej zmianie. Użytkownicy będą automatycznie używać instalacji usług AD RMS w przypadku korzystania z chronionej zawartości.<br /><br />Aby użytkownicy mogli korzystać z zawartości, która była chroniona przed wprowadzeniem tej zmiany, musisz przekierować klientów do wdrożenia lokalnego przy użyciu klucza rejestru **LicensingRedirection** dla pakietu Office 2016 lub Office 2013, zgodnie z opisem w [sekcji dotyczącej odnajdowania usługi](../rms-client/client-deployment-notes.md) w uwagach do wdrażania klienta usług RMS, lub klucza rejestru **LicenseServerRedirection** dla pakietu Office 2010, zgodnie z opisem w temacie [Office Registry Settings](https://technet.microsoft.com/library/dd772637%28v=ws.10%29.aspx) (Ustawienia rejestru pakietu Office).|
|Chcesz całkowicie zrezygnować z technologii Rights Management    →|Przyznaj wyznaczonemu użytkownikowi [prawa administratora](../deploy-use/configure-super-users.md) i udostępnij mu [narzędzie RMS Protection Tool](http://www.microsoft.com/en-us/download/details.aspx?id=47256).<br /><br />Administrator ten może następnie używać narzędzia do zbiorczego odszyfrowywania plików w folderach, które były chronione przez usługę Azure Rights Management. Pozwala to na anulowanie ochrony plików i odczytywanie ich bez użycia technologii Rights Management, takiej jak usługa Azure Information Protection lub AD RMS. To narzędzie może współpracować z usługami AD RMS i Azure Rights Management w ramach usługi Azure Information Protection, dlatego możesz odszyfrować pliki przed lub po dezaktywowaniu usługi Azure Rights Management lub w kombinacji tych sytuacji.|
|Nie możesz zidentyfikować wszystkich plików, które były chronione przez usługę Azure Rights Management w ramach usługi Azure Information Protection, lub chcesz, aby wszyscy użytkownicy mogli automatycznie odczytywać wszystkie pominięte chronione pliki    →|Wdróż ustawienie rejestru na wszystkich komputerach klienckich przy użyciu klucza rejestru **LicensingRedirection** dla pakietu Office 2016 lub Office 2013, zgodnie z opisem w [sekcji dotyczącej odnajdowania usługi](../rms-client/client-deployment-notes.md) w uwagach do wdrażania klienta usług RMS, lub klucza rejestru **LicenseServerRedirection** dla pakietu Office 2010, zgodnie z opisem w temacie [Office Registry Settings](https://technet.microsoft.com/library/dd772637%28v=ws.10%29.aspx) (Ustawienia rejestru pakietu Office).<br /><br />Wdróż również inne ustawienie rejestru, aby uniemożliwić użytkownikom ochronę nowych plików, ustawiając opcję **DisableCreation** na **1**, zgodnie z opisem w temacie [Office Registry Settings](https://technet.microsoft.com/library/dd772637%28v=ws.10%29.aspx) (Ustawienia rejestru pakietu Office).|
|Potrzebujesz kontrolowanej usługi z możliwością odzyskiwania ręcznego w przypadku wszystkich pominiętych plików    →|Przyznaj wyznaczonym użytkownikom w grupie odzyskiwania danych [prawa administratora](../deploy-use/configure-super-users.md) i udostępnij im [Narzędzie ochrony usługi RMS](http://www.microsoft.com/en-us/download/details.aspx?id=47256), aby mogli anulować ochronę plików zleconą przez użytkowników standardowych.<br /><br />Na wszystkich komputerach wdróż ustawienie rejestru, aby uniemożliwić użytkownikom ochronę nowych plików, ustawiając opcję **DisableCreation** na wartość **1**, zgodnie z opisem w temacie [Office Registry Settings](https://technet.microsoft.com/library/dd772637%28v=ws.10%29.aspx) (Ustawienia rejestru pakietu Office).|
Więcej informacji na temat procedur opisanych w tej tabeli można znaleźć w następujących zasobach:

-   Informacje na temat dokumentacji usługi AD RMS i wdrożeń można znaleźć w temacie [Omówienie usług Active Directory Rights Management](https://technet.microsoft.com/library/hh831364.aspx).

-   Aby uzyskać instrukcje dotyczące importowania klucza dzierżawy usługi Azure Information Protection jako pliku TPD, zobacz [Dodawanie zaufanej domeny publikacji](https://technet.microsoft.com/library/cc771460.aspx).

-   Aby zainstalować moduł programu Windows PowerShell dla usługi Azure Rights Management w celu ustawienia adresu URL migracji, zobacz [Instalowanie programu Windows PowerShell dla usługi Azure Rights Management](install-powershell.md).

Gdy wszystko będzie gotowe do zdezaktywowania usługi Azure Rights Management w organizacji, postępuj zgodnie z poniższymi instrukcjami.

## <a name="deactivating-rights-management"></a>Dezaktywowanie usługi Rights Management
Wykonaj kroki jednej z poniższych procedur, aby zdezaktywować usługę [!INCLUDE[aad_rightsmanagement_1](../includes/aad_rightsmanagement_1_md.md)].

> [!TIP]
> Możesz również użyć polecenia cmdlet programu Windows PowerShell, [Disable-Aadrm](/powershell/module/aadrm/disable-aadrm), aby zdezaktywować usługę [!INCLUDE[aad_rightsmanagement_2](../includes/aad_rightsmanagement_2_md.md)].

#### <a name="to-deactivate-rights-management-from-the-office-365-admin-center"></a>Aby zdezaktywować usługę Rights Management w centrum administracyjnym usługi Office 365

1. Przejdź na [stronę usługi Rights Management](https://account.activedirectory.windowsazure.com/RmsOnline/Manage.aspx) dla administratorów usługi Office 365.
    
    Po wyświetleniu monitu o zalogowanie użyj konta administratora globalnego usługi Office 365.    

2. Na stronie **Rights Management** kliknij pozycję **Dezaktywuj**.

3.  Po wyświetleniu monitu **Czy chcesz dezaktywować usługę Rights Management?** kliknij pozycję **Dezaktywuj**.

Teraz powinien pojawić się komunikat **Usługa Rights Management nie została aktywowana** oraz opcja jej aktywowania.

#### <a name="to-deactivate-rights-management-from-the-azure-classic-portal"></a>Aby zdezaktywować usługę Rights Management w klasycznym portalu Azure

1.  Zaloguj się do [klasycznego portalu Azure](http://go.microsoft.com/fwlink/p/?LinkID=275081).

2.  W okienku po lewej stronie kliknij opcję **ACTIVE DIRECTORY**.

3.  Na stronie **Active Directory** kliknij pozycję **RIGHTS MANAGEMENT**.

4.  Upewnij się, że Twoja nazwa dzierżawy jest zaznaczona, kliknij przycisk **DEZAKTYWUJ**, a następnie potwierdź działanie.

**STAN USŁUGI RIGHTS MANAGEMENT** powinien być teraz ustawiony na wartość **Nieaktywna**, a opcja **DEZAKTYWUJ** zostaje zastąpiona opcją **AKTYWUJ**.

[!INCLUDE[Commenting house rules](../includes/houserules.md)]


