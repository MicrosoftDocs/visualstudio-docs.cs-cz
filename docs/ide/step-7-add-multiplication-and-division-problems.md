---
title: 'Krok 7: Přidání úloh násobení a dělení'
description: Přečtěte si, jak přidat problémy násobení a dělení.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 20d39f6694f0e5a05a220206d8d34ad3bb65946a
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99868865"
---
# <a name="step-7-add-multiplication-and-division-problems"></a>Krok 7: Přidání úloh násobení a dělení

V sedmé části tohoto kurzu přidáte problémy násobení a dělení, ale nejprve si myslíte, jak tuto změnu provést. Vezměte v úvahu počáteční krok, který zahrnuje ukládání hodnot.

> [!NOTE]
> Toto téma je součástí série kurzů o základních konceptech kódování. Přehled tohoto kurzu najdete v tématu [kurz 2: vytvoření časovaného matematického kvízu](../ide/tutorial-2-create-a-timed-math-quiz.md).

## <a name="to-add-multiplication-and-division-problems"></a>Přidání problémů násobení a dělení

1. Přidejte do formuláře čtyři další celočíselné proměnné.

     [!code-vb[VbExpressTutorial3Step7#15](../ide/codesnippet/VisualBasic/step-7-add-multiplication-and-division-problems_1.vb)]
     [!code-csharp[VbExpressTutorial3Step7#15](../ide/codesnippet/CSharp/step-7-add-multiplication-and-division-problems_1.cs)]

     [!INCLUDE [devlang-control-csharp-vb](./includes/devlang-control-csharp-vb.md)]

2. Jak jste předtím, upravte `StartTheQuiz()` metodu tak, aby vyplnila náhodná čísla pro problémy násobení a dělení.

     [!code-vb[VbExpressTutorial3Step7#16](../ide/codesnippet/VisualBasic/step-7-add-multiplication-and-division-problems_2.vb)]
     [!code-csharp[VbExpressTutorial3Step7#16](../ide/codesnippet/CSharp/step-7-add-multiplication-and-division-problems_2.cs)]

3. Upravte `CheckTheAnswer()` metodu tak, aby také kontrolovala problémy násobení a dělení.

     [!code-vb[VbExpressTutorial3Step7#17](../ide/codesnippet/VisualBasic/step-7-add-multiplication-and-division-problems_3.vb)]
     [!code-csharp[VbExpressTutorial3Step7#17](../ide/codesnippet/CSharp/step-7-add-multiplication-and-division-problems_3.cs)]

     Pomocí klávesnice nemůžete snadno zadat znaménko násobení (×) a symbol dělení (÷), takže C# a Visual Basic přijímají pro násobení znak hvězdičky (*) a lomítko (/) pro dělení.

4. Změňte poslední část <xref:System.Windows.Forms.Timer.Tick> obslužné rutiny události časovače tak, aby vyplnila správnou odpověď, když vyprší čas.

     [!code-vb[VbExpressTutorial3Step7#23](../ide/codesnippet/VisualBasic/step-7-add-multiplication-and-division-problems_4.vb)]
     [!code-csharp[VbExpressTutorial3Step7#23](../ide/codesnippet/CSharp/step-7-add-multiplication-and-division-problems_4.cs)]

5. Uložte program a spusťte jej.

     Kvíz uživatelé vyplňující musí odpovědět na čtyři problémy, aby se dokončil kvíz, jak ukazuje následující obrázek.

     ![Matematický kvíz se čtyřmi problémy](../ide/media/express_finishedquiz.png)<br/>
***Matematický kvíz** _ _with čtyři problémy *

## <a name="to-continue-or-review"></a>Chcete-li pokračovat nebo přezkoumat

- Pokud chcete přejít na další krok kurzu, přečtěte si **[článek krok 8: Přizpůsobení kvízu](../ide/step-8-customize-the-quiz.md)**.

- Pokud se chcete vrátit k předchozímu kroku kurzu, přečtěte si [Krok 6: Přidání problému odčítání](../ide/step-6-add-a-subtraction-problem.md).
