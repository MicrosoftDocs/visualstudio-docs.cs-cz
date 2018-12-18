---
title: Identifikování a přizpůsobení klávesových zkratek
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: conceptual
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
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 61ea8d6ee9243f79fe250872820643904bb2367a
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/07/2018
ms.locfileid: "53062967"
---
# <a name="identify-and-customize-keyboard-shortcuts-in-visual-studio"></a>Identifikování a přizpůsobení klávesových zkratek v sadě Visual Studio

Můžete určit klávesové zkratky pro příkazy sady Visual Studio, tyto zkratky přizpůsobit a exportovat je, aby je mohli používat ostatní uživatelé. Mnoho zkratek vždy vyvolá stejné příkazy, ale chování zkratky se může lišit v závislosti na následujících podmínkách:

- Výchozí nastavení prostředí, které jste vybrali při prvním spuštění sady Visual Studio (například obecný vývoj nebo Visual C#).

- Zda jste přizpůsobili chování zkratky.

- Kontext použitý při výběru zástupce. Například **F2** zkratka vyvolá `Edit.EditCell` příkazu, pokud používáte **návrháře nastavení** a `File.Rename` příkazu, pokud používáte **Průzkumníktýmovýchprojektů**.

Bez ohledu na nastavení, přizpůsobení a kontext můžete kdykoli najít nebo změnit klávesové zkratky v **možnosti** dialogové okno. Můžete také vyhledat výchozí klávesové zkratky pro několik desítek příkazů [výchozí klávesové zkratky pro často používané příkazy](../ide/default-keyboard-shortcuts-for-frequently-used-commands-in-visual-studio.md), a najdete úplný seznam všech výchozích klávesových zkratek (podle **obecné Nastavení pro vývoj**) v [výchozí klávesové zkratky](../ide/default-keyboard-shortcuts-in-visual-studio.md).

Pokud je klávesová zkratka přiřazena k příkazu v globálním kontextu a bez jiných kontextů, tato zkratka vždy vyvolá daný příkaz. Klávesová zkratka může být však přiřazena k jednomu příkazu v globálním kontextu a k jinému příkazu ve specifickém kontextu. Používáte-li takovou klávesovou zkratku v konkrétním kontextu, tato zkratka vyvolá příkaz pro konkrétní kontext, nikoli pro globální kontext.

> [!NOTE]
> Vaše nastavení a edice sady Visual Studio může změnit názvy a umístění příkazů nabídky a možnosti, které se zobrazí v dialogových oknech. Toto téma vychází **obecným vývojovým nastavením**.

## <a name="identify-a-keyboard-shortcut"></a>Určení klávesové zkratky

1. V panelu nabídky zvolte **nástroje** > **možnosti**.

2. Rozbalte **prostředí**a klikněte na tlačítko **klávesnice**.

   ![Zobrazí klávesové zkratky v dialogovém okně Možnosti](../ide/media/optionskeyboard.png)

3. V **zobrazit příkazy obsahující** zadejte část nebo celý název příkazu bez mezer.

   Můžete například najít příkazy pro `solutionexplorer`.

4. V seznamu zvolte správný příkaz.

    Například můžete použít `View.SolutionExplorer`.

5. Pokud příkaz nemá klávesovou zkratku, zobrazí se v **zkratky pro vybraný příkaz** seznamu.

   ![Zobrazit klávesovou zkratku pro zadaný příkaz](../ide/media/viewshortcut.png)

## <a name="customize-a-keyboard-shortcut"></a>Přizpůsobení klávesové zkratky

1. V panelu nabídky zvolte **nástroje** > **možnosti**.

2. Rozbalte **prostředí** složky a klikněte na tlačítko **klávesnice**.

3. Volitelné: Filtrovat seznam příkazů, které tak, že zadáte část nebo celý název příkazu bez mezer, **zobrazit příkazy obsahující** pole.

4. V seznamu vyberte příkaz, ke kterému chcete přiřadit klávesovou zkratku.

    V **použití nového zástupce v:** seznamu, vyberte oblast funkce, ve které chcete použít klávesovou zkratku.

    Například můžete použít **globální** Pokud chcete, aby zkratka fungovala ve všech kontextech. Můžete použít jakoukoli zkratku, která není namapována (jako globální) v jiném editoru. V opačném případě editor zkratku přepíše.

    > [!NOTE]
    > Následující klávesy nelze přiřadit jako součást klávesové zkratky v **globální**: tisk navigátoru obrazovky/Sys Rq, posuňte Lock, Pause/Break, Tab, Caps Lock, Insert, Home, End, Page Up, Page Down, klávesu s logem Windows, klíč Application, všechny šipky klíče nebo Enter. Num Lock, Delete nebo Clear na numerické klávesnici; kombinace kláves Ctrl + Alt + Delete.

6. V **stiskněte klávesy zkratky** zadejte klávesovou zkratku, kterou chcete použít.

    > [!NOTE]
    > Můžete vytvořit zástupce, který kombinuje písmeno s **Alt** klíč, **Ctrl** klíč, nebo obojí. Můžete také vytvořit zástupce, který kombinuje **Shift** klíč a písmeno s **Alt** klíč, **Ctrl** klíč, nebo obojí.

     Pokud je klávesová zkratka již přiřazena k jinému příkazu, zobrazí se v **zkratku aktuálně používá** pole. V takovém případě zvolte **Backspace** klávesy odstraňte tato zkratka, než se pokusíte nějaký jiný.

    ![Zadat jinou zkratku pro příkaz](../ide/media/reassignshortcut.png)

7. Zvolte **přiřadit** tlačítko.

    > [!NOTE]
    > Pokud chcete zadat jinou zkratku pro příkaz, zvolte **přiřadit** tlačítko a klikněte na tlačítko **zrušit** tlačítko, dialog se zavře, ale změna se nevrátí.

## <a name="share-custom-keyboard-shortcuts"></a>Sdílení vlastní klávesové zkratky

Vlastní klávesové zkratky je možné sdílet exportováním do souboru a předáním souboru ostatním, aby data mohli importovat.

### <a name="to-export-only-keyboard-shortcuts"></a>Export pouze klávesových zkratek

1. V panelu nabídky zvolte **nástroje** > **nastavení importu a exportu**.

2. Zvolte **exportovat vybrané nastavení prostředí**a klikněte na tlačítko **Další** tlačítko.

3. V části **jaká nastavení chcete exportovat?**, zrušte zaškrtnutí políčka **všechna nastavení** zaškrtávací políčko, rozbalte **možnosti**a potom rozbalte **prostředí**.

4. Vyberte **klávesnice** zaškrtněte políčko a klikněte na tlačítko **Další** tlačítko.

    ![Exportovat jenom vlastní klávesové zkratky](../ide/media/exportshortcuts.png)

5. V **co chcete pojmenovat soubor nastavení?** a **Store Můj soubor nastavení v tomto adresáři** polí, buď ponechte výchozí hodnoty nebo zadejte jiné hodnoty a klikněte na tlačítko  **Dokončit** tlačítko.

    Ve výchozím nastavení, klávesové zkratky ukládány do souboru v *%USERPROFILE%\Documents\Visual Studio 2017\Settings* složky. Název souboru zobrazuje datum, kdy jste nastavení exportovali, a je rozšíření *.vssettings*.

### <a name="to-import-only-keyboard-shortcuts"></a>Import pouze klávesových zkratek

1. V panelu nabídky zvolte **nástroje** > **nastavení importu a exportu**.

2. Zvolte **importovat vybrané nastavení prostředí** přepínač a klikněte na tlačítko **Další** tlačítko.

3. Zvolte **Ne, importovat nové nastavení a přepsat současné nastavení** přepínač a klikněte na tlačítko **Další** tlačítko.

4. V části **má nastavení**, zvolte soubor, který obsahuje klávesové zkratky, které chcete importovat, nebo zvolte **Procházet** vyhledejte správný soubor.

5. Zvolte **Další** tlačítko.

6.  V části **nastavení, které chcete importovat?**, zrušte zaškrtnutí políčka **všechna nastavení** zaškrtávací políčko, rozbalte **možnosti**a potom rozbalte **prostředí**.

7. Vyberte **klávesnice** zaškrtněte políčko a klikněte na tlačítko **Dokončit** tlačítko.

    ![Importovat pouze vlastní klávesové zkratky](../ide/media/importshortcuts.png)

## <a name="see-also"></a>Viz také:

- [Funkce pro usnadnění přístupu sady Visual Studio](../ide/reference/accessibility-features-of-visual-studio.md)