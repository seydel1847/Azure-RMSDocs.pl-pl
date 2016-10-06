---
title: "Operacje cyklu życia klucza dzierżawy zarządzanego przez firmę Microsoft | Azure Information Protection"
description: "Informacje na temat operacji cyklu życia, które są istotne, jeśli firma Microsoft zarządza Twoim kluczem dzierżawy dla usługi Azure Information Protection (domyślnie)."
author: cabailey
manager: mbaldwin
ms.date: 09/25/2016
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: 3c48cda6-e004-4bbd-adcf-589815c56c55
ms.reviewer: esaggese
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: d5b6a1fc3fa0a19f3a6b65aa7b8815eda7432cd7
ms.openlocfilehash: 9c2a7d9e65dc860e0bd90789a412a8ef46f946ad


---


# Operacje cyklu życia klucza dzierżawy zarządzane przez firmę Microsoft

>*Dotyczy: Azure Information Protection, Office 365*

Jeśli firma Microsoft zarządza Twoim kluczem dzierżawy dla usługi Azure Information Protection (domyślnie), użyj poniższych sekcji w celu uzyskania dodatkowych informacji na temat operacji cyklu życia związanych z tą topologią.

## Odwołanie klucza dzierżawy
Po anulowaniu subskrypcji usługi Azure Information Protection usługa ta wstrzymuje korzystanie z klucza dzierżawy, co nie wymaga żadnej akcji ze strony użytkownika.

## Ponowne tworzenie klucza dzierżawy
Ponowne tworzenie jest nazywane także wycofywaniem klucza. Klucza dzierżawy nie należy tworzyć ponownie, jeśli nie jest to naprawdę konieczne. Starsze programy klienckie, takie jak Office 2010, nie zostały zaprojektowane do bezproblemowej zmiany klucza. W tym scenariuszu należy usunąć stan usługi Rights Management na komputerach przy użyciu zasad grupy lub równoważnego mechanizmu. Występują jednak określone zdarzenia, które mogą wymusić ponowne utworzenie klucza dzierżawy. Na przykład:

-   Firma została podzielona na dwie lub więcej firm. Po ponownym utworzeniu klucza dzierżawy nowa firma nie będzie miała dostępu do nowej zawartości publikowanej przez pracowników. Mogą oni uzyskać dostęp do starej zawartości, jeśli dysponują kopią starego klucza dzierżawy.

-   Uważasz, że zostało naruszone bezpieczeństwo kopii głównej klucza dzierżawy, która należy do Ciebie.

