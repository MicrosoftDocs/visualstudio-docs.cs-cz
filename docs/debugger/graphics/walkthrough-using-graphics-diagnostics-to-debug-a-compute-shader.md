---
title: Ladění výpočetního shaderu pomocí diagnostiky grafiky
description: Použijte příklad řešení potíží s výpočetním shaderem. Uvidíte, jak používat seznam událostí grafiky, zásobník volání událostí grafiky a fáze zřetězení grafiky.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 69287456-644b-4aff-bd03-b1bbb2abb82a
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 939b1906a32c48aa1ad32f2fb03372a74afc43ec
ms.sourcegitcommit: 40d758f779d42c66cb02ae7face8a62763a8662b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/14/2020
ms.locfileid: "97398711"
---
# <a name="walkthrough-using-graphics-diagnostics-to-debug-a-compute-shader"></a>Návod: Použití diagnostiky grafiky k ladění výpočetního shaderu
Tento návod ukazuje, jak použít nástroje sady Visual Studio Diagnostika grafiky k prozkoumání výpočetního shaderu, který generuje nesprávné výsledky.

 Tento návod ilustruje tyto úlohy:

- K vyhledání potenciálních zdrojů problému použijte **seznam událostí grafiky** .

- Použití **zásobníku volání událostí grafiky** k určení, který výpočetní shader je proveden `Dispatch` událostí DirectCompute.

- Pomocí okna **fáze zřetězení grafiky** a ladicího programu HLSL prověřte výpočetní shader, který je zdrojem problému.

## <a name="scenario"></a>Scénář
 V tomto scénáři jste napsali simulaci kapalinového dynamiky, která využívá DirectCompute k provádění většiny částí aktualizace simulace náročné na výpočetní výkon. Když je aplikace spuštěna, vykreslování datové sady a uživatelského rozhraní vypadá správně, ale simulace se nechová podle očekávání. Pomocí Diagnostika grafiky můžete zachytit problém do protokolu grafiky, abyste mohli aplikaci ladit. Problém v této aplikaci vypadá následovně:

 ![Simulovaná kapalina se chová nesprávně.](media/gfx_diag_demo_compute_shader_fluid_problem.png "gfx_diag_demo_compute_shader_fluid_problem")

 Informace o tom, jak zachytit problémy s grafikou v protokolu grafiky, najdete v tématu [zachycení grafických informací](capturing-graphics-information.md).

## <a name="investigation"></a>Šetření
 Pomocí nástrojů Diagnostika grafiky můžete načíst soubor protokolu grafiky, abyste mohli zkontrolovat zachycené snímky.

#### <a name="to-examine-a-frame-in-a-graphics-log"></a>Prohlédnutí snímku v protokolu grafiky

1. V aplikaci Visual Studio načtěte protokol grafiky, který obsahuje rámec, který vykazuje nesprávné výsledky simulace. V aplikaci Visual Studio se zobrazí nová karta Diagnostika grafiky. V horní části této karty je výstup cíle vykreslování vybraného snímku. V dolní části je **seznam rámců**, který zobrazuje miniaturu každého zachyceného snímku.

2. V **seznamu snímků** vyberte rámec, který ukazuje nesprávné chování simulace. I když se zdá, že chyba je v kódu simulace, a ne kód vykreslování, je stále nutné zvolit rámec, protože DirectCompute události jsou zachyceny na základě rámců a společně s událostmi Direct3D. V tomto scénáři vypadá karta protokol grafiky takto:

    ![Dokument protokolu grafiky v aplikaci Visual Studio.](media/gfx_diag_demo_compute_shader_fluid_step_1.png "gfx_diag_demo_compute_shader_fluid_step_1")

   Po výběru rámce, který demonstruje problém, můžete k jeho diagnostice použít **seznam událostí grafiky** . **Seznam událostí grafiky** obsahuje událost pro každé volání DirectCompute a volání rozhraní Direct3D API, které bylo provedeno během aktivního rámce – například volání rozhraní API pro spuštění výpočtu na GPU nebo pro vykreslení datové sady nebo uživatelského rozhraní. V tomto případě zajímáme `Dispatch` události, které představují části simulace, které jsou spuštěny na GPU.

#### <a name="to-find-the-dispatch-event-for-the-simulation-update"></a>Vyhledání odesílací události pro aktualizaci simulace

1. Na panelu nástrojů **Diagnostika grafiky** vyberte **seznam událostí** a otevřete tak okno **seznam událostí grafiky** .

