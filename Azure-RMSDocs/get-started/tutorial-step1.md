---
# required metadata

title: Azure RMS — samouczek Szybki start — krok 1 | Azure RMS
description: Pierwszy krok samouczka, dzięki któremu możesz szybko wypróbować usługę Microsoft Azure Rights Management dla swojej organizacji. Wystarczy 5 prostych kroków, które powinny zająć mniej niż 15 minut.
keywords:
author: Cabailey
manager: mbaldwin
ms.date: 04/28/2016
ms.topic: get-started-article
ms.prod: azure
ms.service: rights-management
ms.assetid: 7c4798e6-34a0-4c3f-a47f-505764ddf322

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: esaggese
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---



# Samouczek Szybki start usługi Azure RMS, krok 1. Aktywowanie usługi Rights Management

*Dotyczy usług: Azure Rights Management, Office 365*


Przeskocz do: 
> [!div class="op_single_selector"]
- [Wprowadzenie](quick-start-tutorial.md)
- [Krok 1. Aktywacja usługi Azure RMS](tutorial-step1.md)
- [Krok 2. Instalacja aplikacji RMS sharing](tutorial-step2.md)
- [Krok 3. Przesłanie poufnego dokumentu w wiadomości e-mail](tutorial-step3.md)
- [Krok 4. Odbiorca odczytuje dokument](tutorial-step4.md)
- [Krok 5. Śledzenie dokumentu](tutorial-step5.md)


![Azure RMS — samouczek Szybki start — krok 1](../media/AzRMS_QuickStartSteps1.PNG)

Twoja subskrypcja może obsługiwać usługę Azure Rights Management, jednak domyślnie jest ona wyłączona. Możesz ją aktywować przy użyciu centrum administracyjnego usługi Office 365 lub klasycznego portalu Azure:

-   Jeśli masz subskrypcję usługi Office 365 obejmującą usługę Azure Rights Management lub usługi Office 365 bez usługi Azure Rights Management, ale masz subskrypcję usługi Azure RMS Premium: **użyj centrum administracyjnego usługi Office 365**..

-   Jeśli nie masz subskrypcji usługi Office 365: **użyj klasycznego portalu Azure**..

![Zrzuty ekranu do kroku 1 samouczka](../media/AzRMS_Tutorial_1_Screenshots.png)

### Aby aktywować usługę Rights Management w klasycznym centrum administracyjnym usługi Office 365

1.  Przejdź do [portalu usługi Office 365](https://portal.office.com/) i zaloguj się przy użyciu konta służbowego.

2.  Jeśli centrum administracyjne usługi Office 365 nie zostanie wyświetlone automatycznie, wybierz ikonę uruchamiania aplikacji w lewym górnym rogu i wybierz pozycję **Administrator**. Kafelek **Administrator** jest widoczny tylko dla administratorów usługi Office 365.

    > [!TIP]
    > Aby uzyskać pomoc dotyczącą centrum administracyjnego, zobacz [Centrum administracyjne usługi Office 365 — pomoc administratora](https://support.office.com/article/About-the-Office-365-admin-center-Admin-Help-58537702-d421-4d02-8141-e128e3703547)..

3.  W okienku po lewej stronie rozwiń pozycję **USTAWIENIA USŁUGI**..

4.  Kliknij pozycję **Rights Management**..

5.  Na stronie **RIGHTS MANAGEMENT** kliknij pozycję **Zarządzaj**..

6.  Na stronie **Rights Management** kliknij pozycję **Aktywuj**.

7.  Po wyświetleniu monitu **Czy chcesz aktywować usługę Rights Management?** kliknij pozycję **Aktywuj**..

Zostanie wyświetlony komunikat **Usługa Rights Management została aktywowana** wraz z opcją dezaktywowania tej usługi (może być konieczne ręczne odświeżenie strony).

Tym razem nie klikaj pozycji **Funkcje zaawansowane**. Kliknięcie tej pozycji spowoduje wyświetlenie klasycznego portalu Azure umożliwiającego konfigurowanie szablonów, które nie są potrzebne w tym samouczku. Zamiast tego możesz zamknąć centrum administracyjne usługi Office 365.

### Aby aktywować usługę Rights Management w klasycznym portalu Azure

1.  Przejdź do [klasycznego portalu Azure](http://go.microsoft.com/fwlink/p/?LinkID=275081) i zaloguj się.

2.  W okienku po lewej stronie kliknij pozycję **ACTIVE DIRECTORY**..

3.  Na stronie **Active Directory** kliknij pozycję **RIGHTS MANAGEMENT**..

4.  Wybierz katalog do zarządzania dla usługi [!INCLUDE[aad_rightsmanagement_2](../includes/aad_rightsmanagement_2_md.md)], kliknij pozycję **AKTYWUJ**, a następnie potwierdź akcję.

**STAN USŁUGI RIGHTS MANAGEMENT** powinien mieć teraz wartość **Aktywna**, a opcja **AKTYWUJ** powinna zostać zastąpiona opcją **DEZAKTYWUJ**..

W portalu można skonfigurować inne opcje usługi Rights Management, ale nie są one potrzebne w tym samouczku, dlatego możesz zamknąć klasyczny portal Azure.

To wszystko, co musisz zrobić w pierwszym kroku. Usługa została aktywowana i wszyscy użytkownicy w organizacji mogą teraz chronić ważne i poufne dokumenty. W środowisku produkcyjnym warto ograniczyć, kto może początkowo korzystać z tej funkcji, aby przeprowadzić wdrażanie etapowe. Jednak nie jest to konieczne w przypadku tego samouczka.

W przypadku wdrożenia produkcyjnego prawdopodobnie konieczne będzie również skonfigurowanie szablonów niestandardowych, które nie zostały uwzględnione w tym samouczku. Szablony ułatwiają użytkownikom szybkie stosowanie odpowiednich ustawień, gdy konieczna jest ochrona plików. Podczas aktywowania usługi Rights Management użytkownik automatycznie otrzymuje 2 szablony domyślne, które zazwyczaj uzupełnia własnymi szablonami niestandardowymi w środowisku produkcyjnym. Szablony nie są jednak potrzebne w tym samouczku, dlatego możesz teraz przejść do następnego kroku.

|Jeśli potrzebujesz dodatkowych informacji|Dodatkowe informacje|
|--------------------------------|--------------------------|
|Informacje na temat aktywowania usługi Rights Management i określania, kto może chronić pliki i wiadomości e-mail po aktywowaniu usługi|[Aktywacja usługi Azure Rights Management](../deploy-use/activate-service.md)|
|Informacje na temat szablonów domyślnych i sposobu tworzenia nowych szablonów niestandardowych|[Konfigurowanie szablonów niestandardowych usługi Azure Management Rights](../deploy-use/configure-custom-templates.md)|


>[!div class="step-by-step"]
[« Wprowadzenie](quick-start-tutorial.md)
[Krok 2 »](tutorial-step2.md)

<!--HONumber=Apr16_HO4-->


