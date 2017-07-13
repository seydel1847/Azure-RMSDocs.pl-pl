---
title: "Niestandardowe konfiguracje klienta usługi Azure Information Protection"
description: "Informacje na temat dostosowywania klienta usługi Azure Information Protection dla systemu Windows."
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 05/23/2017
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: 5eb3a8a4-3392-4a50-a2d2-e112c9e72a78
ms.reviewer: eymanor
ms.suite: ems
ms.openlocfilehash: 6ab5465db1527e6236d2dca466936c36b260f03d
ms.sourcegitcommit: 04eb4990e2bf0004684221592cb93df35e6acebe
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/30/2017
---
# Niestandardowe konfiguracje klienta usługi Azure Information Protection
<a id="custom-configurations-for-the-azure-information-protection-client" class="xliff"></a>

>*Dotyczy: usługi zarządzania prawami dostępu w usłudze Active Directory, Azure Information Protection, Windows 10, Windows 8.1, Windows 8, Windows 7 z dodatkiem SP1, Windows Server 2016, Windows Server 2012 R2, Windows Server 2012*

Użyj poniższych informacji na potrzeby tworzenia konfiguracji zaawansowanych, które mogą być konieczne w przypadku określonych scenariuszy lub podzbiorów użytkowników w zakresie zarządzania klientem usługi Azure Information Protection. 

## Zapobieganie monitom o logowanie dla komputerów korzystających tylko z usługi AD RMS
<a id="prevent-sign-in-prompts-for-ad-rms-only-computers" class="xliff"></a>

Domyślnie klient usługi Azure Information Protection automatycznie próbuje połączyć się z usługą Azure Information Protection. Dla komputerów, które komunikują się tylko z usługą AD RMS, może to spowodować wyświetlenie użytkownikom zbędnego monitu o logowanie. Temu monitowi o logowanie można zapobiec, edytując rejestr:

Znajdź następującą nazwę wartości, a następnie ustaw dane wartości na **0**:

**HKEY_CURRENT_USER\SOFTWARE\Microsoft\MSIP\EnablePolicyDownload** 

