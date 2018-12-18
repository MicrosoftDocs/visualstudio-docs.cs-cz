---
title: 'Krok 2: Vytvořte náhodný problém s přidáním'
ms.custom: ''
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-acquisition
ms.topic: conceptual
ms.assetid: 6461c4cf-f2aa-4bf5-91ed-06820a4f893d
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: abd70e53c06da53f22bcac4c7f041aaef75bd412
ms.sourcegitcommit: 58052c29fc61c9a1ca55a64a63a7fdcde34668a4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2018
ms.locfileid: "34747864"
---
# <a name="step-2-create-a-random-addition-problem"></a>Krok 2: Vytvořte náhodný problém s přidáním
V druhé části tohoto kurzu provedete kvízu náročné přidáním matematické úlohy, které jsou založeny na náhodných čísel. Můžete také vytvořit metodu, která je s názvem `StartTheQuiz()` a který vyplní úlohy a spustí časovač odpočítávání. Později v tomto kurzu přidáte odčítání, násobení a dělení problémy.

> [!NOTE]
>  Toto téma je součástí série, kurz o základních konceptech kódování. Přehled kurzu, najdete v tématu [kurzu 2: vytvoření matematického kvízu](../ide/tutorial-2-create-a-timed-math-quiz.md).

## <a name="to-create-a-random-addition-problem"></a>Chcete-li vytvořit náhodný problém s přidáním

1.  V návrháři formuláře zvolte formuláře (**Form1**).

2.  Na řádku nabídek zvolte **zobrazení** > **kód**.

     *Form1.cs* nebo *Form1.vb* se zobrazí, v závislosti na programovací jazyk, který používáte, takže můžete zobrazit kód formuláře.

