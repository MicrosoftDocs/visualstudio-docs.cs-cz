---
title: Ladicí program shaderu HLSL | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.graphics.shaderviewer
ms.assetid: 4ccec541-3c49-42bd-972a-686eb3a88fbc
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 27db26a732ec53b81aed4807f4aec546e1bc7f1a
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49825715"
---
# <a name="hlsl-shader-debugger"></a>Ladicí program shaderu HLSL
Ladicí program HLSL v analyzátoru grafiky sady Visual Studio vám pomůže porozumět fungování kódu shaderu HLSL aplikace skutečný podmínek.  
  
 Toto je ladicí program HLSL:  
  
 ![Ladění HLSL pomocí sledování a okna zásobníku volání. ](media/gfx_diag_demo_hlsl_debugger_orientation.png "gfx_diag_demo_hlsl_debugger_orientation")  
  
## <a name="understanding-the-hlsl-debugger"></a>Principy ladicího programu HLSL  
 Ladicí program HLSL vám pomůže objasnit problémy, které vzniknou v kódu shaderu. Ladění kódu HLSL v [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] podobá ladění kódu, která je napsána v jiných jazycích, například C++, C# nebo Visual Basic. Můžete kontrolovat obsah proměnných, nastavit body přerušení, krokovat kód a procházet nahoru zásobníkem volání podobně jako při ladění jiných jazyků.  
  
 Ale protože GPU dosáhnout vysoké výkonu spuštěním kódu shaderu na stovkách vláken současně, ladicí program HLSL je navržen pro práci s další analyzátoru grafiky sady nástrojů zobrazíte všechny tyto informace způsobem, který pomáhá pochopit ho. Analyzátor grafiky znovu vytvoří zachycené snímky pomocí informací zaznamenaných v protokolu grafiky; ladicí program HLSL nesleduje spouštění GPU v reálném čase při spouštění kódu shaderu. Protože protokol grafiky obsahuje dostatek informací pro opětovné vytvoření libovolné části výstupu a protože analýzu grafiky poskytuje nástroje, které vám mohou pomoci přesně určit přesný pixel a událost, pokud dojde k chybě, ladicí program HLSL má pouze simulovat přesný proces shaderu vlákno, které vás zajímají. To znamená, že práce shaderu může být simulována procesorem, ve kterém jsou vnitřní mechanismy plně zobrazeny. Tímto ladicí program HLSL dosahuje možností ladění na úrovni procesoru.  
  
 Ladicí program HLSL je však aktuálně omezen následujícími způsoby:  
  
- Ladicí program HLSL nepodporuje edit-and-continue, ale můžete provádět změny vašeho shadery a pak znovu vygenerovat snímek pro zobrazení výsledků.  
  
- Není možné současně ladit aplikaci a její kód shaderu. Můžete však mezi nimi přepínat.  
  
- K oknu kukátka můžete přidat proměnné a registry, ale výrazy nejsou podporovány.  
  
  Nicméně ladicí program HLSL poskytuje lepší ladění více odpovídající CPU, které by jinak nebylo možné.  
  
## <a name="hlsl-shader-edit--apply"></a>Použít & Upravit HLSL Shader  
 Ladicí program shaderu HLSL nepodporuje Upravit & pokračovat stejným způsobem, který provede ladicí program procesoru, protože spouštěcí model GPU neumožňuje shaderu stavu vrátit. Místo toho podporuje ladicí program HLSL & použít, což vám umožní upravit HLSL zdrojové soubory a klikněte na tlačítko Upravit **použít** se znova vygenerovat snímek projevily provedené změny. Kód shaderu. změny se ukládají do samostatného souboru zachovat integritu vašeho projektu původní zdrojový soubor HLSL, ale jakmile budete spokojeni se změnami můžete **zkopírovat do...**  kopírování změny do svého projektu. Pomocí této funkce můžete rychle iterovat kód shaderu, který obsahuje chyby a eliminovat opětovné nákladnou sestavení a zachycení kroky z vaší HLSL ladění pracovního postupu.  
  
## <a name="hlsl-disassembly"></a>Převod do strojového jazyka HLSL  
 Ladicí program shaderu HLSL poskytuje seznam sestavení shaderu HLSL napravo od výpis HLSL zdrojového kódu.  
  
## <a name="debugging-hlsl-code"></a>Ladění kódu HLSL  
 Se dá dostat ladicího programu HLSL z okna fáze zřetězení nebo z historie pixelů.  
  
#### <a name="to-start-the-hlsl-debugger-from-the-graphics-pipeline-stages-window"></a>Spuštění ladicího programu HLSL z okna Fáze zřetězení grafiky  
  
1.  V **fáze zřetězení grafiky** okně vyhledejte fázi spojenou se shaderem, který chcete ladit.  
  
2.  Pod názvem fáze zřetězení zvolte **spustit ladění**, která se zobrazí jako malá zelená šipka.  
  
    > [!NOTE]
    >  Tento vstupní bod do ladicího programu HLSL ladí pouze první vlákno shaderu pro odpovídající fázi, tedy první vrchol nebo pixel, který je zpracován. Historie pixelů můžete použít pro přístup k jiným vláknům těchto fází shaderu.  
  
#### <a name="to-start-the-hlsl-debugger-from-the-graphics-pixel-history"></a>Spuštění ladicího programu HLSL z okna Historie pixelů grafiky  
  
1. V **historie pixelů grafiky** okna rozbalte volání draw spojené se shaderem, který chcete ladit. Každé volání draw může odpovídat více primitivům.  
  
2. V podrobnostech volání draw rozbalte primitivum, jehož výsledný příspěvek barvy naznačuje chybu v kódu shaderu. Pokud na chyby poukazuje více primitiv, vyberte první primitivum, aby nedošlo ke hromadění chyb, které mohou ztížit diagnostiku problému.  
  
3. V podrobnostech primitiva zvolte, jestli se má ladit **Vertex Shader** nebo **Pixel Shader**. Pokud máte podezření, že pixel shader je správný, ale generuje nesprávný příspěvek barvy, protože vertex shader mu předává nesprávné konstanty, proveďte ladění funkce vertex shader. V opačném případě proveďte ladění funkce pixel shader.  
  
    Napravo od vybraného shaderu zvolte **spustit ladění**, která se zobrazí jako malá zelená šipka.  
  
   > [!NOTE]
   >  Tento vstupní bod do ladicího programu HLSL ladí buď vlákno funkce pixel shader, které odpovídá zvolenému volání draw, primitivu a pixelu, nebo vlákna funkce vertex shader, jejichž výsledky jsou interpolovány voláním draw, primitivem a pixelem, které jste vybrali. U funkcí vertex shader můžete dále upřesnit vstupní bod do určitého vrcholu rozbalením podrobností funkce vertex shader.  
  
   Příklady o tom, jak použít ladicí program HLSL k ladění chyb shaderu naleznete v tématu [příklady](graphics-diagnostics-examples.md) nebo v návodech v části Viz také.  
  
## <a name="see-also"></a>Viz také  
 [Návod: Chybějící objekty z důvodu použití funkce Vertex Shading](walkthrough-missing-objects-due-to-vertex-shading.md)   
 [Návod: Ladění chyb stínováním při vykreslování](walkthrough-debugging-rendering-errors-due-to-shading.md)   
 [Návod: Použití diagnostiky grafiky k ladění výpočetního shaderu](walkthrough-using-graphics-diagnostics-to-debug-a-compute-shader.md)