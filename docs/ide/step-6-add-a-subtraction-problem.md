---
title: 'Krok 6: Přidání problému s odčítáním'
ms.date: 11/04/2016
ms.topic: tutorial
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
dev_langs:
- CSharp
- VB
ms.assetid: 59204ef9-24bd-4f81-b85f-e3168e518a3e
author: ornellaalt
ms.author: ornella
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 6b6dd2b572074265cca62a45b962c604abf5c849
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/20/2020
ms.locfileid: "77579814"
---
# <a name="step-6-add-a-subtraction-problem"></a>Krok 6: Přidání problému s odčítáním
V šesté části tohoto kurzu přidáte problém odčítání a naučíte se provádět následující úkoly:

- Uložte hodnoty odčítání.

- Generovat náhodná čísla pro problém (a ujistěte se, že odpověď je mezi 0 a 100).

- Aktualizujte metodu, která kontroluje odpovědi tak, aby zkontroluje nový problém odčítání příliš.

- Aktualizujte obslužnou rutinu <xref:System.Windows.Forms.Timer.Tick> události časovače tak, aby obslužná rutina události vyplnila správnou odpověď, když vyprší čas.

> [!NOTE]
> Toto téma je součástí série kurzů o základních konceptech kódování. Přehled kurzu najdete v [tématu Výuka 2: Vytvoření časovaného matematického kvízu](../ide/tutorial-2-create-a-timed-math-quiz.md).

## <a name="to-add-a-subtraction-problem"></a>Přidání problému s odčítáním

