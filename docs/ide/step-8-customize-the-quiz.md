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
ms.openlocfilehash: 402817ace34f12fb7659b7251cbe755d036ebc4b
ms.sourcegitcommit: 6eed0372976c0167b9a6d42ba443f9a474b8bb91
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2019
ms.locfileid: "71118646"
---
# <a name="step-8-customize-the-quiz"></a>Krok 8: Přizpůsobení kvízu

V poslední části tutoriálu prozkoumáte několik způsobů, jak kvíz přizpůsobit a rozšíříte si již nabyté znalosti. Například se zamyslíte nad tím, jak program vytvoří problém náhodného dělení, jehož odpovědí není nikdy zlomek. Chcete-li získat další informace `timeLabel` , přepněte ovládací prvek na jinou barvu a dejte pomocnému kvízu.

> [!NOTE]
> Toto téma je součástí série kurzů o základních konceptech kódování.
> - Přehled tohoto kurzu najdete v [kurzu 2: Vytvoření časovaného matematického](../ide/tutorial-2-create-a-timed-math-quiz.md)kvízu
> - Chcete-li stáhnout dokončenou verzi kódu, přečtěte si [ukázku kurzu dokončení matematického kvízu](https://code.msdn.microsoft.com/Complete-Math-Quiz-8581813c).

## <a name="to-customize-the-quiz"></a>Přizpůsobení kvízu

- Pokud je v kvízu ponecháno pouze pět sekund, zapněte ovládací prvek **timeLabel** Red nastavením jeho vlastnosti **BackColor** .

  ```csharp
  timeLabel.BackColor = Color.Red;
  ```

  ```vb
  timeLabel.BackColor = Color.Red
  ```

  > [!IMPORTANT]
  > Pomocí ovládacího prvku programovací jazyk v pravém horním rohu této stránky můžete zobrazit fragment C# kódu nebo Visual Basic fragment kódu.<br><br>![Řízení programovacího jazyka pro Docs.Microsoft.com](../ide/media/docs-programming-language-control.png)

  Resetovat barvu při překročení kvízu.

- Dejte tomuto kvízu pokyn, aby pomohli přehrání zvuku při zadání správné odpovědi do <xref:System.Windows.Forms.NumericUpDown> ovládacího prvku. (Pro každou událost ovládacího prvku <xref:System.Windows.Forms.NumericUpDown.ValueChanged> je nutné napsat obslužnou rutinu události, která se vyvolá vždy, když účastník kvízu změní hodnotu ovládacího prvku.)

## <a name="to-continue-or-review"></a>Chcete-li pokračovat nebo přezkoumat

- Pokud chcete přejít k dalšímu kurzu, přečtěte si  **[kurz 3: Vytvořte porovnávací hru](../ide/tutorial-3-create-a-matching-game.md).**

- Pokud se chcete vrátit k předchozímu kroku kurzu [, přečtěte si krok 7: Přidejte problémy](../ide/step-7-add-multiplication-and-division-problems.md)násobení a dělení.
