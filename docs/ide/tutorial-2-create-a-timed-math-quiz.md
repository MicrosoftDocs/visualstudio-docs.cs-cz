---
title: 'Kurz 2: Vytvoření časovaného matematického kvízu'
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
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/20/2020
ms.locfileid: "77579302"
---
# <a name="tutorial-2-create-a-timed-math-quiz"></a>Kurz 2: Vytvoření časovaného matematického kvízu

V tomto kurzu vytvoříte kvíz, ve kterém příjemce kvízu musí odpovědět na čtyři náhodné aritmetické problémy v zadaném čase.

> [!NOTE]
> Tento kurz zahrnuje c# a visual basic, takže se zaměřte na informace, které jsou specifické pro programovací jazyk, který používáte.

Tento kurz vás provede následujícími úkoly:

- Pomocí třídy vygenerujte <xref:System.Random> náhodná čísla.

- Aktivační události dojít v určitém čase <xref:System.Windows.Forms.Timer> pomocí ovládacího prvku.

- Řízení toku `if else` programu pomocí příkazů.

- Proveďte základní aritmetické operace v kódu.

Po dokončení bude kvíz vypadat podobně jako na následujícím snímku obrazovky, s výjimkou různých čísel:

![Matematický kvíz se čtyřmi problémy](../ide/media/express_finishedquiz.png)

## <a name="tutorial-links"></a>Odkazy na kurz

|Nadpis|Popis|
|-----------|-----------------|
|[Krok 1: Vytvoření projektu a přidání štítků do formuláře](../ide/step-1-create-a-project-and-add-labels-to-your-form.md)|Začněte vytvořením projektu, změnou `Label` vlastností a přidáním ovládacích prvků.|
|[Krok 2: Vytvoření problému náhodného přidání](../ide/step-2-create-a-random-addition-problem.md)|Vytvořte problém s přidáním a pomocí třídy vygenerujte `Random` náhodná čísla.|
|[Krok 3: Přidání časovače odpočítávání](../ide/step-3-add-a-countdown-timer.md)|Přidejte časovač odpočítávání, aby bylo možné kvíz načasovat.|
|[Krok 4: Přidání metody CheckTheAnswer().](../ide/step-4-add-the-checktheanswer-parens-method.md)|Přidejte metodu pro kontrolu, zda příjemce kvízu zadal správnou odpověď na problém.|
|[Krok 5: Přidání obslužných rutin událostí Enter pro ovládací prvky NumericUpDown](../ide/step-5-add-enter-event-handlers-for-the-numericupdown-controls.md)|Přidejte obslužné rutiny událostí, které usnadňují pořizuje kvíz.|
|[Krok 6: Přidání problému s odčítáním](../ide/step-6-add-a-subtraction-problem.md)|Přidejte problém odčítání, který generuje náhodná čísla, používá časovač a kontroluje správné odpovědi.|
|[Krok 7: Přidání problémů s násobením a dělením](../ide/step-7-add-multiplication-and-division-problems.md)|Přidejte problémy s násobením a dělením, které generují náhodná čísla, použijte časovač a zkontrolujte správné odpovědi.|
|[Krok 8: Přizpůsobení kvízu](../ide/step-8-customize-the-quiz.md)|Vyzkoušejte další funkce, například změnu barev a přidání nápovědy.|

K dispozici jsou také skvělé, bezplatné výukové materiály pro video. Další informace o programování v jazyce C#, viz [Základy jazyka C#: Vývoj pro úplné začátečníky](https://channel9.msdn.com/Series/C-Sharp-Fundamentals-Development-for-Absolute-Beginners). Další informace o programování v jazyce Visual Basic najdete v [tématu Základy jazyka: Vývoj pro úplné začátečníky](https://channel9.msdn.com/Series/Visual-Basic-Development-for-Absolute-Beginners).

## <a name="next-steps"></a>Další kroky

Chcete-li zahájit kurz, začněte krokem **[1: Vytvořte projekt a přidejte popisky do formuláře](../ide/step-1-create-a-project-and-add-labels-to-your-form.md)**.

## <a name="see-also"></a>Viz také

* [Další výukové programy pro C#](/visualstudio/get-started/csharp/)
* [Výukové programy jazyka Visual Basic](/visualstudio/get-started/visual-basic/)
* [Výukové programy pro C++](/cpp/get-started/tutorial-console-cpp)
