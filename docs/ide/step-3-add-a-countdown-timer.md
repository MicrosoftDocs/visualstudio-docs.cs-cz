---
title: 'Krok 3: Přidání časovače odpočítávání'
description: Naučte se, jak přidat časovač odpočítávání pro sledování počtu sekund, které zbývá pro dokončení příjemce kvízu.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: 723b5daabd19d2e49462bf62d2657c6a6cd14b7f
ms.sourcegitcommit: df6ba39a62eae387e29f89388be9e3ee5ceff69c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2020
ms.locfileid: "96480639"
---
# <a name="step-3-add-a-countdown-timer"></a>Krok 3: Přidání časovače odpočítávání

V třetí části tohoto kurzu přidáte časovač odpočítávání za účelem sledování počtu sekund, které zbývá pro dokončení příjemce kvízu.

> [!NOTE]
> Toto téma je součástí série kurzů o základních konceptech kódování. Přehled tohoto kurzu najdete v tématu [kurz 2: vytvoření časovaného matematického kvízu](../ide/tutorial-2-create-a-timed-math-quiz.md).

## <a name="to-add-a-countdown-timer"></a>Přidání časovače odpočítávání

1. Přidejte celočíselnou proměnnou s názvem **TimeLeft**, stejně jako jste provedli v předchozím postupu. Váš kód by měl vypadat takto.

     [!code-vb[VbExpressTutorial3Step3#5](../ide/codesnippet/VisualBasic/step-3-add-a-countdown-timer_1.vb)]
     [!code-csharp[VbExpressTutorial3Step3#5](../ide/codesnippet/CSharp/step-3-add-a-countdown-timer_1.cs)]

     [!INCLUDE [devlang-control-csharp-vb](./includes/devlang-control-csharp-vb.md)]

     Nyní potřebujete metodu, která ve skutečnosti počítá sekundy, jako je například časovač, který po dobu, kterou určíte, vyvolá událost.

2. V okně návrh přesuňte <xref:System.Windows.Forms.Timer> ovládací prvek z kategorie **součásti** sady **nástrojů** do formuláře.

     Ovládací prvek se zobrazí v šedé oblasti v dolní části okna návrhu.

3. Ve formuláři vyberte ikonu **Timer1** , kterou jste právě přidali, a nastavte její vlastnost **interval** na **1000**.

     Vzhledem k tomu, že hodnota intervalu je milisekunda, hodnota 1000 způsobí, že se <xref:System.Windows.Forms.Timer.Tick> událost aktivuje každou sekundu.

4. Na formuláři dvakrát klikněte na ovládací prvek **časovač** , nebo ho vyberte a pak stiskněte klávesu **ENTER** .

     Zobrazí se Editor kódu a zobrazí metodu obslužné rutiny události Tick, kterou jste právě přidali.

5. Do nové metody obslužné rutiny události přidejte následující příkazy.

     [!code-vb[VbExpressTutorial3Step3#6](../ide/codesnippet/VisualBasic/step-3-add-a-countdown-timer_2.vb)]
     [!code-csharp[VbExpressTutorial3Step3#6](../ide/codesnippet/CSharp/step-3-add-a-countdown-timer_2.cs)]

     Na základě toho, co jste přidali, časovač kontroluje každou sekundu, zda je čas spuštěn, určením, zda je proměnná **TimeLeft** celého čísla větší než 0. Pokud je, zůstane čas stále. Časovač nejprve odečte 1 od timeLeft a poté aktualizuje vlastnost **text** ovládacího prvku **timeLabel** , aby zobrazila příjemce kvízu, kolik sekund zbývá.

     Pokud žádný čas nezůstane, časovač se zastaví a změní text ovládacího prvku **timeLabel** tak, aby se zobrazil **čas.** Okno se zprávou oznamuje, že kvíz je nad a odpověď je odhalena – v tomto případě přidáním addend1 a addend2. Vlastnost **Enabled** ovládacího prvku **startButton** je nastavena na **hodnotu true** , aby příjemce kvízu mohl spustit jiný kvíz.

     Právě jste přidali `if else` příkaz, což je způsob, jak říct programům rozhodování. `if else`Příkaz vypadá následovně.

    > [!NOTE]
    > Následující příklad je pouze pro ukázku – Nepřidávat ho do projektu.

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

     Prohlédněte si úzce na příkazu, který jste přidali v `else` bloku, abyste zobrazili odpověď na problém sčítání.

     [!code-vb[VbExpressTutorial3Step3#24](../ide/codesnippet/VisualBasic/step-3-add-a-countdown-timer_3.vb)]
     [!code-csharp[VbExpressTutorial3Step3#24](../ide/codesnippet/CSharp/step-3-add-a-countdown-timer_3.cs)]

     Příkaz `addend1 + addend2` sečte hodnoty dvou proměnných dohromady. První část ( `sum.Value` ) používá vlastnost **Value** součtového ovládacího prvku NumericUpDown k zobrazení správné odpovědi. Stejnou vlastnost použijete později ke kontrole odpovědí pro kvíz.

     Kvíz uživatelé vyplňující může snadněji zadat čísla pomocí <xref:System.Windows.Forms.NumericUpDown> ovládacího prvku, což je důvod, proč ho použijete pro odpovědi na matematické problémy. Všechny možné odpovědi jsou celá čísla od 0 do 100. Ponecháním výchozích hodnot vlastností **minimum**, **Maximum** a **počet desetinných míst** zajistíte, že uživatelé vyplňující kvízu nemůže vstupovat do desetinných míst, záporná čísla nebo čísla, která jsou příliš vysoká. (Pokud jste chtěli uživatelé vyplňující kvízu zadat 3,141, ale ne 3,1415, mohli byste nastavit vlastnost **počet desetinných míst** na 3.)

6. Přidejte tři řádky na konec `StartTheQuiz()` metody, aby kód vypadal jako následující.

     [!code-vb[VbExpressTutorial3Step3#7](../ide/codesnippet/VisualBasic/step-3-add-a-countdown-timer_4.vb)]
     [!code-csharp[VbExpressTutorial3Step3#7](../ide/codesnippet/CSharp/step-3-add-a-countdown-timer_4.cs)]

     Teď, když se kvíz spustí, proměnná **TimeLeft** je nastavená na 30 a vlastnost **text** ovládacího prvku **timeLabel** je nastavená na 30 sekund. Pak <xref:System.Windows.Forms.Timer.Start> Metoda ovládacího prvku Timer spustí odpočítávání. (Kvíz ještě nekontroluje odpověď – to je dál.)

7. Uložte program, spusťte jej a pak klikněte na tlačítko **Start** ve formuláři.

     Časovač se začne počítat. Když čas vyprší, kvíz skončí a odpověď se zobrazí. Následující ilustrace znázorňuje kvíz probíhá.

     ![Probíhá Matematický kvíz.](../ide/media/express_addcountdown.png)<br/>
*Probíhá Matematický kvíz.*

## <a name="to-continue-or-review"></a>Chcete-li pokračovat nebo přezkoumat

- Pokud chcete přejít na další krok kurzu, přečtěte si **[Krok 4: Přidání metody metodu CheckTheAnswer ()](../ide/step-4-add-the-checktheanswer-parens-method.md)**.

- Pokud se chcete vrátit k předchozímu kroku kurzu, přečtěte si [článek krok 2: vytvoření náhodného problému přidání](../ide/step-2-create-a-random-addition-problem.md).