Niezależnie od tego ustawienia klient usługi Azure Information Protection postępuje zgodnie ze standardowym [procesem odnajdowania usługi RMS](../rms-client/client-deployment-notes.md#rms-service-discovery), aby odnaleźć swój klaster usługi AD RMS.

## Zaloguj się jako inny użytkownik
<a id="sign-in-as-a-different-user" class="xliff"></a>

W środowisku produkcyjnym użytkownik nie ma zazwyczaj potrzeby logowania się jako inny użytkownik w przypadku korzystania z klienta usługi Azure Information Protection. Może to być jednak konieczne w przypadku administratora, jeśli występuje wielu dzierżawców. Na przykład oprócz dzierżawcy usługi Office 365 lub platformy Azure, którego używa Twoja organizacja, używany jest dzierżawca testowy.

Aby sprawdzić, za pomocą którego konta nastąpiło logowanie, otwórz okno dialogowe **Microsoft Azure Information Protection**, uruchom aplikację pakietu Office i na karcie **Narzędzia główne** w grupie **Ochrona** kliknij opcję **Chroń**, a następnie kliknij przycisk **Pomoc i opinie**. Nazwa konta jest widoczna w sekcji **Stan klienta**.

Szczególnie w przypadku korzystania z konta administratora należy koniecznie sprawdzić nazwę domeny zalogowanego konta. Na przykład w przypadku korzystania z konta „Administrator” dla dwóch różnych dzierżawców można łatwo przeoczyć, że logowanie nastąpiło przy użyciu prawidłowej nazwy konta, ale niewłaściwej domeny. Jeśli tak się stało, może wystąpić problem z pobraniem zasad usługi Azure Information Protection albo nie będzie widać oczekiwanych etykiet lub funkcji.

Aby zalogować się jako inny użytkownik:

1. W Edytorze rejestru przejdź do pozycji **HKEY_CURRENT_USER\SOFTWARE\Microsoft\MSIP** i usuń wartość **TokenCache** (i jej powiązane dane wartości).

2. Uruchom ponownie wszystkie otwarte aplikacje pakietu Office i zaloguj się przy użyciu innego konta użytkownika. Jeśli w aplikacji pakietu Office nie został wyświetlony monit o zalogowanie się do usługi Azure Information Protection, wróć do okna dialogowego **Microsoft Azure Information Protection** i kliknij przycisk **Zaloguj** w zaktualizowanej sekcji **Stan klienta**.

Dodatkowo:

- Jeśli korzystasz z logowania jednokrotnego, wyloguj się z systemu Windows i po wprowadzeniu zmian w rejestrze zaloguj się przy użyciu konta innego użytkownika. Klient usługi Azure Information Protection przeprowadzi automatyczne uwierzytelnienie przy użyciu aktualnie zalogowanego konta użytkownika.

- Jeśli chcesz ponownie zainicjować środowisko usługi Azure Rights Management (tzw. „bootstrapping”), możesz to zrobić za pomocą opcji **Resetuj** w [narzędziu Analizator RMS](https://www.microsoft.com/en-us/download/details.aspx?id=46437).

- Aby usunąć aktualnie pobrane zasady usługi Azure Information Protection, usuń plik **Policy.msip** z folderu **%localappdata%\Microsoft\MSIP**.

## Ukryj opcję menu Klasyfikuj i chroń w Eksploratorze plików systemu Windows
<a id="hide-the-classify-and-protect-menu-option-in-windows-file-explorer" class="xliff"></a>

Użytkownicy korzystający z klienta usługi Azure Information Protection w wersji 1.3.0.0 lub nowszej mogą skonfigurować tę konfigurację zaawansowaną, edytując rejestr. 

Utwórz następującą nazwę wartości DWORD (z dowolnymi danymi wartości):

**HKEY_CLASSES_ROOT\AllFilesystemObjects\shell\Microsoft.Azip.RightClick\LegacyDisable**

## Obsługa odłączonych komputerów
<a id="support-for-disconnected-computers" class="xliff"></a>

Domyślnie klient usługi Azure Information Protection automatycznie próbuje połączyć się z usługą Azure Information Protection, aby pobrać najnowsze zasady usługi Azure Information Protection. W przypadku komputera pozbawionego w danym momencie możliwości nawiązania połączenia z Internetem można zapobiec próbie nawiązania połączenia z usługą, edytując rejestr. Znajdź następującą nazwę wartości i ustaw dane wartości **0**:

**HKEY_CURRENT_USER\SOFTWARE\Microsoft\MSIP\EnablePolicyDownload** 

Upewnij się, że w folderze **%localappdata%\Microsoft\MSIP** znajduje się prawidłowy plik zasad klienta o nazwie **Policy.msip**. W razie potrzeby można wyeksportować zasady z portalu Azure Portal i skopiować wyeksportowany plik do komputera klienckiego. Ta metoda umożliwia również zastąpienie nieaktualnego pliku zasad najnowszymi opublikowanymi zasadami.

## Integracja z klasyfikacją wiadomości programu Exchange dla rozwiązań etykietowania urządzeń przenośnych
<a id="integration-with-exchange-message-classification-for-a-mobile-device-labeling-solution" class="xliff"></a>

Pomimo tego, że program Outlook w sieci Web nie obsługuje natywnie klasyfikacji ani ochrony usługi Azure Information Protection, można użyć klasyfikacji wiadomości programu Exchange w celu poszerzenia zasięgu używania etykiet usługi Azure Information Protection o użytkowników urządzeń przenośnych.

W tym celu: 

1. Użyj polecenia cmdlet [New-MessageClassification](https://technet.microsoft.com/library/bb124400) środowiska PowerShell programu Exchange w celu utworzenia klasyfikacji wiadomości z właściwością Name, która mapuje do nazw etykiet użytkownika w zasadach usługi Azure Information Protection. 

2. Utwórz dla każdej etykiety regułę transportu programu Exchange: zastosuj regułę, jeśli właściwości wiadomości obejmują skonfigurowaną przez Ciebie klasyfikację, a następnie zmodyfikuj właściwości wiadomości, aby ustawić nagłówek wiadomości. 

    Informacje, jakie należy określić dla nagłówka wiadomości, można zidentyfikować, sprawdzając nagłówki internetowe wiadomości e-mail wysłanej i sklasyfikowanej za pomocą etykiety usługi Azure Information Protection. Wyszukaj nagłówek **msip_labels** i ciąg, który następuje zaraz po nim, łącznie ze średnikiem. Korzystając z poprzedniego przykładu:
    
    **msip_labels: MSIP_Label_0e421e6d-ea17-4fdb-8f01-93a3e71333b8_Enabled=True;**
    
    Następnie dla nagłówka wiadomości w regule określ element **msip_labels** dla nagłówka oraz pozostałe elementy ciągu dla wartości nagłówka. Na przykład:
    
    ![Przykładowa reguła transportu usługi Exchange Online, która ustawia nagłówek wiadomości dla określonej etykiety usługi Azure Information Protection](../media/exchange-rule-for-message-header.png)

Zanim to przetestujesz, pamiętaj, że podczas tworzenia lub edytowania reguł transportu często występuje opóźnienie (na przykład trzeba odczekać godzinę). Gdy reguła jest aktywna, w przypadku użytkowników, którzy używają aplikacji Outlook Web Access lub klienta urządzenia przenośnego obsługującego ochronę za pomocą usługi Rights Management, ma miejsce następujący scenariusz: 

- Użytkownicy wybierają klasyfikację wiadomości programu Exchange i wysyłają wiadomość e-mail.

- Reguła programu Exchange wykrywa klasyfikację programu Exchange i odpowiednio modyfikuje nagłówek wiadomości w celu dodania klasyfikacji usługi Azure Information Protection.

- Gdy adresaci korzystający z klienta usługi Azure Information Protection wyświetlają wiadomość e-mail w programie Outlook, widzą przypisane etykiety usługi Azure Information Protection i wszelkie powiązane nagłówki wiadomości e-mail, stopki lub znaki wodne. 

Jeśli etykiety usługi Azure Information Protection zakładają zastosowanie ochrony zarządzania prawami, dodaj tę ochronę do konfiguracji reguły, zaznaczając opcję modyfikacji zabezpieczeń wiadomości, zastosuj ochronę praw, a następnie wybierz szablon RMS lub opcję Nie przesyłaj dalej.

Możesz również skonfigurować reguły transportu na potrzeby mapowania odwrotnego. W tym celu po wykryciu etykiety usługi Azure Information Protection ustaw odpowiednią klasyfikację wiadomości programu Exchange. Wykonaj następujące czynności:

- Dla każdej etykiety usługi Azure Information Protection utwórz regułę transportu, która będzie stosowana, jeśli nagłówek **msip_labels** będzie zawierał nazwę Twojej etykiety (na przykład **Ogólne**), i zastosuj klasyfikację wiadomości mapowaną do tej etykiety.


## Następne kroki
<a id="next-steps" class="xliff"></a>
Po dostosowaniu klienta usługi Azure Information Protection zapoznaj się z poniższymi informacjami dodatkowymi przydatnymi przy obsłudze tego klienta:

- [Rejestrowanie plików i użycia klienta](client-admin-guide-files-and-logging.md)

- [Śledzenie dokumentów](client-admin-guide-document-tracking.md)

- [Obsługiwane typy plików](client-admin-guide-file-types.md)

- [Polecenia programu PowerShell](client-admin-guide-powershell.md)


[!INCLUDE[Commenting house rules](../includes/houserules.md)]
