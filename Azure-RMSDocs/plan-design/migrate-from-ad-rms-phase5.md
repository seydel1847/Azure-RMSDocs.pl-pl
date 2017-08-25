---
title: "Migrowanie z usługi AD RMS do usługi Azure Information Protection — faza 5"
description: "Faza 5 migracji z usługi AD RMS do usługi Azure Information Protection, obejmująca kroki od 10 do 12 z sekcji Migrowanie z usługi AD RMS do usługi Azure Information Protection."
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 08/24/2017
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: d51e7bdd-2e5c-4304-98cc-cf2e7858557d
ms.reviewer: esaggese
ms.suite: ems
ms.openlocfilehash: 11775c64cbd5abd7c10a145a2d48f335db2d5b69
ms.sourcegitcommit: 8251e4db274519a2eb8033d3135a22c27130bd30
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/25/2017
---
# <a name="migration-phase-5---post-migration-tasks"></a>Faza 5 migracji — zadania po migracji

>*Dotyczy: Active Directory Rights Management Services, Azure Information Protection, Office 365*


Skorzystaj z poniższych informacji dotyczących fazy 5 migrowania z usługi AD RMS do usługi Azure Information Protection. Te procedury obejmują kroki od 10 do 12 z sekcji [Migrowanie z usługi AD RMS do usługi Azure Information Protection](migrate-from-ad-rms-to-azure-rms.md).

## <a name="step-10-deprovision-ad-rms"></a>Krok 10. Anulowanie zastrzeżenia usług AD RMS

Należy usunąć punkt połączenia usługi (SCP) z usługi Active Directory, aby uniemożliwić komputerom odnajdywanie infrastruktury lokalnej usługi Rights Management. Ten krok jest opcjonalny w przypadku migrowanych istniejących klientów z powodu przekierowania skonfigurowanego w rejestrze (np. przez uruchomienie skryptu migracji). Jednak usunięcie punktu SCP uniemożliwia nowych klientów i usług potencjalnie powiązanych usług RMS i narzędzi znajdowania punktu połączenia usługi, po zakończeniu migracji. W tym momencie wszystkie połączenia komputera należy przejdź do usługi Azure Rights Management. 

Aby usunąć punkt połączenia usługi, trzeba być zalogowanym jako administrator domeny przedsiębiorstwa, a następnie użyć poniższej procedury:

1. W konsoli Usług zarządzania prawami dostępu w usłudze Active Directory kliknij prawym przyciskiem myszy klaster AD RMS, a następnie kliknij pozycję **Właściwości**.

2. Kliknij kartę **Punkt połączenia usługi**.

3. Zaznacz pole wyboru **Zmień punkt połączenia usługi**.

4. Wybierz pozycję **Usuń bieżący punkt połączenia usługi**, a następnie kliknij przycisk **OK**.

