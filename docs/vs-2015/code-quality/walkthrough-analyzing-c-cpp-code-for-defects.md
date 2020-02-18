---
title: 'Návod: analýzaC++ kódu C v případě vad | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
helpviewer_keywords:
- C/C++, code analysis
- code analysis, walkthroughs
- code, analyzing C/C++
- code analysis tool, walkthroughs
ms.assetid: eaee55b8-85fe-47c7-a489-9be0c46ae8af
caps.latest.revision: 37
author: corob-msft
ms.author: corob
manager: jillfra
ms.openlocfilehash: c822dbcc6a1ece2040da22a3442dd584c3926d97
ms.sourcegitcommit: 68f893f6e472df46f323db34a13a7034dccad25a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/15/2020
ms.locfileid: "77272432"
---
# <a name="walkthrough-analyzing-cc-code-for-defects"></a>Návod: Analýza kódu C/C++ na výskyt závad
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Tento návod ukazuje, jak analyzovat kód CC++ /Code pro potenciální nedostatky v kódu pomocí nástroje Analýza kódu pro C/C++ Code.  
  
 V tomto návodu jste provedli postup použití nástroje Analýza kódu k analýze kódu jazyka C/C++ o potenciální vady kódu.  
  
 Provedete následující kroky:  
  
- Spusťte analýzu kódu v nativním kódu.  
  
- Analyzuje upozornění na vady kódu.  
  
- Považovat upozornění za chybu.  
  
- Opatřit zdrojový kód poznámkami, aby se zlepšila analýza vad kódu.  
  
## <a name="prerequisites"></a>Předpoklady  
  
- [!INCLUDE[vsPreLong](../includes/vsprelong-md.md)] nebo [!INCLUDE[vsUltLong](../includes/vsultlong-md.md)].  
  
- Kopie [ukázkové ukázky](../code-quality/demo-sample.md).  
  
- Základní porozumění C/C++.  
  
### <a name="to-run-code-defect-analysis-on-native-code"></a>Spuštění analýzy vad kódu v nativním kódu  
  
1. Otevřete ukázkové řešení v [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].  
  
     Ukázkové řešení nyní naplňuje **Průzkumník řešení**.  
  
2. V nabídce **sestavení** klikněte na příkaz **znovu sestavit řešení**.  
  
     Řešení se sestaví bez chyb nebo upozornění.  
  
3. V **Průzkumník řešení**vyberte projekt CodeDefects.  
  
4. V nabídce **projekt** klikněte na příkaz **vlastnosti**.  
  
     Zobrazí se dialogové okno **stránky vlastností CodeDefects** .  
  
5. Klikněte na **Analýza kódu**.  
  
6. Klikněte na zaškrtávací políčko **Povolit analýzu kódu proC++ sestavení C/on** .  
  
7. Znovu sestavte projekt CodeDefects.  
  
     Upozornění analýzy kódu se zobrazují v **Seznam chyb**.  
  
### <a name="to-analyze-code-defect-warnings"></a>Analýza upozornění na vady kódu  
  
1. V nabídce **zobrazení** klikněte na příkaz **Seznam chyb**.  
  
     V závislosti na profilu vývojáře, který jste zvolili v [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], bude pravděpodobně nutné Ukázat na **jiné okna** v nabídce **zobrazení** a pak kliknout na tlačítko **Seznam chyb**.  
  
2. V **Seznam chyb**dvakrát klikněte na následující upozornění:  
  
     Upozornění C6230: implicitní přetypování mezi sémanticky odlišnými typy: používá HRESULT v logickém kontextu.  
  
     Editor kódu zobrazuje řádek, který způsobil upozornění ve funkci `bool``ProcessDomain()`. Toto upozornění označuje, že se v příkazu if používá HRESULT, kde se očekává logický výsledek.  
  
3. Opravte toto upozornění pomocí makra úspěšné. Váš kód by měl vypadat podobně jako následující kód:  
  
    ```  
    if (SUCCEEDED (ReadUserAccount()) )  
    ```  
  
4. V **Seznam chyb**dvakrát klikněte na následující upozornění:  
  
     Warning C6282: nesprávný operátor: přiřazení k konstantě v kontextu testu. Bylo = = zamýšleno?  
  