1. Přidejte dvě celé číslo proměnné pro problém odčítání do formuláře, mezi proměnné celé číslo pro problém sčítání a časovač. Kód by měl vypadat takto.

     [!code-vb[VbExpressTutorial3Step5_6#12](../ide/codesnippet/VisualBasic/step-6-add-a-subtraction-problem_1.vb)]
     [!code-csharp[VbExpressTutorial3Step5_6#12](../ide/codesnippet/CSharp/step-6-add-a-subtraction-problem_1.cs)]

     [!INCLUDE [devlang-control-csharp-vb](./includes/devlang-control-csharp-vb.md)]

     Názvy nových proměnných celéčíslo –**minuend** a **subtrahend**– nejsou programovací termíny. Jsou to tradiční názvy v aritmetice pro číslo, které se odečítá (subtrahend) a číslo, ze kterého se odečítá subtrahend (minuend). Rozdíl je minuend mínus subtrahend. Můžete použít jiné názvy, protože program nevyžaduje konkrétní názvy pro proměnné, ovládací prvky, součásti nebo metody. Musíte dodržovat pravidla, jako jsou nepočáteční názvy s číslicemi, ale obecně můžete používat názvy jako x1, x2, x3 a x4. Obecné názvy však ztěžují čtení kódu a problémy téměř nemožné vystopovat. Chcete-li zachovat názvy proměnných jedinečné a užitečné, budete používat tradiční názvy pro násobení (multiplicand × multiplikátor = produkt) a dělení (dividenda ÷ dělitel = podíl) dále v tomto kurzu.

     Dále upravíte metodu `StartTheQuiz()` tak, aby poskytovala náhodné hodnoty pro problém odčítání.

2. Za komentář "Vyplňte problém odčítání" přidejte následující kód.

     [!code-vb[VbExpressTutorial3Step5_6#13](../ide/codesnippet/VisualBasic/step-6-add-a-subtraction-problem_2.vb)]
     [!code-csharp[VbExpressTutorial3Step5_6#13](../ide/codesnippet/CSharp/step-6-add-a-subtraction-problem_2.cs)]

     Chcete-li zabránit záporné odpovědi na <xref:System.Random.Next> problém odčítání, tento kód používá metodu <xref:System.Random> třídy trochu jinak než jak dělá problém sčítání. Když zadáte `Next()` metodu dvě hodnoty, vybere náhodné číslo, které je větší nebo rovno první hodnotě a menší než druhá. Následující kód vybere náhodné číslo od 1 do 100 a uloží jej do minuend proměnné.

     [!code-vb[VbExpressTutorial3Step5_6#21](../ide/codesnippet/VisualBasic/step-6-add-a-subtraction-problem_3.vb)]
     [!code-csharp[VbExpressTutorial3Step5_6#21](../ide/codesnippet/CSharp/step-6-add-a-subtraction-problem_3.cs)]

     Můžete volat `Next()` metodu Random třídy, kterou jste pojmenovali "randomizer" dříve v tomto kurzu, a to několika způsoby. Metody, které můžete volat více než jedním způsobem, jsou označovány jako přetížené a můžete je prozkoumat pomocí technologie IntelliSense. Podívejte se znovu na popis okna IntelliSense pro metodu. `Next()`

     ![Popis okna IntelliSense](../ide/media/express_overloads.png)<br/>
*Popis okna* ***IntelliSense***

     Popisek ukazuje **(+ 2 přetížení (y))**, což `Next()` znamená, že můžete volat metodu dvěma dalšími způsoby. Přetížení obsahují různá čísla nebo typy argumentů, takže pracují mírně odlišně od sebe navzájem. Metoda může například trvat jeden argument celé číslo a jeden z jeho přetížení může trvat celé číslo a řetězec. Můžete zvolit správné přetížení na základě toho, co chcete, aby to udělat. Když do `StartTheQuiz()` metody přidáte kód, zobrazí se v okně Technologie IntelliSense další informace, jakmile zadáte `randomizer.Next(`. Chcete-li přecházet přetížení, zvolte klávesy **šipka nahoru** a **šipka dolů,** jak je znázorněno na následujícím obrázku:

     ![Přetížení pro metodu Next&#40;&#41; v systému IntelliSense](../ide/media/express_nextoverload.png)<br/>
*Přetížení pro metodu* ***Next()*** *v* ***intelliSense***

     V takovém případě chcete zvolit poslední přetížení, protože můžete zadat minimální a maximální hodnoty.

3. Upravte `CheckTheAnswer()` metodu a zkontrolujte správnou odpověď odčítání.

     [!code-vb[VbExpressTutorial3Step5_6#14](../ide/codesnippet/VisualBasic/step-6-add-a-subtraction-problem_4.vb)]
     [!code-csharp[VbExpressTutorial3Step5_6#14](../ide/codesnippet/CSharp/step-6-add-a-subtraction-problem_4.cs)]

     V C# `&&` je `logical and` operátor. V jazyce Visual Basic `AndAlso`je ekvivalentní operátor . Tyto operátory označují "Pokud součet dodatku1 a addend2 se rovná hodnotě součet NumericUpDown a pokud minuend minus subtrahend rovná hodnotě rozdílu NumericUpDown." Metoda `CheckTheAnswer()` vrátí `true` pouze v případě, že odpovědi na sčítání a odčítání problémy jsou správné.

4. Nahraďte poslední část obslužné rutiny události Tick časovače následujícím kódem tak, aby vyplnila správnou odpověď, když vyprší čas.

     [!code-vb[VbExpressTutorial3Step5_6#22](../ide/codesnippet/VisualBasic/step-6-add-a-subtraction-problem_5.vb)]
     [!code-csharp[VbExpressTutorial3Step5_6#22](../ide/codesnippet/CSharp/step-6-add-a-subtraction-problem_5.cs)]

5. Uložte a spusťte kód.

     Program obsahuje problém s odčítáním, jak ukazuje následující obrázek:

     ![Matematický kvíz s problémem odčítání](../ide/media/express_addsubtract.png)<br/>
***Matematický kvíz*** *s problémem odčítání*

## <a name="to-continue-or-review"></a>Chcete-li pokračovat nebo přezkoumat

- Další krok kurzu najdete v **[tématu Krok 7: Přidání problémů s násobením a dělením](../ide/step-7-add-multiplication-and-division-problems.md)**.

- Chcete-li se vrátit k předchozímu kroku kurzu, [přečtěte si krok 5: Přidání obslužných rutin událostí pro ovládací prvky NumericUpDown](../ide/step-5-add-enter-event-handlers-for-the-numericupdown-controls.md).
