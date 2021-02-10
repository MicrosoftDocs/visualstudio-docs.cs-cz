---
title: 'Krok 8: Přizpůsobení kvízu'
description: Naučte se, jak ovládací prvek timeLabel zapnout jinou barvu a dát pomocnému kvízu.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 727d880caf912441009bda66bf516d501bd7303f
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99969643"
---
# <a name="step-8-customize-the-quiz"></a>Krok 8: Přizpůsobení kvízu

V poslední části tutoriálu prozkoumáte několik způsobů, jak kvíz přizpůsobit a rozšíříte si již nabyté znalosti. Například se zamyslíte nad tím, jak program vytvoří problém náhodného dělení, jehož odpovědí není nikdy zlomek. Chcete-li získat další informace, přepněte `timeLabel` ovládací prvek na jinou barvu a dejte pomocnému kvízu.

> [!NOTE]
> Toto téma je součástí série kurzů o základních konceptech kódování. Přehled tohoto kurzu najdete v tématu [kurz 2: vytvoření časovaného matematického kvízu](../ide/tutorial-2-create-a-timed-math-quiz.md).

## <a name="to-customize-the-quiz"></a>Přizpůsobení kvízu

- Pokud je v kvízu ponecháno pouze pět sekund, zapněte ovládací prvek **timeLabel** Red nastavením jeho vlastnosti **BackColor** .

  ```csharp
  timeLabel.BackColor = Color.Red;
  ```

  ```vb
  timeLabel.BackColor = Color.Red
  ```

  [!INCLUDE [devlang-control-csharp-vb](./includes/devlang-control-csharp-vb.md)]

  Resetovat barvu při překročení kvízu.

- Dejte tomuto kvízu pokyn, aby pomohli přehrání zvuku při zadání správné odpovědi do <xref:System.Windows.Forms.NumericUpDown> ovládacího prvku. (Pro každou událost ovládacího prvku <xref:System.Windows.Forms.NumericUpDown.ValueChanged> je nutné napsat obslužnou rutinu události, která se vyvolá vždy, když účastník kvízu změní hodnotu ovládacího prvku.)

## <a name="to-continue-or-review"></a>Chcete-li pokračovat nebo přezkoumat

- Pokud chcete přejít k dalšímu kurzu, přečtěte si **[kurz 3: vytvoření vyhovující hry](../ide/tutorial-3-create-a-matching-game.md)**.

- Chcete-li se vrátit k předchozímu kroku kurzu, přečtěte si [Krok 7: Přidání problémů násobení a dělení](../ide/step-7-add-multiplication-and-division-problems.md).
