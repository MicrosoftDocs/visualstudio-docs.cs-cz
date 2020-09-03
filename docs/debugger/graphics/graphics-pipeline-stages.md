---
title: Fáze zřetězení grafiky | Microsoft Docs
ms.date: 02/09/2017
ms.topic: conceptual
f1_keywords:
- vs.graphics.pipeline
ms.assetid: 2bf5c12e-2a00-401c-8163-4e373d08ad3f
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 1d697313289bbf00234764cc04603b7bc256f174
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "72735471"
---
# <a name="graphics-pipeline-stages"></a>Fáze zřetězení grafiky
Okno fáze zřetězení grafiky vám pomůže pochopit, jak je jednotlivé volání vykreslování transformované všemi fázemi grafického kanálu Direct3D.

 Toto je okno fáze zřetězení:

 ![3D objekt projde fáze zřetězení.](media/gfx_diag_demo_pipeline_stages_orientation.png)

## <a name="understanding-the-graphics-pipeline-stages-window"></a>Principy okna fáze zřetězení grafiky
 Okno fáze zřetězení vizualizuje výsledek každé fáze grafických kanálů samostatně pro každé volání remíz. Obvykle jsou výsledky fází uprostřed kanálu skryté, takže je obtížné zjistit, kde byl problém s vykreslováním spuštěn. Když vizualizujete každou fázi samostatně, okno fáze zřetězení usnadňuje zobrazení místa, kde se problém spouští – například můžete snadno zobrazit, kdy se neočekávaně fáze vrcholu shaderu způsobí, že se objekt nakreslí mimo obrazovku.

 Po zjištění fáze, ve které dojde k problému, můžete pomocí dalších nástrojů analyzátoru grafiky zjistit, jak se data interpretují nebo transformují. Problémy s vykreslováním, které se zobrazují ve fázích zřetězení, jsou často v souvislosti s nesprávným popisovačem formátu vrcholů, laděnými programy shaderů nebo chybou nakonfigurovaným stavem.

### <a name="links-to-related-graphics-objects"></a>Odkazy na související grafické objekty
 Někdy je potřeba další kontext, který určuje, proč volání vykreslování komunikuje určitým způsobem s grafickým kanálem. Aby bylo snazší tento další kontext najít, okno fáze zřetězení grafiky odkazuje na jeden nebo více objektů, které poskytují další kontext související s tím, co se děje v grafickém kanálu.

- V Direct3D 12 je tento objekt obvykle seznam příkazů.

- V Direct3D 11 je tento objekt obvykle kontextem grafického zařízení.

  Tyto odkazy jsou součástí aktuálního podpisu události grafiky, který je umístěný v levém horním rohu okna fáze zřetězení grafiky. Pomocí kteréhokoli z těchto odkazů prověřte další podrobnosti o objektu.

### <a name="viewing-and-debugging-shader-code"></a>Zobrazení a ladění kódu shaderu
 Pomocí ovládacích prvků v dolní části příslušných fází v okně fáze zřetězení můžete prozkoumávat a ladit kód pro funkce vertex shader, trup, doména, geometrie a pixel.

#### <a name="to-view-a-shaders-source-code"></a>Zobrazení zdrojového kódu shaderu

- V okně **fáze zřetězení grafiky** vyhledejte fázi shaderu, která odpovídá shaderu, který chcete prošetřit. Pak pod odkazem na obrázek verze Preview použijte odkaz na název fáze shaderu, například pomocí **vrcholu vertex shaderu Link obj: 30** zobrazte zdrojový kód vertex shader.

    > [!TIP]
    > Číslo objektu, **obj: 30**, identifikuje tento shader v celém rozhraní analyzátoru grafiky, jako je například v okně tabulka objektů a Historie pixelů.

#### <a name="to-debug-a-shader"></a>Ladění shaderu

