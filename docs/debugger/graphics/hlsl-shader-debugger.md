---
title: Ladicí program shaderu HLSL | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.graphics.shaderviewer
ms.assetid: 4ccec541-3c49-42bd-972a-686eb3a88fbc
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 164c404f3bce6b8216092635e3489843039fb1eb
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/22/2019
ms.locfileid: "72735305"
---
# <a name="hlsl-shader-debugger"></a>Ladicí program shaderu HLSL
Ladicí program HLSL v Analyzátor grafiky sady Visual Studio pomáhá pochopit, jak váš kód shaderu HLSL funguje za reálných podmínek vaší aplikace.

 Toto je ladicí program HLSL:

 ![Ladění HLSL pomocí oken sledování a volání zásobníků.](media/gfx_diag_demo_hlsl_debugger_orientation.png "gfx_diag_demo_hlsl_debugger_orientation")

## <a name="understanding-the-hlsl-debugger"></a>Principy ladicího programu HLSL
 Ladicí program HLSL vám pomůže objasnit problémy, které vzniknou v kódu shaderu. Ladění kódu HLSL v [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] podobá ladění kódu, který je napsán v jiných jazycích, například C++ C#, nebo Visual Basic. Můžete kontrolovat obsah proměnných, nastavit body přerušení, krokovat kód a procházet nahoru zásobníkem volání podobně jako při ladění jiných jazyků.

 Nicméně vzhledem k tomu, že GPU dosahují vysokého výkonu spuštěním kódu shaderu na stovkách vláken současně, je ladicí program HLSL navržený tak, aby společně s dalšími nástroji analyzátoru grafiky dokázal prezentovat všechny tyto informace způsobem, který vám pomůže vydávat smysl její. Analyzátor grafiky znovu vytvoří zachycené snímky pomocí informací zaznamenaných v protokolu grafiky. ladicí program HLSL nemonitoruje spouštění GPU v reálném čase při spuštění kódu shaderu. Vzhledem k tomu, že protokol grafiky obsahuje dostatek informací pro opětovné vytvoření jakékoliv části výstupu a protože analýza grafiky poskytuje nástroje, které vám pomohou určit přesný pixel a událost, při které dojde k chybě, ladicí program HLSL musí simulovat přesný shader. vlákno, které vás zajímá. To znamená, že práce shaderu může být simulována procesorem, ve kterém jsou vnitřní mechanismy plně zobrazeny. Tímto ladicí program HLSL dosahuje možností ladění na úrovni procesoru.

 Ladicí program HLSL je však aktuálně omezen následujícími způsoby:

- Ladicí program HLSL nepodporuje funkci upravit a pokračovat, ale můžete provést změny v shaderech a pak znovu vygenerovat rámec pro zobrazení výsledků.

- Není možné současně ladit aplikaci a její kód shaderu. Můžete však mezi nimi přepínat.

- K oknu kukátka můžete přidat proměnné a registry, ale výrazy nejsou podporovány.

  Nicméně ladicí program HLSL poskytuje lepší ladění více odpovídající CPU, které by jinak nebylo možné.

## <a name="hlsl-shader-edit--apply"></a>Použít & pro úpravy shaderu HLSL
 Ladicí program shaderu HLSL nepodporuje úpravu & pokračování stejným způsobem jako ladicí program procesoru, protože model spuštění GPU nepovoluje, aby byl stav shaderu vrácen zpět. Místo toho ladicí program HLSL podporuje úpravu & použít, což umožňuje upravit zdrojové soubory HLSL a pak vybrat **použít** pro opětovné vygenerování rámce, aby se zobrazil účinek změn. Upravený kód shaderu je uložený v samostatném souboru, aby se zachovala integrita původního zdrojového souboru HLSL vašeho projektu, ale když jste spokojeni s vašimi změnami, můžete zvolit **Kopírovat do...** a zkopírovat změny do svého projektu. Pomocí této funkce můžete rychle iterovat na kódu shaderu, který obsahuje chyby, a eliminovat nákladný postup opětovného sestavování a zachycení kroků z pracovního postupu ladění HLSL.

## <a name="hlsl-disassembly"></a>HLSL zpětný překlad
 Ladicí program shaderu HLSL poskytuje seznam sestavení HLSL shaderu napravo od výpisu zdrojového kódu HLSL.

## <a name="debugging-hlsl-code"></a>Ladění kódu HLSL
 K ladicímu programu HLSL se dostanete z oken fáze zřetězení nebo Historie pixelů.

#### <a name="to-start-the-hlsl-debugger-from-the-graphics-pipeline-stages-window"></a>Spuštění ladicího programu HLSL z okna Fáze zřetězení grafiky

1. V okně **fáze zřetězení grafiky** vyhledejte fázi kanálu, která je přidružená k shaderu, který chcete ladit.

2. Pod nadpisem fáze zřetězení vyberte možnost **Spustit ladění**, která se zobrazí jako malá zelená šipka.

    > [!NOTE]
    > Tento vstupní bod do ladicího programu HLSL ladí pouze první vlákno shaderu pro odpovídající fázi, tedy první vrchol nebo pixel, který je zpracován. K přístupu k ostatním vláknům těchto fází shaderu můžete použít historii pixelů.

#### <a name="to-start-the-hlsl-debugger-from-the-graphics-pixel-history"></a>Spuštění ladicího programu HLSL z okna Historie pixelů grafiky

1. V okně **Historie pixelů grafiky** rozbalte volání vykreslování, které je přidruženo k shaderu, který chcete ladit. Každé volání draw může odpovídat více primitivům.

2. V podrobnostech volání draw rozbalte primitivum, jehož výsledný příspěvek barvy naznačuje chybu v kódu shaderu. Pokud na chyby poukazuje více primitiv, vyberte první primitivum, aby nedošlo ke hromadění chyb, které mohou ztížit diagnostiku problému.

3. V podrobnostech primitivního rozhraní vyberte, zda chcete ladit **vertex shader** nebo **pixel shader**. Pokud máte podezření, že pixel shader je správný, ale generuje nesprávný příspěvek barvy, protože vertex shader mu předává nesprávné konstanty, proveďte ladění funkce vertex shader. V opačném případě proveďte ladění funkce pixel shader.

    Napravo od zvoleného shaderu vyberte možnost **Spustit ladění**, která se zobrazí jako malá zelená šipka.

   > [!NOTE]
   > Tento vstupní bod do ladicího programu HLSL ladí buď vlákno funkce pixel shader, které odpovídá zvolenému volání draw, primitivu a pixelu, nebo vlákna funkce vertex shader, jejichž výsledky jsou interpolovány voláním draw, primitivem a pixelem, které jste vybrali. U funkcí vertex shader můžete dále upřesnit vstupní bod do určitého vrcholu rozbalením podrobností funkce vertex shader.

   Příklady použití ladicího programu HLSL k ladění chyb shaderu naleznete v tématu [Příklady](graphics-diagnostics-examples.md) nebo návody, na které se odkazuje v části Viz také.

## <a name="see-also"></a>Viz také:
- [Návod: Chybějící objekty z důvodu použití funkce vertex shading](walkthrough-missing-objects-due-to-vertex-shading.md)
- [Návod: Ladění chyb při vykreslování způsobených stínováním](walkthrough-debugging-rendering-errors-due-to-shading.md)
- [Návod: Použití diagnostiky grafiky k ladění výpočetního shaderu](walkthrough-using-graphics-diagnostics-to-debug-a-compute-shader.md)