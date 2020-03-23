---
title: Volby, Textový editor, Všechny jazyky, Posuvníky
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
ms.openlocfilehash: 54ce07537adc436f719de8596657d1367afcb87d
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "75588795"
---
# <a name="options-text-editor-all-languages-scroll-bars"></a>Volby, Textový editor, Všechny jazyky, Posuvníky
Toto dialogové okno umožňuje změnit výchozí chování posuvníku editoru kódu. Chcete-li tyto možnosti zobrazit, vyberte **možnosti** z nabídky **Nástroje.** Ve složce **Editor textu** rozbalte podsložku **Všechny jazyky** a pak zvolte **Posuvníky**.

> [!CAUTION]
> Tato stránka nastaví výchozí možnosti pro všechny vývojové jazyky. Obnovením volby v tomto dialogovém okně se volby posuvníků ve všech jazycích obnoví na libovolné volby, které jsou zde vybrány. Chcete-li změnit možnosti editoru textu pouze pro jeden jazyk, rozbalte podsložku pro daný jazyk a vyberte jeho stránky možností.

## <a name="show-horizontal-scroll-bar"></a>Zobrazit vodorovný posuvník

Je-li tato možnost vybrána, zobrazí se vodorovný posuvník, který umožňuje posunout se ze strany na stranu a zobrazit prvky, které spadají mimo oblast zobrazení editoru. Pokud vodorovné posuvníky nejsou k dispozici, můžete k posouvání použít kurzorové klávesy.

## <a name="show-vertical-scroll-bar"></a>Zobrazit svislý posuvník

Když je tato volba vybraná, zobrazí se svislý posuvník, který umožňuje posouvat se nahoru a dolů a zobrazit prvky, které spadají mimo oblast zobrazení editoru. Pokud nejsou k dispozici svislé posuvníky, můžete se posouvat pomocí kláves Page Up, Page Down a cursor.

## <a name="display"></a>Displej

### <a name="show-annotations-over-vertical-scroll-bar"></a>Zobrazení poznámk přes svislý posuvník

Vyberte, zda svislý posuvník zobrazuje následující poznámky:

- změny
- značky
- chyby
- poloha stříšky

> [!TIP]
> Možnost **Zobrazit značky** obsahuje zarážky a záložky.

Vyzkoušejte to otevřením velkého souboru kódu a nahrazením některého textu, který se vyskytuje na několika místech v souboru. Posuvník zobrazuje efekt nahrazení, takže změny můžete vyvrátit, pokud jste nahradili něco, co byste neměli mít.

Podívejte se na příspěvek blogu [rozšířeného posuvníku](https://blogs.msdn.microsoft.com/cdnstudents/2014/01/21/visual-studio-tips-and-tricks-enhanced-scroll-bar/) o tom, co znamenají různé barvy a symboly při úpravách kódu.

## <a name="behavior"></a>Chování

Posuvník má dva režimy: režim pruhu a režim mapy.

### <a name="use-bar-mode-for-vertical-scroll-bar"></a>Použití režimu pruhu pro svislý posuvník

*Režim pruhů* zobrazuje na posuvníku indikátory poznámky. Kliknutím na posuvník posunete stránku nahoru nebo dolů, ale nepřeskočíte do tohoto umístění v souboru.

### <a name="use-map-mode-for-vertical-scroll-bar"></a>Použití režimu mapy pro svislý posuvník

V *režimu mapy*klepnete po klepnutí na umístění na posuvníku kurzor na toto umístění v souboru, místo aby se jen posouval nahoru nebo dolů po stránce. Řádky kódu jsou zobrazeny v miniatuře na posuvníku. Výběrem hodnoty v **přehledu zdroje**můžete zvolit, jak široký je sloupec mapy . Chcete-li povolit větší náhled kódu při umístění ukazatele na mapě, vyberte volbu **Zobrazit náhled v popisku.** Sbalené oblasti jsou popodvojené oblasti různě stínovány a popodvojené.

> [!TIP]
> Zobrazení miniaturního kódu můžete vypnout v režimu mapy nastavením **přehledu zdroje** na **Vypnuto**. Pokud je **vybraná možnost Zobrazit popisek náhledu,** zobrazí se při umístění náhled kódu, když na pojedete ukazatelem myši na posuvníku, a kurzor na toto místo v souboru po klepnutí stále přejde do tohoto umístění.

## <a name="see-also"></a>Viz také

- [Postup: Přizpůsobení posuvníku](../how-to-track-your-code-by-customizing-the-scrollbar.md)
