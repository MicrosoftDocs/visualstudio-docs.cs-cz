---
title: 'Postup: Nastavení možností usnadnění ide'
description: Naučte se, jak nastavit možnosti usnadnění v sadě Visual Studio, která usnadní jeho integrované vývojové prostředí (IDE) pro každého, včetně pro lidi, kteří mají slabozraké číst a pro lidi, kteří mají omezenou pohyblivost psát.
ms.date: 08/23/2019
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- accessibility [Visual Studio]
ms.assetid: ddc96c4c-0600-46c1-8267-7dce4c44ad24
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 63bba4e8defcd727f05dbc209aa2f48f7d5f2c92
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "70107770"
---
# <a name="how-to-set-ide-accessibility-options"></a>Postup: Nastavení možností usnadnění ide

Visual Studio obsahuje funkce, které usnadňují čtení lidem se zneviděníním a lidem s omezenou pohyblivostí k psaní. Můžete například změnit velikost a barvu textu v editorech, změnit velikost textu a tlačítek na panelech nástrojů a změnit nastavení, která vám pomohou dokončit funkci nebo příkaz.

Kromě toho Visual Studio podporuje rozložení klávesnice Dvorak, které usnadňují nejčastěji zadaným znakům. Můžete také přizpůsobit výchozí klávesové zkratky, které jsou k dispozici v sadě Visual Studio. Další informace naleznete v [tématu Identifikace a přizpůsobení klávesových zkratek](../../ide/identifying-and-customizing-keyboard-shortcuts-in-visual-studio.md).

