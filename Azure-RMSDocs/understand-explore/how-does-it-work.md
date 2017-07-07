---
title: "Jak działa usługa Azure RMS — Azure Information Protection"
description: "Szczegółowe informacje dotyczące działania usługi Azure RMS i kontrolek kryptograficznych używanych przez tę usługę oraz diagramy krok po kroku dotyczące sposobu działania tego procesu."
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 04/28/2017
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: ed6c964e-4701-4663-a816-7c48cbcaf619
ms.reviewer: esaggese
ms.suite: ems
ms.openlocfilehash: 3d53e57b8bff94c39426b37755c643c1dc9d9fde
ms.sourcegitcommit: 04eb4990e2bf0004684221592cb93df35e6acebe
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/30/2017
---
# <a name="how-does-azure-rms-work-under-the-hood"></a>Jak działa usługa Azure RMS Kulisy

>*Dotyczy: Azure Information Protection, Office 365*

Istotnym aspektem działania usługi Azure RMS jest fakt, że w ramach procesu ochrony informacji usługa Rights Management (ani firma Microsoft) nie widzi ani nie przechowuje danych użytkownika. Chronione informacje nie są wysyłane na platformę Azure ani na niej przechowywane, chyba że użytkownik jawnie zapisze je na platformie Azure lub w innej usłudze chmurowej, która magazynuje dane na tej platformie. Usługa Azure RMS sprawia po prostu, że dane w dokumencie są nieczytelne dla każdego z wyjątkiem autoryzowanych użytkowników i usług:

- Dane są szyfrowane na poziomie aplikacji i zawierają zasady, które definiują autoryzowane użycie danego dokumentu.

- Gdy chroniony dokument jest używany przez uprawnionego użytkownika lub jest przetwarzany przez autoryzowaną usługę, dane zawarte w dokumencie zostają odszyfrowane i wymuszane są prawa określone w ramach zasad.

Na poniższej ilustracji można prześledzić ogólne działanie tego procesu. Dokument zawierający tajną formułę jest chroniony i może zostać pomyślnie otwarty przez autoryzowanego użytkownika lub usługę. Dokument jest zabezpieczony przy użyciu klucza zawartości (zielony klucz na tym rysunku). Jest on unikatowy dla każdego dokumentu i znajduje się w nagłówku pliku, gdzie jest chroniony przez klucz główny dzierżawy usługi Azure Information Protection (czerwony klucz na tym rysunku). Klucz dzierżawy może być wygenerowany i zarządzany przez firmę Microsoft lub użytkownik może sam wygenerować własny klucz dzierżawy i nim zarządzać.

Gdy w trakcie procesu ochrony usługa Azure RMS wykonuje szyfrowanie i odszyfrowywanie, autoryzowanie i wymuszanie ograniczeń, tajne formuły nigdy nie są wysyłane do usługi Azure.

![Jak usługa Azure RMS chroni plik](../media/AzRMS_SecretColaFormula_final.png)

