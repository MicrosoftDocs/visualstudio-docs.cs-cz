---
title: Napsání kódu pro přídavná tlačítka a zaškrtávací políčko
description: Naučte se psát kód pro další tlačítka a cheeck pole v kurzu Vytvoření prohlížeče obrázků.
ms.date: 08/30/2019
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: 4d66f7705821025bd5e30ea0d0c7f2dd57d540e4
ms.sourcegitcommit: 4ae5e9817ad13edd05425febb322b5be6d3c3425
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/11/2020
ms.locfileid: "90036909"
---
# <a name="step-10-write-code-for-additional-buttons-and-a-check-box"></a>Krok 10: Napsání kódu pro přídavná tlačítka a zaškrtávací políčko

Nyní jste připraveni provést další čtyři metody. Tento kód můžete zkopírovat a vložit, ale pokud se chcete dozvědět nejvíc od tohoto kurzu, zadejte kód a použijte technologii IntelliSense.

Tento kód přidá funkce do tlačítek, které jste přidali dříve. Bez tohoto kódu nejsou tlačítka dělat nic. Tlačítka používají kód ve svých <xref:System.Windows.Forms.Control.Click> událostech (a zaškrtávací políčko používá <xref:System.Windows.Forms.CheckBox.CheckedChanged> událost) k provedení různých akcí při aktivaci ovládacích prvků. Například `clearButton_Click` událost (nebo `ClearButton_Click` ), která se aktivuje po kliknutí na tlačítko **Vymazat obrázek** , vymaže aktuální obrázek nastavením jeho vlastnosti **Image** na **hodnotu null** (nebo, **Nothing**). Každá událost v kódu obsahuje komentáře, které vysvětlují, co kód dělá.

> [!TIP]
> Osvědčený postup: vždy komentovat kód. Komentáře jsou informace, které uživatel přečte, a je to čas, kdy se váš kód může pochopit. Vše na řádku komentáře ignoruje aplikace. V jazyce C# můžete zadat komentář k řádku zadáním dvou lomítek na začátku (//) a v Visual Basic přidáte komentář k řádku pomocí jednoduché uvozovky (').

## <a name="how-to-write-code-for-additional-buttons-and-a-check-box"></a>Postup psaní kódu pro další tlačítka a zaškrtávací políčko

Přidejte následující kód do souboru kódu **Form1** (*Form1.cs* nebo *Form1. vb*).

  [!INCLUDE [devlang-control-csharp-vb](./includes/devlang-control-csharp-vb.md)]

  [!code-csharp[VbExpressTutorial1Step9_10#2](../ide/codesnippet/CSharp/step-10-write-code-for-additional-buttons-and-a-check-box_1.cs)]

  [!code-vb[VbExpressTutorial1Step9_10#2](../ide/codesnippet/VisualBasic/step-10-write-code-for-additional-buttons-and-a-check-box_1.vb)]

> [!NOTE]
> Váš kód nemusí zobrazovat písmena "camelCase".

## <a name="next-steps"></a>Další kroky

* Pokud chcete přejít na další krok kurzu, přečtěte si **[Krok 11: spuštění aplikace a zkuste použít jiné funkce](../ide/step-11-run-your-program-and-try-other-features.md)**.

* Pokud se chcete vrátit k předchozímu kroku kurzu, přečtěte si [Krok 9: kontrola, komentář a testování kódu](../ide/step-9-review-comment-and-test-your-code.md).

## <a name="see-also"></a>Viz také

* [Kurz 2: vytvoření časovaného matematického kvízu](tutorial-2-create-a-timed-math-quiz.md)
* [Kurz 3: vytvoření porovnávací hry](tutorial-3-create-a-matching-game.md)
