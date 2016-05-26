---
# required metadata

title: Informacje o ograniczeniach użycia | Azure RMS
description: Ograniczenia użycia są definiowane przez stałe wymienione w tym temacie.
keywords:
author: bruceperlerms
manager: mbaldwin
ms.date: 04/28/2016
ms.topic: article
ms.prod: azure
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: 16E36039-0FD6-4A0A-82C8-2C9DB19D27DD
# optional metadata

#ROBOTS:
audience: developer
#ms.devlang:
ms.reviewer: shubhamp
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# Informacje o ograniczeniach użycia

Ograniczenia użycia są definiowane przez stałe wymienione w tym temacie.



Każde prawo użytkownika, wymienione w prawej kolumnie usługi AD RMS, ma opis, punkt wymuszania i sugerowane metody wymuszania.

| Prawo usługi AD RMS | Opis | Typowe punkty wymuszania | Jak wymusić |
|--------------|-------------|---------------------------|----------------|
|IPC_GENERIC_ALL |Przyznaje wszystkie prawa użytkownikowi.| Brak |To prawo jest używane przez system. Zazwyczaj nie powinno być sprawdzane bezpośrednio. <br><br> Element [**IpcAccessCheck**](/rights-management/sdk/2.1/api/win/functions#msipc_ipcaccesscheck) używa tego prawa do określenia, czy użytkownikowi należy przydzielić inne uprawnienia, jak w poniższym przykładzie.<br><br> `/* fAccessGranted is set to TRUE if either the IPC_GENERIC_WRITE or the IPC_GENERIC_ALL right is granted */` <br><br> `IpcAccessCheck(hKey, IPC_GENERIC_WRITE, &fAccessGranted);`
|IPC_GENERIC_READ |Prawo do odczytu zawartości dokumentu.|Ładowanie dokumentu|Nie ładuj ani nie prezentuj zawartości dokumentu.|
|IPC_GENERIC_WRITE|Prawo do edycji zawartości dokumentu.|Modyfikacja dokumentu|Ustaw wszystkie kontrolki interfejsu użytkownika używane do modyfikowania zawartości dokumentu jako nieedytowalne. <br><br> Wyłącz wszystkie elementy menu, które mogą powodować zmiany w dokumencie. Typowymi przykładami są opcje **Edycja** > **Wytnij**, **Edycja** > **Wklej** i **Wstaw**. <br><br>Wyłącz wszystkie elementy menu skrótów, które mogą powodować zmiany w dokumencie.|
|Brak prawa usługi AD RMS|Obiekt wywołujący nie ma żadnych praw usługi AD RMS|Zapisywanie|Wyłącz menu **Plik** > **Zapisz**. <br><br> **Uwaga** To prawo nie kontroluje opcji **Plik** > **Zapisz jako**, ponieważ prawo nie reprezentuje zmiany w oryginalnym dokumencie.<br><br> Wyłącz wszelkie skróty klawiaturowe, które mogą posłużyć do wyzwalania opcji Zapisz (np. Ctrl + S).<br><br> **Porada** Najlepszym rozwiązaniem jest zaktualizowanie podstawowego kodu opcji **Plik** > **Zapisz** w taki sposób, aby brak takiego prawa u użytkownika powodował błąd. Jest to dodatkowe zabezpieczenie na wypadek pominięcia jakichkolwiek mechanizmów środowiska użytkownika, które mogą służyć do wyzwolenia opcji zapisywania.
|IPC_GENERIC_EXTRACT|Prawo do wyodrębniania zawartości z formatu chronionego i umieszczanie jej w formacie niechronionym.|Kopiuj do Schowka|Wyłącz menu **Edycja** > **Kopiuj**. Wyłącz menu **Edycja** > **Wytnij**. <br><br>Wyłącz funkcje **Kopiuj** i **Wytnij** we wszystkich menu skrótów.<br><br>Wyłącz wszelkie skróty klawiaturowe, które mogą posłużyć do wyzwalania opcji Kopiuj (np. Ctrl + C lub Ctrl + X).<br><br>Zaktualizuj programy obsługi komunikatów okien pod kątem uprawnienia [**WM_CUT**](https://msdn.microsoft.com/library/windows/desktop/ms649023), aby odrzucały kopiowanie danych, jeśli użytkownik nie ma tego prawa. Jeśli okno używa domyślnych programów obsługi komunikatów systemu Windows, utwórz podklasę tego okna i wprowadź własne programy obsługi dla uprawnień **WM_COPY** i **WM_CUT**.
|Brak prawa usługi AD RMS|Obiekt wywołujący nie ma żadnych praw usługi AD RMS|Zapisz jako|W oknie dialogowym **Zapisywanie jako** wyłącz wszelkie formaty plików, które umożliwiałyby zapisanie dokumentu bez ochrony przez usługę RMS.|
|Brak prawa usługi AD RMS|Obiekt wywołujący nie ma żadnych praw usługi AD RMS|Alt + PrtScn|Wywołaj element [**IpcProtectWindow**](/rights-management/sdk/2.1/api/win/functions#msipc_ipcprotectwindow) we wszystkich oknach, które renderują zawartość dokumentu.|
|IPC_GENERIC_EXPORT|Prawo do wyodrębniania zawartości z formatu chronionego i umieszczanie jej w innym formacie chronionym przez usługi AD RMS.|Zapisz jako|W oknie dialogowym **Zapisywanie jako** wyłącz możliwość zapisywania w jakimkolwiek innym formacie pliku.<br><br>**Porada** Najlepszym rozwiązaniem jest zaktualizowanie podstawowego kodu opcji **Plik** > **Zapisz jako** w taki sposób, aby próba zapisania tego pliku w innym formacie przez użytkownika, który nie ma tego prawa, powodowała błąd. Jest to dodatkowe zabezpieczenie na wypadek pominięcia jakichkolwiek mechanizmów środowiska użytkownika, które mogą służyć do wyzwolenia opcji Zapisz jako.|
|IPC_GENERIC_PRINT|Prawo do drukowania zawartości dokumentu.|Drukowanie|Wyłącz menu **Plik** > **Drukuj**.<br><br>Wyłącz wszelkie skróty klawiaturowe, które mogą posłużyć do wyzwalania opcji Drukuj (np. Ctrl + P).<br><br>Wyłącz elementy menu skrótów, które mogą wyzwalać opcję drukowania.<br><br>**Porada** Najlepszym rozwiązaniem jest zaktualizowanie podstawowego kodu opcji **Plik** > **Drukuj** w taki sposób, aby brak tego prawa u użytkownika powodował błąd. Jest to dodatkowe zabezpieczenie na wypadek pominięcia jakichkolwiek mechanizmów środowiska użytkownika, które mogą służyć do wyzwolenia opcji drukowania.|
|IPC_GENERIC_COMMENT|Niektóre aplikacje obsługują możliwość dodawania komentarzy i adnotacji do dokumentu bez aktualizowania podstawowej zawartości dokumentu.<br><br>To prawo zezwala użytkownikowi na dostęp do tej funkcji.|Recenzja > Wstaw komentarz <br><br> Recenzja > Usuń komentarz | Wyłącz wszystkie elementy menu, które mogą służyć do modyfikowania komentarzy lub adnotacji w dokumencie. Przykłady: **Recenzja** > **Wstaw komentarz** i **Recenzja** > **Usuń komentarz**. <br><br>Wyłącz wszelkie skróty klawiaturowe, które mogą wyzwalać opcję modyfikacji komentarzy w dokumencie.<br><br>**Uwaga** Domyślne wdrożenie wymaga, aby uprawnienia **IPC_GENERIC_COMMENT** i **IPC_GENERIC_WRITE** utrwalały nowe komentarze w pliku. Aplikacje mogą umożliwić obsługę w przypadku przyznania prawa **IPC_GENERIC_COMMENT** i nieprzyznania prawa **IPC_GENERIC_WRITE**. W takim przypadku można zezwolić na użycie opcji Zapisz, jeśli modyfikacje dokumentu są ograniczone wyłącznie do komentarzy.|
|IPC_VIEW_RIGHTS||Brak|Wymuszane przez system. System nie pozwoli deweloperowi na wykonanie zapytania o [**listę praw użytkownika**](/rights-management/sdk/2.1/api/win/structures#msipc_ipc_user_rights_list) z licencji, jeśli to prawo nie zostało przyznane.
|IPC_EDIT_RIGHTS|Niektóre aplikacje umożliwiają użytkownikom modyfikowanie zbioru użytkowników i praw dotyczących zawartości chronionej przez usługę AD RMS.<br><br>To prawo zezwala użytkownikowi na dostęp do tej funkcji.|Prawa aplikacji do edycji kontrolek interfejsu użytkownika|Blokuje użytkownikowi dostęp do wszelkich elementów interfejsu użytkownika, których można użyć do edycji zasad usługi RMS dla dokumentu.|

 

 

 


<!--HONumber=May16_HO2-->


