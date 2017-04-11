---
title: "Migrowanie z usługi AD RMS do usługi Azure Information Protection — faza 4"
description: "Faza 4 migracji z usługi AD RMS do usługi Azure Information Protection, obejmująca kroki od 8 do 9 z sekcji Migrowanie z usługi AD RMS do usługi Azure Information Protection."
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 03/08/2017
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: d51e7bdd-2e5c-4304-98cc-cf2e7858557d
ms.reviewer: esaggese
ms.suite: ems
ms.openlocfilehash: d36f47e586ac1295dcc79e43a9e061b4c7c7fe1e
ms.sourcegitcommit: 31e128cc1b917bf767987f0b2144b7f3b6288f2e
translationtype: HT
---
# <a name="migration-phase-4---post-migration-tasks"></a>Faza 4 migracji — zadania po migracji

>*Dotyczy: Active Directory Rights Management Services, Azure Information Protection, Office 365*


Skorzystaj z poniższych informacji dotyczących fazy 4 migrowania z usługi AD RMS do usługi Azure Information Protection. Te procedury obejmują kroki od 8 do 9 z sekcji [Migrowanie z usługi AD RMS do usługi Azure Information Protection](migrate-from-ad-rms-to-azure-rms.md).


## <a name="step-8-decommission-ad-rms"></a>Krok 8. Likwidowanie wdrożenia usługi AD RMS

Należy usunąć punkt połączenia usługi (SCP) z usługi Active Directory, aby uniemożliwić komputerom odnajdywanie infrastruktury lokalnej usługi Rights Management. Ten krok jest opcjonalny w przypadku migrowanych istniejących klientów z powodu przekierowania skonfigurowanego w rejestrze (np. przez uruchomienie skryptu migracji). Jednak usunięcie punktu połączenia usługi uniemożliwi nowym klientom i potencjalnie narzędziom i usługom powiązanym z usługą RMS wyszukiwanie punktu połączenia usługi po zakończeniu migracji. Wszystkie połączenia powinny przechodzić do usługi Azure Rights Management. 

Aby usunąć punkt połączenia usługi, trzeba być zalogowanym jako administrator domeny przedsiębiorstwa, a następnie użyć poniższej procedury:

1. W konsoli Usług zarządzania prawami dostępu w usłudze Active Directory kliknij prawym przyciskiem myszy klaster AD RMS, a następnie kliknij pozycję **Właściwości**.

2. Kliknij kartę **Punkt połączenia usługi**.

3. Zaznacz pole wyboru **Zmień punkt połączenia usługi**.

4. Wybierz pozycję **Usuń bieżący punkt połączenia usługi**, a następnie kliknij przycisk **OK**.

