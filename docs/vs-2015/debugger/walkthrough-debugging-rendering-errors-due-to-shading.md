---
title: 'Návod: Ladění chyb stínováním při vykreslování | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 01875b05-cc7b-4add-afba-f2b776f86974
caps.latest.revision: 17
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5d65c3d2525533e5881b4626941e43fb302ce2aa
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51733200"
---
# <a name="walkthrough-debugging-rendering-errors-due-to-shading"></a>Návod: Ladění chyb při vykreslování způsobených stínováním
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Tento návod ukazuje, jak používat [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] diagnostiky grafiky k prozkoumání objekt, který je nesprávně barevný z důvodu chyby shaderu.  
  
 Tento návod ukazuje, jak:  
  
-   Zkontrolujte dokument grafických protokolů k identifikaci pixelů, které ukazují problém.  
  
-   Použití **historie pixelů grafiky** okno, aby lépe zkoumat stav pixelů.  
  
-   Použití **ladicí program HLSL** prozkoumat pixelů a vertex shader.  
  
## <a name="scenario"></a>Scénář  
 Nesprávný barevné zvýrazňování u objektů běžně nastane, pokud se předá vertex shader pixel shader nesprávných nebo neúplných informací.  
  
 V tomto scénáři jste nedávno přidali objekt do vaší aplikace spolu s novou vertex a pixel shaderů transformovat objekt a přiřaďte jí jedinečný vzhled. Při spuštění aplikace během testu, je objekt vykreslen v plné black. Pomocí diagnostiky grafiky můžete zaznamenat problém do protokolu grafiky, tak, že ladíte aplikaci. Problém je v aplikace vypadá například takto:  
  
 ![Objekt je vykreslen pomocí nesprávných barev. ](../debugger/media/gfx-diag-demo-render-error-shader-problem.png "gfx_diag_demo_render_error_shader_problem")  
  
## <a name="investigation"></a>Šetření  
 Pomocí nástrojů diagnostiky grafiky můžete načíst dokument grafických protokolů ke kontrole snímků, které byly zachyceny během testu.  
  
#### <a name="to-examine-a-frame-in-a-graphics-log"></a>Přezkoumání snímku v protokolu grafiky  
  
