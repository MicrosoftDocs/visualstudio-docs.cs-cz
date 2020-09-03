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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "74299864"
---
# <a name="tutorial-2-create-a-timed-math-quiz"></a>Tutoriál 2: Vytvoření matematického kvízu s časovým limitem
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

V tomto kurzu sestavíte kvíz, ve kterém musí příjemce kvízu odpovědět na čtyři náhodné aritmetické úlohy v určeném čase. Získáte informace o těchto tématech:

- Generujte náhodná čísla pomocí `Random` třídy.

- Aktivovat události, ke kterým dojde v určitém čase pomocí ovládacího prvku **Timer** .

- Řízení toku programu pomocí `if else` příkazů.

- V kódu provádějte základní aritmetické operace.

  Po dokončení bude kvíz vypadat jako na následujícím obrázku, s výjimkou různých čísel.

  ![Matematický kvíz se čtyřmi problémy](../ide/media/express-finishedquiz.png "Express_FinishedQuiz") Kvíz, který vytvoříte v tomto kurzu

> [!NOTE]
> Tento kurz se zabývá jazykem Visual C# i Visual Basic, takže se zaměřte na informace, které jsou specifické pro programovací jazyk, který používáte.

## <a name="related-topics"></a>Související témata

|Nadpis|Popis|
|-----------|-----------------|
|[Krok 1: vytvoření projektu a Přidání popisků do formuláře](../ide/step-1-create-a-project-and-add-labels-to-your-form.md)|Začněte vytvořením projektu, změnou vlastností a přidáním `Label` ovládacích prvků.|
|[Krok 2: vytvoření náhodného přidání problému](../ide/step-2-create-a-random-addition-problem.md)|Vytvořte problém sčítání a použijte `Random` třídu pro generování náhodných čísel.|
|[Krok 3: přidejte časovač odpočítávání](../ide/step-3-add-a-countdown-timer.md)|Přidejte časovač odpočítávání, aby kvíz mohl být časovým limitem.|
|[Krok 4: Přidání metody metodu CheckTheAnswer ()](../ide/step-4-add-the-checktheanswer-parens-method.md)|Přidejte metodu pro kontrolu, zda autor kvízu zadal správnou odpověď pro daný problém.|
|[Krok 5: přidejte obslužné rutiny událostí Enter pro ovládací prvky NumericUpDown](../ide/step-5-add-enter-event-handlers-for-the-numericupdown-controls.md)|Přidejte obslužné rutiny událostí, které usnadňují podobuní kvízu.|
|[Krok 6: Přidání problému odčítání](../ide/step-6-add-a-subtraction-problem.md)|Přidejte problém odčítání, který generuje náhodná čísla, používá časovač a kontroluje správné odpovědi.|
|[Krok 7: přidejte problémy násobení a dělení](../ide/step-7-add-multiplication-and-division-problems.md)|Přidejte problémy násobení a dělení, které generují náhodná čísla, použijte časovač a vyhledejte správné odpovědi.|
|[Krok 8: Přizpůsobení kvízu](../ide/step-8-customize-the-quiz.md)|Vyzkoušejte jiné funkce, jako je například změna barev a přidání nápovědy.|
