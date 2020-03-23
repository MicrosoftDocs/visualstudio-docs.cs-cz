---
title: 'Krok 2: Vytvoření problému náhodného přidání'
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
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/20/2020
ms.locfileid: "77579884"
---
# <a name="step-2-create-a-random-addition-problem"></a>Krok 2: Vytvoření problému náhodného přidání

Ve druhé části tohoto kurzu provedete kvíz náročný přidáním matematických problémů, které jsou založeny na náhodných číslech. Můžete také vytvořit metodu `StartTheQuiz()` s názvem a která vyplní problémy a spustí časovač odpočítávání. Později v tomto kurzu přidáte problémy odčítání, násobení a dělení.

> [!NOTE]
> Toto téma je součástí série kurzů o základních konceptech kódování. Přehled kurzu najdete v [tématu Výuka 2: Vytvoření časovaného matematického kvízu](../ide/tutorial-2-create-a-timed-math-quiz.md).

## <a name="to-create-a-random-addition-problem"></a>Chcete-li vytvořit problém náhodného přidání

1. V návrháři formuláře zvolte formulář (**Formulář1**).

2. Na řádku nabídek zvolte **Zobrazit** > **kód**.

     *Form1.cs* nebo *Form1.vb* se zobrazí v závislosti na programovacím jazyce, který používáte, takže můžete zobrazit kód za formulářem.

