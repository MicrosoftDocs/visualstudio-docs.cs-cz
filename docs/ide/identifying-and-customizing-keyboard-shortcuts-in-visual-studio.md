---
description: Můžete určit klávesové zkratky pro příkazy sady Visual Studio, tyto zkratky přizpůsobit a exportovat je, aby je mohli používat ostatní uživatelé.
title: Identifikování a přizpůsobení klávesových zkratek
ms.date: 11/04/2016
ms.topic: how-to
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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: a1a3aa2ace6279211c27847b8b9cc46d71b0d9ad
ms.sourcegitcommit: 690bfc20744e4b543ee81030a60c8fc6d0d6610f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/29/2021
ms.locfileid: "113038600"
---
# <a name="identify-and-customize-keyboard-shortcuts-in-visual-studio"></a>Identifikace a přizpůsobení klávesových zkratek v Visual Studio

Můžete určit klávesové zkratky pro příkazy sady Visual Studio, tyto zkratky přizpůsobit a exportovat je, aby je mohli používat ostatní uživatelé. Mnoho zkratek vždy vyvolá stejné příkazy, ale chování zkratky se může lišit v závislosti na následujících podmínkách:

- Která výchozí nastavení prostředí zvolíte při prvním otevření Visual Studio, například Obecný vývoj &mdash; nebo Visual C#. (Informace o změně nebo resetování nastavení najdete v tématu [Nastavení prostředí](environment-settings.md).)

- Zda jste přizpůsobili chování zkratky.

- Kontext použitý při výběru zástupce. Klávesová zkratka **F2** například vyvolá příkaz , pokud používáte Návrháře `Edit.EditCell`  `File.Rename` **nastavení,** a vyvolá příkaz , pokud používáte Team Explorer .

