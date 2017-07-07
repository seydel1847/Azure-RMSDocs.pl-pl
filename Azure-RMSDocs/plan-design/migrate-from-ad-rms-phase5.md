---
title: "Migrowanie z usługi AD RMS do usługi Azure Information Protection — faza 5"
description: "Faza 5 migracji z usługi AD RMS do usługi Azure Information Protection, obejmująca kroki od 10 do 12 z sekcji Migrowanie z usługi AD RMS do usługi Azure Information Protection."
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 04/18/2017
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: d51e7bdd-2e5c-4304-98cc-cf2e7858557d
ms.reviewer: esaggese
ms.suite: ems
ms.openlocfilehash: f7678af1314fe7130d1084309a43d7561f7b9494
ms.sourcegitcommit: 04eb4990e2bf0004684221592cb93df35e6acebe
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/30/2017
---
# <a name="migration-phase-5---post-migration-tasks"></a>Faza 5 migracji — zadania po migracji

>*Dotyczy: Active Directory Rights Management Services, Azure Information Protection, Office 365*


Skorzystaj z poniższych informacji dotyczących fazy 5 migrowania z usługi AD RMS do usługi Azure Information Protection. Te procedury obejmują kroki od 10 do 12 z sekcji [Migrowanie z usługi AD RMS do usługi Azure Information Protection](migrate-from-ad-rms-to-azure-rms.md).

## <a name="step-10-deprovison-ad-rms"></a>Krok 10. Anulowanie obsługi usługi AD RMS

Należy usunąć punkt połączenia usługi (SCP) z usługi Active Directory, aby uniemożliwić komputerom odnajdywanie infrastruktury lokalnej usługi Rights Management. Ten krok jest opcjonalny w przypadku migrowanych istniejących klientów z powodu przekierowania skonfigurowanego w rejestrze (np. przez uruchomienie skryptu migracji). Jednak usunięcie punktu połączenia usługi uniemożliwi nowym klientom i potencjalnie narzędziom i usługom powiązanym z usługą RMS wyszukiwanie punktu połączenia usługi po zakończeniu migracji. Wszystkie połączenia powinny przechodzić do usługi Azure Rights Management. 

Aby usunąć punkt połączenia usługi, trzeba być zalogowanym jako administrator domeny przedsiębiorstwa, a następnie użyć poniższej procedury:

1. W konsoli Usług zarządzania prawami dostępu w usłudze Active Directory kliknij prawym przyciskiem myszy klaster AD RMS, a następnie kliknij pozycję **Właściwości**.

2. Kliknij kartę **Punkt połączenia usługi**.

3. Zaznacz pole wyboru **Zmień punkt połączenia usługi**.

4. Wybierz pozycję **Usuń bieżący punkt połączenia usługi**, a następnie kliknij przycisk **OK**.

