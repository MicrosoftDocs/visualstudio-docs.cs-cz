---
title: 'Krok 3: Nastavení vlastností formuláře'
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
ms.openlocfilehash: 82dbef4baee72be8ff96f83e436b2587e9a020ea
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/20/2020
ms.locfileid: "77579865"
---
# <a name="step-3-set-your-form-properties"></a>Krok 3: Nastavení vlastností formuláře

Dále můžete změnit vzhled formuláře pomocí okna **Vlastnosti.**

## <a name="how-to-set-your-form-properties"></a>Jak nastavit vlastnosti formuláře

1. Ujistěte se, že se díváte na **Windows Forms Designer**. V integrovaném vývojovém prostředí sady Visual Studio (IDE) zvolte **kartu Form1.cs [Design]** (nebo kartu **Form1.vb [Design]** v jazyce Visual Basic).

1. Vyberte jej kdekoli ve formuláři **Formulář1.** Podívejte se na **okno Vlastnosti,** které by nyní mělo zobrazovat vlastnosti formuláře. Formuláře mají různé vlastnosti. Můžete například nastavit barvu popředí a pozadí, text nadpisu, který se zobrazí v horní části formuláře, velikost formuláře a další vlastnosti.

   > [!NOTE]
   > Pokud se okno **Vlastnosti** nezobrazí, zastavte aplikaci tak, že na panelu nástrojů vyberete čtvercové tlačítko **Zastavit ladění** nebo okno zavřete. Pokud je aplikace zastavená a stále se nezobrazuje okno **Vlastnosti,** na řádku nabídek zvolte **Zobrazit** > **okno vlastnosti**.

1. Po výběru formuláře vyhledejte vlastnost **Text** v okně **Vlastnosti.** V závislosti na způsobu řazení seznamu může být nutné posunout se dolů. Zvolte **Text**, zadejte **Prohlížeč obrázků**a pak zvolte **Enter**.  Formulář by nyní měl mít textový **prohlížeč obrázků** v záhlaví a okno **Vlastnosti** by mělo vypadat podobně jako na následujícím snímku obrazovky.

    ![Okno Vlastnosti](../ide/media/express_edittextproperty.png)<br>
   ***Okno Vlastnosti*** *window*

   > [!NOTE]
   > Vlastnosti lze seřadit podle **zobrazení kategorizovaného** nebo **abecedního.** Mezi těmito dvěma zobrazeními můžete přepínat pomocí tlačítek v okně **Vlastnosti.** V tomto kurzu je snazší najít vlastnosti prostřednictvím **abecednízobrazení.**

1. Vraťte se do **návrháře formulářů systému Windows**. Zvolte pravé dolní táhlo formuláře, což je malý bílý čtverec v pravém dolním provedení formuláře a zobrazí se následujícím způsobem.

    ![Táhlo přetažení](../ide/media/express_bottomrt_drag.png)<br>
   *Táhlo přetažení*

    Přetažením táhla změňte velikost formuláře tak, aby byl formulář širší a o něco vyšší.

1. Podívejte se na **okno Vlastnosti** a všimněte si, že **size** vlastnost se změnila. Vlastnost **Size** se změní při každé změně velikosti formuláře. Zkuste přetáhnout popisovač formuláře a změnit jeho velikost na velikost formuláře přibližně **550, 350** (není třeba být přesný), což by mělo pro tento projekt dobře fungovat. Jako alternativu můžete zadat hodnoty přímo do vlastnosti **Size** a pak zvolit **enter** klíč.

1. Spusťte aplikaci znovu. Nezapomeňte, že ke spuštění aplikace můžete použít některou z následujících metod.

   - Zvolte klávesu **F5.**

   - Na řádku nabídek zvolte **Ladění** > **ladění startování**.

   - Na panelu nástrojů zvolte tlačítko **Spustit ladění,** které se zobrazí následujícím způsobem.

      ![Tlačítko Spustit ladění panelu nástrojů](../ide/media/express_icondebug.png)<br>
     ***Tlačítko Spustit ladění panelu*** *nástrojů*

     Stejně jako dříve ide sestaví a spustí vaši aplikaci a zobrazí se okno.

1. Než přejdete k dalšímu kroku, zastavte aplikaci, protože ide vám nedovolí změnit aplikaci, když je spuštěná. Nezapomeňte, že k zastavení aplikace můžete použít některou z následujících metod.

   - Na panelu nástrojů zvolte tlačítko **Zastavit ladění.**

   - Na řádku nabídek zvolte **Ladění ladění** > **stop**.

   - Použijte klávesnici a stiskněte **Shift**+**F5**.

   - V horním rohu okna Prohlížeč **obrázků** zvolte tlačítko **X.**

## <a name="next-steps"></a>Další kroky

* Další krok kurzu najdete v **[tématu Krok 4: Rozložení formuláře pomocí ovládacího prvku TableLayoutPanel](../ide/step-4-lay-out-your-form-with-a-tablelayoutpanel-control.md)**.

* Pokud se chcete vrátit k předchozímu kroku kurzu, [přečtěte si obrázek 2: Spuštění aplikace prohlížeč obrázků](../ide/step-2-run-your-program.md).

## <a name="see-also"></a>Viz také

* [Kurz 2: Vytvoření časovaného matematického kvízu](tutorial-2-create-a-timed-math-quiz.md)
* [Tutorial 3: Vytvoření odpovídající hry](tutorial-3-create-a-matching-game.md)
