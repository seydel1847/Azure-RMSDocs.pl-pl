---
title: Instalowanie i konfigurowanie łącznika usługi Rights Management — AIP
description: Informacje ułatwiające instalowanie i konfigurowanie łącznika usługi Azure Rights Management (RMS). Te procedury obejmują kroki od 1 do 4 z sekcji Wdrażanie łącznika usługi Azure Rights Management.
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 12/12/2018
ms.topic: conceptual
ms.service: information-protection
ms.assetid: 4fed9d4f-e420-4a7f-9667-569690e0d733
ms.reviewer: esaggese
ms.suite: ems
ms.openlocfilehash: 57dd5faad33681bbf87045b61335e11baaa973a2
ms.sourcegitcommit: 9dc6da0fb7f96b37ed8eadd43bacd1c8a1a55af8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/18/2019
ms.locfileid: "54393969"
---
# <a name="installing-and-configuring-the-azure-rights-management-connector"></a>Instalowanie i konfigurowanie łącznika Azure Rights Management

>*Dotyczy: [Usługa Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection), Windows Server 2016, Windows Server 2012 R2, Windows Server 2012, Windows Server 2008 R2*

Skorzystaj z poniższych informacji, aby zainstalować i skonfigurować łącznik Azure Rights Management (RMS). Te procedury obejmują kroki od 1 do 4 z sekcji [Wdrażanie łącznika usługi Azure Rights Management](deploy-rms-connector.md).

