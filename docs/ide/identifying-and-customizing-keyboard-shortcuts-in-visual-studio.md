---
title: Identifikování a přizpůsobení klávesových zkratek
ms.date: 11/04/2016
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
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ce87385314ec84c7c0ed9d30c806a6287bb91d9e
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/01/2020
ms.locfileid: "75591330"
---
# <a name="identify-and-customize-keyboard-shortcuts-in-visual-studio"></a>Identifikování a přizpůsobení klávesových zkratek v sadě Visual Studio

Můžete určit klávesové zkratky pro příkazy sady Visual Studio, tyto zkratky přizpůsobit a exportovat je, aby je mohli používat ostatní uživatelé. Mnoho zkratek vždy vyvolá stejné příkazy, ale chování zkratky se může lišit v závislosti na následujících podmínkách:

- Které výchozí nastavení prostředí si zvolíte při prvním otevření sady Visual Studio&mdash;například obecný vývoj nebo vizuál C#. (Informace o změně nebo resetování nastavení naleznete v tématu [nastavení prostředí](environment-settings.md).)

- Zda jste přizpůsobili chování zkratky.

- Kontext použitý při výběru zástupce. Například zkratka **F2** vyvolá příkaz `Edit.EditCell`, pokud používáte **Návrháře nastavení** a vyvolá příkaz `File.Rename`, pokud používáte **Team Explorer**.

Bez ohledu na nastavení, přizpůsobení a kontext můžete kdykoli najít nebo změnit klávesové zkratky v **možnosti** dialogové okno. Můžete také vyhledat výchozí klávesové zkratky pro několik desítek příkazů v [oblíbených klávesových zkratkách](../ide/default-keyboard-shortcuts-for-frequently-used-commands-in-visual-studio.md). Úplný seznam všech výchozích klávesových zkratek (na základě **obecného nastavení vývoje** ) najdete v tématu [všechny klávesové zkratky](../ide/default-keyboard-shortcuts-in-visual-studio.md).

Pokud je zástupce přiřazen k příkazu v *globálním* kontextu a žádné jiné kontexty, tento zástupce Tento příkaz vždycky vyvolá. Klávesová zkratka může být však přiřazena k jednomu příkazu v globálním kontextu a k jinému příkazu ve specifickém kontextu. Používáte-li takovou klávesovou zkratku v konkrétním kontextu, tato zkratka vyvolá příkaz pro konkrétní kontext, nikoli pro globální kontext.

> [!NOTE]
> Vaše nastavení a edice sady Visual Studio může změnit názvy a umístění příkazů nabídky a možnosti, které se zobrazí v dialogových oknech. Tato stránka je založena na profilu **obecného** nastavení pro vývoj.

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

2. Rozbalte **prostředí**a klikněte na tlačítko **klávesnice**.

3. Volitelné: Filtrovat seznam příkazů, které tak, že zadáte část nebo celý název příkazu bez mezer, **zobrazit příkazy obsahující** pole.

4. V seznamu vyberte příkaz, ke kterému chcete přiřadit klávesovou zkratku.

   V **použití nového zástupce v:** seznamu, vyberte oblast funkce, ve které chcete použít klávesovou zkratku.

   Například můžete použít **globální** Pokud chcete, aby zkratka fungovala ve všech kontextech. Můžete použít jakoukoli zkratku, která není namapována (jako globální) v jiném editoru. V opačném případě editor zkratku přepíše.

   > [!NOTE]
   > Následující klíče nelze přiřadit jako součást klávesové zkratky v **globálním**formátu:
   >
   > - ENTER, TAB, CAPS LOCK
   > - Tisk SCRN/SYS RQ, SCROLL LOCK, pozastavení/přerušení
   > - Vložení, domů, konec, stránka nahoru, PageDown
   > - Klávesa s logem Windows, klíč aplikace, kterákoli z kláves se šipkami
   > - NUM LOCK, DELETE nebo Clear na numerické klávesnici
   > - Kombinace kláves CTRL + ALT + DELETE

