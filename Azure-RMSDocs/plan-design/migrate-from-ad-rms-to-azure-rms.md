---
title: "Migrowanie z usługi AD RMS do usługi Azure Information Protection"
description: "Instrukcje dotyczące migracji wdrożenia usług Active Directory Rights Management (AD RMS) do usługi Azure Information Protection. Po zakończeniu migracji użytkownicy będą nadal mieć dostęp do dokumentów i wiadomości e-mail, które organizacja chroniła za pomocą usługi AD RMS. W przypadku nowo chronionej zawartości będzie używana usługa Azure Information Protection."
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 04/06/2017
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: 828cf1f7-d0e7-4edf-8525-91896dbe3172
ms.reviewer: esaggese
ms.suite: ems
ms.openlocfilehash: 89ccb599fe21c409d36b9d0ab28e274e6aedaf1e
ms.sourcegitcommit: 384461f0e3fccd73cd7eda3229b02e51099538d4
translationtype: HT
---
# <a name="migrating-from-ad-rms-to-azure-information-protection"></a>Migrowanie z usługi AD RMS do usługi Azure Information Protection

>*Dotyczy: Active Directory Rights Management Services, Azure Information Protection, Office 365*

Poniższy zestaw instrukcji dotyczy migracji wdrożenia usług Active Directory Rights Management (AD RMS) do usługi Azure Information Protection. 

Po zakończeniu migracji serwery usług AD RMS nie będą już używane, ale użytkownicy będą nadal mieć dostęp do dokumentów i wiadomości e-mail, które organizacja chroniła za pomocą usług AD RMS. W przypadku nowo chronionej zawartości będzie używana usługa Azure Rights Management (Azure RMS) dostępna w ramach usługi Azure Information Protection.

Nie masz pewności, czy ta migracja usług AD RMS jest odpowiednia dla Twojej organizacji?

-   Aby zapoznać się z wprowadzeniem do usługi Azure Information Protection, zobacz artykuł [Co to jest Azure Information Protection?](../understand-explore/what-is-information-protection.md)

-   Porównanie usług Azure Information Protection i AD RMS można znaleźć w artykule [Porównanie usług Azure Information Protection i AD RMS](../understand-explore/compare-azure-rms-ad-rms.md).

## <a name="recommended-reading-before-you-migrate-to-azure-information-protection"></a>Zalecamy przeczytanie przez migrowaniem do usługi Azure Information Protection

Mimo że nie jest to wymagane, zapoznanie się z poniższymi informacjami przed rozpoczęciem migracji może pomóc w lepszym zrozumieniu działania technologii, jeśli jest to związane z wykonywanym krokiem migracji:

- [Planowanie i wdrażanie klucza dzierżawy usługi Azure Information Protection](../plan-design/plan-implement-tenant-key.md): poznaj opcje zarządzania kluczami w swojej dzierżawie usługi Azure Information Protection, gdzie odpowiednik klucza SLC w chmurze jest zarządzany przez firmę Microsoft (ustawienie domyślne) lub przez użytkownika (konfiguracja BYOK („bring your own key”). 

- [Odnajdowanie usługi RMS](../rms-client/client-deployment-notes.md#rms-service-discovery): w tej sekcji uwag dotyczących wdrożenia klienta usługi RMS wyjaśniono, że kolejność dla potrzeb odnajdowania usługi to **rejestr**, następnie **punkt połączenia usługi**, a następnie **chmura**. Podczas procesu migracji, gdy punkt połączenia usługi jest nadal zainstalowany, należy skonfigurować klientów przy użyciu ustawień rejestru dla dzierżawy usługi Azure Information Protection, tak aby nie używali oni klastra usługi AD RMS zwróconego z punktu połączenia usługi.

- [Omówienie łącznika usługi Microsoft Rights Management](../deploy-use/deploy-rms-connector.md#overview-of-the-microsoft-rights-management-connector): w tej sekcji dokumentacji dotyczącej łącznika usług RMS objaśniono sposób łączenia serwerów lokalnych z usługą Azure Rights Management, aby chronić dokumenty i wiadomości e-mail.

Ponadto jeśli znasz sposób działania usług AD RMS, dzięki zapoznaniu się z tematem [Jak działa usługa Azure RMS? Kulisy](../understand-explore/how-does-it-work.md) możesz łatwiej zidentyfikować procesy technologiczne są takie same lub inne w wersji dla chmury.

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
        
    Uwaga: domyślnie wiele klastrów AD RMS jest migrowanych do pojedynczej dzierżawy usługi Azure Information Protection. Jeśli potrzebujesz oddzielnych dzierżaw dla usługi Azure Information Protection, musisz potraktować je jako różne migracje. Nie można zaimportować klucza z jednego klastra RMS do więcej niż jednej dzierżawy.

- **Wszystkie wymagania dotyczące uruchamiania usługi Azure Information Protection, w tym subskrypcji usługi Azure Information Protection (usługa Azure Rights Management nie jest aktywowana):**

    Zobacz artykuł [Wymagania dotyczące usługi Azure Information Protection](../get-started/requirements-azure-rms.md).

    Należy pamiętać, że jeśli masz komputery korzystające z pakietu Office 2010, musisz zainstalować klienta usługi Azure Information Protection, ponieważ ten klient zapewnia możliwość uwierzytelniania użytkowników w usługach w chmurze. W przypadku nowszych wersji pakietu Office klient usługi Azure Information Protection jest wymagany do obsługi klasyfikacji oraz etykietowania, i opcjonalny, ale zalecany, jeśli chcesz tylko chronić dane. Więcej informacji zawiera [podręcznik administratora klienta usługi Azure Information Protection](../rms-client/client-admin-guide.md).

    Mimo że do wykonania migracji z usługi AD RMS niezbędna jest subskrypcja usługi Azure Information Protection, zaleca się nie aktywować usługi Rights Management dla dzierżawy przed rozpoczęciem migracji. Proces migracji obejmuje ten krok aktywacji po wyeksportowaniu kluczy i szablonów z usługi AD RMS i zaimportowaniu ich do dzierżawy usługi Azure Information Protection. Jeśli jednak usługa Rights Management została już aktywowana, nadal można przeprowadzić migrację z usługi AD RMS, wykonując dodatkowe kroki.


- **Przygotowanie do korzystania z usługi Azure Information Protection:**

    - Synchronizacja katalogów między katalogiem lokalnym i usługą Azure Active Directory

    - Grupy z włączoną obsługą poczty w usłudze Azure Active Directory

    Zobacz artykuł [Przygotowanie do korzystania z usługi Azure Information Protection](prepare.md).

- **W przypadku użycia funkcji Zarządzanie prawami do informacji (IRM, Information Rights Management) programu Exchange Server** (np. reguł transportu i programu Outlook Web Access) lub programu SharePoint Server z usługami AD RMS:

    - Planowanie na potrzeby krótkiego okresu, gdy funkcja IRM będzie niedostępna na tych serwerach
 
    Po zakończeniu migracji można nadal korzystać z funkcji IRM na tych serwerach. Proces migracji obejmuje jednak tymczasowe wyłączenie usługi IRM, zainstalowanie i skonfigurowanie łącznika, ponowne skonfigurowanie serwerów i ponowne włączenie funkcji IRM.

    Jest to jedyne zakłócenie działania usługi podczas migracji.

- **Jeśli chcesz zarządzać własnym kluczem dzierżawy usługi Azure Information Protection przy użyciu klucza chronionego za pomocą modułu HSM**:

    - Ta opcjonalna konfiguracja wymaga usługi Azure Key Vault oraz subskrypcji platformy Azure obsługującej usługę Key Vault z kluczami chronionymi za pomocą modułu HSM. Aby uzyskać więcej informacji, zobacz [stronę z cenami usługi Azure Key Vault](https://azure.microsoft.com/en-us/pricing/details/key-vault/). 


### <a name="cryptographic-mode-considerations"></a>Zagadnienia dotyczące trybu kryptograficznego

Chociaż nie jest to wymaganiem wstępnym w przypadku migracji, zaleca się uruchomienie serwerów i klientów usług AD RMS w trybie kryptograficznym 2 przed rozpoczęciem migracji. 

Aby uzyskać więcej informacji o różnych trybach oraz instrukcje uaktualniania, zobacz temat [Tryby kryptograficzne usług AD RMS](https://technet.microsoft.com/library/hh867439(v=ws.10).aspx).

Jeśli klaster AD RMS jest w trybie kryptograficznym 1 i nie można go uaktualnić, można ponownie utworzyć klucz dzierżawy usługi Azure Information Protection po ukończeniu migracji. Po ponownym utworzeniu klucza powstaje nowy klucz dzierżawy korzystający z trybu kryptograficznego 2. Korzystanie z usługi Azure Rights Management z trybem kryptograficznym 1 jest obsługiwane tylko podczas migracji.

Aby potwierdzić tryb kryptograficzny w usłudze AD RMS:
 
- W przypadku systemów Windows Server 2012 R2 oraz Windows 2012: właściwości klastra AD RMS > karta **Ogólne**. 

- W przypadku wszystkich obsługiwanych wersji usługi AD RMS: użyj narzędzia [RMS Analyzer](https://www.microsoft.com/en-us/download/details.aspx?id=46437) i opcji **administratora usługi AD RMS**, aby wyświetlić tryb kryptograficzny w sekcji **Informacje o usłudze RMS**.


### <a name="migration-limitations"></a>Ograniczenia migracji

-   Mimo że proces migracji obsługuje migrację klucza certyfikatu licencjonowania serwera (SLC) do sprzętowego modułu zabezpieczeń (HSM) na potrzeby usługi Azure Information Protection, usługa Exchange Online nie obsługuje obecnie tej konfiguracji dla usługi Rights Management używanej przez usługę Azure Information Protection. Aby można było korzystać z pełnej funkcjonalności IRM z usługą Exchange Online po zakończeniu migracji do usługi Azure Information Protection, klucz dzierżawy usługi Azure Information Protection musi być [zarządzany przez firmę Microsoft](../plan-design/plan-implement-tenant-key.md#choose-your-tenant-key-topology-managed-by-microsoft-the-default-or-managed-by-you-byok). Można również uruchomić usługę IRM z ograniczoną funkcjonalnością w usłudze Exchange Online, gdy klucz dzierżawy usługi Azure Information Protection jest zarządzany przez użytkownika (BYOK). Aby uzyskać więcej informacji o korzystaniu z usługi Exchange Online z usługą Azure Rights Management, zobacz [Krok 8. Konfigurowanie integracji funkcji IRM na potrzeby usługi Exchange Online](migrate-from-ad-rms-phase4.md#step-8-configure-irm-integration-for-exchange-online) w tych instrukcjach migracji.

-   Jeśli masz oprogramowanie i klientów nieobsługiwanych w usłudze Rights Management używanej przez usługę Azure Information Protection, nie będzie można przy ich użyciu chronić ani korzystać z zawartości chronionej przez usługę Azure Rights Management. Zapoznaj się z informacjami w sekcjach dotyczących obsługiwanych aplikacji i klientów w artykule [Wymagania dotyczące usługi Azure Rights Management](../get-started/requirements-azure-rms.md).

-   W przypadku importowania klucza lokalnego do usługi Azure Information Protection jako zarchiwizowanego (zaufana domena publikacji nie jest ustawiana jako aktywna podczas procesu importowania) i migrowania partii użytkowników w ramach migracji stopniowej, zawartość nowo chroniona przez migrowanych użytkowników nie będzie dostępna dla użytkowników nadal korzystających z usługi AD RMS. W tym scenariuszu — jeśli to możliwe— należy zachować krótki czas migracji i migrować użytkowników w partiach logicznych w taki sposób, by użytkownicy współpracujący ze sobą byli migrowani razem.

    To ograniczenie nie ma zastosowania po ustawieniu zaufanej domeny publikacji jako aktywnej podczas procesu importowania, ponieważ wszyscy użytkownicy będą chronić zawartość przy użyciu tego samego klucza. Zalecamy korzystanie z tej konfiguracji, ponieważ umożliwia ona niezależne migrowanie wszystkich użytkowników w wybranym tempie.

-   Jeśli Twoje wdrożenie usługi AD RMS jest skonfigurowane do współpracy z partnerami zewnętrznymi (np. przy użyciu zaufanych domen użytkowników lub federacji), muszą oni migrować do usługi Azure Information Protection w tym samym czasie lub możliwie szybko po zakończeniu Twojej migracji. Aby nadal uzyskiwać dostęp do zawartości, którą organizacja wcześniej chroniła za pomocą usługi Azure Information Protection, muszą oni wprowadzić zmiany konfiguracji klienta podobne do wprowadzonych przez Ciebie i uwzględnionych w tym dokumencie.

    Z powodu możliwych wariantów konfiguracji używanych przez partnerów dokładne instrukcje dotyczące tego procesu ponownej konfiguracji wykraczają poza zakres tego dokumentu. Zapoznaj się jednak z następną sekcją, która zawiera wskazówki dotyczące planowania. Aby uzyskać dodatkową pomoc, [skontaktuj się z pomocą techniczną firmy Microsoft](../get-started/information-support.md#support-options-and-community-resources).

## <a name="migration-planning-if-you-collaborate-with-external-partners"></a>Planowanie migracji we współpracy z partnerami zewnętrznymi

W fazie planowania migracji należy uwzględnić partnerów usług AD RMS, ponieważ oni również muszą przeprowadzić migrację do usługi Azure Information Protection. Przed wykonaniem dowolnego z poniższych kroków migracji upewnij się, że partnerzy spełnili następujące warunki:

- Mają dzierżawę usługi Azure Active Directory, która obsługuje usługę Azure Rights Management.  
    
    Na przykład mają subskrypcję pakietu Office 365 E3 lub E5 albo subskrypcję pakietu Enterprise Mobility + Security lub autonomiczną subskrypcję usługi Azure Information Protection.

- Ich usługa Azure Rights Management nie została jeszcze aktywowana, ale znają swój adres URL usługi Azure Rights Management.

    Aby uzyskać te informacje, partnerzy powinni zainstalować narzędzie Azure Rights Management Tool, nawiązać połączenie z usługą ([Connect-Aadrmservice](/powershell/aadrm/vlatest/connect-aadrmservice)), a następnie wyświetlić informacje o swojej dzierżawie usługi Azure Rights Management ([Get-AadrmConfiguration](/powershell/aadrm/vlatest/get-aadrmconfiguration)).

- Udostępnili Ci adresy URL swojego klastra usług AD RMS i swój adres URL usługi Azure Rights Management, aby umożliwić Ci skonfigurowanie migrowanych klientów w celu przekierowywania żądań dotyczących zawartości chronionej przez usługi AD RMS partnerów do ich dzierżawy usługi Azure Rights Management. Instrukcje dotyczące konfigurowania przekierowywania klienta znajdują się w kroku 7.

- Zaimportowali swoje klucze główne klastra AD RMS (klucze SLC) do swojej dzierżawy, zanim rozpoczniesz migrację swoich użytkowników. Analogicznie musisz zaimportować swoje klucze główne klastra usług AD RMS, zanim partnerzy rozpoczną migrację swoich użytkowników. Instrukcje dotyczące importowania kluczy są omówione w ramach tego procesu migracji, [Krok 4. Eksportowanie danych konfiguracji z usług AD RMS i importowanie ich do usługi Azure Information Protection](migrate-from-ad-rms-phase2.md#step-4-export-configuration-data-from-ad-rms-and-import-it-to-azure-information-protection). 

## <a name="overview-of-the-steps-for-migrating-ad-rms-to-azure-information-protection"></a>Omówienie kroków migracji usługi AD RMS do usługi Azure Information Protection

Kroki migracji można podzielić na 5 fazy, które mogą realizować różni administratorzy w różnych terminach.

[**FAZA 1: PRZYGOTOWANIE MIGRACJI**](migrate-from-ad-rms-phase1.md)

- **Krok 1. Pobieranie narzędzia Azure Rights Management Administration Tool i identyfikowanie adresu URL dzierżawy**

    Proces migracji wymaga uruchomienia co najmniej jednego z poleceń cmdlet programu PowerShell z modułu usługi Azure RMS, który został zainstalowany przy użyciu narzędzia Azure Rights Management Administration Tool. Musisz także znać adres URL usługi Azure Rights Management swojej dzierżawy, który będzie niezbędny do wykonania wielu spośród kroków migracji. Wartość tę możesz ustalić przy użyciu programu PowerShell.

- **Krok 2. Przygotowanie do migracji klientów**

     Jeśli nie można przeprowadzić migracji wszystkich klientów naraz i będą oni migrowani w partiach, należy użyć kontrolek dołączania i wdrożyć skrypt przed migracją.

- **Krok 3. Przygotowanie wdrożenia programu Exchange na potrzeby migracji**

    Ten krok jest wymagany, jeśli używana jest funkcja IRM usługi Exchange Online lub lokalnego programu Exchange do ochrony wiadomości e-mail.

[**FAZA 2 — KONFIGURACJA PO STRONIE SERWERA DLA USŁUG AD RMS**](migrate-from-ad-rms-phase2.md)

- **Krok 4. Eksportowanie danych konfiguracji z usług AD RMS i importowanie ich do usługi Azure Information Protection**

    Dane konfiguracji (klucze, szablony, adresy URL) są eksportowane z usługi AD RMS do pliku XML, a następnie plik ten jest przekazywany do usługi Azure Rights Management wchodzącej w skład usługi Azure Information Protection za pomocą polecenia cmdlet Import-AadrmTpd programu PowerShell. W zależności od konfiguracji klucza usług AD RMS konieczne może być wykonanie dodatkowych kroków:

    - **Migracja klucza chronionego przez oprogramowanie do klucza chronionego przez oprogramowanie**:

        centralnie zarządzane klucze chronione hasłem w usłudze AD RMS do klucza dzierżawy usługi Azure Information Protection zarządzanego przez firmę Microsoft. Jest to najprostsza ścieżka migracji i żadne dodatkowe kroki nie są wymagane.

    - **Migracja klucza chronionego przez moduł HSM do klucza chronionego przez moduł HSM**:

        klucze przechowywane w module HSM dla usługi AD RMS do zarządzanego przez klienta klucza dzierżawy usługi Azure Information Protection (scenariusz „użyj własnego klucza” lub BYOK). Wymagane jest wykonanie dodatkowych kroków w celu przeniesienia klucza z lokalnego modułu HSM firmy Thales do usługi Azure Key Vault i autoryzowania usługi Azure Rights Management do wykorzystania tego klucza. Istniejący klucz chroniony przez moduł HSM musi podlegać ochronie przy użyciu modułu; klucze chronione przez serwer OCS nie są obsługiwane przez usługi Rights Management.

    - **Migracja klucza chronionego przez oprogramowanie do klucza chronionego przez moduł HSM**:

        centralnie zarządzane klucze chronione hasłem w usłudze AD RMS do zarządzanego przez klienta klucza dzierżawy usługi Azure Information Protection (scenariusz „użyj własnego klucza” lub BYOK). Ta migracja wymaga największej liczby kroków konfiguracji, ponieważ najpierw należy wyodrębnić klucz oprogramowania i zaimportować go do lokalnego modułu HSM, a następnie wykonać dodatkowe czynności w celu przeniesienia klucza z lokalnego modułu HSM firmy Thales do modułu HSM usługi Azure Key Vault i autoryzowania usługi Azure Rights Management do użycia magazynu kluczy, w którym przechowywany jest ten klucz.

- **Krok 5. Aktywowanie usługi Azure Rights Management**

    Jeśli to możliwe, ten krok należy wykonać po zakończeniu procesu importowania, a nie przed jego rozpoczęciem.

- **Krok 6. Konfigurowanie importowanych szablonów**

    Stan importowanych szablonów zasad praw jest określony jako zarchiwizowane. Jeśli chcesz, aby użytkownicy mogli widzieć szablony i z nich korzystać, zmień stan szablonów na opublikowane w klasycznym portalu Azure.


[**FAZA 3 — KONFIGURACJA PO STRONIE KLIENTA**](migrate-from-ad-rms-phase3.md)

- **Krok 7. Ponowne konfigurowanie klientów do korzystania z usługi Azure Information Protection**

    Aby korzystać z usługi Azure Rights Management zamiast usług AD RMS, należy ponownie skonfigurować istniejące komputery z systemem Windows. Ten krok dotyczy komputerów w organizacji oraz komputerów w organizacjach partnerów, jeśli współpracowali z Tobą podczas korzystania z usług AD RMS.

    Ponadto jeśli wdrożono [rozszerzenie urządzenia przenośnego](http://technet.microsoft.com/library/dn673574.aspx) do obsługi urządzeń przenośnych, takich jak telefony i urządzenia iPad z systemem iOS, telefony i tablety z systemem Android, telefony z systemem Windows Phone i komputery Mac, należy usunąć rekordy SRV w systemie DNS, które przekierowywały tych klientów do użycia usług AD RMS.


[**FAZA 4 — KONFIGURACJA USŁUG POMOCNICZYCH**](migrate-from-ad-rms-phase4.md)

- **Krok 8. Konfigurowanie integracji funkcji IRM na potrzeby usługi Exchange Online**

    Ten krok jest wykonywany w celu ukończenia migracji usług AD RMS dla usługi Exchange Online, aby korzystała teraz z usługi Azure Rights Management.

- **Krok 9. Konfigurowanie integracji funkcji IRM na potrzeby programów Exchange Server i SharePoint Server**

    Ten krok jest wykonywany w celu ukończenia migracji usług AD RMS dla lokalnego programu Exchange lub SharePoint, aby korzystał z usługi Azure Rights Management, co wymaga wdrożenia łącznika usługi Rights Management.


[**FAZA 5 — ZADANIA PO MIGRACJI**](migrate-from-ad-rms-phase5.md )

- **Krok 10. Anulowanie obsługi usług AD RMS**

    Po potwierdzeniu, że wszyscy klienci używają usługi Azure Rights Management i nie korzystają już z serwerów usług AD RMS, można anulować obsługę wdrożenia usług AD RMS.

- **Krok 11. Usuwanie kontrolek dołączania**

    Kontrolki dołączania skonfigurowane w fazie przygotowania nie są już potrzebne.

- **Krok 12. Ponowne tworzenie klucza dzierżawy usługi Azure Information Protection**

    Ten krok jest wymagany, jeśli przed migracją nie uruchamiano trybu kryptograficznego 2, i opcjonalny (ale zalecany) w przypadku wszystkich migracji, które pomagają w zabezpieczaniu klucza dzierżawy usługi Azure Information Protection.


## <a name="next-steps"></a>Następne kroki
Aby rozpocząć migrację, przejdź do [fazy 1 — przygotowania](migrate-from-ad-rms-phase1.md).

[!INCLUDE[Commenting house rules](../includes/houserules.md)]
