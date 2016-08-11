---
title: "Samouczek Szybki start dla usługi Azure Information Protection | Azure Rights Management"
description: "Samouczek wprowadzający, dzięki któremu możesz szybko wypróbować usługę Microsoft Azure Information Protection dla swojej organizacji. Wystarczą 4 proste kroki, które powinny zająć mniej niż 15 minut."
author: cabailey
manager: mbaldwin
ms.date: 07/29/2016
ms.topic: article
ms.prod: azure
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: 1260b9e5-dba1-41de-84fd-609076587842
translationtype: Human Translation
ms.sourcegitcommit: 93444affe94b280db2c9e4e2960c6902e491dec6
ms.openlocfilehash: 17670eadc7cbf6111ab7fd0a9322e51d401b86e1


---

# Samouczek Szybki start dla usługi Azure Information Protection 

>*Dotyczy: Azure Information Protection (wersja zapoznawcza)*

**[Niniejsze informacje mają charakter wstępny i mogą ulec zmianom. ]**

Samouczek wprowadzający, dzięki któremu możesz szybko wypróbować usługę Microsoft Azure Information Protection dla swojej organizacji. Wystarczą 4 proste kroki, które powinny zająć mniej niż 15 minut. Opcjonalnie będziemy aktywować usługę Azure Rights Management, przyglądać się domyślnej zasadzie usługi Azure Information Protection i modyfikować ją, instalować klienta usługi Azure Information Protection, a następnie używać programu Word do zapoznania się z działaniem funkcjami klasyfikacji, etykietowania i ochrony.

Ten samouczek jest przeznaczony dla administratorów oraz konsultantów IT i ma na celu ułatwienie oceny usługi Azure Information Protection jako rozwiązania do ochrony informacji w organizacji. W środowisku produkcyjnym administrator wykona instrukcje włączania usługi, skonfiguruje zasady usługi Information Protection, a następnie zainstaluje klienta u użytkowników. Instrukcje etykietowania dokumentów będą wykonywane przez użytkowników końcowych. W niniejszym samouczku uwzględniono oba zestawy instrukcji w celu zaprezentowania kompletnego scenariusza klasyfikowania, etykietowania i chronienia danych organizacji. 

W przypadku wystąpienia problemów podczas wykonywania instrukcji zamieszczonych w tym samouczku lub używania wersji zapoznawczej usługi Azure Information Protection albo jeśli chcesz dowiedzieć się, co sądzą inni, odwiedź [witrynę usługi Yammer poświęconą usłudze Azure Information Protection](https://www.yammer.com/askipteam/#/threads/inGroup?type=in_group&feedId=8652489&view=all).

## Wymagania wstępne 
Do ukończenia tego samouczka będą potrzebne następujące elementy:

- Wszelkie subskrypcje obejmujące usługę Azure Rights Management dają dostęp do wersji zapoznawczej usługi Azure Information Protection. Usługa Azure Information Protection jest dostępna we wszystkich regionach, które obsługują usługę Azure Rights Management. Aby uzyskać więcej informacji o dostępnych subskrypcjach oraz linki do bezpłatnych wersji próbnych, zobacz artykuł [Wymagania dotyczące usługi Azure RMS: subskrypcje usług w chmurze, które obsługują usługę Azure RMS](../get-started/requirements-subscriptions.md).

- Subskrypcja platformy Azure, która umożliwia skonfigurowanie zasad usługi Azure Information Protection w portalu Azure. Jeśli organizacja nie ma jeszcze subskrypcji platformy Azure, możesz ją uzyskać, tworząc konto do użycia na potrzeby bezpłatnej wersji próbnej: przejdź na stronę [wprowadzenia do platformy Azure](https://account.windowsazure.com/organization) i postępuj zgodnie z instrukcjami.

  > [!TIP] 
  > Jeśli potrzebujesz jednej lub obu subskrypcji, uzyskaj je z wyprzedzeniem, ponieważ czasami ukończenie tego procesu może wymagać trochę czasu.

- Konto administratora do logowania się do centrum administracyjnego usługi Office 365 lub klasycznego portalu Azure, umożliwiające aktywowanie usługi Rights Management. To konto musi mieć również adres e-mail i działającą usługę poczty e-mail (na przykład Exchange Online lub Exchange Server).

- Komputer z systemem Windows (co najmniej Windows 7 z dodatkiem SP1), na którym jest zainstalowany pakiet Office Professional Plus 2016, Office Professional Plus 2013 z dodatkiem Service Pack 1 lub Office Professional Plus 2010. 

- Jeśli w organizacji wdrożono usługę AD RMS (Active Directory Rights Management Services): komputer musi należeć do grupy roboczej, która wcześniej nie korzystała z usług AD RMS. Jest to wymagane, jeśli chcesz chronić dokumenty i zapewnić, że komputer pobiera szablony tylko z usługi Azure Rights Management. Komputer nie może łączyć się w tym samym czasie jednocześnie z usługą AD RMS i usługą Azure RMS. Aby uzyskać informacje o migracji, zobacz artykuł [Migrowanie z usług AD RMS do usługi Azure Rights Management](../plan-design/migrate-from-ad-rms-to-azure-rms.md).   

Zaczynamy!

>[!div class="step-by-step"]
[&#187; Krok 1](infoprotect-tutorial-step1.md)





<!--HONumber=Jul16_HO5-->


