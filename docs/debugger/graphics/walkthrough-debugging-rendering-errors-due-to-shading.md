---
title: 'Návod: ladění chyb vykreslování z důvodu stínování | Microsoft Docs'
description: Postupujte podle šetření, které najde chybu shaderu. Zobrazuje použití sady Visual Studio Diagnostika grafiky, včetně historie pixelů grafiky a HLSL ladicího programu.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 01875b05-cc7b-4add-afba-f2b776f86974
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 218b263d7e971a0d2bdaa72020bb7cb58c31e000
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/19/2021
ms.locfileid: "112387083"
---
# <a name="walkthrough-debugging-rendering-errors-due-to-shading"></a>Návod: Ladění chyb vykreslování způsobených stínováním
Tento návod ukazuje, jak použít [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Diagnostika grafiky k prozkoumání nesprávně barevného objektu z důvodu chyby shaderu.

 Tento návod ukazuje, jak:

- Projděte si dokument protokolu grafiky a Identifikujte pixely, které ukazují problém.

- Použijte okno **Historie pixelů grafiky** a podrobněji prověřte stav pixelů.

- Pomocí **ladicího programu HLSL** prověřte shadery v pixelech a vrcholu.

## <a name="scenario"></a>Scenario
 Nesprávné zbarvení objektů obvykle probíhá, když vertex shader předává nesprávné nebo neúplné informace o pixel shaderu.

 V tomto scénáři jste nedávno přidali objekt do aplikace. Přidali jste také nové funkce vertex a pixel shaderů pro transformaci objektu a přidělení jedinečného vzhledu. Když aplikaci spustíte během testu, objekt se vykreslí jako sytá černá. Pomocí Diagnostika grafiky zachytíte problém do protokolu grafiky, abyste mohli aplikaci ladit. Problém vypadá jako tento obrázek v aplikaci:

 ![Objekt je vykreslen s nesprávnými barvami.](media/gfx_diag_demo_render_error_shader_problem.png "gfx_diag_demo_render_error_shader_problem")

## <a name="investigation"></a>Šetření
 Pomocí nástrojů Diagnostika grafiky můžete načíst dokument protokolu grafiky pro kontrolu rámců, které byly zachyceny během testu.

#### <a name="to-examine-a-frame-in-a-graphics-log"></a>Prohlédnutí snímku v protokolu grafiky

1. V nástroji [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] načtěte protokol grafiky, který má rámec, který zobrazuje chybějící model. V nástroji se zobrazí nový okno dokumentu s grafickým protokolem [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] . V horní části tohoto okna je výstupem cíle vykreslování vybraného snímku. V dolní části je **seznam rámců**, který zobrazuje jednotlivé zachycené rámce jako obrázek miniatury.

2. V **seznamu snímků** vyberte rámec, ve kterém nemá objekt správný vzhled. Cíl vykreslování se aktualizuje tak, aby odrážel vybraný snímek. V tomto scénáři vypadá okno dokumentu protokolu grafiky jako v tomto obrázku:

    ![Dokument protokolu grafiky v aplikaci Visual Studio.](media/gfx_diag_demo_render_error_shader_step_1.png "gfx_diag_demo_render_error_shader_step_1")

   Po výběru rámce, který demonstruje problém, můžete použít okno **Historie pixelů grafiky** a diagnostikovat ho. Okno **Historie pixelů grafiky** zobrazuje primitivní prvky, které by mohly mít vliv na určitý pixel, jejich shadery a jejich účinky na cíl vykreslování, v chronologickém pořadí.

#### <a name="to-examine-a-pixel"></a>Kontrola pixelu

1. Otevřete okno **Historie pixelů grafiky** . Na panelu nástrojů **Diagnostika grafiky** vyberte položku **Historie pixelů**.

2. Vyberte pixel, který chcete prošetřit. V okně dokument protokolu grafiky vyberte jeden z obrazových bodů na objektu, který je nesprávně barevný:

    ![Výběr pixelu zobrazí informace o jeho historii.](media/gfx_diag_demo_render_error_shader_step_2.png "gfx_diag_demo_render_error_shader_step_2")

    Okno **Historie pixelů grafiky** se aktualizuje tak, aby odráželo vybraný pixel. V tomto scénáři okno **Historie pixelů grafiky** vypadá takto:

    ![Historie pixelů zobrazuje jednu událost DrawIndexed.](media/gfx_diag_demo_render_error_shader_step_3.png "gfx_diag_demo_render_error_shader_step_3")

    Všimněte si, že výsledek funkce pixel shader je zcela neprůhledný (0, 0, 0, 1) a že **se tato kombinovaná** publikace spojila s **předchozí** barvou obrazového bodu v takovém případě, že je **výsledkem** také plně Neprůhledná černá.

   Po prohlédnutí nesprávného barevného pixelu a zjištění, že výstup pixel shaderu není očekávanou barvou, můžete pomocí ladicího programu HLSL prozkoumat pixel shader a zjistit, co se stalo s barvou objektu. Můžete použít ladicí program HLSL k prohlédnutí stavu proměnných HLSL během provádění, krokovat kód HLSL a nastavit zarážky, které vám pomohou diagnostikovat problém.

#### <a name="to-examine-the-pixel-shader"></a>Kontrola funkce pixel shader

1. Spustí ladění pixel shaderu. V okně **Historie pixelů grafiky** v části primitiva objektu vedle **pixel shaderu** klikněte na tlačítko **Spustit ladění** .

2. V tomto scénáři, protože pixel shader pouze předává barvu z vrcholu shaderu, je snadné sledovat, že pixel shader není zdrojem problému.

3. Umístěte ukazatel myši na `input.color` . Všimněte si, že jeho hodnota je plně Neprůhledná černá (0, 0, 0, 1).

    ![Člen "Color" vstupu "Input" je černý.](media/gfx_diag_demo_render_error_shader_step_5.png "gfx_diag_demo_render_error_shader_step_5")

    V tomto scénáři zkoumání odhalí, že nesprávná barva je pravděpodobně výsledkem vertex shaderu, který neposkytuje správné informace o barvě pro funkci pixel shaderu, která má být použita.

   Jakmile zjistíte, že funkce vertex shader pravděpodobně neposkytuje správné informace shaderu pixel shader, je dalším krokem kontrola vrcholu shaderu.

#### <a name="to-examine-the-vertex-shader"></a>Kontrola vrcholu shaderu

1. Spusťte ladění vertex shaderu. V okně **Historie pixelů grafiky** v části primitiva objektu vedle možnosti **vertex shader** klikněte na tlačítko **Spustit ladění** .

2. Vyhledání výstupní struktury funkce vertex shader – jedná se o vstup pro pixel shader. V tomto scénáři je název této struktury `output` . Prohlédněte si kód vertex shader a Všimněte si, že `color` člen `output` struktury byl explicitně nastaven na plně neprůhledný černý, například v důsledku úsilí někoho o ladění.

3. Ověřte, že se člen barvy nikdy nezkopíroval ze vstupní struktury. Vzhledem k tomu, že hodnota `output.color` je nastavena na plně Neprůhledná černá těsně před `output` vrácením struktury, je vhodné se ujistit, že hodnota `output` nebyla správně inicializována na předchozím řádku. Projděte si kód vrcholu shaderu, dokud se nedostanete k čáře, která je nastavena `output.color` na černou a sledujte hodnotu `output.color` . Všimněte si, že hodnota `output.color` není inicializována, dokud není nastavena na černou. Tím se potvrdí, že řádek kódu, který je nastaven `output.color` na černou, by měl být změněn místo odstranění.

    ![Hodnota "Output. Color" je černá.](media/gfx_diag_demo_render_error_shader_step_7.png "gfx_diag_demo_render_error_shader_step_7")

   Po zjištění, že příčinou problému vykreslování je, že funkce vertex shader neposkytuje správnou hodnotu barvy shaderu pixel, můžete tyto informace použít k vyřešení problému. V tomto scénáři je můžete opravit změnou následujícího kódu v vertex shaderu.

```hlsl
output.color = float3(0.0f, 0.0f, 0.0f);
```

 na

```hlsl
output.color = input.color;
```

 Tento kód pouze předává barvu vrcholu z nezměněných vrcholů objektu – složitější funkce vertex shader mohou změnit barvu před jejich předáním pomocí. Opravený kód vertex shader by měl vypadat takto:

 ![Opravený kód vertex shaderu](media/gfx_diag_demo_render_error_shader_step_8.png "gfx_diag_demo_render_error_shader_step_8")

 Po opravě kódu ho znovu sestavte a znovu spusťte aplikaci, abyste zjistili, že problém vykreslování je vyřešen.

 ![Objekt je vykreslen se správnými barvami.](media/gfx_diag_demo_render_error_shader_resolution.png "gfx_diag_demo_render_error_shader_resolution")
