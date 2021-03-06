---
title: Migrowanie z usługi AD RMS do usługi Azure Information Protection — faza 2
description: Faza 2 migracji z usługi AD RMS do usługi Azure Information Protection obejmująca kroki od 4 do 6 z sekcji Migrowanie z usługi AD RMS do usługi Azure Information Protection.
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 11/14/2018
ms.topic: conceptual
ms.service: information-protection
ms.assetid: 5a189695-40a6-4b36-afe6-0823c94993ef
ms.reviewer: esaggese
ms.suite: ems
ms.openlocfilehash: 5fb3e3ab5d32bf5e590bec5b0a1380bf13a7d066
ms.sourcegitcommit: 9dc6da0fb7f96b37ed8eadd43bacd1c8a1a55af8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/18/2019
ms.locfileid: "54394202"
---
# <a name="migration-phase-2---server-side-configuration-for-ad-rms"></a>Faza 2 migracji — konfiguracja po stronie serwera dla usług AD RMS

>*Dotyczy: Usługi Active Directory Rights Management Services, [usługi Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection), [usługi Office 365](https://download.microsoft.com/download/E/C/F/ECF42E71-4EC0-48FF-AA00-577AC14D5B5C/Azure_Information_Protection_licensing_datasheet_EN-US.pdf)*

Skorzystaj z poniższych informacji dotyczących fazy 2 migrowania z usługi AD RMS do usługi Azure Information Protection. Te procedury obejmują kroki od 4 do 6 z sekcji [Migrowanie z usługi AD RMS do usługi Azure Information Protection](migrate-from-ad-rms-to-azure-rms.md).


## <a name="step-4-export-configuration-data-from-ad-rms-and-import-it-to-azure-information-protection"></a>Krok 4. Eksportowanie danych konfiguracji z usługi AD RMS i importowanie ich do usługi Azure Information Protection
Ten krok to proces składający się z dwóch części:

1. Eksportowanie danych konfiguracji z usług AD RMS przez eksportowanie zaufanych domen publikacji do pliku XML. Ten proces przebiega tak samo w przypadku wszystkich migracji.

2. Importowanie danych konfiguracji do usługi Azure Information Protection. W zależności od bieżącej konfiguracji wdrożenia usług AD RMS i preferowanej topologii klucza dzierżawy usługi Azure RMS ten krok może składać się z różnych procesów.

### <a name="export-the-configuration-data-from-ad-rms"></a>Eksportowanie danych konfiguracji z usług AD RMS

Poniższą procedurę należy wykonać we wszystkich klastrach usług AD RMS dla wszystkich zaufanych domen publikacji używanych do ochrony zawartości w Twojej organizacji. Tej procedury nie trzeba wykonywać w klastrach przeznaczonych tylko do licencjonowania.

#### <a name="to-export-the-configuration-data-trusted-publishing-domain-information"></a>Aby eksportować dane konfiguracji (informacje z zaufanej domeny publikacji)

1. Zaloguj się do klastra AD RMS jako użytkownik z uprawnieniami administratora usług AD RMS.

2. Z poziomu konsoli zarządzania usługami AD RMS (**Active Directory Rights Management**) rozwiń nazwę klastra usług AD RMS, rozwiń pozycję **Zasady zaufania**, a następnie kliknij pozycję **Zaufane domeny publikacji**.

3. W okienku wyników wybierz zaufaną domenę publikacji, a następnie w okienku Akcje kliknij pozycję **Eksportuj zaufaną domenę publikacji**.

4. W oknie dialogowym **Eksportowanie zaufanej domeny publikacji**:

    - Kliknij pozycję **Zapisz jako** i zapisz dane przy użyciu wybranej ścieżki i nazwy pliku. Upewnij się, że rozszerzenie nazwy pliku to **XML** (nie jest ono dołączane automatycznie).

    - Określ i potwierdź silne hasło. Zapamiętaj to hasło, ponieważ będzie Ci potrzebne później podczas importowania danych konfiguracji do usługi Azure Information Protection.

    - Nie zaznaczaj pola wyboru, aby zapisać plik zaufanej domeny w usłudze RMS w wersji 1.0.

Po wyeksportowaniu wszystkich zaufanych domen publikacji możesz rozpocząć wykonywanie procedury importowania tych danych do usługi Azure Information Protection.

Należy pamiętać, że zaufane domeny publikacji obejmują klucze certyfikatu licencjodawcy serwera (SLC) do odszyfrowywania chronionych wcześniej plików. Dlatego ważne jest, aby wyeksportować (a później zaimportować na platformę Azure) wszystkie zaufane domeny publikacji, a nie tylko tę, która jest obecnie aktywna.

Na przykład po uaktualnieniu serwerów usług AD RMS z trybu kryptograficznego 1 do trybu kryptograficznego 2 użytkownik będzie miał wiele zaufanych domen publikacji. Jeśli zaufana domena publikacji zawierająca zarchiwizowany klucz, który używał trybu kryptograficznego 1, nie zostanie wyeksportowana, a następnie zaimportowana pod koniec procesu migracji, użytkownicy nie będą mogli otworzyć zawartości chronionej za pomocą klucza trybu kryptograficznego 1.


### <a name="import-the-configuration-data-to-azure-information-protection"></a>Importowanie danych konfiguracji do usługi Azure Information Protection
W zależności od bieżącej konfiguracji wdrożenia usługi AD RMS i preferowanej topologii klucza dzierżawy usługi Azure Information Protection ten krok może obejmować różne procedury.

W bieżącym wdrożeniu usług AD RMS jest używana jedna z następujących konfiguracji klucza certyfikatu licencjodawcy serwera (SLC):

- Ochrona za pomocą hasła w bazie danych usług AD RMS. To jest konfiguracja domyślna.

- Ochrona przy użyciu sprzętowego modułu zabezpieczeń (HSM) firmy Thales.

- Ochrona przy użyciu sprzętowego modułu zabezpieczeń (HSM) firmy innej niż Thales.

- Ochrona za pomocą hasła przy użyciu zewnętrznego dostawcy usług kryptograficznych.

> [!NOTE]
> Aby uzyskać więcej informacji na temat korzystania ze sprzętowych modułów zabezpieczeń z usługami AD RMS, zobacz temat [Using AD RMS with Hardware Security Modules](https://technet.microsoft.com/library/jj651024.aspx) (Używanie usług AD RMS ze sprzętowymi modułami zabezpieczeń).

Dostępne są następujące dwie opcje topologii klucza dzierżawy usługi Azure Information Protection: Firma Microsoft zarządza kluczem dzierżawy (**zarządzanych przez firmę Microsoft**) lub użytkownik zarządza kluczem dzierżawy (**zarządzanych przez klienta**) w usłudze Azure Key Vault. Jeśli zarządzasz własnym kluczem dzierżawy usługi Azure Information Protection, jest czasami określany jako "bring your own key" (BYOK). Aby uzyskać więcej informacji, zobacz artykuł [Planowanie i wdrażanie klucza dzierżawy usługi Azure Information Protection](plan-implement-tenant-key.md).

Skorzystaj z poniższej tabeli, aby określić procedurę do użycia podczas migracji. 

|Bieżące wdrożenie usług AD RMS|Wybrana topologia klucza dzierżawy usługi Azure Information Protection|Instrukcje dotyczące migracji|
|-----------------------------|----------------------------------------|--------------------------|
|Ochrona za pomocą hasła w bazie danych usług AD RMS|Zarządzany przez firmę Microsoft|Zobacz opis procedury **Migracja klucza chronionego przez oprogramowanie do klucza chronionego przez oprogramowanie** pod tą tabelą.<br /><br />Jest to najprostsza ścieżka migracji i wymaga tylko przesłania danych konfiguracji do usługi Azure Information Protection.|
|Ochrona za pomocą modułu HSM przy użyciu sprzętowego modułu zabezpieczeń (HSM) nShield firmy Thales. |Zarządzany przez klienta (BYOK)|Zobacz opis procedury **Migracja klucza chronionego przez moduł HSM do klucza chronionego przez moduł HSM** pod tą tabelą.<br /><br />Ta migracja wymaga zestawu narzędzi rozwiązania BYOK usługi Azure Key Vault oraz wykonania trzech zestawów kroków, aby najpierw przenieść klucz z lokalnego modułu HSM do modułów HSM usługi Azure Key Vault, następnie autoryzować usługę Azure Rights Management działającą w ramach usługi Azure Information Protection do użycia tego klucza dzierżawy, a na koniec przenieść dane konfiguracji do usługi Azure Information Protection.|
|Ochrona za pomocą hasła w bazie danych usług AD RMS|Zarządzany przez klienta (BYOK)|Zobacz opis procedury **Migracja klucza chronionego przez oprogramowanie do klucza chronionego przez moduł HSM** pod tą tabelą.<br /><br />Ta migracja wymaga zestawu narzędzi rozwiązania BYOK usługi Azure Key Vault oraz wykonania czterech zestawów kroków, aby najpierw wyodrębnić klucz oprogramowania i zaimportować go do lokalnego modułu HSM, następnie przenieść klucz z lokalnego modułu HSM do modułów HSM usługi Azure Information Protection, następnie przenieść dane usługi Key Vault do usługi Azure Information Protection, a na koniec przenieść dane konfiguracji do usługi Azure Information Protection.|
|Ochrona za pomocą modułu HSM przy użyciu sprzętowego modułu zabezpieczeń (HSM) firmy innej niż Thales |Zarządzany przez klienta (BYOK)|Skontaktuj się z dostawcą modułu HSM, aby uzyskać instrukcje dotyczące przenoszenia klucza z tego modułu HSM do sprzętowego modułu zabezpieczeń (HSM) Thales nShield. Następnie postępuj zgodnie z instrukcjami dotyczącymi procedury **Migracja klucza chronionego przez moduł HSM do klucza chronionego przez moduł HSM** pod tą tabelą.|
|Ochrona za pomocą hasła przy użyciu zewnętrznego dostawcy usług kryptograficznych|Zarządzany przez klienta (BYOK)|Skontaktuj się z dostawcą usług kryptograficznych, aby uzyskać instrukcje dotyczące przenoszenia klucza do sprzętowego modułu zabezpieczeń (HSM) Thales nShield. Następnie postępuj zgodnie z instrukcjami dotyczącymi procedury **Migracja klucza chronionego przez moduł HSM do klucza chronionego przez moduł HSM** pod tą tabelą.|

Jeśli istnieje klucz chroniony przez moduł HSM, którego nie można wyeksportować, nadal możliwe jest przeprowadzenie migracji do usługi Azure Information Protection, konfigurując klaster usług AD RMS pod kątem trybu tylko do odczytu. W tym trybie wciąż można otwierać wcześniej chronioną zawartość, ale nowo chroniona zawartość używa nowego klucza dzierżawy, który jest zarządzany przez użytkownika (rozwiązanie BYOK) lub przez firmę Microsoft. Aby uzyskać więcej informacji, zobacz [An update is available for Office to support migrations from AD RMS to Azure RMS](https://support.microsoft.com/help/4023955/an-update-is-available-for-office-to-support-migrations-from-ad-rms-to) (Dostępna jest aktualizacja dla pakietu Office na potrzeby obsługi migracji z usług AD RMS do usługi Azure RMS).

Przed rozpoczęciem wykonywania tych procedur dotyczących migracji klucza upewnij się, że masz dostęp do plików XML utworzonych wcześniej podczas eksportu zaufanych domen publikacji. Mogły one zostać na przykład zapisane na dysku USB używanym do przenoszenia danych z serwera usług AD RMS do stacji roboczej połączonej z Internetem.

> [!NOTE]
> Bez względu na sposób przechowywania plików należy skorzystać z najlepszych rozwiązań dotyczących zabezpieczeń, aby je chronić, ponieważ te dane obejmują klucz prywatny.

Aby wykonać krok 4, wybierz instrukcje dotyczące ścieżki migracji: 

- [Klucz chroniony przez oprogramowanie do klucza chronionego przez oprogramowanie](migrate-softwarekey-to-softwarekey.md)
- [Klucz chroniony przez moduł HSM do klucza chronionego przez moduł HSM](migrate-hsmkey-to-hsmkey.md)
- [Klucz chroniony przez moduł HSM do klucza chronionego przez oprogramowanie](migrate-softwarekey-to-hsmkey.md)

## <a name="step-5-activate-the-azure-rights-management-service"></a>Krok 5. Aktywowanie usługi Azure Rights Management

Otwórz sesję programu PowerShell i uruchom następujące polecenia:

1. Połącz się z usługą Azure Rights Management i po wyświetleniu monitu podaj swoje poświadczenia administratora globalnego:
    
        Connect-Aadrmservice

2. Aktywuj usługę Azure Rights Management:
    
        Enable-Aadrm

**Co zrobić, jeśli dzierżawa usługi Azure Information Protection została już aktywowana?** Jeśli usługa Azure Rights Management została już aktywowana dla Twojej organizacji, a następnie utworzono szablony niestandardowe, które mają zostać użyte po migracji, należy wyeksportować i zaimportować te szablony. Ta procedura została opisana w następnym kroku. 

## <a name="step-6-configure-imported-templates"></a>Krok 6. Konfigurowanie importowanych szablonów

Ze względu na to, że zaimportowane szablony mają domyślny stan **Zarchiwizowano**, należy zmienić ten stan na **Opublikowano**, aby użytkownicy mogli używać tych szablonów w usłudze Azure Rights Management.

Szablony, które można importować z usług AD RMS, wyglądają i działają tak samo jak niestandardowe szablony tworzone w witrynie Azure portal. Aby zmienić stan importowanych szablonów na opublikowano, aby użytkownicy mogli je widzieć i wybierać w aplikacjach, zobacz [Konfigurowanie i Zarządzanie szablonami usługi Azure Information Protection](./configure-policy-templates.md).

Oprócz publikowania nowo zaimportowanych szablonów wprowadzono tylko dwie ważne zmiany dotyczące szablonów, który wykonanie może być konieczne przed kontynuacją migracji. Aby udostępnić użytkownikom spójniejsze środowisko pracy podczas migracji, nie należy wprowadzać dodatkowych zmian w importowanych szablonach. Nie należy również publikować dwóch domyślnych szablonów dostarczanych z usługą Azure Information Protection ani tworzyć w tym czasie nowych szablonów. Zamiast tego należy zaczekać na zakończenie procesu migracji i anulowanie obsługi serwerów usług AD RMS.

Zmiany szablonu, których wprowadzenie może być konieczne w ramach tego kroku:

- Jeśli przed migracją utworzono szablony niestandardowe usługi Azure Information Protection, należy je ręcznie wyeksportować i zaimportować.

- W przypadku szablonów w usługach AD RMS była używana **każdy** grupy, może być konieczne ręczne dodawanie użytkowników lub grup. 
    
    W usługach AD RMS grupy Każdy udzielone prawa wszystkim użytkownikom uwierzytelniony przez usługę Active Directory w środowisku lokalnym, a ta grupa nie jest obsługiwana przez usługę Azure Information Protection. Odpowiednik dystrybucji, zapewniania to grupy, które są tworzone automatycznie dla wszystkich użytkowników w dzierżawie usługi Azure AD. Grupy Każdy była używana dla szablonów usług AD RMS, konieczne może dodać użytkowników i uprawnień, które chcesz przyznać im.

### <a name="procedure-if-you-created-custom-templates-before-the-migration"></a>Procedura w przypadku utworzenia szablonów niestandardowych przed migracją

Jeśli szablony niestandardowe zostały utworzone przed rozpoczęciem migracji (przed aktywowaniem usługi Azure Rights Management lub po jej aktywowaniu), nie będą one dostępne dla użytkowników po zakończeniu migracji, nawet jeśli ich stan został ustawiony na **Opublikowano**. Aby były one dostępne dla użytkowników, najpierw należy wykonać następujące czynności: 

1. Zidentyfikować te szablony i zanotować ich identyfikator szablonu, uruchamiając polecenie [Get-AadrmTemplate](/powershell/aadrm/vlatest/get-aadrmtemplate). 

2. Wyeksportować szablony przy użyciu polecenia cmdlet programu PowerShell usługi Azure RMS [Export-AadrmTemplate](/powershell/aadrm/vlatest/export-aadrmtemplate).

3. Zaimportować szablony przy użyciu polecenia cmdlet programu PowerShell usługi Azure RMS [Export-AadrmTemplate](/powershell/module/aadrm/import-aadrmtemplate).

Następnie można opublikować lub zarchiwizować te szablony w taki sam sposób, jak w przypadku każdego innego szablonu utworzonego po migracji.

### <a name="procedure-if-your-templates-in-ad-rms-used-the-anyone-group"></a>Procedura, jeśli szablony w usługach AD RMS używały grupy **KAŻDY**

W przypadku szablonów w usługach AD RMS była używana **każdy** grupy najbliższego odpowiednik grupy usługi Azure Information Protection nosi **AllStaff-7184AB3F-CCD1-46F3-8233-3E09E9CF0E66@\<nazwa_dzierżawy >. onmicrosoft.com**. Na przykład w przypadku firmy Contoso ta grupa może wyglądać podobnie do następującej: <strong>AllStaff-7184AB3F-CCD1-46F3-8233-3E09E9CF0E66@contoso.onmicrosoft.com</strong>. Ta grupa zawiera wszystkich użytkowników w dzierżawie usługi Azure AD.

Jeśli zarządzasz, szablonów i etykiety w witrynie Azure portal, ta grupa wyświetla się jako nazwa domeny dzierżawy usługi w usłudze Azure AD. Na przykład ta grupa może wyglądać podobnie do poniższego firmy Contoso: **contoso.onmicrosoft.com**. Aby dodać tę grupę, wyświetla opcja **Dodaj \<nazwa organizacji > — wszystkie elementy członkowskie**.

Jeśli nie masz pewności, czy szablony usługi AD RMS obejmują grupę KAŻDY, możesz użyć następującego przykładowego skryptu programu Windows PowerShell, aby zidentyfikować te szablony. Aby uzyskać więcej informacji o używaniu programu Windows PowerShell z usługami AD RMS, zobacz [przy użyciu programu Windows PowerShell do administrowania usługami AD RMS](https://technet.microsoft.com/library/ee221079%28v=ws.10%29.aspx).

Można łatwo dodać użytkowników zewnętrznych do szablonów podczas konwertowania tych szablonów do etykiet w witrynie Azure portal. Następnie na **Dodaj uprawnienia** bloku wybierz **wprowadź szczegóły** ręcznie określić adresy e-mail dla tych użytkowników. 

Aby uzyskać więcej informacji na temat tej konfiguracji, zobacz [sposobu konfigurowania etykiety dla ochrony usługi Rights Management](./configure-policy-protection.md).

#### <a name="sample-windows-powershell-script-to-identify-ad-rms-templates-that-include-the-anyone-group"></a>Przykładowy skrypt programu Windows PowerShell umożliwiający zidentyfikowanie szablonów usług AD RMS obejmujących grupę KAŻDY
Ta sekcja zawiera przykładowy skrypt, aby pomóc w zidentyfikowaniu żadnych szablonów usług AD RMS, które mają zdefiniowaną grupą każdy, zgodnie z opisem w poprzedniej sekcji.

**Zastrzeżenie:** Ten przykładowy skrypt nie jest obsługiwana w ramach usług ani programów pomocy technicznej standard firmy Microsoft. Ten przykładowy skrypt jest dostarczany W STANIE TAKIM, W JAKIM SIĘ ZNAJDUJE, bez jakichkolwiek gwarancji.

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


## <a name="next-steps"></a>Następne kroki
Przejdź do [fazy 3 — konfiguracji po stronie klienta](migrate-from-ad-rms-phase3.md).
