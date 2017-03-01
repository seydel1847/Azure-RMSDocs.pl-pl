---
title: "Migracja z usługi AD RMS do usługi Azure Information Protection — faza 3"
description: "Faza 3 migracji z usługi AD RMS do usługi Azure Information Protection obejmująca kroki 6 i 7 z sekcji Migrowanie z usługi AD RMS do usługi Azure Information Protection"
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 02/14/2017
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: 8b039ad5-95a6-4c73-9c22-78c7b0e12cb7
ms.reviewer: esaggese
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 2131f40b51f34de7637c242909f10952b1fa7d9f
ms.openlocfilehash: d5de26f757803f5c354814b9cbcc965de382192c
ms.lasthandoff: 02/24/2017


---

# <a name="migration-phase-3---supporting-services-configuration"></a>Faza 3 migracji — konfiguracja usług pomocniczych

>*Dotyczy: Active Directory Rights Management Services, Azure Information Protection, Office 365*


Skorzystaj z poniższych informacji dotyczących fazy 3 migrowania z usługi AD RMS do usługi Azure Information Protection. Te procedury obejmują kroki 6 i 7 z sekcji [Migrowanie z usługi AD RMS do usługi Azure Information Protection](migrate-from-ad-rms-to-azure-rms.md).


## <a name="step-6-configure-irm-integration-for-exchange-online"></a>Krok 6. Konfigurowanie integracji funkcji IRM na potrzeby usługi Exchange Online