> [!NOTE]
> Zobrazená dialogová okna a příkazy nabídek se mohou lišit od těch, které jsou zde popsány, což se může lišit v závislosti na aktivním nastavení nebo edici. Chcete-li změnit nastavení, zvolte **Nastavení importu a exportu** v nabídce **Nástroje.** Další informace naleznete v tématu [Reset settings](../environment-settings.md#reset-settings).

::: moniker range="vs-2017"

> [!TIP]
> Další informace o nedávných aktualizacích usnadnění najdete v tématu Vylepšení usnadnění v blogu [Visual Studia 2017 verze 15.3.](https://devblogs.microsoft.com/visualstudio/accessibility-improvements-in-visual-studio-2017-version-15-3/)

::: moniker-end

## <a name="editors-dialogs-and-tool-windows"></a>Editory, dialogová okna a okna nástrojů

Ve výchozím nastavení používají dialogová okna a okna nástrojů v sadě Visual Studio stejnou velikost písma a barvy jako operační systém. Nastavení barev pro rámeček ide, dialogová okna, panely nástrojů a okna nástrojů jsou založeny na barevném schématu: světlénebo tmavé. Aktuální barevný motiv můžete změnit v [dialogovém okně Volby: Prostředí > Obecné](../../ide/reference/general-environment-options-dialog-box.md).

Můžete také zobrazit automaticky otevíraná okna v zobrazení Kód editoru. Tato okna vás mohou vyzvat k zadání s dostupnými členy aktuálního objektu a parametry k dokončení funkce nebo příkazu. Tato okna mohou být užitečná, pokud máte potíže s psaním. Však narušují fokus v editoru kódu, což může být problematické pro některé uživatele.

Zde je návod, jak vypnout automaticky otevíraná okna:

1. Z nabídky **Nástroje** zvolte **Možnosti**.

1. Zvolte **Textový editor** > **všechny obecné jazyky** > **.**

1. Zrušte zaškrtnutí políček **Automaticky seznam členů** a informací o **parametrech.**

Můžete změnit uspořádání oken v integrovaném vývojovém prostředí (IDE) tak, aby co nejlépe vyhovovaly způsobu práce. Každé okno nástroje můžete ukotvit, uvolnit, skrýt nebo automaticky skrýt. Další informace o změně rozložení oken naleznete v [tématu Přizpůsobení rozložení oken](../../ide/customizing-window-layouts-in-visual-studio.md).

### <a name="change-the-size-of-text"></a>Změna velikosti textu

Nastavení textových oken nástrojů, například okna **Příkaz,** **Okno okamžité** a **Okno Výstup,** můžete změnit **pomocí** > nástrojů**Možnosti** > **prostředí** > **Písma a barvy**.

Když v rozevíracím seznamu **Zobrazit nastavení pro** rozevírací seznam vyberete možnost **[Všechny textové nástroje Windows],** bude výchozí nastavení v rozevíracích seznamech **Popředí** položky a na **pozadí položky** uvedeno jako **Výchozí.** Chcete-li tato nastavení změnit, zvolte tlačítko **Vlastní.**

Můžete také změnit nastavení zobrazení textu v editoru. Jak na to:

1. Z nabídky **Nástroje** zvolte **Možnosti**.

1. Zvolte**Písma a barvy** **prostředí** > .

1. V rozevírací nabídce **Zobrazit vyberte volbu.**

    Chcete-li změnit velikost písma pro text v editoru, zvolte **Textový editor**.

    Chcete-li změnit velikost písma pro text v textových oknech nástrojů, zvolte **možnost [Všechny textové nástroje Windows]**.

    Chcete-li změnit velikost písma pro text popisu v editoru, zvolte **Editor Tooltip**.

    Chcete-li změnit velikost písma pro text v automaticky otevíraných líacích dokončování příkazů, zvolte **Dokončení výkazu**.

1. V **možnosti Zobrazit položky**vyberte **položku Prostý text**.

1. V **části Písmo**vyberte nový typ písma.

1. V **části Velikost**vyberte novou velikost písma.

    > [!TIP]
    > Chcete-li obnovit velikost textu pro textová okna a editory nástrojů, zvolte **Použít výchozí nastavení**.

7. Vyberte **OK**.

### <a name="change-the-colors-that-are-used-in-the-ide"></a>Změna barev, které se používají v ide

Můžete změnit výchozí barvy pro text, indikátory okrajů, prázdné místo a prvky kódu v editoru. Jak na to:

1. Z nabídky **Nástroje** zvolte **Možnosti**.

1. Ve složce **Prostředí** zvolte **Písma a barvy**.

1. V **části Zobrazit nastavení pro**zvolte Textový **editor**.

1. V **rozesíláte položku**, jejíž zobrazení je třeba změnit, například **Prostý text**, Okraj **indikátoru**, **Viditelné prázdné místo**, Název **atributu HTML**nebo Atribut **XML**.

1. Vyberte nastavení zobrazení z následujících možností: **Popředí položky**, **Pozadí položky**a **Tučné**.

1. Vyberte **OK**.

> [!TIP]
> Chcete-li použít barvy s vysokým kontrastem pro všechna okna aplikací v operačním systému, stiskněte **klávesu Left Alt**+**Left Shift**+**PrtScn**. Pokud je visual studio otevřené, zavřete a znovu otevřete, abyste plně implementovali barvy s vysokým kontrastem.

## <a name="toolbars"></a>Panely nástrojů

Chcete-li zlepšit použitelnost a usnadnění přístupu panelu nástrojů, můžete přidat text do tlačítek panelu nástrojů.

### <a name="to-assign-text-to-toolbar-buttons"></a>Přiřazení textu tlačítkům panelu nástrojů

1. V nabídce **Nástroje** zvolte **Přizpůsobit**.

1. V dialogovém okně **Přizpůsobit** vyberte kartu **Příkazy.**

1. Vyberte **Panel nástrojů**a pak zvolte název panelu nástrojů, který obsahuje tlačítko, pro které chcete zobrazit text.

1. V seznamu vyberte příkaz, který chcete změnit.

1. Zvolte **Změnit výběr**.

1. Zvolte **Obraz a Text**.

### <a name="to-modify-the-displayed-text-in-a-button"></a>Úprava zobrazeného textu v tlačítku

1. Znovu vyberte **změnit výběr**.

1. Přiléhající k In **Name**, vložte zadejte nový titulek pro vybrané tlačítko.

## <a name="see-also"></a>Viz také

* [Funkce usnadnění v sadě Visual Studio](../../ide/reference/accessibility-features-of-visual-studio.md)
* [Usnadnění pro Visual Studio pro Mac](/visualstudio/mac/accessibility/)
* [Prostředky pro navrhování přístupných aplikací](../../ide/reference/resources-for-designing-accessible-applications.md)
