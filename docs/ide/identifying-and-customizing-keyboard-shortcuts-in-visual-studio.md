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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "75591330"
---
# <a name="identify-and-customize-keyboard-shortcuts-in-visual-studio"></a>Identifikace a přizpůsobení klávesových zkratek v Sadě Visual Studio

Můžete určit klávesové zkratky pro příkazy sady Visual Studio, tyto zkratky přizpůsobit a exportovat je, aby je mohli používat ostatní uživatelé. Mnoho zkratek vždy vyvolá stejné příkazy, ale chování zkratky se může lišit v závislosti na následujících podmínkách:

- Které výchozí nastavení prostředí zvolíte při prvním&mdash;spuštění sady Visual Studio, například Obecné vývoj nebo Visual C#. (Informace o změně nebo obnovení nastavení naleznete v [tématu Nastavení prostředí](environment-settings.md).)

- Zda jste přizpůsobili chování zkratky.

- Kontext použitý při výběru zástupce. Například zkratka **F2** vyvolá `Edit.EditCell` příkaz, pokud používáte **Návrhář nastavení** a `File.Rename` vyvolá příkaz, pokud používáte **Průzkumníka týmu**.

Bez ohledu na nastavení, přizpůsobení a kontext můžete vždy najít a změnit klávesovou zkratku v dialogovém okně **Možnosti.** Můžete také vyhledat výchozí klávesové zkratky pro několik desítek příkazů v [populární klávesové zkratky](../ide/default-keyboard-shortcuts-for-frequently-used-commands-in-visual-studio.md). Úplný seznam všech výchozích klávesových zkratek (na základě nastavení **Obecného vývoje)** naleznete v tématu [Všechny klávesové zkratky](../ide/default-keyboard-shortcuts-in-visual-studio.md).

Pokud je zkratka přiřazena příkazu v *globálním* kontextu a bez jiných kontextů, bude tento zástupce vždy vyvolat tento příkaz. Klávesová zkratka může být však přiřazena k jednomu příkazu v globálním kontextu a k jinému příkazu ve specifickém kontextu. Používáte-li takovou klávesovou zkratku v konkrétním kontextu, tato zkratka vyvolá příkaz pro konkrétní kontext, nikoli pro globální kontext.

> [!NOTE]
> Vaše nastavení a edice sady Visual Studio může změnit názvy a umístění příkazů nabídky a možnosti, které se zobrazí v dialogových oknech. Tato stránka je založena na profilu nastavení **obecného vývoje.**

## <a name="identify-a-keyboard-shortcut"></a>Identifikace klávesové zkratky

1. Na řádku nabídek zvolte**Možnosti** **nástrojů** > .

2. Rozbalte **možnost Prostředí**a pak zvolte **Klávesnice**.

   ![Zobrazení klávesových zkratek v dialogovém okně Možnosti](../ide/media/optionskeyboard.png)

3. Do pole **Zobrazit příkazy obsahující** zadejte celý název příkazu bez mezer nebo jeho část.

   Můžete například najít příkazy `solutionexplorer`pro .

4. V seznamu zvolte správný příkaz.

    Můžete například zvolit `View.SolutionExplorer`.

5. Pokud má příkaz klávesovou zkratku, zobrazí se v seznamu **vybraných příkazů Zkratky.**

   ![Zobrazení zástupce určeného příkazu](../ide/media/viewshortcut.png)

## <a name="customize-a-keyboard-shortcut"></a>Přizpůsobení klávesové zkratky

1. Na řádku nabídek zvolte**Možnosti** **nástrojů** > .

2. Rozbalte **možnost Prostředí**a pak zvolte **Klávesnice**.

3. Volitelné: Seznam příkazů můžete filtrovat zadáním celého názvu příkazu bez mezer nebo jeho části do pole **Zobrazit příkazy obsahující.**

4. V seznamu vyberte příkaz, ke kterému chcete přiřadit klávesovou zkratku.

   V seznamu **Použít nový zástupce vyberte** oblast funkcí, ve které chcete zástupce použít.

   Můžete například zvolit **Globální,** pokud chcete, aby zástupce fungoval ve všech kontextech. Můžete použít jakoukoli zkratku, která není namapována (jako globální) v jiném editoru. V opačném případě editor zkratku přepíše.

   > [!NOTE]
   > V **globálním programu**nelze přiřadit následující klávesy jako součást klávesové zkratky :
   >
   > - Enter, Tab, Caps Lock
   > - Tisk Scrn/Sys Rq, Scroll Lock, Pause/Break
   > - Vložit, Domů, Konec, Stránka nahoru, Stránka dolů
   > - Klávesa s logem Windows, klíč aplikace, kterákoli ze šipek
   > - Uzamčení, odstranit nebo vymazat na numerické klávesnici
   > - Kombinace kláves Ctrl+Alt+Delete

