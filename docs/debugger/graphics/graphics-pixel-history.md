---
title: Historie pixelů grafiky | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.graphics.pixelhistory
ms.assetid: 0a2cbde5-1ad9-487e-857c-a3664158c268
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 9e0302e4b245a4fbf94d0eb49850101c404cd8a2
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2018
ms.locfileid: "31479952"
---
# <a name="graphics-pixel-history"></a>Historie pixelů grafiky
Okno historie pixelů grafiky ve Visual Studio Graphics Analyzer vám pomůže pochopit, jak je konkrétní pixelů ovlivňován Direct3D – události, které nastaly během rámce hry nebo aplikace.  
  
 Toto je okno historie pixelu:  
  
 ![Pixel, s třemi Direct3D – události v historii. ](media/gfx_diag_demo_pixel_history_orientation.png "gfx_diag_demo_pixel_history_orientation")  
  
## <a name="understanding-the-pixel-history-window"></a>Principy okno historie pixelu  
 Pomocí historie pixelů, můžete analyzovat, jak je konkrétní pixelů cíle vykreslení ovlivňován Direct3D – události během rámce. Lze přesně určit vykreslování problém pro konkrétní Direct3D – události, i když následující události – nebo následné primitiv v stejné události – nadále změnit je poslední barva hodnota. Například mohou být pixel vykresluje nesprávně a pak zakódován o jiné, poloprůhledné bod, takže jejich barvy jsou obsahuje tyto údaje společně framebuffer. Tento druh problému by bylo obtížné diagnostikovat, jestli jste měli pouze poslední obsah na cílovou vykreslení vás.  
  
 V okně historie pixelu zobrazí úplnou historii jeden bod v průběhu vybraného rámce. **Konečné vyrovnávací paměť snímku** v horní části okna zobrazí barvu, která je zapsán do framebuffer na konci rámečku, společně s další informace o pixelů například rámce, který pochází z a jeho obrazovky souřadnice. Tato oblast obsahuje také **vykreslení Alpha** zaškrtávací políčko. Když toto políčko zaškrtnuto, **konečné vyrovnávací paměť snímku** barvy a prostřední barvu hodnoty jsou zobrazeny s průhlednost přes šachovnicový vzor. Pokud je zaškrtnutí políčka zrušeno, alfa kanálu hodnot barva ignorována.  
  
 Dolní části okna zobrazí události, které měl možnost vliv na barvu pixelů, společně s **počáteční** a **konečné** pseudo události, které představují hodnoty počáteční a finální barev pixelů v framebuffer. Hodnota počáteční barvu je dáno první událost, která změnit barvu pixel (obvykle `Clear` událostí). Jeden bod vždy má tyto dvě pseudo události v historii, i v případě, že žádné další události vliv na jeho. Při další události, měl možnost mít vliv pixel, jsou zobrazeny mezi **počáteční** a **konečné** události. Události můžete rozbalit a zobrazit podrobnosti. Pro jednoduché události například ty, které vymazat cíl vykreslení efekt události je právě hodnoty barvy. Složitější událostmi, jako je například volání kreslení vygenerovat jeden nebo více primitivních elementů, které může přispět k barvu pixelech.  
  
 Základní prvky, které byly vykreslovat událost jsou identifikovány jejich primitivní typ a index, společně s celkový počet primitivní pro objekt. Například identifikátor jako **trojúhelník (1456) (6214)** znamená, že primitivní odpovídá 1456th trojúhelníček v objektu, který se skládá z 6214 trojúhelníčky. Nalevo od každého primitivní identifikátor je ikonu, která shrnuje vliv primitivní na pixelech. Základní prvky, které ovlivňují barev pixelů jsou reprezentované pomocí zaokrouhlené obdélníku, která je vyplněno barvou výsledek. Základní prvky, které jsou vyloučené z mají vliv na barvu pixelů jsou reprezentované pomocí ikony, které určují z důvodu, aby se vyloučila pixelech. Tyto ikony jsou popsané v části [primitivní vyloučení](#exclusion) dále v tomto článku.  
  
 Můžete rozbalit každý primitivní zjistit, jak byl výstup shaderu pixelů sloučit s existující barev pixelů a vytvoření barev výsledek. Odsud můžete také zkontrolovat nebo ladění kódu shaderu pixelů, který je spojen s primitivní, a můžete dále rozšířit uzlu vrchol shaderu Prozkoumat shaderu vrchol vstup.  
  
###  <a name="exclusion"></a> Primitivní vyloučení  
 Pokud na primitivní je vyloučen z ovlivnění barev pixelů, vyloučení mohlo dojít z různých důvodů. Každý důvod je reprezentována ikonu, která je popsaná v této tabulce:  
  
|Ikona|Důvod k vyloučení|  
|----------|--------------------------|  
|![Ikona selhání testu hloubka. ](media/vsg_hist_icon_failed_depth.png "vsg_hist_icon_failed_depth")|Pixel se vyloučilo, protože se nepovedlo hloubka test.|  
|![Ikona selhání testu Nůžkovité. ](media/vsg_hist_icon_failed_scissor.png "vsg_hist_icon_failed_scissor")|Pixel se vyloučilo, protože se jí nepovedlo Nůžkovité test.|  
|![Ikona selhání testu vzorníku. ](media/vsg_hist_icon_failed_stencil.png "vsg_hist_icon_failed_stencil")|Pixel se vyloučilo, protože se nepovedlo vzorníku test.|  
  
### <a name="draw-call-exclusion"></a>Kreslení volání vyloučení  
 Pokud všechny primitiv při kreslení volání jsou vyloučeny z ovlivňující cíl vykreslení, protože jejich selhání testu, volání kreslení nelze rozšířit a která odpovídá důvod pro vyloučení, zobrazí se ikona vedle sebe. Důvody pro vyloučení kreslení volání připomínají důvody pro primitivní vyloučení, a jejich ikony jsou podobné.  
  
### <a name="viewing-and-debugging-shader-code"></a>Zobrazení a ladění kódu shaderu  
 Můžete zkontrolovat a ladění kódu pro vrchol, trupu, domény, geometry a pixelů shadery pomocí ovládacích prvků níže primitivní, který je spojen s shaderu.  
  
##### <a name="to-view-a-shaders-source-code"></a>Chcete-li zobrazit zdrojový kód shaderu  
  
1.  V **historie pixelů grafiky** okně Najít kreslení volání, která odpovídá shaderu chcete prozkoumat a rozbalte ho.  
  
2.  V části kreslení pomocí zavolat právě rozšířit Primitivum, které ukazuje potíže, které vás zajímají vyberte a rozbalte ho.  
  
3.  V části primitivní, co vás zajímá, pomocí následujícího odkazu název shaderu – například pomocí následujícího odkazu **obj:30 vrchol shaderu** zobrazíte zdrojový kód shaderu vrchol.  
  
    > [!TIP]
    >  Číslo objektu **obj:30**, identifikuje tento shaderu v celém rozhraní analyzátor grafiky například v okně objektu tabulky a kanál fáze.  
  
##### <a name="to-debug-a-shader"></a>K ladění shaderu  
  
1.  V **historie pixelů grafiky** okně Najít kreslení volání, která odpovídá shaderu chcete prozkoumat a rozbalte ho.  
  
2.  Potom v části volání kreslení jste právě rozšířit, vyberte na primitivní, která demonstruje problém zajímá a rozbalte ho.  
  
3.  V části primitivní, co vás zajímá, zvolte **spustit ladění**. Tento vstupní bod do výchozí nastavení ladicí program HLSL, aby první volání shaderu pro odpovídající primitivní – to znamená, první pixelu nebo vrchol, který zpracovává shaderu. Existuje pouze jeden bod. přidružené primitivní, ale existuje více než jeden vrchol shaderu volání pro řádky a trojúhelníčky.  
  
     K ladění volání shaderu vrchol pro konkrétní vrchol, rozbalte název odkazu VertexShader a vyhledejte vrchol vás zajímá, zvolte **spustit ladění** vedle sebe.  
  
### <a name="links-to-graphics-objects"></a>Odkazy na grafických objektů  
 Pochopení událostí grafiky v historie pixelů, budete pravděpodobně potřebovat informace o stavu zařízení v době události nebo o Direct3D – objekty, které odkazuje událost. Pro každou jednotlivou událost v historie pixelu **historie pixelů grafiky** poskytuje odkazy na aktuální zařízení stavu a na související objekty.  
  
## <a name="see-also"></a>Viz také  
 [Návod: Chybějící objekty z důvodu stavu zařízení](walkthrough-missing-objects-due-to-device-state.md)   
 [Návod: Ladění chyb při vykreslování způsobených stínováním](walkthrough-debugging-rendering-errors-due-to-shading.md)