Teraz należy monitorować serwery usługi AD RMS pod kątem aktywności, na przykład sprawdzając [żądania w raporcie kondycji systemu](https://technet.microsoft.com/library/ee221012%28v=ws.10%29.aspx), [tabelę żądań obsługi](http://technet.microsoft.com/library/dd772686%28v=ws.10%29.aspx) lub [przeprowadzając inspekcję dostępu użytkowników do chronionej zawartości](http://social.technet.microsoft.com/wiki/contents/articles/3440.ad-rms-frequently-asked-questions-faq.aspx). 

Po potwierdzeniu, że klienci usługi RMS nie komunikują się już z serwerami i pomyślnie używają usługi Azure Information Protection, można usunąć rolę serwera usługi AD RMS z tych serwerów. W przypadku korzystania z serwerów dedykowanych można najpierw wykonać krok zapobiegawczy polegający na zamknięciu serwerów na pewien okres, aby upewnić się, że nie zostaną zgłoszone problemy, które wymagają ponownego uruchomienia tych serwerów w celu zapewnienia ciągłości usługi podczas badania, dlaczego klienci nie korzystają z usługi Azure Information Protection.

Po anulowaniu obsługi serwerów usługi AD RMS można skorzystać z możliwości przejrzenia szablonów w klasycznym portalu Azure. Umożliwi to ich skonsolidowanie, dzięki czemu użytkownicy będą mieć mniej szablonów do wyboru, a także ponowne ich skonfigurowanie, a nawet dodanie nowych. Będzie to również odpowiedni moment, aby opublikować szablony domyślne. Aby uzyskać więcej informacji, zobacz [Konfigurowanie szablonów niestandardowych dla usługi Azure Rights Management](../deploy-use/configure-custom-templates.md).

>[!IMPORTANT]
> Po zakończeniu tej migracji klaster usługi AD RMS nie może być używany z usługą Azure Information Protection ani z opcją „hold your own key” (HYOK). Jeśli zdecydujesz się używać rozwiązania HYOK dla etykiety usługi Azure Information Protection, to z powodu przekierowań, które są teraz stosowane, używany klaster usługi AD RMS musi mieć różne adresy URL licencjonowania do tych w klastrach, które zostały poddane migracji.

## <a name="step-11-remove-onboarding-controls"></a>Krok 11. Usuwanie kontrolek dołączania

Po przeprowadzeniu migracji wszystkich istniejących klientów do usługi Azure Information Protection nie ma powodu, aby w dalszym ciągu korzystać z kontrolek dołączania i obsługiwać grupę **AIPMigrated** utworzoną na potrzeby procesu migracji. 

Najpierw należy usunąć kontrolki dołączania, a następnie można usunąć grupę **AIPMigrated** i wszystkie zadania wdrażania oprogramowania utworzone w celu wdrożenia przekierowań.

Aby usunąć kontrolki dołączania:

1. W sesji programu PowerShell połącz się z usługą Azure Rights Management i po wyświetleniu monitu podaj poświadczenia administratora globalnego:

        Connect-Aadrmservice

2. Uruchom następujące polecenie i wprowadź **Y** w celu potwierdzenia:

        Set-AadrmOnboardingControlPolicy -UseRmsUserLicense $False

3. Potwierdź, że kontrolki dołączania nie są już ustawione:

        Get-AadrmOnboardingControlPolicy

    W danych wyjściowych element **License** powinien wyświetlać **False** i nie powinien być wyświetlany żaden identyfikator GUID dla elementu **SecurityGroupOjbectId**.

## <a name="step-12-re-key-your-azure-information-protection-tenant-key"></a>Krok 12. Ponowne tworzenie klucza dzierżawy usługi Azure Information Protection
Ten krok należy wykonać po zakończeniu migracji, jeśli we wdrożeniu usług AD RMS używano trybu kryptograficznego 1 usług RMS, ponieważ ponowne tworzenie kluczy powoduje powstanie nowego klucza dzierżawy, który korzysta z trybu kryptograficznego 2 usług RMS. Korzystanie z usługi Azure RMS z trybem kryptograficznym 1 jest obsługiwane tylko podczas procesu migracji.

Ta czynność jest opcjonalna, ale zalecana po ukończeniu migracji, nawet w przypadku uruchomienia usług RMS z trybem kryptograficznym 2. Ponowne utworzenie klucza w tym scenariuszu zabezpiecza klucz dzierżawy usługi Azure Information Protection przed potencjalnymi naruszeniami zabezpieczeń klucza usługi AD RMS.

W przypadku ponownego tworzenia klucza dzierżawy usługi Azure Information Protection (proces znany również jako „uaktualnianie klucza”) tworzony jest nowy klucz, a klucz oryginalny zostaje zarchiwizowany. Jednak ze względu na to, że przechodzenie z jednego klucza do innego nie jest realizowane natychmiast, ale trwa kilka tygodni, nie należy czekać do momentu naruszenia bezpieczeństwa oryginalnego klucza, ale ponownie utworzyć klucz dzierżawy usługi Azure Information Protection zaraz po zakończeniu migracji.

Aby ponownie utworzyć klucz dzierżawy usługi Azure Information Protection:

- Jeśli klucz dzierżawy jest zarządzany przez firmę Microsoft: skontaktuj się z [pomocą techniczną firmy Microsoft](../get-started/information-support.md#to-contact-microsoft-support) i otwórz **zgłoszenie do pomocy technicznej usługi Azure Information Protection z żądaniem ponownego utworzenia klucza usługi Azure Information Protection po migracji z usługi AD RMS**. Musisz udowodnić, że jesteś administratorem dzierżawy usługi Azure Information Protection oraz wiedzieć, że potwierdzenie tego procesu może potrwać kilka dni. Naliczane są standardowe opłaty za pomoc techniczną. Ponowne tworzenie klucza dzierżawy nie jest bezpłatną usługą pomocy technicznej.

- Jeśli klucz dzierżawy jest zarządzany przez użytkownika (BYOK): w usłudze Azure Key Vault utwórz ponownie klucz używany dla dzierżawy usługi Azure Information Protection, a następnie uruchom ponownie polecenie cmdlet [Use-AadrmKeyVaultKey](/powershell/aadrm/vlatest/use-aadrmkeyvaultkey), aby określić nowy klucz adresu URL. 

Aby uzyskać więcej informacji na temat zarządzania kluczem dzierżawy usługi Azure Information Protection, zobacz [Operacje związane z kluczem dzierżawy usługi Azure Rights Management](../deploy-use/operations-tenant-key.md).

## <a name="next-steps"></a>Następne kroki

Teraz po zakończeniu migracji sprawdź [plan wdrożenia](deployment-roadmap.md), aby zidentyfikować wszelkie inne zadania wdrożenia, których wykonanie może być konieczne.

[!INCLUDE[Commenting house rules](../includes/houserules.md)]