Teraz można monitorować serwery usług AD RMS dla działania. Na przykład sprawdzić [żądań w raporcie kondycji systemu](https://technet.microsoft.com/library/ee221012%28v=ws.10%29.aspx), [tabelę żądań obsługi](http://technet.microsoft.com/library/dd772686%28v=ws.10%29.aspx) lub [inspekcję dostępu użytkowników do chronionej zawartości](http://social.technet.microsoft.com/wiki/contents/articles/3440.ad-rms-frequently-asked-questions-faq.aspx). 

Po potwierdzeniu, że klienci usługi RMS nie komunikują się już z serwerami i pomyślnie używają usługi Azure Information Protection, można usunąć rolę serwera usługi AD RMS z tych serwerów. Jeśli używasz dedykowanych serwerów można wybrać krok zapobiegawczy polegający na pierwszym zamykanie serwerów w danym okresie czasu. Dzięki temu czas, aby upewnić się, że nie ma żadnych problemów zgłoszonych, które mogą wymagać ponownego uruchomienia tych serwerów, aby utrzymać ciągłość usługi podczas badania, dlaczego klienci nie korzystają z usługi Azure Information Protection.

Po ma anulowana serwerów usług AD RMS, możesz skorzystać z możliwości przejrzenia szablonów w portalu Azure. Na przykład przekonwertować je na etykiet, ich skonsolidowanie, tak aby użytkownicy będą mieć mniej wybranie lub skonfigurować je ponownie. Będzie to również odpowiedni moment, aby opublikować szablony domyślne. Aby uzyskać więcej informacji, zobacz [Konfigurowanie i Zarządzanie szablonami usługi Azure Information Protection](../deploy-use/configure-policy-templates.md).

>[!IMPORTANT]
> Po zakończeniu tej migracji klaster usługi AD RMS nie może być używany z usługą Azure Information Protection ani z opcją „hold your own key” (HYOK). Jeśli zdecydujesz się używać rozwiązania HYOK dla etykiety usługi Azure Information Protection, to z powodu przekierowań, które są teraz stosowane, używany klaster usługi AD RMS musi mieć różne adresy URL licencjonowania do tych w klastrach, które zostały poddane migracji.

## <a name="step-11-remove-onboarding-controls"></a>Krok 11. Usuwanie kontrolek dołączania

Po przeprowadzeniu migracji wszystkich istniejących klientów do usługi Azure Information Protection nie ma powodu, aby w dalszym ciągu korzystać z kontrolek dołączania i obsługiwać grupę **AIPMigrated** utworzoną na potrzeby procesu migracji. 

Najpierw usuń kontrolki dołączania, a następnie usunąć **AIPMigrated** grupę i wszystkie zadania wdrażania oprogramowania, które można utworzyć w celu wdrożenia przekierowań.

Aby usunąć kontrolki dołączania:

1. W sesji programu PowerShell połącz się z usługą Azure Rights Management i po wyświetleniu monitu podaj poświadczenia administratora globalnego:

        Connect-Aadrmservice

2. Uruchom następujące polecenie i wprowadź **Y** w celu potwierdzenia:

        Set-AadrmOnboardingControlPolicy -UseRmsUserLicense $False

3. Potwierdź, że kontrolki dołączania nie są już ustawione:

        Get-AadrmOnboardingControlPolicy

    W danych wyjściowych element **License** powinien wyświetlać **False** i nie powinien być wyświetlany żaden identyfikator GUID dla elementu **SecurityGroupOjbectId**.

## <a name="step-12-rekey-your-azure-information-protection-tenant-key"></a>Krok 12. ponowne tworzenie klucza klucza dzierżawy usługi Azure Information Protection

Ten krok jest zalecane, gdy migracja zostanie zakończona, jeśli wdrożenie usług AD RMS używano RMS trybu kryptograficznego 1. Generowanie wyników w przypadku ochrony, która używa usługi RMS trybu kryptograficznego 2. 

Nawet jeśli wdrożenia usług AD RMS używano trybu kryptograficznego 2, nadal zalecamy wykonać ten krok, ponieważ ułatwia klucza do ochrony dzierżawy przed potencjalnymi naruszeniami bezpieczeństwa klucza usług AD RMS.

Jednak nie ponowne tworzenie klucza w przypadku używania usługi Exchange Online z usługami AD RMS. Exchange Online nie obsługuje zmiany tryby kryptograficzne usług. 

Ponowne tworzenie klucza klucza dzierżawy usługi Azure Information Protection (znanej także jako "Uaktualnianie klucza"), zostaną zarchiwizowane aktualnie aktywnego klucza, a usługi Azure Information Protection, który rozpoczyna się do użycia innego klucza, który określisz. To inny klucz może być nowego klucza, które są tworzone w usłudze Azure Key Vault lub domyślny klucz, który został utworzony automatycznie dla dzierżawy.

Przenoszenie z jednego klucza do innego nie jest realizowane natychmiast, ale trwa kilka tygodni. Ponieważ nie jest bezpośrednim nie poczekaj, aż podejrzewasz naruszenia do oryginalnego klucza, ale tego kroku zaraz po zakończeniu migracji.

Aby wymienić klucz dzierżawy usługi Azure Information Protection:

- **Jeśli klucz dzierżawy jest zarządzany przez firmę Microsoft**: Uruchom polecenie cmdlet programu PowerShell [AadrmKeyProperties zestaw](/powershell/module/aadrm/set-aadrmkeyproperties) i podaj identyfikator klucza dla klucza, który został utworzony automatycznie dla dzierżawy. Można określić wartość, aby określić, uruchamiając [Get-AadrmKeys](/powershell/module/aadrm/get-aadrmkeys) polecenia cmdlet. Klucza, który został utworzony automatycznie dla dzierżawy ma najstarsze Data utworzenia, dlatego można ją zidentyfikować za pomocą następującego polecenia:
    
        (Get-AadrmKeys) | Sort-Object CreationTime | Select-Object -First 1

- **Jeśli klucz dzierżawy jest zarządzany przez użytkownika (BYOK)**: W usłudze Azure Key Vault, powtórz proces tworzenia klucza dzierżawy usługi Azure Information Protection, a następnie uruchom [AadrmKeyVaultKey użyj](/powershell/aadrm/vlatest/use-aadrmkeyvaultkey) polecenia cmdlet ponownie, aby określić identyfikator URI dla tego nowego klucza. 

Aby uzyskać więcej informacji na temat zarządzania kluczem dzierżawy usługi Azure Information Protection, zobacz [Operacje związane z kluczem dzierżawy usługi Azure Rights Management](../deploy-use/operations-tenant-key.md).


## <a name="next-steps"></a>Następne kroki

Teraz po zakończeniu migracji sprawdź [plan wdrożenia](deployment-roadmap.md), aby zidentyfikować wszelkie inne zadania wdrożenia, których wykonanie może być konieczne.

[!INCLUDE[Commenting house rules](../includes/houserules.md)]
