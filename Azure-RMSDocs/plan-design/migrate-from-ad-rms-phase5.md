---
title: "Migrowanie z usługi AD RMS do usługi Azure Information Protection — faza 5"
description: "Faza 5 migracji z usługi AD RMS do usługi Azure Information Protection, obejmująca kroki od 10 do 12 z sekcji Migrowanie z usługi AD RMS do usługi Azure Information Protection."
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 08/07/2017
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: d51e7bdd-2e5c-4304-98cc-cf2e7858557d
ms.reviewer: esaggese
ms.suite: ems
ms.openlocfilehash: aeffd9780001f4c91ea8600f11d8fc3b36abce73
ms.sourcegitcommit: 238657f9450f18213c2b9fb453174df0ce1f1aef
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/07/2017
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

## <a name="step-12-rekey-your-azure-information-protection-tenant-key"></a>Krok 12. Wymiana klucza dzierżawy usługi Azure Information Protection
Ten krok jest wymagany, gdy migracja zostanie zakończona, jeśli wdrożenie usług AD RMS używano RMS trybu kryptograficznego 1. Generowanie tworzy nowy klucz dzierżawy, który korzysta z usług RMS trybu kryptograficznego 2. Tryb kryptograficzny 1 jest obsługiwana dla usługi Azure Information Protection tylko podczas procesu migracji.

Generowanie po zakończeniu migracji pomaga również do ochrony klucza dzierżawy usługi Azure Information Protection przed potencjalnymi naruszeniami bezpieczeństwa klucza usług AD RMS.

Ponowne tworzenie klucza klucza dzierżawy usługi Azure Information Protection (znanej także jako "Uaktualnianie klucza"), tworzony jest nowy klucz, a klucz oryginalny zostaje zarchiwizowany. Jednak przenoszenie z jednego klucza do innego nie jest realizowane natychmiast, ale trwa kilka tygodni. Ponieważ nie jest bezpośrednim, nie należy czekać do momentu naruszenia bezpieczeństwa do oryginalnego klucza, ale ponowne tworzenie klucza klucza dzierżawy usługi Azure Information Protection, natychmiast po zakończeniu migracji.

Aby wymienić klucz dzierżawy usługi Azure Information Protection:

- Jeśli klucz dzierżawy jest zarządzany przez firmę Microsoft: skontaktuj się z [pomocą techniczną firmy Microsoft](../get-started/information-support.md#to-contact-microsoft-support) i otwórz **zgłoszenie do pomocy technicznej usługi Azure Information Protection z żądaniem wymiany klucza usługi Azure Information Protection po migracji z usługi AD RMS**. Musisz udowodnić, że jesteś administratorem dzierżawy usługi Azure Information Protection oraz wiedzieć, że potwierdzenie tego procesu trwa kilka dni. Naliczane są standardowe opłaty za pomoc techniczną. Wymiana klucza dzierżawy nie jest bezpłatną usługą pomocy technicznej.

- Jeśli klucz dzierżawy jest zarządzany przez użytkownika (BYOK): w usłudze Azure Key Vault wymień klucz używany dla dzierżawy usługi Azure Information Protection, a następnie uruchom ponownie polecenie cmdlet [Use-AadrmKeyVaultKey](/powershell/aadrm/vlatest/use-aadrmkeyvaultkey), aby określić adres URL nowego klucza. 

Aby uzyskać więcej informacji na temat zarządzania kluczem dzierżawy usługi Azure Information Protection, zobacz [Operacje związane z kluczem dzierżawy usługi Azure Rights Management](../deploy-use/operations-tenant-key.md).

## <a name="next-steps"></a>Następne kroki

Teraz po zakończeniu migracji sprawdź [plan wdrożenia](deployment-roadmap.md), aby zidentyfikować wszelkie inne zadania wdrożenia, których wykonanie może być konieczne.

[!INCLUDE[Commenting house rules](../includes/houserules.md)]
