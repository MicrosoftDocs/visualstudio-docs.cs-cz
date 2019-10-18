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
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: cee7b855256f352c9ac9ed39994191f4a9e6d946
ms.sourcegitcommit: 98b02f87c7aa1f5eb7f0d1c86bfa36efa8580c57
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/15/2019
ms.locfileid: "72314207"
---
# <a name="step-8-customize-the-quiz"></a>Krok 8: Přizpůsobení kvízu

V poslední části tutoriálu prozkoumáte několik způsobů, jak kvíz přizpůsobit a rozšíříte si již nabyté znalosti. Například se zamyslíte nad tím, jak program vytvoří problém náhodného dělení, jehož odpovědí není nikdy zlomek. Chcete-li získat další informace, převeďte `timeLabel` ovládacího prvku jinou barvu a poskytněte pomocnému kvízu.

> [!NOTE]
> Toto téma je součástí série kurzů o základních konceptech kódování.
> - Přehled tohoto kurzu najdete v tématu [kurz 2: vytvoření časovaného matematického kvízu](../ide/tutorial-2-create-a-timed-math-quiz.md).
> - Chcete-li stáhnout dokončenou verzi kódu, přečtěte si [ukázku kurzu dokončení matematického kvízu](https://code.msdn.microsoft.com/Complete-Math-Quiz-8581813c).

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

- Dejte kvízu, aby podala pokyn přehráním zvuku při zadání správné odpovědi do ovládacího prvku <xref:System.Windows.Forms.NumericUpDown>. (Pro každou událost ovládacího prvku <xref:System.Windows.Forms.NumericUpDown.ValueChanged> je nutné napsat obslužnou rutinu události, která se vyvolá vždy, když účastník kvízu změní hodnotu ovládacího prvku.)

## <a name="to-continue-or-review"></a>Chcete-li pokračovat nebo přezkoumat

- Pokud chcete přejít k dalšímu kurzu, přečtěte si **[kurz 3: vytvoření vyhovující hry](../ide/tutorial-3-create-a-matching-game.md)** .

- Chcete-li se vrátit k předchozímu kroku kurzu, přečtěte si [Krok 7: Přidání problémů násobení a dělení](../ide/step-7-add-multiplication-and-division-problems.md).
