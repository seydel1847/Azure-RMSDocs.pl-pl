---
# required metadata

title: Serwer usług AD RMS | Azure RMS
description: Składnik serwera usług Rights Management Services (RMS) jest implementowany przez zestaw usług sieci Web, które działają na bazie usług Microsoft Internet Information Services.
keywords:
author: bruceperlerms
manager: mbaldwin
ms.date: 04/28/2016
ms.topic: article
ms.prod: azure
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: 17B05780-B0EF-4805-8304-52DCDEB3AADB
# optional metadata

#ROBOTS:
audience: developer
#ms.devlang:
ms.reviewer: shubhamp
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# Serwer usług AD RMS

W tym temacie opisano przeznaczenie i funkcje serwera usług RMS.

Składnik serwera usług Rights Management Services (RMS) jest implementowany przez zestaw usług sieci Web, które działają na bazie usług [Microsoft Internet Information Services](http://www.iis.net/overview) (IIS). Możesz także użyć implementacji opartej na chmurze za pośrednictwem usług RMS na platformie Azure. Aby uzyskać więcej informacji na temat korzystania z usługi Azure Rights Management, zobacz [Umożliwianie współpracy aplikacji usługi z usługą RMS opartą na chmurze](how-to-use-file-api-with-aadrm-cloud.md).

W przypadku serwerów lokalnych, począwszy od systemu Windows Server 2008, można zainstalować i skonfigurować usługę RMS, dodając ją jako rolę. Aby zainstalować usługę w starszych systemach operacyjnych, pobierz ją ze strony [Zarządzanie prawami dostępu w systemie Windows z dodatkiem Service Pack 2](http://www.microsoft.com/download/en/details.aspx?id=4909) w Centrum pobierania Microsoft.

Wśród wielu zainstalowanych usług sieci Web następujące usługi są ważne na potrzeby opracowywania aplikacji.

**Administracja** — Obsługuje administracyjną witrynę sieci Web umożliwiającą zarządzanie usługami RMS. Usługa działa na głównych serwerach certyfikacji i serwerach licencjonowania. Korzystając ze strony [Interfejs API obsługi skryptów usług Active Directory Rights Management Services](https://msdn.microsoft.com/library/Bb968797), można tworzyć skrypty administracyjne.

**Certyfikacja kont** — Tworzy certyfikaty urządzeń, które identyfikują komputery w hierarchii certyfikatów usług RMS, i certyfikaty kont praw dostępu kojarzące użytkowników z określonymi komputerami. Aby uzyskać więcej informacji, zobacz temat [Aktywacja użytkownika](https://msdn.microsoft.com/library/Cc530378).

Ta usługa działa na głównym serwerze certyfikacji.

**Licencjonowanie** — Wystawia licencję użytkownika końcowego, która umożliwia użytkownikowi końcowemu korzystanie z chronionej zawartości. Usługa działa na głównych serwerach certyfikacji i serwerach licencjonowania.

**Publikowanie** — Tworzy [licencję publikowania](https://msdn.microsoft.com/library/Aa362355). Usługa działa na głównych serwerach certyfikacji i serwerach licencjonowania.

**Certyfikacja wstępna** — Umożliwia serwerowi żądanie certyfikatu konta praw (RAC) w imieniu użytkownika. Certyfikat RAC wykorzystuje certyfikat komputera z aktywacji usług RMS do powiązania kont użytkowników z określonymi komputerami lub grupami komputerów i pozwala korzystać użytkownikom z zawartości chronionej. Usługa działa na głównych serwerach certyfikacji i serwerach licencjonowania.

**Lokalizator usług** — Określa adres URL usług certyfikacji kont, licencjonowania i publikowania dla usługi Active Directory, aby te usługi mogły być odnajdowane przez klientów usług RMS. Usługa działa na głównych serwerach certyfikacji i serwerach licencjonowania.

 

## Tematy pokrewne ##
* [Przegląd](ad-rms-overview.md)
* [Usługi Microsoft Internet Information Services](http://www.iis.net/overview)
* [Umożliwianie współpracy aplikacji usługi z usługą RMS opartą na chmurze](how-to-use-file-api-with-aadrm-cloud.md)
* [Zarządzanie prawami dostępu w systemie Windows z dodatkiem Service Pack 2](http://www.microsoft.com/download/en/details.aspx?id=4909)
* [Interfejs API obsługi skryptów usług Active Directory Rights Management Services](https://msdn.microsoft.com/library/Bb968797)
* [Aktywacja komputera](https://msdn.microsoft.com/library/Cc530377)
* [Aktywacja użytkownika](https://msdn.microsoft.com/library/Cc530378)
* [Tworzenie licencji publikowania](https://msdn.microsoft.com/library/Aa362355)

 

 


<!--HONumber=Apr16_HO4-->


