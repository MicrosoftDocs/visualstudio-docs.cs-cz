---
title: 'Krok 4: Přidání metody CheckTheAnswer().'
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: def01817fbd42a0da1a0392e00ba9ccff6876470
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/20/2020
ms.locfileid: "77579842"
---
# <a name="step-4-add-the-checktheanswer-method"></a>Krok 4: Přidání metody CheckTheAnswer().

Ve čtvrté části tohoto kurzu napíšete metodu , která určuje, `CheckTheAnswer()`zda jsou správné odpovědi na matematické problémy. Toto téma je součástí série kurzů o základních konceptech kódování. Přehled kurzu najdete v [tématu Výuka 2: Vytvoření časovaného matematického kvízu](../ide/tutorial-2-create-a-timed-math-quiz.md).

> [!NOTE]
> Toto téma je součástí série kurzů o základních konceptech kódování. Přehled kurzu najdete v [tématu Výuka 2: Vytvoření časovaného matematického kvízu](../ide/tutorial-2-create-a-timed-math-quiz.md).

## <a name="to-verify-whether-the-answers-are-correct"></a>Ověření správnost odpovědí

> [!NOTE]
> Pokud jste po spolu v jazyce Visual `Function` Basic, budete `Sub` používat klíčové slovo namísto obvyklé klíčové slovo, protože tato metoda vrátí hodnotu. Je to opravdu tak jednoduché: sub nevrátí hodnotu, ale funkce ano.

1. Přidejte `CheckTheAnswer()` metodu.

     Při volání této metody přidá hodnoty addend1 a addend2 a porovná výsledek s <xref:System.Windows.Forms.NumericUpDown> hodnotou v ovládacím prvku součtu. Pokud jsou hodnoty stejné, metoda vrátí `true`hodnotu . V opačném případě vrátí `false`metoda hodnotu . Váš kód by měl vypadat takto.

     [!code-vb[VbExpressTutorial3Step4#8](../ide/codesnippet/VisualBasic/step-4-add-the-checktheanswer-parens-method_1.vb)]
     [!code-csharp[VbExpressTutorial3Step4#8](../ide/codesnippet/CSharp/step-4-add-the-checktheanswer-parens-method_1.cs)]

     [!INCLUDE [devlang-control-csharp-vb](./includes/devlang-control-csharp-vb.md)]

     Dále zkontrolujete odpověď aktualizací kódu v metodě pro obslužnou rutinu <xref:System.Windows.Forms.Timer.Tick> události časovače pro volání nové `CheckTheAnswer()` metody.

2. Přidejte následující kód `if else` do příkazu.

     [!code-vb[VbExpressTutorial3Step4#10](../ide/codesnippet/VisualBasic/step-4-add-the-checktheanswer-parens-method_2.vb)]
     [!code-csharp[VbExpressTutorial3Step4#10](../ide/codesnippet/CSharp/step-4-add-the-checktheanswer-parens-method_2.cs)]

     Pokud je odpověď `CheckTheAnswer()` správná, vrátí `true`. Obslužná rutina události zastaví časovač, zobrazí gratulační zprávu a potom znovu zpřístupní tlačítko **Start.** V opačném případě kvíz pokračuje.

3. Uložte program, spusťte jej, spusťte kvíz a poskytněte správnou odpověď na problém s přidáním.

    > [!NOTE]
    > Když zadáte odpověď, musíte buď vybrat výchozí hodnotu, než začnete zadávat odpověď, nebo musíte odstranit nulu ručně. Toto chování opravíte později v tomto kurzu.

     Když zadáte správnou odpověď, otevře se okno se zprávou, tlačítko **Start** bude k dispozici a časovač se zastaví.

## <a name="to-continue-or-review"></a>Chcete-li pokračovat nebo přezkoumat

- Další krok kurzu najdete v **[tématu Krok 5: Přidání obslužných rutin událostí pro ovládací prvky NumericUpDown](../ide/step-5-add-enter-event-handlers-for-the-numericupdown-controls.md)**.

- Chcete-li se vrátit k předchozímu kroku kurzu, [přečtěte si krok 3: Přidání časovače odpočítávání](../ide/step-3-add-a-countdown-timer.md).