Aby monitorować działanie serwerów usługi AD RMS, można na przykład sprawdzać [żądania w raporcie kondycji systemu](https://technet.microsoft.com/library/ee221012%28v=ws.10%29.aspx), [tabelę żądań obsługi](http://technet.microsoft.com/library/dd772686%28v=ws.10%29.aspx) lub [przeprowadzać inspekcję dostępu użytkowników do chronionej zawartości](http://social.technet.microsoft.com/wiki/contents/articles/3440.ad-rms-frequently-asked-questions-faq.aspx). Po potwierdzeniu, że klienci usługi RMS nie komunikują się już z serwerami i pomyślnie używają usługi Azure Information Protection, można usunąć rolę serwera usługi AD RMS z tych serwerów. W przypadku korzystania z serwerów dedykowanych można najpierw wykonać krok zapobiegawczy polegający na zamknięciu serwerów na pewien okres, aby upewnić się, że nie zostaną zgłoszone problemy, które wymagają ponownego uruchomienia tych serwerów w celu zapewnienia ciągłości usługi podczas badania, dlaczego klienci nie korzystają z usługi Azure Information Protection.

Po zlikwidowaniu serwerów usługi AD RMS można skorzystać z możliwości przejrzenia szablonów w klasycznym portalu Azure. Umożliwi to ich skonsolidowanie, dzięki czemu użytkownicy będą mieć mniej szablonów do wyboru, a także ponowne ich skonfigurowanie, a nawet dodanie nowych. Będzie to również odpowiedni moment, aby opublikować szablony domyślne. Aby uzyskać więcej informacji, zobacz [Konfigurowanie szablonów niestandardowych dla usługi Azure Rights Management](../deploy-use/configure-custom-templates.md).

## <a name="step-9-re-key-your-azure-information-protection-tenant-key"></a>Krok 9. Ponowne tworzenie klucza dzierżawy usługi Azure Information Protection
Ten krok należy wykonać po zakończeniu migracji, jeśli we wdrożeniu usług AD RMS używano trybu kryptograficznego 1 usług RMS, ponieważ ponowne tworzenie kluczy powoduje powstanie nowego klucza dzierżawy, który korzysta z trybu kryptograficznego 2 usług RMS. Korzystanie z usługi Azure RMS z trybem kryptograficznym 1 jest obsługiwane tylko podczas procesu migracji.

Ta czynność jest opcjonalna, ale zalecana po ukończeniu migracji, nawet w przypadku uruchomienia usług RMS z trybem kryptograficznym 2. Ponowne utworzenie klucza w tym scenariuszu zabezpiecza klucz dzierżawy usługi Azure Information Protection przed potencjalnymi naruszeniami zabezpieczeń klucza usługi AD RMS.

W przypadku ponownego tworzenia klucza dzierżawy usługi Azure Information Protection (proces znany również jako „uaktualnianie klucza”) tworzony jest nowy klucz, a klucz oryginalny zostaje zarchiwizowany. Jednak ze względu na to, że przechodzenie z jednego klucza do innego nie jest realizowane natychmiast, ale trwa kilka tygodni, nie należy czekać do momentu naruszenia bezpieczeństwa oryginalnego klucza, ale ponownie utworzyć klucz dzierżawy usługi Azure Information Protection zaraz po zakończeniu migracji.

Aby ponownie utworzyć klucz dzierżawy usługi Azure Information Protection:

- Jeśli klucz dzierżawy jest zarządzany przez firmę Microsoft: skontaktuj się z [pomocą techniczną firmy Microsoft](../get-started/information-support.md#to-contact-microsoft-support) i otwórz **zgłoszenie do pomocy technicznej usługi Azure Information Protection z żądaniem ponownego utworzenia klucza usługi Azure Information Protection po migracji z usługi AD RMS**. Musisz udowodnić, że jesteś administratorem dzierżawy usługi Azure Information Protection oraz wiedzieć, że potwierdzenie tego procesu może potrwać kilka dni. Naliczane są standardowe opłaty za pomoc techniczną. Ponowne tworzenie klucza dzierżawy nie jest bezpłatną usługą pomocy technicznej.

- Jeśli klucz dzierżawy jest zarządzany przez użytkownika (BYOK): w usłudze Azure Key Vault utwórz ponownie klucz używany dla dzierżawy usługi Azure Information Protection, a następnie uruchom ponownie polecenie cmdlet [Use-AadrmKeyVaultKey](/powershell/aadrm/vlatest/use-aadrmkeyvaultkey), aby określić nowy klucz adresu URL. 

## <a name="next-steps"></a>Następne kroki

Aby uzyskać więcej informacji na temat zarządzania kluczem dzierżawy usługi Azure Information Protection, zobacz [Operacje związane z kluczem dzierżawy usługi Azure Rights Management](../deploy-use/operations-tenant-key.md).

Teraz po zakończeniu migracji sprawdź [plan wdrożenia](deployment-roadmap.md), aby zidentyfikować wszelkie inne zadania wdrożenia, których wykonanie może być konieczne.

[!INCLUDE[Commenting house rules](../includes/houserules.md)]
