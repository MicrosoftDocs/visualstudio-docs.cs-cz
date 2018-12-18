---
title: 'Krok 2: Vytvořte náhodný problém s přidáním | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 6461c4cf-f2aa-4bf5-91ed-06820a4f893d
caps.latest.revision: 29
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 47429cb995dd7374276a9e2872d1b80ed452281a
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/12/2018
ms.locfileid: "49204370"
---
# <a name="step-2-create-a-random-addition-problem"></a>Krok 2: Vytvořte náhodný problém s přidáním
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

V druhé části tohoto kurzu je náročnější kvíz přidáním matematických úlohy, které jsou založeny na náhodných čísel. Také vytvořit metoda s názvem `StartTheQuiz()` a která vyplní úlohy a spustí časovač odpočítávání. Později v tomto kurzu přidáte odčítání, násobení a dělení.  
  
> [!NOTE]
>  Toto téma je součástí série kurzů o základních principech kódování. Přehled kurzu, naleznete v tématu [kurz 2: vytvoření a Timed Math Quiz](../ide/tutorial-2-create-a-timed-math-quiz.md).  
  
### <a name="to-create-a-random-addition-problem"></a>Chcete-li vytvořit náhodnou úlohu sčítání  
  
1.  V Návrháři formulářů vyberte formulář (Form1).  
  
2.  V panelu nabídky zvolte **zobrazení**, **kód**.  
  
     Form1.cs nebo Form1.vb se objeví, v závislosti na programovacím jazyce, který používáte, takže můžete zobrazit kód za formulářem.  
  