Możesz ponownie utworzyć klucz dzierżawy, [kontaktując się z pomocą techniczną firmy Microsoft](../get-started/information-support.md#to-contact-microsoft-support) w celu otworzenia **sprawy pomocy technicznej usługi Azure Information Protection z żądaniem ponownego utworzenia klucza dzierżawy usługi Azure Information Protection**. Musisz udowodnić, że jesteś administratorem dzierżawy usługi Azure Information Protection oraz wiedzieć, że potwierdzenie tego procesu może potrwać kilka dni. Naliczane są standardowe opłaty za pomoc techniczną. Ponowne tworzenie klucza dzierżawy nie jest bezpłatną usługą pomocy technicznej.

Po ponownym utworzeniu klucza dzierżawy nowa zawartość jest chroniona przy użyciu nowego klucza dzierżawy. Następuje to etapowo, w związku z czym przez pewien czas część nowej zawartości będzie nadal chroniona przez stary klucz dzierżawy. Zawartość chroniona wcześniej jest nadal chroniona przez stary klucz dzierżawy. W celu obsługi tego scenariusza usługa Azure Information Protection zachowuje stary klucz dzierżawy, co pozwala na wydawanie licencji dla starszej zawartości.

## Tworzenie kopii zapasowej i odzyskiwanie klucza dzierżawy
Za tworzenie kopii zapasowych klucza dzierżawy odpowiada firma Microsoft. Nie wymaga to żadnej akcji z Twojej strony.

## Eksport klucza dzierżawy
Konfigurację i klucz dzierżawy usługi Azure Information Protection można wyeksportować, wykonując instrukcje zamieszczone w następujących trzech krokach:

### Krok 1. Zainicjowanie eksportu

-   W tym celu [skontaktuj się z pomocą techniczną firmy Microsoft](../get-started/information-support.md#to-contact-microsoft-support), aby otworzyć **sprawę pomocy technicznej usługi Azure Information Protection z żądaniem eksportu klucza usługi Azure Information Protection**. Musisz udowodnić, że jesteś administratorem dzierżawy usługi Azure Information Protection oraz wiedzieć, że potwierdzenie tego procesu może potrwać kilka dni. Naliczane są standardowe opłaty za pomoc techniczną. Eksportowanie klucza dzierżawy nie jest bezpłatną usługą pomocy technicznej.

### Krok 2. Oczekiwanie na weryfikację

-   Firma Microsoft sprawdza, czy żądanie wydania klucza dzierżawy usługi Azure Information Protection jest uzasadnione. Proces ten może potrwać do 3 tygodni.

### Krok 3. Otrzymanie instrukcji dotyczących klucza od CSS

-   Pomoc techniczna firmy Microsoft (CSS, Customer Support Services) przesyła konfigurację i klucz dzierżawy usługi Azure Information Protection w formie zaszyfrowanej, w chronionym hasłem pliku o rozszerzeniu tpd. W tym celu CSS przesyła najpierw Tobie (osobie, która zainicjowała eksport) narzędzie pocztą e-mail. Narzędzie należy uruchomić z wiersza polecenia w następujący sposób:

    ```
    AadrmTpd.exe -createkey
    ```
    Powoduje to wygenerowanie pary kluczy RSA oraz zapisanie części publicznej i prywatnej w formie plików w bieżącym folderze. Przykład: **PublicKey-FA29D0FE-5049-4C8E-931B-96C6152B0441.txt** i **PrivateKey-FA29D0FE-5049-4C8E-931B-96C6152B0441.txt**.

    Odpowiedz na wiadomość e-mail od CSS, dołączając plik o nazwie rozpoczynającej się od **PublicKey**. CSS przesyła następnie plik TPD w formie pliku xml zaszyfrowanego przy użyciu Twojego klucza RSA. Skopiuj ten plik do folderu, w którym pierwotnie zostało uruchomione narzędzie AadrmTpd i uruchom narzędzie ponownie przy użyciu pliku o nazwie rozpoczynającej się od **PrivateKey** oraz pliku otrzymanego od CSS. Na przykład:

    ```
    AadrmTpd.exe -key PrivateKey-FA29D0FE-5049-4C8E-931B-96C6152B0441.txt -target TPD-77172C7B-8E21-48B7-9854-7A4CEAC474D0.xml
    ```
    Polecenie to powinno zwracać dwa pliki: jeden z nich zawiera hasło do chronionego hasłem pliku TPD w formie zwykłego tekstu, a drugi to sam chroniony hasłem plik TPD. W celu zapewnienia odwołań krzyżowych oba powinny mieć identyfikatory GUID jako pliki kluczy publicznych i prywatnych w momencie uruchomienia polecenia AadrmTpd.exe -createkey:

    -   Password-FA29D0FE-5049-4C8E-931B-96C6152B0441.txt

    -   ExportedTPD-FA29D0FE-5049-4C8E-931B-96C6152B0441.xml

    Należy wykonać kopię zapasową tych plików i zapisać je w bezpiecznym miejscu, co pozwoli na kontynuowanie odszyfrowywania zawartości chronionej przy użyciu tego klucza dzierżawy. Dodatkowo w przypadku migracji do usługi AD RMS można zaimportować ten plik TPD (plik o nazwie rozpoczynającej się od **ExportedTDP**) do serwera usługi AD RMS.

### Krok 4. Ciągły: ochrona klucza dzierżawy

-   Po otrzymaniu klucza dzierżawy należy przechowywać go w bezpiecznym miejscu, ponieważ uzyskanie dostępu do niego umożliwia odszyfrowanie wszystkich dokumentów chronionych przy użyciu tego klucza.

    Jeśli przyczyną eksportu klucza dzierżawy jest chęć zaprzestania korzystania z usługi Azure Information Protection, najlepszym rozwiązaniem jest dezaktywacja usługi Azure Rights Management w dzierżawie usługi Azure Information Protection. Nie należy opóźniać tego działania po otrzymaniu klucza dzierżawy, ponieważ umożliwia to ograniczenie konsekwencji w przypadku uzyskania dostępu do klucza dzierżawy przez osobę nieupoważnioną. Aby uzyskać instrukcje, zobacz [Likwidowanie i dezaktywowanie usługi Azure Rights Management](decommission-deactivate.md).

## Reakcja na naruszenie zabezpieczeń
Żaden system zabezpieczeń, niezależnie od jego siły, nie jest kompletny bez procedur reakcji na naruszenie zabezpieczeń. Klucz dzierżawy może zostać naruszony lub skradziony. Nawet w przypadku zapewnienia odpowiedniej ochrony klucza mogą występować luki w zabezpieczeniach dotyczące obecnej generacji technologii sprzętowych modułów zabezpieczeń, długości kluczy i algorytmów.

Firma Microsoft ma dedykowany zespół, który reaguje na przypadki naruszenia zabezpieczeń produktów i usług. Bezpośrednio po uzyskaniu wiarygodnego raportu o incydencie zespół ten bada jego zakres, przyczynę i środki naprawcze. Jeśli dane zdarzenie ma wpływ na Twoje zasoby, firma Microsoft powiadomi o tym administratorów dzierżawy usługi Azure Information Protection pocztą e-mail, korzystając z adresu podanego podczas rejestrowania subskrypcji.

W przypadku naruszenia zabezpieczeń najlepsze działanie, które może podjąć użytkownik lub firma Microsoft, jest zależne od zakresu naruszenia. Firma Microsoft zapewnia wsparcie w tym procesie. Poniższa tabela zawiera typowe sytuacje i prawdopodobne reakcje, choć dokładna reakcja jest zależna od informacji uzyskanych w trakcie badania.

|Opis zdarzenia|Prawdopodobna reakcja|
|------------------------|-------------------|
|Przeciek klucza dzierżawy.|Utwórz ponownie klucz dzierżawy Zobacz sekcję [Ponowne tworzenie klucza dzierżawy](operations-microsoft-managed-tenant-key.md#re-key-your-tenant-key) w tym artykule.|
|Nieautoryzowana osoba lub złośliwe oprogramowanie uzyskało prawa do korzystania z klucza dzierżawy, ale nie nastąpił przeciek samego klucza.|Ponowne utworzenie klucza dzierżawy nie jest pomocne w tym przypadku, problem wymaga analizy przyczyny. Jeśli za uzyskanie dostępu przez nieautoryzowaną osobę odpowiada proces lub błąd oprogramowania, sytuację należy rozwiązać.|
|Odkryto lukę w zabezpieczeniach algorytmu RSA lub długości klucza albo ataki siłowe stały się wykonalne.|Firma Microsoft musi zaktualizować usługę Azure Information Protection o obsługę nowych algorytmów i dłuższych kluczy o większej odporności, a także poinstruować wszystkich klientów o konieczności odnowienia kluczy dzierżawy.|





<!--HONumber=Sep16_HO4-->