6. V **stiskněte klávesy zkratky** zadejte klávesovou zkratku, kterou chcete použít.

    > [!NOTE]
    > Můžete vytvořit zástupce, který kombinuje písmeno s **Alt** klíč, **Ctrl** klíč, nebo obojí. Můžete také vytvořit zástupce, který kombinuje **Shift** klíč a písmeno s **Alt** klíč, **Ctrl** klíč, nebo obojí.

     Pokud je klávesová zkratka již přiřazena k jinému příkazu, zobrazí se v **zkratku aktuálně používá** pole. V takovém případě zvolte **Backspace** klávesy odstraňte tato zkratka, než se pokusíte nějaký jiný.

    ![Zadat jinou zkratku pro příkaz](../ide/media/reassignshortcut.png)

7. Zvolte **přiřadit** tlačítko.

    > [!NOTE]
    > Pokud pro příkaz zadáte jiný zástupce, klikněte na **přiřadit**a potom kliknutím na **Storno** zavřete dialogové okno, ale zástupce, který jste přiřadili, se nevrátí.

## <a name="share-custom-keyboard-shortcuts"></a>Sdílení vlastní klávesové zkratky

Vlastní klávesové zkratky je možné sdílet exportováním do souboru a předáním souboru ostatním, aby data mohli importovat.

### <a name="to-export-only-keyboard-shortcuts"></a>Export pouze klávesových zkratek

1. V panelu nabídky zvolte **nástroje** > **nastavení importu a exportu**.

2. Zvolte možnost **Exportovat vybrané nastavení prostředí**a pak zvolte možnost **Další**.

3. V části **jaká nastavení chcete exportovat?** , zrušte zaškrtnutí políčka **všechna nastavení** zaškrtávací políčko, rozbalte **možnosti**a potom rozbalte **prostředí**.

4. Zaškrtněte políčko **klávesnice** a klikněte na tlačítko **Další**.

   ![Exportovat jenom vlastní klávesové zkratky](../ide/media/exportshortcuts.png)

5. V poli **jak chcete pojmenovat soubor nastavení** a **Uložit soubor nastavení do tohoto adresáře** , buď ponechte výchozí hodnoty, nebo zadejte jiné hodnoty a pak zvolte **Dokončit**.

::: moniker range="vs-2017"

Ve výchozím nastavení, klávesové zkratky ukládány do souboru v *%USERPROFILE%\Documents\Visual Studio 2017\Settings* složky. Název souboru zobrazuje datum, kdy jste nastavení exportovali, a je rozšíření *.vssettings*.

::: moniker-end

::: moniker range=">=vs-2019"

Ve výchozím nastavení se zástupci ukládají do souboru ve složce *%UserProfile%\Documents\Visual Studio 2019 \ Settings* . Název souboru zobrazuje datum, kdy jste nastavení exportovali, a je rozšíření *.vssettings*.

::: moniker-end

### <a name="to-import-only-keyboard-shortcuts"></a>Import pouze klávesových zkratek

1. V panelu nabídky zvolte **nástroje** > **nastavení importu a exportu**.

2. Zvolte možnost **Importovat vybrané nastavení prostředí** a pak klikněte na tlačítko **Další**.

3. Klikněte na tlačítko **Ne, importovat nové nastavení, přepsat aktuální nastavení** a pak zvolte možnost **Další**.

4. V části **má nastavení**, zvolte soubor, který obsahuje klávesové zkratky, které chcete importovat, nebo zvolte **Procházet** vyhledejte správný soubor.

5. Zvolte **Další**.

6. V části **nastavení, které chcete importovat?** , zrušte zaškrtnutí políčka **všechna nastavení** zaškrtávací políčko, rozbalte **možnosti**a potom rozbalte **prostředí**.

7. Zaškrtněte políčko **klávesnice** a pak zvolte **Dokončit**.

   ![Importovat pouze vlastní klávesové zkratky](../ide/media/importshortcuts.png)

## <a name="see-also"></a>Viz také:

- [Funkce pro usnadnění přístupu sady Visual Studio](../ide/reference/accessibility-features-of-visual-studio.md)
