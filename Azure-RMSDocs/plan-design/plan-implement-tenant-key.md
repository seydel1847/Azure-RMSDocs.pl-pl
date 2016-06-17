---
# required metadata

title: Planowanie i wdrażanie klucza dzierżawy usługi Azure Rights Management | Azure RMS
description:
keywords:
author: cabailey
manager: mbaldwin
ms.date: 05/20/2016
ms.topic: article
ms.prod: azure
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: f0d33c5f-a6a6-44a1-bdec-5be1bc8e1e14

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: esaggese
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# Planowanie i wdrażanie klucza dzierżawy usługi Azure Rights Management

*Dotyczy usług: Azure Rights Management, Office 365*

Informacje zawarte w tym artykule umożliwiają zaplanowanie użycia klucza dzierżawy usługi Rights Management (RMS) dla usługi Azure RMS oraz zarządzanie nim. Domyślne ustawienie zakłada, że to firma Microsoft zarządza kluczem dzierżawy. Ustawienie to można zmienić, aby zarządzać własnym kluczem dzierżawy w celu zachowania zgodności z konkretnymi przepisami mającymi zastosowanie w danej organizacji.  Samodzielne zarządzanie kluczem dzierżawy określa się także mianem strategii BYOK (Bring Your Own Key), czyli „Przynieś własny klucz”.

> [!NOTE]
> Klucz dzierżawy usługi RMS jest również nazywany kluczem certyfikatu licencjodawcy serwera (SLC). Usługa Azure RMS obsługuje co najmniej jeden klucz dla każdej organizacji, która ją subskrybuje. Za każdym razem, gdy na potrzeby usługi RMS używanej w obrębie organizacji jest wykorzystywany klucz (np. klucz użytkownika, klucz komputera, klucz szyfrowania dokumentu), ma miejsce szyfrowane połączenie użytego klucza z kluczem dzierżawy RMS.

**Krótki przegląd:** poniższa tabela pełni rolę przewodnika po zalecanych topologiach klucza dzierżawy. Więcej informacji można znaleźć w dodatkowej dokumentacji.

W przypadku wdrożenia usługi Azure RMS z użyciem klucza dzierżawy zarządzanego przez firmę Microsoft istnieje możliwość przejścia w późniejszym czasie na klucz zarządzany przez użytkownika (BYOK). Obecnie nie ma jednak możliwości zmiany klucza dzierżawy usługi Azure RMS z BYOK na zarządzany przez firmę Microsoft.

|Wymaganie biznesowe|Zalecana topologia klucza dzierżawy|
|------------------------|-----------------------------------|
|Skorzystaj z możliwości szybkiego wdrożenia usługi Azure RMS — proces nie wymaga użycia żadnego specjalnego sprzętu|Klucz zarządzany przez firmę Microsoft|
|Wymagana pełna funkcjonalność IRM w usłudze Exchange Online z usługą Azure RMS|Klucz zarządzany przez firmę Microsoft|
|Klucze są tworzone przez użytkownika i bezpiecznie przechowywane w sprzętowym module zabezpieczeń (HSM)|BYOK<br /><br />Obecnie wybór tej konfiguracji powoduje ograniczenie funkcjonalności IRM w usłudze Exchange Online. Więcej informacji można znaleźć w temacie [Cennik i ograniczenia dotyczące funkcji BYOK](byok-price-restrictions.md).|

## Wybierz topologię klucza dzierżawy: klucz zarządzany przez firmę Microsoft (ustawienie domyślne) lub klucz zarządzany przez użytkownika (BYOK)
Zdecyduj, która topologia klucza dzierżawy jest najodpowiedniejsza dla Twojej organizacji. Domyślnie usługa Azure RMS generuje klucz dzierżawy i zarządza większością aspektów cyklu jego życia. Jest to najprostsza opcja, która wiąże się z najmniejszą liczbą obowiązków administracyjnych użytkownika. W większości przypadków użytkownik nie musi nawet wiedzieć, że ma klucz dzierżawy. Wystarczy, że zarejestruje się w usłudze Azure RMS — resztą procesu zarządzania kluczem zajmie się firma Microsoft.

