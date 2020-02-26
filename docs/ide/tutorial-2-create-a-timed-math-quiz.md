---
title: 'Kurz 2: vytvoření časovaného matematického kvízu'
ms.date: 10/16/2019
ms.assetid: d7165d08-ace3-457d-b57d-fb8f80760a6f
ms.topic: tutorial
ms.technology: vs-ide-general
author: ornellaalt
ms.author: ornella
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 5b1f3620ef462228ff6a3461f44019e9c515a1c0
ms.sourcegitcommit: 2ae2436dc3484b9dfa10e0483afba1e5a02a52eb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/25/2020
ms.locfileid: "77579302"
---
# <a name="tutorial-2-create-a-timed-math-quiz"></a>Kurz 2: vytvoření časovaného matematického kvízu

V tomto kurzu sestavíte kvíz, ve kterém musí příjemce kvízu odpovědět na čtyři náhodné aritmetické úlohy v určeném čase.

> [!NOTE]
> Tento kurz se zabývá C# i Visual Basic, takže se zaměřte na informace, které jsou specifické pro programovací jazyk, který používáte.

Tento kurz vás provede následujícími úlohami:

- Generujte náhodná čísla pomocí třídy <xref:System.Random>.

- Aktivovat události, ke kterým dojde v určitém čase pomocí ovládacího prvku <xref:System.Windows.Forms.Timer>.

- Řízení toku programu pomocí příkazů `if else`.

- V kódu provádějte základní aritmetické operace.

Po dokončení bude kvíz vypadat podobně jako na následujícím snímku obrazovky s výjimkou různých čísel:

![Matematický kvíz se čtyřmi problémy](../ide/media/express_finishedquiz.png)

## <a name="tutorial-links"></a>Odkazy na kurz

|Název|Popis|
|-----------|-----------------|
|[Krok 1: vytvoření projektu a Přidání popisků do formuláře](../ide/step-1-create-a-project-and-add-labels-to-your-form.md)|Začněte tím, že vytvoříte projekt, změníte vlastnosti a přidáte `Label` ovládací prvky.|
|[Krok 2: vytvoření náhodného přidání problému](../ide/step-2-create-a-random-addition-problem.md)|Vytvořte problém sčítání a použijte třídu `Random` pro generování náhodných čísel.|
|[Krok 3: přidejte časovač odpočítávání](../ide/step-3-add-a-countdown-timer.md)|Přidejte časovač odpočítávání, aby kvíz mohl být časovým limitem.|
|[Krok 4: Přidání metody metodu CheckTheAnswer ()](../ide/step-4-add-the-checktheanswer-parens-method.md)|Přidejte metodu pro kontrolu, zda autor kvízu zadal správnou odpověď pro daný problém.|
|[Krok 5: přidejte obslužné rutiny událostí Enter pro ovládací prvky NumericUpDown](../ide/step-5-add-enter-event-handlers-for-the-numericupdown-controls.md)|Přidejte obslužné rutiny událostí, které usnadňují podobuní kvízu.|
|[Krok 6: Přidání problému odčítání](../ide/step-6-add-a-subtraction-problem.md)|Přidejte problém odčítání, který generuje náhodná čísla, používá časovač a kontroluje správné odpovědi.|
|[Krok 7: přidejte problémy násobení a dělení](../ide/step-7-add-multiplication-and-division-problems.md)|Přidejte problémy násobení a dělení, které generují náhodná čísla, použijte časovač a vyhledejte správné odpovědi.|
|[Krok 8: Přizpůsobení kvízu](../ide/step-8-customize-the-quiz.md)|Vyzkoušejte jiné funkce, jako je například změna barev a přidání nápovědy.|

K dispozici jsou také skvělé a bezplatné studijní materiály pro video. Další informace o programování v C#nástroji najdete v tématu [ C# základy: vývoj pro absolutní začátečníky](https://channel9.msdn.com/Series/C-Sharp-Fundamentals-Development-for-Absolute-Beginners). Další informace o programování v Visual Basic najdete v tématu [Visual Basic základy: vývoj pro absolutní začátečníky](https://channel9.msdn.com/Series/Visual-Basic-Development-for-Absolute-Beginners).

## <a name="next-steps"></a>Další kroky

Pokud chcete začít s kurzem, začněte v **[kroku 1: Vytvořte projekt a přidejte popisky do formuláře](../ide/step-1-create-a-project-and-add-labels-to-your-form.md)** .

## <a name="see-also"></a>Viz také

* [Další C# kurzy](/visualstudio/get-started/csharp/)
* [Kurzy Visual Basic](/visualstudio/get-started/visual-basic/)
* [C++výuka](/cpp/get-started/tutorial-console-cpp)
