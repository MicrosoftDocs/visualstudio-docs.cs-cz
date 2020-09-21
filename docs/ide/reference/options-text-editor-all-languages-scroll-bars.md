---
title: Možnosti, textový editor, všechny jazyky, posuvníky
ms.date: 10/25/2018
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.All_Languages.ScrollBars
- VS.ToolsOptionsPages.Text_Editor.Basic.ScrollBars
- VS.ToolsOptionsPages.Text_Editor.CSharp.ScrollBars
- VS.ToolsOptionsPages.Text_Editor.C%2FC%2B%2B.ScrollBars
- VS.ToolsOptionsPages.Text_Editor.CoffeeScript.ScrollBars
- VS.ToolsOptionsPages.Text_Editor.CSS.ScrollBars
- VS.ToolsOptionsPages.Text_Editor.Dockerfile.ScrollBars
- VS.ToolsOptionsPages.Text_Editor.F%2523.ScrollBars
- VS.ToolsOptionsPages.Text_Editor.HQL.ScrollBars
- VS.ToolsOptionsPages.Text_Editor.HTML.ScrollBars
- VS.ToolsOptionsPages.Text_Editor.HTMLX.ScrollBars
- VS.ToolsOptionsPages.Text_Editor.JavaScript.ScrollBars
- VS.ToolsOptionsPages.Text_Editor.TypeScript.ScrollBars
- VS.ToolsOptionsPages.Text_Editor.JSON.ScrollBars
- VS.ToolsOptionsPages.Text_Editor.LESS.ScrollBars
- VS.ToolsOptionsPages.Text_Editor.Plain_Text.ScrollBars
- VS.ToolsOptionsPages.Text_Editor.ResJSON.ScrollBars
- VS.ToolsOptionsPages.Text_Editor.SCSS.ScrollBars
- VS.ToolsOptionsPages.Text_Editor.SQL_Server_Tools.ScrollBars
- VS.ToolsOptionsPages.Text_Editor.StreamAnalytics.ScrollBars
- VS.ToolsOptionsPages.Text_Editor.T-SQL90.ScrollBars
- VS.ToolsOptionsPages.Text_Editor.U-SQL.ScrollBars
- VS.ToolsOptionsPages.Text_Editor.XAML.ScrollBars
- VS.ToolsOptionsPages.Text_Editor.XML.ScrollBars
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c89be8a79aad9a2e3e0cdbc8601a08a99c1ad1aa
ms.sourcegitcommit: 566144d59c376474c09bbb55164c01d70f4b621c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2020
ms.locfileid: "90808087"
---
# <a name="options-text-editor-all-languages-scroll-bars"></a>Možnosti, textový editor, všechny jazyky, posuvníky
Toto dialogové okno umožňuje změnit výchozí chování posuvníku editoru kódu. Chcete-li zobrazit tyto možnosti, vyberte **Možnosti** v nabídce **nástroje** . V rámci složky **textový editor** rozbalte podsložku **všechny jazyky** a pak zvolte **posuvníky**.

> [!CAUTION]
> Tato stránka nastaví výchozí možnosti pro všechny vývojové jazyky. Resetování možnosti v tomto dialogovém okně obnoví možnosti posuvníků ve všech jazycích na jakékoli vybrané možnosti. Chcete-li změnit možnosti textového editoru pouze pro jeden jazyk, rozbalte podsložku pro daný jazyk a vyberte její stránky možností.

## <a name="show-horizontal-scroll-bar"></a>Zobrazit vodorovný posuvník

Když se tato možnost vybere, zobrazí vodorovný posuvník, který vám umožní posouvat se od sebe až po zobrazení prvků, které spadají mimo oblast zobrazení editoru. Pokud nejsou k dispozici vodorovné posuvníky, můžete k posouvání použít klávesy kurzoru.

## <a name="show-vertical-scroll-bar"></a>Zobrazit svislý posuvník

Je-li vybrána tato možnost, zobrazí svislý posuvník, který umožňuje posun nahoru a dolů k zobrazení prvků, které spadají mimo oblast zobrazení editoru. Pokud nejsou svislé posuvníky k dispozici, můžete k posouvání použít klávesu Page Up, Page Down a Cursor.

## <a name="display"></a>Zobrazení

### <a name="show-annotations-over-vertical-scroll-bar"></a>Zobrazit poznámky přes svislý posuvník

Vyberte, zda se u svislého posuvníku zobrazí následující poznámky:

- změny
- značky
- chyby
- pozice blikajícího kurzoru

> [!TIP]
> Možnost **Zobrazit značky** obsahuje zarážky a záložky.

Vyzkoušejte si to tak, že otevřete velký soubor kódu a nahradíte nějaký text, který se nachází na několika místech v souboru. Posuvník zobrazuje účinek nahrazení, takže můžete zálohovat změny, pokud jste nahradili něco, co byste neměli mít.

Podívejte se na [Rozšířený posuvník](/archive/blogs/cdnstudents/visual-studio-tips-and-tricks-enhanced-scroll-bar) v příspěvku na blogu, na kterém různé barvy a symboly znamenají při úpravách kódu.

## <a name="behavior"></a>Chování

Posuvník má dva režimy: režim pruhů a režim mapování.

### <a name="use-bar-mode-for-vertical-scroll-bar"></a>Pro svislý posuvník použít režim pruhového panelu

*Režim pruhů* zobrazuje indikátory poznámek na posuvníku. Kliknutím na posuvník posunete stránku nahoru nebo dolů, ale nepřejdete do tohoto umístění v souboru.

### <a name="use-map-mode-for-vertical-scroll-bar"></a>Pro svislý posuvník použít režim mapování

Když v *režimu mapování*kliknete na umístění na posuvníku, přesune se kurzor na toto místo v souboru místo pouhého posouvání nahoru nebo dolů stránky. Řádky kódu jsou v miniaturním zobrazení zobrazeny na posuvníku. Můžete zvolit, jak velký má sloupec mapy výběrem hodnoty v **přehledu zdroje**. Chcete-li povolit větší náhled kódu při přesunutí ukazatele na mapu, vyberte možnost **Zobrazit náhled tlačítka** . Sbalené oblasti jsou vybarvené jinak a při jejich dvojitém kliknutí se rozbalí.

> [!TIP]
> Zobrazení miniaturního kódu můžete zapnout v režimu mapování nastavením **zdrojového přehledu** na **vypnuto**. Pokud je vybrána možnost **Zobrazit náhled náhledu** , stále se zobrazuje náhled kódu v tomto umístění, když na posuvníku najedete ukazatel myši, a když na něj kliknete, přesune se kurzor na toto umístění v souboru.

## <a name="see-also"></a>Viz také

- [Postupy: přizpůsobení posuvníku](../how-to-track-your-code-by-customizing-the-scrollbar.md)