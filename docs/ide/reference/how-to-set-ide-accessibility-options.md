---
title: 'Postupy: nastavení možností dostupnosti IDE'
description: Naučte se, jak nastavit možnosti usnadnění přístupu v sadě Visual Studio, aby bylo možné využít integrované vývojové prostředí (IDE) pro všechny uživatele, a to včetně pro lidi, kteří mají nízkou vizi ke čtení a pro lidi, kteří mají omezená pohyblivost k zápisu.
ms.date: 08/23/2019
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
ms.topic: how-to
helpviewer_keywords:
- accessibility [Visual Studio]
ms.assetid: ddc96c4c-0600-46c1-8267-7dce4c44ad24
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 4d7cc99747571feb5b443f10355d867da7c22f44
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99952912"
---
# <a name="how-to-set-ide-accessibility-options"></a>Postupy: nastavení možností dostupnosti IDE

Visual Studio obsahuje funkce, které usnadňují uživatelům, kteří mají ke čtení nízkou pohyblivost, a pro lidi, kteří mají omezené možnosti psaní. Například můžete změnit velikost a barvu textu v editorech, změnit velikost textu a tlačítek na panelech nástrojů a změnit nastavení tak, aby vám pomohlo dokončit funkci nebo příkaz.

Kromě toho Visual Studio podporuje rozložení klávesnice Dvorak, které usnadňují přístup k nejčastěji zadaným znakům. Můžete také přizpůsobit výchozí klávesové zkratky, které jsou k dispozici v aplikaci Visual Studio. Další informace najdete v tématu [identifikace a přizpůsobení klávesových zkratek](../../ide/identifying-and-customizing-keyboard-shortcuts-in-visual-studio.md).

