---
title: 'Krok 10: napište kód pro další tlačítka a zaškrtávací políčko'
ms.date: 08/30/2019
ms.assetid: 185cf370-ab39-4ac0-b6bc-601d5b95a4a2
ms.topic: tutorial
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
dev_langs:
- CSharp
- VB
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 414e477dcc2e7b3bd4fcde6c82fe6c0ef77f1df0
ms.sourcegitcommit: f3f668ecaf11b4c2738ebc91923c6b5e38e74670
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/16/2020
ms.locfileid: "76113375"
---
# <a name="step-10-write-code-for-additional-buttons-and-a-check-box"></a>Krok 10: napište kód pro další tlačítka a zaškrtávací políčko

Nyní jste připraveni provést další čtyři metody. Tento kód můžete zkopírovat a vložit, ale pokud se chcete dozvědět nejvíc od tohoto kurzu, zadejte kód a použijte technologii IntelliSense.

Tento kód přidá funkce do tlačítek, které jste přidali dříve. Bez tohoto kódu nejsou tlačítka dělat nic. Tlačítka používají kód v jejich <xref:System.Windows.Forms.Control.Click>ch událostech (a zaškrtávací políčko používá událost <xref:System.Windows.Forms.CheckBox.CheckedChanged>) k provedení různých akcí při aktivaci ovládacích prvků. Například událost `clearButton_Click` (nebo `ClearButton_Click`), která se aktivuje po kliknutí na tlačítko **Vymazat obrázek** , vymaže aktuální obrázek nastavením vlastnosti **Image** na **hodnotu null** (nebo, **Nothing**). Každá událost v kódu obsahuje komentáře, které vysvětlují, co kód dělá.

> [!TIP]
> Osvědčený postup: vždy komentovat kód. Komentáře jsou informace, které uživatel přečte, a je to čas, kdy se váš kód může pochopit. Vše na řádku komentáře ignoruje aplikace. V C#aplikaci můžete zadat komentář k řádku zadáním dvou lomítka na začátku (//) a v Visual Basic přidáte komentář k řádku, který začíná jednoduchou uvozovkou (').

## <a name="how-to-write-code-for-additional-buttons-and-a-check-box"></a>Postup psaní kódu pro další tlačítka a zaškrtávací políčko

Přidejte následující kód do souboru kódu **Form1** (*Form1.cs* nebo *Form1. vb*).

  [!INCLUDE [devlang-control-csharp-vb](./includes/devlang-control-csharp-vb.md)]

  [!code-csharp[VbExpressTutorial1Step9_10#2](../ide/codesnippet/CSharp/step-10-write-code-for-additional-buttons-and-a-check-box_1.cs)]

  [!code-vb[VbExpressTutorial1Step9_10#2](../ide/codesnippet/VisualBasic/step-10-write-code-for-additional-buttons-and-a-check-box_1.vb)]

> [!NOTE]
> Váš kód nemusí zobrazovat písmena "camelCase".

## <a name="next-steps"></a>Další kroky

* Pokud chcete přejít na další krok kurzu, přečtěte si **[Krok 11: spuštění aplikace a zkuste použít jiné funkce](../ide/step-11-run-your-program-and-try-other-features.md)** .

* Pokud se chcete vrátit k předchozímu kroku kurzu, přečtěte si [Krok 9: kontrola, komentář a testování kódu](../ide/step-9-review-comment-and-test-your-code.md).

## <a name="see-also"></a>Viz také:

* [Kurz 2: vytvoření časovaného matematického kvízu](tutorial-2-create-a-timed-math-quiz.md)
* [Kurz 3: vytvoření porovnávací hry](tutorial-3-create-a-matching-game.md)
