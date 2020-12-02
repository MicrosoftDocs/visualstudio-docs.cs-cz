---
title: 'Krok 3: Nastavení vlastností formuláře'
description: Naučte se, jak pomocí okno Vlastnosti změnit vzhled formuláře.
ms.custom: SEO-VS-2020
ms.date: 08/30/2019
ms.assetid: 634ef037-1525-48c8-ac7f-abf04be69376
ms.topic: tutorial
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
author: ornellaalt
ms.author: ornella
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 0b858ed302c7fe89049585edb7cc5c4391a4789b
ms.sourcegitcommit: df6ba39a62eae387e29f89388be9e3ee5ceff69c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2020
ms.locfileid: "96480613"
---
# <a name="step-3-set-your-form-properties"></a>Krok 3: Nastavení vlastností formuláře

Dále pomocí okna **vlastnosti** změníte vzhled formuláře.

## <a name="how-to-set-your-form-properties"></a>Nastavení vlastností formuláře

1. Ujistěte se, že se díváte na **Návrhář formulářů**. V integrovaném vývojovém prostředí (IDE) sady Visual Studio vyberte kartu **Form1.cs [Design]** (nebo kartu **Form1. vb [design]** v Visual Basic).

1. Zvolte libovolné místo uvnitř formuláře **Form1** a vyberte ho. Podívejte se na okno **vlastnosti** , ve kterém by se teď měly zobrazovat vlastnosti formuláře. Formuláře mají různé vlastnosti. Například můžete nastavit barvu popředí a pozadí, text nadpisu, který se zobrazí v horní části formuláře, velikost formuláře a další vlastnosti.

   > [!NOTE]
   > Pokud se okno **vlastnosti** nezobrazí, zastavte aplikaci výběrem čtvercového tlačítka **Zastavit ladění** na panelu nástrojů nebo pouhým zavřením okna. Pokud je aplikace zastavena a stále nevidíte okno **vlastnosti** , v řádku nabídek vyberte možnost **Zobrazit**  >  **okno vlastností**.

1. Po výběru formuláře vyhledejte vlastnost **text** v okně **vlastnosti** . V závislosti na tom, jak je seznam seřazený, se možná budete muset posunout dolů. Zvolte **text**, zadejte **Prohlížeč obrázků** a pak zvolte **ENTER**.  Formulář by měl mít nyní v záhlaví text **Viewer** a okno **vlastnosti** by mělo vypadat podobně jako na následujícím snímku obrazovky.

    ![Vlastnosti – okno](../ide/media/express_edittextproperty.png)<br>
   **_Vlastnosti_* _ _window *

   > [!NOTE]
   > Vlastnosti lze seřadit podle **kategorií** nebo zobrazení podle **abecedy** . Mezi těmito dvěma zobrazeními můžete přepínat pomocí tlačítek v okně **vlastnosti** . V tomto kurzu je snazší najít vlastnosti pomocí **abecedního** zobrazení.

1. Vraťte se na **Návrhář formulářů**. Vyberte táhlo v pravém dolním rohu formuláře, což je malé bílé čtverce v pravém dolním rohu formuláře a zobrazí se takto.

    ![Přetáhněte popisovač](../ide/media/express_bottomrt_drag.png)<br>
   *Přetáhněte popisovač*

    Přetažením úchytu můžete změnit velikost formuláře, takže je formulář širší a trochu vyšší.

1. Podívejte se na okno **vlastnosti** a Všimněte si, že se změnila vlastnost **Size** . Vlastnost **Size** se změní pokaždé, když změníte velikost formuláře. Zkuste přetáhnout táhlo formuláře, aby se změnila velikost formuláře přibližně **550, 350** (není potřeba přesně), což by mělo pro tento projekt dobře fungovat. Alternativně můžete zadat hodnoty přímo do vlastnosti **Size** a pak zvolit klávesu **ENTER** .

1. Spusťte aplikaci znovu. Nezapomeňte, že ke spuštění vaší aplikace můžete použít kteroukoli z následujících metod.

   - Klikněte na klávesu **F5** .

   - Na panelu nabídek vyberte **ladit**  >  **Spustit ladění**.

   - Na panelu nástrojů klikněte na tlačítko **Spustit ladění** , které se zobrazí takto.

      ![Spustit ladění – tlačítko panelu nástrojů](../ide/media/express_icondebug.png)<br>
     **_Spustit ladění_* _ _toolbar tlačítko *

     Stejně jako předtím, rozhraní IDE sestaví a spustí vaši aplikaci a zobrazí se okno.

1. Než budete pokračovat k dalšímu kroku, zastavte aplikaci, protože rozhraní IDE vám neumožní změnit vaši aplikaci, když je spuštěná. Nezapomeňte, že k zastavení vaší aplikace můžete použít kteroukoli z následujících metod.

   - Na panelu nástrojů klikněte na tlačítko **Zastavit ladění** .

   - Na řádku nabídek klikněte na položku **ladit**  >  **Zastavit ladění**.

   - Použijte klávesnici a stiskněte **SHIFT** + **F5**.

   - V horním rohu okna **Prohlížeč obrázků** klikněte na tlačítko **X** .

## <a name="next-steps"></a>Další kroky

* Chcete-li přejít na další krok kurzu, viz **[Krok 4: rozložení formuláře pomocí ovládacího prvku TableLayoutPanel](../ide/step-4-lay-out-your-form-with-a-tablelayoutpanel-control.md)**.

* Pokud se chcete vrátit k předchozímu kroku kurzu, přečtěte si [článek krok 2: spuštění aplikace v prohlížeči obrázků](../ide/step-2-run-your-program.md).

## <a name="see-also"></a>Viz také

* [Kurz 2: vytvoření časovaného matematického kvízu](tutorial-2-create-a-timed-math-quiz.md)
* [Kurz 3: vytvoření porovnávací hry](tutorial-3-create-a-matching-game.md)
