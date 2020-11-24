---
title: Jak se pohybovat v integrovaném vývojovém prostředí (IDE)
description: Naučte se, jak se pohybovat v integrovaném vývojovém prostředí sady Visual Studio z okna do okna a souboru do souboru několika různými způsoby.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
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
ms.openlocfilehash: b8f2e796ed122bc4dba0c1fb4cfca85c74065fb8
ms.sourcegitcommit: d6207a3a590c9ea84e3b25981d39933ad5f19ea3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/24/2020
ms.locfileid: "95597038"
---
# <a name="how-to-move-around-in-the-visual-studio-ide"></a>Postupy: pohyb v integrovaném vývojovém prostředí sady Visual Studio

Integrované vývojové prostředí (IDE) bylo navrženo tak, aby bylo možné přesouvat z okna do okna a souboru do souboru několika různými způsoby v závislosti na požadavcích na preference nebo projektu. Můžete se rozhodnout přepínat v editoru otevřené soubory nebo cyklicky procházet všechna aktivní okna nástrojů v integrovaném vývojovém prostředí (IDE). Můžete také přepnout přímo na libovolný soubor otevřený v editoru bez ohledu na pořadí, ve kterém byl naposledy použit. Tyto funkce mohou zvýšit vaši produktivitu při práci v integrovaném vývojovém prostředí.

> [!NOTE]
> Možnosti dostupné v dialogových oknech a názvy a umístění příkazů nabídky, které vidíte, se mohou lišit od toho, co je popsáno v tomto článku v závislosti na aktivních nastaveních nebo edici. Tento článek se vytvořil s **obecným** nastavením. Chcete-li změnit nastavení, například **Obecné** nebo **Visual C++** nastavení, zvolte **nástroje**  >  **Nastavení importu a exportu** a pak zvolte možnost **resetovat všechna nastavení**.

## <a name="keyboard-shortcuts"></a>Klávesové zkratky

Téměř všechny příkazy nabídky v aplikaci Visual Studio mají klávesovou zkratku. Můžete také vytvořit vlastní zástupce. Další informace najdete v tématu [identifikace a přizpůsobení klávesových zkratek](../ide/identifying-and-customizing-keyboard-shortcuts-in-visual-studio.md).

## <a name="navigate-among-files-in-the-editor"></a>Navigace mezi soubory v editoru

K přesunu souborů otevřených v editoru můžete použít několik metod. Můžete přecházet mezi soubory na základě pořadí, ve kterém k nim přistupujete, pomocí Navigátoru IDE můžete rychle najít libovolný otevřený soubor nebo připnout oblíbené soubory na kartu a zajistit, aby byly vždy viditelné.

Přejděte zpět a procházejte vpřed v editoru podle pořadí, ve kterém byly použity, podobně jako u back-mailů a vpřed pro zobrazení historie v aplikaci Microsoft Internet Explorer.

### <a name="to-move-through-open-files-in-order-of-use"></a>Procházení otevřených souborů v pořadí podle použití

- Chcete-li aktivovat otevřené dokumenty v pořadí, v jakém byly naposledy změněny, stiskněte klávesu **CTRL** + **-** (pomlčka).

- Chcete-li aktivovat otevřené dokumenty v obráceném pořadí, stiskněte klávesy **CTRL** + **SHIFT** + **-** (spojovník).

    > [!NOTE]
    > **Přejít zpět** a **Přejít vpřed** také najdete v nabídce **zobrazení** .

Můžete také přepnout do konkrétního souboru otevřeného v editoru, bez ohledu na to, kdy jste ho naposledy otevřeli, pomocí seznamu aktivní soubory v editoru **rozhraní IDE**, seznam **aktivních souborů** nebo okna **Windows** .

**Rozhraní IDE navigátor** funguje podobně jako přepínač aplikace systému Windows. Není k dispozici z nabídek a lze k nim získat přístup pouze pomocí klávesových zkratek. K zacyklování **souborů v závislosti** na pořadí, ve kterém chcete cyklicky procházet, můžete použít kterýkoli ze dvou příkazů.

