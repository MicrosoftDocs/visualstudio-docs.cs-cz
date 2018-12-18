---
title: Diagnostika grafiky | Dokumentace Microsoftu
ms.custom: seodec18
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.graphics
ms.assetid: fa69c550-62a7-41b5-bb1f-7eb04af1a6e8
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: e40a8ce0f2785aa606922d3f9c49f3aad48f7591
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/07/2018
ms.locfileid: "53058614"
---
# <a name="visual-studio-graphics-diagnostics"></a>Diagnostika grafiky sady Visual Studio
Visual Studio*diagnostiky grafiky* je sada nástrojů pro nahrávání a pak analýzu problémů vykreslování a výkon v aplikacích rozhraní Direct3D. Diagnostika grafiky je použít v aplikacích, které běží místně v počítači Windows v emulátoru zařízení Windows nebo na vzdálený počítač nebo zařízení.  

 Pracovní postup diagnostiky grafiky začíná zachytáváním záznam o tom, jak vaše aplikace používá rozhraní Direct3D – live během jejího běhu – tak, aby jeho chování mohou být analyzovány okamžitě, sdílet nebo uložit pro pozdější. Relace zachycení lze spustit a řídit ručně ze sady Visual Studio nebo pomocí nástroje příkazového řádku pro zachytávání **dxcap.exe**. Relace zachycení se navíc dají inicializovat a řídit prostřednictvím kódu programu pomocí zachycení diagnostiky grafiky rozhraní API.  

 Po zachycení relace byla zaznamenána jeho obsah je možné přehrát pomocí sady Visual Studio *analyzátoru grafiky sady* kdykoli znovu vytvořit zachycené snímky pomocí přesně stejné prostředky a vykreslování příkazy aplikace používá. Potom pomocí nástrojů v okně Analyer grafiky, některé z zachycené snímky mohou být analyzovány podrobně. Tyto nástroje slouží ke kontrole jakékoli volání rozhraní API Direct3D, prostředků, objekt stavu kanálu, fázi zřetězení nebo dokonce celou historii všech pixel v zachyceném snímku. Pomocí těchto nástrojů ve vzájemné součinnosti problém vykreslování se dají zkoumat intuitivně, počínaje jak se zobrazuje v zachyceném snímku a jeho hlavní příčinou aplikace zdrojového kódu, shadery nebo grafické prostředky podrobnostem.  

 Chcete-li diagnostikovat problémy s výkonem, mohou být analyzovány zachyceného snímku s použitím *analýza snímků* nástroj. Tento nástroj vám umožní prozkoumat potenciální optimalizací výkonu tak, že automaticky mění způsob, jak aplikace používá rozhraní Direct3D a srovnávací testy všechny varianty pro vás. V minulosti, možná jste udělali a ručně jednoduše benchmarked změny tohoto typu se najít ty, které provedli rozdíl na více instancí. S analýzu snímků stačí provést změny, které už znáte, se vyplatí.  

 Diagnostika grafiky pomáhá aplikacím Direct3D bohatou grafikou vypadat a spustit co nejlépe.  

 I nadále [přehled](overview-of-visual-studio-graphics-diagnostics.md) Další informace o co Diagnostika grafiky sady Visual Studio nabízí.  

