---
title: "Wprowadzenie — aplikacja AIP dla systemów iOS i Android"
description: 
keywords: "Informacje na temat sposobu wyświetlania wiadomości e-mail lub plików w aplikacji Azure Information Protection dla systemów iOS i Android"
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 10/16/2017
ms.topic: article
ms.prod: azure
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: 3d5d18d8-7b2e-456c-bb45-48da4eb55544
ms.reviewer: esaggese
ms.suite: ems
ms.openlocfilehash: db44f73c20d7440d403b1d3a7a7ea0201f8a7abb
ms.sourcegitcommit: 965108d50739148864b2ae7dcc661ae65f1b154c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/17/2017
---
# <a name="get-started-with-the-microsoft-azure-information-protection-app-for-ios-and-android"></a>Wprowadzenie do aplikacji Microsoft Azure Information Protection dla systemów iOS i Android

*Dotyczy: Active Directory Rights Management Services, Azure Information Protection*

Przed użyciem instrukcji na tej stronie, upewnij się, że zostały przeczytane [często zadawane pytania dotyczące aplikacji usługi Azure Information Protection dla systemu iOS i Android](mobile-app-faq.md). Ta strona wyjaśniono aplikacja jest dla, urządzeń, które są obsługiwane i podstawowe informacje o sposobie korzystania z aplikacji.

Większość użytkowników zwykle użyje aplikacji usługi Azure Information Protection, podczas muszą otworzyć chronioną wiadomość e-mail lub pliku. Ale jeśli jesteś administratorem, który chce przetestować aplikację dla użytkowników, lub po prostu chcesz wypróbować aplikację, zanim zajdzie potrzeba jej użycia, możesz skorzystać z poniższych instrukcji.

> [!NOTE]
> Nie najpierw otwórz aplikację, a następnie wybierz dokumenty i wiadomości e-mail, aby wyświetlić. Zamiast tego otworzyć dokument lub wiadomość e-mail, a następnie wybierz tę aplikację, aby wyświetlić dokument lub wiadomość e-mail.
>
> Podobnie nie należy próbować zalogować się do aplikacji, aż zostanie wyświetlony monit.

Aby korzystać z poniższych instrukcji, należy dostępu z urządzenia przenośnego do jednego z plików, które obsługuje aplikację. Na przykład:

- **Plik .rpmsg**: to jest chroniona prawami wiadomość e-mail wyświetlana jako załącznik w wiadomości e-mail, gdy aplikacja poczty e-mail na urządzeniu przenośnym nie obsługuje natywnie ochrony danych za pomocą usługi Rights Management. 
    
    Użyj innego urządzenia, aby wysłać do siebie wiadomość e-mail chronioną prawami, do której można uzyskać dostęp z urządzenia przenośnego. Na przykład użyj programu Outlook na komputerze z systemem Windows. Listę klientów poczty e-mail, które natywnie obsługują usługę Rights Management, można znaleźć w kolumnie POCZTA E-MAIL na stronie [Aplikacje obsługujące ochronę danych usługi Azure Rights Management](../get-started/requirements-applications.md).

- **Plik PDF chroniony prawami**: na komputerze z systemem Windows możesz użyć klienta usługi Azure Information Protection w celu zapewnienia [ochrony dla pliku PDF](client-classify-protect.md). Następnie możesz wysłać do siebie plik PDF chroniony prawami jako załącznik wiadomości e-mail. Możesz także przekazać plik PDF do chronionej biblioteki programu SharePoint, a następnie udostępnić go przy użyciu swojego adresu e-mail.

- **Plik .ptxt, .pjpg lub .ppng**: na komputerze z systemem Windows możesz użyć klienta usługi Azure Information Protection, aby objąć ochroną plik tekstowy lub obraz, a następnie wysłać sobie zawartość w postaci pliku chronionego w załączniku wiadomości e-mail. Pełna lista typów plików, których można używać do testowania, znajduje się w pierwszej tabeli sekcji [Typy plików, dla których jest obsługiwana klasyfikacja i ochrona](client-admin-guide-file-types.md#supported-file-types-for-classification-and-protection) przewodnika administratora klienta usługi Azure Information Protection. 

Aby wyświetlić te pliki w przeglądarce usługi Azure Information Protection, naciśnij załącznik lub link wiadomości e-mail. Po wyświetleniu monitu o wybranie aplikacji do ich otwarcia wybierz aplikację **AIP Viewer**. Zostanie wyświetlona prośba o zalogowanie do konta służbowego lub o wybranie certyfikatu. Po uwierzytelnieniu poświadczeń aplikacja usługi Azure Information Protection wyświetli wiadomość e-mail lub plik do odczytu.

## <a name="next-steps"></a>Następne kroki

Aby przekazać pytania lub opinie na temat tej aplikacji, które nie zostały opisane w [— często zadawane pytania](mobile-app-faq.md), można znaleźć w naszych [witryny usługi Yammer](https://www.yammer.com/AskIPTeam).

Jeśli aplikacja nie pracuje zgodnie z opisem, zobacz zasoby wymienione w naszym [House reguły](../house-rules.md) strony.

[!INCLUDE[Commenting house rules](../includes/houserules.md)]