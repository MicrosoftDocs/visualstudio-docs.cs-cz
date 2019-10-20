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
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 585c50818148235cebcdda3f18a9ed91f1a2aa1a
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72656487"
---
# <a name="identify-and-customize-keyboard-shortcuts-in-visual-studio"></a>Identifikace a přizpůsobení klávesových zkratek v aplikaci Visual Studio

Můžete určit klávesové zkratky pro příkazy sady Visual Studio, tyto zkratky přizpůsobit a exportovat je, aby je mohli používat ostatní uživatelé. Mnoho zkratek vždy vyvolá stejné příkazy, ale chování zkratky se může lišit v závislosti na následujících podmínkách:

- Které výchozí nastavení prostředí si zvolíte při prvním otevření sady Visual Studio &mdash;for příklad, obecný vývoj nebo vizuál C#. (Informace o změně nebo resetování nastavení naleznete v tématu [nastavení prostředí](environment-settings.md).)

- Zda jste přizpůsobili chování zkratky.

- Kontext použitý při výběru zástupce. Například zkratka **F2** vyvolá příkaz `Edit.EditCell`, pokud používáte **Návrháře nastavení** a vyvolá příkaz `File.Rename`, pokud používáte **Team Explorer**.

Bez ohledu na nastavení, přizpůsobení a kontext můžete klávesovou zkratku vždycky najít a změnit v dialogovém okně **Možnosti** . Můžete také vyhledat výchozí klávesové zkratky pro několik desítek příkazů v [oblíbených klávesových zkratkách](../ide/default-keyboard-shortcuts-for-frequently-used-commands-in-visual-studio.md). Úplný seznam všech výchozích klávesových zkratek (na základě **obecného nastavení vývoje** ) najdete v tématu [všechny klávesové zkratky](../ide/default-keyboard-shortcuts-in-visual-studio.md).

Pokud je zástupce přiřazen k příkazu v *globálním* kontextu a žádné jiné kontexty, tento zástupce Tento příkaz vždycky vyvolá. Klávesová zkratka může být však přiřazena k jednomu příkazu v globálním kontextu a k jinému příkazu ve specifickém kontextu. Používáte-li takovou klávesovou zkratku v konkrétním kontextu, tato zkratka vyvolá příkaz pro konkrétní kontext, nikoli pro globální kontext.

> [!NOTE]
> Vaše nastavení a edice sady Visual Studio může změnit názvy a umístění příkazů nabídky a možnosti, které se zobrazí v dialogových oknech. Tato stránka je založena na profilu **obecného** nastavení pro vývoj.

## <a name="identify-a-keyboard-shortcut"></a>Identifikace klávesové zkratky

1. Na panelu nabídek vyberte možnost **nástroje**  > **Možnosti**.

2. Rozbalte položku **prostředí**a pak zvolte možnost **klávesnice**.

   ![Zobrazení klávesových zkratek v dialogovém okně Možnosti](../ide/media/optionskeyboard.png)

3. V poli **Zobrazit příkazy** , které obsahují, zadejte celý příkaz nebo část názvu příkazu bez mezer.

   Můžete například najít příkazy pro `solutionexplorer`.

4. V seznamu zvolte správný příkaz.

    Můžete například vybrat `View.SolutionExplorer`.

5. Pokud má příkaz klávesovou zkratku, zobrazí se v **zkratkách pro vybraný seznam příkazů** .

   ![Zobrazit zástupce pro zadaný příkaz](../ide/media/viewshortcut.png)

## <a name="customize-a-keyboard-shortcut"></a>Přizpůsobení klávesové zkratky

1. Na panelu nabídek vyberte možnost **nástroje**  > **Možnosti**.

2. Rozbalte položku **prostředí**a pak zvolte možnost **klávesnice**.

3. Volitelné: vyfiltrujte seznam příkazů zadáním celého názvu nebo části názvu příkazu bez mezer v poli **Zobrazit příkazy** , které obsahují.

4. V seznamu vyberte příkaz, ke kterému chcete přiřadit klávesovou zkratku.

   V seznamu **použít nového zástupce v** seznamu vyberte oblast funkcí, ve které chcete zástupce použít.

   Můžete například zvolit **globální** , pokud chcete, aby zástupce pracoval ve všech kontextech. Můžete použít jakoukoli zkratku, která není namapována (jako globální) v jiném editoru. V opačném případě editor zkratku přepíše.

   > [!NOTE]
   > Následující klíče nelze přiřadit jako součást klávesové zkratky v **globálním**formátu:
   >
   > - ENTER, TAB, CAPS LOCK
   > - Tisk SCRN/SYS RQ, SCROLL LOCK, pozastavení/přerušení
   > - Vložení, domů, konec, stránka nahoru, PageDown
   > - Klávesa s logem Windows, klíč aplikace, kterákoli z kláves se šipkami
   > - NUM LOCK, DELETE nebo Clear na numerické klávesnici
   > - Kombinace kláves CTRL + ALT + DELETE