Przed rozpoczęciem upewnij się, czy zostały sprawdzone [wymagania wstępne](deploy-rms-connector.md#prerequisites-for-the-rms-connector) dla tego wdrożenia.


## <a name="installing-the-rms-connector"></a>Instalowanie łącznika usług RMS

1.  Zidentyfikuj komputery (co najmniej dwa) tego #identyfikator
2.  l uruchomienia łącznika usługi RMS. Muszą one odpowiadać minimalnej specyfikacji wymienionej w wymaganiach wstępnych.

    > [!NOTE]
    > Zostanie zainstalowany pojedynczy łącznik RMS (składający się z wielu serwerów w celu zapewnienia wysokiej dostępności) na dzierżawę (dzierżawę usługi Office 365 lub dzierżawę usługi Azure AD). W przeciwieństwie do usługi Active Directory RMS nie musisz instalować łącznika usług RMS w każdym lesie.

2.  Pobierz pliki źródłowe dla łącznika usługi RMS z [Centrum pobierania Microsoft](https://go.microsoft.com/fwlink/?LinkId=314106).

    Aby zainstalować łącznik usług RMS, pobierz plik RMSConnectorSetup.exe.

    Ponadto:

    -   Jeśli chcesz później skonfigurować łącznik z komputera 32-bitowego, pobierz również plik RMSConnectorAdminToolSetup_x86.exe.

    -   Jeśli chcesz użyć narzędzia do konfiguracji serwera dla łącznika usługi RMS, aby zautomatyzować konfigurację ustawień rejestru na serwerach lokalnych, Pobierz również plik GenConnectorConfig.ps1.

3.  Na komputerze, na którym chcesz zainstalować łącznik usługi RMS, uruchom plik **RMSConnectorSetup.exe** z uprawnieniami administratora.

4.  Na stronie powitalnej Instalatora łącznika zarządzania prawami firmy Microsoft, wybierz **łącznik instalacji usługi Microsoft Rights Management na komputerze**, a następnie kliknij przycisk **dalej**.

5.  Przeczytaj i zaakceptuj postanowienia licencyjne łącznika usługi RMS, a następnie kliknij przycisk **Dalej**.

W celu kontynuacji wprowadź konto i hasło, aby skonfigurować łącznik usługi RMS.

## <a name="entering-credentials"></a>Wprowadzanie poświadczeń
Przed skonfigurowaniem łącznika usług RMS, musisz wprowadzić poświadczenia dla konta, które ma wystarczające uprawnienia do konfigurowania łącznika usług RMS. Na przykład można wpisać <strong>admin@contoso.com</strong>, a następnie podać hasło dla tego konta.

To konto nie może wymagać uwierzytelniania wieloskładnikowego (MFA), ponieważ narzędzie administracyjne usługi Microsoft Rights Management nie obsługuje metody MFA dla tego konta. 

Łącznik nakłada pewne ograniczenia dotyczące znaków w tym haśle. Nie można użyć hasła, które ma jakiekolwiek z następujących znaków: Handlowe "i" ( **&** ); left nawiasu ostrego ( **[** ), prawy nawias ( **]** ); jest to proste oferty ( **"** ); i apostrof ( **'** ). Jeśli hasło zawiera dowolny z tych znaków, uwierzytelnienie dla łącznika usług RMS zakończy się niepowodzeniem i pojawi się komunikat o błędzie informujący, że **kombinacja nazwy użytkownika i hasła nie jest poprawna**, mimo że można pomyślnie zalogować się przy użyciu tego konta i hasła w przypadku innych scenariuszy. Jeśli ten scenariusz dotyczy to Twojego hasła, użyj innego konta z hasłem, które nie zawierają dowolne spośród tych znaków specjalnych, lub zresetować hasło, aby nie zawierało ono żadnego z tych znaków specjalnych.

Ponadto, jeśli zostały zaimplementowane [kontrolki dołączania](activate-service.md#configuring-onboarding-controls-for-a-phased-deployment), upewnij się, że podane przez Ciebie konto użytkownika może chronić zawartość. Jeśli na przykład możliwość ochrony zawartości została ograniczona do grupy „Dział IT”, konto określone w tym miejscu musi być członkiem tej grupy. W przeciwnym razie zostanie wyświetlony komunikat o błędzie: **Próba odnalezienia lokalizacji usługi administracji i organizacji nie powiodła się. Upewnij się, że usługa Microsoft Rights Management jest włączona dla Twojej organizacji.**

Można użyć konta, które ma jedno z następujących uprawnień:

- **Administrator globalny dzierżawy**: Konto administratora globalnego dla dzierżawy usługi Office 365 lub dzierżawy usługi Azure AD.

- **Administrator globalny usługi Azure Rights Management**: Konto usługi Azure Active Directory, któremu przypisano rolę administratora globalnego usługi Azure RMS.

- **Administrator łącznika usługi Azure Rights Management**: Konto usługi Azure Active Directory, któremu udzielono prawa do instalowania łącznika usług RMS dla Twojej organizacji i administrowania.

  > [!NOTE]
  > Rola administratora globalnego usługi Azure Rights Management i roli administratora łącznika usługi Azure Rights Management jest przypisana do kont za pomocą polecenia cmdlet [Add-AadrmRoleBasedAdministrator](/powershell/module/aadrm/add-aadrmrolebasedadministrator) usługi Azure RMS.
  > 
  > Aby uruchomić łącznik usługi RMS z najmniejszymi uprawnieniami, utwórz w tym celu dedykowane konto, dla którego zostanie następnie przypisana rola administratora łącznika usługi Azure RMS w następujący sposób:
  > 
  > 1. Jeśli jeszcze nie zostało to zrobione, pobierz i zainstaluj środowisko Windows PowerShell dla usług Rights Management. Aby uzyskać więcej informacji, zobacz [Instalowanie modułu AADRM programu PowerShell](install-powershell.md).
  > 
  >    Uruchom program Windows PowerShell za pomocą polecenia **Uruchom jako administrator** i połącz się z usługą Azure RMS za pomocą polecenia [Connect-AadrmService](/powershell/module/aadrm/connect-aadrmservice):
  > 
  >    ```
  >    Connect-AadrmService                   //provide Office 365 tenant administrator or Azure RMS global administrator credentials
  >    ```
  > 2. Następnie uruchom polecenie [AadrmRoleBasedAdministrator](/powershell/module/aadrm/add-aadrmrolebasedadministrator) przy użyciu tylko jednego z następujących parametrów:
  > 
  >    ```
  >    Add-AadrmRoleBasedAdministrator -EmailAddress <email address> -Role "ConnectorAdministrator"
  >    ```
  > 
  >    ```
  >    Add-AadrmRoleBasedAdministrator -ObjectId <object id> -Role "ConnectorAdministrator"
  >    ```
  > 
  >    ```
  >    Add-AadrmRoleBasedAdministrator -SecurityGroupDisplayName <group Name> -Role "ConnectorAdministrator"
  >    ```
  >    Na przykład wpisz: **Dodaj AadrmRoleBasedAdministrator - EmailAddress melisa@contoso.com -Role "ConnectorAdministrator"**
  > 
  >    Mimo że te polecenia przypisują rolę ConnectorAdministrator, można w tym miejscu użyć również roli GlobalAdministrator.

W procesie instalacji łącznika usługi RMS weryfikowane i instalowane jest całe wstępnie wymagane oprogramowanie, instalowana jest usługa Internet Information Services (IIS), jeśli nie została zainstalowana wcześniej, oraz instalowane i konfigurowane jest oprogramowanie łącznika. Ponadto usługa Azure RMS zostaje przygotowana do konfiguracji poprzez utworzenie następujących obiektów:

-   Pusta tabela serwerów, które są autoryzowane do korzystania z łącznika w celu komunikowania się z usługami Azure RMS. Serwery zostaną dodane do tej tabeli później.

-   Zestaw tokenów zabezpieczających łącznik, które autoryzują operacje przeprowadzane za pomocą usług Azure RMS. Tokeny te są pobierane z usługi Azure RMS i instalowane na komputerze lokalnym w rejestrze. Są chronione za pomocą danych interfejsu programowania aplikacji ochrony (DPAPI) oraz poświadczeń konta systemu lokalnego.

Na ostatniej stronie kreatora wykonaj następujące czynności, a następnie kliknij przycisk **Zakończ**:

-   Jeśli jest to pierwszy łącznik, który został zainstalowany, nie zaznaczaj w tej chwili opcji **Uruchom konsolę administratora łącznika do autoryzowania serwerów**. Zaznaczysz tę opcję po zainstalowaniu drugiego (lub końcowego) łącznika usług RMS. Zamiast tego uruchom ponownie kreatora na co najmniej jednym komputerze. Należy zainstalować co najmniej dwa łączniki.

-   Jeśli zainstalowano drugi (lub końcowy) łącznik, wybierz pozycję **Uruchom konsolę administratora łącznika do autoryzowania serwerów**.

> [!TIP]
> W tym momencie dostępny jest test weryfikujący, który można wykonać, aby sprawdzić, czy usługi sieci web dla łącznika usług RMS działają:
>
> -   Za pomocą przeglądarki sieci web połącz się z adresem **http://&lt;adres_łącznika&gt;/_wmcs/certification/servercertification.asmx**, zastępując *&lt;adres_łącznika&gt;* adresem serwera lub nazwą zainstalowanego łącznika usługi RMS. Po udanym połączeniu wyświetlana jest strona **ServerCertificationWebService**.

Jeśli musisz odinstalować łącznik usług RMS, ponownie uruchom kreatora i wybierz opcję odinstalowania.

Jeśli wystąpią jakiekolwiek problemy podczas instalacji, sprawdź dziennik instalacji: **connector_ Rights Management %LocalAppData%\Temp\Microsoft\<Data i godzina > .log** 

Na przykład dziennik instalacji może wyglądać podobnie do connector_20170803110352.log C:\Users\Administrator\AppData\Local\Temp\Microsoft Rights Management

## <a name="authorizing-servers-to-use-the-rms-connector"></a>Autoryzowanie serwerów do korzystania z łącznika usług RMS
Po zainstalowaniu łącznika usługi RMS na co najmniej dwóch komputerach wszystko jest gotowe do autoryzowania serwerów i usług, które mają używać łącznika usługi RMS. Na przykład: serwerów z systemem Exchange Server 2013 lub SharePoint Server 2013.

Aby zdefiniować te serwery, uruchom narzędzie administracyjne łącznika usługi RMS i dodaj pozycje do listy dozwolonych serwerów. To narzędzie można uruchomić po zaznaczeniu opcji **Uruchom konsolę administracyjną łącznika do autoryzowania serwerów** pod koniec działania kreatora konfigurowania łącznika Microsoft Rights Management. Można też uruchomić je oddzielnie z poziomu kreatora.

Podczas autoryzowania serwerów należy pamiętać o następujących kwestiach:

- Dodawanym serwerom zostaną przyznane specjalne uprawnienia. Wszystkim kontom określonym dla roli programu Exchange Server w konfiguracji łącznika zostanie przyznana [rola administratora](configure-super-users.md) w usługach Azure RMS, która umożliwi im dostęp do całej zawartości tej dzierżawy RMS. Funkcja administratora jest automatycznie włączana na tym etapie w razie potrzeby. Aby uniknąć zagrożenia zabezpieczeń podniesienia uprawnień, należy wskazać tylko konta używane przez serwery programu Exchange w danej organizacji. Wszystkim serwerom skonfigurowanym jako serwery programu SharePoint lub serwery plików, które używają infrastruktury FCI, zostaną przyznane uprawnienia zwykłych użytkowników.

- Można dodać wiele serwerów jako pojedynczy wpis, określając zabezpieczenie usługi Active Directory lub grupy dystrybucyjnej, lub konto usługi, które jest używane przez więcej niż jeden serwer. Podczas używania tej konfiguracji Grupa serwerów współużytkuje te same certyfikaty usług RMS i są wszystkie uznaje się za właścicieli zawartości chronionej przez dowolny z nich. Aby zminimalizować ogólne koszty administracyjne, zalecane jest użycie tej konfiguracji pojedynczej grupy zamiast poszczególnych serwerów w celu autoryzowania serwerów programu Exchange w danej organizacji lub farmy serwerów programu SharePoint.

Na stronie **Serwery, które mogą wykorzystywać łącznik** kliknij przycisk **Dodaj**.

> [!NOTE]
> Autoryzowanie serwerów jest konfiguracją w usłudze Azure RMS równoważną konfiguracji usługi AD RMS ręcznego zastosowania uprawnień NTFS do pliku ServerCertification.asmx dla kont usługi lub serwera i ręcznego udzielania uprawnień administratora dla kont serwera Exchange. Stosowanie uprawnień NTFS do pliku ServerCertification.asmx nie jest wymagane dla łącznika.


### <a name="add-a-server-to-the-list-of-allowed-servers"></a>Dodawanie serwera do listy dozwolonych serwerów
Na stronie **Zezwalaj serwerowi na korzystanie z łącznika** wprowadź nazwę obiektu lub przewiń, aby zidentyfikować obiekt do autoryzacji.

Ważne jest, aby autoryzować odpowiedni obiekt. Aby serwera mógł korzystać z łącznika, do autoryzacji należy wybrać konto, na którym uruchomiona jest usługa lokalna (na przykład program Exchange lub SharePoint). Na przykład jeśli usługa jest uruchomiona jako skonfigurowane konto usługi, dodaj nazwę tego konta usługi do listy. Jeśli usługa jest uruchomiona jako System lokalny, dodaj nazwę obiektu komputera (na przykład SERVERNAME$). Najlepszym rozwiązaniem jest utworzenie grupy, która zawiera te konta i wskazanie jej zamiast nazw poszczególnych serwerów.

Więcej informacji na temat różnych ról serwerów:

-   W przypadku serwerów z systemem Exchange: Należy określić grupę zabezpieczeń i użyć domyślnej grupy (**serwery Exchange**) programu Exchange automatycznie tworzy i przechowuje na wszystkich serwerach programu Exchange w lesie.

-   W przypadku serwerów z programem SharePoint:

    -   Jeśli serwer programu SharePoint 2010 jest skonfigurowany do uruchamiania jako System lokalny (nie używa konta usługi), ręcznie utwórz grupę zabezpieczeń w usługach domenowych w usłudze Active Directory, a następnie dodaj obiekt nazwy komputera dla serwera w tej konfiguracji do tej grupy.

    -   Jeśli serwer programu SharePoint jest skonfigurowany do używania konta usługi (zalecana praktyka dla programu SharePoint 2010 i jedyna możliwość dla programu SharePoint 2016 i SharePoint 2013), należy wykonać następujące czynności:

        1.  Dodaj konto usługi, na którym jest uruchomiona Usługa administracji centralnej programu SharePoint, aby umożliwić skonfigurowanie programu SharePoint za pomocą jego konsoli administratora.

        2.  Dodaj konto skonfigurowane dla puli aplikacji programu SharePoint.

        > [!TIP]
        > Jeśli te dwa konta są różne, należy rozważyć utworzenie pojedynczej grupy, który zawiera oba konta, aby zminimalizować ogólne koszty administracyjne.

-   W przypadku serwerów plików, które korzystają z infrastruktury klasyfikacji pliku, usługi skojarzone są uruchamiane za pomocą konta systemu lokalnego, dlatego jest wymagane autoryzowanie konta komputera dla serwerów plików (na przykład SERVERNAME$) lub grupy, która zawiera te konta komputera.

Po zakończeniu dodawania serwerów do listy kliknij przycisk **Zamknij**.

Jeśli jeszcze nie zostało to zrobione, należy teraz skonfigurować funkcję równoważenia obciążenia dla serwerów, które mają zainstalowany łącznik usługi RMS, i rozważyć, czy dla połączeń między tymi serwerami i serwerami, które właśnie zostały autoryzowane, należy używać protokołu HTTPS.

## <a name="configuring-load-balancing-and-high-availability"></a>Konfigurowanie funkcji równoważenia obciążenia i wysokiej dostępności
Po zainstalowaniu drugiego lub końcowego wystąpienia łącznika usługi RMS należy zdefiniować nazwę serwera w adresie URL łącznika i skonfigurować system z równoważeniem obciążenia.

Nazwa serwera w adresie URL łącznika może być dowolną nazwą w kontrolowanym obszarze nazw. Na przykład można utworzyć wpis w systemie DNS dla adresu **rmsconnector.contoso.com** i skonfigurować go do używania adresu IP w systemie równoważenia obciążenia. Nie ma żadnych specjalnych wymagań dla tej nazwy i nie musi być ona skonfigurowana na samych serwerach łącznika. Jeśli serwery programów Exchange i SharePoint nie będą komunikować się za pomocą łącznika przez Internet, ta nazwa nie musi być rozpoznawalna w sieci Internet.

> [!IMPORTANT]
> Zaleca się nie zmieniać tej nazwy po skonfigurowaniu serwerów programu Exchange i SharePoint do korzystania z łącznika, ponieważ należy następnie wyczyść wszystkie konfiguracje IRM tych serwerów i skonfigurować je ponownie.

Po utworzeniu nazwy w systemie DNS i skonfigurowaniu jej dla adresu IP należy skonfigurować dla tego adresu funkcję równoważenia obciążenia kierującą ruch do serwerów łącznika. Do tego celu można wykorzystać dowolną usługę równoważenia obciążenia opartą na protokole IP, która obejmuje funkcję równoważenia obciążenia sieciowego (NLB) w systemie Windows Server. Aby uzyskać więcej informacji, zobacz [Load Balancing Deployment Guide](https://technet.microsoft.com/library/cc754833%28v=WS.10%29.aspx) (Przewodnik wdrażania usługi równoważenia obciążenia).

Aby skonfigurować klaster równoważenia obciążenia sieciowego, użyj następujących ustawień:

-   Ports: 80 (dla protokołu HTTP) lub 443 (dla protokołu HTTPS)

    Aby uzyskać więcej informacji na temat użycia protokołu HTTP lub HTTPS, zobacz następną sekcję.

-   Koligacja: Brak

-   Metoda dystrybucji: równe

Nazwa zdefiniowana dla systemu z równoważeniem obciążenia (dla serwerów z uruchomioną usługą łącznika usługi RMS) jest nazwą łącznika usługi RMS w danej organizacji. Można jej użyć później, podczas konfigurowania serwerów lokalnych do korzystania z usługi Azure RMS.

## <a name="configuring-the-rms-connector-to-use-https"></a>Konfigurowanie łącznika usług RMS do korzystania z protokołu HTTPS
> [!NOTE]
> Ten krok konfiguracji jest opcjonalny, ale zalecany w celu zapewnienia dodatkowej ochrony.

Mimo że korzystanie z protokołu TLS lub SSL jest opcjonalne dla łącznika usług RMS, jest zalecane dla dowolnej usługi opartej na protokole HTTP wymagającej zwiększonej ochrony. Ta konfiguracja uwierzytelnia serwery z łącznikiem na serwerach programu Exchange i SharePoint używających tego łącznika. Dodatkowo wszystkie dane, które są wysyłane z tych serwerów do łącznika są zaszyfrowane.

Aby umożliwić łącznikowi usług RMS wykorzystanie protokołu TLS, na każdym serwerze z uruchomionym łącznikiem usług RMS zainstaluj certyfikat uwierzytelniania serwera zawierający nazwę używaną dla łącznika. Na przykład jeśli nazwą Twojego łącznika usług RMS zdefiniowanego w systemie DNS jest **rmsconnector.contoso.com**, wdróż certyfikat uwierzytelniania serwera zawierający wpis **rmsconnector.contoso.com** w podmiocie certyfikatu jako nazwę pospolitą. Możesz także umieścić wpis **rmsconnector.contoso.com** w alternatywnej nazwie certyfikatu jako wartość DNS. Certyfikat nie musi obejmować nazwy serwera. Następnie w usługach IIS, powiąż ten certyfikat z domyślną witryny sieci Web.

Jeśli używasz opcji protokołu HTTPS, upewnij się, że wszystkie serwery z uruchomionym łącznikiem mają ważny certyfikat uwierzytelniania serwera, który tworzy łańcuch z zaufanym dla serwerów programu Exchange i SharePoint głównym urzędem certyfikacji. Ponadto jeśli urząd certyfikacji (CA), który wystawił certyfikaty dla serwerów łącznika publikuje listy odwołania certyfikatów (CRL), serwery programu Exchange i programu SharePoint muszą mieć możliwość pobrania tej listy CRL.

> [!TIP]
> Można użyć następujących informacji i zasobów w celu żądania i instalowania certyfikatu uwierzytelniania serwera i powiązania tego certyfikatu z domyślną witryną sieci Web w usługach IIS:
>
> - Jeśli używasz usług certyfikatów w usłudze Active Directory (AD CS) i urzędu certyfikacji przedsiębiorstwa (CA) do wdrożenia tych certyfikatów uwierzytelniania serwera, możesz zduplikować, a następnie wykorzystać szablon certyfikatu serwera sieci Web. Ten szablon certyfikatu używa **podanej w żądaniu** nazwy podmiotu certyfikatu, co oznacza, że w przypadku żądania certyfikatu można podać nazwę FQDN łącznika usług RMS dla nazwy podmiotu certyfikatu lub alternatywnej nazwy podmiotu.
> -   Jeśli używasz autonomicznego urzędu certyfikacji lub nabywasz ten certyfikat od innej firmy, zobacz [Konfigurowanie certyfikatów serwera internetowego (usługi IIS 7)](https://technet.microsoft.com/library/cc731977%28v=ws.10%29.aspx) w bibliotece dokumentacji [serwera sieci Web (IIS)](https://technet.microsoft.com/library/cc753433%28v=ws.10%29.aspx) w witrynie TechNet.
> - Aby skonfigurować usługi IIS do używania certyfikatu, zobacz [Dodawanie powiązań do witryny (usługi IIS 7)](https://technet.microsoft.com/library/cc731692.aspx) w bibliotece dokumentacji [serwera sieci Web (IIS)](https://technet.microsoft.com/library/cc753433%28v=ws.10%29.aspx) w witrynie TechNet.

## <a name="configuring-the-rms-connector-for-a-web-proxy-server"></a>Konfigurowanie łącznika usług RMS dla serwera proxy sieci Web
Jeśli serwery łącznika są zainstalowane w sieci, która nie ma bezpośredniego połączenia z siecią Internet i wymaga ręcznej konfiguracji serwera proxy sieci Web dla zapewnienia ruchu wychodzącego do sieci Internet, należy na tych serwerach skonfigurować rejestr dla łącznika usług RMS.

#### <a name="to-configure-the-rms-connector-to-use-a-web-proxy-server"></a>Aby skonfigurować łącznik usług RMS w celu użycia serwera proxy sieci Web

1.  Na każdym serwerze z programem łącznika usług RMS otwórz edytor rejestru, np. Regedit.

2.  Przejdź do klucza **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\AADRM\Connector**

3.  Dodaj wartość ciągu **ProxyAddress**, a następnie ustaw dla tej wartości dane **http://&lt;Mój_adres_IP_lub_domena_serwera_proxy&gt;:&lt;Mój_port_serwera_proxy&gt;**.

    Na przykład: **http://proxyserver.contoso.com:8080**

4.  Zamknij edytor rejestru, a następnie ponownie uruchom serwer lub wykonaj polecenie IISReset w celu ponownego uruchomienia usług IIS.

## <a name="installing-the-rms-connector-administration-tool-on-administrative-computers"></a>Instalowanie narzędzia administracyjnego łącznika usługi RMS na komputerach administracyjnych
Narzędzie administracyjne łącznika usługi RMS można uruchomić z komputera, który nie ma zainstalowanego łącznika usług RMS, jeśli ten komputer spełnia następujące wymagania:

-   Komputer fizyczny lub wirtualny z systemem Windows Server 2012 lub Windows Server 2012 R2 (wszystkie wersje), Windows Server 2008 R2 lub Windows Server 2008 R2 z dodatkiem Service Pack 1 (wszystkie wersje), Windows 8.1, Windows 8 lub Windows 7.

-   Co najmniej 1 GB pamięci RAM.

-   Co najmniej 64 GB miejsca na dysku.

-   Co najmniej jeden interfejs sieciowy.

-   Dostęp do sieci Internet za pośrednictwem zapory (lub serwera proxy sieci Web).

Aby zainstalować narzędzie administracyjne łącznika usługi RMS, uruchom następujące pliki:

-   Na komputerze 32-bitowe: RMSConnectorAdminToolSetup_x86.exe

-   Na komputerze 64-bitowym: RMSConnectorSetup.exe

Jeśli te pliki nie zostały już pobrane, możesz to zrobić w [Centrum pobierania Microsoft](https://go.microsoft.com/fwlink/?LinkId=314106).


## <a name="next-steps"></a>Następne kroki
Teraz, gdy łącznik usługi RMS jest zainstalowany i skonfigurowany, można przystąpić do konfigurowania serwerów lokalnych, aby mogły z niego korzystać. Przejdź do sekcji [Konfigurowanie serwerów na potrzeby łącznika Azure Rights Management](configure-servers-rms-connector.md).

