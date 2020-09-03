---
title: 'Krok 2: vytvoření náhodného přidání problému | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
ms.assetid: 6461c4cf-f2aa-4bf5-91ed-06820a4f893d
caps.latest.revision: 29
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 54dee9c25fc9b8ddf1f8cf6c54c40d68ce53dc6a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "72671860"
---
# <a name="step-2-create-a-random-addition-problem"></a>Krok 2: Vytvořte náhodný problém s přidáním
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

V druhé části tohoto kurzu uděláte nenáročný kvíz přidáním matematických problémů, které jsou založeny na náhodných číslech. Také vytvoříte metodu s názvem, `StartTheQuiz()` která vyplní problémy a spustí časovač odpočítávání. Později v tomto kurzu přidáte problémy odčítání, násobení a dělení.

> [!NOTE]
> Toto téma je součástí série kurzů o základních konceptech kódování. Přehled tohoto kurzu najdete v tématu [kurz 2: vytvoření časovaného matematického kvízu](../ide/tutorial-2-create-a-timed-math-quiz.md).

### <a name="to-create-a-random-addition-problem"></a>Postup vytvoření náhodného přidání problému

1. V návrháři formuláře vyberte formulář (Form1).

2. Na panelu nabídek vyberte možnost **zobrazení**, **kód**.

     Form1.cs nebo Form1. vb se zobrazí v závislosti na programovacím jazyku, který používáte, abyste mohli zobrazit kód za formulářem.

