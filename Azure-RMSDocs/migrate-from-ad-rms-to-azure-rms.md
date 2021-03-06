---
title: Migrowanie z usługi AD RMS do usługi Azure Information Protection
description: Instrukcje dotyczące migracji wdrożenia usług Active Directory Rights Management (AD RMS) do usługi Azure Information Protection. Po zakończeniu migracji użytkownicy będą nadal mieć dostęp do dokumentów i wiadomości e-mail, które organizacja chroniła za pomocą usługi AD RMS. W przypadku nowo chronionej zawartości będzie używana usługa Azure Information Protection.
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 12/11/2018
ms.topic: conceptual
ms.service: information-protection
ms.assetid: 828cf1f7-d0e7-4edf-8525-91896dbe3172
ms.reviewer: esaggese
ms.suite: ems
ms.openlocfilehash: 3f7c06a6415160b5c2245dc60e94bf7d9633ef7f
ms.sourcegitcommit: 9dc6da0fb7f96b37ed8eadd43bacd1c8a1a55af8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/18/2019
ms.locfileid: "54393750"
---
# <a name="migrating-from-ad-rms-to-azure-information-protection"></a>Migrowanie z usługi AD RMS do usługi Azure Information Protection

>*Dotyczy: Usługi Active Directory Rights Management Services, [usługi Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection), [usługi Office 365](https://download.microsoft.com/download/E/C/F/ECF42E71-4EC0-48FF-AA00-577AC14D5B5C/Azure_Information_Protection_licensing_datasheet_EN-US.pdf)*

Poniższy zestaw instrukcji dotyczy migracji wdrożenia usług Active Directory Rights Management (AD RMS) do usługi Azure Information Protection. 

Po zakończeniu migracji serwery usług AD RMS nie będą już używane, ale użytkownicy będą nadal mieć dostęp do dokumentów i wiadomości e-mail, które organizacja chroniła za pomocą usług AD RMS. W przypadku nowo chronionej zawartości będzie używana usługa Azure Rights Management (Azure RMS) dostępna w ramach usługi Azure Information Protection.

Nie masz pewności, czy ta migracja usług AD RMS jest odpowiednia dla Twojej organizacji?

- Aby zapoznać się z wprowadzeniem do usługi Azure Information Protection, zobacz artykuł [Co to jest usługa Azure Information Protection?](./what-is-information-protection.md)

- Porównanie usług Azure Information Protection i AD RMS można znaleźć w artykule [Porównanie usług Azure Information Protection i AD RMS](./compare-on-premise.md).

## <a name="recommended-reading-before-you-migrate-to-azure-information-protection"></a>Zalecamy przeczytanie przez migrowaniem do usługi Azure Information Protection

Mimo że nie jest to wymagane, przeczytanie poniższej dokumentacji przed rozpoczęciem migracji może okazać się pomocne. Dzięki uzyskanej w ten sposób wiedzy można lepiej zrozumieć, jak technologia działa w procesie migracji.

- [Planowanie i wdrażanie klucza dzierżawy usługi Azure Information Protection](./plan-implement-tenant-key.md): Opis opcji zarządzania kluczami, które mają dla Twojej dzierżawy usługi Azure Information Protection, gdzie odpowiednik klucza SLC w chmurze jest zarządzany przez firmę Microsoft (ustawienie domyślne) lub przez użytkownika ("bring your own key", konfiguracja BYOK). 

- [Odnajdowanie usługi RMS](./rms-client/client-deployment-notes.md#rms-service-discovery): Ta sekcja uwagi dotyczące wdrażania klienta usługi RMS wyjaśniono, że kolejność dla potrzeb odnajdowania usługi to **rejestru**, następnie **SCP**, następnie **chmury**. Podczas procesu migracji, gdy punkt połączenia usługi jest nadal zainstalowany, należy skonfigurować klientów przy użyciu ustawień rejestru dla dzierżawy usługi Azure Information Protection, tak aby nie używali oni klastra usługi AD RMS zwróconego z punktu połączenia usługi.

- [Omówienie łącznika usługi Microsoft Rights Management](./deploy-rms-connector.md#overview-of-the-microsoft-rights-management-connector): W tej sekcji dokumentacji łącznika usługi RMS wyjaśniono, jak usługi na serwerach lokalnych mogą połączyć się z usługą Azure Rights Management do ochrony dokumentów i wiadomości e-mail.

Ponadto jeśli znasz sposób działania usług AD RMS, dzięki zapoznaniu się z tematem [Jak działa usługa Azure RMS? Kulisy](./how-does-it-work.md) możesz łatwiej zidentyfikować procesy technologiczne są takie same lub inne w wersji dla chmury.

## <a name="prerequisites-for-migrating-ad-rms-to-azure-information-protection"></a>Wymagania wstępne dotyczące migracji usługi AD RMS do usługi Azure Information Protection

Przed rozpoczęciem migracji do usługi Azure Information Protection upewnij się, że zostały spełnione następujące wymagania wstępne oraz że znasz wszystkie ograniczenia.

- **Obsługiwane wdrożenie usługi RMS:**
    
  - Następujące wersje usługi AD RMS obsługują migrację do usługi Azure Information Protection:
    
      - Windows Server 2008 R2 (x64)
        
      - Windows Server 2012 (x64)
        
      - Windows Server 2012 R2 (x64)
        
      - Windows Server 2016 (x64)
        
  - Obsługiwane są wszystkie prawidłowe topologie usług AD RMS:
    
      - Pojedynczy las, pojedynczy klaster RMS
        
      - Pojedynczy las, wiele klastrów RMS przeznaczonych tylko do licencjonowania
        
      - Wiele lasów, wiele klastrów RMS
        
    Uwaga: Domyślnie wiele klastrów AD RMS jest migrowanych do pojedynczej dzierżawy usługi Azure Information Protection. Jeśli potrzebujesz oddzielnych dzierżaw dla usługi Azure Information Protection, musisz potraktować je jako różne migracje. Nie można zaimportować klucza z jednego klastra RMS do więcej niż jednej dzierżawy.

- **Wszystkie wymagania dotyczące uruchamiania usługi Azure Information Protection, w tym subskrypcji usługi Azure Information Protection (usługa Azure Rights Management nie jest aktywowana):**

    Zobacz artykuł [Wymagania dotyczące usługi Azure Information Protection](./requirements.md).

    Należy pamiętać, że w przypadku komputerów korzystających z pakietu Office 2010, musisz zainstalować klienta usługi Azure Information Protection, ponieważ ten klient zapewnia możliwość uwierzytelniania użytkowników w usługach w chmurze. W przypadku nowszych wersji pakietu Office klient usługi Azure Information Protection jest wymagany do obsługi klasyfikacji oraz etykietowania, i opcjonalny, ale zalecany, jeśli chcesz tylko chronić dane. Więcej informacji zawiera [podręcznik administratora klienta usługi Azure Information Protection](./rms-client/client-admin-guide.md).

    Mimo że można było migrować z usług AD RMS, musisz mieć subskrypcję usługi Azure Information Protection, zaleca się, że usługi Rights Management dla dzierżawy nie została aktywowana przed rozpoczęciem migracji. Proces migracji obejmuje ten krok aktywacji po wyeksportowaniu kluczy i szablonów z usługi AD RMS i zaimportowaniu ich do dzierżawy usługi Azure Information Protection. Jednakże jeśli usługa Rights Management została już aktywowana, możesz nadal można przeprowadzić migrację z usługi AD RMS pewnych dodatkowych kroków.


- **Przygotowanie do korzystania z usługi Azure Information Protection:**

  - Synchronizacja katalogów między katalogiem lokalnym i usługą Azure Active Directory

  - Grupy z włączoną obsługą poczty w usłudze Azure Active Directory

    Zobacz artykuł [Przygotowywanie użytkowników i grup do korzystania z usługi Azure Information Protection](prepare.md).

- **Jeśli używano funkcji zarządzania prawami do informacji (IRM) programu Exchange Server** (np. reguł transportu i programu Outlook Web Access) lub programu SharePoint Server z usługami AD RMS:

  - Planowanie na potrzeby krótkiego okresu, gdy funkcja IRM będzie niedostępna na tych serwerach
 
    Po zakończeniu migracji można nadal korzystać z funkcji IRM na tych serwerach. Proces migracji obejmuje jednak tymczasowe wyłączenie usługi IRM, zainstalowanie i skonfigurowanie łącznika, ponowne skonfigurowanie serwerów i ponowne włączenie funkcji IRM.

    Jest to jedyne zakłócenie działania usługi podczas migracji.

- **Jeśli chcesz zarządzać własnym kluczem dzierżawy usługi Azure Information Protection przy użyciu klucza chronionego za pomocą modułu HSM**:

    - Ta opcjonalna konfiguracja wymaga usługi Azure Key Vault oraz subskrypcji platformy Azure obsługującej usługę Key Vault z kluczami chronionymi za pomocą modułu HSM. Aby uzyskać więcej informacji, zobacz [stronę z cenami usługi Azure Key Vault](https://azure.microsoft.com/pricing/details/key-vault/). 


### <a name="cryptographic-mode-considerations"></a>Zagadnienia dotyczące trybu kryptograficznego

Jeśli klaster AD RMS jest obecnie w trybie kryptograficznym 1, nie uaktualniaj klastra do trybu kryptograficznego 2 przed rozpoczęciem migracji. Zamiast tego należy przeprowadzić migrację za pomocą trybu kryptograficznego 1, i możesz wymienić klucz dzierżawy, po zakończeniu migracji, jako jedno z zadań po migracji.

Aby potwierdzić tryb kryptograficzny w usłudze AD RMS:
 
- W przypadku systemu Windows Server 2012 R2 i Windows 2012: Właściwości klastra usługi AD RMS > **ogólne** kartę. 

- Windows Server 2008 R2: Sprawdź, czy [długość klucza RSA zostaje zwiększona do 2048 bitów dla usługi AD RMS w systemie Windows Server 2008 R2 i Windows Server 2008](https://support.microsoft.com/help/2627272/rsa-key-length-is-increased-to-2048-bits-for-ad-rms-in-windows-server ) zainstalowano poprawkę. Jeśli nie jest dostępne, klaster AD RMS działa w trybie kryptograficznym 1.

### <a name="migration-limitations"></a>Ograniczenia migracji

- Jeśli masz oprogramowanie i klientów, które nie są obsługiwane przez usługę Rights Management, która jest używana przez usługę Azure Information Protection, nie będą mogli chronić ani korzystać z zawartości chronionej przez usługę Azure Rights Management. Zapoznaj się z informacjami w sekcjach dotyczących obsługiwanych aplikacji i klientów w artykule [Wymagania dotyczące usługi Azure Rights Management](./requirements.md).

- Jeśli Twoje wdrożenie usługi AD RMS jest skonfigurowane do współpracy z partnerami zewnętrznymi (np. przy użyciu zaufanych domen użytkowników lub federacji), muszą oni migrować do usługi Azure Information Protection w tym samym czasie lub możliwie szybko po zakończeniu Twojej migracji. Aby nadal uzyskiwać dostęp do zawartości, którą organizacja wcześniej chroniła za pomocą usługi Azure Information Protection, muszą oni wprowadzić zmiany konfiguracji klienta podobne do wprowadzonych przez Ciebie i uwzględnionych w tym dokumencie.
    
    Z powodu możliwych wariantów konfiguracji używanych przez partnerów dokładne instrukcje dotyczące tego procesu ponownej konfiguracji wykraczają poza zakres tego dokumentu. Zapoznaj się jednak z następną sekcją, która zawiera wskazówki dotyczące planowania. Aby uzyskać dodatkową pomoc, [skontaktuj się z pomocą techniczną firmy Microsoft](./information-support.md#support-options-and-community-resources).

## <a name="migration-planning-if-you-collaborate-with-external-partners"></a>Planowanie migracji we współpracy z partnerami zewnętrznymi

W fazie planowania migracji należy uwzględnić partnerów usług AD RMS, ponieważ oni również muszą przeprowadzić migrację do usługi Azure Information Protection. Przed wykonaniem dowolnego z poniższych kroków migracji upewnij się, że partnerzy spełnili następujące warunki:

- Mają dzierżawę usługi Azure Active Directory, która obsługuje usługę Azure Rights Management.  
    
    Na przykład mają subskrypcję pakietu Office 365 E3 lub E5 albo subskrypcję pakietu Enterprise Mobility + Security lub autonomiczną subskrypcję usługi Azure Information Protection.

- Ich usługa Azure Rights Management nie została jeszcze aktywowana, ale znają swój adres URL usługi Azure Rights Management.

    Aby uzyskać te informacje, partnerzy powinni zainstalować narzędzie Azure Rights Management Tool, nawiązać połączenie z usługą ([Connect-AadrmService](/powershell/aadrm/vlatest/connect-aadrmservice)), a następnie wyświetlić informacje o swojej dzierżawie usługi Azure Rights Management ([Get-AadrmConfiguration](/powershell/aadrm/vlatest/get-aadrmconfiguration)).

- Udostępnili Ci adresy URL swojego klastra usług AD RMS i swój adres URL usługi Azure Rights Management, aby umożliwić Ci skonfigurowanie migrowanych klientów w celu przekierowywania żądań dotyczących zawartości chronionej przez usługi AD RMS partnerów do ich dzierżawy usługi Azure Rights Management. Instrukcje dotyczące konfigurowania przekierowywania klienta znajdują się w kroku 7.

- Zaimportowali swoje klucze główne klastra AD RMS (klucze SLC) do swojej dzierżawy, zanim rozpoczniesz migrację swoich użytkowników. Analogicznie musisz zaimportować swoje klucze główne klastra usług AD RMS, zanim partnerzy rozpoczną migrację swoich użytkowników. Instrukcje dotyczące importowania kluczy zostały omówione w ramach tego procesu migracji: [Krok 4. Eksportowanie danych konfiguracji z usług AD RMS i importowanie ich do usługi Azure Information Protection](migrate-from-ad-rms-phase2.md#step-4-export-configuration-data-from-ad-rms-and-import-it-to-azure-information-protection). 

## <a name="overview-of-the-steps-for-migrating-ad-rms-to-azure-information-protection"></a>Omówienie kroków migracji usługi AD RMS do usługi Azure Information Protection

Kroki migracji można podzielić na pięć faz, które mogą realizować różni administratorzy w różnych terminach.

[**FAZA 1: PRZYGOTOWANIE MIGRACJI**](migrate-from-ad-rms-phase1.md)

- **Krok 1: Instalowanie modułu AADRM programu PowerShell i identyfikowanie adresu URL dzierżawy**

    Proces migracji wymaga uruchomienia co najmniej jednego z poleceń cmdlet programu PowerShell w module AADRM. Musisz znać adres URL usługi Azure Rights Management swojej dzierżawy do wykonania wielu kroków migracji, a tożsamość wartość tę możesz przy użyciu programu PowerShell.

- **Krok 2. Przygotowanie do migracji klientów**

    Jeśli nie można przeprowadzić migracji wszystkich klientów równocześnie i będą oni migrowani w partiach, należy użyć kontrolek dołączania i wdrożyć skrypt przed migracją. Jednak jeśli użytkownik będzie migrują wszystko jednocześnie, a nie przeprowadzenie migracji stopniowej, możesz pominąć ten krok.

- **Krok 3: Przygotowanie wdrożenia programu Exchange na potrzeby migracji**

    Ten krok jest wymagany, jeśli używana jest funkcja IRM usługi Exchange Online lub lokalnego programu Exchange do ochrony wiadomości e-mail. Jednak jeśli użytkownik będzie migrują wszystko jednocześnie, a nie przeprowadzenie migracji stopniowej, możesz pominąć ten krok.

[**FAZA 2: KONFIGURACJA PO STRONIE SERWERA DLA USŁUG AD RMS**](migrate-from-ad-rms-phase2.md)

- **Krok 4. Eksportowanie danych konfiguracji z usług AD RMS i importowanie ich do usługi Azure Information Protection**

    Dane konfiguracji (klucze, szablony, adresy URL) są eksportowane z usługi AD RMS do pliku XML, a następnie plik ten jest przekazywany do usługi Azure Rights Management wchodzącej w skład usługi Azure Information Protection za pomocą polecenia cmdlet Import-AadrmTpd programu PowerShell. Następnie należy zidentyfikować importowany klucz certyfikatu licencjodawcy serwera (SLC), który ma zostać użyty jako klucz dzierżawy usługi Azure Rights Management. W zależności od konfiguracji klucza usług AD RMS konieczne może być wykonanie dodatkowych kroków:

    - **Migracja klucza chronionego przez oprogramowanie do klucza chronionego przez oprogramowanie**:

        Centralnie zarządzane klucze haseł w usługach AD RMS do klucza dzierżawy zarządzanego przez firmę Microsoft Azure Information Protection. Jest to najprostsza ścieżka migracji i żadne dodatkowe kroki nie są wymagane.

    - **Migracja klucza chronionego przez moduł HSM do klucza chronionego przez moduł HSM**:

        klucze przechowywane w module HSM dla usługi AD RMS do zarządzanego przez klienta klucza dzierżawy usługi Azure Information Protection (scenariusz „użyj własnego klucza” lub BYOK). Wymagane jest wykonanie dodatkowych kroków w celu przeniesienia klucza z lokalnego modułu HSM firmy Thales do usługi Azure Key Vault i autoryzowania usługi Azure Rights Management do wykorzystania tego klucza. Istniejący klucz chroniony przez moduł HSM musi podlegać ochronie przy użyciu modułu; klucze chronione przez serwer OCS nie są obsługiwane przez usługi Rights Management.

    - **Migracja klucza chronionego przez oprogramowanie do klucza chronionego przez moduł HSM**:

        centralnie zarządzane klucze chronione hasłem w usłudze AD RMS do zarządzanego przez klienta klucza dzierżawy usługi Azure Information Protection (scenariusz „użyj własnego klucza” lub BYOK). Ta migracja wymaga największej liczby kroków konfiguracji, ponieważ najpierw należy wyodrębnić klucz oprogramowania i zaimportować go do lokalnego modułu HSM, a następnie wykonać dodatkowe czynności w celu przeniesienia klucza z lokalnego modułu HSM firmy Thales do modułu HSM usługi Azure Key Vault i autoryzowania usługi Azure Rights Management do użycia magazynu kluczy, w którym przechowywany jest ten klucz.

- **Krok 5. Aktywowanie usługi Azure Rights Management**

    Jeśli to możliwe, ten krok należy wykonać po zakończeniu procesu importowania, a nie przed jego rozpoczęciem. Jeśli usługa została aktywowana przed importem, wymagane jest wykonanie dodatkowych kroków.

- **Krok 6. Konfigurowanie importowanych szablonów**

    Stan importowanych szablonów zasad praw jest określony jako zarchiwizowane. Jeśli chcesz, aby użytkownicy mogli widzieć szablony i z nich korzystać, zmień stan szablonów w celu ich opublikowania w klasycznej witrynie Azure Portal.


[**FAZA 3: KONFIGURACJA PO STRONIE KLIENTA**](migrate-from-ad-rms-phase3.md)

- **Krok 7: Ponownie skonfiguruj komputery Windows, aby korzystać z usługi Azure Information Protection**

    Aby korzystać z usługi Azure Rights Management zamiast usług AD RMS, należy ponownie skonfigurować istniejące komputery Windows. Ten krok dotyczy komputerów w organizacji oraz na komputerach w organizacji partnera mają we współpracy z ich podczas, gdy podczas uruchamiania usług AD RMS.

[**FAZA 4: KONFIGURACJA USŁUG POMOCNICZYCH**](migrate-from-ad-rms-phase4.md)

- **Krok 8: Konfigurowanie integracji funkcji IRM dla usługi Exchange Online**

    Ten krok jest wykonywany w celu ukończenia migracji usług AD RMS dla usługi Exchange Online, aby korzystała teraz z usługi Azure Rights Management.

- **Krok 9: Konfigurowanie integracji funkcji IRM dla programu Exchange Server i SharePoint Server**

    Ten krok jest wykonywany w celu ukończenia migracji usług AD RMS dla lokalnego programu Exchange lub SharePoint, aby korzystał z usługi Azure Rights Management, co wymaga wdrożenia łącznika usługi Rights Management.


[**ETAP 5: ZADANIA PO MIGRACJI**](migrate-from-ad-rms-phase5.md )

- **Krok 10: Anulowanie aprowizacji usługi AD RMS**

    Po potwierdzeniu, że wszystkie komputery Windows używają usługi Azure Rights Management i nie korzystają już z serwerów usług AD RMS, można anulować obsługę wdrożenia usług AD RMS.

- **Krok 11: Zadania migracji klienta ukończone**

    Jeśli wdrożono [rozszerzenie dla urządzeń przenośnych](https://technet.microsoft.com/library/dn673574.aspx) do obsługi urządzeń przenośnych, takich jak telefony z systemem iOS i urządzenia Ipad, telefony z systemem Android i tabletów, Windows phone oraz komputerów Mac, należy usunąć rekordy SRV w systemie DNS, które przekierowywały tych klientów do korzystania z usług AD RMS. 
    
    Kontrolki dołączania skonfigurowane w fazie przygotowania nie są już potrzebne. Jednak nie było używane kontrolek dołączania, ponieważ wybrano opcję migrują wszystko jednocześnie, zamiast zajmować się migracją stopniowe, możesz pominąć instrukcjami, aby usunąć kontrolki dołączania.
    
    Jeśli komputery Windows korzystają z pakietu Office 2010, sprawdź, czy należy wyłączyć **zarządzania szablonem zasad praw AD RMS (automatyczne)** zadania.

- **Krok 12: Wymień klucz dzierżawy usługi Azure Information Protection**

    Ten krok jest zalecany, jeśli użytkownik nie uruchamiano trybu kryptograficznego 2 przed migracją.


## <a name="next-steps"></a>Następne kroki
Aby rozpocząć migrację, przejdź do [fazy 1 — przygotowania](migrate-from-ad-rms-phase1.md).

