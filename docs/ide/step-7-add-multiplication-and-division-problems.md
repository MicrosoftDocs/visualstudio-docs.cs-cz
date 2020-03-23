---
title: 'Krok 7: Přidání problémů s násobením a dělením'
ms.date: 11/04/2016
ms.topic: tutorial
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
dev_langs:
- CSharp
- VB
ms.assetid: e638959e-f6a4-4eb4-b2e9-f63b7855cf8f
author: ornellaalt
ms.author: ornella
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 92a1744b68ad043dcee21dcb5995fbd1908bd81b
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/20/2020
ms.locfileid: "77579775"
---
# <a name="step-7-add-multiplication-and-division-problems"></a>Krok 7: Přidání problémů s násobením a dělením

V sedmé části tohoto kurzu přidáte problémy násobení a dělení, ale nejprve přemýšlet o tom, jak tuto změnu provést. Zvažte počáteční krok, který zahrnuje ukládání hodnot.

> [!NOTE]
> Toto téma je součástí série kurzů o základních konceptech kódování. Přehled kurzu najdete v [tématu Výuka 2: Vytvoření časovaného matematického kvízu](../ide/tutorial-2-create-a-timed-math-quiz.md).

## <a name="to-add-multiplication-and-division-problems"></a>Přidání problémů s násobením a dělením

1. Přidejte do formuláře další čtyři celé proměnné.

     [!code-vb[VbExpressTutorial3Step7#15](../ide/codesnippet/VisualBasic/step-7-add-multiplication-and-division-problems_1.vb)]
     [!code-csharp[VbExpressTutorial3Step7#15](../ide/codesnippet/CSharp/step-7-add-multiplication-and-division-problems_1.cs)]

     [!INCLUDE [devlang-control-csharp-vb](./includes/devlang-control-csharp-vb.md)]

2. Stejně jako dříve `StartTheQuiz()` upravte metodu tak, aby vyplnila náhodná čísla pro problémy s násobením a dělením.

     [!code-vb[VbExpressTutorial3Step7#16](../ide/codesnippet/VisualBasic/step-7-add-multiplication-and-division-problems_2.vb)]
     [!code-csharp[VbExpressTutorial3Step7#16](../ide/codesnippet/CSharp/step-7-add-multiplication-and-division-problems_2.cs)]

3. Upravte `CheckTheAnswer()` metodu tak, aby také kontroluje problémy násobení a dělení.

     [!code-vb[VbExpressTutorial3Step7#17](../ide/codesnippet/VisualBasic/step-7-add-multiplication-and-division-problems_3.vb)]
     [!code-csharp[VbExpressTutorial3Step7#17](../ide/codesnippet/CSharp/step-7-add-multiplication-and-division-problems_3.cs)]

     Nelze snadno zadat násobení znaménko (×) a znaménko dělení (÷) pomocí klávesnice, takže C# a Visual Basic přijmout hvězdičku (*) pro násobení a lomítko (/) pro dělení.

4. Změňte poslední část obslužné <xref:System.Windows.Forms.Timer.Tick> rutiny události časovače tak, aby vyplnila správnou odpověď, když vyprší čas.

     [!code-vb[VbExpressTutorial3Step7#23](../ide/codesnippet/VisualBasic/step-7-add-multiplication-and-division-problems_4.vb)]
     [!code-csharp[VbExpressTutorial3Step7#23](../ide/codesnippet/CSharp/step-7-add-multiplication-and-division-problems_4.cs)]

5. Uložte program a spusťte jej.

     Účastníci kvízu musí odpovědět na čtyři problémy, aby dokončili kvíz, jak ukazuje následující obrázek.

     ![Matematický kvíz se čtyřmi problémy](../ide/media/express_finishedquiz.png)<br/>
***Matematický kvíz se*** *čtyřmi problémy*

## <a name="to-continue-or-review"></a>Chcete-li pokračovat nebo přezkoumat

- Další krok kurzu najdete v **[tématu Krok 8: Přizpůsobení kvízu](../ide/step-8-customize-the-quiz.md)**.

- Chcete-li se vrátit k předchozímu kroku kurzu, [přečtěte si následující krok 6: Přidání problému s odčítáním](../ide/step-6-add-a-subtraction-problem.md).
