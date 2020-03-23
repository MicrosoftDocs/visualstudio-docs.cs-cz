---
title: Jak se pohybovat v ide
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- environments [Visual Studio], navigation
- documents [Visual Studio], navigating
- IDE, navigation
- navigation [Visual Studio]
- files [Visual Studio], navigating between
- windows [Visual Studio], navigating
- Window.NextDocumentWindowNav
- IDE navigator
ms.assetid: 6c36b6eb-c93f-496b-af08-4199f7afd8bd
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 2febdedf5cf472132de936c37cad787df3d77518
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "75590992"
---
# <a name="how-to-move-around-in-the-visual-studio-ide"></a>Postup: Pohyb v ide sady Visual Studio

Integrované vývojové prostředí (IDE) bylo navrženo tak, aby vám umožnilo přecházet z okna do okna a souboru do souboru několika různými způsoby v závislosti na vašich preferencích nebo požadavcích na projekt. Můžete se rozhodnout cykonovat otevřené soubory v editoru nebo cykonožovat všechna aktivní okna nástrojů v rozhraní IDE. Můžete také přepnout přímo na libovolný soubor otevřený v editoru, bez ohledu na pořadí, ve kterém byl naposledy přístupný. Tyto funkce mohou pomoci zvýšit produktivitu při práci v ide.

> [!NOTE]
> Možnosti dostupné v dialogových oknech a názvy a umístění příkazů nabídky, které vidíte, se mohou lišit od toho, co je popsáno v tomto článku, v závislosti na aktivním nastavení nebo edici. Tento článek byl napsán s **ohledem na obecné** nastavení. Chcete-li změnit nastavení, například **na Obecné** nebo Vizuální **nastavení c++,** zvolte **Nástroje** > **Import a export nastavení**a pak zvolte Obnovit všechna **nastavení**.

## <a name="keyboard-shortcuts"></a>Klávesové zkratky

Téměř každý příkaz nabídky v sadě Visual Studio má klávesovou zkratku. Můžete také vytvořit vlastní zástupce. Další informace naleznete v [tématu Identifikace a přizpůsobení klávesových zkratek](../ide/identifying-and-customizing-keyboard-shortcuts-in-visual-studio.md).

## <a name="navigate-among-files-in-the-editor"></a>Navigace mezi soubory v editoru

Můžete použít několik metod pro procházení souborů otevřených v editoru. Můžete se přesouvat mezi soubory na základě pořadí, ve kterém k nim přistupujete, pomocí navigátoru IDE rychle najít libovolný aktuálně otevřený soubor nebo dobře připnout oblíbené soubory na kartu, aby byly vždy viditelné.

Procházejte vpřed a procházejte otevřenými soubory v editoru na základě pořadí, ve kterém byly zpřístupněny, podobně jako v aplikaci Historie zobrazení v aplikaci Microsoft Internet Explorer.

### <a name="to-move-through-open-files-in-order-of-use"></a>Procházení otevřených souborů v pořadí použití

- Chcete-li aktivovat otevřené dokumenty v pořadí, v jakém se jich naposledy dotkli, stiskněte **kombinaci kláves** + **-** (pomlčka).

- Chcete-li otevřít dokumenty v opačném pořadí, stiskněte **kombinaci kláves Ctrl**+**Shift** + **-** (pomlčka).

    > [!NOTE]
    > **Přejít vzad** a **navigovat vpřed** také lze nalézt v nabídce **Zobrazení.**

Můžete také přepnout na určitý soubor otevřený v editoru, bez ohledu na to, kdy jste k souboru naposledy přistupovali, pomocí **navigátoru IDE**, seznamu **Aktivní soubory** v editoru nebo dialogového okna **Windows.**

**IDE Navigator** funguje podobně jako přepínač aplikací systému Windows. Není k dispozici z nabídek a lze k němu přistupovat pouze pomocí klávesových zkratek. Můžete použít jeden ze dvou příkazů pro přístup k **IDE Navigator** (viz níže) pro cyklují soubory, v závislosti na pořadí, ve kterém chcete cyklu prostřednictvím.

