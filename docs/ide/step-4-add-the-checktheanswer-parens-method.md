---
title: 'Krok 4: Přidání metody CheckTheAnswer()'
description: Naučte se psát metodu metodu CheckTheAnswer (), abyste zjistili, jestli jsou odpovědi na matematické problémy správné.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: tutorial
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
dev_langs:
- CSharp
- VB
ms.assetid: c66f3831-b4a0-40bc-a109-8f46f4db35ed
author: ornellaalt
ms.author: ornella
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: f6e52d415b4278a04e559c64cdcfac86cdf22261
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99950702"
---
# <a name="step-4-add-the-checktheanswer-method"></a>Krok 4: Přidání metody CheckTheAnswer()

Ve čtvrté části tohoto kurzu napíšete metodu, `CheckTheAnswer()` která určuje, zda jsou odpovědi na matematické problémy správné. Toto téma je součástí série kurzů o základních konceptech kódování. Přehled tohoto kurzu najdete v tématu [kurz 2: vytvoření časovaného matematického kvízu](../ide/tutorial-2-create-a-timed-math-quiz.md).

> [!NOTE]
> Toto téma je součástí série kurzů o základních konceptech kódování. Přehled tohoto kurzu najdete v tématu [kurz 2: vytvoření časovaného matematického kvízu](../ide/tutorial-2-create-a-timed-math-quiz.md).

## <a name="to-verify-whether-the-answers-are-correct"></a>Ověření, zda jsou odpovědi správné

> [!NOTE]
> Pokud sledujete v Visual Basic, použijete `Function` místo obvyklého klíčového slova klíčové slovo, `Sub` protože tato metoda vrací hodnotu. Je to opravdu jednoduché: procedura Sub nevrací hodnotu, ale funkce.

1. Přidejte `CheckTheAnswer()` metodu. Tato metoda by měla být v souladu s jinými metodami, které jste provedli, například `StartTheQuiz()` .

     Při volání této metody přidá hodnoty addend1 a addend2 a porovná výsledek s hodnotou v <xref:System.Windows.Forms.NumericUpDown> ovládacím prvku Sum. Pokud jsou hodnoty stejné, metoda vrátí hodnotu `true` . V opačném případě metoda vrátí hodnotu `false` . Váš kód by měl vypadat takto.

     [!code-vb[VbExpressTutorial3Step4#8](../ide/codesnippet/VisualBasic/step-4-add-the-checktheanswer-parens-method_1.vb)]
     [!code-csharp[VbExpressTutorial3Step4#8](../ide/codesnippet/CSharp/step-4-add-the-checktheanswer-parens-method_1.cs)]

     [!INCLUDE [devlang-control-csharp-vb](./includes/devlang-control-csharp-vb.md)]

     V dalším kroku zkontrolujete odpověď tím, že aktualizujete kód v metodě <xref:System.Windows.Forms.Timer.Tick> obslužné rutiny události časovače k volání nové `CheckTheAnswer()` metody.

2. Do `if else` příkazu v metodě přidejte následující kód `Timer1_Tick()` , aby se časovač zastavilo, když uživatel získá odpověď vpravo.

     [!code-vb[VbExpressTutorial3Step4#10](../ide/codesnippet/VisualBasic/step-4-add-the-checktheanswer-parens-method_2.vb)]
     [!code-csharp[VbExpressTutorial3Step4#10](../ide/codesnippet/CSharp/step-4-add-the-checktheanswer-parens-method_2.cs)]

     Pokud je odpověď správná, `CheckTheAnswer()` vrátí `true` . Obslužná rutina události zastaví časovač, zobrazí zprávu congratulatory a pak znovu zpřístupní tlačítko **Start** . V opačném případě kvíz pokračuje.

3. Uložte program, spusťte jej, spusťte kvíz a poskytněte správnou odpověď na problém sčítání.

    > [!NOTE]
    > Když zadáte odpověď, musíte buď vybrat výchozí hodnotu, než začnete zadávat odpověď, nebo musíte nulu odstranit ručně. Toto chování opravíte později v tomto kurzu.

     Když zadáte správnou odpověď, otevře se okno se zprávou, tlačítko **Start** bude k dispozici a časovač se zastaví.

## <a name="to-continue-or-review"></a>Chcete-li pokračovat nebo přezkoumat

- Pokud chcete přejít na další krok kurzu, přečtěte si **[Krok 5: Přidání obslužných rutin událostí pro ovládací prvky NumericUpDown](../ide/step-5-add-enter-event-handlers-for-the-numericupdown-controls.md)**.

- Pokud se chcete vrátit k předchozímu kroku kurzu, přečtěte si [článek krok 3: Přidání časovače odpočítávání](../ide/step-3-add-a-countdown-timer.md).
