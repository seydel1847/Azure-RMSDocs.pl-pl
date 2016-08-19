---
title: "Konfigurowanie etykiety pod kątem oznaczeń wizualnych w usłudze Azure Information Protection | Azure Rights Management"
description: 
author: cabailey
manager: mbaldwin
ms.date: 08/10/2016
ms.topic: article
ms.prod: azure
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: df2676eeb062-f25a-4cf8-a782-e59664427d54
translationtype: Human Translation
ms.sourcegitcommit: b2263c212a1b869b778767493645f10ad821828f
ms.openlocfilehash: 78b68c7a502776c6492437e9b8a5c3f1ebf27f95


---

# Konfigurowanie etykiety pod kątem oznaczeń wizualnych w usłudze Azure Information Protection

>*Dotyczy: Azure Information Protection (wersja zapoznawcza)*

**[Niniejsze informacje mają charakter wstępny i mogą ulec zmianom. ]**

Gdy przypisujesz etykietę do dokumentu lub wiadomości e-mail, możesz wybrać kilka opcji, dzięki którym wybrana klasyfikacja będzie łatwo widoczna. Oznaczenia wizualne to nagłówek, stopka i znak wodny:

Oznaczenia wizualne są stosowane w dokumentach Word, Excel i PowerPoint po zastosowaniu etykiety i zapisaniu dokumentu. W przypadku wiadomości e-mail oznaczenia wizualne są stosowane, gdy wiadomość e-mail jest wysyłana.

Dodatkowe informacje dotyczące tych oznaczeń wizualnych:

- Nagłówki i stopki dotyczą programów Word, Excel, PowerPoint i Outlook.

- Znaki wodne dotyczą programów Word, Excel i PowerPoint:

    - Excel: znaki wodne są widoczne tylko w trybach Podgląd wydruku i Układ strony oraz po wydrukowaniu.

    - PowerPoint: znaki wodne są stosowane do wzorca slajdów jako obraz tła.

- Można określić tylko ciąg tekstowy lub użyć [zmiennych](#using-variables-in-the-text-string) w celu dynamicznego tworzenia ciągu tekstowego podczas stosowania nagłówka, stopki lub znaku wodnego. 

Użyj poniższych instrukcji, aby skonfigurować oznaczenia wizualne dla etykiety.

1. Jeśli jeszcze tego nie zrobiono, zaloguj się do [Portalu Azure](https://portal.azure.com), a następnie przejdź do bloku **Azure Information Protection**. 
    
    Na przykład w menu centralnym kliknij przycisk **Przeglądaj** i w polu filtru zacznij wpisywać ciąg **Information**. Wybierz pozycję **Azure Information Protection**.

2. W bloku **Azure Information Protection** wybierz etykietę, którą chcesz skonfigurować pod kątem oznaczeń wizualnych.

3. W bloku **Etykieta** w sekcji **Ustaw oznaczenie wizualne (np. nagłówek lub stopkę)** skonfiguruj ustawienia dla żądanych oznaczeń wizualnych, a następnie kliknij przycisk **Zapisz**:

    - Aby skonfigurować nagłówek: dla opcji **Dokumenty oznaczone tą etykietą mają nagłówek** wybierz wartość **Wł.**, jeśli chcesz użyć nagłówka, lub **Wył.**, jeśli nie chcesz. Jeśli wybierzesz opcję **Wł.**, następnie należy określić tekst, rozmiar, kolor i wyrównanie nagłówka.
    
    - Aby skonfigurować stopkę: dla opcji **Dokumenty oznaczone tą etykietą mają stopkę** wybierz wartość **Wł.**, jeśli chcesz użyć stopki, lub **Wył.**, jeśli nie chcesz. Jeśli wybierzesz opcję **Wł.**, następnie należy określić tekst, rozmiar, kolor i wyrównanie stopki.
    
    - Aby skonfigurować znak wodny: dla opcji **Dokumenty oznaczone tą etykietą mają znak wodny** wybierz wartość **Wł.**, jeśli chcesz użyć znaku wodnego, lub **Wył.**, jeśli nie chcesz. Jeśli wybierzesz opcję **Wł.**, następnie należy określić tekst, rozmiar i kolor znaku wodnego oraz układ nagłówka. 

4. Aby udostępnić użytkownikom zmiany, w bloku **Azure Information Protection** kliknij przycisk **Opublikuj**.

## Używanie zmiennych w ciągu tekstowym

W ciągu tekstowym dla nagłówka, stopki lub znaku wodnego można używać następujących zmiennych:

- `${Item.Label}` dla wybranej etykiety

- `${Item.Name}` dla nazwy pliku lub tematu wiadomości e-mail

- `${Item.Location}` dla ścieżki pliku

- `${User.Name}` dla właściciela dokumentu lub wiadomości e-mail

- `${Event.DateTime}` dla daty i godziny ustawienia wybranej etykiety 
    
Przykład: w przypadku określenia ciągu `Document: ${item.name} Sensitivity: ${item.label}` dla stopki etykiety Tajne, tekst stopki stosowany dla udokumentowanego nazwanego pliku project.docx będzie następujący: **Document: project.docx Sensitivity: Tajne**.

## Następne kroki

Aby uzyskać więcej informacji o konfigurowaniu zasad usługi Azure Information Protection, użyj linków w sekcji [Konfigurowanie zasad organizacji](configure-policy.md#configuring-your-organization-s-policy).  





<!--HONumber=Aug16_HO2-->


