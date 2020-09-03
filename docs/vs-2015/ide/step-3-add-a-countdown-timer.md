---
title: 'Krok 3: přidejte časovač odpočítávání | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
ms.assetid: 62670a2b-efdc-45c6-9646-9b17eeb33dcb
caps.latest.revision: 25
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: bae5b4a81864cc591491c21218a5d8253dfc61bb
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "72671848"
---
# <a name="step-3-add-a-countdown-timer"></a>Krok 3: Přidejte časovač odpočítávání
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

V třetí části tohoto kurzu přidáte časovač odpočítávání za účelem sledování počtu sekund, které zbývá pro dokončení příjemce kvízu.

> [!NOTE]
> Toto téma je součástí série kurzů o základních konceptech kódování. Přehled tohoto kurzu najdete v tématu [kurz 2: vytvoření časovaného matematického kvízu](../ide/tutorial-2-create-a-timed-math-quiz.md).

### <a name="to-add-a-countdown-timer"></a>Přidání časovače odpočítávání

1. Přidejte celočíselnou proměnnou s názvem **TimeLeft**, stejně jako jste provedli v předchozím postupu. Váš kód by měl vypadat takto.

     [!code-csharp[VbExpressTutorial3Step3#5](../snippets/csharp/VS_Snippets_VBCSharp/vbexpresstutorial3step3/cs/form1.cs#5)]
     [!code-vb[VbExpressTutorial3Step3#5](../snippets/visualbasic/VS_Snippets_VBCSharp/vbexpresstutorial3step3/vb/form1.vb#5)]

     Nyní potřebujete metodu, která ve skutečnosti počítá sekundy, jako je například časovač, který po dobu, kterou určíte, vyvolá událost.

2. V okně návrh přesuňte `Timer` ovládací prvek z kategorie **součásti** sady nástrojů do formuláře.

     Ovládací prvek se zobrazí v šedé oblasti v dolní části okna návrhu.

3. Ve formuláři vyberte ikonu **Timer1** , kterou jste právě přidali, a nastavte její vlastnost **interval** na **1000**.

     Vzhledem k tomu, že hodnota intervalu je milisekund, hodnota 1000 způsobí, že se událost Tick vyvolá každou sekundu.

4. Na formuláři dvakrát klikněte na ovládací prvek časovač, nebo ho vyberte a pak stiskněte klávesu ENTER.

     Zobrazí se Editor kódu a zobrazí metodu obslužné rutiny události Tick, kterou jste právě přidali.

5. Do nové metody obslužné rutiny události přidejte následující příkazy.

     [!code-csharp[VbExpressTutorial3Step3#6](../snippets/csharp/VS_Snippets_VBCSharp/vbexpresstutorial3step3/cs/form1.cs#6)]
     [!code-vb[VbExpressTutorial3Step3#6](../snippets/visualbasic/VS_Snippets_VBCSharp/vbexpresstutorial3step3/vb/form1.vb#6)]

     Na základě toho, co jste přidali, časovač kontroluje každou sekundu, zda je čas spuštěn, určením, zda je proměnná **TimeLeft** celého čísla větší než 0. Pokud je, zůstane čas stále. Časovač nejprve odečte 1 od timeLeft a pak aktualizuje vlastnost **text** `timeLabel` ovládacího prvku tak, aby zobrazovala kvíz o tom, kolik sekund zbývá.

     Pokud žádný čas nezůstane, časovač se zastaví a změní text `timeLabel` ovládacího prvku tak, aby se zobrazil **čas.** Okno se zprávou oznamuje, že kvíz je nad a odpověď je odhalena – v tomto případě přidáním addend1 a addend2. Vlastnost **Enabled** `startButton` ovládacího prvku je nastavena na hodnotu `true` tak, aby příjemce kvízu mohl spustit jiný kvíz.

     Právě jste přidali `if else` příkaz, což je způsob, jak říct programům rozhodování. `if else`Příkaz vypadá následovně.

    > [!NOTE]
    > Následující příklad je pouze pro ilustraci – nepřidávejte ho do projektu.

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

     [!code-csharp[VbExpressTutorial3Step3#24](../snippets/csharp/VS_Snippets_VBCSharp/vbexpresstutorial3step3/cs/form1.cs#24)]
     [!code-vb[VbExpressTutorial3Step3#24](../snippets/visualbasic/VS_Snippets_VBCSharp/vbexpresstutorial3step3/vb/form1.vb#24)]

     Příkaz `addend1 + addend2` sečte hodnoty dvou proměnných dohromady. První část ( `sum.Value` ) používá vlastnost **Value** `NumericUpDown` ovládacího prvku Sum k zobrazení správné odpovědi. Stejnou vlastnost použijete později ke kontrole odpovědí pro kvíz.

     Kvíz uživatelé vyplňující může snadněji zadat čísla pomocí `NumericUpDown` ovládacího prvku, což je důvod, proč ho použijete pro odpovědi na matematické problémy. Všechny možné odpovědi jsou celá čísla od 0 do 100. Ponecháním výchozích hodnot vlastností **minimum**, **Maximum**a **počet desetinných míst** zajistíte, že uživatelé vyplňující kvízu nemůže vstupovat do desetinných míst, záporná čísla nebo čísla, která jsou příliš vysoká. (Pokud jste chtěli uživatelé vyplňující kvízu zadat 3,141, ale ne 3,1415, mohli byste nastavit vlastnost **počet desetinných míst** na 3.)

6. Přidejte tři řádky na konec `StartTheQuiz()` metody, aby kód vypadal jako následující.

     [!code-csharp[VbExpressTutorial3Step3#7](../snippets/csharp/VS_Snippets_VBCSharp/vbexpresstutorial3step3/cs/form1.cs#7)]
     [!code-vb[VbExpressTutorial3Step3#7](../snippets/visualbasic/VS_Snippets_VBCSharp/vbexpresstutorial3step3/vb/form1.vb#7)]

     Teď, když se kvíz spustí, proměnná **TimeLeft** je nastavená na 30 a vlastnost **text** `timeLabel` ovládacího prvku je nastavená na 30 sekund. Pak `Start()` Metoda `Timer` ovládacího prvku spustí odpočítávání. (Kvíz ještě nekontroluje odpověď – to je dál.)

7. Uložte program, spusťte jej a pak klikněte na tlačítko **Start** ve formuláři.

     Časovač se začne počítat. Když čas vyprší, kvíz skončí a odpověď se zobrazí. Následující ilustrace znázorňuje kvíz probíhá.

     Probíhá ![Matematický kvíz](../ide/media/express-addcountdown.png "Express_AddCountdown") . Probíhá Matematický kvíz.

### <a name="to-continue-or-review"></a>Chcete-li pokračovat nebo přezkoumat

- Pokud chcete přejít na další krok kurzu, přečtěte si [Krok 4: Přidání metody metodu CheckTheAnswer ()](../ide/step-4-add-the-checktheanswer-parens-method.md).

- Pokud se chcete vrátit k předchozímu kroku kurzu, přečtěte si [článek krok 2: vytvoření náhodného problému přidání](../ide/step-2-create-a-random-addition-problem.md).
