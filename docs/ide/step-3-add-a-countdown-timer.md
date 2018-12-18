---
title: 'Krok 3: Přidejte časovač odpočítávání'
ms.custom: ''
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-acquisition
ms.topic: conceptual
ms.assetid: 62670a2b-efdc-45c6-9646-9b17eeb33dcb
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 2e7cf75b23b74753b875aafb43a5dd331b18c623
ms.sourcegitcommit: 58052c29fc61c9a1ca55a64a63a7fdcde34668a4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2018
ms.locfileid: "34748137"
---
# <a name="step-3-add-a-countdown-timer"></a>Krok 3: Přidejte časovač odpočítávání
V třetím části tohoto kurzu budete přidejte časovač odpočítávání sledovat počet sekund, které zůstávají pro příjemce kvízu s časovým limitem ukončíte.

> [!NOTE]
>  Toto téma je součástí série, kurz o základních konceptech kódování. Přehled kurzu, najdete v tématu [kurzu 2: vytvoření matematického kvízu](../ide/tutorial-2-create-a-timed-math-quiz.md).

## <a name="to-add-a-countdown-timer"></a>Chcete-li přidat časovač odpočítávání

1.  Přidat proměnná typu integer, který je pojmenován **timeLeft**, stejně jako v předchozím postupu. Váš kód by měl vypadat následovně.

     [!code-vb[VbExpressTutorial3Step3#5](../ide/codesnippet/VisualBasic/step-3-add-a-countdown-timer_1.vb)]
     [!code-csharp[VbExpressTutorial3Step3#5](../ide/codesnippet/CSharp/step-3-add-a-countdown-timer_1.cs)]

     Teď musíte metodu, která ve skutečnosti vrátí počet sekund, jako je například časovač, který vyvolá událost po množství času, který určíte.

2.  V okně návrhu přesunout <xref:System.Windows.Forms.Timer> řídit z **součásti** kategorii **sada nástrojů** do svého formuláře.

     Ovládací prvek se zobrazí v šedivá oblast v dolní části okna návrhu.

3.  Ve formuláři, vyberte **timer1** ikonu, který jste právě přidali a nastavit jeho **Interval** vlastnost **1000**.

     Vzhledem k tomu, že je hodnota intervalu milisekund, hodnotu 1000 příčin <xref:System.Windows.Forms.Timer.Tick> událostí vyvolá každou sekundu.

4.  Ve formuláři, poklepejte na **časovače** řídit, nebo zvolte jej a potom zvolte **Enter** klíč.

     Editor kódu zobrazí se metoda obslužné rutiny událostí značek, kterou jste právě přidali.

5.  Přidejte následující příkazy pro nové obslužná rutina události.

     [!code-vb[VbExpressTutorial3Step3#6](../ide/codesnippet/VisualBasic/step-3-add-a-countdown-timer_2.vb)]
     [!code-csharp[VbExpressTutorial3Step3#6](../ide/codesnippet/CSharp/step-3-add-a-countdown-timer_2.cs)]

     Podle toho, co jste přidali, časovač zkontroluje, každou sekundu jestli čas byla spuštěna tak, že určíte jestli **timeLeft** proměnná s celým číslem je větší než 0. Pokud se jedná, čas stále zůstává. Časovač nejprve odečte 1 z timeLeft a pak aktualizuje **Text** vlastnost **timeLabel** řízení k příjemce kvízu s časovým limitem zobrazit, kolik sekund zůstanou.

     Pokud zůstane žádný čas, časovač se zastaví a text se změní **timeLabel** řídit tak, aby se zobrazí **čas vypršel!** Okno se zprávou oznamuje, že kvízu je u konce a odpověď je odhalena – v takovém případě přidáním addend1 a addend2. **Povoleno** vlastnost **startButton** řízení je nastavené na **true** tak, aby kvízu s časovým limitem příjemce může spustit jinou kvízu s časovým limitem.

     Právě jste přidali `if else` příkaz, který je, jak zjistit programů rozhodnutí. `if else` Příkaz vypadá jako následující.

    > [!NOTE]
    >  Následující příklad je pouze pro ilustraci-nepřidáte do projektu.

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

     Prohlédněte si blíže příkaz, který jste přidali v `else` blok zobrazit odpověď sčítání.

     [!code-vb[VbExpressTutorial3Step3#24](../ide/codesnippet/VisualBasic/step-3-add-a-countdown-timer_3.vb)]
     [!code-csharp[VbExpressTutorial3Step3#24](../ide/codesnippet/CSharp/step-3-add-a-countdown-timer_3.cs)]

     Příkaz `addend1 + addend2` přidá hodnoty v dvě proměnné, které k sobě. První část (`sum.Value`) používá **hodnotu** vlastnost součtu NumericUpDown – ovládací prvek pro zobrazení správné odpovědi. Ke kontrole odpovědi na kvízu později použijete stejnou vlastnost.

     Píší kvízu s časovým limitem poznámky lze snadněji zadejte čísla pomocí <xref:System.Windows.Forms.NumericUpDown> prvek, který je důvod, proč použijete jeden pro odpovědi na matematické úlohy. Všechny potenciální odpovědi jsou celá čísla od 0 do 100. Protože výchozí hodnoty **minimální**, **maximální**, a **počet desetinných míst** vlastnosti, můžete zajistit, aby píší kvízu s časovým limitem poznámky nelze zadat počet desetinných míst, záporná čísla, nebo čísla, která je příliš vysoká. (Pokud jste chtěli povolit píší kvízu s časovým limitem poznámky k zadání 3,141, ale není 3.1415, můžete nastavit **počet desetinných míst** vlastnost 3.)

6.  Přidejte tři řádky na konec `StartTheQuiz()` proto kód vypadá takto.

     [!code-vb[VbExpressTutorial3Step3#7](../ide/codesnippet/VisualBasic/step-3-add-a-countdown-timer_4.vb)]
     [!code-csharp[VbExpressTutorial3Step3#7](../ide/codesnippet/CSharp/step-3-add-a-countdown-timer_4.cs)]

     Nyní, při spuštění vaší kvízu s časovým limitem, **timeLeft** proměnná je nastavená na 30 a **Text** vlastnost **timeLabel** řízení je nastavené na 30 sekund. Pak se <xref:System.Windows.Forms.Timer.Start> spustí metody ovládacího prvku časovač odpočítávání. (Kvízu neohlásí odpověď ještě – které teď.)

7.  Uložení programu, spusťte ji a pak zvolte **spustit** tlačítko ve formuláři.

     Časovač se začne počítat. Když čas vyprší, elementy end kvízu s časovým limitem, a zobrazí se odpověď. Následující obrázek znázorňuje kvízu v průběhu.

     ![Matematického kvízu v průběhu](../ide/media/express_addcountdown.png) matematického kvízu v průběhu

## <a name="to-continue-or-review"></a>Chcete-li pokračovat nebo přezkoumat

-   Chcete-li přejít k dalšímu kroku kurzu, přečtěte si téma [krok 4: Přidejte metodu CheckTheAnswer()](../ide/step-4-add-the-checktheanswer-parens-method.md).

-   Chcete-li vrátit k předchozímu kroku kurzu, přečtěte si téma [krok 2: Vytvořte náhodný problém s přidáním](../ide/step-2-create-a-random-addition-problem.md).