Użytkownik może także przejąć pełną kontrolę nad kluczem dzierżawy, m.in. utworzyć go oraz przechowywać lokalnie jego kopię główną. Ten model jest często określany mianem BYOK (ang. Bring Your Own Key), czyli „Przynieś własny klucz”. Po wybraniu tej opcji:

1.  Klucz dzierżawy jest generowany lokalnie przez użytkownika w sposób zgodny z zasadami dotyczącymi infrastruktury IT obowiązującymi w organizacji.

2.  Przechowywany lokalnie klucz jest bezpiecznie przesyłany z lokalnego sprzętowego modułu zabezpieczeń (HSM) do należących do firmy Microsoft i zarządzanych przez nią modułów HSM. W toku całego tego procesu klucz dzierżawy nigdy nie przekracza granic zabezpieczeń sprzętowych.

3.  W przypadku przeniesienia klucza dzierżawy do firmy Microsoft pozostaje on objęty ochroną sprzętowych modułów zabezpieczeń firmy Thales. Firma Microsoft podjęła współpracę z firmą Thales, aby zagwarantować, że klucze dzierżawy jej użytkowników nie zostaną wyodrębnione ze sprzętowych modułów zabezpieczeń firmy Microsoft.

Choć generowane niemalże w czasie rzeczywistym dzienniki z usługi Azure RMS są opcjonalne, warto z nich skorzystać, aby przekonać się, kiedy i w jaki sposób jest używany klucz dzierżawy.

> [!NOTE]
> Dodatkowym środkiem ochrony dostępnym w usłudze Azure RMS są wykorzystywane w jej ramach oddzielne środowiska Security World dla centrów danych w Ameryce Północnej, regionie Europy, Bliskiego Wschodu i Afryki (EMEA) oraz Azji. Klucz dzierżawy, którym zarządza użytkownik, jest powiązany ze środowiskiem Security World odpowiadającym regionowi, w którym jest zarejestrowana dzierżawa usługi RMS. Na przykład klucz dzierżawy europejskiego klienta nie może zostać użyty w centrach danych w Ameryce Północnej ani Azji.

## Cykl życia klucza dzierżawy
Jeśli użytkownik zdecyduje, że to firma Microsoft ma zarządzać kluczem dzierżawy, będzie ona obsługiwać większość operacji związanych z cyklem życia klucza. Jeśli jednak użytkownik zechce zarządzać kluczem dzierżawy, będzie odpowiadać za wiele operacji związanych z cyklem życia klucza oraz za niektóre dodatkowe procedury.

Na poniższych diagramach omówiono te dwie opcje i przedstawiono ich porównanie. Na pierwszym diagramie pokazano, jak niskie są koszty administracyjne ponoszone przez użytkownika w przypadku konfiguracji domyślnej, gdy to firma Microsoft zarządza kluczem dzierżawy.

![Cykl życia klucza dzierżawy usługi Azure RMS w przypadku zarządzania kluczem przez firmę Microsoft (konfiguracja domyślna)](../media/RMS_BYOK_cloud.png)

Drugi diagram przedstawia dodatkowe kroki wymagane w przypadku, gdy za zarządzanie kluczem dzierżawy odpowiada użytkownik.

![Cykl życia klucza dzierżawy usługi Azure RMS w przypadku zarządzania kluczem przez użytkownika (konfiguracja BYOK)](../media/RMS_BYOK_onprem.png)

