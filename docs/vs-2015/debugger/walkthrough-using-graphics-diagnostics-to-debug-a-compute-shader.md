---
title: 'Návod: Použití diagnostiky grafiky k ladění výpočetního shaderu | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 69287456-644b-4aff-bd03-b1bbb2abb82a
caps.latest.revision: 15
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 55f0b9de879011110d8df46c0e4d738265b0fa34
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51730645"
---
# <a name="walkthrough-using-graphics-diagnostics-to-debug-a-compute-shader"></a>Návod: Použití diagnostiky grafiky k ladění výpočetního shaderu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Tento návod ukazuje, jak použít nástrojů Diagnostika grafiky sady Visual Studio k vyšetření výpočetního shaderu, který generuje nesprávné výsledky.  
  
 Tento návod ilustruje tyto úkoly:  
  
-   Použití **seznam událostí grafiky** k vyhledání potenciálních zdrojů problému.  
  
-   Použití **zásobník volání událostí grafiky** k zjištění, který výpočetní shader je proveden DirectCompute `Dispatch` událostí.  
  
-   Použití **fáze zřetězení grafiky** okno a ladicího programu HLSL Zkoumejte výpočetní shader, který je zdrojem potíží.  
  
## <a name="scenario"></a>Scénář  
 V tomto scénáři jste napsali simulaci dynamiky kapalin, která používá rozhraní DirectCompute k provádění výpočetně nejnáročnějších částí aktualizace simulace. Při spuštění aplikace vykreslování datové sady a uživatelského rozhraní vypadá správně, ale simulace se nechová podle očekávání. Pomocí diagnostiky grafiky můžete zaznamenat problém do protokolu grafiky, tak, že ladíte aplikaci. Problém je v aplikace vypadá například takto:  
  
 ![Simulované fluid chová nesprávně. ](../debugger/media/gfx-diag-demo-compute-shader-fluid-problem.png "gfx_diag_demo_compute_shader_fluid_problem")  
  
 Informace o tom, jak zachytit problémy s grafikou v protokolu grafiky, naleznete v tématu [Capturing Graphics Information](../debugger/capturing-graphics-information.md).  
  
## <a name="investigation"></a>Šetření  
 Nástrojů diagnostiky grafiky můžete načíst soubor protokolu grafiky, takže si můžete prohlédnout zachycené snímky.  
  
#### <a name="to-examine-a-frame-in-a-graphics-log"></a>Přezkoumání snímku v protokolu grafiky  
  
1. V sadě Visual Studio načtěte protokol grafiky, který obsahuje rámec vykazující nesprávné výsledky simulace. Nová karta Diagnostika grafiky se zobrazí v sadě Visual Studio. V horní části této karty je výstup cíle vykreslení vybraného snímku. V dolní části je **seznam snímků**, který zobrazuje náhled každého zachyceného snímku.  
  
2. V **seznam snímků**, vyberte snímek, který ukazuje chování nesprávné simulace. I když se zobrazí chyba v kódu simulace a v kódu vykreslování nikoli, je stále nutné zvolit snímek, protože události DirectCompute jsou zachyceny na základě jednotlivých snímcích spolu s událostmi Direct3D. V tomto scénáři vypadá karta protokolu grafiky:  
  
    ![Dokumentu protokolu grafiky v aplikaci Visual Studio. ](../debugger/media/gfx-diag-demo-compute-shader-fluid-step-1.png "gfx_diag_demo_compute_shader_fluid_step_1")  
  
   Po vybrání rámce, který znázorňuje problém, můžete použít **seznam událostí grafiky** k její diagnostice. **Seznam událostí grafiky** obsahuje události pro každé volání DirectCompute a volání API rozhraní Direct3D, které bylo provedeno během aktivního rámce – například volání rozhraní API pro spuštění výpočtu na GPU nebo vykreslení datové sady nebo uživatelského rozhraní. V tomto případě nás zajímají `Dispatch` události, které představují části simulace, které běží na GPU.  
  
#### <a name="to-find-the-dispatch-event-for-the-simulation-update"></a>K nalezení události odeslání pro aktualizaci simulace  
  
1. Na **diagnostiky grafiky** nástrojů, zvolte **seznam událostí** otevřít **seznam událostí grafiky** okna.  
  
