---
title: 'Krok 4: Přidání metody CheckTheAnswer()'
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
ms.assetid: c66f3831-b4a0-40bc-a109-8f46f4db35ed
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 8c40150c3fbcd07abfad4a10155722750cbe4849
ms.sourcegitcommit: 0e482cfc15f809b564c3de61646f29ecd7bfcba6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/14/2019
ms.locfileid: "70987699"
---
# <a name="step-4-add-the-checktheanswer-method"></a>Krok 4: Přidání metody CheckTheAnswer()

Ve čtvrté části tohoto kurzu napíšete metodu `CheckTheAnswer()`, která určuje, zda jsou odpovědi na matematické problémy správné. Toto téma je součástí série kurzů o základních konceptech kódování. Přehled tohoto kurzu najdete v [kurzu 2: Vytvoření časovaného matematického](../ide/tutorial-2-create-a-timed-math-quiz.md)kvízu

> [!NOTE]
> Toto téma je součástí série kurzů o základních konceptech kódování. 
> - Přehled tohoto kurzu najdete v [kurzu 2: Vytvoření časovaného matematického](../ide/tutorial-2-create-a-timed-math-quiz.md)kvízu 
> - Chcete-li stáhnout dokončenou verzi kódu, přečtěte si [ukázku kurzu dokončení matematického kvízu](https://code.msdn.microsoft.com/Complete-Math-Quiz-8581813c).

## <a name="to-verify-whether-the-answers-are-correct"></a>Ověření, zda jsou odpovědi správné

> [!NOTE]
> Pokud sledujete v Visual Basic, použijete `Function` místo obvyklého `Sub` klíčového slova klíčové slovo, protože tato metoda vrací hodnotu. Je to opravdu jednoduché: procedura Sub nevrací hodnotu, ale funkce.

1. `CheckTheAnswer()` Přidejte metodu.

     Při volání této metody přidá hodnoty addend1 a addend2 a porovná výsledek s hodnotou v ovládacím prvku Sum <xref:System.Windows.Forms.NumericUpDown> . Pokud jsou hodnoty stejné, metoda vrátí hodnotu `true`. V opačném případě metoda vrátí hodnotu `false`. Váš kód by měl vypadat takto.

     [!code-vb[VbExpressTutorial3Step4#8](../ide/codesnippet/VisualBasic/step-4-add-the-checktheanswer-parens-method_1.vb)]
     [!code-csharp[VbExpressTutorial3Step4#8](../ide/codesnippet/CSharp/step-4-add-the-checktheanswer-parens-method_1.cs)]

     > [!IMPORTANT]
     > Pomocí ovládacího prvku programovací jazyk v pravém horním rohu této stránky můžete zobrazit fragment C# kódu nebo Visual Basic fragment kódu.<br><br>![Řízení programovacího jazyka pro Docs.Microsoft.com](../ide/media/docs-programming-language-control.png)

     V dalším kroku zkontrolujete odpověď tím, že aktualizujete kód v metodě obslužné rutiny <xref:System.Windows.Forms.Timer.Tick> události časovače k volání nové `CheckTheAnswer()` metody.

2. Do `if else` příkazu přidejte následující kód.

     [!code-vb[VbExpressTutorial3Step4#10](../ide/codesnippet/VisualBasic/step-4-add-the-checktheanswer-parens-method_2.vb)]
     [!code-csharp[VbExpressTutorial3Step4#10](../ide/codesnippet/CSharp/step-4-add-the-checktheanswer-parens-method_2.cs)]

     Pokud je odpověď správná, `CheckTheAnswer()` vrátí. `true` Obslužná rutina události zastaví časovač, zobrazí zprávu congratulatory a pak znovu zpřístupní tlačítko **Start** . V opačném případě kvíz pokračuje.

3. Uložte program, spusťte jej, spusťte kvíz a poskytněte správnou odpověď na problém sčítání.

    > [!NOTE]
    > Když zadáte odpověď, musíte buď vybrat výchozí hodnotu, než začnete zadávat odpověď, nebo musíte nulu odstranit ručně. Toto chování opravíte později v tomto kurzu.

     Když zadáte správnou odpověď, otevře se okno se zprávou, tlačítko **Start** bude k dispozici a časovač se zastaví.

## <a name="to-continue-or-review"></a>Chcete-li pokračovat nebo přezkoumat

- Pokud chcete přejít na další krok kurzu, přečtěte si  **[krok 5: Přidejte obslužné rutiny událostí Enter pro ovládací](../ide/step-5-add-enter-event-handlers-for-the-numericupdown-controls.md)prvky**NumericUpDown.

- Pokud se chcete vrátit k předchozímu kroku kurzu [, podívejte se na krok 3: Přidejte časovač](../ide/step-3-add-a-countdown-timer.md)odpočítávání.