## <a name="in-this-section"></a>V tomto oddílu  
 [Přehled](overview-of-visual-studio-graphics-diagnostics.md)  
 Představuje pracovní postup diagnostiky grafiky a nástroje.  

 [Začínáme](getting-started-with-visual-studio-graphics-diagnostics.md)  
 V této části se dozvíte, jak nainstalovat Diagnostika grafiky sady Visual Studio a jak můžete začít s vaší aplikací Direct3D použití diagnostiky grafiky.  

 [Zaznamenání grafických informací](capturing-graphics-information.md)  
 Chcete-li diagnostiku grafiky použít k prozkoumání problému vykreslování ve vaší aplikaci, první záznam informace o tom, jak aplikace používá rozhraní DirectX. Během relace nahrávání jako vaše aplikace běží za normálních okolností je *zachycení* (to znamená, vyberte) rámce, které vás zajímají. Zachycení obsahují podrobné informace o způsobu vykreslení rámce. Součástí zaznamenaných informací můžete uložit jako graphics log dokument dále prozkoumat nebo sdílet s ostatními členy týmu.  

 [Využití GPU](gpu-usage.md)  
 K použití diagnostiky grafiky, chcete-li Profilovat aplikaci, použijte nástroj využití GPU. Využití GPU je možné společně s další nástroje pro profilaci, jako je například využití procesoru, korelovat CPU a GPU aktivita, která může přispět k problémy s výkonem ve vaší aplikaci.  

 [Dokument grafických protokolů](graphics-log-document.md)  
 Spustit posouzení protokol grafiky nahrané, použijete pro výběr zachyceného snímku okno dokumentu protokolu grafiky – nebo dokonce konkrétní pixel – tak, aby můžete prozkoumat podrobněji *události* (to znamená, rozhraní DirectX volání rozhraní API), které by ovlivnily ho .  

 [Analýza snímků](graphics-frame-analysis.md)  
 Po vybrání rámce, použijete k prozkoumání a vyladit výkon vykreslování analýza grafických snímků.  

 [Seznam událostí](graphics-event-list.md)  
 Po vybrání rámce, můžete použít **seznam událostí grafiky** prozkoumat jeho události a určit, zda se vztahují k problému vykreslování.  

 [Stav](graphics-state.md)  
 Okno stavu vám pomůže pochopit stav grafiky, která je aktivní v okamžiku aktuální událost.  

 [Fáze zřetězení](graphics-pipeline-stages.md)  
 V **fáze zřetězení grafiky** okně byste prozkoumat, jak aktuálně vybrané události je zpracována každé fáze zřetězení grafiky, aby mohli identifikovat, kde se nejprve zobrazí problému vykreslování. Zkoumání fáze zřetězení je zvláště užitečné, pokud objekt nezobrazí z důvodu nesprávné transformace, nebo pokud jeden z těchto fází vytvoří výstup, který neodpovídá co do další fáze očekává, že.  

 [Zásobník volání událostí](graphics-event-call-stack.md)  
 Můžete použít **zásobník volání událostí grafiky** prozkoumat zásobníku volání aktuálně vybrané události, takže můžete přejít na kód aplikace, které se vztahují k problému vykreslování.  

 [Historie pixelu](graphics-pixel-history.md)  
 S použitím **historie pixelů grafiky** okno analyzovat, jak je aktuálně vybraný pixel ovlivněna události, které k nim, identifikujete událost nebo kombinaci těchto událostí, které způsobí určité druhy problémů s vykreslováním. Historie pixelů je zvláště užitečný, pokud objekt je vykreslen nesprávně, protože výstup pixel shaderu je buď nesprávný nebo byl sloučen nesprávně s Snímková vyrovnávací paměť, nebo objekt nemá dokonce zdát, že vzhledem k tomu, že byly vyřazeny jeho pixelů dřív, než dorazí vyrovnávací paměť snímku.  

 [Tabulka objektů](graphics-object-table.md)  
 Můžete použít **Graphics Object Table** prozkoumat vlastnosti a obsah konkrétní objekty Direct3D a zdroje, které platí pro aktuálně vybrané události. Tabulka objektů můžete určit, která je aktivní během události kontextu zařízení grafiky a zkontrolovat obsah grafické prostředky jako vyrovnávací paměť konstant, vyrovnávací paměti vrcholů a textury.  

 [Ladicí program HLSL](hlsl-shader-debugger.md)  
 Prozkoumat, jak kód shaderu pro aktuálně vybrané události a grafickém kanálu fáze se chová, můžete použít **ladicí program HLSL** krokovat kód, zkontrolovat obsah proměnné a provádět další typické úlohy ladění. Ladicí program HLSL můžete také použít k prozkoumání výpočetní kód shaderu, bez ohledu na to, jestli výsledky jsou dále zpracovávat v zřetězení grafiky nebo jsou jen pro čtení zpět o vaši aplikaci.  

 [Nástroj příkazového řádku pro zachytávání](command-line-capture-tool.md)  
 Použijte nástroj příkazového řádku pro zachytávání k rychlému zachytávání a přehrávání grafické informace bez použití sady Visual Studio nebo zachytávání prostřednictvím kódu programu. Konkrétně můžete použít nástroj příkazového řádku pro zachytávání pro službu automation, nebo v testovacím prostředí.  

 [Příklady](graphics-diagnostics-examples.md)  
 Několik příklady ukazují, jak pomocí nástrojů diagnostiky grafiky společně diagnostikovat různé druhy problémů s vykreslováním.  

## <a name="related-sections"></a>Související oddíly  

| Název | Popis |
| - | - |
| [Prohlídka funkcí ladicího programu](../debugging-in-visual-studio.md) | Představuje funkce ladění v [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. |
| [Grafika DirectX a hraní her](http://go.microsoft.com/fwlink/?LinkId=256498) | Obsahuje články, které popisují technologií grafiky DirectX. |