2. Zkontrolujte **seznam událostí grafiky** pro událost draw, která vykresluje datovou sadu. Abychom to usnadnili, zadejte `Draw` v **hledání** pole v pravém horním rohu **seznam událostí grafiky** okna. Vyfiltruje seznam tak, aby obsahoval pouze události, které mají "Draw" v názvech. V tomto scénáři zjistíte, že těmto událostem draw došlo k chybě:  
  
    ![Seznam událostí &#40;EL&#41; ukazuje událostem draw. ](../debugger/media/gfx-diag-demo-compute-shader-fluid-step-2.png "gfx_diag_demo_compute_shader_fluid_step_2")  
  
3. Procházet všemi událostmi draw při sledování cíle vykreslení v kartě dokumentu protokol grafiky.  
  
4. Zastavení při vykreslování cíle nejprve zobrazí vygenerovanou datovou sadu. V tomto scénáři je vykreslena datová sada v první události draw. Se zobrazí chyba simulace:  
  
    ![Událost vykreslení to nakreslete simulace datové sady. ](../debugger/media/gfx-diag-demo-compute-shader-fluid-step-3.png "gfx_diag_demo_compute_shader_fluid_step_3")  
  
5. Nyní vyhledejte **seznam událostí grafiky** pro `Dispatch` událost, která aktualizuje simulaci. Protože je pravděpodobné, že simulace je aktualizován před vykreslením, můžete se nejprve soustředit na `Dispatch` události, které nastanou před událostí draw, která vykresluje výsledky. Abychom to usnadnili, upravte **hledání** pole ke čtení `Draw;Dispatch;CSSetShader(`. Vyfiltruje seznam tak, aby obsahoval také `Dispatch` a `CSSetShader` události vedle událostí draw. V tomto scénáři zjistíte, že několik `Dispatch` události došlo před událostí draw:  
  
    ![Ukazuje EL kreslení, odesílání a CSSetShader události](../debugger/media/gfx-diag-demo-compute-shader-fluid-step-4.png "gfx_diag_demo_compute_shader_fluid_step_4")  
  
   Teď, když víte, které málo z potenciálně mnoha `Dispatch` události mohou souviset s problémem, můžete je prozkoumat podrobněji.  
  
#### <a name="to-determine-which-compute-shader-a-dispatch-call-executes"></a>Chcete-li zjistit, který výpočetní shader odeslání výpočtu provede  
  
1. Na **diagnostiky grafiky** nástrojů, zvolte **zásobník volání událostí** otevřít **zásobník volání událostí grafiky** okna.  
  
2. Počínaje událostí draw, která vykresluje výsledky simulace, přechod zpět každý pomocí jednotlivých předchozí `CSSetShader` událostí. Potom v **zásobník volání událostí grafiky** okně zvolte funkci zcela nahoře přejděte na lokalitu volání. Při volání webu můžete použít první parametr [CSSetShader](http://msdn.microsoft.com/library/ff476402.aspx) k určení, které výpočetní shadery jsou provedeny následující `Dispatch` událostí.  
  
   V tomto scénáři existují tři páry `CSSetShader` a `Dispatch` události v každém rámci. Při zpětné práci přestavuje, třetí pár představuje krok integrace (kam částice jsou skutečně přesunuty), druhá pár představuje krok vynucení výpočtu (kde se počítají síly ovlivňující jednotlivé částice) a první pár představuje Krok výpočtu hustoty.  
  
#### <a name="to-debug-the-compute-shader"></a>Chcete-li ladit výpočetní shader  
  
1. Na **diagnostiky grafiky** nástrojů, zvolte **fáze zřetězení** otevřít **fáze zřetězení grafiky** okna.  
  
2. Vyberte třetí `Dispatch` událostí (tu, která bezprostředně předchází události draw) a pak na **fáze zřetězení grafiky** okně v části **výpočetní Shader** fáze, zvolte  **Spuštění ladění**.  
  
    ![Vyberte třetí událost odeslání v EL.](../debugger/media/gfx-diag-demo-compute-shader-fluid-step-6.png "gfx_diag_demo_compute_shader_fluid_step_6")  
  
    Ladicí program HLSL je spuštěn na shader, který provádí krok integrace.  
  
3. Zkontrolujte zdrojový kód výpočetního shaderu pro krok integrace pro hledání zdroje chyby. Při použití diagnostiky grafiky k ladění kódu HLSL výpočetního shaderu, můžete krokovat kód a použít další známé ladicí nástroje, jako jsou okna kukátka. V tomto scénáři zjistíte, že existuje zřejmě není chyba ve výpočetním shaderu, který provádí krok integrace.  
  
    ![Ladění výpočetního shaderu IntegrateCS. ](../debugger/media/gfx-diag-demo-compute-shader-fluid-step-7.png "gfx_diag_demo_compute_shader_fluid_step_7")  
  
4. Chcete zastavit ladění výpočetního shaderu na **ladění** nástrojů, zvolte **Zastavit ladění** (klávesnice: Shift + F5).  
  
5. Dále vyberte druhou `Dispatch` události a spusťte ladění výpočetního shaderu, stejně jako v předchozím kroku.  
  
    ![Výběr druhá událost odeslání v EL.](../debugger/media/gfx-diag-demo-compute-shader-fluid-step-8.png "gfx_diag_demo_compute_shader_fluid_step_8")  
  
    Ladicí program HLSL je spuštěn na shader, který vypočítá síly, které působí na jednotlivé částice kapaliny.  
  
6. Zkontrolujte zdrojový kód shaderu výpočetní prostředky pro krok vynucení výpočtu. V tomto scénáři zjistíte, že zdroj chyby je zde.  
  
    ![Ladění ForceCS&#95;jednoduchý výpočetní shader. ](../debugger/media/gfx-diag-demo-compute-shader-fluid-step-9.png "gfx_diag_demo_compute_shader_fluid_step_9")  
  
   Po zjištění umístění chyby můžete zastavit ladění a upravit zdrojový kód výpočetního shaderu správně vypočítat vzdálenost mezi částicemi. V tomto scénáři stačí změnit řádek `float2 diff = N_position + P_position;` k `float2 diff = N_position - P_position;`:  
  
   ![Opravené výpočetní&#45;kód shaderu. ](../debugger/media/gfx-diag-demo-compute-shader-fluid-step-10.png "gfx_diag_demo_compute_shader_fluid_step_10")  
  
   V tomto scénáři protože jsou výpočetní shadery kompilovány za běhu, je možné pouze restartovat aplikaci po provedení změn, abyste viděli, jak ovlivňují simulaci. Nemusíte aplikaci znovu vytvořit. Při spuštění aplikace zjistíte, že simulace nyní pracuje správně.  
  
   ![Simulované fluid pracuje správně. ](../debugger/media/gfx-diag-demo-compute-shader-fluid-resolution.png "gfx_diag_demo_compute_shader_fluid_resolution")



