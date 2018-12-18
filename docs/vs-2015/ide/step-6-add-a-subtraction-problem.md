---
title: 'Krok 6: Přidejte problém odečtení | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 59204ef9-24bd-4f81-b85f-e3168e518a3e
caps.latest.revision: 27
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 793204bf4a08d09d7ce6e48e37254dd311ac6a08
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/12/2018
ms.locfileid: "49229239"
---
# <a name="step-6-add-a-subtraction-problem"></a>Krok 6: Přidejte problém odečtení
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

V šesté části tohoto kurzu kurzu přidáte úlohu odčítání a zjistěte, jak provádět následující úlohy:  
  
-   Store hodnoty odčítání.  
  
-   Generovat náhodná čísla pro úlohu (a ujistěte se, že odpověď je od 0 do 100).  
  
-   Aktualizujte metodu, která kontroluje odpovědi, takže příliš zkontroluje nový problém s odčítáním.  
  
-   Aktualizujte obslužné rutiny události cyklů časovače, aby obslužná rutina události vyplnila správnou odpověď, když vyprší čas.  
  
### <a name="to-add-a-subtraction-problem"></a>Chcete-li přidat úlohu odčítání  
  
1.  Přidáte dvě celočíselné proměnné pro odčítání do svého formuláře mezi celočíselné proměnné pro sčítání a časovač. Kód by měl vypadat nějak takto.  
  
     [!code-csharp[VbExpressTutorial3Step5_6#12](../snippets/csharp/VS_Snippets_VBCSharp/vbexpresstutorial3step5_6/cs/form1.cs#12)]
     [!code-vb[VbExpressTutorial3Step5_6#12](../snippets/visualbasic/VS_Snippets_VBCSharp/vbexpresstutorial3step5_6/vb/form1.vb#12)]  
  
     Názvy nových proměnných celých čísel –**minuend** a **subtrahend**– nejsou programovací termíny. Jsou to tradiční názvy v aritmetice pro číslo, které se ještě odečteno (subtrahend) a číslo, ze kterého je menšitel se odečte (minuend). Rozdíl je minuend mínus subtrahend. Můžete použít jiné názvy, protože program nevyžaduje konkrétní názvy pro proměnné, ovládací prvky, komponenty nebo metody. Je třeba dodržovat pravidla, například názvy číslicemi, ale obvykle můžete použít názvy, například x1, x2, x3 a x4. Ale obecný názvy usnadňují mohou ztížit čtení kódu a problémy téměř znemožnit sledování. Pokud chcete zachovat názvy proměnných jedinečný a užitečné, budete používat tradiční názvy pro násobení (násobenec x násobitel = produktu) a dělení (dělitel ÷ Delenec = podíl) později v tomto kurzu.  
  
     V dalším kroku upravíte `StartTheQuiz()` metodu pro poskytnutí náhodných hodnot pro problém s odčítáním.  
  
2.  Přidejte následující kód za komentář "Vyplnění úlohy odčítání".  
  
     [!code-csharp[VbExpressTutorial3Step5_6#13](../snippets/csharp/VS_Snippets_VBCSharp/vbexpresstutorial3step5_6/cs/form1.cs#13)]
     [!code-vb[VbExpressTutorial3Step5_6#13](../snippets/visualbasic/VS_Snippets_VBCSharp/vbexpresstutorial3step5_6/vb/form1.vb#13)]  
  
     K nedocházelo k záporným odpovědím pro úlohu odčítání, tento kód používá `Next()` metodu `Random` třídy trochu odlišně od jak na úlohu sčítání. Když poskytnete `Next()` metoda dvě hodnoty, použije náhodné číslo, které je větší než nebo rovno první hodnota a menší než druhý. Následující kód zvolí náhodné číslo od 1 do 100 a uloží jej do proměnné minuend.  
  
     [!code-csharp[VbExpressTutorial3Step5_6#21](../snippets/csharp/VS_Snippets_VBCSharp/vbexpresstutorial3step5_6/cs/form1.cs#21)]
     [!code-vb[VbExpressTutorial3Step5_6#21](../snippets/visualbasic/VS_Snippets_VBCSharp/vbexpresstutorial3step5_6/vb/form1.vb#21)]  
  
     Můžete volat `Next()` metodu `Random` třídy, kterou jste nazvali "randomizer" dříve v tomto kurzu několika různými způsoby. Metody, které můžete volat více než jedním způsobem, se nazývají přetížené a můžete je zkoumala technologie IntelliSense. Znovu se podívejte na text nápovědy v okně technologie IntelliSense `Next()` metody.  
  
     ![Okno popisu tlačítka technologie IntelliSense](../ide/media/express-overloads.png "Express_Overloads")  
Okno popisu tlačítka technologie IntelliSense  
  
     Zobrazí se popis **(+ 2 overload(s))**, což znamená, že můžete volat `Next()` metoda dvěma dalšími způsoby. Přetížení obsahují různá čísla nebo typy argumentů, tak, aby fungovaly mírně odlišně od sebe. Například metoda může převzít jediný celočíselný argument, zatímco jedno z jejich přetížení může trvat celé číslo a řetězec. Zvolíte správné přetížení na základě na co chcete udělat. Když přidáte kód, který `StartTheQuiz()` metoda, další informace se zobrazí v okně technologie Intellisense ihned poté, co zadáte `randomizer.Next(`. Stiskněte klávesy šipka nahoru a Šipka dolů k cyklování skrze přetížení, jako je vidět na následujícím obrázku.  
  
     ![Přetížení pro další&#40; &#41; metoda v technologii IntelliSense](../ide/media/express-nextoverload.png "Express_NextOverload")  
Přetížení pro metodu Next() v IntelliSense  
  
     V tomto případě chcete zvolit poslední přetížení, protože můžete určit minimální a maximální hodnoty.  
  
3.  Upravit `CheckTheAnswer()` metodu ke kontrole správného odečtení odpovědí.  
  
     [!code-csharp[VbExpressTutorial3Step5_6#14](../snippets/csharp/VS_Snippets_VBCSharp/vbexpresstutorial3step5_6/cs/form1.cs#14)]
     [!code-vb[VbExpressTutorial3Step5_6#14](../snippets/visualbasic/VS_Snippets_VBCSharp/vbexpresstutorial3step5_6/vb/form1.vb#14)]  
  
     V jazyce Visual C# `&&` je `logical and` operátor. V jazyce Visual Basic je ekvivalentní operátor `AndAlso`. Tyto operátory označují "Pokud součet addend1 a addend2 je roven hodnotě součtu NumericUpDown a minuend mínus subtrahend je roven hodnotě rozdílu NumericUpDown." `CheckTheAnswer()` Vrátí metoda `true` pouze v případě, že odpovědi na sčítání a odčítání problémy jsou obě správné.  
  
4.  Nahraďte poslední část obslužné rutiny události cyklů časovače následujícím kódem, tak, aby vyplnila správnou odpověď, když vyprší čas.  
  
     [!code-csharp[VbExpressTutorial3Step5_6#22](../snippets/csharp/VS_Snippets_VBCSharp/vbexpresstutorial3step5_6/cs/form1.cs#22)]
     [!code-vb[VbExpressTutorial3Step5_6#22](../snippets/visualbasic/VS_Snippets_VBCSharp/vbexpresstutorial3step5_6/vb/form1.vb#22)]  
  
5.  Uložte a spusťte váš kód.  
  
     Váš program zahrnuje úlohu odčítání, jak ukazuje následující obrázek.  
  
     ![Matematický kvíz s úlohou odečítání](../ide/media/express-addsubtract.png "Express_AddSubtract")  
Matematický kvíz s úlohou odečítání  
  
### <a name="to-continue-or-review"></a>Chcete-li pokračovat nebo přezkoumat  
  
-   Přechod k dalšímu kroku výukového programu naleznete v tématu [krok 7: Přidat úlohy násobení a dělení](../ide/step-7-add-multiplication-and-division-problems.md).  
  
-   Chcete-li vrátit k předchozímu kroku tutoriálu, přečtěte si téma [krok 5: přidejte zadejte obslužné rutiny událostí pro ovládací prvky NumericUpDown](../ide/step-5-add-enter-event-handlers-for-the-numericupdown-controls.md).



