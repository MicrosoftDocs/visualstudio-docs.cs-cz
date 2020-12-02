---
title: 'Krok 6: Přidání úlohy odčítání'
description: Naučte se, jak přidat problém odčítání a také zjistit, jak provádět úlohy.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: tutorial
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
dev_langs:
- CSharp
- VB
ms.assetid: 59204ef9-24bd-4f81-b85f-e3168e518a3e
author: ornellaalt
ms.author: ornella
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 8157335e47ec13c66da471f77ddbd2877bcac12d
ms.sourcegitcommit: df6ba39a62eae387e29f89388be9e3ee5ceff69c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2020
ms.locfileid: "96480665"
---
# <a name="step-6-add-a-subtraction-problem"></a>Krok 6: Přidání úlohy odčítání
V šesté části tohoto kurzu přidáte problém odčítání a naučíte se, jak provádět následující úlohy:

- Uložte hodnoty odčítání.

- Vygenerujte náhodná čísla pro daný problém (a ujistěte se, že odpověď je mezi 0 a 100).

- Aktualizujte metodu, která zkontroluje odpovědi, aby vyhledá i nový problém odčítání.

- Aktualizujte <xref:System.Windows.Forms.Timer.Tick> obslužnou rutinu události časovače tak, aby obslužná rutina události vyplnila správnou odpověď, když vyprší čas.

> [!NOTE]
> Toto téma je součástí série kurzů o základních konceptech kódování. Přehled tohoto kurzu najdete v tématu [kurz 2: vytvoření časovaného matematického kvízu](../ide/tutorial-2-create-a-timed-math-quiz.md).

## <a name="to-add-a-subtraction-problem"></a>Přidání problému odčítání

