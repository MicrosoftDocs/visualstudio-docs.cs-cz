---
title: 'Krok 3: Přidání časovače odpočítávání'
ms.date: 11/04/2016
ms.topic: tutorial
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
dev_langs:
- CSharp
- VB
ms.assetid: 62670a2b-efdc-45c6-9646-9b17eeb33dcb
author: ornellaalt
ms.author: ornella
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 6ca2dce7f6f9ddc484b67f250f34d69747c6e46e
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/20/2020
ms.locfileid: "77579867"
---
# <a name="step-3-add-a-countdown-timer"></a>Krok 3: Přidání časovače odpočítávání

Ve třetí části tohoto kurzu přidáte odpočítávací časovač, abyste sledovali počet sekund, které zbývají pro dokončení příjemce kvízu.

> [!NOTE]
> Toto téma je součástí série kurzů o základních konceptech kódování. Přehled kurzu najdete v [tématu Výuka 2: Vytvoření časovaného matematického kvízu](../ide/tutorial-2-create-a-timed-math-quiz.md).

## <a name="to-add-a-countdown-timer"></a>Přidání časovače odpočítávání

1. Přidejte celou proměnnou s názvem **timeLeft**, stejně jako v předchozím postupu. Váš kód by měl vypadat takto.

     [!code-vb[VbExpressTutorial3Step3#5](../ide/codesnippet/VisualBasic/step-3-add-a-countdown-timer_1.vb)]
     [!code-csharp[VbExpressTutorial3Step3#5](../ide/codesnippet/CSharp/step-3-add-a-countdown-timer_1.cs)]

     [!INCLUDE [devlang-control-csharp-vb](./includes/devlang-control-csharp-vb.md)]

     Nyní potřebujete metodu, která skutečně počítá sekund, jako je například časovač, který vyvolá událost po množství času, který zadáte.

2. V okně návrhu <xref:System.Windows.Forms.Timer> přesuňte ovládací prvek z kategorie **Součásti** **panelu nástrojů** do formuláře.

     Ovládací prvek se zobrazí v šedé oblasti v dolní části okna návrhu.

3. Ve formuláři zvolte ikonu **timer1,** kterou jste právě přidali, a nastavte její vlastnost **Interval** na **1000**.

     Vzhledem k tomu, že hodnota intervalu je milisekund, hodnota 1000 způsobí, že událost k požáru <xref:System.Windows.Forms.Timer.Tick> každou sekundu.

4. Ve formuláři poklepejte na ovládací prvek **Časovač** nebo ho zvolte a pak zvolte **enter.**

     Zobrazí se editor kódu a zobrazí metodu pro obslužnou rutinu události Tick, kterou jste právě přidali.

5. Přidejte následující příkazy do metody nové obslužné rutiny události.

     [!code-vb[VbExpressTutorial3Step3#6](../ide/codesnippet/VisualBasic/step-3-add-a-countdown-timer_2.vb)]
     [!code-csharp[VbExpressTutorial3Step3#6](../ide/codesnippet/CSharp/step-3-add-a-countdown-timer_2.cs)]

     Na základě toho, co jste přidali, časovač zkontroluje každou sekundu, zda vyprší čas určením, zda **timeLeft** celá číselná proměnná je větší než 0. Pokud ano, stále zbývá čas. Časovač nejprve odečte 1 od timeLeft a potom aktualizuje **Text** vlastnost **timeLabel** ovládacího prvku zobrazit kvíz příjemce, kolik sekund zbývá.

     Pokud nezbývá žádný čas, časovač se zastaví a změní text ovládacího prvku **timeLabel** tak, aby se zoál **čas!** Okno se zprávou oznamuje, že kvíz je u konce a odpověď je odhalena – v tomto případě přidáním dodatku1 a dodatku2. **Vlastnost Enabled** ovládacího prvku **startButton** je nastavena na **hodnotu true,** aby příjemce kvízu mohl spustit jiný kvíz.

     Právě jste `if else` přidali prohlášení, což je, jak říct programy, aby se rozhodnutí. Prohlášení `if else` vypadá takto.

    > [!NOTE]
    > Následující příklad je pouze pro demonstraci – nepřidávejte jej do projektu.

    ```vb
    If (something that your program will check) Then
        ' One or more statements that will run
        ' if what the program checked is true.
    Else
        ' One or more statements that will run
        ' if what the program checked is false.
    End If
    ```

    ```csharp
    if (something that your program will check)
    {
        // One or more statements that will run
        // if what the program checked is true.
    }
    else
    {
        // One or more statements that will run
        // if what the program checked is false.
    }
    ```

     Podívejte se pozorně na prohlášení, `else` které jste přidali v bloku zobrazit odpověď na problém přidání.

     [!code-vb[VbExpressTutorial3Step3#24](../ide/codesnippet/VisualBasic/step-3-add-a-countdown-timer_3.vb)]
     [!code-csharp[VbExpressTutorial3Step3#24](../ide/codesnippet/CSharp/step-3-add-a-countdown-timer_3.cs)]

     Příkaz `addend1 + addend2` přidá hodnoty ve dvou proměnných dohromady. První část`sum.Value`( ) používá **Value** vlastnost součet NumericUpDown ovládací prvek zobrazit správnou odpověď. Stejnou vlastnost později použijete ke kontrole odpovědí na kvíz.

     Účastníci kvízu mohou snadněji <xref:System.Windows.Forms.NumericUpDown> zadávat čísla pomocí ovládacího prvku, což je důvod, proč je používáte pro odpovědi na matematické problémy. Všechny potenciální odpovědi jsou celá čísla od 0 do 100. Ponecháte-li výchozí hodnoty vlastností **Minimum**, **Maximum**a **DecimalPlaces,** zajistíte, že příjemci kvízu nemohou zadávat desetinná čísla, záporná čísla nebo čísla, která jsou příliš vysoká. (Pokud jste chtěli povolit příjemcům kvízů zadat 3.141, ale ne 3.1415, můžete nastavit **vlastnost DecimalPlaces** na 3.)

6. Přidejte tři řádky na `StartTheQuiz()` konec metody, takže kód vypadá takto.

     [!code-vb[VbExpressTutorial3Step3#7](../ide/codesnippet/VisualBasic/step-3-add-a-countdown-timer_4.vb)]
     [!code-csharp[VbExpressTutorial3Step3#7](../ide/codesnippet/CSharp/step-3-add-a-countdown-timer_4.cs)]

     Nyní, když se spustí kvíz, proměnná **timeLeft** je nastavena na 30 a **vlastnost Text** ovládacího prvku **timeLabel** je nastavena na 30 sekund. Poté <xref:System.Windows.Forms.Timer.Start> metoda ovládacího prvku Timer spustí odpočítávání. (Kvíz ještě nekontroluje odpověď – která následuje.)

7. Uložte program, spusťte jej a pak ve formuláři zvolte tlačítko **Start.**

     Časovač začne odpočítávat. Když vyprší čas, kvíz skončí a zobrazí se odpověď. Následující obrázek znázorňuje probíhající kvíz.

     ![Probíhá matematický kvíz](../ide/media/express_addcountdown.png)<br/>
*Probíhá matematický kvíz*

## <a name="to-continue-or-review"></a>Chcete-li pokračovat nebo přezkoumat

- Chcete-li přejít k dalšímu kroku kurzu, **[přečtěte si postup 4: Přidání metody CheckTheAnswer().](../ide/step-4-add-the-checktheanswer-parens-method.md)**

- Chcete-li se vrátit k předchozímu kroku kurzu, [přečtěte si krok 2: Vytvoření problému náhodného přidání](../ide/step-2-create-a-random-addition-problem.md).
