---
title: Historie pixelů grafiky | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.graphics.pixelhistory
ms.assetid: 0a2cbde5-1ad9-487e-857c-a3664158c268
caps.latest.revision: 17
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 20b33c987cf7e2b1ab57160b4f4917246d9030b6
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51733153"
---
# <a name="graphics-pixel-history"></a>Historie pixelů grafiky
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Okno historie pixelů grafiky v analyzátoru grafiky sady Visual Studio vám pomůže pochopit, jak je ovlivněna konkrétní pixel událostmi rozhraní Direct3D, ke kterým dochází při snímku hře nebo aplikaci.  
  
 Toto je v okně historie pixelů:  
  
 ![Pixel se tři události rozhraní Direct3D v historii. ](../debugger/media/gfx-diag-demo-pixel-history-orientation.png "gfx_diag_demo_pixel_history_orientation")  
  
## <a name="understanding-the-pixel-history-window"></a>Principy okna Historie pixelů  
 S využitím historie pixelů, můžete analyzovat, jak konkrétní pixel cíle vykreslování je ovlivněna událostmi rozhraní Direct3D průběhu rámce. Můžete identifikovat problém vykreslování na určité události rozhraní Direct3D, i když následující události – nebo dalších primitivních elementů v stejnou událost – budou stále měnit hodnotu konečnou barvu pixelu na. Pixel například může být vykreslen nesprávně a potom zakryto jiný, poloprůhledného pixel, tak, aby jejich barvy jsou prolnuty společně v framebuffer. Tento druh problému by bylo obtížné zjistit, jestli máte pouze konečný obsah cíl vykreslování a provede vás.  
  
 V okně historie pixelů se zobrazí veškeré jeho historie pixelů v průběhu vybraného snímku. **Finální vyrovnávací paměť snímku** v horní části okna se zobrazí barva, která jsou zapsána do framebuffer na konci rámce, společně s další informace o pixelu, jako je například rámce, který pochází z a jeho obrazovka souřadnice. Tato oblast také obsahuje **vykreslit alfa** zaškrtávací políčko. Když toto políčko zaškrtnuto, **konečné Snímková vyrovnávací paměť** barvu a prostřední barvu hodnoty jsou zobrazeny s transparentnosti přes šachovnicový vzor. Pokud políčko není zaškrtnuto, alfa kanál barevných se ignoruje.  
  
 Dolní části okna se zobrazí události, které využili příležitost dobře se ovlivní barvu pixelu, spolu s **počáteční** a **konečné** pseudo události, které představují hodnoty počáteční a konečné barvy pixel v framebuffer. Počáteční barva hodnotu Určuje první událost, která se změnila barvu pixelu (obvykle `Clear` událostí). Pixel vždy má tyto dvě pseudo události v historii, i v případě, že to vliv na žádné události. Při další události využili příležitost dobře se ovlivnit je pixel, se zobrazí mezi **počáteční** a **konečné** události. Události lze rozbalit a zobrazit jeho podrobnosti. Pro jednoduché události jako je ta, která vymažou cíl vykreslování efekt události je právě hodnotu barvy. Složitější události, například volání draw generovat jednu nebo více primitiv, které může přispět k barvu pixelu.  
  
 Primitiva, které byly vykreslené události jsou označeny jejich primitivní typ a index, spolu s celkový počtem primitivní pro objekt. Například identifikátor jako **trojúhelník (1456) (6214)** znamená, že odpovídá 1456th trojúhelník v objektu, který se skládá z 6214 trojúhelníky primitivní vlastnost. Nalevo od každého primitivního identifikátor je ikona, která shrnuje vliv primitivní vlastnost na obrazového bodu. Primitiva, které ovlivní barvu pixelu jsou reprezentovány zakulacený obdélník, který je vyplněn barvou výsledek. Primitiva, které jsou vyloučené z efektu barvu pixelu jsou reprezentované pomocí ikony označující důvod, je pixel byl vyloučen. Tyto ikony jsou popsány v části [primitivní vyloučení](../debugger/graphics-pixel-history.md#exclusion) dále v tomto článku.  
  
 Můžete rozbalit každý primitivní prozkoumat, jak se výstup pixel shaderu sloučeny s existující barva pixel a vytvoření výsledku barev. Odsud můžete také prozkoumat nebo ladit kód pixel shader, který je spojen s primitivní vlastnost, a můžete dále rozšířit uzlu shader vrcholu prozkoumat shader vrcholu vstup.  
  
###  <a name="exclusion"></a> Primitivní vyloučení  
 Pokud jednoduchého typu je vyloučen z by to ovlivnilo barva pixel, vyloučení může dojít k různých důvodů. Každý důvod je reprezentován ikonou, která je popsaná v této tabulce:  
  
|Ikona|Důvod pro vyloučení|  
|----------|--------------------------|  
|![Hloubka ikona selhání testu. ](../debugger/media/vsg-hist-icon-failed-depth.png "vsg_hist_icon_failed_depth")|Je pixel byl vyloučen, protože se neprošel testem hloubky.|  
|![Vystřihovací ikona selhání testu. ](../debugger/media/vsg-hist-icon-failed-scissor.png "vsg_hist_icon_failed_scissor")|Je pixel byl vyloučen, protože se neprošel testem vystřihování.|  
|![Ikona selhání testu šablony hloubky. ](../debugger/media/vsg-hist-icon-failed-stencil.png "vsg_hist_icon_failed_stencil")|Je pixel byl vyloučen, protože se neprošel testem vzorníku.|  
  
### <a name="draw-call-exclusion"></a>Vyloučení volání příkazu pro vykreslení  
 Pokud všechny primitiv při kreslení volání jsou vyloučeny z by to ovlivnilo cíle vykreslování, protože jejich selhání testu, pak volání draw nelze rozšířit a zobrazí se vedle sebe ikonu, která odpovídá důvod pro vyloučení. Důvody pro vyloučení volání draw se podobají důvody pro primitivní vyloučení a jejich ikony jsou podobné.  
  
### <a name="viewing-and-debugging-shader-code"></a>Zobrazení a ladění kódu shaderu  
 Můžete prozkoumat a ladění kódu pro vrchol, trupu, domény, geometrie a pixel shadery pomocí ovládacích prvků dole primitivní hodnota, která je přidružená k shaderu.  
  
##### <a name="to-view-a-shaders-source-code"></a>Chcete-li zobrazit zdrojový kód shaderu  
  
1.  V **historie pixelů grafiky** okně vyhledejte volání draw, která odpovídá shaderu chcete prozkoumat a rozbalte ho.  
  
2.  V části draw vám stačí rozbalit, vyberte jednoduchého typu, který ukazuje problém, který vás zajímá a rozbalte ho.  
  
3.  V rámci primitivních vás zajímá, pomocí následujícího odkazu název shaderu – například pomocí následujícího odkazu **Vertex Shader obj:30** Chcete-li zobrazit zdrojový kód shaderu vrcholu.  
  
    > [!TIP]
    >  Číslo objektu **obj:30**, identifikuje tento shader v celém rozhraní analyzátoru grafiky sady například v okně fáze tabulky a kanál objektu.  
  
##### <a name="to-debug-a-shader"></a>K ladění shaderu  
  
1.  V **historie pixelů grafiky** okně vyhledejte volání draw, která odpovídá shaderu chcete prozkoumat a rozbalte ho.  
  
2.  Potom podle volání vykreslování můžete jenom rozšířit, vyberte jednoduchého typu, který ukazuje problém zajímá a rozbalte ho.  
  
3.  V části Primitivum, které vás zajímá, vyberte **spustit ladění**. Tento vstupní bod do výchozí nastavení ladicího programu HLSL, aby před prvním vyvoláním služby shaderu pro odpovídající základní – to znamená, první pixelů nebo vrchol, který je zpracován shaderu. Existuje pouze jeden pixel přidružené Primitivum, ale existuje více než jeden vertex shader volání pro řádky a trojúhelníky.  
  
     Ladění vyvolání vertex shader pro konkrétní vrchol, rozbalte název odkazu VertexShader a vyhledejte vrchol, který vás zajímá, klikněte na tlačítko **spustit ladění** vedle sebe.  
  
### <a name="links-to-graphics-objects"></a>Odkazy na grafických objektů  
 Informace o tom událostí grafiky v historie pixelů, budete pravděpodobně potřebovat informace o stavu zařízení v době události a objekty Direct3D, na které odkazuje událost. Pro každou jednotlivou událost v historii pixelů **historie pixelů grafiky** obsahuje odkazy na aktuální zařízení, stavu a o souvisejících objektů.  
  
## <a name="see-also"></a>Viz také  
 [Návod: Chybějící objekty z důvodu stavu zařízení](../debugger/walkthrough-missing-objects-due-to-device-state.md)   
 [Návod: Ladění chyb při vykreslování způsobených stínováním](../debugger/walkthrough-debugging-rendering-errors-due-to-shading.md)