5. Opravte toto upozornění pomocí testování rovnosti. Váš kód by měl vypadat podobně jako následující kód:  
  
    ```  
    if ((len == ACCOUNT_DOMAIN_LEN) || (g_userAccount[len] != '\\'))  
    ```  
  
### <a name="to-treat-warning-as-an-error"></a>Zpracování upozornění jako chyby  
  
1. V souboru Error. cpp přidejte následující příkaz `#pragma` na začátek souboru, aby se upozornění C6001 jako chyba:  
  
    ```  
    #pragma warning (error: 6001)  
    ```  
  
2. Znovu sestavte projekt CodeDefects.  
  
     V **Seznam chyb**se teď jako chyba zobrazuje C6001.  
  
3. Opravte zbývající dvě chyby C6001 v **Seznam chyb** inicializací `i` a `j` na 0.  
  
4. Znovu sestavte projekt CodeDefects.  
  
     Projekt se vytváří bez upozornění a chyb.  
  
### <a name="to-correct-the-source-code-annotation-warnings-in-annotationc"></a>Oprava upozornění pro poznámky zdrojového kódu v poznámce. c  
  
1. V Průzkumník řešení vyberte projekt poznámky.  
  
2. V nabídce **projekt** klikněte na příkaz **vlastnosti**.  
  
     Zobrazí se dialogové okno **stránky vlastností poznámky** .  
  
3. Klikněte na **Analýza kódu**.  
  
4. Zaškrtněte zaškrtávací políčko **Povolit analýzu kódu pro sestaveníC++ C/on** .  
  
5. Znovu sestavte projekt poznámky.  
  
6. V **Seznam chyb**dvakrát klikněte na následující upozornění:  
  
     Upozornění C6011: přesměrování NULOVÉho ukazatele "newNode".  
  
     Toto upozornění signalizuje selhání volajícímu, aby zkontroloval vrácenou hodnotu. V takovém případě volání **AllocateNode** může vracet hodnotu null (viz hlavičkový soubor poznámky. h pro deklaraci funkce pro AllocateNode).  
  
7. Otevřete soubor poznámky. cpp.  
  
8. Chcete-li toto upozornění opravit, použijte příkaz if pro otestování návratové hodnoty. Váš kód by měl vypadat podobně jako následující kód:  
  
     `if (NULL != newNode)`  
  
     `{`  
  
     `newNode->data = value;`  
  
     `newNode->next = 0;`  
  
     `node->next = newNode;`  
  
     `}`  
  
9. Znovu sestavte projekt poznámky.  
  
     Projekt se vytváří bez upozornění a chyb.  
  
### <a name="to-use-source-code-annotation"></a>Použití poznámky ke zdrojovému kódu  
  
1. Pomocí podmínek pre a post, jak je znázorněno v tomto příkladu, opatřit poznámkami formální parametry a návratovou hodnotu funkce `AddTail`.  
  
     `[returnvalue:SA_Post (Null=SA_Maybe)] LinkedList* AddTail`  
  
     `(`  
  
     `[SA_Pre(Null=SA_Maybe)] LinkedList* node,`  
  
     `int value`  
  
     `)`  
  
2. Znovu sestavit projekt poznámek.  
  
3. V **Seznam chyb**dvakrát klikněte na následující upozornění:  
  
     Upozornění C6011: přesměrování NULOVÉho ukazatele "Node".  
  
     Toto upozornění znamená, že uzel předaný do funkce může mít hodnotu null a označuje číslo řádku, kde bylo upozornění vyvoláno.  
  
4. Chcete-li toto upozornění opravit, použijte příkaz if pro otestování návratové hodnoty. Váš kód by měl vypadat podobně jako následující kód:  
  
    ```  
    . . .  
    LinkedList *newNode = NULL;   
    if (NULL == node)  
    {  
         return NULL;  
        . . .  
    }  
    ```  
  
5. Znovu sestavit projekt poznámek.  
  
     Projekt se vytváří bez upozornění a chyb.  
  
## <a name="see-also"></a>Viz také  
 [Návod: Analýza spravovaného kódu na výskyt závad v kódu](../code-quality/walkthrough-analyzing-managed-code-for-code-defects.md)