3. Vytvořte <xref:System.Random> objekt přidáním příkazu `new` v horní části kódu, například následující.

     [!code-csharp[VbExpressTutorial3Step2#1](../ide/codesnippet/CSharp/step-2-create-a-random-addition-problem_1.cs)]
     [!code-vb[VbExpressTutorial3Step2#1](../ide/codesnippet/VisualBasic/step-2-create-a-random-addition-problem_1.vb)]

     [!INCLUDE [devlang-control-csharp-vb](./includes/devlang-control-csharp-vb.md)]

     Do formuláře jste přidali objekt Random a pojmenovali jste **randomizátor**objektu .

     `Random`označuje jako objekt. Pravděpodobně jste slyšeli, že slovo dříve, a dozvíte se více o tom, co to znamená pro programování v příštím kurzu. Prozatím si pamatujte, že `new` příkazy můžete použít k vytvoření tlačítek, popisků, panelů, OpenFileDialogs, ColorDialogs, SoundPlayers, Randoms a dokonce i forem a tyto položky jsou označovány jako objekty. Při spuštění programu je formulář spuštěn a kód za ním vytvoří náhodný objekt a pojmenuje jej **randomizer**.

     Brzy vytvoříte metodu pro kontrolu odpovědí, takže váš kvíz musí používat proměnné pro uložení náhodných čísel, která generuje pro každý problém. Viz [Proměnné](/dotnet/visual-basic/programming-guide/language-features/variables/index) nebo [typy](/dotnet/csharp/programming-guide/types/index). Chcete-li správně používat proměnné, musíte je deklarovat, což znamená, že jsou uvedeny jejich názvy a datové typy.

4. Přidejte do formuláře dvě celé proměnné a pojmenujte je **do doplňku1** a **dodatku2**.

    > [!NOTE]
    > Celá proměnná se označuje jako int v jazyce C# nebo integer v jazyce Visual Basic. Tento druh proměnné ukládá kladné nebo záporné číslo od -2147483648 do 2147483647 a může ukládat pouze celá čísla, nikoli desetinná čísla.

     Podobnou syntaxi použijete k přidání celé proměnné, jako jste přidali náhodný objekt, jak ukazuje následující kód.

     [!code-csharp[VbExpressTutorial3Step2#2](../ide/codesnippet/CSharp/step-2-create-a-random-addition-problem_2.cs)]
     [!code-vb[VbExpressTutorial3Step2#2](../ide/codesnippet/VisualBasic/step-2-create-a-random-addition-problem_2.vb)]

5. Přidejte metodu s `StartTheQuiz()` názvem a která používá <xref:System.Random.Next> metodu Random objektu k zobrazení náhodných čísel v popiscích. `StartTheQuiz()`nakonec vyplní všechny problémy a pak spustit časovač, takže přidejte komentář. Funkce by měla vypadat takto.

     [!code-csharp[VbExpressTutorial3Step2#3](../ide/codesnippet/CSharp/step-2-create-a-random-addition-problem_3.cs)]
     [!code-vb[VbExpressTutorial3Step2#3](../ide/codesnippet/VisualBasic/step-2-create-a-random-addition-problem_3.vb)]

     Všimněte si, že když zadáte `randomizer` tečku (.) po v kódu, otevře se okno IntelliSense a zobrazí všechny metody random objektu, které můžete volat. Například Technologie IntelliSense `Next()` uvádí metodu následujícím způsobem.

     ![Další metoda](../ide/media/express_randomwhite.png)<br/>
*Další metoda*

     Když zadáte tečku za objektem, technologie IntelliSense zobrazí seznam členů objektu, například vlastnosti, metody a události.

    > [!NOTE]
    > Při použití `Next()` metody s `Random` objektem, například `randomizer.Next(50)`při volání , dostanete náhodné číslo, které je menší než 50 (od 0 do 49). V tomto příkladu `randomizer.Next(51)`jste zavolali . Použili jste 51 a ne 50, takže dvě náhodná čísla se sčítají s odpovědí, která je od 0 do 100. Pokud předáte metodě `Next()` 50, zvolí číslo od 0 do 49, takže nejvyšší možná odpověď je 98, nikoli 100. Po prvních dvou příkazech v metodě run, každý ze dvou celé proměnné, **addend1** a **addend2**, držet náhodné číslo od 0 do 50. Tento snímek obrazovky zobrazuje kód Jazyka C#, ale technologie IntelliSense funguje stejným způsobem pro jazyk Visual Basic.

     Podívejte se blíže na tato prohlášení.

     [!code-csharp[VbExpressTutorial3Step2#18](../ide/codesnippet/CSharp/step-2-create-a-random-addition-problem_4.cs)]
     [!code-vb[VbExpressTutorial3Step2#18](../ide/codesnippet/VisualBasic/step-2-create-a-random-addition-problem_4.vb)]

     Příkazy nastavit **vlastnosti Text** **plusLeftLabel** a **plusRightLabel** tak, aby se zobrazí dvě náhodná čísla. Chcete-li převést čísla `ToString()` na text, je nutné použít metodu celého čísla. (V programování řetězec znamená text. Ovládací prvky popisků zobrazují pouze text, nikoli čísla.

6. V okně návrhu poklepejte na tlačítko **Start** nebo zvolte a pak zvolte **enter.**

     Když příjemce kvízu vybere toto tlačítko, kvíz by měl začít a právě jste přidali obslužnou rutinu události Click, která toto chování implementuje.

7. Přidejte následující dva příkazy.

     [!code-csharp[VbExpressTutorial3Step2#4](../ide/codesnippet/CSharp/step-2-create-a-random-addition-problem_5.cs)]
     [!code-vb[VbExpressTutorial3Step2#4](../ide/codesnippet/VisualBasic/step-2-create-a-random-addition-problem_5.vb)]

     První příkaz volá `StartTheQuiz()` novou metodu. Druhý příkaz nastaví **Povoleno** vlastnost ovládacího prvku **startButton** na **False** tak, aby příjemce kvízu nelze vybrat tlačítko během kvízu.

8. Uložte kód, spusťte ho a pak zvolte tlačítko **Start.**

     Objeví se problém s náhodným přidáním, jak je znázorněno na následujícím snímku obrazovky.

     ![Problém náhodného sčítání](../ide/media/express_additionproblem.png)<br/>
*Problém náhodného sčítání*

     V dalším kroku kurzu přidáte částku.

## <a name="to-continue-or-review"></a>Chcete-li pokračovat nebo přezkoumat

- Pokud chcete přejít k dalšímu kroku kurzu, **[přečtěte si krok 3: Přidání časovače odpočítávání](../ide/step-3-add-a-countdown-timer.md)**.

- Chcete-li se vrátit k předchozímu kroku kurzu, [přečtěte si následující krok 1: Vytvoření projektu a přidání popisků do formuláře](../ide/step-1-create-a-project-and-add-labels-to-your-form.md).