> [!NOTE]
> Dialogová okna a příkazy nabídek, které vidíte, se mohou lišit od těch, které jsou zde popsané, které se mohou lišit v závislosti na aktivních nastaveních nebo edici. Chcete-li změnit nastavení, v nabídce **nástroje** klikněte na položku **Nastavení importu a exportu** . Další informace najdete v tématu [resetování nastavení](../environment-settings.md#reset-settings).

::: moniker range="vs-2017"

> [!TIP]
> Další informace o nejnovějších aktualizacích usnadnění najdete v blogovém příspěvku o [vylepšeních dostupnosti v aplikaci Visual Studio 2017 verze 15,3](https://devblogs.microsoft.com/visualstudio/accessibility-improvements-in-visual-studio-2017-version-15-3/) .

::: moniker-end

## <a name="editors-dialogs-and-tool-windows"></a>Editory, dialogová okna a okna nástrojů

Ve výchozím nastavení používají dialogová okna a okna nástrojů v aplikaci Visual Studio stejnou velikost písma a barvy jako operační systém. Nastavení barev pro rámeček rozhraní IDE, dialogová okna, panely nástrojů a okna nástrojů jsou založena na barevném schématu: světlá nebo tmavá. Aktuální barevný motiv můžete změnit v [dialogovém okně Možnosti: prostředí > obecné](../../ide/reference/general-environment-options-dialog-box.md).

Můžete také zobrazit automaticky otevíraná okna v zobrazení kódu editoru. Tato okna vás mohou vyzvat s dostupnými členy na aktuálním objektu a parametry k dokončení funkce nebo příkazu. Tato okna můžou být užitečná, pokud máte potíže při psaní. Nicméně narušují fokus v editoru kódu, což může být pro některé uživatele problematické.

Tady je postup, jak vypnout automaticky otevíraná okna:

1. V nabídce **nástroje** klikněte na příkaz **Možnosti**.

1. Vyberte **Text Editor**  >    >  **Obecné** jazyky.

1. Zrušte zaškrtnutí políček **Členové automatického seznamu** a **informace o parametrech** .

Můžete změnit uspořádání oken v integrovaném vývojovém prostředí (IDE) tak, aby nejlépe vyhovovala způsobu, jakým pracujete. Jednotlivá okna nástroje můžete ukotvit, floatovat, skrývat nebo automaticky skrývat. Další informace o tom, jak změnit rozložení oken, najdete v tématu [přizpůsobení rozložení oken](../../ide/customizing-window-layouts-in-visual-studio.md).

### <a name="change-the-size-of-text"></a>Změna velikosti textu

Můžete změnit nastavení pro textová okna nástrojů, jako je okno **příkazového** řádku, okno **okamžité** okna a **výstup** pomocí **nástrojů**  >  **Možnosti**  >  **prostředí**  >  **písma a barvy**.

Když vyberete **[všechna okna textových nástrojů]** v rozevíracím **seznamu zobrazit nastavení pro** , výchozí nastavení je uvedeno jako **výchozí** v rozevíracích seznamech **položky** a **pozadí položky** . Chcete-li změnit tato nastavení, klikněte na tlačítko **vlastní** .

Můžete také změnit nastavení způsobu zobrazení textu v editoru. Jak na to:

1. V nabídce **nástroje** klikněte na příkaz **Možnosti**.

1. Vyberte možnost  >  **písma a barvy** prostředí.

1. Vyberte možnost v rozevírací nabídce **Zobrazit nastavení pro** .

    Chcete-li změnit velikost písma textu v editoru, vyberte možnost **textový editor**.

    Chcete-li změnit velikost písma textu v textových oknech nástrojů, vyberte možnost **[všechna okna textových nástrojů]**.

    Chcete-li změnit velikost písma textu popisku v editoru, klikněte na tlačítko **Editor popis**.

    Chcete-li změnit velikost písma textu v místních oknech dokončování příkazů, vyberte možnost **dokončování příkazů**.

1. V **zobrazení položky** vyberte **prostý text**.

1. V **písma** vyberte nový typ písma.

1. V rámečku **Velikost** vyberte novou velikost písma.

    > [!TIP]
    > Chcete-li obnovit velikost textu textových oken a editorů založených na textu, vyberte možnost **použít výchozí**.

7. Vyberte **OK**.

### <a name="change-the-colors-that-are-used-in-the-ide"></a>Změna barev použitých v integrovaném vývojovém prostředí

Můžete zvolit, že chcete změnit výchozí barvy pro text, indikátory okrajů, prázdné znaky a prvky kódu v editoru. Jak na to:

1. V nabídce **nástroje** klikněte na příkaz **Možnosti**.

1. Ve složce **prostředí** vyberte možnost **písma a barvy**.

1. V **zobrazení zobrazit nastavení pro** vyberte **textový editor**.

1. V položce **Zobrazit položky** vyberte položku, jejíž zobrazení potřebujete změnit, například **prostý text**, **okraj indikátoru**, **viditelné prázdné znaky**, **název atributu HTML** nebo **atribut XML**.

1. Vyberte nastavení zobrazení z následujících možností: **popředí položky**, **pozadí položky** a **tučné**.

1. Vyberte **OK**.

> [!TIP]
> Chcete-li pro všechna okna aplikací v operačním systému použít barvy s vysokým kontrastem, stiskněte **levý ALT** levý klávesu + **SHIFT** + **Print Screen**. Pokud je Visual Studio otevřené, zavřete ho a znovu ho otevřete, abyste mohli plně implementovat barvy s vysokým kontrastem.

## <a name="toolbars"></a>Panely nástrojů

Pro zlepšení použitelnosti panelu nástrojů a usnadnění přístupu můžete přidat text na tlačítka panelu nástrojů.

### <a name="to-assign-text-to-toolbar-buttons"></a>Přiřazení textu k tlačítkům panelu nástrojů

1. V nabídce **nástroje** vyberte možnost **přizpůsobit**.

1. V dialogovém okně **přizpůsobit** vyberte kartu **příkazy** .

1. Vyberte **panel nástrojů** a potom zvolte název panelu nástrojů, který obsahuje tlačítko, pro které chcete zobrazit text.

1. V seznamu vyberte příkaz, který máte v úmyslu změnit.

1. Vyberte možnost **změnit výběr**.

1. Vyberte **obrázek a text**.

### <a name="to-modify-the-displayed-text-in-a-button"></a>Úprava zobrazeného textu v tlačítku

1. Znovu vyberte **změnit výběr**.

1. Vedle pole **název** zadejte pro vybrané tlačítko Nový titulek.

## <a name="see-also"></a>Viz také

* [Funkce usnadnění v aplikaci Visual Studio](../../ide/reference/accessibility-features-of-visual-studio.md)
* [Přístupnost pro Visual Studio pro Mac](/visualstudio/mac/accessibility/)
* [Prostředky pro návrh přístupných aplikací](../../ide/reference/resources-for-designing-accessible-applications.md)