6. V poli **stisknutí klávesových zkratek** zadejte klávesovou zkratku, kterou chcete použít.

    > [!NOTE]
    > Můžete vytvořit zástupce, který kombinuje písmeno s klávesou **ALT** , klávesou **CTRL** nebo obojím. Můžete také vytvořit zástupce, který kombinuje klávesu **SHIFT** a písmeno s klávesou **ALT** , klávesou **CTRL** nebo obojím.

     Pokud je zástupce už přiřazený k jinému příkazu, zobrazí se v poli **zástupce, který aktuálně používá** . V takovém případě stiskněte klávesu **BACKSPACE** k odstranění tohoto zástupce před tím, než se pokusíte použít jiný příkaz.

    ![Zadat jiný zástupce pro příkaz](../ide/media/reassignshortcut.png)

7. Klikněte na tlačítko **přiřadit** .

    > [!NOTE]
    > Pokud pro příkaz zadáte jiný zástupce, klikněte na **přiřadit**a potom kliknutím na **Storno** zavřete dialogové okno, ale zástupce, který jste přiřadili, se nevrátí.

## <a name="share-custom-keyboard-shortcuts"></a>Sdílení vlastních klávesových zkratek

Vlastní klávesové zkratky je možné sdílet exportováním do souboru a předáním souboru ostatním, aby data mohli importovat.

### <a name="to-export-only-keyboard-shortcuts"></a>Export pouze klávesových zkratek

1. Na panelu nabídek vyberte **nástroje**  > **Nastavení importu a exportu**.

2. Zvolte možnost **Exportovat vybrané nastavení prostředí**a pak zvolte možnost **Další**.

3. V části **Jaké nastavení chcete exportovat?** zrušte zaškrtnutí políčka **všechna nastavení** , rozbalte položku Možnosti a potom rozbalte **možnost** **prostředí**.

4. Zaškrtněte políčko **klávesnice** a klikněte na tlačítko **Další**.

   ![Export pouze přizpůsobených klávesových zkratek](../ide/media/exportshortcuts.png)

5. V poli **jak chcete pojmenovat soubor nastavení** a **Uložit soubor nastavení do tohoto adresáře** , buď ponechte výchozí hodnoty, nebo zadejte jiné hodnoty a pak zvolte **Dokončit**.

::: moniker range="vs-2017"

Ve výchozím nastavení se zástupci ukládají do souboru ve složce *%UserProfile%\Documents\Visual Studio 2017 \ Settings* . Název souboru odráží datum, kdy jste nastavení exportovali, a přípona je *. vssettings*.

::: moniker-end

::: moniker range=">=vs-2019"

Ve výchozím nastavení se zástupci ukládají do souboru ve složce *%UserProfile%\Documents\Visual Studio 2019 \ Settings* . Název souboru odráží datum, kdy jste nastavení exportovali, a přípona je *. vssettings*.

::: moniker-end

### <a name="to-import-only-keyboard-shortcuts"></a>Import pouze klávesových zkratek

1. Na panelu nabídek vyberte **nástroje**  > **Nastavení importu a exportu**.

2. Zvolte možnost **Importovat vybrané nastavení prostředí** a pak klikněte na tlačítko **Další**.

3. Klikněte na tlačítko **Ne, importovat nové nastavení, přepsat aktuální nastavení** a pak zvolte možnost **Další**.

4. V části **Moje nastavení**vyberte soubor obsahující zástupce, které chcete importovat, nebo klikněte na tlačítko **Procházet** a vyhledejte správný soubor.

5. Klikněte na tlačítko **Další**.

6. V části **které nastavení chcete importovat?** zrušte zaškrtnutí políčka **všechna nastavení** , rozbalte položku Možnosti a potom rozbalte **možnost** **prostředí**.

7. Zaškrtněte políčko **klávesnice** a pak zvolte **Dokončit**.

   ![Import pouze přizpůsobených klávesových zkratek](../ide/media/importshortcuts.png)

## <a name="see-also"></a>Viz také:

- [Funkce usnadnění v aplikaci Visual Studio](../ide/reference/accessibility-features-of-visual-studio.md)