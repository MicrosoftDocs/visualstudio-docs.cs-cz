---
title: 'Návod: Analýza kódu C / C++ na výskyt závad | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- C/C++, code analysis
- code analysis, walkthroughs
- code, analyzing C/C++
- code analysis tool, walkthroughs
ms.assetid: eaee55b8-85fe-47c7-a489-9be0c46ae8af
caps.latest.revision: 37
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 6a5e98ee673d232065dd522b0b81a21760306979
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51782307"
---
# <a name="walkthrough-analyzing-cc-code-for-defects"></a>Návod: Analýza kódu C/C++ na výskyt závad
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Tento návod ukazuje, jak analýza kódu C/C++ pro potenciální závady kódu pomocí nástroje Analýza kódu pro kód C/C++.  
  
 V tomto podrobném návodu projděte proces pomocí analýzy kódu pro analýzu kódu C/C++ pro potenciální závady kódu.  
  
 Bude proveďte následující kroky:  
  
-   Spustíte analýzu kódu na nativní kód.  
  
-   Analýza upozornění vad kódu.  
  
-   Považovat upozornění za chybu.  
  
-   Popis zdrojového kódu ke zlepšení chyb analýzy kódu.  
  
## <a name="prerequisites"></a>Požadavky  
  
-   [!INCLUDE[vsPreLong](../includes/vsprelong-md.md)] nebo [!INCLUDE[vsUltLong](../includes/vsultlong-md.md)].  
  
-   Kopie [demonstrační ukázka](../code-quality/demo-sample.md).  
  
-   Základní znalosti jazyka C/C++.  
  
### <a name="to-run-code-defect-analysis-on-native-code"></a>Pro spuštění analýzy vadu kódu v nativním kódu  
  
1.  Ukázka řešení otevřít v [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].  
  
     Ukázka řešení nyní naplní **Průzkumníka řešení**.  
  
2.  Na **sestavení** nabídky, klikněte na tlačítko **znovu sestavit řešení**.  
  
     Řešení je sestaveno bez jakýchkoli chyb nebo upozornění.  
  
3.  V **Průzkumníka řešení**, vyberte projekt CodeDefects.  
  
4.  Na **projektu** nabídky, klikněte na tlačítko **vlastnosti**.  
  
     **Stránky vlastností CodeDefects** se zobrazí dialogové okno.  
  
5.  Klikněte na tlačítko **analýza kódu**.  
  
6.  Klikněte na tlačítko **povolit analýzu kódu pro C/C++ při sestavení** zaškrtávací políčko.  
  
7.  Znovu sestavte projekt CodeDefects.  
  
     Upozornění analýzy kódu se zobrazují v **seznam chyb**.  
  
### <a name="to-analyze-code-defect-warnings"></a>K analýze upozornění vad kódu  
  
1.  Na **zobrazení** nabídky, klikněte na tlačítko **seznam chyb**.  
  
     V závislosti na profil pro vývojáře, který jste zvolili v [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], možná budete muset odkazovat na **ostatní Windows** na **zobrazení** nabídky a pak klikněte na tlačítko **seznam chyb**.  
  
2.  V **seznam chyb**, dvakrát klikněte na následující upozornění:  
  
     upozornění C6230: implicitní přetypování mezi sémanticky odlišnými typy: použití HRESULT v kontextu logické hodnoty.  
  
     Editor kódu zobrazí řádek, který způsobil toto upozornění ve funkci `bool``ProcessDomain()`. Toto upozornění signalizuje, že hodnotu HRESULT se používá v příkazu "if" kde se očekává výsledek s logickou hodnotu.  
  
3.  Použití makra SUCCEEDED opravte toto upozornění. Váš kód by měl vypadat následovně:  
  
    ```  
    if (SUCCEEDED (ReadUserAccount()) )  
    ```  
  
4.  V **seznam chyb**, dvakrát klikněte na následující upozornění:  
  
     upozornění C6282: nesprávný operátor: přiřazení konstanty v kontextu testu. Byl == očekávání?  
  