Bez ohledu na nastavení, přizpůsobení a kontext můžete vždy najít a změnit klávesovou zkratku v **dialogovém okně** Možnosti. V části Oblíbené klávesové zkratky můžete také hledat výchozí klávesové zkratky pro několik desítek [příkazů.](../ide/default-keyboard-shortcuts-in-visual-studio.md#most-popular-keyboard-shortcuts) Úplný seznam všech výchozích klávesových zkratek (na základě nastavení **Obecné vývojové** prostředí) najdete v tématu Všechny [klávesové zkratky](../ide/default-keyboard-shortcuts-in-visual-studio.md).

Pokud je zástupce přiřazen k příkazu v *globálním* kontextu a žádné jiné kontexty, tato zkratka tento příkaz vždy vyvolá. Klávesová zkratka může být však přiřazena k jednomu příkazu v globálním kontextu a k jinému příkazu ve specifickém kontextu. Používáte-li takovou klávesovou zkratku v konkrétním kontextu, tato zkratka vyvolá příkaz pro konkrétní kontext, nikoli pro globální kontext.

> [!NOTE]
> Vaše nastavení a edice sady Visual Studio může změnit názvy a umístění příkazů nabídky a možnosti, které se zobrazí v dialogových oknech. Tato stránka je založená na **profilu Nastavení obecného** vývoje.

## <a name="identify-a-keyboard-shortcut"></a>Identifikace klávesové zkratky

1. Na řádku nabídek zvolte **Nástroje**  >  **Možnosti**.

2. Rozbalte **Prostředí** a pak zvolte **Klávesnice.**

   ![Zobrazení klávesových zkratek v dialogovém okně Možnosti](../ide/media/optionskeyboard.png)

3. Do **pole Zobrazit příkazy** obsahující zadejte celý název příkazu nebo jeho část bez mezer.

   Můžete například najít příkazy pro `solutionexplorer` .

4. V seznamu zvolte správný příkaz.

    Můžete například zvolit `View.SolutionExplorer` .

5. Pokud má příkaz klávesovou zkratku, zobrazí se v seznamu **zástupců vybraných** příkazů.

   ![Zobrazení zástupce pro zadaný příkaz](../ide/media/viewshortcut.png)

## <a name="customize-a-keyboard-shortcut"></a>Přizpůsobení klávesové zkratky

1. Na řádku nabídek zvolte **Nástroje**  >  **Možnosti**.

2. Rozbalte **Prostředí** a pak zvolte **Klávesnice.**

3. Volitelné: Vyfiltrujte seznam příkazů tak, že do pole **Zobrazit** příkazy obsahující zadáte celý název příkazu nebo jeho část bez mezer.

4. V seznamu vyberte příkaz, ke kterému chcete přiřadit klávesovou zkratku.

   V **seznamu Použít novou klávesovou** zkratku v vyberte oblast funkce, ve které chcete zástupce použít.

   Můžete například zvolit možnost **Globální,** pokud chcete, aby zástupce fungoval ve všech kontextech. Můžete použít jakoukoli zkratku, která není namapována (jako globální) v jiném editoru. V opačném případě editor zkratku přepíše.

   > [!NOTE]
   > Následující klávesy nelze přiřadit jako součást klávesové zkratky v **globálním měřítku:**
   >
   > - Enter, Tab, Caps Lock
   > - Print Scrn/Sys Rq, Scroll Lock, Pause/Break
   > - Insert, Home, End, Page Up, Page Down
   > - Klíč loga Windows, klíč aplikace, libovolná klávesa se šipkami
   > - Num Lock, Delete nebo Clear na číselné klávesnici
   > - Kombinace kláves Ctrl+Alt+Delete

6. Do pole **Klávesová zkratka zadejte** zástupce, který chcete použít.

    > [!NOTE]
    > Můžete vytvořit zástupce, který kombinuje písmeno s klávesou **Alt,** **klávesou Ctrl** nebo oběma klávesami. Můžete také vytvořit zástupce, který kombinuje klávesu **Shift** a písmeno s klávesou **Alt,** **klávesou Ctrl** nebo oběma klávesami.

     Pokud je zástupce již přiřazen k jinému příkazu, zobrazí se v poli **Zástupce aktuálně používaný příkazem** . V takovém případě zvolte klávesu **Backspace** a tuto klávesovou zkratku odstraňte, než zkusíte jinou.

    ![Zadání jiné zkratky pro příkaz](../ide/media/reassignshortcut.png)

7. Zvolte **tlačítko Přiřadit.**

    > [!NOTE]
    > Pokud pro příkaz zadáte jinou klávesovou zkratku, klikněte na Přiřadit a potom kliknutím na Zrušit dialogové okno zavřete, zástupce, který jste přiřadili, se nevrátil. 

## <a name="share-custom-keyboard-shortcuts"></a>Sdílení vlastních klávesových zkratek

Vlastní klávesové zkratky je možné sdílet exportováním do souboru a předáním souboru ostatním, aby data mohli importovat.

### <a name="to-export-only-keyboard-shortcuts"></a>Export pouze klávesových zkratek

1. V řádku nabídek zvolte Nástroje  >  **Nastavení importu a exportu.**

2. Zvolte **Exportovat vybrané nastavení prostředí** a pak zvolte **Další.**

3. V **části Jaká nastavení chcete exportovat?** zrušte zaškrtnutí políčka **Všechna** nastavení, rozbalte **Možnosti** a pak rozbalte **Prostředí**.

4. Zaškrtněte políčko **Klávesnice** a pak zvolte **Další.**

   ![Export jenom přizpůsobených klávesových zkratek](../ide/media/exportshortcuts.png)

5. V **polích Jak chcete** soubor nastavení  a Uložit můj soubor nastavení do tohoto adresáře ponechte výchozí hodnoty nebo zadejte jiné hodnoty a pak zvolte **Dokončit.**

::: moniker range="vs-2017"

Ve výchozím nastavení se klávesové zkratky ukládají do souboru ve složce *%USERPROFILE%\Documents\Visual Studio 2017\Settings.* Název souboru odráží datum exportu nastavení a přípona *je .vssettings*.

::: moniker-end

::: moniker range=">=vs-2019"

Ve výchozím nastavení se klávesové zkratky ukládají do souboru ve složce *%USERPROFILE%\Documents\Visual Studio 2019\Settings.* Název souboru odráží datum exportu nastavení a přípona *je .vssettings*.

::: moniker-end

### <a name="to-import-only-keyboard-shortcuts"></a>Import pouze klávesových zkratek

1. V řádku nabídek zvolte Nástroje  >  **Nastavení importu a exportu.**

2. Zvolte **tlačítko Importovat vybrané nastavení** prostředí a pak zvolte **Další.**

3. Zvolte tlačítko **ne, stačí importovat nová nastavení,** přepsat aktuální nastavení a pak zvolit **Další.**

4. V **části Moje** nastavení zvolte soubor obsahující zástupce, které chcete  importovat, nebo zvolte tlačítko Procházet a vyhledejte správný soubor.

5. Zvolte **Další**.

6. V **části Která nastavení chcete importovat?** zrušte zaškrtnutí políčka Všechna nastavení, rozbalte **Možnosti** a pak rozbalte **Prostředí**. 

7. Zaškrtněte políčko **Klávesnice** a pak zvolte **Dokončit.**

   ![Importovat jenom přizpůsobené klávesové zkratky](../ide/media/importshortcuts.png)

## <a name="see-also"></a>Viz také

- [Funkce usnadnění přístupu Visual Studio](../ide/reference/accessibility-features-of-visual-studio.md)
