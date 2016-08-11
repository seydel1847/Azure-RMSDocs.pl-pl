---
title: "Konfigurowanie etykiety w celu zastosowania ochrony usługi Rights Management | Azure Rights Management"
description: 
author: cabailey
manager: mbaldwin
ms.date: 07/29/2016
ms.topic: article
ms.prod: azure
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: df26430b-315a-4012-93b5-8f5f42e049cc
translationtype: Human Translation
ms.sourcegitcommit: 00b4cd2b1e7b1196cedd39d7052db534e781bb13
ms.openlocfilehash: 7a20b59c404959c4ec209e8c29ac61ab71233e87


---

# Konfigurowanie etykiety w celu zastosowania ochrony usługi Rights Management

>*Dotyczy: Azure Information Protection (wersja zapoznawcza)*

**[Niniejsze informacje mają charakter wstępny i mogą ulec zmianom. ]**

Najbardziej poufne dokumenty i wiadomości e-mail możesz chronić przy użyciu usługi Azure Rights Management, która korzysta z zasad szyfrowania, tożsamości oraz autoryzacji w celu zapobieżenia utracie danych. Ta ochrona jest stosowana, gdy skonfigurujesz etykietę do używania szablonu usługi Rights Management. 

Ten szablon może być jednym z szablonów domyślnych, które są automatycznie tworzone podczas aktywacji usługi Azure Rights Management, lub szablonem niestandardowym. Szablony działów są obsługiwane, ale stosują ochronę tylko wtedy, gdy autor dokumentu lub wiadomości e-mail znajduje się w skonfigurowanym zakresie szablonu. Jeśli użytkownik znajduje się poza zakresem, zobaczy komunikat informujący o tym, że usługa Azure Information Protection nie może zastosować etykiety.

## Jak działa ochrona

Gdy dokument lub wiadomość e-mail są chronione przez usługę Azure Rights Management, będą szyfrowane podczas przechowywania i podczas przesyłania, a odszyfrować je mogą tylko autoryzowani użytkownicy. Szyfrowanie zostaje utrzymane w dokumencie lub wiadomości e-mail, nawet w przypadku zmiany nazwy dokumentu lub wiadomości. Ponadto możesz skonfigurować prawa i ograniczenia użytkowania, np.:

- Tylko użytkownicy w organizacji mogą otworzyć dokument lub wiadomość e-mail.

- Tylko użytkownicy w dziale marketingu mogą edytować i drukować dokument lub wiadomość e-mail, podczas gdy wszyscy inni użytkownicy w organizacji mogą jedynie wyświetlać dokument lub wiadomość e-mail.

- Użytkownicy nie mogą przesłać wiadomości e-mail dalej.

- Dokumentów lub wiadomości e-mail przesyłanych do partnerów biznesowych nie można otworzyć po określonej dacie.

Aby uzyskać więcej informacji o szablonach i sposobie konfigurowania tych praw i ograniczeń użytkowania, zobacz [Konfigurowanie szablonów niestandardowych usługi Azure Rights Management](../deploy-use/configure-custom-templates.md).

Aby uzyskać więcej informacji na temat usługi Azure Rights Management i jej działania, zobacz [Co to jest usługa Azure Rights Management?](../understand-explore/what-is-azure-rms.md)

> [!IMPORTANT]
> Aby skonfigurować etykietę do stosowania ochrony usługi Rights Management, usługa Azure Rights Management musi być aktywowana dla Twojej organizacji. Jeśli jeszcze nie zostało to zrobione, zobacz [Aktywacja usługi Azure Rights Management](../deploy-use/activate-service.md).


## Aby skonfigurować etykietę w celu zastosowania ochrony usługi Rights Management

1. Zaloguj się do [portalu Azure](https://portal.azure.com).
 
2. Następnie w menu centralnym kliknij **Przeglądaj** i w polu filtru zacznij pisać **Information**. Wybierz pozycję **Azure Information Protection**.

3. W bloku **Azure Information Protection** wybierz etykietę, którą chcesz skonfigurować w celu stosowania ochrony usługi Rights Management.

4. W bloku **Etykieta** w sekcji **Ustawianie szablonu usług RMS w celu ochrony dokumentów i wiadomości e-mail oznaczonych tą etykietą** skonfiguruj następujące ustawienia:

    - Jeśli widzisz opcję **Wybierz szablon usług RMS z**: wybierz ustawienie **Azure RMS**. 
    
        Nie wybieraj opcji **AD RMS** ani skojarzonych opcji konfiguracji bez wsparcia ze strony firmy Microsoft. Jeśli chcesz testować usługę Azure Information Protection z usługami Active Directory Rights Management, wyślij wiadomość e-mail na adres askipteam@microsoft.com. 
    
    - Dla opcji **Wybierz szablon usług RMS**: kliknij menu rozwijane i wybierz szablon, którego chcesz użyć do ochrony dokumentów i wiadomości e-mail przy użyciu tej etykiety.

        > [!NOTE] Jeśli utworzysz nowy szablon po otworzeniu bloku **Etykieta**, zamknij ten blok i wróć do kroku 3, aby nowo utworzony szablon został pobrany z platformy Azure i był dostępny do wyboru.

5. Kliknij polecenie **Zapisz**.

6. Aby udostępnić użytkownikom zmiany, w bloku **Azure Information Protection** kliknij przycisk **Opublikuj**.

## Następne kroki

Aby uzyskać więcej informacji o konfigurowaniu zasad usługi Azure Information Protection, użyj linków w sekcji [Konfigurowanie zasad organizacji](configure-policy.md#configuring-your-organization-s-policy).  



<!--HONumber=Jul16_HO5-->


