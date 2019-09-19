---
title: 'Kurz 2: Vytvoření časovaného matematického kvízu'
ms.date: 11/04/2016
ms.assetid: d7165d08-ace3-457d-b57d-fb8f80760a6f
ms.topic: tutorial
ms.technology: vs-ide-general
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 39550eb3e2d5fe78e50257b51b52642740781600
ms.sourcegitcommit: 6eed0372976c0167b9a6d42ba443f9a474b8bb91
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2019
ms.locfileid: "71118863"
---
# <a name="tutorial-2-create-a-timed-math-quiz"></a>Kurz 2: Vytvoření časovaného matematického kvízu

V tomto kurzu sestavíte kvíz, ve kterém musí příjemce kvízu odpovědět na čtyři náhodné aritmetické úlohy v určeném čase. Získáte informace o následujících postupech:

- Generujte náhodná čísla pomocí <xref:System.Random> třídy.

- Aktivovat události, ke kterým dojde v určitém čase pomocí <xref:System.Windows.Forms.Timer> ovládacího prvku.

- Řízení toku programu pomocí `if else` příkazů.

- V kódu provádějte základní aritmetické operace.

Po dokončení bude kvíz vypadat podobně jako na následujícím snímku obrazovky s výjimkou různých čísel:

![Matematický kvíz se čtyřmi problémy](../ide/media/express_finishedquiz.png)

## <a name="tutorial-links"></a>Odkazy na kurz

Pokud si chcete stáhnout dokončenou verzi kvízu, přečtěte si [ukázku kurz dokončení matematického kvízu](https://code.msdn.microsoft.com/Complete-Math-Quiz-8581813c).

> [!NOTE]
> Tento kurz se zabývá C# i Visual Basic, takže se zaměřte na informace, které jsou specifické pro programovací jazyk, který používáte.

## <a name="related-topics"></a>Související témata

|Název|Popis|
|-----------|-----------------|
|[Krok 1: Vytvoření projektu a Přidání popisků do formuláře](../ide/step-1-create-a-project-and-add-labels-to-your-form.md)|Začněte vytvořením projektu, změnou vlastností a přidáním `Label` ovládacích prvků.|
|[Krok 2: Vytvoření náhodného přidání problému](../ide/step-2-create-a-random-addition-problem.md)|Vytvořte problém sčítání a použijte `Random` třídu pro generování náhodných čísel.|
|[Krok 3: Přidat časovač odpočítávání](../ide/step-3-add-a-countdown-timer.md)|Přidejte časovač odpočítávání, aby kvíz mohl být časovým limitem.|
|[Krok 4: Přidání metody metodu CheckTheAnswer ()](../ide/step-4-add-the-checktheanswer-parens-method.md)|Přidejte metodu pro kontrolu, zda autor kvízu zadal správnou odpověď pro daný problém.|
|[Krok 5: Přidat obslužné rutiny událostí Enter pro ovládací prvky NumericUpDown](../ide/step-5-add-enter-event-handlers-for-the-numericupdown-controls.md)|Přidejte obslužné rutiny událostí, které usnadňují podobuní kvízu.|
|[Krok 6: Přidat problém odčítání](../ide/step-6-add-a-subtraction-problem.md)|Přidejte problém odčítání, který generuje náhodná čísla, používá časovač a kontroluje správné odpovědi.|
|[Krok 7: Přidat problémy násobení a dělení](../ide/step-7-add-multiplication-and-division-problems.md)|Přidejte problémy násobení a dělení, které generují náhodná čísla, použijte časovač a vyhledejte správné odpovědi.|
|[Krok 8: Přizpůsobení kvízu](../ide/step-8-customize-the-quiz.md)|Vyzkoušejte jiné funkce, jako je například změna barev a přidání nápovědy.|