![Visual Studio – navigátor IDE](../ide/media/vs2015_ide_navigator.png)

`Window.PreviousDocumentWindowNav` umožňuje přesunout se k souboru, který se naposledy otevřel, a `Window.NextDocumentWindowNav` umožňuje přesun v obráceném pořadí. **Nastavení obecného vývoje** přiřadí klávesu **SHIFT** + **ALT** + **F7** k `Window.PreviousDocumentWindowNav` a **ALT** + **F7** do `Window.NextDocumentWindowNav` .

> [!NOTE]
> Pokud kombinace nastavení, kterou používáte, ještě nemá přiřazenou kombinaci klávesových zkratek, můžete přiřadit vlastní příkaz pomocí stránky **klávesnice** dialogového okna **Možnosti** . Další informace najdete v tématu [identifikace a přizpůsobení klávesových zkratek](../ide/identifying-and-customizing-keyboard-shortcuts-in-visual-studio.md).

### <a name="to-switch-to-specific-files-in-the-editor"></a>Přepnutí na konkrétní soubory v editoru

- Stisknutím **kombinace kláves CTRL** + **Tab** zobrazte **navigátor IDE**. Podržte stisknutou klávesu **CTRL** a stiskněte klávesu **tabulátor** opakovaně, dokud nevyberete soubor, na který chcete přepnout.

    > [!TIP]
    > Chcete-li změnit pořadí, ve kterém procházíte seznamem **aktivních souborů** , podržte klávesu **CTRL** + **+ SHIFT** a stiskněte klávesu **TAB**.

    \- ani

- V pravém horním rohu editoru klikněte na tlačítko **aktivní soubory** a potom vyberte soubor ze seznamu, na který chcete přejít.

    \- ani

- Na panelu nabídek vyberte **okna okna**  >  **Windows**.

- V seznamu vyberte soubor, který chcete zobrazit, a pak zvolte **aktivovat**.

## <a name="navigate-among-tool-windows-in-the-ide"></a>Navigace mezi okny nástrojů v integrovaném vývojovém prostředí

**Rozhraní IDE Navigator** také umožňuje cyklicky procházet okna nástrojů, která jste otevřeli v integrovaném vývojovém prostředí (IDE). Můžete použít kterýkoli ze dvou příkazů pro přístup k **navigátoru IDE** pro přepínání mezi okny nástrojů v závislosti na pořadí, ve kterém chcete cyklicky přepínat. `Window.PreviousToolWindowNav` umožňuje přesunout se k souboru, který se naposledy otevřel, a `Window.NextToolWindowNav` umožňuje přesun v obráceném pořadí. **Nastavení obecného vývoje** přiřadí klávesu **SHIFT** + **ALT** + **F7** k `Window.PreviousDocumentWindowNav` a **ALT** + **F7** do `Window.NextDocumentWindowNav` .

> [!NOTE]
> Pokud kombinace nastavení, kterou používáte, ještě nemá přiřazenou kombinaci klávesových zkratek, můžete přiřadit vlastní příkaz pomocí stránky **klávesnice** dialogového okna **Možnosti** . Další informace najdete v tématu [identifikace a přizpůsobení klávesových zkratek](../ide/identifying-and-customizing-keyboard-shortcuts-in-visual-studio.md).

### <a name="to-switch-to-a-specific-tool-window-in-the-ide"></a>Přepnutí na určité okno nástrojů v integrovaném vývojovém prostředí

- Stisknutím klávesy **ALT** + **F7** zobrazte **navigátor IDE**. Podržte stisknutou klávesu **ALT** a stiskněte klávesu **F7** opakovaně, dokud nevyberete okno, na které chcete přepnout.

    > [!TIP]
    > Chcete-li změnit pořadí, ve kterém procházíte seznamem **oken aktivních nástrojů** , podržte klávesy **SHIFT** + **ALT +** F7 a stiskněte klávesu **F7**.

## <a name="see-also"></a>Viz také

- [Přizpůsobení rozložení oken](../ide/customizing-window-layouts-in-visual-studio.md)
- [Výchozí klávesové zkratky](../ide/default-keyboard-shortcuts-in-visual-studio.md)