Szczegółowy opis wykonywanych działań można znaleźć w sekcji [Wskazówki dotyczące działania usługi Azure RMS: pierwsze użycie, ochrona zawartości, zużycie zawartości](#walkthrough-of-how-azure-rms-works-first-use-content-protection-content-consumption) w tym artykule.

Aby uzyskać szczegółowe informacje techniczne dotyczące algorytmów i długości kluczy używanych przez usługę Azure RMS, zobacz następną sekcję.

## <a name="cryptographic-controls-used-by-azure-rms-algorithms-and-key-lengths"></a>Formanty kryptograficzne używane przez usługę Azure RMS: algorytmy i długości kluczy
Nawet jeśli znajomość działania usługi RMS nie jest użytkownikowi potrzebna, może on zostać poproszony o informację na temat używanych formantów kryptograficznych w celu zapewnienia, że zabezpieczenia spełniają standardy branżowe.


|Formanty kryptograficzne|Użycie w usłudze Azure RMS|
|-|-|
|Algorytm: AES<br /><br />Długość klucza: 128 bitów i 256 bitów [[1]](#footnote-1)|Ochrona dokumentacji|
|Algorytm: RSA<br /><br />Długość klucza: 2048 bitów [[2]](#footnote-2)|Ochrona klucza|
|SHA-256|Podpisywanie certyfikatu|

###### <a name="footnote-1"></a>Przypis 1 

Wariant 256-bitowy jest używany przez klienta usługi Azure Information Protection i aplikację do tworzenia i przetwarzania dokumentów chronionych usługami Microsoft Rights Management na potrzeby ochrony ogólnej i ochrony natywnej, gdy plik ma rozszerzenie nazwy pliku .ppdf lub jest chronionym plikiem tekstowym lub graficznym (na przykład .ptxt lub .pjpg).

###### <a name="footnote-2"></a>Przypis 2

2048 bitów to długość klucza po aktywowaniu usługi Azure Rights Management. Długość klucza 1024 bity jest obsługiwana w następujących scenariuszach opcjonalnych:

- Podczas migracji lokalnej, jeśli klaster AD RMS jest uruchomiony w trybie kryptograficznym 1 i nie można go uaktualnić do trybu kryptograficznego 2.

- W przypadku kluczy archiwizowanych, które zostały utworzone lokalnie przed migracją, aby zawartość, która była chroniona przez usługi AD RMS, mogła być nadal otwierana po migracji do usługi Azure Rights Management.

- Jeśli klienci zdecydują się na użycie funkcji BYOK przy użyciu usługi Azure Key Vault. Zalecamy minimalny rozmiar klucza wynoszący 2048 bity, ale to ustawienie nie jest wymuszane.

### <a name="how-the-azure-rms-cryptographic-keys-are-stored-and-secured"></a>Jak są przechowywane i zabezpieczane klucze kryptograficzne usługi Azure RMS

Dla każdego dokumentu lub wiadomości e-mail, które są chronione przez usługę Azure RMS, usługa ta tworzy pojedynczy klucz AES („klucz zawartości”), który zostaje osadzony w dokumencie i będzie zawarty w kolejnych wersjach dokumentu. 

Klucz zawartości jest chroniony za pomocą klucza RSA organizacji (klucz dzierżawy usługi Azure Information Protection) jako część zasad w dokumencie, a zasady są także podpisane przez autora dokumentu. Ten klucz dzierżawy jest wspólny dla wszystkich dokumentów i wiadomości e-mail, które są chronione przez usługę Azure Rights Management w organizacji. Może go zmienić tylko administrator usługi Azure Information Protection, jeśli organizacja korzysta z klucza dzierżawy zarządzanego przez klienta w ramach rozwiązania BYOK (Bring Your Own Key). 

Ten klucz dzierżawy jest w usługach online firmy Microsoft chroniony w dokładnie kontrolowanym i ściśle monitorowanym środowisku. W przypadku stosowania klucza dzierżawy zarządzanego przez klienta (BYOK) poziom zabezpieczeń jest rozszerzony dzięki użyciu szeregu wysokiej klasy sprzętowych modułów zabezpieczeń (HSM) w każdym regionie świadczenia usługi Azure, bez możliwości wyodrębniania, eksportowania lub udostępniania kluczy niezależnie od okoliczności. Aby uzyskać więcej informacji na temat klucza dzierżawy i rozwiązania BYOK, zobacz [Planowanie i wdrażanie klucza dzierżawy usługi Azure Information Protection](../plan-design/plan-implement-tenant-key.md).

Licencje i certyfikaty wysyłane do urządzenia z systemem Windows są chronione przy użyciu klucza prywatnego na urządzeniu klienta, który jest tworzony w chwili, gdy użytkownik po raz pierwszy korzysta na urządzeniu z usługi Azure RMS. Ten klucz prywatny jest z kolei chroniony funkcją DPAPI po stronie klienta, która zabezpiecza informacje za pomocą klucza generowanego na podstawie hasła użytkownika. Na urządzeniach przenośnych klucze są używane tylko jeden raz. Ponieważ nie są przechowywane po stronie klienta, nie wymagają ochrony na urządzeniu. 


## <a name="walkthrough-of-how-azure-rms-works-first-use-content-protection-content-consumption"></a>Wskazówki dotyczące działania usługi Azure RMS: pierwsze użycie, ochrona zawartości, zużycie zawartości
Aby bardziej szczegółowo poznać działanie usługi Azure RMS, przeanalizujemy typowy przepływ pracy realizowany po [aktywowaniu usługi Azure Rights Management](../deploy-use/activate-service.md) oraz gdy użytkownik najpierw używa usługi Rights Management na komputerze z systemem Windows (proces znany także jako **inicjowanie środowiska użytkownika** lub uruchomienie), **chroni zawartość** (dokument lub wiadomość e-mail), a następnie **korzysta** z zawartości chronionej przez kogoś innego (otwiera i używa).

Po zainicjowaniu środowiska użytkownika dany użytkownik może chronić dokumenty lub korzystać z chronionych dokumentów na tym komputerze.

> [!NOTE]
> Jeśli użytkownik przejdzie do innego komputera z systemem Windows lub inny użytkownik skorzysta z tego samego komputera z systemem Windows, proces inicjowania jest powtarzany.

### <a name="initializing-the-user-environment"></a>Inicjowanie środowiska użytkownika
Zanim użytkownik będzie mógł chronić zawartość lub korzystać z zawartości chronionej na komputerze z systemem Windows, należy przygotować środowisko użytkownika na urządzeniu. To proces jednorazowy, który jest wykonywany automatycznie bez interwencji użytkownika, gdy użytkownik próbuje chronić zawartość lub korzystać z zawartości chronionej:

![Przepływ aktywacji klienta usługi RMS — krok 1, uwierzytelnianie klienta](../media/AzRMS.png)

**Działania wykonywane w kroku 1**: klient RMS na komputerze najpierw łączy się z usługą Azure Rights Management i uwierzytelnia użytkownika przy użyciu jego konta usługi Azure Active Directory.

Gdy konto użytkownika jest sfederowane przy użyciu usługi Azure Active Directory, uwierzytelnianie odbywa się automatyczne, a użytkownik nie otrzymuje monitu o podanie poświadczeń.

![Aktywacja klienta usługi RMS — krok 2, certyfikaty są pobierane do klienta](../media/AzRMS_useractivation2.png)

**Działania wykonywane w kroku 2**: po uwierzytelnieniu użytkownika połączenie jest automatycznie przekierowywane do dzierżawy usługi Azure Information Protection organizacji, która wystawia certyfikaty umożliwiające użytkownikowi uwierzytelnianie w usłudze Azure Rights Management w celu korzystania z zawartości chronionej oraz ochrony zawartości w trybie offline.

Kopia certyfikatu użytkownika jest przechowywana na platformie Azure, dzięki czemu w przypadku zmiany urządzenia przez użytkownika certyfikaty są tworzone przy użyciu tych samych kluczy.

### <a name="content-protection"></a>Ochrona zawartości
Gdy użytkownik chroni dokument, klient RMS wykonuje następujące czynności w odniesieniu do dokumentu niechronionego:

![Ochrona dokumentów za pomocą usługi RMS — krok 1, dokument jest szyfrowany](../media/AzRMS_documentprotection1.png)

**Działania wykonywane w kroku 1**: na kliencie RMS zostaje utworzony klucz losowy (klucz zawartości) użyty następnie do zaszyfrowania dokumentu za pomocą algorytmu szyfrowania symetrycznego AES.

![Ochrona dokumentów za pomocą usługi RMS — krok 2, zasady są tworzone](../media/AzRMS_documentprotection2.png)

**Działania wykonywane w kroku 2**: klient usługi RMS tworzy certyfikat, który obejmuje zasady dla dokumentu zawierające [prawa użytkowania](../deploy-use/configure-usage-rights.md) dla użytkowników lub grup i inne ograniczenia, takie jak data wygaśnięcia. Te ustawienia można zdefiniować w szablonie, który został wcześniej skonfigurowany przez administratora, lub określić w momencie, gdy zawartość jest chroniona (czasem nazywa się to „zasadą ad hoc”).   

Główny atrybut usługi Azure AD używany do identyfikowania wybranych użytkowników i grup to atrybut ProxyAddresses usługi Azure AD, w którym są przechowywane wszystkie adresy e-mail użytkownika lub grupy. Jeśli jednak konto użytkownika nie ma żadnych wartości atrybutu ProxyAddresses usługi AD, w zamian jest używana wartość UserPrincipalName użytkownika.

Następnie klient RMS wykorzystuje klucz organizacji uzyskany podczas inicjowania środowiska użytkownika do szyfrowania zasad i symetrycznego klucza zawartości. Klient usługi RMS podpisuje także zasady, korzystając z certyfikatu użytkownika uzyskanego podczas inicjowania środowiska użytkownika.

![Ochrona dokumentów za pomocą usługi RMS — krok 3, zasady są osadzane w dokumencie](../media/AzRMS_documentprotection3.png)

**Działania wykonywane w kroku 3**: na koniec zasady zostają osadzone przez klienta RMS w pliku, w którym treść dokumentu została zaszyfrowana wcześniej, co łącznie tworzy dokument chroniony.

Ten dokument może być przechowywany w dowolnym miejscu lub udostępniany przy użyciu dowolnej metody, a zasady zawsze pozostają częścią zaszyfrowanego dokumentu.

### <a name="content-consumption"></a>Użycie zawartości
Gdy użytkownik chce skorzystać z chronionego dokumentu, na kliencie RMS tworzone jest żądanie dostępu do usługi Azure Rights Management:

![Użycie dokumentu RMS — krok 1, użytkownik jest uwierzytelniany i pobiera listę praw](../media/AzRMS_documentconsumption1.png)

**Działania wykonywane w kroku 1**: uwierzytelniony użytkownik wysyła zasady zawarte w dokumencie i certyfikaty użytkownika do usługi Azure Rights Management. Usługa odszyfrowuje i ocenia zasady oraz tworzy listę praw (jeśli istnieją), jakie użytkownik ma w odniesieniu do dokumentu. W celu identyfikacji użytkownika atrybut ProxyAddresses usługi Azure AD jest używany dla konta użytkownika i grup, których użytkownik jest członkiem. Ze względu na wydajność członkostwo w grupie jest [buforowane](../plan-design/prepare.md#group-membership-caching-by-azure-rights-management). Jeśli konto użytkownika nie ma żadnych wartości atrybutu ProxyAddresses usługi Azure AD, w zamian jest używana wartość UserPrincipalName usługi Azure AD.

![Użycie dokumentu RMS — krok 2, licencja użytkowania jest zwracana do klienta](../media/AzRMS_documentconsumption2.png)

**Działania wykonywane w kroku 2**: następnie klucz zawartości AES zostaje wyodrębniony przez usługę z odszyfrowanych zasad. Ten klucz jest następnie szyfrowany przy użyciu należącego do użytkownika klucza publicznego RSA, który został otrzymany wraz z żądaniem.

Ponownie zaszyfrowany klucz zawartości zostaje następnie osadzony w zaszyfrowanej licencji użytkowania razem z listą praw użytkownika, która jest zwracana do klienta RMS.

![Użycie dokumentu RMS — krok 3, dokument jest odszyfrowywany i prawa są wymuszane](../media/AzRMS_documentconsumption3.png)

**Działania wykonywane w kroku 3**: na koniec klient RMS odbiera zaszyfrowaną licencję użytkowania i odszyfrowuje ją przy użyciu własnego klucza prywatnego użytkownika. Dzięki temu klient RMS może odszyfrować treść dokumentu, gdy jest to wymagane, i renderować ją na ekranie.

Klient odszyfrowuje również listę uprawnień i przekazuje ją do aplikacji, która wymusza te prawa w interfejsie użytkownika aplikacji.

> [!NOTE]
> Gdy użytkownicy spoza Twojej organizacji korzystają z zabezpieczonej przez Ciebie zawartości, przepływ użycia jest taki sam. Tym, co zmienia się w tym scenariuszu, jest sposób uwierzytelniania użytkownika. Aby uzyskać więcej informacji, zobacz [W jaki sposób może zostać uwierzytelniony użytkownik spoza mojej firmy, któremu udostępniam chroniony dokument?](../get-started/faqs-rms.md#when-i-share-a-protected-document-with-somebody-outside-my-company-how-does-that-user-get-authenticated)


### <a name="variations"></a>Warianty
Przedstawione wskazówki obejmują scenariusze standardowe, ale istnieją różne ich warianty:

-   **Urządzenia przenośne**: gdy urządzenia przenośne chronią pliki lub korzystają z nich przy użyciu usługi Azure Rights Management, przepływy procesu są dużo prostsze. W przypadku urządzeń przenośnych nie jest wykonywany proces inicjowania użytkownika, ponieważ każda transakcja (wykonywana w celu ochrony lub wykorzystania zawartości) jest niezależna. Podobnie jak komputery z systemem Windows, urządzenia przenośne łączą się z usługą Azure Rights Management i dokonują uwierzytelnienia. W celu ochrony zawartości urządzenia przenośne przesyłają zasady, a usługa Azure Rights Management wysyła do nich licencję publikowania i klucz symetryczny do ochrony dokumentu. Aby umożliwić użycie zawartości, po nawiązaniu połączenia z usługą Azure Rights Management i wykonaniu uwierzytelnienia urządzenia przenośne przesyłają zasady dokumentu do usługi Azure Rights Management i żądają licencji użytkowania. W odpowiedzi usługa Azure Rights Management wysyła do urządzeń przenośnych niezbędne klucze i ograniczenia. Oba procesy używają zabezpieczeń TLS do ochrony wymiany kluczy i innej komunikacji.

-   **Łącznik usługi RMS**: w przypadku korzystania z usługi Azure Rights Management z łącznikiem usługi RMS przepływy procesu pozostają takie same. Jedyna różnica polega na tym, że łącznik działa jako przekaźnik pomiędzy usługami lokalnymi (takimi jak Exchange Server i SharePoint Server) a usługą Azure Rights Management. Łącznik sam nie wykonuje żadnych operacji, takich jak inicjowanie środowiska użytkownika bądź szyfrowanie i odszyfrowywanie. Przekazuje on po prostu treść komunikacji zazwyczaj wysyłaną do serwera usług AD RMS, obsługując tłumaczenie między protokołami używanymi po każdej stronie. W tym scenariuszu można korzystać z usługi Azure Rights Management wraz z usługami lokalnymi.

-   **Ochrona ogólna (pfile)**: gdy usługa Azure Rights Management chroni plik w sposób ogólny, przepływ procesu w odniesieniu do ochrony zawartości jest zasadniczo taki sam, z tą różnicą, że to klient RMS tworzy zasady, na podstawie których są przyznawane wszystkie uprawnienia. Gdy plik jest używany, zostaje odszyfrowywany przed przekazaniem do aplikacji docelowej. Ten scenariusz umożliwia ochronę wszystkich plików, także tych bez natywnej obsługi usługi RMS.

-   **Chroniony plik PDF (ppdf)**: gdy usługa Azure Rights Management zapewnia natywną ochronę pliku pakietu Office, tworzona jest również kopia danego pliku chroniona przez usługę w taki sam sposób. Jedyna różnica polega na tym, że kopia pliku jest w formacie PPDF, który przeglądarka usługi Azure Information Protection i aplikacja RMS sharing mogą otworzyć tylko do wyświetlania. Ten scenariusz umożliwia wysyłanie chronionych załączników za pośrednictwem poczty e-mail przy zapewnieniu, że odbiorcy zawsze będą mogli je odczytać, nawet jeśli urządzenie przenośne nie jest wyposażone w aplikację z natywną obsługą chronionych plików pakietu Office.

## <a name="next-steps"></a>Następne kroki

Aby dowiedzieć się więcej na temat usługi Azure Rights Management, zapoznaj się z innymi artykułami w sekcji **Poznawanie i eksplorowanie**, na przykład [Jak aplikacje obsługują usługę Azure Rights Management](applications-support.md). Znajdziesz tu informacje na temat integracji istniejących aplikacji z usługą Azure Rights Management w celu uzyskania rozwiązania zapewniającego ochronę informacji. 

Zapoznaj się z sekcją [Usługa Azure Information Protection — terminologia](../get-started/terminology.md), aby zapoznać się z pojęciami, które możesz napotkać podczas konfigurowania i używania usługi Azure Rights Management. Przed rozpoczęciem wdrażania zobacz również [Wymagania dotyczące usługi Azure Information Protection](../get-started/requirements-azure-rms.md). Jeśli chcesz od razu rozpocząć korzystanie z usługi i osobiście wypróbować jej możliwości, skorzystaj z [Samouczka szybkiego startu dla usługi Azure Information Management](../get-started/infoprotect-quick-start-tutorial.md).

Jeśli chcesz rozpocząć wdrażanie ochrony danych w organizacji, użyj [planu wdrożenia usługi Azure Information Protection](../plan-design/deployment-roadmap.md), który zawiera informacje o kolejnych krokach procesu wdrażania i linki do praktycznych instrukcji.

> [!TIP]
> Aby uzyskać dodatkowe informacje i pomoc, skorzystaj z zasobów i linków w sekcji [Informacje i pomoc techniczna dla usługi Azure Information Protection](../get-started/information-support.md).

[!INCLUDE[Commenting house rules](../includes/houserules.md)]