6. Do pole **Stiskněte klávesové zkratky** zadejte zástupce, který chcete použít.

    > [!NOTE]
    > Můžete vytvořit zástupce, který kombinuje písmeno s klávesou **Alt,** klávesou **Ctrl** nebo oběma. Můžete také vytvořit zástupce, který kombinuje klávesu **Shift** a písmeno s klávesou **Alt,** klávesou **Ctrl** nebo obojím.

     Pokud je zástupce již přiřazen k jinému příkazu, zobrazí se v poli **Zástupce aktuálně používaný.** V takovém případě zvolte klávesu **Backspace,** chcete-li odstranit tuto zkratku, než se pokusíte jinou.

    ![Určení jiného zástupce příkazu](../ide/media/reassignshortcut.png)

7. Zvolte tlačítko **Přiřadit.**

    > [!NOTE]
    > Pokud pro příkaz zadáte jinou zkratku, klepněte na **tlačítko Přiřadit**a klepnutím na tlačítko **Storno** zavřete dialogové okno, přiřazená zkratka se nevrátí zpět.

## <a name="share-custom-keyboard-shortcuts"></a>Sdílení vlastních klávesových zkratek

Vlastní klávesové zkratky je možné sdílet exportováním do souboru a předáním souboru ostatním, aby data mohli importovat.

### <a name="to-export-only-keyboard-shortcuts"></a>Export pouze klávesových zkratek

1. Na řádku nabídek zvolte **Nástroje** > **importu a exportu nastavení**.

2. Zvolte **Exportovat vybraná nastavení prostředí**a pak zvolte **Další**.

3. V části **Jaká nastavení chcete exportovat?** **All Settings** **Options** **Environment**

4. Zaškrtněte políčko **Klávesnice** a pak zvolte **Další**.

   ![Exportovat pouze přizpůsobené klávesové zkratky](../ide/media/exportshortcuts.png)

5. V části **Co chcete pojmenovat soubor nastavení** a Uložit soubor nastavení do těchto polí **adresáře,** ponechejte výchozí hodnoty nebo zadejte různé hodnoty a pak zvolte **Dokončit**.

::: moniker range="vs-2017"

Ve výchozím nastavení jsou zástupci uloženi v souboru ve složce *%USERPROFILE%\Documents\Visual Studio 2017\Settings.* Název souboru odráží datum, kdy jste nastavení exportovali, a přípona je *.vssettings*.

::: moniker-end

::: moniker range=">=vs-2019"

Ve výchozím nastavení jsou zástupci uloženi v souboru ve složce *%USERPROFILE%\Documents\Visual Studio 2019\Settings.* Název souboru odráží datum, kdy jste nastavení exportovali, a přípona je *.vssettings*.

::: moniker-end

### <a name="to-import-only-keyboard-shortcuts"></a>Import pouze klávesových zkratek

1. Na řádku nabídek zvolte **Nástroje** > **importu a exportu nastavení**.

2. Zvolte tlačítko **Importovat vybrané nastavení prostředí** a pak zvolte **Další**.

3. Zvolte **Ne, stačí importovat nová nastavení, přepsat tlačítko aktuálního nastavení** a pak zvolte **Další**.

4. V části **Moje nastavení**vyberte soubor obsahující zástupce, které chcete importovat, nebo zvolte tlačítko **Procházet,** chcete-li najít správný soubor.

5. Zvolte **Další**.

6. V části **Která nastavení chcete importovat?** **All Settings** **Options** **Environment**

7. Zaškrtněte políčko **Klávesnice** a pak zvolte **Dokončit**.

   ![Importovat pouze přizpůsobené klávesové zkratky](../ide/media/importshortcuts.png)

## <a name="see-also"></a>Viz také

- [Funkce usnadnění v sadě Visual Studio](../ide/reference/accessibility-features-of-visual-studio.md)
