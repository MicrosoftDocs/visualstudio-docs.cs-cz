---
title: Identifikování a přizpůsobení klávesových zkratek
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- VS.ToolsOptionsPages.Environment.Keyboard
helpviewer_keywords:
- keyboard shortcuts [Visual Studio], customizing
- importing shortcut keys [Visual Studio]
- shortcut key combinations [Visual Studio]
- commands [Visual Studio], shortcut keys
- custom shortcut keys [Visual Studio]
- customizing keyboard shortcuts [Visual Studio]
- exporting shortcut keys [Visual Studio]
ms.assetid: d2774be2-60a4-4d6f-95f1-79d0d9e55b56
caps.latest.revision: 30
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: ac425903ade4dbf90f094376927d46629b1c675d
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/07/2018
ms.locfileid: "53053996"
---
# <a name="identifying-and-customizing-keyboard-shortcuts-in-visual-studio"></a>Identifikování a přizpůsobení klávesových zkratek v sadě Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Můžete určit klávesové zkratky pro příkazy sady Visual Studio, tyto zkratky přizpůsobit a exportovat je, aby je mohli používat ostatní uživatelé. Mnoho zkratek vždy vyvolá stejné příkazy, ale chování zkratky se může lišit v závislosti na následujících podmínkách:

- Výchozí nastavení prostředí, které jste vybrali při prvním spuštění sady Visual Studio (například obecný vývoj nebo Visual C#).

- Zda jste přizpůsobili chování zkratky.

- Kontext použitý při výběru zástupce. Například zkratka F2 vyvolá příkaz Edit.EditCell, pokud používáte Návrháře nastavení, a příkaz File.Rename, pokud používáte Průzkumník týmových projektů.

  Bez ohledu na nastavení, přizpůsobení a kontext můžete kdykoli najít nebo změnit klávesové zkratky v **možnosti** dialogové okno. Můžete také vyhledat výchozí klávesové zkratky pro několik desítek příkazů [výchozí klávesové zkratky for Frequently Used Commands](../ide/default-keyboard-shortcuts-for-frequently-used-commands-in-visual-studio.md), a najdete úplný seznam všech výchozích klávesových zkratek (podle obecný vývoj Nastavení) v [výchozí klávesové zkratky](../ide/default-keyboard-shortcuts-in-visual-studio.md).

  **V tomto tématu**

- [Určení klávesové zkratky](../ide/identifying-and-customizing-keyboard-shortcuts-in-visual-studio.md#bkmk_identify)

- [Přizpůsobení klávesové zkratky](../ide/identifying-and-customizing-keyboard-shortcuts-in-visual-studio.md#bkmk_assign)

- [Sdílení vlastní klávesové zkratky](../ide/identifying-and-customizing-keyboard-shortcuts-in-visual-studio.md#bkmk_transfer)

  Pokud je klávesová zkratka přiřazena k příkazu v globálním kontextu a bez jiných kontextů, tato zkratka vždy vyvolá daný příkaz. Klávesová zkratka může být však přiřazena k jednomu příkazu v globálním kontextu a k jinému příkazu ve specifickém kontextu. Používáte-li takovou klávesovou zkratku v konkrétním kontextu, tato zkratka vyvolá příkaz pro konkrétní kontext, nikoli pro globální kontext.

> [!NOTE]
>  Vaše nastavení a edice sady Visual Studio může změnit názvy a umístění příkazů nabídky a možnosti, které se zobrazí v dialogových oknech. Toto téma vychází **obecným vývojovým nastavením**.

##  <a name="bkmk_identify"></a> Určení klávesové zkratky

1.  V panelu nabídky zvolte **nástroje**, **možnosti**.

2.  Rozbalte **prostředí**a klikněte na tlačítko **klávesnice**.

     ![Zobrazí klávesové zkratky v dialogovém okně Možnosti](../ide/media/optionskeyboard.png "OptionsKeyboard")

3.  V **zobrazit příkazy obsahující** zadejte část nebo celý název příkazu bez mezer.

     Můžete například najít příkazy pro **solutionexplorer**.

4.  V seznamu zvolte správný příkaz.

     Například můžete použít **View.SolutionExplorer**.

5.  Pokud příkaz nemá klávesovou zkratku, zobrazí se v **zkratky pro vybraný příkaz** seznamu.

     ![Zobrazit klávesovou zkratku pro zadaný příkaz](../ide/media/viewshortcut.png "ViewShortcut")

##  <a name="bkmk_assign"></a> Přizpůsobení klávesové zkratky

1.  V panelu nabídky zvolte **nástroje**, **možnosti**.

2.  Rozbalte **prostředí** složky a klikněte na tlačítko **klávesnice**.

     ![Zobrazí klávesové zkratky v dialogovém okně Možnosti](../ide/media/optionskeyboard.png "OptionsKeyboard")

3.  V **zobrazit příkazy obsahující** zadejte část nebo celý název příkazu bez mezer.

     Můžete například najít příkazy pro **solutionexplorer**.

4.  V seznamu vyberte příkaz, ke kterému chcete přiřadit klávesovou zkratku.

5.  V **použití nového zástupce v:** seznamu, vyberte oblast funkce, ve které chcete použít klávesovou zkratku.

     Například můžete použít **globální** Pokud chcete, aby zkratka fungovala ve všech kontextech. Můžete použít jakoukoli zkratku, která není namapována (jako globální) v jiném editoru. V opačném případě editor zkratku přepíše.

    > [!NOTE]
    >  Následující klávesy nelze přiřadit jako součást klávesové zkratky v **globální**: tisk navigátoru obrazovky/Sys Rq, posuňte Lock, Pause/Break, Tab, Caps Lock, Insert, Home, End, Page Up, Page Down, klávesu s logem Windows, klíč Application, všechny šipky klíče nebo Enter. Num Lock, Delete nebo Clear na numerické klávesnici; nebo Ctrl + Alt + Delete.

6.  V **stiskněte klávesy zkratky** zadejte klávesovou zkratku, kterou chcete použít.

    > [!NOTE]
    >  Můžete vytvořit zástupce, který kombinuje písmeno s klávesou Alt, klávesou Ctrl nebo oběma klávesami. Můžete také vytvořit zástupce, který kombinuje klávesu Shift a písmeno s klávesou Alt, klávesou Ctrl nebo oběma klávesami.

     Pokud je klávesová zkratka již přiřazena k jinému příkazu, zobrazí se v **zkratku aktuálně používá** pole. V takovém případě stisknutím klávesy Backspace tuto klávesovou zkratku smažte a zkuste jinou.

     ![Zadat jinou zkratku pro příkaz](../ide/media/reassignshortcut.png "ReassignShortcut")

7.  Zvolte **přiřadit** tlačítko.

    > [!NOTE]
    >  Pokud chcete zadat jinou zkratku pro příkaz, zvolte **přiřadit** tlačítko a klikněte na tlačítko **zrušit** tlačítko, dialog se zavře, ale změna se nevrátí.

##  <a name="bkmk_transfer"></a> Sdílení vlastní klávesové zkratky
 Vlastní klávesové zkratky je možné sdílet exportováním do souboru a předáním souboru ostatním, aby data mohli importovat.

#### <a name="to-export-only-keyboard-shortcuts"></a>Export pouze klávesových zkratek

1.  V panelu nabídky zvolte **nástroje**, **nastavení importu a exportu**.

2.  Zvolte **exportovat vybrané nastavení prostředí**a klikněte na tlačítko **Další** tlačítko.

3.  V části **jaká nastavení chcete exportovat?**, zrušte zaškrtnutí políčka **všechna nastavení** zaškrtávací políčko, rozbalte **možnosti**a potom rozbalte **prostředí**.

4.  Vyberte **klávesnice** zaškrtněte políčko a klikněte na tlačítko **Další** tlačítko.

     ![Export pouze klávesových zkratek přizpůsobit](../ide/media/exportshortcuts.png "ExportShortcuts")

5.  V **co chcete pojmenovat soubor nastavení?** a **Store Můj soubor nastavení v tomto adresáři** polí, buď ponechte výchozí hodnoty nebo zadejte jiné hodnoty a klikněte na tlačítko  **Dokončit** tlačítko.

     Ve výchozím nastavení jsou klávesové zkratky ukládány do souboru ve složce USERPROFILE%\Documents\Visual Studio 2013\Settings. Název souboru zobrazuje datum, kdy jste nastavení exportovali, a přípona je .vssettings.

#### <a name="to-import-only-keyboard-shortcuts"></a>Import pouze klávesových zkratek

1.  V panelu nabídky zvolte **nástroje**, **nastavení importu a exportu**.

2.  Zvolte **importovat vybrané nastavení prostředí** přepínač a klikněte na tlačítko **Další** tlačítko.

3.  Zvolte **Ne, importovat nové nastavení a přepsat současné nastavení** přepínač a klikněte na tlačítko **Další** tlačítko.

4.  V části **má nastavení**, zvolte soubor, který obsahuje klávesové zkratky, které chcete importovat, nebo zvolte **Procházet** vyhledejte správný soubor.

5.  Zvolte **Další** tlačítko.

6.  V části **nastavení, které chcete importovat?**, zrušte zaškrtnutí políčka **všechna nastavení** zaškrtávací políčko, rozbalte **možnosti**a potom rozbalte **prostředí**.

7.  Vyberte **klávesnice** zaškrtněte políčko a klikněte na tlačítko **Dokončit** tlačítko.

     ![Import pouze klávesových zkratek přizpůsobit](../ide/media/importshortcuts.png "ImportShortcuts")

## <a name="see-also"></a>Viz také
 [Funkce sady Visual Studio pro usnadnění přístupu](../ide/reference/accessibility-features-of-visual-studio.md)