Jeśli wcześniej zaimportowano zaufaną domenę publikacji z usługi AD RMS do usługi Exchange Online, należy usunąć tę domenę, aby uniknąć konfliktu szablonów i zasad po przeprowadzeniu migracji do usługi Azure Information Protection. W tym celu użyj polecenia cmdlet [Remove-RMSTrustedPublishingDomain](https://technet.microsoft.com/library/jj200720%28v=exchg.150%29.aspx) w usłudze Exchange Online.

W przypadku wybrania topologii klucza dzierżawy usługi Azure Information Protection **Zarządzany przez firmę Microsoft**:

-   Zobacz sekcję [Exchange Online: IRM configuration](../deploy-use/configure-office365.md#exchange-online-irm-configuration) (Usługa Exchange Online: konfiguracja funkcji IRM) artykułu [Office 365: Configuration for clients and online services](../deploy-use/configure-office365.md) (Usługa Office 365: konfiguracja dla klientów i usług online). Ta sekcja zawiera typowe polecenia uruchamiane w celu nawiązania połączenia z usługą Exchange Online, importowania klucza dzierżawy z usługi Azure Information Protection oraz włączania funkcji IRM na potrzeby usługi Exchange Online. Po wykonaniu tych kroków dostępna będzie pełna funkcjonalność ochrony za pomocą usługi Azure Rights Management z usługą Exchange Online.

W przypadku wybrania topologii klucza dzierżawy usługi Azure Information Protection **Zarządzany przez klienta (BYOK)**:

-   Funkcjonalność ochrony za pomocą usług Rights Management zostanie ograniczona w programie Exchange Online zgodnie z opisem w artykule [Cennik i ograniczenia dotyczące funkcji BYOK](byok-price-restrictions.md).

## <a name="step-7-deploy-the-rms-connector"></a>Krok 7. Wdrażanie łącznika usługi RMS
W przypadku użycia funkcji Zarządzanie prawami do informacji (IRM) programu Exchange Server lub SharePoint Server z usługą AD RMS należy najpierw wyłączyć funkcję IRM na tych serwerach i usunąć konfigurację usługi AD RMS. Następnie można wdrożyć łącznik usługi Rights Management (RMS), który działa jako interfejs komunikacji (przekaźnik) między serwerami lokalnymi i usługą ochrony dla usługi Azure Information Protection.

Na zakończenie tego kroku — jeśli do usługi Azure Information Protection zaimportowano wiele plików danych konfiguracji usługi AD RMS (XML) użytych do ochrony wiadomości e-mail — należy ręcznie zmodyfikować rejestr na komputerach z programem Exchange Server, aby przekierować wszystkie adresy URL zaufanych domen publikacji do łącznika usługi RMS.

> [!NOTE]
> Przed rozpoczęciem sprawdź wersje serwerów lokalnych obsługujących usługę Azure Rights Management zgodnie z opisem w sekcji [Serwery lokalne, które obsługują usługę Azure RMS](../get-started/requirements-servers.md).

### <a name="disable-irm-on-exchange-servers-and-remove-ad-rms-configuration"></a>Wyłączanie funkcji IRM na serwerach Exchange Server i usuwanie konfiguracji usługi AD RMS

1.  Na każdym serwerze programu Exchange znajdź następujący folder i usuń z niego wszystkie wpisy: \ProgramData\Microsoft\DRM\Server\S-1-5-18

2.  Na jednym z serwerów programu Exchange użyj polecenia cmdlet [Set_IRMConfiguration](http://technet.microsoft.com/library/dd979792.aspx), aby najpierw wyłączyć funkcje IRM dla wiadomości wysyłanych do adresatów wewnętrznych:

    ```
    Set-IRMConfiguration -InternalLicensingEnabled $false
    ```

3.  Użyj tego samego polecenia cmdlet, aby wyłączyć funkcje IRM dla wiadomości wysyłanych do adresatów zewnętrznych:

    ```
    Set-IRMConfiguration -ExternalLicensingEnabled $false
    ```

4.  Następnie użyj tego samego polecenia cmdlet, aby wyłączyć funkcję IRM w aplikacji Microsoft Office Outlook Web App i programie Microsoft Exchange ActiveSync:

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

5.  Na każdym komputerze z programem SharePoint Server usuń zawartość folderu \ProgramData\Microsoft\MSIPC\Server\*&lt;Identyfikator SID konta, na którym działa program SharePoint Server&gt;*.

#### <a name="install-and-configure-the-rms-connector"></a>Instalowanie i konfigurowanie łącznika usługi RMS

-   Postępuj zgodnie z instrukcjami w artykule [Wdrażanie łącznika usługi Azure Rights Management](../deploy-use/deploy-rms-connector.md).

#### <a name="for-exchange-only-and-multiple-tpds-edit-the-registry"></a>Tylko program Exchange i wiele zaufanych domen publikacji: edycja rejestru

-   Na każdym serwerze Exchange Server ręcznie dodaj następujące klucze rejestru dla każdego dodatkowego zaimportowanego pliku danych konfiguracji (XML) w celu przekierowania adresów URL zaufanych domen publikacji do łącznika usługi RMS. Te wpisy rejestru są specyficzne dla migracji i nie są dodawane przez narzędzie do konfiguracji serwera dla łącznika usługi Microsoft RMS.

    Podczas wprowadzania tych zmian rejestru postępuj zgodnie z następującymi instrukcjami:

    -   Zastąp wartość *ConnectorFQDN* nazwą łącznika zdefiniowaną w systemie DNS. Na przykład **rmsconnector.contoso.com**.

    -   W adresie URL łącznika użyj prefiksu protokołu HTTP lub HTTPS w zależności od protokołu, który ma być używany zgodnie z konfiguracją łącznika podczas komunikacji na serwerach lokalnych.

W przypadku programu Exchange 2013 — edycja rejestru 1:


**Ścieżka rejestru:**

HKLM\SOFTWARE\Microsoft\ExchangeServer\v15\IRM\LicenseServerRedirection

**Typ:**

Reg_SZ

**Wartość:**

https://\<Adres URL licencjonowania usług AD RMS w sieci intranet\>/_wmcs/licensing

**Dane:**

Jeden z następujących elementów w zależności od tego, czy podczas komunikacji serwera Exchange z łącznikiem usługi RMS jest używany protokół HTTP, czy HTTPS:

- http://\<nazwaFQDNłącznika\>/_wmcs/licensing

- https://\<nazwaŁącznika\>/_wmcs/licensing


---

W przypadku programu Exchange 2013 — edycja rejestru 2:

**Ścieżka rejestru:**

HKLM\SOFTWARE\Microsoft\ExchangeServer\v15\IRM\LicenseServerRedirection 


**Typ:**

Reg_SZ

**Wartość:**

https://\<Adres URL licencjonowania usług AD RMS w sieci ekstranet\>/_wmcs/licensing


**Dane:**

Jeden z następujących elementów w zależności od tego, czy podczas komunikacji serwera Exchange z łącznikiem usługi RMS jest używany protokół HTTP, czy HTTPS:

- http://\<nazwaFQDNłącznika\>/_wmcs/licensing

- https://\<nazwaFQDNłącznika\>/_wmcs/licensing

---

W przypadku programu Exchange 2010 — edycja rejestru 1:



**Ścieżka rejestru:**

HKLM\SOFTWARE\Microsoft\ExchangeServer\v14\IRM\LicenseServerRedirection

**Typ:**

Reg_SZ

**Wartość:**

https://\<Adres URL licencjonowania usług AD RMS w sieci intranet\>/_wmcs/licensing

**Dane:**

Jeden z następujących elementów w zależności od tego, czy podczas komunikacji serwera Exchange z łącznikiem usługi RMS jest używany protokół HTTP, czy HTTPS:

- http://\<nazwaFQDNłącznika\>/_wmcs/licensing

- https://\<nazwaŁącznika\>/_wmcs/licensing


---

W przypadku programu Exchange 2010 — edycja rejestru 2:


**Ścieżka rejestru:**

HKLM\SOFTWARE\Microsoft\ExchangeServer\v14\IRM\LicenseServerRedirection
 

**Typ:**

Reg_SZ

**Wartość:**

https://\<Adres URL licencjonowania usług AD RMS w sieci ekstranet\>/_wmcs/licensing


**Dane:**

Jeden z następujących elementów w zależności od tego, czy podczas komunikacji serwera Exchange z łącznikiem usługi RMS jest używany protokół HTTP, czy HTTPS:

- http://\<nazwaFQDNłącznika\>/_wmcs/licensing

- https://\<nazwaFQDNłącznika\>/_wmcs/licensing

---

Po wykonaniu tych procedur zapoznaj się z sekcją **Następne kroki** w artykule [Wdrażanie łącznika usług Azure Rights Management](../deploy-use/deploy-rms-connector.md).

## <a name="next-steps"></a>Następne kroki
Aby kontynuować migrację, przejdź do [fazy 4 — zadań po migracji](migrate-from-ad-rms-phase4.md).

[!INCLUDE[Commenting house rules](../includes/houserules.md)]
