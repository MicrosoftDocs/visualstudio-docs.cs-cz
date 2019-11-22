---
title: 'Kurz 2: vytvoření časovaného matematického kvízu | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
ms.assetid: d7165d08-ace3-457d-b57d-fb8f80760a6f
caps.latest.revision: 19
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: b91e5f864bc15f1fbcab9400d0cd3a4a2e8224a9
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2019
ms.locfileid: "74299864"
---
# <a name="tutorial-2-create-a-timed-math-quiz"></a>Tutoriál 2: Vytvoření matematického kvízu s časovým limitem
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

V tomto kurzu sestavíte kvíz, ve kterém musí příjemce kvízu odpovědět na čtyři náhodné aritmetické úlohy v určeném čase. Získáte informace o následujících postupech:

- Generujte náhodná čísla pomocí třídy `Random`.

- Aktivovat události, ke kterým dojde v určitém čase pomocí ovládacího prvku **Timer** .

- Řízení toku programu pomocí příkazů `if else`.

- V kódu provádějte základní aritmetické operace.

  Po dokončení bude kvíz vypadat jako na následujícím obrázku, s výjimkou různých čísel.

  ![Matematický kvíz se čtyřmi problémy](../ide/media/express-finishedquiz.png "Express_FinishedQuiz") Kvíz, který vytvoříte v tomto kurzu

> [!NOTE]
> Tento kurz se zabývá vizuálů C# i Visual Basic, takže se zaměřte na informace, které jsou specifické pro programovací jazyk, který používáte.

## <a name="related-topics"></a>Související témata

|Název|Popis|
|-----------|-----------------|
|[Krok 1: Vytvořte projekt a přidejte do svého formuláře popisky](../ide/step-1-create-a-project-and-add-labels-to-your-form.md)|Začněte tím, že vytvoříte projekt, změníte vlastnosti a přidáte `Label` ovládací prvky.|
|[Krok 2: Vytvořte náhodný problém s přidáním](../ide/step-2-create-a-random-addition-problem.md)|Vytvořte problém sčítání a použijte třídu `Random` pro generování náhodných čísel.|
|[Krok 3: Přidejte časovač odpočítávání](../ide/step-3-add-a-countdown-timer.md)|Přidejte časovač odpočítávání, aby kvíz mohl být časovým limitem.|
|[Krok 4: Přidejte metodu CheckTheAnswer()](../ide/step-4-add-the-checktheanswer-parens-method.md)|Přidejte metodu pro kontrolu, zda autor kvízu zadal správnou odpověď pro daný problém.|
|[Krok 5: Přidejte obslužné rutiny události pro ovládací prvky NumericUpDown](../ide/step-5-add-enter-event-handlers-for-the-numericupdown-controls.md)|Přidejte obslužné rutiny událostí, které usnadňují podobuní kvízu.|
|[Krok 6: Přidejte problém odečtení](../ide/step-6-add-a-subtraction-problem.md)|Přidejte problém odčítání, který generuje náhodná čísla, používá časovač a kontroluje správné odpovědi.|
|[Krok 7: Přidejte problémy násobení a dělení](../ide/step-7-add-multiplication-and-division-problems.md)|Přidejte problémy násobení a dělení, které generují náhodná čísla, použijte časovač a vyhledejte správné odpovědi.|
|[Krok 8: Přizpůsobení kvízu](../ide/step-8-customize-the-quiz.md)|Vyzkoušejte jiné funkce, jako je například změna barev a přidání nápovědy.|
