---
title: Migrowanie z usługi AD RMS do usługi Azure Information Protection — faza 5
description: Faza 5 migracji z usługi AD RMS do usługi Azure Information Protection, obejmująca kroki od 10 do 12 z sekcji Migrowanie z usługi AD RMS do usługi Azure Information Protection.
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 11/11/2018
ms.topic: article
ms.prod: ''
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: d51e7bdd-2e5c-4304-98cc-cf2e7858557d
ms.reviewer: esaggese
ms.suite: ems
ms.openlocfilehash: 39eb09eaf3810ec8cb7152499d704be47e6ad045
ms.sourcegitcommit: 44ff610dec678604c449d42cc0b0863ca8224009
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/31/2018
ms.locfileid: "39372179"
---
# <a name="migration-phase-5---post-migration-tasks"></a>Faza 5 migracji — zadania po migracji

>*Dotyczy: Active Directory Rights Management Services, [usługi Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection), [usługi Office 365](http://download.microsoft.com/download/E/C/F/ECF42E71-4EC0-48FF-AA00-577AC14D5B5C/Azure_Information_Protection_licensing_datasheet_EN-US.pdf)*


Skorzystaj z poniższych informacji dotyczących fazy 5 migrowania z usługi AD RMS do usługi Azure Information Protection. Te procedury obejmują kroki od 10 do 12 z sekcji [Migrowanie z usługi AD RMS do usługi Azure Information Protection](migrate-from-ad-rms-to-azure-rms.md).

## <a name="step-10-deprovision-ad-rms"></a>Krok 10. Anulowanie aprowizacji usługi AD RMS

Należy usunąć punkt połączenia usługi (SCP) z usługi Active Directory, aby uniemożliwić komputerom odnajdywanie infrastruktury lokalnej usługi Rights Management. Ten krok jest opcjonalny w przypadku migrowanych istniejących klientów z powodu przekierowania skonfigurowanego w rejestrze (np. przez uruchomienie skryptu migracji). Jednak usunięcie punktu połączenia usługi uniemożliwia nowym klientom i potencjalnie RMS związane z usług i narzędzi wyszukiwanie punktu połączenia usługi, po zakończeniu migracji. W tym momencie wszystkie połączenia komputerze przejdź do usługi Azure Rights Management. 

Aby usunąć punkt połączenia usługi, trzeba być zalogowanym jako administrator domeny przedsiębiorstwa, a następnie użyć poniższej procedury:

1. W konsoli Usług zarządzania prawami dostępu w usłudze Active Directory kliknij prawym przyciskiem myszy klaster AD RMS, a następnie kliknij pozycję **Właściwości**.

2. Kliknij kartę **Punkt połączenia usługi**.

3. Zaznacz pole wyboru **Zmień punkt połączenia usługi**.

4. Wybierz pozycję **Usuń bieżący punkt połączenia usługi**, a następnie kliknij przycisk **OK**.

Teraz można monitorować serwery AD RMS dla działania. Na przykład sprawdzić [żądania w raporcie kondycji systemu](https://technet.microsoft.com/library/ee221012%28v=ws.10%29.aspx), [tabelę](http://technet.microsoft.com/library/dd772686%28v=ws.10%29.aspx) lub [Przeprowadź inspekcję dostępu użytkowników do chronionej zawartości](http://social.technet.microsoft.com/wiki/contents/articles/3440.ad-rms-frequently-asked-questions-faq.aspx). 

Po potwierdzeniu, że klienci usługi RMS nie komunikują się już z serwerami i pomyślnie używają usługi Azure Information Protection, można usunąć rolę serwera usługi AD RMS z tych serwerów. Jeśli używasz dedykowanych serwerów, możesz preferować krok zapobiegawczy polegający na pierwszym zamykanie serwerów w okresie czasu. Dzięki temu czas, aby upewnić się, że ma nie zostaną zgłoszone problemy, które mogą wymagać ponownego uruchomienia tych serwerów, aby utrzymać ciągłość usługi podczas badania, dlaczego klienci nie korzystają z usługi Azure Information Protection.

Po anulowaniu obsługi serwerów usługi AD RMS, możesz chcieć skorzystać z możliwości przejrzenia szablonów w witrynie Azure portal. Na przykład przekonwertować je na etykiety, ich skonsolidowanie, dzięki czemu użytkownicy będą mieć mniej dokonać wyboru między lub skonfigurować je ponownie. Będzie to również odpowiedni moment, aby opublikować szablony domyślne. Aby uzyskać więcej informacji, zobacz [Konfigurowanie i Zarządzanie szablonami usługi Azure Information Protection](../deploy-use/configure-policy-templates.md).

>[!IMPORTANT]
> Po zakończeniu tej migracji klaster usługi AD RMS nie może być używany z usługą Azure Information Protection ani z opcją „hold your own key” (HYOK). Jeśli zdecydujesz się używać rozwiązania HYOK dla etykiety usługi Azure Information Protection, to z powodu przekierowań, które są teraz stosowane, używany klaster usługi AD RMS musi mieć różne adresy URL licencjonowania do tych w klastrach, które zostały poddane migracji.

## <a name="step-11-complete-client-migration-tasks"></a>Krok 11. Zadania migracji klienta ukończone

Dla klientów urządzeń przenośnych i komputerów Mac: Usuń rekordy SRV systemu DNS, które zostały utworzone, podczas wdrażania [rozszerzenia usług AD RMS dla urządzeń przenośnych](http://technet.microsoft.com/library/dn673574.aspx).

Gdy propogated tych zmian systemu DNS, Ci klienci automatycznie odnajdywać i rozpocząć korzystanie z usługi Azure Rights Management. Jednak komputery Mac, systemem Office Mac buforowanie tych informacji z usług AD RMS. Dla tych komputerów ten proces może potrwać do 30 dni. 

Aby wymusić komputerom Mac na natychmiast uruchom proces wykrywania w narzędziu keychain, wyszukaj "adal" i Usuń wszystkie wpisy biblioteki ADAL. Następnie uruchom następujące polecenia na tych komputerach:

````

rm -r ~/Library/Cache/MSRightsManagement

rm -r ~/Library/Caches/com.microsoft.RMS-XPCService

rm -r ~/Library/Caches/Microsoft\ Rights\ Management\ Services

rm -r ~/Library/Containers/com.microsoft.RMS-XPCService

rm -r ~/Library/Containers/com.microsoft.RMSTestApp

rm ~/Library/Group\ Containers/UBF8T346G9.Office/DRM.plist

killall cfprefsd

````

Gdy wszystkie istniejące komputery Windows zostały przeniesione do usługi Azure Information Protection, nie ma powodu w dalszym ciągu korzystać z kontrolek dołączania i obsługiwać **AIPMigrated** grupy utworzone w ramach procesu migracji. 

Najpierw usunąć kontrolki dołączania, a następnie usunąć **AIPMigrated** grupę i wszystkie metody wdrażania oprogramowania utworzone w celu wdrożenia skryptów migracji.

Aby usunąć kontrolki dołączania:

1. W sesji programu PowerShell połącz się z usługą Azure Rights Management i po wyświetleniu monitu podaj poświadczenia administratora globalnego:

        Connect-Aadrmservice

2. Uruchom następujące polecenie i wprowadź **Y** w celu potwierdzenia:

        Set-AadrmOnboardingControlPolicy -UseRmsUserLicense $False
    
    Należy pamiętać, że to polecenie usuwa wszystkie wymuszanie licencji dla usługi ochrony usługi Azure Rights Management, aby wszystkie komputery można chronić dokumenty i wiadomości e-mail.

3. Potwierdź, że kontrolki dołączania nie są już ustawione:

        Get-AadrmOnboardingControlPolicy

    W danych wyjściowych element **License** powinien wyświetlać **False** i nie powinien być wyświetlany żaden identyfikator GUID dla elementu **SecurityGroupOjbectId**.

Ponadto jeśli używasz pakietu Office 2010 i mieć włączone **zarządzania szablonem zasad praw AD RMS (automatyczne)** zadań w bibliotece harmonogramu zadań Windows, wyłącz to zadanie, ponieważ nie jest używany przez usługi Azure Information Klient ochrony. To zadanie jest zazwyczaj włączane przy użyciu zasad grupy i obsługuje wdrożenia usług AD RMS. To zadanie można znaleźć w następującej lokalizacji: **Microsoft** > **Windows** > **Active Directory Rights Management Services Client**

## <a name="step-12-rekey-your-azure-information-protection-tenant-key"></a>Krok 12. Wymień klucz dzierżawy usługi Azure Information Protection

Ten krok jest zalecany, gdy migracja zostanie zakończona, jeśli we wdrożeniu usług AD RMS używano usługi RMS trybu kryptograficznego 1. Wymiana klucza powoduje ochrony, który używa usługi RMS trybu kryptograficznego 2. 

Nawet jeśli we wdrożeniu usług AD RMS używano trybu kryptograficznego 2, nadal zalecane wykonaj ten krok, ponieważ nowy klucz pomaga chronić dzierżawy przed potencjalnymi naruszeniami zabezpieczeń klucza usługi AD RMS.

Po wymianie klucza dzierżawy usługi Azure Information Protection (znany także jako "Uaktualnianie klucza") aktualnie aktywnego klucza zostaje zarchiwizowany i usługi Azure Information Protection zaczyna używać innego klucza, który określisz. Ten inny klucz może być nowy klucz, który zostanie utworzony w usłudze Azure Key Vault lub domyślnego klucza, który został utworzony automatycznie dla dzierżawy.

Przenoszenie z jednego klucza do innego nie jest realizowane natychmiast, ale trwa kilka tygodni. Ponieważ nie jest bezpośrednim nie poczekaj, aż podejrzewasz naruszenia bezpieczeństwa oryginalnego klucza, ale nie w tym kroku zaraz po zakończeniu migracji.

Aby wymienić klucz dzierżawy usługi Azure Information Protection:

- **Jeśli klucz dzierżawy jest zarządzany przez firmę Microsoft**: Uruchom polecenie cmdlet programu PowerShell [Set-AadrmKeyProperties](/powershell/module/aadrm/set-aadrmkeyproperties) i określić identyfikatora klucza dla klucza, który został utworzony automatycznie dla dzierżawy. Można zidentyfikować wartość do określenia, uruchamiając [Get-AadrmKeys](/powershell/module/aadrm/get-aadrmkeys) polecenia cmdlet. Klucz, który został utworzony automatycznie dla dzierżawy usługi ma najstarsze Data utworzenia, dzięki czemu można ją zidentyfikować za pomocą następującego polecenia:
    
        (Get-AadrmKeys) | Sort-Object CreationTime | Select-Object -First 1

- **Jeśli klucz dzierżawy jest zarządzany przez użytkownika (BYOK)**: W usłudze Azure Key Vault, powtórz proces tworzenia klucza dzierżawy usługi Azure Information Protection, a następnie uruchom [Use-AadrmKeyVaultKey](/powershell/aadrm/vlatest/use-aadrmkeyvaultkey) polecenie cmdlet ponownie, aby określić identyfikator URI Ten nowy klucz. 

Aby uzyskać więcej informacji na temat zarządzania kluczem dzierżawy usługi Azure Information Protection, zobacz [operacje związane z kluczem dzierżawy usługi Azure Information Protection](../deploy-use/operations-tenant-key.md).


## <a name="next-steps"></a>Kolejne kroki

Teraz po zakończeniu migracji sprawdź [plan wdrożenia](deployment-roadmap.md), aby zidentyfikować wszelkie inne zadania wdrożenia, których wykonanie może być konieczne.

