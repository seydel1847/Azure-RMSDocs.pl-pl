---
title: "Migrowanie z usługi AD RMS do usługi Azure Information Protection | Azure Information Protection"
description: "Instrukcje dotyczące migracji wdrożenia usług Active Directory Rights Management (AD RMS) do usługi Azure Information Protection. Po zakończeniu migracji użytkownicy będą nadal mieć dostęp do dokumentów i wiadomości e-mail, które organizacja chroniła za pomocą usługi AD RMS. W przypadku nowo chronionej zawartości będzie używana usługa Azure Information Protection."
author: cabailey
manager: mbaldwin
ms.date: 10/27/2016
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: 828cf1f7-d0e7-4edf-8525-91896dbe3172
ms.reviewer: esaggese
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 5774a94582e6a685f84a1fc6cd9915258bf7cbe0
ms.openlocfilehash: 49c65779e5651f25082369822b60b09435c41041


---

# <a name="migrating-from-ad-rms-to-azure-information-protection"></a>Migrowanie z usługi AD RMS do usługi Azure Information Protection

>*Dotyczy: Active Directory Rights Management Services, Azure Information Protection, Office 365*

Poniższy zestaw instrukcji dotyczy migracji wdrożenia usług Active Directory Rights Management (AD RMS) do usługi Azure Information Protection. Po zakończeniu migracji użytkownicy będą nadal mieć dostęp do dokumentów i wiadomości e-mail, które organizacja chroniła za pomocą usługi AD RMS. W przypadku nowo chronionej zawartości będzie używana usługa Azure Rights Management dostępna w ramach usługi Azure Information Protection.

Nie masz pewności, czy ta migracja usług AD RMS jest odpowiednia dla Twojej organizacji?

-   Aby zapoznać się z wprowadzeniem do usługi Azure Information Protection, zobacz artykuł [Co to jest Azure Information Protection?](../understand-explore/what-is-information-protection.md)

-   Porównanie usług Azure Information Protection i AD RMS można znaleźć w artykule [Porównanie usług Azure Information Protection i AD RMS](../understand-explore/compare-azure-rms-ad-rms.md).

## <a name="recommended-reading-before-you-migrate-to-azure-information-protection"></a>Zalecamy przeczytanie przez migrowaniem do usługi Azure Information Protection

Mimo że nie jest to wymagane, zapoznanie się z poniższymi informacjami przed rozpoczęciem migracji może pomóc w lepszym zrozumieniu działania technologii, jeśli jest to związane z wykonywanym krokiem migracji:

- [Planowanie i wdrażanie klucza dzierżawy usługi Azure Information Protection](../plan-design/plan-implement-tenant-key.md): poznaj opcje zarządzania kluczami w swojej dzierżawie usługi Azure Information Protection, gdzie odpowiednik klucza SLC w chmurze jest zarządzany przez firmę Microsoft (ustawienie domyślne) lub przez użytkownika (konfiguracja BYOK („bring your own key”). 

- [Odnajdowanie usługi RMS](../rms-client/client-deployment-notes.md#rms-service-discovery): w tej sekcji uwag dotyczących wdrożenia klienta usługi RMS wyjaśniono, że kolejność dla potrzeb odnajdowania usługi to **rejestr** > **punkt połączenia usługi** > **chmura**. Podczas procesu migracji, gdy punkt połączenia usługi jest nadal zainstalowany, należy skonfigurować klientów przy użyciu ustawień rejestru dla dzierżawy usługi Azure Information Protection, tak aby nie używali oni klastra usługi AD RMS zwróconego z punktu połączenia usługi.

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
        
    - Tryb kryptograficzny 2:

        - Twoje serwery i klienci usługi AD RMS muszą działać w trybie kryptograficznym 2, zanim rozpoczniesz migrację do usługi Azure Information Protection.
        
        Mimo że bieżący klucz certyfikatu licencjodawcy serwera (SLC) musi używać trybu kryptograficznego 2, poprzednie klucze skonfigurowane dla trybu kryptograficznego 1 są obsługiwane w usłudze Azure Information Protection jako klucze zarchiwizowane. Aby uzyskać więcej informacji na temat trybów kryptograficznych i sposobu przejścia na tryb kryptograficzny 2, zobacz [Tryby kryptograficzne usług AD RMS](https://technet.microsoft.com/library/hh867439(v=ws.10).aspx).
        
    - Obsługiwane są wszystkie prawidłowe topologie usług AD RMS:
    
        - Pojedynczy las, pojedynczy klaster RMS
        
        - Pojedynczy las, wiele klastrów RMS przeznaczonych tylko do licencjonowania
        
        - Wiele lasów, wiele klastrów RMS
        
    Uwaga: domyślnie wiele klastrów RMS jest migrowanych do pojedynczej dzierżawy usługi Azure Information Protection. Jeśli potrzebujesz oddzielnych dzierżaw usługi Azure Information Protection, musisz potraktować je jako różne migracje. Klucza z jednego klastra RMS nie można zaimportować do więcej niż jednej dzierżawy usługi Azure Information Protection.

- **Wszystkie wymagania dotyczące uruchamiania usługi Azure Information Protection, w tym dzierżawy usługi Azure Information Protection (nieaktywnej):**

    Zobacz artykuł [Wymagania dotyczące usługi Azure Information Protection](../get-started/requirements-azure-rms.md).

    Mimo że do wykonania migracji z usługi AD RMS niezbędna jest dzierżawa usługi Azure Information Protection, zaleca się nie aktywować usługi Rights Management przed rozpoczęciem migracji. Proces migracji obejmuje ten krok po wyeksportowaniu kluczy i szablonów z usługi AD RMS i zaimportowaniu ich do usługi Azure Information Protection. Jeśli jednak usługa Rights Management została już aktywowana, nadal można przeprowadzić migrację z usługi AD RMS.


- **Przygotowanie do korzystania z usługi Azure Information Protection:**

    - Synchronizacja katalogów między katalogiem lokalnym i usługą Azure Active Directory

    - Grupy z włączoną obsługą poczty w usłudze Azure Active Directory

    Zobacz artykuł [Przygotowanie do korzystania z usługi Azure Information Protection](prepare.md).


- **W przypadku użycia funkcji Zarządzanie prawami do informacji (IRM, Information Rights Management) programu Exchange Server** (np. reguł transportu i programu Outlook Web Access) lub programu SharePoint Server z usługami AD RMS:

    - Planowanie na potrzeby krótkiego okresu, gdy funkcja IRM będzie niedostępna na tych serwerach
 
    Po zakończeniu migracji można nadal korzystać z funkcji IRM na tych serwerach przy użyciu usługi Azure Rights Management. Proces migracji obejmuje jednak tymczasowe wyłączenie usługi IRM, zainstalowanie i skonfigurowanie łącznika, ponowne skonfigurowanie serwerów i ponowne włączenie funkcji IRM.

    Jest to jedyne zakłócenie działania usługi podczas migracji.

- **Jeśli chcesz zarządzać własnym kluczem dzierżawy usługi Azure Information Protection przy użyciu klucza chronionego za pomocą modułu HSM**:

    - Ta opcjonalna konfiguracja wymaga usługi Azure Key Vault oraz subskrypcji platformy Azure obsługującej usługę Key Vault z kluczami chronionymi za pomocą modułu HSM. Aby uzyskać więcej informacji, zobacz [stronę z cenami usługi Azure Key Vault](https://azure.microsoft.com/en-us/pricing/details/key-vault/). 


Ograniczenia:

-   Mimo że proces migracji obsługuje migrację klucza certyfikatu licencjonowania serwera (SLC) do sprzętowego modułu zabezpieczeń (HSM) na potrzeby usługi Azure Information Protection, usługa Exchange Online nie obsługuje obecnie tej konfiguracji dla usługi Rights Management używanej przez usługę Azure Information Protection. Aby można było korzystać z pełnej funkcjonalności IRM z usługą Exchange Online po zakończeniu migracji do usługi Azure Information Protection, klucz dzierżawy usługi Azure Information Protection musi być [zarządzany przez firmę Microsoft](../plan-design/plan-implement-tenant-key.md#choose-your-tenant-key-topology-managed-by-microsoft-the-default-or-managed-by-you-byok). Można również uruchomić usługę IRM z ograniczoną funkcjonalnością w usłudze Exchange Online, gdy dzierżawa usługi Azure Information Protection jest zarządzana przez użytkownika (BYOK). Aby uzyskać więcej informacji o korzystaniu z usługi Exchange Online z usługą Azure Rights Management, zobacz [Krok 6. Konfigurowanie integracji funkcji IRM na potrzeby usługi Exchange Online](migrate-from-ad-rms-phase3.md#step-6-configure-irm-integration-for-exchange-online) w tych instrukcjach migracji.

-   Jeśli masz oprogramowanie i klientów nieobsługiwanych w usłudze Rights Management używanej przez usługę Azure Information Protection, nie będzie można przy ich użyciu chronić ani korzystać z zawartości chronionej przez usługę Azure Rights Management. Zapoznaj się z informacjami w sekcji dotyczącej obsługiwanych aplikacji i klientów w artykule [Requirements for Azure Rights Management](../get-started/requirements-azure-rms.md) (Wymagania dotyczące usługi Azure Rights Management).

-   W przypadku importowania klucza lokalnego do usługi Azure Information Protection jako zarchiwizowanego (zaufana domena publikacji nie jest ustawiana jako aktywna podczas procesu importowania) i migrowania partii użytkowników w ramach migracji stopniowej, zawartość nowo chroniona przez migrowanych użytkowników nie będzie dostępna dla użytkowników nadal korzystających z usługi AD RMS. W tym scenariuszu — jeśli to możliwe— należy zachować krótki czas migracji i migrować użytkowników w partiach logicznych w taki sposób, by użytkownicy współpracujący ze sobą byli migrowani razem.

    To ograniczenie nie ma zastosowania po ustawieniu zaufanej domeny publikacji jako aktywnej podczas procesu importowania, ponieważ wszyscy użytkownicy będą chronić zawartość przy użyciu tego samego klucza. Zalecamy korzystanie z tej konfiguracji, ponieważ umożliwia ona niezależne migrowanie wszystkich użytkowników w wybranym tempie.

-   Jeśli współpracujesz z partnerami zewnętrznymi (np. przy użyciu zaufanych domen użytkowników lub federacji), muszą oni migrować do usługi Azure Information Protection w tym samym czasie lub możliwie szybko po zakończeniu Twojej migracji. Aby nadal uzyskiwać dostęp do zawartości, którą organizacja wcześniej chroniła za pomocą usługi Azure Information Protection, muszą oni wprowadzić zmiany konfiguracji klienta podobne do wprowadzonych przez Ciebie i uwzględnionych w tym dokumencie.

    Z powodu możliwych wariantów konfiguracji używanych przez partnerów dokładne instrukcje dotyczące tego procesu ponownej konfiguracji wykraczają poza zakres tego dokumentu. Aby uzyskać pomoc, [skontaktuj się z pomocą techniczną firmy Microsoft](../get-started/information-support.md#support-options-and-community-resources).

## <a name="overview-of-the-steps-for-migrating-ad-rms-to-azure-information-protection"></a>Omówienie kroków migracji usługi AD RMS do usługi Azure Information Protection


Kroki migracji można podzielić na 4 fazy, które mogą realizować różni administratorzy w różnych terminach.

[**FAZA 1 — KONFIGURACJA PO STRONIE SERWERA DLA USŁUG AD RMS**](migrate-from-ad-rms-phase1.md)

- **Krok 1. Pobieranie narzędzia Azure Rights Management Administration Tool**

    Proces migracji wymaga uruchomienia co najmniej jednego z poleceń cmdlet środowiska Windows PowerShell z modułu usługi Azure RMS, który został zainstalowany przy użyciu narzędzia Azure Rights Management Administration Tool.

- **Krok 2. Eksportowanie danych konfiguracji z usług AD RMS i importowanie ich do usługi Azure Information Protection**

    Dane konfiguracji (klucze, szablony, adresy URL) są eksportowane z usługi AD RMS do pliku XML, a następnie plik ten jest przekazywany do usługi Azure Rights Management wchodzącej w skład usługi Azure Information Protection za pomocą polecenia cmdlet Import-AadrmTpd programu Windows PowerShell. W zależności od konfiguracji klucza usług AD RMS konieczne może być wykonanie dodatkowych kroków:

    - **Migracja klucza chronionego przez oprogramowanie do klucza chronionego przez oprogramowanie**:

        centralnie zarządzane klucze chronione hasłem w usłudze AD RMS do klucza dzierżawy usługi Azure Information Protection zarządzanego przez firmę Microsoft. Jest to najprostsza ścieżka migracji i żadne dodatkowe kroki nie są wymagane.

    - **Migracja klucza chronionego przez moduł HSM do klucza chronionego przez moduł HSM**:

        klucze przechowywane w module HSM dla usługi AD RMS do zarządzanego przez klienta klucza dzierżawy usługi Azure Information Protection (scenariusz „użyj własnego klucza” lub BYOK). Wymagane jest wykonanie dodatkowych kroków w celu przeniesienia klucza z lokalnego modułu HSM firmy Thales do usługi Azure Key Vault i autoryzowania usługi Azure Rights Management do wykorzystania tego klucza. Istniejący klucz chroniony przez moduł HSM musi podlegać ochronie przy użyciu modułu; klucze chronione przez serwer OCS nie są obsługiwane przez usługi Rights Management.

    - **Migracja klucza chronionego przez oprogramowanie do klucza chronionego przez moduł HSM**:

        centralnie zarządzane klucze chronione hasłem w usłudze AD RMS do zarządzanego przez klienta klucza dzierżawy usługi Azure Information Protection (scenariusz „użyj własnego klucza” lub BYOK). Ta migracja wymaga największej liczby kroków konfiguracji, ponieważ najpierw należy wyodrębnić klucz oprogramowania i zaimportować go do lokalnego modułu HSM, a następnie wykonać dodatkowe czynności w celu przeniesienia klucza z lokalnego modułu HSM firmy Thales do modułu HSM usługi Azure Key Vault i autoryzowania usługi Azure Rights Management do użycia magazynu kluczy, w którym przechowywany jest ten klucz.

- **Krok 3. Aktywowanie dzierżawy usługi Azure Information Protection**

    Jeśli to możliwe, ten krok należy wykonać po zakończeniu procesu importowania, a nie przed jego rozpoczęciem.

- **Krok 4. Konfigurowanie importowanych szablonów**

    Stan importowanych szablonów zasad praw jest określony jako zarchiwizowane. Jeśli chcesz, aby użytkownicy mogli widzieć szablony i z nich korzystać, zmień stan szablonów na opublikowane w klasycznym portalu Azure.


[**FAZA 2 — KONFIGURACJA PO STRONIE KLIENTA**](migrate-from-ad-rms-phase2.md)


- **Krok 5. Ponowne konfigurowanie klientów do korzystania z usługi Azure Information Protection**

    Aby korzystać z usługi Azure Information Protection zamiast usługi AD RMS, należy ponownie skonfigurować istniejące komputery z systemem Windows. Ten krok dotyczy komputerów w organizacji oraz komputerów w organizacjach partnerów, jeśli współpracowali z Tobą podczas korzystania z usług AD RMS.

    Jeśli dodatkowo wdrożono [rozszerzenie urządzenia przenośnego](http://technet.microsoft.com/library/dn673574.aspx) do obsługi urządzeń przenośnych, takich jak telefony i urządzenia iPad z systemem iOS, telefony i tablety z systemem Android, telefony z systemem Windows Phone i komputery Mac, należy usunąć rekordy SRV w systemie DNS, które przekierowywały tych klientów do użycia usług AD RMS.


[**FAZA 3 — KONFIGURACJA USŁUG POMOCNICZYCH**](migrate-from-ad-rms-phase3.md)


- **Krok 6. Konfigurowanie integracji funkcji IRM z usługą Exchange Online**

    Ten krok jest wymagany, jeśli chcesz używać usługi Exchange Online z usługą Azure Rights Management działającą w ramach usługi Azure Information Protection.


- **Krok 7. Wdrażanie łącznika usługi RMS**

    Ten krok jest wymagany, jeśli chcesz używać dowolnych z następujących usług lokalnych z usługą Azure Rights Management w celu ochrony wiadomości e-mail i dokumentów pakietu Office:

    - Exchange Server (np. reguły transportu i program Outlook Web Access)

    - SharePoint Server

    - System Windows Server z uruchomioną infrastrukturą klasyfikacji plików (FCI)


[**FAZA 4 — ZADANIA PO MIGRACJI**](migrate-from-ad-rms-phase4.md )

- **Krok 8. Likwidowanie wdrożenia usług AD RMS**

    Po potwierdzeniu, że wszyscy klienci używają usługi Azure Information Protection i nie korzystają już z serwerów usługi AD RMS, można zlikwidować wdrożenie usługi AD RMS.


- **Krok 9. Ponowne tworzenie klucza dzierżawy usługi Azure Information Protection**

    Ten krok jest opcjonalny, ale też zalecany, jeśli wybrana w kroku 2 topologia klucza dzierżawy usługi Azure Information Protection jest zarządzana przez firmę Microsoft. Ten krok nie ma zastosowania, jeśli wybrana topologia klucza dzierżawy usługi Azure Information Protection jest zarządzana przez klienta (BYOK).


## <a name="next-steps"></a>Następne kroki
Aby rozpocząć migrację, przejdź do [fazy 1 — konfiguracji po stronie serwera](migrate-from-ad-rms-phase1.md).




<!--HONumber=Oct16_HO4-->