- V okně **fáze zřetězení grafiky** vyhledejte fázi shaderu, která odpovídá shaderu, který chcete ladit. Potom pod obrázkem náhledu zvolte možnost **Spustit ladění**. Tento vstupní bod do ladicího programu HLSL se nastaví jako první vyvolání shaderu pro odpovídající fázi, tj. první pixel, vrchol nebo primitivum, která je zpracována shaderem během tohoto volání metody Draw. K vyvolání tohoto shaderu pro určitý pixel nebo vrchol se dá dostat prostřednictvím **Historie pixelů grafiky**.

### <a name="the-pipeline-stages"></a>Fáze zřetězení
 Okno fáze zřetězení vizualizuje pouze fáze kanálu, které byly aktivní během volání metody Draw. Každá fáze kanálu grafiky transformuje vstup z předchozí fáze a předá výsledek do další fáze. První fáze – vstupní Assembler – přebírá data indexu a vrcholu z vaší aplikace jako svůj vstup. poslední fáze – sloučení výstupu – sloučí nově vykreslené pixely spolu s aktuálním obsahem framebuffer nebo cíle vykreslování jako svůj výstup, aby se vytvořil finální obrázek, který vidíte na obrazovce.

> [!NOTE]
> V okně **fáze zřetězení grafiky** nejsou podporované výpočetní shadery.

 **Vstupní Assembler** Vstupní Assembler přečte data indexu a vrcholu určená vaší aplikací a sestaví ho pro grafický hardware.

 V okně fáze zřetězení je výstup vstupního assembleru vizuálně vizuální jako model drátěného modelu. Pokud se chcete podívat na výsledek, vyberte **vstupní Assembler** v okně **fáze zřetězení grafiky** , abyste zobrazili sestavené vrcholy v plném 3D pomocí editoru modelů.

> [!NOTE]
> Pokud se `POSITION` sémantika nevyskytuje ve vstupním výstupu assembleru, ve **vstupní fázi assembleru** se nic nezobrazuje.

 **Vertex shader** Fáze vertex shader zpracovává vrcholy, obvykle provádí operace jako transformace, změny vzhledu a osvětlení. Funkce vertex shadery vytvoří stejný počet vrcholů, které jako vstup přebírají.

 V okně fáze zřetězení se výstup vrcholu shaderu vizuálně rozpravuje jako rastrový obrázek drátěného modelu. Pokud se chcete podívat na výsledek, vyberte v oknech **fáze zřetězení grafiky** možnost **vertex shader** , abyste zobrazili zpracované vrcholy v editoru imagí.

