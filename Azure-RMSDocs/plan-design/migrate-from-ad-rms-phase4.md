---
title: "Migrowanie z usługi AD RMS do usługi Azure Information Protection — faza 4"
description: "Faza 4 migracji z usługi AD RMS do usługi Azure Information Protection, obejmująca kroki od 8 do 9 z sekcji Migrowanie z usługi AD RMS do usługi Azure Information Protection."
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 04/18/2017
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: 8b039ad5-95a6-4c73-9c22-78c7b0e12cb7
ms.reviewer: esaggese
ms.suite: ems
ms.openlocfilehash: 51a689248834f2578655d62752c19b7a387068a5
ms.sourcegitcommit: 237ce3a0cc4921da5a08ed5753e6491403298194
translationtype: HT
---
# <a name="migration-phase-4---supporting-services-configuration"></a>Faza 4 migracji — konfiguracja usług pomocniczych

>*Dotyczy: Active Directory Rights Management Services, Azure Information Protection, Office 365*


Skorzystaj z poniższych informacji dotyczących fazy 4 migrowania z usługi AD RMS do usługi Azure Information Protection. Te procedury obejmują kroki od 8 do 9 z sekcji [Migrowanie z usługi AD RMS do usługi Azure Information Protection](migrate-from-ad-rms-to-azure-rms.md).



## <a name="step-8-configure-irm-integration-for-exchange-online"></a>Krok 8. Konfigurowanie integracji funkcji IRM na potrzeby usługi Exchange Online