1. Přidejte dvě celočíselné proměnné pro problém odčítání do formuláře mezi celočíselnými proměnnými pro daný problém sčítání a časovač. Kód by měl vypadat takto.

     [!code-vb[VbExpressTutorial3Step5_6#12](../ide/codesnippet/VisualBasic/step-6-add-a-subtraction-problem_1.vb)]
     [!code-csharp[VbExpressTutorial3Step5_6#12](../ide/codesnippet/CSharp/step-6-add-a-subtraction-problem_1.cs)]

     [!INCLUDE [devlang-control-csharp-vb](./includes/devlang-control-csharp-vb.md)]

     Názvy nových celočíselných proměnných –**minuend** a **subtrahend**– nejedná se o programovací pojem. Jedná se o tradiční názvy aritmetické operace pro číslo, které se odečte (subtrahend), a číslo, ze kterého se odečte subtrahend (minuend). Rozdíl je minuend mínus subtrahend. Můžete použít jiné názvy, protože program nevyžaduje konkrétní názvy pro proměnné, ovládací prvky, komponenty nebo metody. Musíte dodržovat pravidla, jako je například nepočáteční názvy začínající číslicemi, ale obecně můžete použít názvy, například x1, X2, X3 a X4. Obecné názvy ale zjednodušují čtení kódu a problémy téměř nemožné sledovat. Aby názvy proměnných byly jedinečné a užitečné, použijte tradiční názvy pro násobení (multiplicand × násobitel = Product) a dělení (dělené ÷ dělitele = podíl) později v tomto kurzu.

     Dále upravíte `StartTheQuiz()` metodu tak, aby poskytovala náhodné hodnoty pro problém odčítání.

2. Přidejte následující kód za komentář "vyplňování problému při odčítání".

     [!code-vb[VbExpressTutorial3Step5_6#13](../ide/codesnippet/VisualBasic/step-6-add-a-subtraction-problem_2.vb)]
     [!code-csharp[VbExpressTutorial3Step5_6#13](../ide/codesnippet/CSharp/step-6-add-a-subtraction-problem_2.cs)]

     Chcete-li zabránit negativním odpovědím na problém odčítání, tento kód používá <xref:System.Random.Next> metodu <xref:System.Random> třídy trochu odlišně od toho, jak to dělá. Při předání `Next()` metody dvěma hodnotám vybere náhodné číslo, které je větší než nebo rovno první hodnotě a menší než druhá hodnota. Následující kód zvolí náhodné číslo od 1 do 100 a uloží jej do proměnné minuend.

     [!code-vb[VbExpressTutorial3Step5_6#21](../ide/codesnippet/VisualBasic/step-6-add-a-subtraction-problem_3.vb)]
     [!code-csharp[VbExpressTutorial3Step5_6#21](../ide/codesnippet/CSharp/step-6-add-a-subtraction-problem_3.cs)]

     Můžete zavolat `Next()` metodu náhodné třídy, kterou jste pojmenovali "randomizer" dříve v tomto kurzu, a to více způsoby. Metody, které lze volat více než jedním způsobem, jsou označovány jako přetížené a můžete je prozkoumat pomocí technologie IntelliSense. Prohlédněte si znovu Popis popisku okna technologie IntelliSense pro `Next()` metodu.

     ![Popisek okna IntelliSense](../ide/media/express_overloads.png)<br/>
**_IntelliSense_* _ _window popisu tlačítka *

     V popisu se zobrazí **(+ 2 přetížení)**, což znamená, že můžete zavolat `Next()` metodu dvěma dalšími způsoby. Přetížení obsahují odlišná čísla nebo typy argumentů, aby byly mírně odlišné od sebe. Například metoda může mít jeden celočíselný argument a jedno z jeho přetížení může mít celočíselnou hodnotu a řetězec. Můžete zvolit správné přetížení na základě toho, co chcete udělat. Při přidání kódu do `StartTheQuiz()` metody se v okně IntelliSense zobrazí další informace hned po zadání `randomizer.Next(` . Chcete-li cyklicky přepínat, vyberte **šipky nahoru** a **dolů** , jak je znázorněno na následujícím obrázku:

     ![Přetížení pro metodu Next&#40;&#41; v IntelliSense](../ide/media/express_nextoverload.png)<br/>
*Přetížení pro*  * **Next ()** _ _Metoda ve * ***IntelliSense**_

     V takovém případě chcete zvolit poslední přetížení, protože můžete zadat minimální a maximální hodnoty.

3. Upravte `CheckTheAnswer()` metodu pro kontrolu správné odpovědi na odčítání.

     [!code-vb[VbExpressTutorial3Step5_6#14](../ide/codesnippet/VisualBasic/step-6-add-a-subtraction-problem_4.vb)]
     [!code-csharp[VbExpressTutorial3Step5_6#14](../ide/codesnippet/CSharp/step-6-add-a-subtraction-problem_4.cs)]

     V jazyce C# `&&` je `logical and` operátor. V Visual Basic ekvivalentní operátor `AndAlso` . Tyto operátory označují "Pokud součet hodnot addend1 a addend2 se rovná hodnotě součtu NumericUpDown a pokud je minuend mínus subtrahend rovna hodnotě rozdílu NumericUpDown." `CheckTheAnswer()`Metoda vrátí `true` pouze v případě, že jsou odpovědi na problémy sčítání a odčítání správné.

4. Poslední část obslužné rutiny události Tick časovače nahraďte následujícím kódem, aby vyplnila správnou odpověď, když vyprší čas.

     [!code-vb[VbExpressTutorial3Step5_6#22](../ide/codesnippet/VisualBasic/step-6-add-a-subtraction-problem_5.vb)]
     [!code-csharp[VbExpressTutorial3Step5_6#22](../ide/codesnippet/CSharp/step-6-add-a-subtraction-problem_5.cs)]

5. Uložte a spusťte kód.

     Váš program zahrnuje úlohu odčítání, jak ukazuje následující obrázek:

     ![Matematický kvíz s problémem odčítání](../ide/media/express_addsubtract.png)<br/>
Problém odčítání _with _*_matematického kvízu_*_ *

## <a name="to-continue-or-review"></a>Chcete-li pokračovat nebo přezkoumat

- Chcete-li přejít k dalšímu kroku kurzu, přečtěte si **[článek krok 7: Přidání problémů násobení a dělení](../ide/step-7-add-multiplication-and-division-problems.md)**.

- Chcete-li se vrátit k předchozímu kroku kurzu, přečtěte si [Krok 5: Přidání obslužných rutin událostí Enter pro ovládací prvky NumericUpDown](../ide/step-5-add-enter-event-handlers-for-the-numericupdown-controls.md).