1. V [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], načtěte protokol grafiky, který obsahuje rámec vykazující chybí model. Zobrazí se nové okno dokumentu protokolu grafiky v [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. V horní části tohoto okna je výstup cíle vykreslení vybraného snímku. V dolní části je **seznam snímků**, který zobrazuje jako obrázek miniatury každého zachyceného snímku.  
  
2. V **seznam snímků**, vyberte snímek, ve kterém objekt nemá správný vzhled. Cíl vykreslování se aktualizuje tak, aby odrážely vybraného snímku. V tomto scénáři protokolu grafiky dokumentu okno vypadá nějak takto:  
  
    ![Dokumentu protokolu grafiky v aplikaci Visual Studio. ](../debugger/media/gfx-diag-demo-render-error-shader-step-1.png "gfx_diag_demo_render_error_shader_step_1")  
  
   Po vybrání rámce, který znázorňuje problém, můžete použít **historie pixelů grafiky** okna k provedení diagnostiky. **Historie pixelů grafiky** okno zobrazuje primitivních elementů, které by měly vliv na konkrétní pixel, jejich shadery, a jaké jejich dopadu na cíl vykreslování byly, v chronologickém pořadí.  
  
#### <a name="to-examine-a-pixel"></a>Prozkoumat pixel  
  
1. Otevřít **historie pixelů grafiky** okna. Na **diagnostiky grafiky** nástrojů, zvolte **historie pixelů**.  
  
2. Vyberte pixel prozkoumat. V okně dokumentu protokol grafiky vyberte jednu z pixelů na objekt, který je nesprávně barevný:  
  
    ![Výběr pixel zobrazí informace o jeho historie. ](../debugger/media/gfx-diag-demo-render-error-shader-step-2.png "gfx_diag_demo_render_error_shader_step_2")  
  
    **Historie pixelů grafiky** okno se aktualizuje tak, aby odrážely vybraný pixel. V tomto scénáři **historie pixelů grafiky** okno vypadá takto:  
  
    ![Historie pixelů se zobrazí jedna DrawIndexed událost. ](../debugger/media/gfx-diag-demo-render-error-shader-step-3.png "gfx_diag_demo_render_error_shader_step_3")  
  
    Všimněte si, že výsledek pixel shaderu úplně neprůhledné černé (0, 0, 0, 1) a že **slučovací modul výstupu** v kombinaci se **předchozí** barvu pixelu takovým způsobem, který **výsledek** je taky plně neprůhledný černý.  
  
   Po prozkoumání pixel, který je nesprávně barevný a zjistit, že výstup pixel shaderu není očekávaný barvy, můžete použít ladicí program HLSL sloužící ke zkoumání pixel shader a zjistěte, co se stalo s barva objektu. Můžete použít ladicí program HLSL a kontrolu stavu proměnných HLSL během provádění, krokovat kód HLSL a nastavit zarážky, které vám pomohou diagnostikovat problém.  
  
#### <a name="to-examine-the-pixel-shader"></a>Prozkoumat pixel shader  
  
1. Spusťte ladění pixel shader. V **historie pixelů grafiky** okno, v rámci objektu na primitivní, vedle **Pixel Shader**, zvolte **spustit ladění** tlačítko.  
  
2. V tomto scénáři protože pixel shader pouze předává barvu z vertex shader, je snadné podívejte se, že pixel shaderu není příčiny problému.  
  
3. Ukazatele myši na `input.color`. Všimněte si, že její hodnota je zcela neprůhledný černý (0, 0, 0, 1).  
  
    ![Člen "color" "vstup" je černá. ](../debugger/media/gfx-diag-demo-render-error-shader-step-5.png "gfx_diag_demo_render_error_shader_step_5")  
  
    V tomto scénáři ukáže průzkum nesprávné barva je pravděpodobně výsledkem vertex shader, který neposkytuje informace o Pravá barva pixel shader, který se má operace provést.  
  
   Jakmile potvrdíte, že vertex shader pravděpodobně není poskytuje správné informace pro pixel shader, dalším krokem je prozkoumat vertex shader.  
  
#### <a name="to-examine-the-vertex-shader"></a>Prozkoumat vertex shader  
  
1. Spusťte ladění vertex shader. V **historie pixelů grafiky** okno, v rámci objektu na primitivní, vedle **Vertex Shader**, zvolte **spustit ladění** tlačítko.  
  
2. Vyhledejte vertex shader výstup struktura – Toto je vstupem pixel shader. V tomto scénáři je název této struktury `output`. Zkoumání kódu shader vrcholu a Všimněte si, že `color` člena `output` struktury byla explicitně nastavena na plně neprůhledný černý, pravděpodobně v důsledku osoby je ladění úsilí.  
  
3. Potvrďte, že je člen barva nikdy zkopírovány z ve vstupní struktuře. Protože hodnota `output.color` je nastavena na plně neprůhledný černý těsně před `output` vrátila strukturu, je vhodné Ujistěte se, že hodnota `output` nebyla správně inicializována na předchozí řádek. Krokovat kód vertex shader, dokud se nedostanete na řádek, který nastaví `output.color` na černou, při sledování hodnotu `output.color`. Všimněte si, že hodnota `output.color` není inicializován, dokud se nenastaví na černou. Tím potvrdíte, že řádek kódu, který nastaví `output.color` do černé by měl být upravit, spíše než odstraněn.  
  
    ![Hodnota "output.color" je černá. ](../debugger/media/gfx-diag-demo-render-error-shader-step-7.png "gfx_diag_demo_render_error_shader_step_7")  
  
   Jakmile zjistíte příčinu problému vykreslování, vertex shader neposkytuje hodnota správná barva pixel shaderu, můžete použít tyto informace k vyřešení problému. V tomto scénáři můžete to napravit změnou následující kód do vertex shaderu  
  
```  
output.color = float3(0.0f, 0.0f, 0.0f);  
```  
  
 až  
  
```hlsl  
output.color = input.color;  
```  
  
 Tento kód jenom předává vrcholu barvu z objektu vrcholy bez jakýchkoli úprav – složitější vertex shader před předáním prostřednictvím změnit barvu. Vrchol Opravený kód shaderu by měl vypadat takto:  
  
 ![Kód shaderu opravený vrcholu. ](../debugger/media/gfx-diag-demo-render-error-shader-step-8.png "gfx_diag_demo_render_error_shader_step_8")  
  
 Po opravě kód její opětovné sestavení a spuštění aplikace znovu a zjistit, že je vyřešen problém vykreslování.  
  
 ![Objekt je vykreslen pomocí správné barvy. ](../debugger/media/gfx-diag-demo-render-error-shader-resolution.png "gfx_diag_demo_render_error_shader_resolution")