3.  Vytvoření <xref:System.Random> objekt přidáním `new` příkaz v horní části kódu, jako je následující.

     [!code-csharp[VbExpressTutorial3Step2#1](../ide/codesnippet/CSharp/step-2-create-a-random-addition-problem_1.cs)]
     [!code-vb[VbExpressTutorial3Step2#1](../ide/codesnippet/VisualBasic/step-2-create-a-random-addition-problem_1.vb)]

     Jste přidali do svého formuláře Random objekt a s názvem objektu **randomizer**.

     `Random` je známý jako objekt. Pravděpodobně jste slyšeli dané slovo před, a další informace o tom, co je pro programování v dalším kurzu. Prozatím se jenom nezapomeňte, že můžete používat `new` příkazy k vytvoření tlačítka, popisky, panelů, OpenFileDialogs, ColorDialogs, SoundPlayers, Randoms a také formulářů a tyto položky jsou označovány jako objekty. Když spusťte svůj program, spuštění formuláře a kódu na pozadí se vytvoří náhodný objekt a pojmenuje ji **randomizer**.

     Brzy budete sestavení metody zkontrolujte odpovědi, takže vaše kvízu s časovým limitem musí používat proměnné pro uložení náhodná čísla, který ho generuje pro každou problém. V tématu [proměnné](/dotnet/visual-basic/programming-guide/language-features/variables/index) nebo [typy](/dotnet/csharp/programming-guide/types/index). Odpovídajícím způsobem používat proměnné, musíte deklarovat, což znamená, že výpis jejich názvy a datové typy.

4.  Přidejte do formuláře dvě proměnné celé číslo a název je **addend1** a **addend2**.

    > [!NOTE]
    >  Proměnná s celým číslem se označuje jako int v C# nebo celé číslo v jazyce Visual Basic. Tento druh proměnné ukládá kladné a záporné číslo od -2147483648 až 2147483647 a můžete uložit jenom celá čísla, nikoli desetinná místa.

     Pomocí podobné syntaxe přidáte proměnná typu integer, jako jste to udělali přidejte náhodný objekt jako následující kód.

     [!code-csharp[VbExpressTutorial3Step2#2](../ide/codesnippet/CSharp/step-2-create-a-random-addition-problem_2.cs)]
     [!code-vb[VbExpressTutorial3Step2#2](../ide/codesnippet/VisualBasic/step-2-create-a-random-addition-problem_2.vb)]

5.  Přidejte metodu, která je s názvem `StartTheQuiz()` a náhodných objekt, který používá <xref:System.Random.Next> metoda zobrazíte náhodná čísla v štítky. `StartTheQuiz()` bude nakonec vyplní všechny problémy a pak spustit časovač, proto přidejte komentář. Funkce by měla vypadat podobně jako tento.

     [!code-csharp[VbExpressTutorial3Step2#3](../ide/codesnippet/CSharp/step-2-create-a-random-addition-problem_3.cs)]
     [!code-vb[VbExpressTutorial3Step2#3](../ide/codesnippet/VisualBasic/step-2-create-a-random-addition-problem_3.vb)]

     Všimněte si, že když zadáte tečku (.) po `randomizer` v kódu, otevře okno technologie IntelliSense a jsou zobrazeny všechny objekt náhodných metody, které můžete volat. Například IntelliSense zobrazí seznam `Next()` metoda následujícím způsobem.

     ![Next – metoda](../ide/media/express_randomwhite.png) Next – metoda

     Když zadáte tečku po objekt, IntelliSense zobrazí seznam členů objektu, například vlastnosti, metod a události.

    > [!NOTE]
    >  Při použití `Next()` metoda s `Random` objektu, například při volání `randomizer.Next(50)`, získat náhodné číslo, které je menší než 50 (od 0 do 49). V tomto příkladu jste volali metodu `randomizer.Next(51)`. 51 a nikoli 50 použít tak, aby dvě náhodná čísla přidá do odpovědi, která je od 0 do 100. Pokud předáte 50 až `Next()` metody zvolí číslo od 0 až 49, takže nejvyšší možná odpověď je 98, ne 100. Po spuštění první dva příkazy v metodě, každý z celé číslo dvě proměnné, **addend1** a **addend2**, podržte náhodné číslo od 0 do 50. Tento snímek obrazovky ukazuje kód jazyka Visual C#, ale IntelliSense v jazyce Visual Basic funguje stejným způsobem.

     Prohlédněte si blíže tyto příkazy.

     [!code-csharp[VbExpressTutorial3Step2#18](../ide/codesnippet/CSharp/step-2-create-a-random-addition-problem_4.cs)]
     [!code-vb[VbExpressTutorial3Step2#18](../ide/codesnippet/VisualBasic/step-2-create-a-random-addition-problem_4.vb)]

     Sadu příkazů **Text** vlastnosti **plusLeftLabel** a **plusRightLabel** tak, aby se zobrazují dvě náhodná čísla. Je nutné použít na celé číslo `ToString()` metodu k převedení čísel na text. (V programování, znamená textový řetězec. Popisek – ovládací prvky zobrazení pouze textu, nikoli čísla.

6.  V okně návrhu buď klikněte dvakrát na **spustit** tlačítko, nebo zvolte jej a potom zvolte **Enter** klíč.

     Když kvízu s časovým limitem příjemce rozhodne toto tlačítko, by se měl spustit kvízu a jste právě přidali obslužnou rutinu události kliknutí k implementaci tohoto chování.

7.  Přidejte následující dva příkazy.

     [!code-csharp[VbExpressTutorial3Step2#4](../ide/codesnippet/CSharp/step-2-create-a-random-addition-problem_5.cs)]
     [!code-vb[VbExpressTutorial3Step2#4](../ide/codesnippet/VisualBasic/step-2-create-a-random-addition-problem_5.vb)]

     První příkaz volá novou `StartTheQuiz()` metoda. Druhý příkaz nastaví **povoleno** vlastnost **startButton** řídit k **False** tak, aby příjemce kvízu s časovým limitem nemůžete vybrat tlačítko během kvízu.

8.  Uložit kódu, spusťte ji a pak zvolte **spustit** tlačítko.

     Zobrazí se náhodný problém s přidáním, jak ukazuje následující obrázek.

     ![Náhodný problém s přidáním](../ide/media/express_additionproblem.png) náhodných sčítání

     V dalším kroku kurzu přidáte součet.

## <a name="to-continue-or-review"></a>Chcete-li pokračovat nebo přezkoumat

-   Chcete-li přejít k dalšímu kroku kurzu, přečtěte si téma [krok 3: přidejte časovač odpočítávání](../ide/step-3-add-a-countdown-timer.md).

-   Chcete-li vrátit k předchozímu kroku kurzu, přečtěte si téma [krok 1: Vytvořte projekt a přidejte do svého formuláře popisky](../ide/step-1-create-a-project-and-add-labels-to-your-form.md).
