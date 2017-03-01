---
title: "Ustawienia rejestru dla łącznika usługi Rights Management — AIP"
description: "Informacje dotyczące ustawień rejestru na serwerach używających łącznika usług RMS. Zalecana metoda konfiguracji tych ustawień polega na użyciu narzędzia do konfiguracji serwera dla łącznika usług Microsoft RMS."
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 02/23/2017
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: ed3e9a3d-0f7c-4abc-9d0b-aa3b18403d39
ms.reviewer: esaggese
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 2131f40b51f34de7637c242909f10952b1fa7d9f
ms.openlocfilehash: b894be1ef3d41a9faf6c3fd3b3fd8c5b94a62517
ms.lasthandoff: 02/24/2017


---


# <a name="registry-setting-for-the-rights-management-connector"></a>Ustawienia rejestru dla łącznika usługi Rights Management

>*Dotyczy: Azure Information Protection, Office 365*


Tabele zawarte w poniższych sekcjach umożliwiają ręczne dodanie lub sprawdzenie ustawień rejestru na serwerach z uruchomionym programem Exchange lub SharePoint albo systemem Windows Server, co pozwala skonfigurować używanie [łącznika usługi RMS](deploy-rms-connector.md) na tych serwerach. Zalecana metoda konfiguracji serwerów polega na użyciu narzędzia do konfiguracji serwera dla łącznika usługi Microsoft RMS.

Oto instrukcje dotyczące użycia tych ustawień:

-   *MicrosoftRMSURL* jest adresem URL usługi Microsoft RMS, używanym w organizacji. Aby znaleźć tę wartość:

    1.  Uruchom polecenie cmdlet [Get-AadrmConfiguration](http://msdn.microsoft.com/library/windowsazure/dn629410.aspx) dla usługi Azure RMS. Jeśli jeszcze nie zainstalowano modułu Windows PowerShell dla usługi Azure RMS, zobacz temat [Instalowanie programu Windows PowerShell dla usługi Azure Rights Management](install-powershell.md).

    2.  Opierając się na danych wyjściowych, zidentyfikuj wartość **LicensingIntranetDistributionPointUrl**.

        Na przykład: **LicensingIntranetDistributionPointUrl: https://5c6bb73b-1038-4eec-863d-49bded473437.rms.na.aadrm.com/_wmcs/licensing**

    3.  Usuń element **/_wmcs/licensing** z tego ciągu. Wynikowy ciąg jest adresem URL usługi Microsoft RMS. W naszym przykładzie adres URL usługi Microsoft RMS ma następującą wartość:

        **https://5c6bb73b-1038-4eec-863d-49bded473437.rms.na.aadrm.com**

-   *ConnectorFQDN* jest nazwą elementu do równoważenia obciążenia zdefiniowaną dla łącznika w systemie DNS. Na przykład **rmsconnector.contoso.com**.

-   Jeśli na potrzeby komunikacji między łącznikiem a serwerami lokalnymi skonfigurowano używanie protokołu HTTPS, w adresie URL łącznika użyj prefiksu protokołu HTTPS. Więcej informacji zawiera sekcja [Konfigurowanie łącznika usługi RMS do używania protokołu HTTPS](install-configure-rms-connector.md#configuring-the-rms-connector-to-use-https) w głównej instrukcji. W przypadku adresów URL usługi Microsoft RMS zawsze jest używany protokół HTTPS.


## <a name="exchange-2016-or-exchange-2013-registry-settings"></a>Ustawienia rejestru dla programu Exchange 2016 lub Exchange 2013

**Ścieżka rejestru:** HKEY_LOCAL_MACHINE\Software\Microsoft\MSDRM\ServiceLocation\Activation

**Typ:** Reg_SZ

**Wartość:** domyślna

**Dane:** https://*MicrosoftRMSURL*/_wmcs/certification

---

**Ścieżka rejestru:** HKEY_LOCAL_MACHINE\Software\Microsoft\MSDRM\ServiceLocation\EnterprisePublishing

**Typ:** Reg_SZ

**Wartość:** domyślna

**Dane:** https://*MicrosoftRMSURL*/_wmcs/Licensing

---

**Ścieżka rejestru:** HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\ExchangeServer\v15\IRM\CertificationServerRedirection

**Typ:** Reg_SZ

**Wartość:** https://*MicrosoftRMSURL*


**Dane:** jedna z poniższych pozycji w zależności od tego, czy do komunikacji między serwerem programu Exchange a łącznikiem usługi RMS jest używany protokół HTTP czy HTTPS:

- http://*ConnectorFQDN*

- https://*ConnectorFQDN*

---

**Ścieżka rejestru:** HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\ExchangeServer\v15\IRM\LicenseServerRedirection

**Typ:** Reg_SZ

**Wartość:** https://*MicrosoftRMSURL*


**Dane:** jedna z poniższych pozycji w zależności od tego, czy do komunikacji między serwerem programu Exchange a łącznikiem usługi RMS jest używany protokół HTTP czy HTTPS:

- http://*ConnectorFQDN*

- https://*ConnectorFQDN*


## <a name="exchange-2010-registry-settings"></a>Ustawienia rejestru dla programu Exchange 2010

**Ścieżka rejestru:** HKEY_LOCAL_MACHINE\Software\Microsoft\MSDRM\ServiceLocation\Activation

**Typ:** Reg_SZ

**Wartość:** domyślna

**Dane:** https://*MicrosoftRMSURL*/_wmcs/certification

---

**Ścieżka rejestru:** HKEY_LOCAL_MACHINE\Software\Microsoft\MSDRM\ServiceLocation\EnterprisePublishing

**Typ:** Reg_SZ

**Wartość:** domyślna

**Dane:** https://*MicrosoftRMSURL*/_wmcs/Licensing

---

**Ścieżka rejestru:** HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\ExchangeServer\v14\IRM\CertificationServerRedirection

**Typ:** Reg_SZ

**Wartość:** https://*MicrosoftRMSURL*

**Dane:** jedna z poniższych pozycji w zależności od tego, czy do komunikacji między serwerem programu Exchange a łącznikiem usługi RMS jest używany protokół HTTP czy HTTPS:

- http://*ConnectorFQDN*

- https://*ConnectorFQDN*

---

**Ścieżka rejestru:** HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\ExchangeServer\v14\IRM\LicenseServerRedirection

**Typ:** Reg_SZ

**Wartość:** https://*MicrosoftRMSURL*

**Dane:** jedna z poniższych pozycji w zależności od tego, czy do komunikacji między serwerem programu Exchange a łącznikiem usługi RMS jest używany protokół HTTP czy HTTPS:

- http://*ConnectorFQDN*

- https://*ConnectorFQDN*


## <a name="sharepoint-2016-or-sharepoint-2013-registry-settings"></a>Ustawienia rejestru dla programu SharePoint 2016 lub SharePoint 2013

**Ścieżka rejestru:** HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\MSIPC\ServiceLocation\LicensingRedirection

**Typ:** Reg_SZ

**Wartość:** https://*MicrosoftRMSURL*/_wmcs/licensing


**Dane:** jedna z poniższych pozycji w zależności od tego, czy do komunikacji między serwerem programu SharePoint a łącznikiem usługi RMS jest używany protokół HTTP czy HTTPS:

- http://*ConnectorFQDN*/_wmcs/licensing

- https://*ConnectorFQDN*/_wmcs/licensing

---

**Ścieżka rejestru:** HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\MSIPC\ServiceLocation\EnterpriseCertification

**Typ:** Reg_SZ

**Wartość:** domyślna

**Dane:** jedna z poniższych pozycji w zależności od tego, czy do komunikacji między serwerem programu SharePoint a łącznikiem usługi RMS jest używany protokół HTTP czy HTTPS:

- http://*ConnectorFQDN*/_wmcs/certification

- https://*ConnectorFQDN*/_wmcs/certification

---

**Ścieżka rejestru:** HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\MSIPC\ServiceLocation\EnterprisePublishing

**Typ:** Reg_SZ

**Wartość:** domyślna


**Dane:** jedna z poniższych pozycji w zależności od tego, czy do komunikacji między serwerem programu SharePoint a łącznikiem usługi RMS jest używany protokół HTTP czy HTTPS:

- http://*ConnectorFQDN*/_wmcs/licensing

- https://*ConnectorFQDN*/_wmcs/licensing




## <a name="file-server-and-file-classification-infrastructure-registry-settings"></a>Ustawienia rejestru dla serwera plików i infrastruktury klasyfikacji plików

**Ścieżka rejestru:** HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\MSDRM\ServiceLocation\EnterprisePublishing

**Typ:** Reg_SZ

**Wartość:** domyślna

**Dane:** http://*ConnectorFQDN*/_wmcs/licensing

---

**Ścieżka rejestru:** HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\MSDRM\ServiceLocation\Activation

**Typ:** Reg_SZ

**Wartość:** domyślna

**Dane:** http://*ConnectorFQDN*/_wmcs/certification


Powrót do tematu [Wdrażanie łącznika usługi Azure Rights Management](deploy-rms-connector.md)

[!INCLUDE[Commenting house rules](../includes/houserules.md)]