Jeśli użytkownik zdecyduje się powierzyć firmie Microsoft zarządzanie kluczem dzierżawy, w celu wygenerowania klucza nie są wymagane żadne dalsze działania — można przejść bezpośrednio do sekcji [Następne kroki](plan-implement-tenant-key.md#next-steps).

Jeśli użytkownik zdecyduje się samodzielnie zarządzać kluczem dzierżawy, powinien przeczytać poniższe sekcje, aby uzyskać więcej informacji.

## Wdrażanie klucza dzierżawy usługi Azure Rights Management

Użyj zawartych w tej sekcji informacji oraz procedur, aby wygenerować klucz dzierżawy i samodzielnie nim zarządzać; scenariusz BYOK:


> [!IMPORTANT]
> Jeśli używasz już usługi [!INCLUDE[aad_rightsmanagement_1](../includes/aad_rightsmanagement_1_md.md)] (usługa została aktywowana) i masz użytkowników, którzy korzystają z pakietu Office 2010, przed rozpoczęciem realizacji tych procedur skontaktuj się z działem pomocy technicznej firmy Microsoft (CSS). W zależności od scenariusza i wymagań może być możliwe dalsze używanie funkcji BYOK, mogą jednak mieć zastosowanie wybrane ograniczenia lub może zajść potrzeba wykonania dodatkowych kroków.
> 
> Skontaktuj się z działem pomocy technicznej firmy Microsoft (CSS) także jeśli w Twojej organizacji obowiązują konkretne zasady dotyczące postępowania z kluczami.

### Wymagania wstępne dotyczące funkcji BYOK
Poniższa tabela zawiera listę wymagań wstępnych, które należy spełnić, aby móc korzystać z funkcji BYOK.

|Wymaganie|Więcej informacji|
|---------------|--------------------|
|Subskrypcja obejmująca usługę Azure RMS.|Więcej informacji o dostępnych subskrypcjach można znaleźć w temacie [Subskrypcje usług w chmurze, które obsługują usługę Azure RMS](../get-started/requirements-subscriptions.md).|
|Nie należy używać usługi RMS dla użytkowników indywidualnych ani usługi Exchange Online. Użytkownicy, którzy zdecydują się korzystać z usługi Exchange Online, muszą zrozumieć i zaakceptować ograniczenia związane z korzystaniem z funkcji BYOK w tej konfiguracji.|Więcej informacji na temat ogólnych i bieżących ograniczeń dotyczących korzystania z funkcji BYOK znajduje się w sekcji [Cennik i ograniczenia dotyczące funkcji BYOK](byok-price-restrictions.md).<br /><br />**Ważne**: funkcja BYOK nie jest obecnie zgodna z usługą Exchange Online.|
|Sprzętowe moduły zabezpieczeń, karty inteligentne i oprogramowanie firmy Thales.<br /><br />**Uwaga**: do przeprowadzenia migracji z usługi AD RMS do usługi Azure RMS przy użyciu klucza oprogramowania i klucza sprzętowego wymagane są sterowniki firmy Thales w wersji 11.62 lub nowszej.|Użytkownik musi mieć dostęp do sprzętowego modułu zabezpieczeń firmy Thales oraz podstawową wiedzę na temat działania sprzętowych modułów zabezpieczeń firmy Thales. Lista zgodnych modeli oraz informacje na temat możliwości zakupu sprzętowego modułu zabezpieczeń znajdują się w sekcji [Sprzętowy moduł zabezpieczeń firmy Thales](http://www.thales-esecurity.com/msrms/buy).|
|Aby przekazać klucz dzierżawy przez Internet, a nie fizycznie (przebywając w Redmond w Stanach Zjednoczonych), należy spełnić 3 wymagania:<br /><br />1. Stacja robocza w trybie offline o architekturze x64 z systemem operacyjnym Windows w wersji Windows 7 lub nowszej oraz oprogramowaniem Thales nShield w wersji 11.62 lub nowszej.<br /><br />W przypadku stacji roboczych z systemem Windows 7 wymagana jest [instalacja oprogramowania Microsoft .NET Framework 4.5](http://go.microsoft.com/fwlink/?LinkId=225702).<br /><br />2. Podłączona do Internetu stacja robocza z systemem operacyjnym Windows w wersji Windows 7 lub nowszej.<br /><br />3. Dysk USB lub inne przenośne urządzenie pamięci masowej z co najmniej 16 MB wolnego miejsca.|Spełnienie tych wymagań wstępnych nie jest konieczne, jeśli użytkownik zamierza udać się do Redmond i przekazać klucz dzierżawy osobiście.<br /><br />Ze względów bezpieczeństwa odradza się podłączanie pierwszej stacji roboczej do sieci. Podłączenia takiego nie uniemożliwiają jednak ograniczenia natury programistycznej.<br /><br />Uwaga: W treści kolejnych instrukcji pierwsza stacja robocza jest określana mianem **odłączonej stacji roboczej**.<br /><br />Ponadto jeśli klucz dzierżawy jest przeznaczony dla środowiska produkcyjnego, zaleca się użycie drugiej, oddzielnej stacji roboczej do pobrania zestawu narzędzi i przesłania klucza dzierżawy. Do celów testowych można jednak użyć pierwszej stacji roboczej.<br /><br />Uwaga: W treści kolejnych instrukcji druga stacja robocza jest określana mianem **stacji roboczej podłączonej do Internetu**.|

Procedury generowania i użytkowania klucza dzierżawy różnią się w zależności od tego, czy użytkownik zamierza wykonać je przez Internet, czy też osobiście:

-   **Przez Internet:** procedura wymaga wykonania wybranych kroków dodatkowych konfiguracji, takich jak pobranie i użycie zestawu narzędzi oraz użycie poleceń cmdlet programu Windows PowerShell. Nie trzeba jednak znajdować się fizycznie w obiekcie firmy Microsoft, aby móc przekazać swój klucz dzierżawy. W celu zapewnienia bezpieczeństwa wykorzystywane są następujące metody:

    -   Użytkownik generuje klucz dzierżawy z poziomu stacji roboczej w trybie offline, dzięki czemu obszar narażony na ataki zostaje zredukowany.

    -   Klucz dzierżawy jest szyfrowany za pomocą klucza wymiany klucza (KEK), który pozostaje zaszyfrowany do czasu, gdy zostanie przesłany do sprzętowych modułów zabezpieczeń usługi Azure RMS. Wyłącznie zaszyfrowana wersja klucza dzierżawy opuszcza pierwotną stację roboczą.

    -   Narzędzie ustawia w obrębie klucza dzierżawy właściwości, które łączą klucz dzierżawy ze środowiskiem zabezpieczeń Security World usługi Azure RMS. Gdy sprzętowe moduły zabezpieczeń usługi Azure RMS odbiorą i odszyfrują klucz dzierżawy, klucz może zostać użyty tylko przez nie. Nie można wyeksportować klucza dzierżawy. To powiązanie jest wymuszone przez sprzętowy moduł zabezpieczeń firmy Thales.

    -   Klucz wymiany klucza (KEK), który jest używany do szyfrowania klucza dzierżawy, jest generowany wewnątrz sprzętowego modułu zabezpieczeń usługi RMS Azure i nie można go wyeksportować. Sprzętowe moduły zabezpieczeń wymagają, aby poza ich obrębem nie był dostępny żaden jasny obraz klucza wymiany klucza (KEK). Ponadto zestaw narzędzi zawiera zaświadczenie od firmy Thales potwierdzające, że klucza KEK nie można wyeksportować i że został on wygenerowany wewnątrz oryginalnego sprzętowego modułu zabezpieczeń wyprodukowanego przez firmę Thales.

    -   Zestaw narzędzi zawiera także zaświadczenie od firmy Thales potwierdzające, że środowisko zabezpieczeń Security World usługi Azure RMS zostało także wygenerowane w oryginalnym sprzętowym module zabezpieczeń wyprodukowanym przez firmę Thales. Stanowi ono dowód na to, że firma Microsoft korzysta z oryginalnego sprzętu.

    -   Firma Microsoft używa oddzielnych kluczy KEK oraz oddzielnych środowisk zabezpieczeń Security World w każdym regionie geograficznym, co daje gwarancję, że klucz dzierżawy może być używany tylko w centrach danych w regionie, w którym został zaszyfrowany. Na przykład klucz dzierżawy europejskiego klienta nie może zostać użyty w centrach danych w Ameryce Północnej ani Azji.

    > [!NOTE]
    > Klucz dzierżawy może być bezpiecznie przesyłany za pośrednictwem niezaufanych komputerów i sieci, ponieważ jest on zaszyfrowany i zabezpieczony z użyciem uprawnień z poziomu kontroli dostępu, dzięki czemu można używać go tylko w obrębie sprzętowych modułów zabezpieczeń użytkownika oraz sprzętowych modułów zabezpieczeń firmy Microsoft dla usługi Azure RMS. Skryptów należących do zestawu narzędzi można użyć w celu weryfikacji środków bezpieczeństwa oraz uzyskania bardziej szczegółowych informacji na temat sposobu wykonywania procedury po stronie firmy Thales: [Zarządzanie kluczami sprzętowymi w chmurze RMS](https://www.thales-esecurity.com/knowledge-base/white-papers/hardware-key-management-in-the-rms-cloud).

-   **Osobiście:** Takie rozwiązanie wymaga skontaktowania się z działem pomocy technicznej (CSS) firmy Microsoft w celu zaplanowania spotkania, podczas którego nastąpi przekazanie klucza dla usługi Azure RMS. W takim scenariuszu użytkownik musi przyjechać do biura firmy Microsoft w Redmond w stanie Waszyngton (Stany Zjednoczone) w celu przekazania klucza dzierżawy środowiska zabezpieczeń Security World usługi Azure RMS.

Aby uzyskać dokładne instrukcje, należy wybrać metodę wygenerowania i przekazania klucza dzierżawy: 

- [Przez Internet](generate-tenant-key-internet.md)
- [Osobiście](generate-tenant-key-in-person.md)


## Następne kroki

Gdy udało się już zaplanować używanie klucza dzierżawy i w razie potrzeby wygenerować go, wykonaj następujące czynności:

1.  Rozpocznij korzystanie z klucza dzierżawy:

    -   Jeśli jeszcze nie zostało to zrobione, należy teraz aktywować usługę Rights Management, aby organizacja mogła zacząć korzystać z usługi RMS. Użytkownicy natychmiast otrzymują możliwość korzystania ze swojego klucza dzierżawy (zarządzanego przez firmę Microsoft lub przez użytkownika).

        Aby uzyskać więcej informacji o aktywacji, zobacz [Aktywacja usługi Azure Rights Management](../deploy-use/activate-service.md).

    -   Jeśli usługa Rights Management została już aktywowana, a następnie podjęto decyzję o samodzielnym zarządzaniu kluczem dzierżawy, użytkownicy stopniowo przechodzą ze starego klucza dzierżawy na nowy. Okres przejściowy może trwać do kilku tygodni. Dokumenty i pliki, które były chronione przy użyciu starego klucza dzierżawy, pozostają dostępne dla użytkowników upoważnionych do dostępu do nich.

2.  Rozważ włączenie funkcji rejestrowania użycia, która tworzy dzienniki uwzględniające każdą czynność wykonywaną w ramach usługi RMS.

    Użytkownik samodzielnie zarządzający kluczem dzierżawy może uzyskać dostęp do rejestrów uwzględniających informacje o użyciu jego własnego klucza dzierżawy. Poniżej znajduje się przykładowy plik dziennika w programie Excel; typy żądań **Decrypt** i **SignDigest** pokazują, że klucz dzierżawy jest w użyciu.

    ![Plik dziennika wyświetlony w programie Excel, pokazujący, że klucz dzierżawy jest w użyciu](../media/RMS_Logging.gif)

    Więcej informacji na temat rejestrowania użycia znajduje się w sekcji [Rejestrowanie i analizowanie danych użycia usługi Azure Rights Management](../deploy-use/log-analyze-usage.md).

3.  Wykonuj czynności związane z obsługą klucza dzierżawy.

    Aby uzyskać więcej informacji, zobacz [Operacje związane z kluczem dzierżawy usługi Azure Rights Management](../deploy-use/operations-tenant-key.md).



<!--HONumber=May16_HO3-->


