---
title: Historie pixelů grafiky | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.graphics.pixelhistory
ms.assetid: 0a2cbde5-1ad9-487e-857c-a3664158c268
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 8cb1b7a869915eebc561e1baf47082dd5dbc00df
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "72735489"
---
# <a name="graphics-pixel-history"></a>Historie pixelů grafiky
Okno Historie pixelů grafiky v Analyzátor grafiky sady Visual Studio pomáhá pochopit, jakým způsobem ovlivňují události Direct3D, ke kterým dochází v rámci hry nebo aplikace, konkrétní pixel.

 Toto je okno s historií pixelů:

 ![Obrazový bod se třemi událostmi Direct3D ve své historii.](media/gfx_diag_demo_pixel_history_orientation.png "gfx_diag_demo_pixel_history_orientation")

## <a name="understanding-the-pixel-history-window"></a>Princip okna s historií pixelů
 Pomocí Historie pixelů můžete analyzovat, jak určitý pixel cíle vykreslování ovlivňuje události Direct3D během snímku. Můžete určit problém vykreslování konkrétní události Direct3D, a to i v případě, že následné události (nebo následné primitivní prvky) stejné události mění konečnou hodnotu barvy v pixelech. Například obrazový bod může být vykreslen nesprávně a následně skryt jiným, částečně transparentním pixelem tak, aby byly jejich barvy kombinovány společně v framebuffer. Tento druh problému by mohl být obtížné diagnostikovat, pokud jste k vás měli jenom konečný obsah cíle vykreslování.

 Okno Historie pixelů zobrazuje úplnou historii pixelu v průběhu vybraného snímku. **Poslední vyrovnávací paměť snímku** v horní části okna zobrazuje barvu, která je zapsána do framebuffer na konci snímku, spolu s dalšími informacemi o pixelech, jako je například rámec, ze kterého pochází, a jeho souřadnicemi obrazovky. Tato oblast také obsahuje zaškrtávací políčko pro **vykreslení alfa** . Když je toto políčko zaškrtnuté, zobrazí se **finální Barva snímku** a hodnoty mezilehlé barvy s průhledností přes šachovnicový vzor. Pokud políčko není zaškrtnuté, alfa kanál hodnot barvy se ignoruje.

 V dolní části okna se zobrazí události, které mají šanci na barvu v obrazovém bodu, spolu s **počátečními** a **koncovými** pseudomi událostmi, které reprezentují počáteční a konečné hodnoty barev v pixelech v framebuffer. Počáteční hodnota barvy je určena první událostí, která změnila barvu pixelu (obvykle `Clear` událost). Pixel má vždy tyto dvě pseudo události ve své historii, a to i v případě, že ji neovlivnila žádná jiná událost. V případě, že by jiné události mohly ovlivnit pixel, jsou zobrazeny mezi **počátečními** a **koncovými** událostmi. Události lze rozbalit a zobrazit tak jejich podrobnosti. U jednoduchých událostí, jako jsou například ty, které vymažou cíl vykreslování, je účinek události pouze hodnota barvy. Složitější události jako volání remíz vygenerují jeden nebo více primitivních elementů, které mohou přispět k barvě pixelu.

 Primitivní prvky, které byly vykresleny událostí, jsou označeny jejich primitivním typem a indexem spolu s celkovým primitivním počtem objektů. Například identifikátor, například **trojúhelník (1456) z (6214)** znamená, že primitiv odpovídá trojúhelníku 1456th v objektu, který je 6214 tvořen trojúhelníky. Vlevo od každého primitivního identifikátoru je ikona, která shrnuje efekt, který měl primitivní na pixelu. Primitivní prvky, které mají vliv na barvu v pixelech, jsou reprezentovány zaobleným obdélníkem, který je vyplněn výslednou barvou. Primitivní prvky, které jsou vyloučené z používání efektu na pixel Color, jsou reprezentovány ikonami, které označují důvod vyloučení pixelu. Tyto ikony jsou popsány v oddílu věnovaném [primitivnímu vyloučení](#exclusion) dále v tomto článku.

 Jednotlivé primitivní prvky můžete rozbalit a ověřit tak, jak byl výstup pixel shaderu sloučen s existující barvou pixelu, aby vznikla Výsledná barva. Z tohoto místa můžete také prověřit nebo ladit kód pixel shaderu, který je přidružen k primitivnímu prvku, a můžete dále rozbalovat uzel vertex shader pro prohlédnutí vstupu vertex shaderu.

### <a name="primitive-exclusion"></a><a name="exclusion"></a> Primitivní vyloučení
 Pokud je primitiva vyloučena z vlivu barvy v pixelech, může dojít k vyloučení z nejrůznějších důvodů. Každý důvod je reprezentován ikonou, která je popsána v této tabulce:

|Ikona|Důvod vyloučení|
|----------|--------------------------|
|![Ikona selhání testu hloubky](media/vsg_hist_icon_failed_depth.png "vsg_hist_icon_failed_depth")|Pixel byl vyloučen, protože neprošel testem hloubky.|
|![Ikona selhání testu vystřihovací](media/vsg_hist_icon_failed_scissor.png "vsg_hist_icon_failed_scissor")|Pixel byl vyloučen, protože selhal při testu vystřihovací.|
|![Ikona selhání testu vzorníku](media/vsg_hist_icon_failed_stencil.png "vsg_hist_icon_failed_stencil")|Pixel byl vyloučen, protože neprošel testem vzorníku.|

### <a name="draw-call-exclusion"></a>Vykreslit vyloučení volání
 Pokud jsou všechny primitivní prvky v volání remíz vyloučeny z vlivu na cíl vykreslování, protože selžou test, volání draw nelze rozbalit a ikona, která odpovídá důvodu vyloučení, se zobrazí vedle ní. Důvody pro vyloučení volání metody Draw připomínají důvody pro primitivní vyloučení a jejich ikony jsou podobné.

### <a name="viewing-and-debugging-shader-code"></a>Zobrazení a ladění kódu shaderu
 Pomocí ovládacích prvků, které jsou přidruženy k shaderu, můžete kontrolovat a ladit kód pro funkce vertex shader, trup, doména, geometrie a pixel.

##### <a name="to-view-a-shaders-source-code"></a>Zobrazení zdrojového kódu shaderu

1. V okně **Historie pixelů grafiky** vyhledejte volání draw, které odpovídá shaderu, který chcete prošetřit a rozbalit.

2. V rámci volání draw, které jste právě rozbalili, vyberte primitivum, které demonstruje problém, který vás zajímá, a rozbalte ho.

3. V rámci primitiva, na kterou vás zajímáte, použijte odkaz na název shaderu, například pomocí **vrcholu vertex shaderu Link obj: 30** zobrazte zdrojový kód vertex shader.

    > [!TIP]
    > Číslo objektu, **obj: 30**, identifikuje tento shader v celém rozhraní analyzátoru grafiky, jako je například v okně tabulky objektů a fáze zřetězení.

##### <a name="to-debug-a-shader"></a>Ladění shaderu

1. V okně **Historie pixelů grafiky** vyhledejte volání draw, které odpovídá shaderu, který chcete prošetřit a rozbalit.

2. Potom v rámci volání draw, které jste právě rozbalili, vyberte primitivní, který ukazuje problém, který vás zajímá, a rozbalte ho.

3. V rámci primitiva, na kterou vás zajímáte, vyberte **Spustit ladění**. Tento vstupní bod do ladicího programu HLSL se standardně používá jako první vyvolání shaderu pro odpovídající primitivum – to znamená první pixel nebo vrchol, který je zpracován shaderem. K primitivnímu objektu je přidružen pouze jeden pixel, ale pro čáry a trojúhelníky existuje více než jedno vyvolání funkce vertex shader.

     Chcete-li ladit vyvolání vertex shader pro konkrétní vrchol, rozbalte odkaz název VertexShader a vyhledejte vrchol, který vás zajímá, a pak zvolte možnost **Spustit ladění** vedle něj.

### <a name="links-to-graphics-objects"></a>Odkazy na grafické objekty
 Chcete-li pochopit události grafiky v historii pixelů, budete možná potřebovat informace o stavu zařízení v době události nebo o objektech Direct3D, na které se odkazuje událost. Pro každou událost v historii pixelů poskytuje **Historie pixelů grafiky** odkazy na aktuální stav zařízení a na související objekty.

## <a name="see-also"></a>Viz také
- [Návod: Chybějící objekty z důvodu stavu zařízení](walkthrough-missing-objects-due-to-device-state.md)
- [Návod: Ladění chyb vykreslování způsobených stínováním](walkthrough-debugging-rendering-errors-due-to-shading.md)