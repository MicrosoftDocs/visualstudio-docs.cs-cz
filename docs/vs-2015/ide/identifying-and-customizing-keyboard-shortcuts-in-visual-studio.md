---
title: Identifikování a přizpůsobení klávesových zkratek
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
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
ms.assetid: d2774be2-60a4-4d6f-95f1-79d0d9e55b56
caps.latest.revision: 30
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: e63395838d7d91170d54edbb07c0b38db548ccdf
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "72670494"
---
# <a name="identifying-and-customizing-keyboard-shortcuts-in-visual-studio"></a>Identifikování a přizpůsobení klávesových zkratek v sadě Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Můžete určit klávesové zkratky pro příkazy sady Visual Studio, tyto zkratky přizpůsobit a exportovat je, aby je mohli používat ostatní uživatelé. Mnoho zkratek vždy vyvolá stejné příkazy, ale chování zkratky se může lišit v závislosti na následujících podmínkách:

- Výchozí nastavení prostředí, které jste vybrali při prvním spuštění sady Visual Studio (například obecný vývoj nebo Visual C#).

- Zda jste přizpůsobili chování zkratky.

- Kontext použitý při výběru zástupce. Například zkratka F2 vyvolá příkaz Edit.EditCell, pokud používáte Návrháře nastavení, a příkaz File.Rename, pokud používáte Průzkumník týmových projektů.

  Bez ohledu na nastavení, přizpůsobení a kontext můžete klávesovou zkratku vždycky najít a změnit v dialogovém okně **Možnosti** . Můžete také vyhledat výchozí klávesové zkratky pro několik desítek příkazů ve [výchozích klávesových zkratkách pro často používané příkazy](../ide/default-keyboard-shortcuts-for-frequently-used-commands-in-visual-studio.md)a můžete najít úplný seznam všech výchozích klávesových zkratek (na základě obecného nastavení vývoje) ve [výchozích klávesových zkratkách](../ide/default-keyboard-shortcuts-in-visual-studio.md).

  **V tomto tématu**

- [Identifikace klávesových zkratek](../ide/identifying-and-customizing-keyboard-shortcuts-in-visual-studio.md#bkmk_identify)

- [Přizpůsobení klávesové zkratky](../ide/identifying-and-customizing-keyboard-shortcuts-in-visual-studio.md#bkmk_assign)

- [Sdílení vlastních klávesových zkratek](../ide/identifying-and-customizing-keyboard-shortcuts-in-visual-studio.md#bkmk_transfer)

  Pokud je klávesová zkratka přiřazena k příkazu v globálním kontextu a bez jiných kontextů, tato zkratka vždy vyvolá daný příkaz. Klávesová zkratka může být však přiřazena k jednomu příkazu v globálním kontextu a k jinému příkazu ve specifickém kontextu. Používáte-li takovou klávesovou zkratku v konkrétním kontextu, tato zkratka vyvolá příkaz pro konkrétní kontext, nikoli pro globální kontext.

> [!NOTE]
> Vaše nastavení a edice sady Visual Studio může změnit názvy a umístění příkazů nabídky a možnosti, které se zobrazí v dialogových oknech. Toto téma je založeno na **obecném nastavení pro vývoj**.

## <a name="identifying-a-keyboard-shortcut"></a><a name="bkmk_identify"></a> Identifikace klávesových zkratek

1. Na řádku nabídek klikněte na **nástroje**, **Možnosti**.

2. Rozbalte položku **prostředí**a pak zvolte možnost **klávesnice**.

     ![Zobrazení klávesových zkratek v dialogovém okně Možnosti](../ide/media/optionskeyboard.png "OptionsKeyboard")

3. V poli **Zobrazit příkazy** , které obsahují, zadejte celý příkaz nebo část názvu příkazu bez mezer.

     Můžete například najít příkazy pro **SolutionExplorer**.

4. V seznamu zvolte správný příkaz.

     Můžete například vybrat **Zobrazit. SolutionExplorer**.

5. Pokud má příkaz klávesovou zkratku, zobrazí se v **zkratkách pro vybraný seznam příkazů** .

     ![Zobrazit zástupce pro zadaný příkaz](../ide/media/viewshortcut.png "ViewShortcut")

## <a name="customizing-a-keyboard-shortcut"></a><a name="bkmk_assign"></a> Přizpůsobení klávesové zkratky

1. Na řádku nabídek klikněte na **nástroje**, **Možnosti**.

2. Rozbalte složku **prostředí** a pak zvolte možnost **klávesnice**.

     ![Zobrazení klávesových zkratek v dialogovém okně Možnosti](../ide/media/optionskeyboard.png "OptionsKeyboard")

3. V poli **Zobrazit příkazy** , které obsahují, zadejte celý příkaz nebo část názvu příkazu bez mezer.

     Můžete například najít příkazy pro **SolutionExplorer**.

4. V seznamu vyberte příkaz, ke kterému chcete přiřadit klávesovou zkratku.

5. V seznamu **použít nového zástupce v** seznamu vyberte oblast funkcí, ve které chcete zástupce použít.

     Můžete například zvolit **globální** , pokud chcete, aby zástupce pracoval ve všech kontextech. Můžete použít jakoukoli zkratku, která není namapována (jako globální) v jiném editoru. V opačném případě editor zkratku přepíše.

    > [!NOTE]
    > Následující klíče nemůžete přiřadit jako součást klávesové zkratky v **globálním**formátu: Print Scrn/Sys Rq, SCROLL LOCK, Pause/Break, TAB, CAPS LOCK, vložení, domů, konec, stránka nahoru, PageDown, klávesa s logem Windows, klávesa aplikace, kterákoli z kláves se šipkami nebo ENTER; NUM LOCK, DELETE nebo Clear na numerické klávesnici; nebo CTRL + ALT + DELETE.

6. V poli **stisknutí klávesových zkratek** zadejte klávesovou zkratku, kterou chcete použít.

    > [!NOTE]
    > Můžete vytvořit zástupce, který kombinuje písmeno s klávesou Alt, klávesou Ctrl nebo oběma klávesami. Můžete také vytvořit zástupce, který kombinuje klávesu Shift a písmeno s klávesou Alt, klávesou Ctrl nebo oběma klávesami.

     Pokud je zástupce už přiřazený k jinému příkazu, zobrazí se v poli **zástupce, který aktuálně používá** . V takovém případě stisknutím klávesy Backspace tuto klávesovou zkratku smažte a zkuste jinou.

     ![Zadat jiný zástupce pro příkaz](../ide/media/reassignshortcut.png "ReassignShortcut")

7. Klikněte na tlačítko **přiřadit** .

    > [!NOTE]
    > Pokud pro příkaz zadáte jiný zástupce, klikněte na tlačítko **přiřadit** a pak klikněte na tlačítko **Zrušit** , dialogové okno se zavře, ale změna se nevrátí.

## <a name="sharing-custom-keyboard-shortcuts"></a><a name="bkmk_transfer"></a> Sdílení vlastních klávesových zkratek
 Vlastní klávesové zkratky je možné sdílet exportováním do souboru a předáním souboru ostatním, aby data mohli importovat.

#### <a name="to-export-only-keyboard-shortcuts"></a>Export pouze klávesových zkratek

1. Na řádku nabídek klikněte na **nástroje**, **Nastavení importu a exportu**.

2. Zvolte **Exportovat vybrané nastavení prostředí**a pak klikněte na tlačítko **Další** .

3. V části **Jaké nastavení chcete exportovat?** zrušte zaškrtnutí políčka **všechna nastavení** , rozbalte položku Možnosti a potom rozbalte **možnost** **prostředí**.

4. Zaškrtněte políčko **klávesnice** a pak klikněte na tlačítko **Další** .

     ![Export pouze přizpůsobených klávesových zkratek](../ide/media/exportshortcuts.png "ExportShortcuts")

5. V poli **jak chcete pojmenovat soubor nastavení?** a **Uložit do tohoto adresáře soubor nastavení** , buď ponechte výchozí hodnoty, nebo zadejte jiné hodnoty a pak klikněte na tlačítko **Dokončit** .

     Ve výchozím nastavení jsou klávesové zkratky ukládány do souboru ve složce USERPROFILE%\Documents\Visual Studio 2013\Settings. Název souboru zobrazuje datum, kdy jste nastavení exportovali, a přípona je .vssettings.

#### <a name="to-import-only-keyboard-shortcuts"></a>Import pouze klávesových zkratek

1. Na řádku nabídek klikněte na **nástroje**, **Nastavení importu a exportu**.

2. Zvolte přepínač **Importovat vybrané nastavení prostředí** a pak klikněte na tlačítko **Další** .

3. Klikněte na tlačítko **Ne, importovat nové nastavení, přepsat aktuální nastavení,** a poté klikněte na tlačítko **Další** .

4. V části **Moje nastavení**vyberte soubor obsahující zástupce, které chcete importovat, nebo klikněte na tlačítko **Procházet** a vyhledejte správný soubor.

5. Klikněte na tlačítko **Další** .

6. V části **které nastavení chcete importovat?** zrušte zaškrtnutí políčka **všechna nastavení** , rozbalte položku Možnosti a potom rozbalte **možnost** **prostředí**.

7. Zaškrtněte políčko **klávesnice** a pak klikněte na tlačítko **Dokončit** .

     ![Import pouze přizpůsobených klávesových zkratek](../ide/media/importshortcuts.png "ImportShortcuts")

## <a name="see-also"></a>Viz také
 [Funkce pro usnadnění přístupu sady Visual Studio](../ide/reference/accessibility-features-of-visual-studio.md)
