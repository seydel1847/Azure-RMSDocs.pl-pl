---
title: "Likwidacja i dezaktywacja usługi Azure RMS"
description: "Informacje i instrukcje w razie użytkownik nie ma być użyty z ochrony opartej na chmurze usługi Azure Information Protection."
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 02/20/2018
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: 0b1c2064-0d01-45ae-a541-cebd7fd762ad
ms.reviewer: esaggese
ms.suite: ems
ms.openlocfilehash: 18eff00f6b316c48dbca5a9a8ec2c2ab4e58f76c
ms.sourcegitcommit: 67750454f8fa86d12772a0075a1d01a69f167bcb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/23/2018
---
# <a name="decommissioning-and-deactivating-protection-for-azure-information-protection"></a>Likwidowanie i dezaktywowanie ochrony usługi Azure Information Protection

>*Dotyczy: Azure Information Protection, Office 365*

Czy organizacja chroni zawartość za pomocą usługi Azure Rights Management z usługi Azure Information Protection kontroli są zawsze. Jeśli zdecydujesz, że nie chcesz używać tej usługi ochrony informacji, możesz mieć pewność, że nie można zablokować zawartość, która była wcześniej chroniona.

Jeśli nie potrzebujesz nieprzerwanego dostępu do wcześniej chronionej zawartości, należy dezaktywować usługę i subskrypcja usługi Azure Information Protection wygaśnie. Takie rozwiązanie byłoby na przykład odpowiednie w sytuacji, gdy testowanie usługi Azure Information Protection zakończyło się przed wdrożeniem jej w środowisku produkcyjnym.

Jednak jeśli wdrożeniu usługi Azure Information Protection w środowisku produkcyjnym i chronione dokumenty i wiadomości e-mail, upewnij się, czy masz kopię klucza dzierżawy usługi Azure Information Protection, aby zdezaktywować usługę Azure Rights Management. Upewnij się, że masz kopię klucza przed wygaśnięciem subskrypcji, aby upewnić się, że mogą zachować dostęp do zawartości, która była chroniona przez usługę Azure Rights Management Po dezaktywowaniu tej usługi. Jeśli używasz dostarczania własnego klucza rozwiązania (BYOK) gdzie Generowanie i zarządzanie własnym kluczem w module HSM, masz już klucz dzierżawy usługi Azure Information Protection. Jeśli jednak był to klucz zarządzany przez firmę Microsoft (opcja domyślna), zapoznaj się z instrukcjami dotyczącymi eksportowania klucza dzierżawy w artykule [Operacje dotyczące klucza dzierżawy usługi Azure Rights Management](operations-tenant-key.md).

> [!TIP]
> Nawet po wygaśnięciu subskrypcji dzierżawa usługi Azure Information Protection pozostaje dostępna, co umożliwia korzystanie z zawartości przez dłuższy czas. Nie można już jednak eksportować klucza dzierżawy.

Jeśli masz klucz dzierżawy usługi Azure Information Protection, możesz wdrożyć usługę Rights Management (AD RMS) lokalnie i zaimportować klucz dzierżawy jako zaufaną domenę publikacji (TPD, Trusted Publishing Domain). Następnie możesz wybrać następujące opcje likwidowania wdrożenia usługi Azure Information Protection:

