---
title: 'Krok 10: Napište kód pro další tlačítka a zaškrtávací políčko'
ms.date: 08/30/2019
ms.assetid: 185cf370-ab39-4ac0-b6bc-601d5b95a4a2
ms.topic: tutorial
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
dev_langs:
- CSharp
- VB
author: ornellaalt
ms.author: ornella
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e0dc7281b51d0efe0d19020df6a154e332ad9bb0
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/20/2020
ms.locfileid: "77579435"
---
# <a name="step-10-write-code-for-additional-buttons-and-a-check-box"></a>Krok 10: Napište kód pro další tlačítka a zaškrtávací políčko

Nyní jste připraveni dokončit další čtyři metody. Tento kód můžete zkopírovat a vložit, ale pokud se chcete z tohoto kurzu dozvědět nejvíce, zadejte kód a použijte technologie IntelliSense.

Tento kód přidává funkce tlačítka, která jste přidali dříve. Bez tohoto kódu tlačítka nic nedělají. Tlačítka používají kód <xref:System.Windows.Forms.Control.Click> v jejich události (a <xref:System.Windows.Forms.CheckBox.CheckedChanged> zaškrtávací políčko používá událost) dělat různé věci při aktivaci ovládacích prvků. Například `clearButton_Click` `ClearButton_Click`(nebo ) událost, která se aktivuje, když zvolíte tlačítko Vymazat **obrázek,** vymaže aktuální obrázek nastavením **vlastnosti Image** na **hodnotu null** (nebo **nic).** Každá událost v kódu obsahuje komentáře, které vysvětlují, co kód dělá.

> [!TIP]
> Osvědčenýpostup: Vždy okomentářujte svůj kód. Komentáře jsou informace pro osobu ke čtení, a to stojí za to čas, aby se váš kód srozumitelný. Aplikace ignoruje vše na řádku komentáře. V jazyce C# můžete komentovat řádek zadáním dvou lomítka na začátku (//) a v jazyce Visual Basic můžete komentovat řádek začínajícím jedním uvozovkovým uvozovkami (').

## <a name="how-to-write-code-for-additional-buttons-and-a-check-box"></a>Jak napsat kód pro další tlačítka a zaškrtávací políčko

Přidejte následující kód do souboru kódu **Form1** (*Form1.cs* nebo *Form1.vb*).

  [!INCLUDE [devlang-control-csharp-vb](./includes/devlang-control-csharp-vb.md)]

  [!code-csharp[VbExpressTutorial1Step9_10#2](../ide/codesnippet/CSharp/step-10-write-code-for-additional-buttons-and-a-check-box_1.cs)]

  [!code-vb[VbExpressTutorial1Step9_10#2](../ide/codesnippet/VisualBasic/step-10-write-code-for-additional-buttons-and-a-check-box_1.vb)]

> [!NOTE]
> Váš kód nemusí zobrazovat písmena camelCase.

## <a name="next-steps"></a>Další kroky

* Další krok kurzu najdete v **[tématu Krok 11: Spuštění aplikace a vyzkoušení dalších funkcí](../ide/step-11-run-your-program-and-try-other-features.md)**.

* Chcete-li se vrátit k předchozímu kroku kurzu, [přečtěte si krok 9: Kontrola, komentář a testování kódu](../ide/step-9-review-comment-and-test-your-code.md).

## <a name="see-also"></a>Viz také

* [Kurz 2: Vytvoření časovaného matematického kvízu](tutorial-2-create-a-timed-math-quiz.md)
* [Tutorial 3: Vytvoření odpovídající hry](tutorial-3-create-a-matching-game.md)
