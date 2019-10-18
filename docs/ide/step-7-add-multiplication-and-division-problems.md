---
title: 'Krok 7: přidejte problémy násobení a dělení'
ms.date: 11/04/2016
ms.topic: tutorial
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
dev_langs:
- CSharp
- VB
ms.assetid: e638959e-f6a4-4eb4-b2e9-f63b7855cf8f
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f02827ebd5617485f180f4a16652b1cc841c41f4
ms.sourcegitcommit: 98b02f87c7aa1f5eb7f0d1c86bfa36efa8580c57
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/15/2019
ms.locfileid: "72314229"
---
# <a name="step-7-add-multiplication-and-division-problems"></a>Krok 7: přidejte problémy násobení a dělení

V sedmé části tohoto kurzu přidáte problémy násobení a dělení, ale nejprve si myslíte, jak tuto změnu provést. Vezměte v úvahu počáteční krok, který zahrnuje ukládání hodnot.

> [!NOTE]
> Toto téma je součástí série kurzů o základních konceptech kódování.
> - Přehled tohoto kurzu najdete v tématu [kurz 2: vytvoření časovaného matematického kvízu](../ide/tutorial-2-create-a-timed-math-quiz.md).
> - Chcete-li stáhnout dokončenou verzi kódu, přečtěte si [ukázku kurzu dokončení matematického kvízu](https://code.msdn.microsoft.com/Complete-Math-Quiz-8581813c).

## <a name="to-add-multiplication-and-division-problems"></a>Přidání problémů násobení a dělení

1. Přidejte do formuláře čtyři další celočíselné proměnné.

     [!code-vb[VbExpressTutorial3Step7#15](../ide/codesnippet/VisualBasic/step-7-add-multiplication-and-division-problems_1.vb)]
     [!code-csharp[VbExpressTutorial3Step7#15](../ide/codesnippet/CSharp/step-7-add-multiplication-and-division-problems_1.cs)]

     [!INCLUDE [devlang-control-csharp-vb](./includes/devlang-control-csharp-vb.md)]

2. Jak jste předtím, upravte metodu `StartTheQuiz()` tak, aby vyplnila náhodná čísla pro problémy násobení a dělení.

     [!code-vb[VbExpressTutorial3Step7#16](../ide/codesnippet/VisualBasic/step-7-add-multiplication-and-division-problems_2.vb)]
     [!code-csharp[VbExpressTutorial3Step7#16](../ide/codesnippet/CSharp/step-7-add-multiplication-and-division-problems_2.cs)]

3. Upravte metodu `CheckTheAnswer()` tak, aby také kontrolovala problémy násobení a dělení.

     [!code-vb[VbExpressTutorial3Step7#17](../ide/codesnippet/VisualBasic/step-7-add-multiplication-and-division-problems_3.vb)]
     [!code-csharp[VbExpressTutorial3Step7#17](../ide/codesnippet/CSharp/step-7-add-multiplication-and-division-problems_3.cs)]

     Pomocí klávesnice nemůžete snadno zadat znak násobení (×) a znaménko dělení (÷), takže vizuál C# a Visual Basic přijímají pro násobení znak hvězdičky (*) a lomítko (/) pro dělení.

4. Změňte poslední část obslužné rutiny události časovače <xref:System.Windows.Forms.Timer.Tick> tak, aby vyplnila správnou odpověď, když vyprší čas.

     [!code-vb[VbExpressTutorial3Step7#23](../ide/codesnippet/VisualBasic/step-7-add-multiplication-and-division-problems_4.vb)]
     [!code-csharp[VbExpressTutorial3Step7#23](../ide/codesnippet/CSharp/step-7-add-multiplication-and-division-problems_4.cs)]

5. Uložte program a spusťte jej.

     Kvíz uživatelé vyplňující musí odpovědět na čtyři problémy, aby se dokončil kvíz, jak ukazuje následující obrázek.

     ![Math kvíz se čtyřmi problémy ](../ide/media/express_finishedquiz.png)<br/>
***Matematický kvíz*** *se čtyřmi problémy*

## <a name="to-continue-or-review"></a>Chcete-li pokračovat nebo přezkoumat

- Pokud chcete přejít na další krok kurzu, přečtěte si **[článek krok 8: Přizpůsobení kvízu](../ide/step-8-customize-the-quiz.md)** S.

- Pokud se chcete vrátit k předchozímu kroku kurzu, přečtěte si [Krok 6: Přidání problému odčítání](../ide/step-6-add-a-subtraction-problem.md).
