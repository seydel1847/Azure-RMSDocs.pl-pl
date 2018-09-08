---
title: Serwer usług AD RMS | Azure RMS
description: Składnik serwera usług Rights Management Services (RMS) jest implementowany przez zestaw usług sieci Web, które działają na bazie usługi Microsoft Internet Information Services.
keywords: ''
author: lleonard-msft
ms.author: alleonar
manager: mbaldwin
ms.date: 02/23/2017
ms.topic: conceptual
ms.service: information-protection
ms.assetid: 17B05780-B0EF-4805-8304-52DCDEB3AADB
audience: developer
ms.reviewer: shubhamp
ms.suite: ems
ms.openlocfilehash: d190dd1559378473e52c2c741fcf4693f9e43a59
ms.sourcegitcommit: 26a2c1becdf3e3145dc1168f5ea8492f2e1ff2f3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2018
ms.locfileid: "44151338"
---
# <a name="server"></a>Serwer

W tym temacie opisano przeznaczenie i funkcje serwera usług RMS na potrzeby platformy Azure i systemu Windows Server.

**Usługi Azure RMS** — aby uzyskać więcej informacji na temat korzystania z usługi Azure Rights Management, zobacz [Umożliwianie współpracy aplikacji usługi z usługą RMS opartą na chmurze](how-to-use-file-api-with-aadrm-cloud.md).

> [!IMPORTANT] 
> Zalecamy tworzenie i testowanie aplikacji za pomocą usług Azure RMS.

**System Windows Server** — w przypadku usługi RMS znajdującej się na serwerach lokalnych, począwszy od systemu Windows Server 2008, można zainstalować i skonfigurować usługi RMS, dodając je jako rolę. Aby zainstalować usługę w starszych systemach operacyjnych, pobierz ją ze strony [Zarządzanie prawami dostępu w systemie Windows z dodatkiem Service Pack 2](http://www.microsoft.com/download/en/details.aspx?id=4909) w Centrum pobierania Microsoft.

Wśród wielu zainstalowanych usług sieci Web następujące usługi są ważne na potrzeby opracowywania aplikacji dla serwera usług RMS uruchomionego w systemie Windows Server.

| Usługa | Opis |
|---------|-------------|
| Administration | Obsługuje administracyjną witrynę sieci Web umożliwiającą zarządzanie usługami RMS. Usługa działa na głównych serwerach certyfikacji i serwerach licencjonowania. Korzystając ze strony Interfejs API obsługi skryptów usług Active Directory Rights Management Services, można tworzyć skrypty administracyjne.|
| Certyfikacja kont |Tworzy certyfikaty urządzeń, które identyfikują komputery w hierarchii certyfikatów usług RMS, i certyfikaty kont praw dostępu kojarzące użytkowników z określonymi komputerami. Aby uzyskać więcej informacji, zobacz Aktywowanie komputera i aktywowanie użytkownika.<p><p>Ta usługa działa na głównym serwerze certyfikacji. |
|Licencjonowanie | Wydaje *licencję użytkowania*. Usługa działa na głównych serwerach certyfikacji i serwerach licencjonowania.|
|Publikowanie | Tworzy *licencję publikowania* definiującą zasady, które mogą być wyliczane w licencji użytkowania. Aby uzyskać więcej informacji, zobacz [Tworzenie licencji publikowania](https://msdn.microsoft.com/library/Aa362355).<p><p>Usługa działa na głównych serwerach certyfikacji i serwerach licencjonowania.|
|Certyfikacja wstępna | Umożliwia serwerowi żądanie *certyfikatu konta praw* w imieniu użytkownika. Usługa działa na głównych serwerach certyfikacji i serwerach licencjonowania.|
|Lokalizator usług | Określa adres URL usług certyfikacji kont, licencjonowania i publikowania dla usługi Active Directory, aby te usługi mogły być odnajdowane przez klientów usług RMS. Usługa działa na głównych serwerach certyfikacji i serwerach licencjonowania.|

## <a name="related-topics"></a>Tematy pokrewne ##
* [Przegląd](ad-rms-overview.md)
* [Usługi Microsoft Internet Information Services](http://www.iis.net/overview)
* [Umożliwianie współpracy aplikacji usługi z usługą RMS opartą na chmurze](how-to-use-file-api-with-aadrm-cloud.md)
* [Zarządzanie prawami dostępu w systemie Windows z dodatkiem Service Pack 2](http://www.microsoft.com/download/en/details.aspx?id=4909)
* [Interfejs API obsługi skryptów usług Active Directory Rights Management Services](https://msdn.microsoft.com/library/Bb968797)
* [Aktywacja komputera](https://msdn.microsoft.com/library/Cc530377)
* [Aktywacja użytkownika](https://msdn.microsoft.com/library/Cc530378)
* [Tworzenie licencji publikowania](https://msdn.microsoft.com/library/Aa362355)