> [!NOTE]
> Pokud `POSITION` `SV_POSITION` ve výstupu vertex shader neexistují sémantika nebo, pak se ve fázi **vertex shader** nezobrazí žádné výsledky.

 **Shader trupu** (pouze Direct3D 11 a Direct3D 12) fáze shaderu trupu zpracovává řídicí body, které definují plochu s nižším pořadím, jako je například čára, trojúhelník nebo quad. Jako výstup vytvoří fázi geometrie s vyšším pořadím a konstanty opravy, které jsou předány do fáze teselace pevné funkce.

 Fáze shaderu trupu není v okně fáze zřetězení vizuálů.

 **Fáze teselace** (jenom Direct3D 11 a Direct3D 12) fáze teselace je pevná funkce (Neprogramovatelná) hardwarová jednotka, která předzpracovává doménu představovanou výstupem shaderu trupu. Jako výstup vytvoří vzorek vzorkování domény a sadu menších primitivních prvků – body, čáry, trojúhelníky, které spojují tyto ukázky.

 Fáze teselace není v okně fáze zřetězení vizuálů.

 **Domain shader** (pouze Direct3D 11 a Direct3D 12) fáze funkce domény zpracovává z shaderu trupu více než, tedy faktory teselace z fáze teselace. Faktory teselace můžou zahrnovat vstupní faktory teselace a také výstupní faktory. Jako výstup vypočítá pozice vrcholu bodu na výstupní opravě podle faktorů teselace.

 V okně fáze zřetězení se nezobrazuje fáze prostředí domény.

 **Shader geometrie** Fáze geometrie shaderu zpracovává celé primitivní prvky – body, čáry nebo trojúhelníky, spolu s nepovinnými daty vrcholů pro sousední primitivní prvky. Na rozdíl od vertex shaderu mohou geometrie shadery způsobovat více nebo méně primitivních primitiv, než jako vstup.

 V okně fáze zřetězení se výstup geometrie shaderu vizuálně rozpravuje jako rastrový obrázek drátěného modelu. Chcete-li se podívat na výsledek, vyberte v okně **fáze zřetězení grafiky** možnost **geometrie shader** a zobrazte zpracovávané primitivy v editoru obrázků.

 **Fáze výstupu streamu** Fáze výstupu streamu může zachytit transformované primitivní prvky před rastrování a zapsat je do paměti. odtud se data dají znovu rozšiřovat jako vstup do předchozích fází grafického kanálu nebo si ho můžou přečíst i procesor.

 Fáze výstupu streamu není v okně fáze zřetězení vizuálů.

 **Fáze rastrového** rámečku Fáze rastrového obrázku je pevná funkce (Neprogramovatelná) hardwarová jednotka, která převádí vektorové primitivy – body, čáry, trojúhelníky – na rastrový obrázek pomocí převodu prověřování na řádku. Při rastrových vrcholech se transformují do homogenního prostoru pro Klipart a oříznuté. Jako výstup jsou namapovány funkce pixel shadery a atributy na vrchol jsou interpolované napříč primitivy a připravené pro funkci pixel shader.

 V okně fáze zřetězení se nevizuální fáze Rastrováním nezobrazuje.

 **Pixel shader** Fáze funkce pixel shader zpracovává rastrované primitivy společně s interpolovaná data vrcholů za účelem generování hodnot na pixel, jako je barva a hloubka.

 V okně fáze zřetězení je výstup pixel shaderu vizuální jako rastrový obrázek s plnou barvou. Chcete-li se podívat na výsledek, vyberte **pixel shader** v okně **fáze zřetězení grafiky** k zobrazení zpracovaných primitivních prvků v editoru obrázků.

 **Sloučení výstupu** Výstupní fáze fúze kombinuje účinek nově vykreslených pixelů spolu s existujícím obsahem jejich odpovídajících vyrovnávacích pamětí – barvy, hloubky a vzorníku, aby se vytvořily nové hodnoty v těchto vyrovnávacích pamětech.

 Výstup fúze v okně fáze zřetězení je vizuální jako rastrový obrázek s plnou barvou. Pokud se chcete podívat na výsledky, vyberte sloučení **výstupu** v okně **fáze zřetězení grafiky** , abyste viděli sloučenou framebuffer.

### <a name="vertex-and-geometry-shader-preview"></a>Vrchol a geometrie shader Preview
 Když vyberete fázi vrcholu nebo shaderu geometrie v okně **fáze zřetězení** , můžete zobrazit vstupy a výstupy z shaderu na panelu níže.  Tady najdete podrobnosti o seznamu vrcholů dodaných shaderům po jejich sestavení pomocí vstupní fáze assembleru.

 ![Prohlížeč vstupní vyrovnávací paměti fáze vertex shaderu](media/gfx_diag_vertex_shader_inbuffers.png)

 Chcete-li zobrazit výsledek fáze vertex shader, klikněte na miniaturu fáze vrcholu shaderu, abyste zobrazili rastrový obrázek v plné velikosti a rastrovaný drátěný model po jeho transformaci pomocí vrcholu shaderu.

 ![Náhled výsledku fáze vertex shaderu](media/gfx_diag_vertex_shader_preview.png)

## <a name="see-also"></a>Viz také
- [Návod: Chybějící objekty z důvodu použití vertex shaderu](walkthrough-missing-objects-due-to-vertex-shading.md)
- [Návod: Ladění chyb vykreslování způsobených stínováním](walkthrough-debugging-rendering-errors-due-to-shading.md)