2. Zkontrolujte **seznam událostí grafiky** pro událost Draw, která vykresluje datovou sadu. Pokud to chcete usnadnit, zadejte `Draw` do **vyhledávacího** pole v pravém horním rohu okna **seznam událostí grafiky** . Tím se seznam vyfiltruje tak, aby obsahoval jenom události, které mají v názvech "Draw". V tomto scénáři zjistíte, že došlo k těmto událostem Draw:

    ![Seznam událostí &#40;EL&#41; zobrazuje události Draw.](media/gfx_diag_demo_compute_shader_fluid_step_2.png "gfx_diag_demo_compute_shader_fluid_step_2")

3. Procházejte všemi událostmi vykreslování a sledujte cíl vykreslování na kartě dokumentu protokolu grafiky.

4. Zastavit, pokud cíl vykreslování nejprve zobrazí vykreslenou datovou sadu. V tomto scénáři je datová sada vykreslena v první události Draw. Zobrazí se chyba v simulaci:

    ![Tato událost vykreslování vykresluje datovou sadu simulace.](media/gfx_diag_demo_compute_shader_fluid_step_3.png "gfx_diag_demo_compute_shader_fluid_step_3")

5. Nyní zkontrolujte **seznam událostí grafiky** pro `Dispatch` událost, která aktualizuje simulaci. Vzhledem k tomu, že je pravděpodobně před vykreslením simulace aktualizována, můžete nejprve soustředit na `Dispatch` události, ke kterým dojde před událostí Draw, která vykresluje výsledky. Chcete-li to usnadnit, upravte **vyhledávací** pole pro čtení `Draw;Dispatch;CSSetShader(` . Tím se seznam vyfiltruje tak, aby také obsahoval `Dispatch` události a, a `CSSetShader` navíc události Draw. V tomto scénáři zjistíte, že `Dispatch` před událostí Draw došlo k několika událostem:

    ![EL zobrazuje události vykreslování, odeslání a CSSetShader](media/gfx_diag_demo_compute_shader_fluid_step_4.png "gfx_diag_demo_compute_shader_fluid_step_4")

   Když teď víte, které z potenciálně mnoha `Dispatch` událostí by mohly odpovídat problému, můžete je podrobněji prostudovat.

#### <a name="to-determine-which-compute-shader-a-dispatch-call-executes"></a>Určení, které výpočetní shader a které vykoná volání expedice

1. Na panelu nástrojů **Diagnostika grafiky** vyberte možnost **zásobník volání událostí** a otevřete tak okno **zásobníku volání událostí grafiky** .

2. Počínaje událostí Draw, která vykresluje výsledky simulace, se přesunou zpět přes každou předchozí `CSSetShader` událost. Pak v okně **zásobník volání událostí grafiky** zvolte funkci nejvyšší úrovně, která umožňuje přejít na web volání. Na webu volání můžete použít první parametr volání funkce [CSSetShader](/windows/desktop/api/d3d11/nf-d3d11-id3d11devicecontext-cssetshader) k určení, který výpočetní shader je proveden další `Dispatch` událostí.

   V tomto scénáři jsou `CSSetShader` v každém snímku tři páry a `Dispatch` události. V opačném případě třetí pár představuje krok integrace (kde jsou skutečně přesunuty tekuté částice), druhý pár představuje krok vynucení výpočtu (kde jsou vypočítány síly ovlivňující jednotlivé částice) a první pár představuje krok výpočtu hustoty.

#### <a name="to-debug-the-compute-shader"></a>Ladění výpočetního shaderu

1. Na panelu nástrojů **Diagnostika grafiky** výběrem možnosti **fáze zřetězení** otevřete okno **fáze zřetězení grafiky** .

2. Vyberte třetí `Dispatch` událost (ta, která bezprostředně předchází události Draw) a pak v okně **fáze zřetězení grafiky** pod fází **výpočetní shader** vyberte **Spustit ladění**.

    ![Výběr třetí odesílací události v EL.](media/gfx_diag_demo_compute_shader_fluid_step_6.png "gfx_diag_demo_compute_shader_fluid_step_6")

    Ladicí program HLSL je spuštěn na shaderu, který provádí krok integrace.

3. Projděte si zdrojový kód COMPUTE-shader pro krok integrace a vyhledejte zdroj chyby. Když použijete Diagnostika grafiky k ladění kódu HLSL COMPUTE-shader, můžete krokovat kód a použít jiné známé ladicí nástroje, jako jsou například okna kukátka. V tomto scénáři zjistíte, že se v výpočetním shaderu, který provádí krok integrace, nezobrazí chyba.

    ![Ladění výpočetního shaderu IntegrateCS.](media/gfx_diag_demo_compute_shader_fluid_step_7.png "gfx_diag_demo_compute_shader_fluid_step_7")

4. Chcete-li zastavit ladění výpočetního shaderu, na panelu nástrojů **ladění** vyberte možnost **Zastavit ladění** (klávesnice: Shift + F5).

5. Dále vyberte druhou `Dispatch` událost a spusťte ladění výpočetního shaderu stejným způsobem jako v předchozím kroku.

    ![Výběr druhé odesílací události v EL.](media/gfx_diag_demo_compute_shader_fluid_step_8.png "gfx_diag_demo_compute_shader_fluid_step_8")

    Ladicí program HLSL je spuštěn na shaderu, který počítá síly, které působí na každé částice tekutiny.

6. Projděte si zdrojový kód výpočetního shaderu pro krok vynucení výpočtu. V tomto scénáři zjistíte, že zdroj chyby je zde.

    ![Ladění ForceCS&#95;jednoduchého výpočetního shaderu.](media/gfx_diag_demo_compute_shader_fluid_step_9.png "gfx_diag_demo_compute_shader_fluid_step_9")

   Po určení umístění chyby můžete zastavit ladění a upravit zdrojový kód výpočetního shaderu, aby se správně počítala vzdálenost mezi interakcemi částic. V tomto scénáři stačí řádek změnit `float2 diff = N_position + P_position;` na `float2 diff = N_position - P_position;` :

   ![Opravený výpočetní&#45;kód shaderu.](media/gfx_diag_demo_compute_shader_fluid_step_10.png "gfx_diag_demo_compute_shader_fluid_step_10")

   V tomto scénáři vzhledem k tomu, že výpočetní shadery jsou kompilovány za běhu, můžete aplikaci restartovat pouze poté, co provedete změny ke sledování vlivu na simulaci. Nemusíte znovu sestavovat aplikaci. Když aplikaci spustíte, zjistíte, že se simulace teď chová správně.

   ![Simulovaná kapalina se chová správně.](media/gfx_diag_demo_compute_shader_fluid_resolution.png "gfx_diag_demo_compute_shader_fluid_resolution")