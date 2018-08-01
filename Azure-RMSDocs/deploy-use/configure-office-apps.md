---
title: Konfiguracja dla klientów do korzystania z aplikacji pakietu Office z usługą Azure RMS z usługi AIP
description: Informacje i instrukcje dla administratorów dotyczące konfigurowania aplikacji pakietu Office do pracy z usługą Azure Rights Management w ramach usługi Azure Information Protection.
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 02/08/2017
ms.topic: article
ms.prod: ''
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: ec269afe-4e87-4cc1-9144-5fbb594b412e
ms.reviewer: esaggese
ms.suite: ems
ms.openlocfilehash: f9cbb099770724ed5329e491fcbd4499abd9fdb8
ms.sourcegitcommit: 44ff610dec678604c449d42cc0b0863ca8224009
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/31/2018
ms.locfileid: "39372380"
---
# <a name="office-apps-configuration-for-clients-to-use-the-azure-rights-management-service"></a>Aplikacje pakietu Office: Konfiguracja dla klientów do korzystania z usługi Azure Rights Management

>*Dotyczy: [usługi Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection), [usługi Office 365](http://download.microsoft.com/download/E/C/F/ECF42E71-4EC0-48FF-AA00-577AC14D5B5C/Azure_Information_Protection_licensing_datasheet_EN-US.pdf)*


Dzięki tym informacjom można ustalić, co należy zrobić, aby aplikacje pakietu Office pracy z usługą Azure Rights Management z usługi Azure Information Protection.

## <a name="office-2016-and-office-2013"></a>Pakiety Office 2016 i Office 2013
Że te nowsze wersje pakietu Office natywnie obsługują usługę Azure Rights Management, żadna konfiguracja komputera klienckiego jest wymagany do obsługi funkcji information rights management (IRM) dla aplikacji, takich jak Word, Excel, PowerPoint, Outlook, oraz W programie Outlook w sieci web. Wszyscy użytkownicy wystarczy się zalogować się do aplikacji pakietu Office przy użyciu ich [!INCLUDE[o365_1](../includes/o365_1.md)] poświadczeń. Można następnie mogą chronić pliki i wiadomości e-mail i używać plików i wiadomości e-mail, które są chronione przez innych użytkowników.

Zalecamy jednak uzupełnienie tych aplikacji o klienta usługi Azure Information Protection, dzięki czemu użytkownicy będą mogli skorzystać z zalet dodatku pakietu Office i możliwości obsługi dodatkowych typów plików. Aby uzyskać więcej informacji, zobacz temat [Klient usługi Azure Information Protection: instalacja i konfiguracja klienta](configure-client.md).

## <a name="office-2010"></a>Pakiet Office 2010
Aby komputery klienckie mogły używać usługi Azure Rights Management z pakietem Office 2010 muszą mieć klienta usługi Azure Information Protection lub aplikacji do udostępniania usługi Rights Management dla Windows. Nie jest wymagana żadna dalsza konfiguracja, a użytkownicy muszą tylko zalogować się przy użyciu poświadczeń usługi [!INCLUDE[o365_1](../includes/o365_1.md)], aby chronić pliki i używać plików chronionych przez inne osoby.

Aby uzyskać więcej informacji na temat klienta usługi Azure Information Protection, zobacz artykuł [Klient usługi Azure Information Protection: instalacja i konfiguracja klienta](configure-client.md).