5.  Opravte toto upozornění při testování rovnosti. Váš kód by měl vypadat podobně jako následující kód:  
  
    ```  
    if ((len == ACCOUNT_DOMAIN_LEN) || (g_userAccount[len] != '\\'))  
    ```  
  
### <a name="to-treat-warning-as-an-error"></a>Považovat upozornění za chybu  
  
1.  V souboru Bug.cpp, přidejte následující `#pragma` příkaz na začátek souboru, který se upozornění C6001 považovat za chybu:  
  
    ```  
    #pragma warning (error: 6001)  
    ```  
  
2.  Znovu sestavte projekt CodeDefects.  
  
     V **seznam chyb**, C6001 se teď zobrazí jako chyba.  
  
3.  Opravte chyby zbývající dva C6001 v **seznam chyb** podle inicializace `i` a `j` na hodnotu 0.  
  
4.  Znovu sestavte projekt CodeDefects.  
  
     Projekt se sestaví bez žádná upozornění ani chyby.  
  
### <a name="to-correct-the-source-code-annotation-warnings-in-annotationc"></a>Chcete-li opravit upozornění anotace zdrojového kódu v annotation.c  
  
1.  V Průzkumníku řešení vyberte projekt poznámky.  
  
2.  Na **projektu** nabídky, klikněte na tlačítko **vlastnosti**.  
  
     **Stránky vlastností poznámky** se zobrazí dialogové okno.  
  
3.  Klikněte na tlačítko **analýza kódu**.  
  
4.  Vyberte **povolit analýzu kódu pro C/C++ při sestavení** zaškrtávací políčko.  
  
5.  Znovu sestavte projekt poznámky.  
  
6.  V **seznam chyb**, dvakrát klikněte na následující upozornění:  
  
     upozornění C6011: přesměrování ukazatele NULL "newNode".  
  
     Toto upozornění znamená selhání volajícího zkontrolovat návratovou hodnotu. V tomto případě volání **AllocateNode** může vrátit hodnotu NULL (viz annotations.h hlavičkový soubor pro deklaraci funkce pro AllocateNode).  
  
7.  Otevřete soubor annotations.cpp.  
  
8.  Chcete-li opravit toto upozornění, použijte k testování hodnotu vrácenou příkazem 'if'. Váš kód by měl vypadat následovně:  
  
     `if (NULL != newNode)`  
  
     `{`  
  
     `newNode->data = value;`  
  
     `newNode->next = 0;`  
  
     `node->next = newNode;`  
  
     `}`  
  
9. Znovu sestavte projekt poznámky.  
  
     Projekt se sestaví bez žádná upozornění ani chyby.  
  
### <a name="to-use-source-code-annotation"></a>Použití poznámek zdrojového kódu  
  
1.  Přidat poznámku formální parametry a vrátí hodnotu funkce `AddTail` s použitím podmínky hodnocením před kurzem a příspěvku, jak je znázorněno v tomto příkladu:  
  
     `[returnvalue:SA_Post (Null=SA_Maybe)] LinkedList* AddTail`  
  
     `(`  
  
     `[SA_Pre(Null=SA_Maybe)] LinkedList* node,`  
  
     `int value`  
  
     `)`  
  
2.  Znovu sestavte projekt poznámky.  
  
3.  V **seznam chyb**, dvakrát klikněte na následující upozornění:  
  
     upozornění C6011: přesměrování ukazatele NULL "uzel".  
  
     Toto upozornění označuje, že uzel předaného do funkce může mít hodnotu null a označuje číslo řádku, které upozornění vygenerovalo.  
  
4.  Chcete-li opravit toto upozornění, použijte k testování hodnotu vrácenou příkazem 'if'. Váš kód by měl vypadat následovně:  
  
    ```  
    . . .  
    LinkedList *newNode = NULL;   
    if (NULL == node)  
    {  
         return NULL;  
        . . .  
    }  
    ```  
  
5.  Znovu sestavte projekt poznámky.  
  
     Projekt se sestaví bez žádná upozornění ani chyby.  
  
## <a name="see-also"></a>Viz také  
 [Návod: Analýza spravovaného kódu na výskyt závad v kódu](../code-quality/walkthrough-analyzing-managed-code-for-code-defects.md)



