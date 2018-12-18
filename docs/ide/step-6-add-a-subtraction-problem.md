---
title: 'Krok 6: Přidejte problém odečtení'
ms.custom: ''
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-acquisition
ms.topic: conceptual
ms.assetid: 59204ef9-24bd-4f81-b85f-e3168e518a3e
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 6960f7ca6db9584af8d43b9cee0d0c6bc810bc7f
ms.sourcegitcommit: 58052c29fc61c9a1ca55a64a63a7fdcde34668a4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2018
ms.locfileid: "34747890"
---
# <a name="step-6-add-a-subtraction-problem"></a>Krok 6: Přidejte problém odečtení
V šesté části tohoto kurzu budete přidejte problém odečtení a zjistěte, jak provádět následující úlohy:

-   Uložení hodnot odčítání.

-   Generovat náhodná čísla pro problém (a ujistěte se, že odpověď je od 0 do 100).

-   Aktualizujte metodu, která kontroluje odpovědi, takže příliš zkontroluje nové odčítání.

-   Aktualizace vašeho časovače <xref:System.Windows.Forms.Timer.Tick> obslužné rutiny události tak, aby obslužná rutina události vyplnila správnou odpověď, když vyprší čas.

## <a name="to-add-a-subtraction-problem"></a>Chcete-li přidat problém odečtení

1.  Přidejte do svého formuláře mezi proměnné celé číslo pro sčítání a časovač dvě proměnné celé číslo pro odčítání. Kód by měl vypadat následovně.

     [!code-vb[VbExpressTutorial3Step5_6#12](../ide/codesnippet/VisualBasic/step-6-add-a-subtraction-problem_1.vb)]
     [!code-csharp[VbExpressTutorial3Step5_6#12](../ide/codesnippet/CSharp/step-6-add-a-subtraction-problem_1.cs)]

     Názvy nové proměnné celé číslo –**minuend** a **subtrahend**– nejsou programování podmínky. Jsou tradiční jména v aritmetice pro číslo, které je odečten (subtrahend) a číslo, ze kterého se subtrahend odečítat (minuend). Rozdíl je minuend mínus subtrahend. Můžete použít jiné názvy, protože program nevyžaduje konkrétní názvy proměnných, ovládací prvky, komponenty nebo metody. Je třeba postupovat podle pravidla například názvy není počínaje číslic, ale obecně můžete použít názvy, například x1, x2, x3 a x4. Však obecné názvy znemožňují kód obtížné číst a problémy téměř sledovat. Chcete-li zachovat názvy proměnných jedinečný a užitečné, budete používat tradiční názvy pro násobení (násobenec x násobitel = produkt s) a dělení (dělenec ÷ dělitel = podíl) dále v tomto kurzu.

     Potom budete změníte `StartTheQuiz()` metoda zajistit náhodných hodnot pro odčítání.

2.  Přidejte následující kód po komentář "Vyplňte odčítání".

     [!code-vb[VbExpressTutorial3Step5_6#13](../ide/codesnippet/VisualBasic/step-6-add-a-subtraction-problem_2.vb)]
     [!code-csharp[VbExpressTutorial3Step5_6#13](../ide/codesnippet/CSharp/step-6-add-a-subtraction-problem_2.cs)]

     Aby záporné odpovědi na problém odečtení tento kód používá <xref:System.Random.Next> metodu <xref:System.Random> třídy trochu jinak z jak sčítání funguje. Pokud dáváte `Next()` metoda dvě hodnoty, vybere náhodné číslo, které je větší než nebo rovna hodnotě první a menší než druhý. Následující kód vybere náhodné číslo od 1 do 100 a ukládá v proměnné minuend.

     [!code-vb[VbExpressTutorial3Step5_6#21](../ide/codesnippet/VisualBasic/step-6-add-a-subtraction-problem_3.vb)]
     [!code-csharp[VbExpressTutorial3Step5_6#21](../ide/codesnippet/CSharp/step-6-add-a-subtraction-problem_3.cs)]

     Můžete volat `Next()` metoda náhodných třídy, která je s názvem "randomizer" dříve v tomto kurzu několika způsoby. Metody, které můžete volat více než jedním způsobem se označují jako přetížený a IntelliSense můžete prozkoumat je. Podívejte se na popis okno IntelliSense pro znovu `Next()` metoda.

     ![Okno IntelliSense popisu tlačítka](../ide/media/express_overloads.png)
**IntelliSense** okno popisu tlačítka

     Zobrazí popisek **(+ 2 overload(s))**, což znamená, že můžete volat `Next()` metoda dva další způsoby. Přetížení obsahovat různý počet nebo různé typy argumentů, tak, aby fungovaly trochu jinak od sebe navzájem. Například metoda může trvat celé číslo jeden argument a jeden z jeho přetížení může trvat celé číslo a řetězec. Zvolíte správné přetížení založené na co chcete udělat. Když přidáte kód, který `StartTheQuiz()` metoda, další informace se zobrazí v okně IntelliSense při zadání `randomizer.Next(`. Chcete-li procházení přetížení, zvolte **šipka nahoru** a **šipka dolů** klíče, jak je znázorněno na následujícím obrázku:

     ![Přetížení pro další&#40; &#41; metoda IntelliSense](../ide/media/express_nextoverload.png) přetížení pro **Next()** metoda v **IntelliSense**

     V takovém případě budete chtít zvolte poslední přetížení, protože můžete zadat minimální a maximální hodnoty.

3.  Změnit `CheckTheAnswer()` metodu ke kontrole správné odčítání odpověď.

     [!code-vb[VbExpressTutorial3Step5_6#14](../ide/codesnippet/VisualBasic/step-6-add-a-subtraction-problem_4.vb)]
     [!code-csharp[VbExpressTutorial3Step5_6#14](../ide/codesnippet/CSharp/step-6-add-a-subtraction-problem_4.cs)]

     V jazyce Visual C# `&&` je `logical and` operátor. V jazyce Visual Basic je ekvivalentní operátor `AndAlso`. Tyto operátory uvádí "Pokud součet addend1 a addend2 rovná hodnotě součtu NumericUpDown, a pokud minuend mínus subtrahend roven hodnotě rozdílu NumericUpDown." `CheckTheAnswer()` Metoda vrátí `true` pouze v případě, že se odpovědi na přidání a problémů odčítání správné.

4.  Poslední část obslužné rutiny události časovače značek nahraďte následujícím kódem, tak, že vyplní správnou odpověď, když vyprší čas.

     [!code-vb[VbExpressTutorial3Step5_6#22](../ide/codesnippet/VisualBasic/step-6-add-a-subtraction-problem_5.vb)]
     [!code-csharp[VbExpressTutorial3Step5_6#22](../ide/codesnippet/CSharp/step-6-add-a-subtraction-problem_5.cs)]

5.  Uložte a spusťte vašeho kódu.

     Váš program zahrnuje odčítání, jak ukazuje následující obrázek:

     ![Matematického kvízu s problém odečtení](../ide/media/express_addsubtract.png)
**matematického kvízu** s problém odečtení

## <a name="to-continue-or-review"></a>Chcete-li pokračovat nebo přezkoumat

-   Chcete-li přejít k dalšímu kroku kurzu, přečtěte si téma [krok 7: přidejte problémy násobení a dělení](../ide/step-7-add-multiplication-and-division-problems.md).

-   Chcete-li vrátit k předchozímu kroku kurzu, přečtěte si téma [krok 5: přidejte zadejte obslužných rutin událostí pro ovládací prvky NumericUpDown](../ide/step-5-add-enter-event-handlers-for-the-numericupdown-controls.md).
