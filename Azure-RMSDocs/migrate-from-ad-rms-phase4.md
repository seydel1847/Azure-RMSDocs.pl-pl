---
title: Migrowanie z usługi AD RMS do usługi Azure Information Protection — faza 4
description: Faza 4 migracji z usługi AD RMS do usługi Azure Information Protection, obejmująca kroki od 8 do 9 z sekcji Migrowanie z usługi AD RMS do usługi Azure Information Protection.
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 12/12/2018
ms.topic: conceptual
ms.service: information-protection
ms.assetid: 8b039ad5-95a6-4c73-9c22-78c7b0e12cb7
ms.reviewer: esaggese
ms.suite: ems
ms.openlocfilehash: d694876a91e0d39d0d429e5dd5503bb153fd5521
ms.sourcegitcommit: 1d2912b4f0f6e8d7596cbf31e2143a783158ab11
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/12/2018
ms.locfileid: "53305458"
---
# <a name="migration-phase-4---supporting-services-configuration"></a>Faza 4 migracji — konfiguracja usług pomocniczych

>*Dotyczy: Usługi Active Directory Rights Management Services, [usługi Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection), [usługi Office 365](https://download.microsoft.com/download/E/C/F/ECF42E71-4EC0-48FF-AA00-577AC14D5B5C/Azure_Information_Protection_licensing_datasheet_EN-US.pdf)*


Skorzystaj z poniższych informacji dotyczących fazy 4 migrowania z usługi AD RMS do usługi Azure Information Protection. Te procedury obejmują kroki od 8 do 9 z sekcji [Migrowanie z usługi AD RMS do usługi Azure Information Protection](migrate-from-ad-rms-to-azure-rms.md).



## <a name="step-8-configure-irm-integration-for-exchange-online"></a>Krok 8. Konfigurowanie integracji funkcji IRM na potrzeby usługi Exchange Online

> [!IMPORTANT]
> Ponieważ nie można kontrolować użytkowników poddanych migracji grupę adresatów, którzy mogą wybrać dla chronionych wiadomości e-mail, upewnij się, że wszyscy użytkownicy i grupy obsługujące pocztę w Twojej organizacji mają konta w usłudze Azure AD, które mogą być używane z usługi Azure Information Protection. [Więcej informacji](prepare.md)

Niezależnie od siebie z dzierżawy usługi Azure Information Protection topologii klucza, która została wybrana, wykonaj następujące czynności:

1. Dla programu Exchange Online, aby można było odszyfrować wiadomości e-mail, które są chronione przez usługi AD RMS musi wiedzieć, że adres URL AD RMS dla klastra odnosi się do klucza, który jest dostępny w dzierżawie. Można to zrobić przy użyciu rekordu DNS SRV dla klastra usługi AD RMS, który umożliwia również ponowne konfigurowanie klientów pakietu Office do korzystania z usługi Azure Information Protection. Jeśli nie utworzono rekordu DNS SRV dla ponowna konfiguracja klienta w kroku 7, należy utworzyć teraz ten rekord do obsługi usługi Exchange Online. [Instrukcje](migrate-from-ad-rms-phase3.md#client-reconfiguration-by-using-dns-redirection)
    
    Podczas tego rekordu DNS znajduje się w miejscu, a użytkownicy przy użyciu programu Outlook w sieci web i klientów mobilnych poczty e-mail będą mogli wyświetlić usług AD RMS chronionych wiadomości e-mail w tych aplikacji i programu Exchange będzie można użyć klucza, zaimportowane z usługi AD RMS do odszyfrowania, indeksu , dziennika i ochrona zawartości, która jest chroniona przez usługi AD RMS.  

2. Uruchamianie usługi Exchange Online [Get-IRMConfiguration] (https://technet.microsoft.com/library/dd776120(v=exchg.160\).aspx) polecenia. Jeśli potrzebujesz pomocy, uruchomienie tego polecenia, zobacz instrukcje krok po kroku z [usługi Exchange Online: Konfiguracja usługi IRM](configure-office365.md#exchange-online-irm-configuration).
    
    Z danych wyjściowych, sprawdź, czy **AzureRMSLicensingEnabled** ustawiono **True**:
    
    - Jeśli ustawiono AzureRMSLicensingEnabled **True**, żadna dalsza konfiguracja jest wymagane dla tego kroku. 
    
    - Jeśli ustawiono AzureRMSLicensingEnabled **False**Uruchom `Set-IRMConfiguration -AzureRMSLicensingEnabled $true` i następnie skorzystaj z procedury weryfikacji [skonfigurować nowe możliwości szyfrowanie wiadomości usługi Office 365 korzystających z usługi Azure Information Protection](https://support.office.com/article/7ff0c040-b25c-4378-9904-b1b50210d00e)aby upewnić się, że usługa Exchange Online jest teraz gotowe do użycia usługi Azure Rights Management. 

## <a name="step-9-configure-irm-integration-for-exchange-server-and-sharepoint-server"></a>Krok 9. Konfigurowanie integracji funkcji IRM dla programów Exchange Server i SharePoint Server

Jeśli w przypadku użycia funkcji Zarządzanie prawami do informacji (IRM) programu Exchange Server lub SharePoint Server z usługami AD RMS, musisz wdrożyć łącznik usługi Rights Management (RMS), który działa jako interfejs komunikacji (przekaźnik) między lokalną serwery i usługą ochrony dla usługi Azure Information Protection.

Ten krok obejmuje instalowanie i konfigurowanie łącznika, wyłączanie usługi IRM dla programów Exchange i SharePoint oraz konfigurowanie tych serwerów do korzystania z łącznika. Na koniec — jeśli do usługi Azure Information Protection zaimportowano pliki danych konfiguracji usługi AD RMS (XML) użyte do ochrony wiadomości e-mail — należy ręcznie zmodyfikować rejestr na komputerach z programem Exchange Server, aby przekierować wszystkie adresy URL zaufanych domen publikacji do łącznika usługi RMS.

> [!NOTE]
> Przed rozpoczęciem sprawdź wersje serwerów lokalnych obsługujących usługę Azure Rights Management zgodnie z opisem w sekcji [Serwery lokalne, które obsługują usługę Azure RMS](./requirements-servers.md).

### <a name="install-and-configure-the-rms-connector"></a>Instalowanie i konfigurowanie łącznika usługi RMS

Postępuj zgodnie z instrukcjami w artykule [Wdrażanie łącznika usługi Azure Rights Management](./deploy-rms-connector.md) i wykonaj kroki od 1 do 4. Nie rozpoczynaj jeszcze kroku 5 z poziomu instrukcji łącznika. 

### <a name="disable-irm-on-exchange-servers-and-remove-ad-rms-configuration"></a>Wyłączanie funkcji IRM na serwerach Exchange Server i usuwanie konfiguracji usługi AD RMS

1.  Na każdym serwerze programu Exchange znajdź następujący folder i usuń z niego wszystkie wpisy: **\ProgramData\Microsoft\DRM\Server\S-1-5-18**

2. Z jednego z serwerów programu Exchange uruchom następujące polecenia programu PowerShell, aby upewnić się, że użytkownicy będą mogli czytać wiadomości e-mail chronione za pomocą usługi Azure Rights Management.

    Przed uruchomieniem tych poleceń zastąp własnym adresem URL usługi Azure Rights Management element *\<Twój adres URL dzierżawy>*.

        $irmConfig = Get-IRMConfiguration
        $list = $irmConfig.LicensingLocation 
        $list += "<Your Tenant URL>/_wmcs/licensing"
        Set-IRMConfiguration -LicensingLocation $list

3.  Teraz wyłącz funkcje IRM dla wiadomości wysyłanych do adresatów wewnętrznych:

    ```
    Set-IRMConfiguration -InternalLicensingEnabled $false
    ```

4. Następnie użyj tego samego polecenia cmdlet, aby wyłączyć funkcję IRM w aplikacji Microsoft Office Outlook Web App i programie Microsoft Exchange ActiveSync:

    ```
    Set-IRMConfiguration -ClientAccessServerEnabled $false
    ```

5.  Na koniec użyj tego samego polecenia cmdlet, aby wyczyścić wszystkie buforowane certyfikaty:

    ```
    Set-IRMConfiguration -RefreshServerCertificates
    ```

6.  Na każdym serwerze Exchange Server zresetuj usługi IIS, na przykład uruchamiając wiersz polecenia jako administrator, a następnie wpisując ciąg **iisreset**.

### <a name="disable-irm-on-sharepoint-servers-and-remove-ad-rms-configuration"></a>Wyłączanie funkcji IRM na serwerach SharePoint Server i usuwanie konfiguracji usługi AD RMS

1.  Upewnij się, że nie istnieją żadne dokumenty wyewidencjonowane z bibliotek chronionych za pomocą usługi RMS. Jeśli takie dokumenty istnieją, po zakończeniu wykonywania tej procedury staną się niedostępne.

2.  W witrynie Administracja centralna programu SharePoint w sieci Web w sekcji **Szybkie uruchamianie** kliknij pozycję **Zabezpieczenia**.

3.  Na stronie **Zabezpieczenia** w sekcji **Zasady dotyczące informacji** kliknij pozycję **Konfiguruj zarządzanie prawami do informacji**.

4.  Na stronie **Zarządzanie prawami do informacji** w sekcji **Zarządzanie prawami do informacji** zaznacz pole **Nie używaj usługi IRM na tym serwerze**, a następnie kliknij przycisk **OK**.

5.  Na każdym komputerze z programem SharePoint Server usuń zawartość folderu \ProgramData\Microsoft\MSIPC\Server\\<*Identyfikator SID konta, na którym działa program SharePoint Server>*.

### <a name="configure-exchange-and-sharepoint-to-use-the-connector"></a>Konfigurowanie programów Exchange i SharePoint do używania łącznika

1. Wróć do instrukcji dotyczących wdrażania łącznika usług RMS: [Krok 5: Konfigurowanie serwerów do korzystania z łącznika usługi RMS](./configure-servers-rms-connector.md)

    Jeśli masz tylko serwer SharePoint Server, przejdź prosto do sekcji [Następne kroki](#next-steps), aby kontynuować migrację. 

2. Na każdym serwerze Exchange Server ręcznie dodaj klucze rejestru w następnej sekcji dla każdego zaimportowanego pliku danych konfiguracji (XML) w celu przekierowania adresów URL zaufanych domen publikacji do łącznika usługi RMS. Te wpisy rejestru są specyficzne dla migracji i nie są dodawane przez narzędzie do konfiguracji serwera dla łącznika usługi Microsoft RMS.

    Podczas wprowadzania tych zmian rejestru postępuj zgodnie z następującymi instrukcjami:

    -   Zastąp wartość *nazwa FQDN łącznika* nazwą łącznika zdefiniowaną w systemie DNS. Na przykład **rmsconnector.contoso.com**.

    -   W adresie URL łącznika użyj prefiksu protokołu HTTP lub HTTPS w zależności od protokołu, który ma być używany zgodnie z konfiguracją łącznika podczas komunikacji na serwerach lokalnych.

#### <a name="registry-edits-for-exchange"></a>Zmiany w rejestrze w przypadku programu Exchange

Dla wszystkich serwerów programu Exchange należy dodać następujące wartości rejestru do LicenseServerRedirection, w zależności od Twojej wersji programu Exchange:

---

W przypadku programów Exchange 2013 i Exchange 2016 — edycja rejestru 1:


**Ścieżka rejestru:**

HKLM\SOFTWARE\Microsoft\ExchangeServer\v15\IRM\LicenseServerRedirection

**Typ:** Reg_SZ

**Wartość:** https://\<Adres URL licencjonowania usług AD RMS w sieci intranet\>/_wmcs/licensing

**Dane:**

Jeden z następujących elementów w zależności od tego, czy podczas komunikacji serwera Exchange z łącznikiem usługi RMS jest używany protokół HTTP, czy HTTPS:

- http://\<nazwa FQDN łącznika\>/_wmcs/licensing

- https://\<nazwa FQDN łącznika\>/_wmcs/licensing


---

Programu Exchange 2013 — Edycja rejestru 2:

**Ścieżka rejestru:**

HKLM\SOFTWARE\Microsoft\ExchangeServer\v15\IRM\LicenseServerRedirection 

**Typ:** Reg_SZ

**Wartość:** https://\<Adres URL licencjonowania usług AD RMS w sieci ekstranet\>/_wmcs/licensing

**Dane:**

Jeden z następujących elementów w zależności od tego, czy podczas komunikacji serwera Exchange z łącznikiem usługi RMS jest używany protokół HTTP, czy HTTPS:

- http://\<nazwa FQDN łącznika\>/_wmcs/licensing

- https://\<nazwa FQDN łącznika\>/_wmcs/licensing

---

W przypadku programu Exchange 2010 — edycja rejestru 1:


**Ścieżka rejestru:**

HKLM\SOFTWARE\Microsoft\ExchangeServer\v14\IRM\LicenseServerRedirection

**Typ:** Reg_SZ

**Wartość:** https://\<Adres URL licencjonowania usług AD RMS w sieci intranet\>/_wmcs/licensing

**Dane:**

Jeden z następujących elementów w zależności od tego, czy podczas komunikacji serwera Exchange z łącznikiem usługi RMS jest używany protokół HTTP, czy HTTPS:

- http://\<nazwa FQDN łącznika\>/_wmcs/licensing

- https://\<nazwa łącznika\>/_wmcs/licensing


---

W przypadku programu Exchange 2010 — edycja rejestru 2:


**Ścieżka rejestru:**

HKLM\SOFTWARE\Microsoft\ExchangeServer\v14\IRM\LicenseServerRedirection

**Typ:** Reg_SZ

**Wartość:** https://\<Adres URL licencjonowania usług AD RMS w sieci ekstranet\>/_wmcs/licensing

**Dane:**

Jeden z następujących elementów w zależności od tego, czy podczas komunikacji serwera Exchange z łącznikiem usługi RMS jest używany protokół HTTP, czy HTTPS:

- http://\<nazwa FQDN łącznika\>/_wmcs/licensing

- https://\<nazwa FQDN łącznika\>/_wmcs/licensing

---


## <a name="next-steps"></a>Następne kroki
Aby kontynuować migrację, przejdź do [fazy 5 — zadań po migracji](migrate-from-ad-rms-phase5.md).