3.  Vytvoření `Random` objektu tak, že přidáte `new` příkazu v horní části kódu, jako je následující.  
  
     [!code-csharp[VbExpressTutorial3Step2#1](../snippets/csharp/VS_Snippets_VBCSharp/vbexpresstutorial3step2/cs/form1.cs#1)]
     [!code-vb[VbExpressTutorial3Step2#1](../snippets/visualbasic/VS_Snippets_VBCSharp/vbexpresstutorial3step2/vb/form1.vb#1)]  
  
     Přidání `Random` objektu do formuláře a s názvem objektu **randomizer**.  
  
     `Random` je znám jako objekt. Pravděpodobně jste slyšeli toto slovo dříve, a další informace o tom, co znamená pro programování v dalším kurzu. Teď stačí mějte na paměti, které můžete použít `new` příkazy k vytvoření tlačítek, popisků, panelů, dialogů pro otevření souborů, dialogů barev, hudebních přehrávačů, náhodných položek a dokonce i formulářů a tyto položky se označují jako objekty. Když svůj program spustíte, formulář bude spuštěn a kód za ním vytvoří `Random` objektu a pojmenuje ho **randomizer**.  
  
     Brzy budete vytvářet metodu pro zkontrolování odpovědí, takže váš kvíz musí používat proměnné pro uložení náhodných čísel, která pro každý problém generují. Zobrazit [proměnné](http://msdn.microsoft.com/library/4cfaa06d-4ae3-4307-897b-cf599dc24caa) nebo [typy](http://msdn.microsoft.com/library/f782d7cc-035e-4500-b1b1-36a9881130ad). Pro správné použití proměnných, je třeba je deklarovat, což znamená vypsat jejich názvy a datové typy.  
  
4.  Do formuláře přidat dvě celočíselné proměnné a pojmenujte je **addend1** a **addend2**.  
  
    > [!NOTE]
    >  Celočíselná proměnná je označována jako int v jazyce C# nebo Integer v jazyce Visual Basic. Tento typ proměnné ukládá kladné nebo záporné číslo od -2147483648 do 2147483647 a můžete ukládat pouze celá čísla bez desetinných čísel.  
  
     Podobná syntaxe umožňuje přidat proměnnou celého čísla, jako jste přidali `Random` objektu, jak ukazuje následující kód.  
  
     [!code-csharp[VbExpressTutorial3Step2#2](../snippets/csharp/VS_Snippets_VBCSharp/vbexpresstutorial3step2/cs/form1.cs#2)]
     [!code-vb[VbExpressTutorial3Step2#2](../snippets/visualbasic/VS_Snippets_VBCSharp/vbexpresstutorial3step2/vb/form1.vb#2)]  
  
5.  Přidejte metodu s názvem `StartTheQuiz()` a, která používá `Random` objektu `Next()` metodu pro zobrazení náhodných čísel v popiscích. `StartTheQuiz()` bude nakonec vyplní všechny úlohy a pak spustí časovač, takže přidejte komentář. Funkce by měl vypadat nějak takto.  
  
     [!code-csharp[VbExpressTutorial3Step2#3](../snippets/csharp/VS_Snippets_VBCSharp/vbexpresstutorial3step2/cs/form1.cs#3)]
     [!code-vb[VbExpressTutorial3Step2#3](../snippets/visualbasic/VS_Snippets_VBCSharp/vbexpresstutorial3step2/vb/form1.vb#3)]  
  
     Všimněte si, že pokud zadáte tečku (.) po **randomizer** v kódu, okno technologie IntelliSense se otevře a zobrazí všechny `Random` metody objektu, které můžete volat. Například, Intellisense vypíše `Next()` metodu následujícím způsobem.  
  
     ![Další metoda](../ide/media/express-randomwhite.png "Express_RandomWhite")  
Next – metoda  
  
     Pokud zadáte tečku po objektu, technologie IntelliSense zobrazí seznam členů objektu, jako jsou vlastnosti, metody a události.  
  
    > [!NOTE]
    >  Při použití `Next()` metodou `Random` objektu, například při volání `randomizer.Next(50)`, získat náhodné číslo, které je menší než 50 (od 0 do 49). V tomto příkladu jste volali `randomizer.Next(51)`. Použili jste 51 a nikoli 50, aby dvě náhodná čísla sečetla pro odpověď, která je od 0 do 100. Pokud předáte 50 až `Next()` metoda, zvolí číslo od 0 do 49, takže nejvyšší možná odpověď je 98, ne 100. Po spuštění prvních dvou příkazů v metodě, každé dvě celočíselné proměnné `addend1` a `addend2`, drží náhodné číslo od 0 do 50. Tento snímek obrazovky ukazuje kód Visual C#, ale IntelliSense funguje stejným způsobem jako v jazyce Visual Basic.  
  
     Prohlédněte si blíže tyto příkazy.  
  
     [!code-csharp[VbExpressTutorial3Step2#18](../snippets/csharp/VS_Snippets_VBCSharp/vbexpresstutorial3step2/cs/form1.cs#18)]
     [!code-vb[VbExpressTutorial3Step2#18](../snippets/visualbasic/VS_Snippets_VBCSharp/vbexpresstutorial3step2/vb/form1.vb#18)]  
  
     Příkazy nastaví **Text** vlastnosti **plusLeftLabel** a **plusRightLabel** tak, aby zobrazují dvě náhodná čísla. Je nutné použít na celé číslo `ToString()` metodu k převedení čísel na text. (V programování řetězec znamená text. Ovládací prvek Label zobrazí pouze text, nikoli čísla.  
  
6.  V okně návrhu buď poklepejte **Start** tlačítko, nebo jej vyberte a stiskněte klávesu Enter.  
  
     Když kvízu zvolí toto tlačítko, kvíz by se měl spustit a vy jste právě přidali obslužnou rutinu události Click k implementaci tohoto chování.  
  
7.  Přidejte následující dva příkazy.  
  
     [!code-csharp[VbExpressTutorial3Step2#4](../snippets/csharp/VS_Snippets_VBCSharp/vbexpresstutorial3step2/cs/form1.cs#4)]
     [!code-vb[VbExpressTutorial3Step2#4](../snippets/visualbasic/VS_Snippets_VBCSharp/vbexpresstutorial3step2/vb/form1.vb#4)]  
  
     První příkaz volá novou `StartTheQuiz()` metody. Druhý příkaz nastaví **povoleno** vlastnost **startButton** mít pod kontrolou **False** tak, aby kvízu nemohl na tlačítko během kvízu.  
  
8.  Uložte svůj kód, spusťte ho a klikněte na tlačítko **Start** tlačítko.  
  
     Náhodná úloha sčítání se zobrazí, jak ukazuje následující obrázek.  
  
     ![Náhodná úloha sčítání](../ide/media/express-additionproblem.png "Express_AdditionProblem")  
Náhodná úloha sčítání  
  
     V dalším kroku výukového programu přidáte součet.  
  
### <a name="to-continue-or-review"></a>Chcete-li pokračovat nebo přezkoumat  
  
-   Přechod k dalšímu kroku výukového programu naleznete v tématu [krok 3: přidejte časovač odpočítávání](../ide/step-3-add-a-countdown-timer.md).  
  
-   Chcete-li vrátit k předchozímu kroku tutoriálu, přečtěte si téma [krok 1: Vytvořte projekt a přidat popisky na svůj formulář](../ide/step-1-create-a-project-and-add-labels-to-your-form.md).



