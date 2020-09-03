---
title: 'Krok 2: Vytvoření úlohy sčítání náhodných čísel'
ms.date: 11/04/2016
ms.topic: tutorial
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
dev_langs:
- CSharp
- VB
ms.assetid: 6461c4cf-f2aa-4bf5-91ed-06820a4f893d
author: ornellaalt
ms.author: ornella
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 2febef6987cf3440f92f6a6c505840cfe3ca3448
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "77579884"
---
# <a name="step-2-create-a-random-addition-problem"></a>Krok 2: Vytvoření úlohy sčítání náhodných čísel

V druhé části tohoto kurzu uděláte nenáročný kvíz přidáním matematických problémů, které jsou založeny na náhodných číslech. Také vytvoříte metodu s názvem, `StartTheQuiz()` která vyplní problémy a spustí časovač odpočítávání. Později v tomto kurzu přidáte problémy odčítání, násobení a dělení.

> [!NOTE]
> Toto téma je součástí série kurzů o základních konceptech kódování. Přehled tohoto kurzu najdete v tématu [kurz 2: vytvoření časovaného matematického kvízu](../ide/tutorial-2-create-a-timed-math-quiz.md).

## <a name="to-create-a-random-addition-problem"></a>Postup vytvoření náhodného přidání problému

1. V návrháři formuláře vyberte formulář (**Form1**).

2. Na panelu nabídek vyberte možnost **Zobrazit**  >  **kód**.

     *Form1.cs* nebo *Form1. vb* se zobrazí v závislosti na programovacím jazyku, který používáte, abyste mohli zobrazit kód za formulářem.

