---
title: Diagnostika grafiky sady Visual Studio | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.graphics
ms.assetid: fa69c550-62a7-41b5-bb1f-7eb04af1a6e8
caps.latest.revision: 42
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 29ca6b2110038a427c76622d50f769321cda9ff9
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2019
ms.locfileid: "74296916"
---
# <a name="visual-studio-graphics-diagnostics"></a>Diagnostika grafiky sady Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio*Diagnostika grafiky* je sada nástrojů pro zaznamenávání a analýzu problémů s výkonem a výkonem v aplikacích Direct3D. Diagnostika grafiky je použít v aplikacích, které běží místně v počítači Windows v emulátoru zařízení Windows nebo na vzdálený počítač nebo zařízení.  
  
 Pracovní postup diagnostiky grafiky začíná zachytáváním záznam o tom, jak vaše aplikace používá rozhraní Direct3D – live během jejího běhu – tak, aby jeho chování mohou být analyzovány okamžitě, sdílet nebo uložit pro pozdější. Relace zachycení lze spustit a řídit ručně ze sady Visual Studio nebo pomocí nástroje pro zachycení příkazového řádku **DXCap. exe**. Relace zachycení se taky dají iniciovat a řídit programově pomocí rozhraní API pro zachycení Diagnostika grafiky.  
  
 Po nahrání jeho obsahu je možné ho pomocí *analyzátoru grafiky* sady Visual Studio kdykoli přehrát a znovu vytvořit zachycené snímky pomocí stejných prostředků a příkazů pro vykreslování, které aplikace používala. Pak můžete pomocí nástrojů, které jsou k dispozici v okně analyzátor grafiky, analyzovat všechny zachycené snímky podrobněji. Tyto nástroje slouží ke kontrole jakékoli volání rozhraní API Direct3D, prostředků, objekt stavu kanálu, fázi zřetězení nebo dokonce celou historii všech pixel v zachyceném snímku. Pomocí těchto nástrojů ve vzájemné součinnosti problém vykreslování se dají zkoumat intuitivně, počínaje jak se zobrazuje v zachyceném snímku a jeho hlavní příčinou aplikace zdrojového kódu, shadery nebo grafické prostředky podrobnostem.  
  
 Chcete-li diagnostikovat problémy s výkonem, lze zachycený snímek analyzovat pomocí nástroje pro *analýzu snímků* . Tento nástroj vám umožní prozkoumat potenciální optimalizací výkonu tak, že automaticky mění způsob, jak aplikace používá rozhraní Direct3D a srovnávací testy všechny varianty pro vás. V minulosti, možná jste udělali a ručně jednoduše benchmarked změny tohoto typu se najít ty, které provedli rozdíl na více instancí. S analýzu snímků stačí provést změny, které už znáte, se vyplatí.  
  
 Diagnostika grafiky pomáhá aplikacím Direct3D bohatou grafikou vypadat a spustit co nejlépe.  
  
 Další informace o tom, co Visual Studio Diagnostika grafiky nabízí, najdete dál v [přehledu](../debugger/overview-of-visual-studio-graphics-diagnostics.md) .  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Přehled](../debugger/overview-of-visual-studio-graphics-diagnostics.md)  
 Představuje pracovní postup diagnostiky grafiky a nástroje.  
  
 [Začínáme](../debugger/getting-started-with-visual-studio-graphics-diagnostics.md)  
 V této části se dozvíte, jak nainstalovat Diagnostika grafiky sady Visual Studio a jak můžete začít s vaší aplikací Direct3D použití diagnostiky grafiky.  
  
 [Zaznamenání grafických informací](../debugger/capturing-graphics-information.md)  
 Chcete-li diagnostiku grafiky použít k prozkoumání problému vykreslování ve vaší aplikaci, první záznam informace o tom, jak aplikace používá rozhraní DirectX. Během relace nahrávání se při normálním spuštění aplikace *zachytí* (to znamená výběr) rámců, které vás zajímají. Zachycení obsahují podrobné informace o způsobu vykreslení rámce. Součástí zaznamenaných informací můžete uložit jako graphics log dokument dále prozkoumat nebo sdílet s ostatními členy týmu.  
  
 [Využití GPU](../debugger/gpu-usage.md)  
 K použití diagnostiky grafiky, chcete-li Profilovat aplikaci, použijte nástroj využití GPU. Využití GPU je možné společně s další nástroje pro profilaci, jako je například využití procesoru, korelovat CPU a GPU aktivita, která může přispět k problémy s výkonem ve vaší aplikaci.  
  
 [Dokument grafických protokolů](../debugger/graphics-log-document.md)  
 Chcete-li spustit kontrolu zaznamenaného protokolu grafiky, použijte okno dokument protokolu grafiky k výběru zachyceného snímku nebo dokonce konkrétního pixelu, aby bylo možné podrobněji prostudovat *události* (tj. volání rozhraní API DirectX), která to ovlivňují.  
  
 [Analýza snímků](../debugger/graphics-frame-analysis.md)  
 Po vybrání rámce, použijete k prozkoumání a vyladit výkon vykreslování analýza grafických snímků.  
  
 [Seznam událostí](../debugger/graphics-event-list.md)  
 Po výběru rámce použijete **seznam událostí grafiky** k prohlédnutí jeho událostí, abyste zjistili, zda souvisejí s problémem vykreslování.  
  
 [State](../debugger/graphics-state.md)  
 Okno stavu vám pomůže pochopit stav grafiky, která je aktivní v okamžiku aktuální událost.  
  
 [Fáze zřetězení](../debugger/graphics-pipeline-stages.md)  
 V okně **fáze zřetězení grafiky** můžete prozkoumat, jak je aktuálně vybraná událost zpracována každou fází grafického kanálu, abyste mohli zjistit, kde se problém s vykreslováním zobrazuje poprvé. Zkoumání fáze zřetězení je zvláště užitečné, pokud objekt nezobrazí z důvodu nesprávné transformace, nebo pokud jeden z těchto fází vytvoří výstup, který neodpovídá co do další fáze očekává, že.  
  
 [Zásobník volání událostí](../debugger/graphics-event-call-stack.md)  
 **Zásobník volání událostí grafiky** slouží k prohlédnutí zásobníku volání aktuálně vybrané události, abyste mohli přejít ke kódu aplikace, který se vztahuje k problému vykreslování.  
  
 [Historie pixelu](../debugger/graphics-pixel-history.md)  
 Pomocí okna **Historie pixelů grafiky** můžete analyzovat, jak je aktuálně vybraný pixel ovlivněn událostmi, které ho ovlivnily, a můžete určit událost nebo kombinaci událostí, které způsobují určitý druh problémů s vykreslováním. Historie pixelů je zvláště užitečný, pokud objekt je vykreslen nesprávně, protože výstup pixel shaderu je buď nesprávný nebo byl sloučen nesprávně s Snímková vyrovnávací paměť, nebo objekt nemá dokonce zdát, že vzhledem k tomu, že byly vyřazeny jeho pixelů dřív, než dorazí vyrovnávací paměť snímku.  
  
 [Tabulka objektů](../debugger/graphics-object-table.md)  
 **Tabulka grafických objektů** slouží k prohlédnutí vlastností a obsahu konkrétních objektů a prostředků Direct3D, které jsou platné pro aktuálně vybranou událost. Tabulka objektů můžete určit, která je aktivní během události kontextu zařízení grafiky a zkontrolovat obsah grafické prostředky jako vyrovnávací paměť konstant, vyrovnávací paměti vrcholů a textury.  
  
 [Ladicí program HLSL](../debugger/hlsl-shader-debugger.md)  
 Chcete-li se podívat, jak se kód shaderu pro aktuálně vybranou událost a vrstvu grafických kanálů chová, použijte **ladicí program HLSL** pro procházení kódu, Projděte si obsah proměnných a proveďte jiné typické úlohy ladění. Ladicí program HLSL můžete také použít k prozkoumání výpočetní kód shaderu, bez ohledu na to, jestli výsledky jsou dále zpracovávat v zřetězení grafiky nebo jsou jen pro čtení zpět o vaši aplikaci.  
  
 [Nástroj příkazového řádku pro zachytávání](../debugger/command-line-capture-tool.md)  
 Použijte nástroj příkazového řádku pro zachytávání k rychlému zachytávání a přehrávání grafické informace bez použití sady Visual Studio nebo zachytávání prostřednictvím kódu programu. Konkrétně můžete použít nástroj příkazového řádku pro zachytávání pro službu automation, nebo v testovacím prostředí.  
  
 [Příklady](../debugger/graphics-diagnostics-examples.md)  
 Několik příklady ukazují, jak pomocí nástrojů diagnostiky grafiky společně diagnostikovat různé druhy problémů s vykreslováním.  
  
## <a name="related-sections"></a>Související oddíly  
  
|Titul|Popis|  
|-----------|-----------------|  
|[Ladění v sadě Visual Studio](../debugger/debugging-in-visual-studio.md)|Zavádí funkce ladění v [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].|  
|[Grafika rozhraní DirectX a hry](https://go.microsoft.com/fwlink/?LinkId=256498)|Obsahuje články, které popisují technologií grafiky DirectX.|
