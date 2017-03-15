---
title: "Klient usługi Azure Information Protection&colon; historia wersji"
description: "Poznaj nowe i zmienione funkcje w wersji klienta usługi Azure Information Protection dla systemu Windows."
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 03/06/2017
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: 6ebd0ca3-1864-4b3d-bb3e-a168eee5eb1d
ms.reviewer: esaggese
ms.suite: ems
ms.openlocfilehash: cfd5eae4191cb0b09d8d43f9f708c80ff724d136
ms.sourcegitcommit: 31e128cc1b917bf767987f0b2144b7f3b6288f2e
translationtype: HT
---
# <a name="azure-information-protection-client-version-release-history"></a>Klient usługi Azure Information Protection: historia wersji

>*Dotyczy: Azure Information Protection*

Zespół pracujący nad usługą Azure Information Protection regularnie aktualizuje klienta usługi Azure Information Protection w celu wprowadzenia poprawek i dodania nowych funkcji. Klient jest uwzględniony w wykazie usługi Microsoft Update (kategoria: **Azure Information Protection**) i zawsze możesz pobrać najnowszą ogólnodostępną wersję oraz wersję kolejną (zapoznawczą) z [Centrum pobierania Microsoft](https://www.microsoft.com/en-us/download/details.aspx?id=53018).

Wersje zapoznawcze nie powinny być wdrażane dla użytkowników końcowych w sieciach produkcyjnych. Umożliwiają one natomiast zapoznanie się z nowymi funkcjami i poprawkami, które zostaną wprowadzone w kolejnej ogólnodostępnej wersji, oraz ich wypróbowanie. 

Poniższe informacje pozwalają dowiedzieć się, co wprowadzono lub zmieniono w ogólnodostępnej wersji. Najnowsza wersja jest wyświetlana na początku listy. Informacje dotyczące bieżącej wersji zapoznawczej znajdują się na stronie pobierania.

> [!NOTE]
> Niewielkie poprawki nie są wyświetlane, dlatego jeśli wystąpi problem z klientem usługi Azure Information Protection, sprawdź najpierw, czy ten problem nie dotyczy najnowszej ogólnodostępnej wersji. Jeśli tak jest, sprawdź bieżącą wersję zapoznawczą.
>  
> Jeśli problem nie ustąpi, zapoznaj się z informacjami w temacie [Opcje pomocy technicznej i zasoby społecznościowe](../get-started/information-support.md#support-options-and-community-resources). Zachęcamy także do kontaktowania się z naszym zespołem ds. usługi Azure Information Protection w [witrynie Yammer](https://www.yammer.com/askipteam/).

## <a name="version-131552"></a>Wersja 1.3.155.2

**Wydana**: 2017-08-02

**Nowe wymagania**:

Microsoft .NET Framework

- Ta wersja klienta usługi Azure Information Protection wymaga programu Microsoft .NET Framework w wersji 4.6.2 lub wyższej. W przypadku jej braku Instalator spróbuje ją pobrać i zainstalować. Po zakończeniu instalacji klienta usługi Azure Information Protection może być wymagane ponowne uruchomienie komputera.

- Jeśli przeglądarka usługi Azure Information Protection jest instalowana oddzielnie, wymagany jest program Microsoft .NET Framework w wersji 4.5.2 lub wyższej. W przypadku jego braku Instalator nie pobierze i nie zainstaluje tego programu.

**Nowe funkcje**:

- Nowy, ujednolicony klient, który łączy funkcje aplikacji RMS sharing dla systemu Windows z możliwościami klienta usługi Azure Information Protection. Obejmuje następujące funkcje:
    
    - Integracja z Eksploratorem plików systemu Windows (kliknięcie prawym przyciskiem myszy) w celu stosowania etykiet i ochrony. Obsługa dodatkowych formatów plików i możliwość wybierania wielu plików.
    - Przeglądarka chronionych dokumentów (w tym chronionych dokumentów PDF do użytku w programie SharePoint).
    - Polecenia cmdlet programu PowerShell pozwalające pobrać i ustawić etykiety dla plików przechowywanych lokalnie lub w udziałach sieciowych. Wspomniane polecenia cmdlet są instalowane z poleceniami cmdlet dostarczanymi wcześniej z narzędziem RMS Protection Tool (modułem RMSProtection).
    - Dzienniki użycia klienta zawierające informacje dotyczące np. doboru i sposobu użycia etykiet przez poszczególne osoby.

Ta wersja klienta jest [ogólnodostępną wersją](https://blogs.technet.microsoft.com/enterprisemobility/2017/02/08/azure-information-protection-december-update-moves-to-general-availability/) zapoznawczą klienta, która została zapowiedziana po raz pierwszy w grudniu 2016 roku. Aby uzyskać więcej informacji na temat tej wersji klienta, zapoznaj się z następującymi podręcznikami:

- [Podręcznik administratora klienta usługi Azure Information Protection](client-admin-guide.md)

- [Podręcznik użytkownika usługi Azure Information Protection](client-user-guide.md)


## <a name="version-1240"></a>Wersja 1.2.4.0

**Wydana**: 2016-10-27

**Poprawki**:

- Instalacja klienta zostanie ukończona po wyłączeniu usługi Windows Update.

- W pakiecie Office 2016 po zapisaniu dokumentu i skonfigurowaniu zastosowanej etykiety dla nagłówka lub stopki kursor nie jest przenoszony do nagłówka lub stopki.

- Automatyczna klasyfikacja działa w programie Word w przypadku tekstu w powiązanych polach tekstowych.

**Nowa funkcja**:

- Testy diagnostyczne i opcja resetowania, które użytkownik może uruchomić z aplikacji pakietu Office po zainstalowaniu klienta usługi Azure Information Protection: na karcie **Narzędzia główne** w grupie **Ochrona** kliknij pozycję **Chroń**, kliknij pozycję **Pomoc i opinie**, a następnie kliknij pozycję **Uruchom diagnostykę**. 

    Aby uzyskać więcej informacji na temat tej opcji, zobacz sekcję [Aby zweryfikować instalację, stan połączenia albo zgłosić problem](client-admin-guide.md#additional-checks-to-verify-installation-connection-status-or-send-feedback) w dokumentacji instalacji klienta.

## <a name="version-11230"></a>Wersja 1.1.23.0

**Wydana**: 2016-10-01

Wersja ogólnie dostępna.

## <a name="next-steps"></a>Następne kroki

Aby uzyskać więcej informacji na temat instalacji klienta:

- Użytkownicy: [pobieranie i instalowanie klienta](install-client-app.md)

- Administratorzy: [Podręcznik administratora klienta usługi Azure Information Protection](client-admin-guide.md)


[!INCLUDE[Commenting house rules](../includes/houserules.md)]