3. Vytvořte <xref:System.Random> objekt přidáním `new` příkazu poblíž horní části kódu, podobně jako následující.

     [!code-csharp[VbExpressTutorial3Step2#1](../ide/codesnippet/CSharp/step-2-create-a-random-addition-problem_1.cs)]
     [!code-vb[VbExpressTutorial3Step2#1](../ide/codesnippet/VisualBasic/step-2-create-a-random-addition-problem_1.vb)]

     [!INCLUDE [devlang-control-csharp-vb](./includes/devlang-control-csharp-vb.md)]

     Přidali jste do formuláře náhodný objekt a pojmenovali jste objekt **randomizer**.

     `Random` je označován jako objekt. Pravděpodobně jste si toto slovo už slyšeli a v dalším kurzu se dozvíte víc o tom, co znamená pro programování. Prozatím zapamatujte na to, že můžete použít `new` příkazy k vytváření tlačítek, popisků, panelů, openfiledialogch, barev, SoundPlayers, náhodných objektů a dokonce i forem a tyto položky se nazývají objekty. Když spustíte program, formulář se spustí a kód za ním vytvoří náhodný objekt a pojmenuje ho **randomizer**.

     Brzy sestavíte metodu pro kontrolu odpovědí, takže kvíz musí používat proměnné k ukládání náhodných čísel, která generuje pro každý problém. Viz [proměnné](/dotnet/visual-basic/programming-guide/language-features/variables/index) nebo [typy](/dotnet/csharp/programming-guide/types/index). Aby bylo možné správné používání proměnných, je nutné je deklarovat, což znamená, že obsahuje seznam názvů a datových typů.

4. Do formuláře přidejte dvě celočíselné proměnné a pojmenujte je **addend1** a **addend2**.

    > [!NOTE]
    > Celočíselná proměnná je označována jako int v jazyce C# nebo celé číslo v Visual Basic. Tento druh proměnné ukládá kladné nebo záporné číslo od-2147483648 do 2147483647 a může ukládat pouze celá čísla, nikoli desetinná místa.

     Podobnou syntaxi použijte k přidání celočíselné proměnné jako při přidání náhodného objektu, jak ukazuje následující kód.

     [!code-csharp[VbExpressTutorial3Step2#2](../ide/codesnippet/CSharp/step-2-create-a-random-addition-problem_2.cs)]
     [!code-vb[VbExpressTutorial3Step2#2](../ide/codesnippet/VisualBasic/step-2-create-a-random-addition-problem_2.vb)]

5. Přidejte metodu s názvem `StartTheQuiz()` a, která používá metodu náhodného objektu <xref:System.Random.Next> k zobrazení náhodných čísel v popiscích. `StartTheQuiz()` nakonec vyplní všechny problémy a potom spustí časovač, takže přidejte komentář. Funkce by měla vypadat nějak takto.

     [!code-csharp[VbExpressTutorial3Step2#3](../ide/codesnippet/CSharp/step-2-create-a-random-addition-problem_3.cs)]
     [!code-vb[VbExpressTutorial3Step2#3](../ide/codesnippet/VisualBasic/step-2-create-a-random-addition-problem_3.vb)]

     Všimněte si, že při zadání tečky (.) po `randomizer` v kódu se otevře okno IntelliSense a zobrazí se všechny metody náhodného objektu, které lze volat. Například IntelliSense Vypíše metodu následujícím `Next()` způsobem.

     ![Next – metoda](../ide/media/express_randomwhite.png)<br/>
*Next – metoda*

     Když zadáte tečku po objektu, IntelliSense zobrazí seznam členů objektu, jako jsou vlastnosti, metody a události.

    > [!NOTE]
    > Při použití `Next()` metody s `Random` objektem, například při volání `randomizer.Next(50)` , získáte náhodné číslo, které je menší než 50 (od 0 do 49). V tomto příkladu jste volali `randomizer.Next(51)` . Použili jste 51 a ne 50, aby se dvě náhodná čísla přidala k odpovědi, která je od 0 do 100. Pokud metodě předáte 50 `Next()` , zvolí číslo od 0 do 49, takže nejvyšší možná odpověď je 98, ne 100. Po prvním dvou příkazech, které jsou spuštěny v metodě, každá z těchto dvou celočíselných proměnných, **addend1** a **addend2**, drží náhodné číslo od 0 do 50. Tento snímek obrazovky ukazuje kód C#, ale IntelliSense funguje stejným způsobem jako Visual Basic.

     Prohlédněte si blíže tyto příkazy.

     [!code-csharp[VbExpressTutorial3Step2#18](../ide/codesnippet/CSharp/step-2-create-a-random-addition-problem_4.cs)]
     [!code-vb[VbExpressTutorial3Step2#18](../ide/codesnippet/VisualBasic/step-2-create-a-random-addition-problem_4.vb)]

     Příkazy nastaví vlastnosti **textu** pro **plusLeftLabel** a **plusRightLabel** tak, aby zobrazovaly dvě náhodná čísla. `ToString()`Pro převod čísel na text je nutné použít metodu celého čísla. (V programování řetězec znamená text. Ovládací prvky Label zobrazují pouze text, nikoli čísla.

6. V okně návrh dvakrát klikněte na tlačítko **Start** , nebo zvolte příkaz a stiskněte klávesu **ENTER** .

     Když si ten zvolí toto tlačítko, kvíz by měl začít a právě jste přidali obslužnou rutinu události Click pro implementaci tohoto chování.

7. Přidejte následující dva příkazy.

     [!code-csharp[VbExpressTutorial3Step2#4](../ide/codesnippet/CSharp/step-2-create-a-random-addition-problem_5.cs)]
     [!code-vb[VbExpressTutorial3Step2#4](../ide/codesnippet/VisualBasic/step-2-create-a-random-addition-problem_5.vb)]

     První příkaz volá novou `StartTheQuiz()` metodu. Druhý příkaz nastaví vlastnost **Enabled** ovládacího prvku **StartButton** na **hodnotu false** , aby autor kvízu nemohl tlačítko vybrat během kvízu.

8. Uložte kód, spusťte jej a pak klikněte na tlačítko **Start** .

     Zobrazí se náhodný problém sčítání, jak je znázorněno na následujícím snímku obrazovky.

     ![Náhodný problém sčítání](../ide/media/express_additionproblem.png)<br/>
*Náhodný problém sčítání*

     V dalším kroku kurzu přidáte součet.

## <a name="to-continue-or-review"></a>Chcete-li pokračovat nebo přezkoumat

- Pokud chcete přejít na další krok kurzu, přečtěte si **[článek krok 3: Přidání časovače odpočítávání](../ide/step-3-add-a-countdown-timer.md)**.

- Pokud se chcete vrátit k předchozímu kroku kurzu, přečtěte si téma [Krok 1: vytvoření projektu a Přidání popisků do formuláře](../ide/step-1-create-a-project-and-add-labels-to-your-form.md).