|Jeśli dotyczy to Ciebie...|… Czynności|
|----------------------------|--------------|
|Chcesz, aby wszyscy użytkownicy nadal używali usługi Rights Management, ale za pomocą rozwiązania lokalnego, a nie usługi Azure Information Protection    →|Użyj polecenia cmdlet [Set-AadrmMigrationUrl](/powershell/module/aadrm/Set-AadrmMigrationUrl), aby przekierować istniejących użytkowników do wdrożenia lokalnego, jeśli używają oni zawartości chronionej po tej zmianie. Użytkownicy będą automatycznie używać instalacji usług AD RMS w przypadku korzystania z chronionej zawartości.<br /><br />Aby użytkownicy mogli korzystać z zawartości, która była chroniona przed wprowadzeniem tej zmiany, przekierowywania klientów do wdrożenia lokalnego przy użyciu **LicensingRedirection** klucza rejestru dla pakietu Office 2016 lub Office 2013. Aby uzyskać instrukcje, zobacz [sekcji dotyczącej odnajdowania usługi](../rms-client/client-deployment-notes.md) w uwagach do wdrażania klienta RMS i **LicenseServerRedirection** klucza rejestru dla pakietu Office 2010, zgodnie z opisem w [ustawienia rejestru pakietu Office](https://technet.microsoft.com/library/dd772637%28v=ws.10%29.aspx).|
|Chcesz całkowicie zrezygnować z technologii Rights Management    →|Przyznaj wyznaczonym administratora [prawa administratora](../deploy-use/configure-super-users.md) i zainstaluj [klienta Azure Information Protection](../rms-client/client-admin-guide-install.md) dla tego użytkownika.<br /><br />Administrator można następnie użyć modułu programu PowerShell z tego klienta do zbiorczego odszyfrowywania plików w folderach, które były chronione przez usługę Azure Rights Management. Pliki na anulowanie ochrony i odczytywanie ich bez technologii Rights Management, takich jak usługi Azure Information Protection lub usług AD RMS. Ponieważ ten moduł programu PowerShell można używać z usługą Azure Rights Management z usługi Azure Information Protection i AD RMS, użytkownik może odszyfrować pliki przed lub Po dezaktywowaniu usługi Azure Rights Management lub kombinacji.|
|Nie jest możliwe zidentyfikować pliki, które były chronione przez usługę Azure Rights Management z usługi Azure Information Protection. Lub wszyscy użytkownicy mogli automatycznie odczytywać chronione pliki, które zostały pominięte →|Wdróż ustawienie rejestru na wszystkich komputerach klienckich przy użyciu klucza rejestru **LicensingRedirection** dla pakietu Office 2016 lub Office 2013, zgodnie z opisem w [sekcji dotyczącej odnajdowania usługi](../rms-client/client-deployment-notes.md) w uwagach do wdrażania klienta usług RMS, lub klucza rejestru **LicenseServerRedirection** dla pakietu Office 2010, zgodnie z opisem w temacie [Office Registry Settings](https://technet.microsoft.com/library/dd772637%28v=ws.10%29.aspx) (Ustawienia rejestru pakietu Office).<br /><br />Wdróż również inne ustawienie rejestru, aby uniemożliwić użytkownikom ochronę nowych plików, ustawiając opcję **DisableCreation** na **1**, zgodnie z opisem w temacie [Office Registry Settings](https://technet.microsoft.com/library/dd772637%28v=ws.10%29.aspx) (Ustawienia rejestru pakietu Office).|
|Potrzebujesz kontrolowanej usługi z możliwością odzyskiwania ręcznego w przypadku wszystkich pominiętych plików    →|Przyznaj wyznaczonym użytkownikom w grupie odzyskiwania danych [prawa administratora](../deploy-use/configure-super-users.md) i zainstaluj [klienta Azure Information Protection](../rms-client/client-admin-guide-install.md) dla tych użytkowników, aby mogli anulować ochronę plików zleconą tej akcji przez Użytkownicy w wersji Standard.<br /><br />Na wszystkich komputerach wdróż ustawienie rejestru, aby uniemożliwić użytkownikom ochronę nowych plików, ustawiając opcję **DisableCreation** na wartość **1**, zgodnie z opisem w temacie [Office Registry Settings](https://technet.microsoft.com/library/dd772637%28v=ws.10%29.aspx) (Ustawienia rejestru pakietu Office).|
Więcej informacji na temat procedur opisanych w tej tabeli można znaleźć w następujących zasobach:

- Informacje na temat dokumentacji usługi AD RMS i wdrożeń można znaleźć w temacie [Omówienie usług Active Directory Rights Management](https://technet.microsoft.com/library/hh831364.aspx).

- Aby uzyskać instrukcje dotyczące importowania klucza dzierżawy usługi Azure Information Protection jako pliku TPD, zobacz [Dodawanie zaufanej domeny publikacji](https://technet.microsoft.com/library/cc771460.aspx).

- Aby zainstalować moduł programu Windows PowerShell dla usługi Azure Rights Management, aby ustawić adres URL migracji, zobacz [Instalowanie modułu programu PowerShell AADRM](install-powershell.md).

- Przy użyciu klienta usługi Azure Information Protection przy użyciu programu PowerShell, zobacz [przy użyciu programu PowerShell przy użyciu klienta usługi Azure Information Protection](../rms-client/client-admin-guide-powershell.md).

Gdy wszystko będzie gotowe do zdezaktywowania usługi Azure Rights Management w organizacji, postępuj zgodnie z poniższymi instrukcjami.

## <a name="deactivating-rights-management"></a>Dezaktywowanie usługi Rights Management
Wykonaj kroki jednej z poniższych procedur, aby zdezaktywować usługę [!INCLUDE[aad_rightsmanagement_1](../includes/aad_rightsmanagement_1_md.md)].

> [!TIP]
> Możesz również użyć polecenia cmdlet programu Windows PowerShell, [Disable-Aadrm](/powershell/module/aadrm/disable-aadrm), aby zdezaktywować usługę [!INCLUDE[aad_rightsmanagement_2](../includes/aad_rightsmanagement_2_md.md)].

#### <a name="to-deactivate-rights-management-from-the-office-365-admin-center"></a>Aby zdezaktywować usługę Rights Management w centrum administracyjnym usługi Office 365

1. Przejdź na [stronę usługi Rights Management](https://account.activedirectory.windowsazure.com/RmsOnline/Manage.aspx) dla administratorów usługi Office 365.
    
    Po wyświetleniu monitu o zalogowanie użyj konta administratora globalnego usługi Office 365.    

2. Na stronie **Rights Management** kliknij pozycję **Dezaktywuj**.

3.  Po wyświetleniu monitu **czy chcesz dezaktywować usługę Rights Management?** kliknij **dezaktywować**.

Teraz powinien pojawić się komunikat **Usługa Rights Management nie została aktywowana** oraz opcja jej aktywowania.

#### <a name="to-deactivate-rights-management-from-the-azure-portal"></a>Aby zdezaktywować usługę Rights Management w portalu Azure

1. Jeśli jeszcze tego nie zrobiono, Otwórz nowe okno przeglądarki i [Zaloguj się do portalu Azure](configure-policy.md#signing-in-to-the-azure-portal). Następnie przejdź do bloku **Azure Information Protection**.
    
    Na przykład, w menu centralnym kliknij **wszystkie usługi** i zacznij wpisywać ciąg **informacji** w polu filtru. Wybierz pozycję **Azure Information Protection**.

2. Na początkowej **usługi Azure Information Protection** bloku, wybierz opcję **aktywacji ochrony**. 

3.  Na **usługi Azure Information Protection — aktywacji ochrony** bloku, wybierz opcję **Dezaktywuj**. Wybierz **tak** o potwierdzenie wyboru.

Wyświetla pasek informacji **dezaktywacji zakończyło się pomyślnie** i **Dezaktywuj** zastąpione programem **Aktywuj**. 


[!INCLUDE[Commenting house rules](../includes/houserules.md)]


