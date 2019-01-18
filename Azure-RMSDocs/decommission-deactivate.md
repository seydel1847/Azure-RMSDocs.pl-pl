---
title: Likwidacja i dezaktywacja usługi Azure RMS
description: Informacje i instrukcje, gdy już nie chcesz korzystać z ochrony opartej na chmurze usługi Azure Information Protection.
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 12/12/2018
ms.topic: conceptual
ms.service: information-protection
ms.assetid: 0b1c2064-0d01-45ae-a541-cebd7fd762ad
ms.reviewer: esaggese
ms.suite: ems
ms.openlocfilehash: 9e1b7134beaccfe4032da700ebdab1682afce90b
ms.sourcegitcommit: 9dc6da0fb7f96b37ed8eadd43bacd1c8a1a55af8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/18/2019
ms.locfileid: "54393916"
---
# <a name="decommissioning-and-deactivating-protection-for-azure-information-protection"></a>Likwidowanie i dezaktywowanie ochrony usługi Azure Information Protection

>*Dotyczy: [Usługa Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection), [usługi Office 365](https://download.microsoft.com/download/E/C/F/ECF42E71-4EC0-48FF-AA00-577AC14D5B5C/Azure_Information_Protection_licensing_datasheet_EN-US.pdf)*

Ty masz zawsze kontrolę nad tym tego, czy organizacja chroni zawartość za pomocą usługi Azure Rights Management z usługi Azure Information Protection. Jeśli zdecydujesz, że nie chcesz korzystać z tej informacji usługi ochrony, możesz mieć pewność, że użytkownik nie zostanie zablokowana zawartość, która była wcześniej chroniona.

Jeśli nie potrzebujesz ciągłego dostępu do wcześniej chronionej zawartości, należy dezaktywować usługę i zaczekać na wygaśnięcie subskrypcji usługi Azure Information Protection. Takie rozwiązanie byłoby na przykład odpowiednie w sytuacji, gdy testowanie usługi Azure Information Protection zakończyło się przed wdrożeniem jej w środowisku produkcyjnym.

Jednak jeśli wdrożeniu usługi Azure Information Protection w środowisku produkcyjnym i chronione dokumenty i wiadomości e-mail, upewnij się, że masz kopię klucza dzierżawy usługi Azure Information Protection, przed dezaktywowaniem usługi Azure Rights Management. Upewnij się, że masz kopię klucza przed wygaśnięciem subskrypcji, aby upewnić się, że można zachować dostęp do zawartości, która była chroniona przez usługę Azure Rights Management Po dezaktywowaniu tej usługi. Jeśli używasz dostarczania własnego klucza rozwiązania (BYOK) gdzie Generowanie i zarządzać własnym kluczem w module HSM, masz już klucz dzierżawy usługi Azure Information Protection. Ale jeśli został on zarządzany przez firmę Microsoft (ustawienie domyślne), zapoznaj się z instrukcjami dla eksportu klucza dzierżawy w [operacje związane z kluczem dzierżawy usługi Azure Information Protection](operations-tenant-key.md) artykułu.

> [!TIP]
> Nawet po wygaśnięciu subskrypcji dzierżawa usługi Azure Information Protection pozostaje dostępna, co umożliwia korzystanie z zawartości przez dłuższy czas. Nie można już jednak eksportować klucza dzierżawy.

Jeśli masz klucz dzierżawy usługi Azure Information Protection, możesz wdrożyć usługę Rights Management (AD RMS) lokalnie i zaimportować klucz dzierżawy jako zaufaną domenę publikacji (TPD, Trusted Publishing Domain). Następnie możesz wybrać następujące opcje likwidowania wdrożenia usługi Azure Information Protection:


|                                                                                                          Jeśli dotyczy to Ciebie...                                                                                                          |                                                                                                                                                                                                                                                                                                                                                                                                               … Czynności                                                                                                                                                                                                                                                                                                                                                                                                               |
|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|                                                Chcesz, aby wszyscy użytkownicy nadal używali usługi Rights Management, ale za pomocą rozwiązania lokalnego, a nie usługi Azure Information Protection    →                                                 | Użyj polecenia cmdlet [Set-AadrmMigrationUrl](/powershell/module/aadrm/Set-AadrmMigrationUrl), aby przekierować istniejących użytkowników do wdrożenia lokalnego, jeśli używają oni zawartości chronionej po tej zmianie. Użytkownicy będą automatycznie używać instalacji usług AD RMS w przypadku korzystania z chronionej zawartości.<br /><br />Aby użytkownicy mogli korzystać z zawartości, która była chroniona przed wprowadzeniem tej zmiany, przekierować klientów do wdrożenia lokalnego przy użyciu **LicensingRedirection** klucza rejestru dla pakietu Office 2016 lub Office 2013. Aby uzyskać instrukcje, zobacz [sekcji dotyczącej odnajdowania usługi](./rms-client/client-deployment-notes.md) w uwagi dotyczące wdrażania klienta RMS, a **LicenseServerRedirection** klucza rejestru dla pakietu Office 2010, zgodnie z opisem w [pakietu Office Ustawienia rejestru](https://technet.microsoft.com/library/dd772637%28v=ws.10%29.aspx). |
|                                                                                   Chcesz całkowicie zrezygnować z technologii Rights Management    →                                                                                    |                 Przyznaj wyznaczonym administratora [prawa administratora](configure-super-users.md) i zainstaluj [klienta Azure Information Protection](./rms-client/client-admin-guide-install.md) dla tego użytkownika.<br /><br />Administrator ten może następnie używać modułu programu PowerShell z tego klienta do zbiorczego odszyfrowywania plików w folderach, które były chronione przez usługę Azure Rights Management. Pliki anulowanie ochrony i odczytywanie ich bez użycia technologii Rights Management, takiej jak usługi Azure Information Protection ani usług AD RMS. Ponieważ ten moduł programu PowerShell z usługą Azure Rights Management z usługi Azure Information Protection i AD RMS, do wyboru masz odszyfrowywania plików przed lub Po dezaktywowaniu usługi Azure Rights Management lub kombinacji.                 |
| Nie jesteś w stanie zidentyfikować wszystkich plików, które były chronione przez usługę Azure Rights Management z usługi Azure Information Protection. Lub, aby wszyscy użytkownicy mogli automatycznie odczytywać chronione pliki, które zostały pominięte → |                                                                 Wdróż ustawienie rejestru na wszystkich komputerach klienckich przy użyciu klucza rejestru **LicensingRedirection** dla pakietu Office 2016 lub Office 2013, zgodnie z opisem w [sekcji dotyczącej odnajdowania usługi](./rms-client/client-deployment-notes.md) w uwagach do wdrażania klienta usług RMS, lub klucza rejestru **LicenseServerRedirection** dla pakietu Office 2010, zgodnie z opisem w temacie [Office Registry Settings](https://technet.microsoft.com/library/dd772637%28v=ws.10%29.aspx) (Ustawienia rejestru pakietu Office).<br /><br />Wdróż również inne ustawienie rejestru, aby uniemożliwić użytkownikom ochronę nowych plików, ustawiając opcję **DisableCreation** na **1**, zgodnie z opisem w temacie [Office Registry Settings](https://technet.microsoft.com/library/dd772637%28v=ws.10%29.aspx) (Ustawienia rejestru pakietu Office).                                                                  |
|                                                                             Potrzebujesz kontrolowanej usługi z możliwością odzyskiwania ręcznego w przypadku wszystkich pominiętych plików    →                                                                             |                                                                                                                                      Przyznaj wyznaczonym użytkownikom w grupie odzyskiwania danych [prawa administratora](configure-super-users.md) i zainstaluj [klienta Azure Information Protection](./rms-client/client-admin-guide-install.md) dla tych użytkowników, aby mogli anulować ochronę plików zleconą tej akcji przez Użytkownicy standardowi.<br /><br />Na wszystkich komputerach wdróż ustawienie rejestru, aby uniemożliwić użytkownikom ochronę nowych plików, ustawiając opcję **DisableCreation** na wartość **1**, zgodnie z opisem w temacie [Office Registry Settings](https://technet.microsoft.com/library/dd772637%28v=ws.10%29.aspx) (Ustawienia rejestru pakietu Office).                                                                                                                                      |

Więcej informacji na temat procedur opisanych w tej tabeli można znaleźć w następujących zasobach:

- Informacje na temat dokumentacji usługi AD RMS i wdrożeń można znaleźć w temacie [Omówienie usług Active Directory Rights Management](https://technet.microsoft.com/library/hh831364.aspx).

- Aby uzyskać instrukcje dotyczące importowania klucza dzierżawy usługi Azure Information Protection jako pliku TPD, zobacz [Dodawanie zaufanej domeny publikacji](https://technet.microsoft.com/library/cc771460.aspx).

- Aby zainstalować moduł programu Windows PowerShell dla usługi Azure Rights Management, można ustawić adresu URL migracji, zobacz [Instalowanie modułu AADRM programu PowerShell](install-powershell.md).

- Aby użyć programu PowerShell z klientem usługi Azure Information Protection, zobacz [przy użyciu programu PowerShell z klientem usługi Azure Information Protection](./rms-client/client-admin-guide-powershell.md).

Gdy wszystko będzie gotowe do zdezaktywowania usługi Azure Rights Management w organizacji, postępuj zgodnie z poniższymi instrukcjami.

## <a name="deactivating-rights-management"></a>Dezaktywowanie usługi Rights Management
Użyj jednej z poniższych procedur, aby zdezaktywować usługę Azure Rights Management.

> [!TIP]
> Możesz również użyć polecenia cmdlet programu Windows PowerShell, [Disable-Aadrm](/powershell/module/aadrm/disable-aadrm), aby zdezaktywować usługę Rights Management.

#### <a name="to-deactivate-rights-management-from-the-office-365-admin-center"></a>Aby zdezaktywować usługę Rights Management w centrum administracyjnym usługi Office 365

1. Przejdź na [stronę usługi Rights Management](https://account.activedirectory.windowsazure.com/RmsOnline/Manage.aspx) dla administratorów usługi Office 365.

    Po wyświetleniu monitu o zalogowanie użyj konta administratora globalnego usługi Office 365.    

2. Na stronie **Rights Management** kliknij pozycję **Dezaktywuj**.

3.  Po wyświetleniu monitu **czy chcesz dezaktywować usługę Rights Management?** kliknij **dezaktywować**.

Teraz powinien pojawić się komunikat **Usługa Rights Management nie została aktywowana** oraz opcja jej aktywowania.

#### <a name="to-deactivate-rights-management-from-the-azure-portal"></a>Aby zdezaktywować usługę Rights Management w witrynie Azure portal

1. Jeśli jeszcze tego nie zrobiono, Otwórz nowe okno przeglądarki i [Zaloguj się do witryny Azure portal](configure-policy.md#signing-in-to-the-azure-portal). Następnie przejdź do bloku **Azure Information Protection**.

    Na przykład w menu Centrum kliknij pozycję **wszystkich usług** i zacznij wpisywać **informacji** w polu filtru. Wybierz pozycję **Azure Information Protection**.

2. W pierwszym **usługi Azure Information Protection** bloku wybierz **Aktywacja ochrony**. 

3.  Na **usługi Azure Information Protection — Aktywacja ochrony** bloku wybierz **Dezaktywuj**. Wybierz **tak** o potwierdzenie wyboru.

Wyświetla pasek informacji **dezaktywacja została zakończona pomyślnie** i **Dezaktywuj** zostanie zastąpiona przez **Aktywuj**. 




