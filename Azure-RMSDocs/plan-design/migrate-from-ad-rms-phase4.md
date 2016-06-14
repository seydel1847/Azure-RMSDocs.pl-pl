---
# required metadata

title: Migrowanie z usług AD RMS do usługi Azure Rights Management — faza 4 | Azure RMS
description:
keywords:
author: cabailey
manager: mbaldwin
ms.date: 04/28/2016
ms.topic: article
ms.prod: azure
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: d51e7bdd-2e5c-4304-98cc-cf2e7858557d


# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: esaggese
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# Faza 4 migracji — zadania po migracji

*Dotyczy usług: Active Directory Rights Management Services, Azure Rights Management*


Skorzystaj z poniższych informacji dotyczących fazy 4 migrowania usług AD RMS do usługi Azure Rights Management (Azure RMS). Te procedury obejmują kroki od 8 do 9 z sekcji [Migrowanie z usług AD RMS do usługi Azure Rights Management](migrate-from-ad-rms-to-azure-rms.md).


## Krok 8. Likwidowanie wdrożenia usług AD RMS

Opcjonalnie: należy usunąć punkt połączenia usługi (SCP) z usługi Active Directory, aby uniemożliwić komputerom odnajdywanie infrastruktury lokalnej usługi Rights Management. Ten krok jest opcjonalny z powodu przekierowania skonfigurowanego w rejestrze (np. przez uruchomienie skryptu migracji). Aby usunąć punkt połączenia usługi, należy użyć narzędzia rejestrowania punktu połączenia usługi AD będącego częścią [zestawu narzędzi administracyjnych usług Rights Management](http://www.microsoft.com/download/details.aspx?id=1479)..

Aby monitorować działanie serwerów usług AD RMS, można na przykład sprawdzać [żądania w raporcie kondycji systemu](https://technet.microsoft.com/library/ee221012%28v=ws.10%29.aspx), [tabelę żądań obsługi](http://technet.microsoft.com/library/dd772686%28v=ws.10%29.aspx) lub [przeprowadzać inspekcję dostępu użytkowników do chronionej zawartości](http://social.technet.microsoft.com/wiki/contents/articles/3440.ad-rms-frequently-asked-questions-faq.aspx). Po potwierdzeniu, że klienci usług RMS nie komunikują się już z serwerami i pomyślnie używają usługi Azure RMS, można usunąć rolę serwera usług AD RMS z tych serwerów. W przypadku korzystania z serwerów dedykowanych można najpierw wykonać krok zapobiegawczy polegający na zamknięciu serwerów na pewien okres, aby upewnić się, że nie zostaną zgłoszone problemy, które wymagają ponownego uruchomienia tych serwerów w celu zapewnienia ciągłości usługi podczas badania, dlaczego klienci nie korzystają z usługi Azure RMS.

Po zlikwidowaniu serwerów usług AD RMS można skorzystać z możliwości przejrzenia szablonów w klasycznym portalu Azure. Umożliwi to ich skonsolidowanie, dzięki czemu użytkownicy będą mieć mniej szablonów do wyboru, a także ponowne ich skonfigurowanie, a nawet dodanie nowych. Będzie to również odpowiedni moment, aby opublikować szablony domyślne. Aby uzyskać więcej informacji, zobacz [Konfigurowanie szablonów niestandardowych usługi Azure Rights Management](../deploy-use/configure-custom-templates.md).

## Krok 9. Ponowne tworzenie klucza dzierżawy usługi Azure RMS
Ten krok należy wykonać po zakończeniu migracji, jeśli we wdrożeniu usług AD RMS używano trybu kryptograficznego 1 usług RMS, ponieważ ponowne tworzenie kluczy powoduje powstanie nowego klucza dzierżawy, który korzysta z trybu kryptograficznego 2 usług RMS. Korzystanie z usługi Azure RMS z trybem kryptograficznym 1 jest obsługiwane tylko podczas procesu migracji.

Ten krok jest opcjonalny, ale zalecany po zakończeniu migracji nawet w przypadku korzystania z trybu kryptograficznego 2 usług RMS, ponieważ ułatwia on zabezpieczenie klucza dzierżawy usługi Azure RMS przed potencjalnymi naruszeniami bezpieczeństwa klucza usług AD RMS. W przypadku ponownego tworzenia klucza dzierżawy usługi Azure RMS (proces znany również jako „uaktualnianie klucza”) tworzony jest nowy klucz, a klucz oryginalny zostaje zarchiwizowany. Jednak ze względu na to, że przechodzenie z jednego klucza do innego nie jest realizowane natychmiast, ale trwa kilka tygodni, nie należy czekać do momentu naruszenia bezpieczeństwa oryginalnego klucza, ale przeprowadzić ponownie tworzenie klucza dzierżawy usługi RMS zaraz po zakończeniu migracji.

Aby ponownie utworzyć klucz dzierżawy usługi Azure RMS:

-   Jeśli klucz dzierżawy usług RMS jest zarządzany przez firmę Microsoft: zadzwoń do działu pomocy technicznej firmy Microsoft i potwierdź, że jesteś administratorem dzierżawy usług RMS.

-   Jeśli klucz dzierżawy usług RMS jest zarządzany przez użytkownika (BYOK): powtórz procedurę BYOK, aby wygenerować i utworzyć nowy klucz przez Internet lub osobiście.

Aby uzyskać więcej informacji na temat zarządzania kluczem dzierżawy usług RMS, zobacz temat [Operations for your Azure Rights Management Tenant Key](../deploy-use/operations-tenant-key.md) (Operacje dotyczące klucza dzierżawy usługi Azure Rights Management)..

## Następne kroki

Teraz po zakończeniu migracji sprawdź [plan wdrożenia](deployment-roadmap.md), aby zidentyfikować wszelkie inne zadania wdrożenia, których wykonanie może być konieczne.



<!--HONumber=Apr16_HO4-->


