---
title: 'Krok 7: Přidání úloh násobení a dělení'
ms.date: 11/04/2016
ms.topic: tutorial
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
ms.devlang:
- csharp
- vb
dev_langs:
- csharp
- vb
ms.assetid: e638959e-f6a4-4eb4-b2e9-f63b7855cf8f
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 182ab3c06ef0956d6c0d97c4276a44c3f3239875
ms.sourcegitcommit: 0e482cfc15f809b564c3de61646f29ecd7bfcba6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/14/2019
ms.locfileid: "70987867"
---
# <a name="step-7-add-multiplication-and-division-problems"></a>Krok 7: Přidání úloh násobení a dělení

V sedmé části tohoto kurzu přidáte problémy násobení a dělení, ale nejprve si myslíte, jak tuto změnu provést. Vezměte v úvahu počáteční krok, který zahrnuje ukládání hodnot.

> [!NOTE]
> Toto téma je součástí série kurzů o základních konceptech kódování. 
> - Přehled tohoto kurzu najdete v [kurzu 2: Vytvoření časovaného matematického](../ide/tutorial-2-create-a-timed-math-quiz.md)kvízu 
> - Chcete-li stáhnout dokončenou verzi kódu, přečtěte si [ukázku kurzu dokončení matematického kvízu](https://code.msdn.microsoft.com/Complete-Math-Quiz-8581813c).

## <a name="to-add-multiplication-and-division-problems"></a>Přidání problémů násobení a dělení

1. Přidejte do formuláře čtyři další celočíselné proměnné.

     [!code-vb[VbExpressTutorial3Step7#15](../ide/codesnippet/VisualBasic/step-7-add-multiplication-and-division-problems_1.vb)]
     [!code-csharp[VbExpressTutorial3Step7#15](../ide/codesnippet/CSharp/step-7-add-multiplication-and-division-problems_1.cs)]

     > [!IMPORTANT]
     > Pomocí ovládacího prvku programovací jazyk v pravém horním rohu této stránky můžete zobrazit fragment C# kódu nebo Visual Basic fragment kódu.<br><br>![Řízení programovacího jazyka pro Docs.Microsoft.com](../ide/media/docs-programming-language-control.png)

2. Jak jste předtím, upravte `StartTheQuiz()` metodu tak, aby vyplnila náhodná čísla pro problémy násobení a dělení.

     [!code-vb[VbExpressTutorial3Step7#16](../ide/codesnippet/VisualBasic/step-7-add-multiplication-and-division-problems_2.vb)]
     [!code-csharp[VbExpressTutorial3Step7#16](../ide/codesnippet/CSharp/step-7-add-multiplication-and-division-problems_2.cs)]

3. `CheckTheAnswer()` Upravte metodu tak, aby také kontrolovala problémy násobení a dělení.

     [!code-vb[VbExpressTutorial3Step7#17](../ide/codesnippet/VisualBasic/step-7-add-multiplication-and-division-problems_3.vb)]
     [!code-csharp[VbExpressTutorial3Step7#17](../ide/codesnippet/CSharp/step-7-add-multiplication-and-division-problems_3.cs)]

     Pomocí klávesnice nemůžete snadno zadat znak násobení (×) a znaménko dělení (÷), takže vizuál C# a Visual Basic přijímají pro násobení znak hvězdičky (*) a lomítko (/) pro dělení.

4. Změňte poslední část obslužné rutiny <xref:System.Windows.Forms.Timer.Tick> události časovače tak, aby vyplnila správnou odpověď, když vyprší čas.

     [!code-vb[VbExpressTutorial3Step7#23](../ide/codesnippet/VisualBasic/step-7-add-multiplication-and-division-problems_4.vb)]
     [!code-csharp[VbExpressTutorial3Step7#23](../ide/codesnippet/CSharp/step-7-add-multiplication-and-division-problems_4.cs)]

5. Uložte program a spusťte jej.

     Kvíz uživatelé vyplňující musí odpovědět na čtyři problémy, aby se dokončil kvíz, jak ukazuje následující obrázek.

     ![Matematický kvíz se čtyřmi problémy](../ide/media/express_finishedquiz.png)<br/>
***Matematický kvíz*** *se čtyřmi problémy*

## <a name="to-continue-or-review"></a>Chcete-li pokračovat nebo přezkoumat

- Pokud chcete přejít na další krok kurzu, přečtěte si  **[krok 8: Přizpůsobení kvízu](../ide/step-8-customize-the-quiz.md)** S.

- Pokud se chcete vrátit k předchozímu kroku kurzu [, přečtěte si krok 6: Přidejte problém](../ide/step-6-add-a-subtraction-problem.md)odčítání.
