---
# required metadata

title: Migrowanie z usług AD RMS do usługi Azure Rights Management — faza 1 | Azure RMS
description:
keywords:
author: cabailey
manager: mbaldwin
ms.date: 04/28/2016
ms.topic: article
ms.prod: azure
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: 5a189695-40a6-4b36-afe6-0823c94993ef

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: esaggese
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# Faza 1 migracji — konfiguracja po stronie serwera dla usług AD RMS

*Dotyczy usług: Active Directory Rights Management Services, Azure Rights Management*

Skorzystaj z poniższych informacji dotyczących fazy 1 migrowania usług AD RMS do usługi Azure Rights Management (Azure RMS). Te procedury obejmują kroki od 1 do 4 z sekcji [Migrowanie z usług AD RMS do usługi Azure Rights Management](migrate-from-ad-rms-to-azure-rms.md).


## Krok 1. Pobieranie narzędzia Azure Rights Management Administration Tool
Przejdź do Centrum pobierania Microsoft i pobierz narzędzie [Azure Rights Management Administration Tool](http://go.microsoft.com/fwlink/?LinkId=257721), które zawiera moduł administracyjny usługi Azure RMS dla programu Windows PowerShell.

Zainstaluj narzędzie. Instrukcje znajdują się w sekcji [Instalowanie programu Windows PowerShell dla usługi Azure Rights Management](../deploy-use/install-powershell.md)..

## Krok 2. Eksportowanie danych konfiguracji z usług AD RMS i importowanie ich do usługi Azure RMS
Ten krok to proces składający się z dwóch części:

1.  Eksportowanie danych konfiguracji z usług AD RMS przez eksportowanie zaufanych domen publikacji do pliku XML. Ten proces przebiega tak samo w przypadku wszystkich migracji.

2.  Importowanie danych konfiguracji do usługi Azure RMS. W zależności od bieżącej konfiguracji wdrożenia usług AD RMS i preferowanej topologii klucza dzierżawy usługi Azure RMS ten krok może składać się z różnych procesów.

### Eksportowanie danych konfiguracji z usług AD RMS
Poniższą procedurę należy wykonać we wszystkich klastrach usług AD RMS dla wszystkich zaufanych domen publikacji używanych do ochrony zawartości w Twojej organizacji. Tego kroku nie trzeba wykonywać w klastrach przeznaczonych tylko do licencjonowania.

> [!NOTE]
> Jeśli korzystasz z usługi Rights Management dla systemu Windows Server 2003, zamiast tych instrukcji wykonaj kroki procedury [eksportowania klucza prywatnego podpisanego certyfikatu licencjodawcy, zaufanej domeny użytkownika, zaufanej domeny publikacji i usługi RMS](http://technet.microsoft.com/library/jj835767%28v=ws.10%29.aspx) opisanej w artykule [Migrating from Windows RMS to AD RMS in a Different Infrastructure](http://technet.microsoft.com/library/jj835767%28v=ws.10%29.aspx) (Migracja z usług RMS systemu Windows do usług AD RMS w innej infrastrukturze).

#### Aby eksportować dane konfiguracji (informacje z zaufanej domeny publikacji)

1.  Zaloguj się do klastra AD RMS jako użytkownik z uprawnieniami administratora usług AD RMS.

2.  Z poziomu konsoli zarządzania usługami AD RMS (**Active Directory Rights Management Services**) rozwiń nazwę klastra usług AD RMS, rozwiń pozycję **Zasady zaufania**, a następnie kliknij pozycję **Zaufane domeny publikacji**..

3.  W okienku wyników wybierz zaufaną domenę publikacji, a następnie w okienku Akcje kliknij pozycję **Eksportuj zaufaną domenę publikacji**..

4.  W oknie dialogowym **Eksportowanie zaufanej domeny publikacji**:

    -   Kliknij pozycję **Zapisz jako** i zapisz dane przy użyciu wybranej ścieżki i nazwy pliku. Upewnij się, że rozszerzenie nazwy pliku to **XML** (nie jest ono dołączane automatycznie).

    -   Określ i potwierdź silne hasło. Zapamiętaj to hasło, ponieważ będzie Ci potrzebne później podczas importowania danych konfiguracji do usługi Azure RMS.

    -   Nie zaznaczaj pola wyboru, aby zapisać plik zaufanej domeny w usłudze RMS w wersji 1.0.

Po wyeksportowaniu wszystkich zaufanych domen publikacji możesz rozpocząć wykonywanie procedury importowania tych danych do sprzętowego modułu zabezpieczeń (HSM) usługi Azure RMS firmy Thales. Aby uzyskać więcej informacji, 

### Importowanie danych konfiguracji do usługi Azure RMS
W zależności od bieżącej konfiguracji wdrożenia usług AD RMS i preferowanej topologii klucza dzierżawy usługi Azure RMS ten krok może obejmować różne procedury.

W bieżącym wdrożeniu usług AD RMS będzie używana jedna z następujących konfiguracji klucza certyfikatu licencjodawcy serwera (SLC):

-   Ochrona za pomocą hasła w bazie danych usług AD RMS. To jest konfiguracja domyślna.

-   Ochrona przy użyciu sprzętowego modułu zabezpieczeń (HSM) firmy Thales.

-   Ochrona przy użyciu sprzętowego modułu zabezpieczeń (HSM) firmy innej niż Thales.

-   Ochrona za pomocą hasła przy użyciu zewnętrznego dostawcy usług kryptograficznych.

> [!NOTE]
> Aby uzyskać więcej informacji na temat korzystania ze sprzętowych modułów zabezpieczeń z usługami AD RMS, zobacz temat [Using AD RMS with Hardware Security Modules](http://technet.microsoft.com/library/jj651024.aspx) (Używanie usług AD RMS ze sprzętowymi modułami zabezpieczeń)..

Istnieją dwie opcje topologii klucza dzierżawy usługi Azure RMS: firma Microsoft zarządza kluczem dzierżawy (**zarządzany przez firmę Microsoft**) lub użytkownik zarządza kluczem dzierżawy (**zarządzany przez klienta**). Scenariusz, w którym użytkownik zarządza własnym kluczem dzierżawy usługi Azure RMS, jest czasami określany jako „użyj własnego klucza” (BYOK, Bring Your Own Key) i wymaga sprzętowego modułu zabezpieczeń (HSM) firmy Thales. Aby uzyskać więcej informacji, zobacz artykuł [Planowanie i wdrażanie klucza dzierżawy usługi Azure Rights Management](plan-implement-tenant-key.md).

> [!IMPORTANT]
> Usługa Exchange Online nie jest obecnie zgodna ze scenariuszem BYOK w usłudze Azure RMS.  Jeśli chcesz użyć scenariusza BYOK po migracji i planujesz korzystanie z usługi Exchange Online, upewnij się, że rozumiesz, w jaki sposób ta konfiguracja ogranicza funkcję IRM w usłudze Exchange Online. Zapoznaj się z informacjami w temacie [Cennik i ograniczenia dotyczące funkcji BYOK](byok-price-restrictions.md), aby określić najlepszą topologię klucza dzierżawy usługi Azure RMS dla danej migracji.

Skorzystaj z poniższej tabeli, aby określić procedurę do użycia podczas migracji. Kombinacje, które nie zostały wymienione, nie są obsługiwane.

|Bieżące wdrożenie usług AD RMS|Wybrana topologia klucza dzierżawy usługi Azure RMS|Instrukcje dotyczące migracji|
|-----------------------------|----------------------------------------|--------------------------|
|Ochrona za pomocą hasła w bazie danych usług AD RMS|Zarządzany przez firmę Microsoft|Zobacz opis procedury **Migracja klucza chronionego przez oprogramowanie do klucza chronionego przez oprogramowanie** pod tą tabelą.<br /><br />Jest to najprostsza ścieżka migracji i wymaga tylko przesłania danych konfiguracji do usługi Azure RMS.|
|Ochrona za pomocą modułu HSM przy użyciu sprzętowego modułu zabezpieczeń (HSM) nShield firmy Thales.|Zarządzany przez klienta (BYOK)|Zobacz opis procedury **Migracja klucza chronionego przez moduł HSM do klucza chronionego przez moduł HSM** pod tą tabelą.<br /><br />Przeniesienie klucza z lokalnego modułu HSM do modułów HSM usługi Azure RMS, a następnie transfer danych konfiguracji do usługi Azure RMS wymaga zestawu narzędzi BYOK i wykonania dwóch zestawów kroków.|
|Ochrona za pomocą hasła w bazie danych usług AD RMS|Zarządzany przez klienta (BYOK)|Zobacz opis procedury **Migracja klucza chronionego przez oprogramowanie do klucza chronionego przez moduł HSM** pod tą tabelą.<br /><br />Ta migracja wymaga zestawu narzędzi scenariusza BYOK oraz wykonania trzech zestawów kroków, aby najpierw wyodrębnić klucz oprogramowania i zaimportować go do lokalnego modułu HSM, następnie przenieść klucz z lokalnego modułu HSM do modułów HSM usługi Azure RMS, a na koniec przenieść dane konfiguracji do usługi Azure RMS.|
|Ochrona za pomocą modułu HSM przy użyciu sprzętowego modułu zabezpieczeń (HSM) firmy innej niż Thales|Zarządzany przez klienta (BYOK)|Skontaktuj się z dostawcą modułu HSM, aby uzyskać instrukcje dotyczące przenoszenia klucza z tego modułu HSM do sprzętowego modułu zabezpieczeń (HSM) nShield firmy Thales. Następnie postępuj zgodnie z instrukcjami dotyczącymi procedury **Migracja klucza chronionego przez moduł HSM do klucza chronionego przez moduł HSM** pod tą tabelą.|
|Ochrona za pomocą hasła przy użyciu zewnętrznego dostawcy usług kryptograficznych|Zarządzany przez klienta (BYOK)|Skontaktuj się z dostawcą usług kryptograficznych, aby uzyskać instrukcje dotyczące przenoszenia klucza do sprzętowego modułu zabezpieczeń (HSM) nShield firmy Thales. Następnie postępuj zgodnie z instrukcjami dotyczącymi procedury **Migracja klucza chronionego przez moduł HSM do klucza chronionego przez moduł HSM** pod tą tabelą.|
Przed rozpoczęciem wykonywania tych procedur upewnij się, że masz dostęp do plików XML utworzonych wcześniej podczas eksportu zaufanych domen publikacji. Mogły one zostać na przykład zapisane na dysku USB używanym do przenoszenia danych z serwera usług AD RMS do stacji roboczej połączonej z Internetem.

> [!NOTE]
> Bez względu na sposób przechowywania plików należy skorzystać z najlepszych rozwiązań dotyczących zabezpieczeń, aby je chronić, ponieważ te dane obejmują klucz prywatny.


Aby wykonać krok 2, wybierz instrukcje dotyczące ścieżki migracji: 


- [Klucz programowy do klucza programowego](migrate-softwarekey-to-softwarekey.md)
- [Klucz HSM do klucza HSM](migrate-hsmkey-to-hsmkey.md)
- [Klucz programowy do klucza HSM](migrate-softwarekey-to-hsmkey.md)


## Krok 3. Aktywowanie dzierżawy usługi RMS
Instrukcje dotyczące tego kroku zostały szczegółowo opisane w artykule [Aktywacja usługi Azure Rights Management](../deploy-use/activate-service.md).


> [!TIP]
> Jeśli masz subskrypcję usługi Office 365, możesz aktywować usługę Azure RMS w centrum administracyjnym usługi Office 365 lub w klasycznym portalu Azure. Zaleca się użycie klasycznego portalu Azure, ponieważ ten portal zarządzania będzie używany do wykonania następnego kroku.

**Co zrobić, jeśli dzierżawa usługi Azure RMS została już aktywowana?** Jeśli usługa Azure RMS została już aktywowana w Twojej organizacji, użytkownicy mogli używać usługi Azure RMS do ochrony zawartości przy użyciu automatycznie generowanego klucza dzierżawy (i domyślnych szablonów) zamiast istniejących kluczy (i szablonów) z usług AD RMS. Jest to mało prawdopodobne w przypadku komputerów, które są właściwie zarządzane w intranecie, ponieważ są one automatycznie konfigurowane na potrzeby infrastruktury usług AD RMS. Może się jednak tak zdarzyć w przypadku komputerów grupy roboczej lub komputerów, które rzadko łączą się z intranetem. Niestety zidentyfikowanie tych komputerów może być trudne, dlatego zalecamy rezygnację z aktywowania usługi przed zaimportowaniem danych konfiguracji z usług AD RMS.

Jeśli dzierżawa usługi Azure RMS została już aktywowana i można zidentyfikować te komputery, upewnij się, że na tych komputerach uruchomiono skrypt CleanUpRMS_RUN_Elevated.cmd zgodnie z opisem w kroku 5. Uruchomienie tego skryptu wymusza ponowne zainicjowanie środowiska użytkownika, tak aby pobierali oni zaktualizowany klucz dzierżawy i zaimportowane szablony.

## Krok 4. Konfigurowanie importowanych szablonów
Ze względu na to, że zaimportowane szablony mają domyślny stan **Zarchiwizowano**, należy zmienić ten stan na **Opublikowano**, aby użytkownicy mogli używać tych szablonów w usłudze Azure RMS.

Dodatkowo jeśli w przypadku szablonów w usługach AD RMS była używana grupa **KAŻDY**, zostanie ona automatycznie usunięta po zaimportowaniu szablonów do usługi Azure RMS. Należy ręcznie dodać odpowiednik grupy lub użytkowników oraz te same prawa do importowanych szablonów. Odpowiednik tej grupy dla usługi Azure RMS nosi nazwę **AllStaff-7184AB3F-CCD1-46F3-8233-3E09E9CF0E66@<nazwa_dzierżawy>.onmicrosoft.com**. Na przykład w przypadku firmy Contoso nazwa grupy może wyglądać następująco: **AllStaff-7184AB3F-CCD1-46F3-8233-3E09E9CF0E66@contoso.onmicrosoft.com**..

Jeśli nie masz pewności, czy szablony AD RMS obejmują grupę ANYONE, możesz użyć przykładowego skryptu Windows PowerShell, aby zidentyfikować te szablony. Aby uzyskać więcej informacji o korzystaniu z programu Windows PowerShell z usługami AD RMS, zobacz temat [Using Windows PowerShell to Administer AD RMS](https://technet.microsoft.com/library/ee221079%28v=ws.10%29.aspx) (Administrowanie usługami AD RMS przy użyciu programu Windows PowerShell)..

Grupę automatycznie utworzoną w organizacji można zobaczyć po skopiowaniu jednego z domyślnych szablonów zasad praw w klasycznym portalu Azure i zidentyfikowaniu pozycji **NAZWA UŻYTKOWNIKA** na stronie **PRAWA**. W klasycznym portalu nie można jednak dodać tej grupy do utworzonego ręcznie lub zaimportowanego szablonu. Zamiast tego należy użyć jednej z następujących opcji programu PowerShell z usługą Azure RMS:

-   Użyj polecenia cmdlet [New-AadrmRightsDefinition](https://msdn.microsoft.com/library/azure/dn727080.aspx), aby zdefiniować prawa i grupę „AllStaff” jako obiekt definicji praw, a następnie uruchom ponownie to polecenie dla każdej z pozostałych grup lub użytkowników, którym już przyznano prawa w oryginalnym szablonie (oprócz grupy KAŻDY). Następnie dodaj wszystkie obiekty definicji praw do szablonów przy użyciu polecenia cmdlet [Set-AadrmTemplateProperty](https://msdn.microsoft.com/en-us/library/azure/dn727076.aspx).

-   Użyj polecenia cmdlet [Export-AadrmTemplate](https://msdn.microsoft.com/library/azure/dn727078.aspx), aby wyeksportować szablon do pliku XML, który można edytować, po czym dodaj grupę i prawa „AllStaff” do istniejących grup i praw. Następnie użyj polecenia cmdlet [Import-AadrmTemplate](https://msdn.microsoft.com/library/azure/dn727077.aspx) w celu zaimportowania tej zmiany z powrotem do usługi Azure RMS.

> [!NOTE]
> Grupa „AllStaff” nie jest dokładnym odpowiednikiem grupy KAŻDY w usługach AD RMS: grupa „AllStaff” zawiera wszystkich użytkowników w dzierżawie platformy Azure, a grupa KAŻDY zawiera wszystkich uwierzytelnionych użytkowników, którzy mogą znajdować się poza organizacją.
> 
> Z powodu tej różnicy między dwiema grupami oprócz grupy „AllStaff” konieczne może być także dodanie użytkowników zewnętrznych. Zewnętrzne adresy e-mail dla grup nie są obecnie obsługiwane.

Szablony, które można importować z usług AD RMS, wyglądają i działają tak samo jak niestandardowe szablony tworzone w klasycznym portalu Azure. Aby zmienić stan importowanych szablonów na Opublikowano, aby użytkownicy mogli je widzieć i wybierać w aplikacjach lub aby wprowadzić inne zmiany szablonów, zobacz temat [Konfigurowanie szablonów niestandardowych usługi Azure Rights Management](../deploy-use/configure-custom-templates.md)..

> [!TIP]
> Aby udostępnić użytkownikom spójniejsze środowisko pracy podczas procesu migracji, nie należy wprowadzać zmian importowanych szablonów innych niż te dwie zmiany. Nie należy również publikować dwóch domyślnych szablonów dostarczanych z usługą Azure RMS ani tworzyć w tym czasie nowych szablonów. Zamiast tego należy zaczekać na zakończenie procesu migracji i likwidację serwerów usług AD RMS.

### Przykładowy skrypt programu Windows PowerShell umożliwiający zidentyfikowanie szablonów usług AD RMS obejmujących grupę KAŻDY
Ta sekcja zawiera przykładowy skrypt, który ułatwia zidentyfikowanie szablonów usług AD RMS ze zdefiniowaną grupą KAŻDY, zgodnie z opisem w poprzedniej sekcji.

**Zastrzeżenie:** ten przykładowy skrypt nie jest obsługiwany w ramach żadnych standardowych usług ani programów pomocy technicznej firmy Microsoft. Ten przykładowy skrypt jest dostarczany W STANIE TAKIM, W JAKIM SIĘ ZNAJDUJE bez jakichkolwiek gwarancji.*

```
import-module adrmsadmin 

New-PSDrive -Name MyRmsAdmin -PsProvider AdRmsAdmin -Root https://localhost -Force 

$ListofTemplates=dir MyRmsAdmin:\RightsPolicyTemplate

foreach($Template in $ListofTemplates) 
{ 
                $templateID=$Template.id

                $rights = dir MyRmsAdmin:\RightsPolicyTemplate\$Templateid\userright

     $templateName=$Template.DefaultDisplayName 

        if ($rights.usergroupname -eq "anyone")

                         {
                           $templateName = $Template.defaultdisplayname

                           write-host "Template " -NoNewline

                           write-host -NoNewline $templateName -ForegroundColor Red

                           write-host " contains rights for " -NoNewline

                           write-host ANYONE  -ForegroundColor Red
                         }
 } 
Remove-PSDrive MyRmsAdmin -force
```


## Następne kroki
Przejdź do [fazy 2 — konfiguracji po stronie klienta](migrate-from-ad-rms-phase2.md)..



<!--HONumber=Apr16_HO4-->

