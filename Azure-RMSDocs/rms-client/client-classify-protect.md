---
title: "Klasyfikowanie i ochrona pliku lub wiadomości e-mail za pomocą usługi Azure Information Protection| Azure Information Protection"
description: "Instrukcje dotyczące sposobu klasyfikowania i ochrony dokumentów i wiadomości e-mail użytkownika."
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 12/07/2016
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: 75268245-6f14-4218-b904-202f63fb3ce6
ms.reviewer: esaggese
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: e6d4cc50259b9d9bb73a75c648f9e6915562accf
ms.openlocfilehash: e1d61fbe1d74a4a57d9a1fdf518aeb0242d0f7ad


---

# <a name="classify-and-protect-a-file-or-email-by-using-azure-information-protection"></a>Klasyfikowanie i ochrona pliku lub wiadomości e-mail za pomocą usługi Azure Information Protection

>*Dotyczy: usługi Active Directory Rights Management, Azure Information Protection, Windows 10, Windows 8.1, Windows 8, Windows 7 z dodatkiem SP1*

**[Ta wersja klienta jest w wersji zapoznawczej i może ulec zmianie.]**

Najprostszy sposób klasyfikowania i ochrony dokumentów i wiadomości e-mail jest dostępny podczas ich tworzenia lub edytowania za pośrednictwem aplikacji komputerowych pakietu Office: **Word**, **Excel**, **PowerPoint** i **Outlook**. 

Pliki można jednak klasyfikować i chronić także za pomocą **Eksploratora plików**, który obsługuje dodatkowe typy plików i stanowi wygodny sposób klasyfikowania oraz ochrony wielu plików jednocześnie.

## <a name="using-office-apps-to-classify-and-protect-your-documents-and-emails"></a>Korzystanie z aplikacji pakietu Office do klasyfikowania i ochrony dokumentów i wiadomości e-mail

Za pomocą paska usługi Azure Information Protection wybierz jedną z etykiet, które zostały skonfigurowane dla Ciebie. Na przykład:

![Przykład paska usługi Azure Information Protection](../media/info-protect-bar-not-set-callout.png)


## <a name="using-file-explorer-to-classify-and-protect-files"></a>Klasyfikowanie i ochrona plików za pomocą Eksploratora plików

Korzystając z Eksploratora plików, można szybko klasyfikować i chronić pojedynczy plik, wiele plików lub folder. 

Po wybraniu folderu do wszystkich plików znajdujących się w nim i jego podfolderach zostaną automatycznie przypisane ustawione opcje ochrony. Jednak nowe pliki tworzone w tym folderze lub jego podfolderach nie są konfigurowane automatycznie z użyciem tych opcji.

Podczas korzystania z Eksploratora plików do klasyfikowania i ochrony plików można zauważyć, że etykiety nie zawsze są dostępne. Dzieje się tak w przypadku, gdy wybrane pliki nie obsługują klasyfikacji. W przypadku tych plików można wybrać etykietę tylko wtedy, gdy administrator skonfigurował etykietę do stosowania ochrony. Można też określić własne ustawienia ochrony. 