3. Vytvořte `Random` objekt přidáním `new` příkazu poblíž horní části kódu, podobně jako následující.

     [!code-csharp[VbExpressTutorial3Step2#1](../snippets/csharp/VS_Snippets_VBCSharp/vbexpresstutorial3step2/cs/form1.cs#1)]
     [!code-vb[VbExpressTutorial3Step2#1](../snippets/visualbasic/VS_Snippets_VBCSharp/vbexpresstutorial3step2/vb/form1.vb#1)]

     Přidali jste `Random` objekt do formuláře a jmenovali jste objekt **randomizer**.

     `Random` je označován jako objekt. Pravděpodobně jste si toto slovo už slyšeli a v dalším kurzu se dozvíte víc o tom, co znamená pro programování. Prozatím zapamatujte na to, že můžete použít `new` příkazy k vytváření tlačítek, popisků, panelů, openfiledialogch, barev, SoundPlayers, náhodných objektů a dokonce i forem a tyto položky se nazývají objekty. Když spustíte program, formulář se spustí a kód za ním vytvoří `Random` objekt a pojmenuje ho **randomizer**.

     Brzy sestavíte metodu pro kontrolu odpovědí, takže kvíz musí používat proměnné k ukládání náhodných čísel, která generuje pro každý problém. Viz [proměnné](https://msdn.microsoft.com/library/4cfaa06d-4ae3-4307-897b-cf599dc24caa) nebo [typy](https://msdn.microsoft.com/library/f782d7cc-035e-4500-b1b1-36a9881130ad). Aby bylo možné správné používání proměnných, je nutné je deklarovat, což znamená, že obsahuje seznam názvů a datových typů.

4. Do formuláře přidejte dvě celočíselné proměnné a pojmenujte je **addend1** a **addend2**.

    > [!NOTE]
    > Celočíselná proměnná je označována jako int v jazyce C# nebo celé číslo v Visual Basic. Tento druh proměnné ukládá kladné nebo záporné číslo od-2147483648 do 2147483647 a může ukládat pouze celá čísla, nikoli desetinná místa.

     Podobnou syntaxi použijte k přidání celočíselné proměnné jako při přidání `Random` objektu, jak ukazuje následující kód.

     [!code-csharp[VbExpressTutorial3Step2#2](../snippets/csharp/VS_Snippets_VBCSharp/vbexpresstutorial3step2/cs/form1.cs#2)]
     [!code-vb[VbExpressTutorial3Step2#2](../snippets/visualbasic/VS_Snippets_VBCSharp/vbexpresstutorial3step2/vb/form1.vb#2)]

5. Přidejte metodu s názvem `StartTheQuiz()` a, která používá `Random` `Next()` metodu objektu k zobrazení náhodných čísel v popiscích. `StartTheQuiz()` nakonec vyplní všechny problémy a potom spustí časovač, takže přidejte komentář. Funkce by měla vypadat nějak takto.

     [!code-csharp[VbExpressTutorial3Step2#3](../snippets/csharp/VS_Snippets_VBCSharp/vbexpresstutorial3step2/cs/form1.cs#3)]
     [!code-vb[VbExpressTutorial3Step2#3](../snippets/visualbasic/VS_Snippets_VBCSharp/vbexpresstutorial3step2/vb/form1.vb#3)]

     Všimněte si, že při zadání tečky (.) po **randomizaci** v kódu se otevře okno technologie IntelliSense a zobrazí se všechny `Random` metody objektu, které lze volat. Například IntelliSense Vypíše metodu následujícím `Next()` způsobem.

     ![Next – metoda](../ide/media/express-randomwhite.png "Express_RandomWhite") Next – metoda

     Když zadáte tečku po objektu, IntelliSense zobrazí seznam členů objektu, jako jsou vlastnosti, metody a události.

    > [!NOTE]
    > Při použití `Next()` metody s `Random` objektem, například při volání `randomizer.Next(50)` , získáte náhodné číslo, které je menší než 50 (od 0 do 49). V tomto příkladu jste volali `randomizer.Next(51)` . Použili jste 51 a ne 50, aby se dvě náhodná čísla přidala k odpovědi, která je od 0 do 100. Pokud metodě předáte 50 `Next()` , zvolí číslo od 0 do 49, takže nejvyšší možná odpověď je 98, ne 100. Po prvním dvou příkazech v metodě se spustí každá ze dvou celočíselných proměnných a pak `addend1` `addend2` bude obsahovat náhodné číslo od 0 do 50. Tento snímek obrazovky ukazuje kód jazyka Visual C#, ale IntelliSense funguje stejným způsobem jako Visual Basic.

     Prohlédněte si blíže tyto příkazy.

     [!code-csharp[VbExpressTutorial3Step2#18](../snippets/csharp/VS_Snippets_VBCSharp/vbexpresstutorial3step2/cs/form1.cs#18)]
     [!code-vb[VbExpressTutorial3Step2#18](../snippets/visualbasic/VS_Snippets_VBCSharp/vbexpresstutorial3step2/vb/form1.vb#18)]

     Příkazy nastaví vlastnosti **textu** pro **plusLeftLabel** a **plusRightLabel** tak, aby zobrazovaly dvě náhodná čísla. `ToString()`Pro převod čísel na text je nutné použít metodu celého čísla. (V programování řetězec znamená text. Ovládací prvky Label zobrazují pouze text, nikoli čísla.

6. V okně návrh dvakrát klikněte na tlačítko **Start** , nebo zvolte příkaz a stiskněte klávesu ENTER.

     Když si ten zvolí toto tlačítko, kvíz by měl začít a právě jste přidali obslužnou rutinu události Click pro implementaci tohoto chování.

7. Přidejte následující dva příkazy.

     [!code-csharp[VbExpressTutorial3Step2#4](../snippets/csharp/VS_Snippets_VBCSharp/vbexpresstutorial3step2/cs/form1.cs#4)]
     [!code-vb[VbExpressTutorial3Step2#4](../snippets/visualbasic/VS_Snippets_VBCSharp/vbexpresstutorial3step2/vb/form1.vb#4)]

     První příkaz volá novou `StartTheQuiz()` metodu. Druhý příkaz nastaví vlastnost **Enabled** ovládacího prvku **StartButton** na **hodnotu false** , aby autor kvízu nemohl tlačítko vybrat během kvízu.

8. Uložte kód, spusťte jej a pak klikněte na tlačítko **Start** .

     Zobrazí se náhodný problém sčítání, jak ukazuje následující obrázek.

     ![Náhodný problém sčítání](../ide/media/express-additionproblem.png "Express_AdditionProblem") Náhodný problém sčítání

     V dalším kroku kurzu přidáte součet.

### <a name="to-continue-or-review"></a>Chcete-li pokračovat nebo přezkoumat

- Pokud chcete přejít na další krok kurzu, přečtěte si [článek krok 3: Přidání časovače odpočítávání](../ide/step-3-add-a-countdown-timer.md).

- Pokud se chcete vrátit k předchozímu kroku kurzu, přečtěte si téma [Krok 1: vytvoření projektu a Přidání popisků do formuláře](../ide/step-1-create-a-project-and-add-labels-to-your-form.md).