Jeśli wcześniej zaimportowano zaufaną domenę publikacji z usługi AD RMS do usługi Exchange Online, należy usunąć tę domenę, aby uniknąć konfliktu szablonów i zasad po przeprowadzeniu migracji do usługi Azure Information Protection. W tym celu użyj polecenia cmdlet [Remove-RMSTrustedPublishingDomain](https://technet.microsoft.com/library/jj200720%28v=exchg.150%29.aspx) w usłudze Exchange Online.

W przypadku wybrania topologii klucza dzierżawy usługi Azure Information Protection **Zarządzany przez firmę Microsoft**:

1. Skorzystaj z instrukcji podanych w sekcji [Usługa Exchange Online: konfiguracja funkcji IRM](../deploy-use/configure-office365.md#exchange-online-irm-configuration) artykułu [Office 365: konfiguracja dla klientów i usług online](../deploy-use/configure-office365.md). Ta sekcja zawiera typowe polecenia uruchamiane w celu nawiązania połączenia z usługą Exchange Online, importowania klucza dzierżawy z usługi Azure Information Protection oraz włączania funkcji IRM na potrzeby usługi Exchange Online. Po wykonaniu tych kroków dostępna będzie pełna funkcjonalność ochrony za pomocą usługi Azure Rights Management z usługą Exchange Online.

2. Oprócz standardowej konfiguracji w celu włączenia funkcji IRM dla usługi Exchange Online uruchom następujące polecenia programu PowerShell, aby upewnić się, że użytkownicy będą mogli czytać wiadomości e-mail, które zostały wysłane z użyciem ochrony za pomocą usług AD RMS.

    Zastąp własną nazwą domeny organizacji element *\<yourcompany.domain>*.

        $irmConfig = Get-IRMConfiguration
        $list = $irmConfig.LicensingLocation
        $list += "https://adrms.<yourcompany.domain>/_wmcs/licensing"
        Set-IRMConfiguration -LicensingLocation $list
        Set-IRMConfiguration -internallicensingenabled $false
        Set-IRMConfiguration -internallicensingenabled $true


W przypadku wybrania topologii klucza dzierżawy usługi Azure Information Protection **Zarządzany przez klienta (BYOK)**:

-   Funkcjonalność ochrony za pomocą usług Rights Management zostanie ograniczona w programie Exchange Online zgodnie z opisem w artykule [Cennik i ograniczenia dotyczące funkcji BYOK](byok-price-restrictions.md).


## <a name="step-9-configure-irm-integration-for-exchange-server-and-sharepoint-server"></a>Krok 9. Konfigurowanie integracji funkcji IRM dla programów Exchange Server i SharePoint Server

W przypadku używania funkcji zarządzania prawami do informacji (IRM) programu Exchange Server lub programu SharePoint Server z usługami AD RMS należy wdrożyć łącznik usługi Rights Management (RMS), który działa jako interfejs komunikacji (przekaźnik) między serwerami lokalnymi i usługą ochrony dla usługi Azure Information Protection.

Ta procedura obejmuje instalowanie i konfigurowanie łącznika, wyłączenie funkcji IRM dla programu Exchange i programu SharePoint oraz konfigurowanie tych serwerów do korzystania z łącznika. Na koniec — jeśli do usługi Azure Information Protection zaimportowano pliki danych konfiguracji usługi AD RMS (XML) użyte do ochrony wiadomości e-mail — należy ręcznie zmodyfikować rejestr na komputerach z programem Exchange Server, aby przekierować wszystkie adresy URL zaufanych domen publikacji do łącznika usługi RMS.

> [!NOTE]
> Przed rozpoczęciem sprawdź wersje serwerów lokalnych obsługujących usługę Azure Rights Management zgodnie z opisem w sekcji [Serwery lokalne, które obsługują usługę Azure RMS](../get-started/requirements-servers.md).

### <a name="install-and-configure-the-rms-connector"></a>Instalowanie i konfigurowanie łącznika usługi RMS

Postępuj zgodnie z instrukcjami w artykule [Wdrażanie łącznika usługi Azure Rights Management](../deploy-use/deploy-rms-connector.md) i wykonaj kroki od 1 do 4. Nie rozpoczynaj jeszcze kroku 5 z poziomu instrukcji łącznika. 

### <a name="disable-irm-on-exchange-servers-and-remove-ad-rms-configuration"></a>Wyłączanie funkcji IRM na serwerach Exchange Server i usuwanie konfiguracji usługi AD RMS

1.  Na każdym serwerze programu Exchange znajdź następujący folder i usuń z niego wszystkie wpisy: **\ProgramData\Microsoft\DRM\Server\S-1-5-18**

2. Z jednego z serwerów programu Exchange uruchom następujące polecenia programu PowerShell, aby upewnić się, że użytkownicy będą mogli czytać wiadomości e-mail chronione za pomocą usługi Azure Rights Management.

    Przed uruchomieniem tych poleceń zastąp własnym adresem URL usługi Azure Rights Management element *\<Twój adres URL dzierżawy>*.

        $irmConfig = Get-IRMConfiguration
        $list = $irmConfig.LicensingLocation 
        $list + "<Your Tenant URL>/_wmcs/licensing"
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

1. Wróć do instrukcji dotyczących wdrażania łącznika usługi RMS: [krok 5. Konfigurowanie serwerów do korzystania z łącznika usługi RMS](../deploy-use/configure-servers-rms-connector.md)

    Jeśli masz tylko serwer SharePoint Server, przejdź prosto do sekcji [Następne kroki](#next-steps), aby kontynuować migrację. 

2. Na każdym serwerze Exchange Server ręcznie dodaj klucze rejestru w następnej sekcji dla każdego zaimportowanego pliku danych konfiguracji (XML) w celu przekierowania adresów URL zaufanych domen publikacji do łącznika usługi RMS. Te wpisy rejestru są specyficzne dla migracji i nie są dodawane przez narzędzie do konfiguracji serwera dla łącznika usługi Microsoft RMS.

    Podczas wprowadzania tych zmian rejestru postępuj zgodnie z następującymi instrukcjami:

    -   Zastąp wartość *nazwa FQDN łącznika* nazwą łącznika zdefiniowaną w systemie DNS. Na przykład **rmsconnector.contoso.com**.

    -   W adresie URL łącznika użyj prefiksu protokołu HTTP lub HTTPS w zależności od protokołu, który ma być używany zgodnie z konfiguracją łącznika podczas komunikacji na serwerach lokalnych.

#### <a name="registry-edits-for-exchange"></a>Zmiany w rejestrze w przypadku programu Exchange

Dla wszystkich serwerów programu Exchange usuń wartości rejestru, które dodano dla wpisu LicenseServerRedirection w fazie przygotowania. Te wartości zostały dodane do następujących ścieżek:

HKLM\SOFTWARE\Microsoft\ExchangeServer\v15\IRM\LicenseServerRedirection

HKLM\SOFTWARE\Microsoft\ExchangeServer\v14\IRM\LicenseServerRedirection


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

W przypadku programu Exchange 2013 — edycja rejestru 2:

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

[!INCLUDE[Commenting house rules](../includes/houserules.md)]