Aby uzyskać listę typów plików, które są obsługiwane w Eksploratorze plików, zobacz sekcję [Typy plików obsługiwane w funkcji klasyfikacji i ochrony](#file-types-supported-for-classification-and-protection) na tej stronie.


### <a name="to-classify-and-protect-a-file-by-using-file-explorer"></a>Aby sklasyfikować i chronić plik za pomocą Eksploratora plików

1.  W Eksploratorze plików wybierz plik, wiele plików lub folder. Kliknij prawym przyciskiem myszy i wybierz opcję **Klasyfikuj i chroń (wersja zapoznawcza)**. 

2. W oknie dialogowym **Klasyfikuj i chroń — Azure Information Protection** użyj etykiet w sposób analogiczny jak w aplikacji pakietu Office, który ustawia klasyfikację i ochronę w sposób zdefiniowany przez administratora. Jeśli nie można wybrać etykiety (jest niedostępna), wybrany plik nie obsługuje klasyfikacji, ale można go chronić.

3. Aby chronić plik, wybierz ustawienie ochrony spośród ustawień zdefiniowanych przez administratora dla wybranej etykiety (**Automatycznie, na podstawie wybranej etykiety klasyfikacji**) lub określ własne ustawienia (**Zastąp uprawnieniami niestandardowymi**).
    
    Opcja zastąpienia nie używa żadnych ustawień ochrony, które administrator mógł zdefiniować dla wybranej etykiety. Zamiast tego można określić własne ustawienia ochrony. 

4. Jeśli wybrano opcję zastąpienia, należy określić następujące ustawienia:

    - **Wybierz uprawnienia**: Wybierz poziom dostępu, który ma być przypisany użytkownikom przy ochronie wybranego pliku lub plików.
    
    - **Wybierz użytkowników**: Określ osoby, które powinny mieć wybrane przez Ciebie uprawnienia do pliku lub plików. Do wyszukiwania i wybierania osób i grup w organizacji można użyć książki adresowej. W przypadku osób z innej organizacji należy określić ich pełny adres e-mail. Upewnij się, że używasz służbowego adresu e-mail, ponieważ osobiste adresy e-mail nie są obecnie obsługiwane.
        
    - **Unieważnij dostęp**: Wybierz tę opcję tylko w przypadku plików zależnych od czasu, dzięki czemu określone przez Ciebie osoby nie będą mogły otworzyć wybranego pliku lub plików po określonej przez Ciebie dacie. Nadal będziesz mieć możliwość otwarcia oryginalnego pliku, ale po północy (Twojej bieżącej strefy czasowej) wybranego przez Ciebie dnia określone przez Ciebie osoby nie będą mogły go otworzyć.

5. Kliknij opcję **Zastosuj**, a następnie kliknij opcję **Zamknij**.

Wybrany plik lub pliki są teraz sklasyfikowane i chronione zgodnie z wybranymi przez Ciebie opcjami. W niektórych przypadkach (kiedy dodanie ochrony powoduje zmianę rozszerzenia nazwy pliku) oryginalny plik znajdujący się w Eksploratorze plików zostaje zastąpiony nowym plikiem oznaczonym ikoną kłódki, sygnalizującą ochronę za pomocą usługi Azure Information Protection. Na przykład:

![Chroniony plik z ikoną kłódki usługi Azure Information Protection](../media/Pfile.png)

Jeśli zmienisz zdanie na temat klasyfikacji i ochrony lub zechcesz później zmodyfikować ustawienia, po prostu powtórz proces z nowymi ustawieniami.

Wcześniej określona dla pliku klasyfikacja i ochrona obowiązuje nadal, nawet jeśli plik zostanie wysłany za pomocą poczty e-mail lub zapisany w innej lokalizacji. Jeśli plik jest chroniony, można śledzić, w jaki sposób jest używany, i w razie potrzeby odwołać dostęp do niego. Aby uzyskać więcej informacji, zobacz temat [Śledzenie i odwoływanie dokumentów chronionych podczas korzystania z usługi Azure Information Protection](client-track-revoke.md). 

#### <a name="file-types-supported-for-classification-and-protection"></a>Typy plików obsługiwane w funkcji klasyfikacji i ochrony

Sama klasyfikacja jest obsługiwana dla następujących typów plików. Inne typy plików obsługują klasyfikację, gdy jednocześnie są chronione.

- **Microsoft Visio**: .vsdx, .vsdm, .vssx, .vssm, .vsd, .vdw, .vst

- **Microsoft Project**: .mpp, .mpt

- **Microsoft Publisher**: .pub

- **Microsoft Office 97, Office 2010, Office 2003**: .xls, .xlt, .doc, .dot, .ppt, .pps, .pot

- **Microsoft XPS**: .xps .oxps

- **Obrazy**: .jpg, .jpe, .jpeg, .jif, .jfif, .jfi.png, .tif, .tiff

- **SolidWorks**: .sldprt, .slddrw, .sldasm

- **Autodesk Design Review 2013**: .dwfx

- **Adobe Photoshop**: .psd

- **Digital Negative**: .dng


Ochrona za pomocą usługi Rights Management jest obsługiwana w przypadku typów plików udokumentowanych w artykule [Konfiguracja interfejsu API plików](../develop/file-api-configuration.md). Tę ochronę można zastosować automatycznie po wybraniu etykiety, która została skonfigurowana przez administratora, lub można określić własne ustawienia ochrony za pomocą [poziomów uprawnień](../deploy-use/configure-usage-rights.md#rights-included-in-permissions-levels). 


## <a name="other-instructions"></a>Inne instrukcje
Aby uzyskać instrukcje dotyczące wykonywania określonych czynności, zobacz następujące sekcje z podręcznika użytkownika usługi Azure Information Protection:

-   [Co chcesz zrobić?](client-user-guide.md#what-do-you-want-to-do)




<!--HONumber=Dec16_HO1-->