![Navigátor IDE sady Visual Studio](../ide/media/vs2015_ide_navigator.png)

`Window.PreviousDocumentWindowNav`umožňuje přesunout do souboru, který `Window.NextDocumentWindowNav` byl naposledy zpřístupněn, a umožňuje přesun v opačném pořadí. **Obecné nastavení vývoje** přiřadí **shift**+**alt**+**f7** `Window.PreviousDocumentWindowNav` a **alt**+**f7** na `Window.NextDocumentWindowNav`.

> [!NOTE]
> Pokud kombinace nastavení, kterou používáte, ještě nemá k tomuto příkazu přiřazenou kombinaci klávesových zkratek, můžete přiřadit vlastní příkaz pomocí stránky **Klávesnice** v dialogovém okně **Možnosti.** Další informace naleznete v [tématu Identifikace a přizpůsobení klávesových zkratek](../ide/identifying-and-customizing-keyboard-shortcuts-in-visual-studio.md).

### <a name="to-switch-to-specific-files-in-the-editor"></a>Přepnutí na určité soubory v editoru

- Stisknutím **klávesy Ctrl**+**zobrazte** **navigátor IDE Navigator**. Podržte stisknutou klávesu **Ctrl** a opakovaně stiskněte **klávesu Tab,** dokud nevyberete soubor, na který chcete přepnout.

    > [!TIP]
    > Chcete-li obrátit pořadí procházení seznamu **Aktivní soubory,** podržte klávesy **Ctrl**+**Shift** a stiskněte **klávesu Tab**.

    \-nebo -

- V pravém horním rohu editoru zvolte tlačítko **Aktivní soubory** a pak vyberte soubor ze seznamu, na který chcete přepnout.

    \-nebo -

- Na řádku nabídek zvolte **Okna** > **Okna**.

- V seznamu vyberte soubor, který chcete zobrazit, a pak zvolte **Aktivovat**.

## <a name="navigate-among-tool-windows-in-the-ide"></a>Navigace mezi okny nástrojů v prostředí IDE

**Navigátor IDE** také umožňuje cykonoběh přes okna nástrojů, které máte otevřené v ide. Můžete použít jeden ze dvou příkazů pro přístup k **navigátoru IDE** pro cyklické procházení oken nástrojů, v závislosti na pořadí, ve kterém chcete cyklu. `Window.PreviousToolWindowNav`umožňuje přesunout do souboru, který `Window.NextToolWindowNav` byl naposledy zpřístupněn, a umožňuje přesun v opačném pořadí. **Obecné nastavení vývoje** přiřadí **shift**+**alt**+**f7** `Window.PreviousDocumentWindowNav` a **alt**+**f7** na `Window.NextDocumentWindowNav`.

> [!NOTE]
> Pokud kombinace nastavení, kterou používáte, ještě nemá k tomuto příkazu přiřazenou kombinaci klávesových zkratek, můžete přiřadit vlastní příkaz pomocí stránky **Klávesnice** v dialogovém okně **Možnosti.** Další informace naleznete v [tématu Identifikace a přizpůsobení klávesových zkratek](../ide/identifying-and-customizing-keyboard-shortcuts-in-visual-studio.md).

### <a name="to-switch-to-a-specific-tool-window-in-the-ide"></a>Přepnutí do konkrétního okna nástroje v ide

- Stisknutím **klávesy Alt**+**F7** zobrazte **navigátor IDE Navigator**. Podržte stisknutou klávesu **Alt** a opakovaně stiskněte **klávesu F7,** dokud nevyberete okno, do které chcete přepnout.

    > [!TIP]
    > Chcete-li obrátit pořadí, ve kterém procházíte **seznamem aktivních nástrojů systému Windows,** podržte klávesy **Shift**+**Alt** a stiskněte **klávesu F7**.

## <a name="see-also"></a>Viz také

- [Přizpůsobení rozložení oken](../ide/customizing-window-layouts-in-visual-studio.md)
- [Výchozí klávesové zkratky](../ide/default-keyboard-shortcuts-in-visual-studio.md)
