---
title: 'Krok 4: Přidejte metodu metodu CheckTheAnswer () | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
ms.assetid: c66f3831-b4a0-40bc-a109-8f46f4db35ed
caps.latest.revision: 21
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: cbfdc15b06d857b7537a4a327f3201c86d4db2d5
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72671783"
---
# <a name="step-4-add-the-checktheanswer-method"></a>Krok 4: Přidejte metodu CheckTheAnswer()
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Ve čtvrté části tohoto kurzu napíšete metodu, `CheckTheAnswer()`, která určuje, zda jsou odpovědi na matematické problémy správné. Toto téma je součástí série kurzů o základních konceptech kódování. Přehled tohoto kurzu najdete v tématu [kurz 2: vytvoření časovaného matematického kvízu](../ide/tutorial-2-create-a-timed-math-quiz.md).

> [!NOTE]
> Pokud sledujete spolu v Visual Basic, použijete místo `Sub` obvyklého klíčového slova `Function` klíčové slovo, protože tato metoda vrací hodnotu. Je to opravdu jednoduché: procedura Sub nevrací hodnotu, ale funkce.

### <a name="to-verify-whether-the-answers-are-correct"></a>Ověření, zda jsou odpovědi správné

1. Přidejte metodu `CheckTheAnswer()`.

     Při volání této metody přidá hodnoty addend1 a addend2 a porovná výsledek s hodnotou v ovládacím prvku Sum `NumericUpDown`. Pokud jsou hodnoty stejné, metoda vrátí hodnotu `true`. V opačném případě metoda vrátí hodnotu `false`. Váš kód by měl vypadat takto.

     [!code-csharp[VbExpressTutorial3Step4#8](../snippets/csharp/VS_Snippets_VBCSharp/vbexpresstutorial3step4/cs/form1.cs#8)]
     [!code-vb[VbExpressTutorial3Step4#8](../snippets/visualbasic/VS_Snippets_VBCSharp/vbexpresstutorial3step4/vb/form1.vb#8)]

     V dalším kroku zkontrolujete odpověď tak, že aktualizujete kód v metodě obslužné rutiny události Tick časovače pro volání nové metody `CheckTheAnswer()`.

2. Do příkazu `if else` přidejte následující kód.

     [!code-csharp[VbExpressTutorial3Step4#10](../snippets/csharp/VS_Snippets_VBCSharp/vbexpresstutorial3step4/cs/form1.cs#10)]
     [!code-vb[VbExpressTutorial3Step4#10](../snippets/visualbasic/VS_Snippets_VBCSharp/vbexpresstutorial3step4/vb/form1.vb#10)]

     Pokud je odpověď správná, `CheckTheAnswer()` vrátí `true`. Obslužná rutina události zastaví časovač, zobrazí zprávu congratulatory a pak znovu zpřístupní tlačítko **Start** . V opačném případě kvíz pokračuje.

3. Uložte program, spusťte jej, spusťte kvíz a poskytněte správnou odpověď na problém sčítání.

    > [!NOTE]
    > Když zadáte odpověď, musíte buď vybrat výchozí hodnotu, než začnete zadávat odpověď, nebo musíte nulu odstranit ručně. Toto chování opravíte později v tomto kurzu.

     Když zadáte správnou odpověď, otevře se okno se zprávou, tlačítko **Start** bude k dispozici a časovač se zastaví.

### <a name="to-continue-or-review"></a>Chcete-li pokračovat nebo přezkoumat

- Pokud chcete přejít na další krok kurzu, přečtěte si [Krok 5: Přidání obslužných rutin událostí pro ovládací prvky NumericUpDown](../ide/step-5-add-enter-event-handlers-for-the-numericupdown-controls.md).

- Pokud se chcete vrátit k předchozímu kroku kurzu, přečtěte si [článek krok 3: Přidání časovače odpočítávání](../ide/step-3-add-a-countdown-timer.md).
