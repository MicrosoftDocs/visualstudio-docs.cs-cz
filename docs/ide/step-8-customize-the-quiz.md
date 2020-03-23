---
title: 'Krok 8: Přizpůsobení kvízu'
ms.date: 11/04/2016
ms.topic: tutorial
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
dev_langs:
- CSharp
- VB
ms.assetid: dc8edb13-1b23-47d7-b859-8c6f7888c1a9
author: ornellaalt
ms.author: ornella
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e568a9fa844802ddab934264cbc316d3514fe577
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/20/2020
ms.locfileid: "77579365"
---
# <a name="step-8-customize-the-quiz"></a>Krok 8: Přizpůsobení kvízu

V poslední části tutoriálu prozkoumáte několik způsobů, jak kvíz přizpůsobit a rozšíříte si již nabyté znalosti. Například se zamyslíte nad tím, jak program vytvoří problém náhodného dělení, jehož odpovědí není nikdy zlomek. Chcete-li se `timeLabel` dozvědět více, otočte ovládací prvek jinou barvou a dejte příjemci kvízu nápovědu.

> [!NOTE]
> Toto téma je součástí série kurzů o základních konceptech kódování. Přehled kurzu najdete v [tématu Výuka 2: Vytvoření časovaného matematického kvízu](../ide/tutorial-2-create-a-timed-math-quiz.md).

## <a name="to-customize-the-quiz"></a>Přizpůsobení kvízu

- Když v kvízu zbývá pouze pět sekund, otočte ovládací prvek **timeLabel** červeně nastavením jeho vlastnosti **BackColor.**

  ```csharp
  timeLabel.BackColor = Color.Red;
  ```

  ```vb
  timeLabel.BackColor = Color.Red
  ```

  [!INCLUDE [devlang-control-csharp-vb](./includes/devlang-control-csharp-vb.md)]

  Po dokončení kvízu vynulujte barvu.

- Dejte příjemci kvízu nápovědu tím, že přehrajete <xref:System.Windows.Forms.NumericUpDown> zvuk, když je do ovládacího prvku zadána správná odpověď. (Pro každou událost ovládacího prvku <xref:System.Windows.Forms.NumericUpDown.ValueChanged> je nutné napsat obslužnou rutinu události, která se vyvolá vždy, když účastník kvízu změní hodnotu ovládacího prvku.)

## <a name="to-continue-or-review"></a>Chcete-li pokračovat nebo přezkoumat

- Chcete-li přejít k dalšímu kurzu, **[přečtěte si informace o tématu Návod 3: Vytvoření odpovídající hry](../ide/tutorial-3-create-a-matching-game.md)**.

- Chcete-li se vrátit k předchozímu kroku kurzu, [přečtěte si krok 7: Přidání problémů s násobením a dělením](../ide/step-7-add-multiplication-and-division-problems.md).
