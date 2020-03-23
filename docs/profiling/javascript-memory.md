---
title: Analyzujte využití paměti JavaScript v aplikacích UPW | Dokumenty společnosti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- JavaScript
helpviewer_keywords:
- dominators, memory analyzer (JavaScript)
- memory leaks (JavaScript)
- heap memory, JavaScript
- leaks, memory (JavaScript)
- snapshots, memory analyzer (JavaScript)
- JavaScript Memory Analyzer
- analyzing memory, JavaScript
- memory analyzer, JavaScript
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: cfbc0dcecbf9b30afdfb268117e34c2fcfc0341e
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "73189393"
---
# <a name="analyze-javascript-memory-usage-in-uwp-apps"></a>Analýza využití paměti JavaScriptv aplikacích UPW
Analyzátor paměti JavaScript je k dispozici v sadě Visual Studio, které vám pomůže pochopit využití paměti a najít nevracení paměti v aplikacích UPW vytvořených pro Windows pomocí JavaScriptu. Mezi podporované aplikace patří aplikace pro univerzální aplikace pro Windows Apps.

 Analyzátor paměti JavaScript může dělat tyto věci za vás:

- Pomůže vám rychle najít problémy s využitím paměti v aplikaci s důrazem na nejrelevantnější data.

     Tato data získáte v souhrnech snímků, které zobrazují rozdíly mezi dvěma snímky a poskytují odkazy na podrobnější zobrazení.

- Poskytněte zobrazení dominatorů, typů a kořenů, které pomáhají izolovat problémy.

- Snižte neužitečné informace v datech haldy JavaScriptu.

     Objekty, které nejsou vytvořeny přímo v kódu aplikace, se automaticky odfiltrují. Data můžete také filtrovat podle názvu objektu.

## <a name="run-the-javascript-memory-analyzer"></a>Spuštění analyzátoru paměti JavaScript
 Analyzátor paměti můžete použít, když máte pracovní aplikaci UPW otevřenou v sadě Visual Studio.

#### <a name="to-run-the-memory-analyzer"></a>Spuštění analyzátoru paměti

1. Otevřete sadu Visual Studio.

2. Pokud aplikaci spouštěte z Visual Studia, v seznamu **Spustit ladění** na panelu nástrojů **Standardní** zvolte cíl ladění projektu: **místní počítač** nebo **zařízení**.

3. Na řádku nabídek zvolte **Ladění** > **profileru výkonu**.

     Ve výchozím nastavení je analyzován aktuální projekt spuštění. Pokud chcete změnit cíl analýzy, zvolte **Změnit cíl**.

     ![Cíl analýzy změn](../profiling/media/js_tools_target.png "JS_Tools_Target")

     Pro cíl analýzy jsou k dispozici následující možnosti:

    - **Spuštění projektu**. Analyzuje aktuální projekt spuštění. Pokud aplikaci používáte ve vzdáleném počítači, musíte zvolit tuto možnost, která je výchozí.

    - **Spuštění aplikace**. Umožňuje vybrat aplikaci UPW ze seznamu spuštěných aplikací. Tuto možnost nelze použít, když aplikaci používáte ve vzdáleném počítači.

         Tuto možnost použijte k analýze využití paměti aplikací spuštěných v počítači, když nemáte přístup ke zdrojovému kódu.

    - **Nainstalovaná aplikace**. Umožňuje vybrat nainstalovanou aplikaci UPW, kterou chcete analyzovat. Tuto možnost nelze použít, když aplikaci používáte ve vzdáleném počítači.

         Tuto možnost použijte k analýze využití paměti aplikací, které jste nainstalovali do počítače, když nemáte přístup ke zdrojovému kódu. Tato možnost může být také užitečná, když chcete analyzovat využití paměti libovolné aplikace mimo vývoj vlastní aplikace.

4. V **části Dostupné nástroje**zaškrtněte políčko Paměť **JavaScriptu** a pak zvolte **Start**.

5. Při spuštění analyzátoru paměti může okno Řízení uživatelských účtů požadovat vaše oprávnění ke spuštění nástroje Visual Studio ETW Collector.exe. Zvolte **Ano**.

     Interakci s aplikací otestovat příslušné scénáře využití paměti a zobrazit graf paměti, jak je popsáno v následujících částech.

6. Přepněte do sady Visual Studio stisknutím **klávesy Alt**+**Tab**.

7. Chcete-li zobrazit data, která shromažďuje analyzátor paměti, zvolte **Pořízení snímku haldy**. Viz [Zobrazení souhrnu snímků](#view-a-snapshot-summary) dále v tomto tématu.

## <a name="check-memory-usage"></a>Kontrola využití paměti
 Můžete se pokusit identifikovat nevracení paměti pomocí různých zobrazení v analyzátoru paměti JavaScript. Pokud už máte podezření, že vaše aplikace netěsná paměť, najdete v [tématu izolovat nevracení paměti](#isolate-a-memory-leak) pro navrhované pracovního postupu.

 Pomocí následujících zobrazení můžete identifikovat nevracení paměti v aplikaci:

- [Zobrazit souhrn využití živé paměti](#view-live-memory-usage-summary). Pomocí grafu využití paměti vyhledejte náhlé zvýšení využití paměti nebo neustálé zvyšování využití paměti, které je výsledkem určitých akcí. Použijte zobrazení souhrnu využití živé paměti k pořízení snímků haldy. Snímky se zobrazí jako kolekce v grafu využití paměti.

    > [!TIP]
    > Uvidíte špičku využití paměti při pořízení snímku. Použijte souhrny snímků pro přesnější indikaci růstu.

- [Zobrazení souhrnu snímku](#view-a-snapshot-summary). Můžete zobrazit souhrnné informace snímku během nebo po relaci profilování paměti. Pomocí souhrnů snímek propojit podrobnosti snímku a snímek rozdíl zobrazení.

    > [!TIP]
    > Rozdílové zobrazení snímku obvykle poskytuje nejužitečnější informace o nevracení paměti.

- [Zobrazit podrobnosti snímku](#view-snapshot-details). Zobrazuje podrobná data o využití paměti pro jeden snímek.

- [Zobrazit snímek diff](#view-a-snapshot-diff). Zobrazuje rozdílové hodnoty mezi snímky. Tato zobrazení zobrazují rozdíly ve velikosti objektu a počtu objektů.

## <a name="isolate-a-memory-leak"></a>Izolovat nevracení paměti
 Tyto kroky poskytují pracovní postup, který vám může pomoci efektivněji používat analyzátor paměti JavaScript. Tyto kroky mohou být užitečné, pokud máte podezření, že vaše aplikace má nevracení paměti. Kurz, který vás provede procesem identifikace nevracení paměti v pracovní aplikaci, najdete v [tématu Návod: Vyhledání nevracení paměti (JavaScript)](javascript-memory.md).

1. Otevřete aplikaci ve Visual Studiu.

2. Spusťte JavaScript Memory Analyzer (viz předchozí kroky).

3. Spusťte aplikaci ve scénáři, který chcete otestovat. Scénář může například zahrnovat velkou mutaci DOM při načtení určité stránky nebo při spuštění aplikace.

4. Opakujte scénář 1-4 další časy.

   > [!TIP]
   > Opakovaným opakováním testovacího scénáře několikrát můžete zajistit, že inicializační práce může být odfiltrována z výsledků.

5. Přepněte do sady Visual Studio (stiskněte **klávesu Alt**+**Tab).**

6. Pořízení snímku haldy účaří výběrem **pořízení snímku haldy**.

    Následující obrázek znázorňuje příklad snímku směrného plánu.

    ![Snímek účaří](../profiling/media/js_mem_leak_workflow_baseline.png "JS_Mem_Leak_Workflow_Baseline")

   > [!TIP]
   > Pro přesnější kontrolu nad časování snímků, můžete použít [přidružit zdrojový kód s daty využití paměti](#associate-source-code-with-memory-usage-data) příkaz ve vašem kódu.

7. Přepněte do aplikace a opakujte scénář, který testujete (opakujte pouze jednou).

8. Přepněte do sady Visual Studio a pořizovat druhý snímek.

9. Přepněte do aplikace a opakujte scénář, který testujete (opakujte pouze jednou).

10. Přepněte do sady Visual Studio a pořizovat třetí snímek.

     Následující obrázek znázorňuje příklad druhého a třetího snímku.

     ![Druhý a třetí snímek](../profiling/media/js_mem_leak_workflow.png "JS_Mem_Leak_Workflow")

     Pořízením směrného, druhého a třetího snímku v tomto pracovním postupu můžete snadněji odfiltrovat změny, které nejsou spojeny s nevracením paměti. Například může být očekávané změny, jako je například aktualizace záhlaví a zápatí na stránce, která bude generovat některé změny využití paměti, ale může nesouvisí s nevracení paměti.

11. Ze třetího snímku zvolte odkaz na jeden z rozdílových zobrazení:

    - Rozdílová velikost haldy (levý odkaz pod velikostí haldy). Text odkazu zobrazuje rozdíl mezi haldy velikost aktuální snímek a velikost haldy předchozí snímek.

    - Rozdílový počet objektů (pravé propojení pod počtem objektů). Text odkazu zobrazuje dvě hodnoty (například +1858 / -1765): První hodnota je počet nových objektů přidaných od předchozího snímku a druhá hodnota je počet objektů odebraných od předchozího snímku.

      Tyto odkazy otevřít rozdílové podrobnosti snímek zobrazení typů na haldě, seřazené podle zachované velikosti nebo počet objektů, v závislosti na odkaz, který odkaz jste otevřeli.

12. Zvolte jednu z následujících možností filtru **obor,** která vám pomůže identifikovat problémy s využitím paměti:

    - **Objekty, které zbyly z #2 snímek**.

    - **Objekty přidané mezi #2 snímků a #3**

    > [!TIP]
    > Pomocí filtrovaného zobrazení objektů, které zbyly z předchozího snímku, prozkoumejte nevracení paměti. Například pokud rozdílový počet objektů je +205 / -195, toto zobrazení zobrazí 10 objektů, které zbyly a tyto jsou pravděpodobně kandidáty pro nevracení paměti.

     Následující obrázek znázorňuje rozdílové zobrazení objektů, které zbyly z snímek #2.

     ![Zobrazení rozdílu snímků zobrazující typy](../profiling/media/js_mem_snapshot_diff.png "JS_Mem_Snapshot_Diff")

     Na předchozím obrázku vidíme, že dva objekty zbývají z předchozího snímku. Zjistěte, zda se očekává chování pro konkrétní aplikaci. Pokud ne, může to znamenat nevracení paměti.

13. Chcete-li zjistit, kde jsou objekty v rozdílových pohledech zakořeněny ve globálním objektu, což jim brání v uvolňování paměti, otevřete místní nabídku objektu a pak zvolte **Zobrazit v zobrazení kořenů**. Velký počet objektů může být zachována v paměti, protože jsou odkazovány jeden objekt (nebo několik objektů), které jsou zakořeněny do globálního objektu.

14. Pokud existuje příliš mnoho objektů v zobrazení objektů, které zbyly, pokuste se dále izolovat období, ve kterém dochází k nevracení paměti a potom znovu pořizovat tři snímky. Chcete-li dále izolovat nevracení paměti, použijte [přidružit zdrojový kód s daty využití paměti](#associate-source-code-with-memory-usage-data), [Přidružit zdrojový kód s daty využití paměti](#associate-source-code-with-memory-usage-data)a další data o využití paměti, která jsou k dispozici v analyzátoru paměti.

## <a name="view-live-memory-usage-summary"></a>Zobrazit souhrn využití živé paměti
 Zobrazení souhrnu využití živé paměti poskytuje graf využití paměti pro spuštěnou aplikaci a kolekci všech dlaždic souhrnu snímků. V tomto zobrazení můžete provádět základní úkoly, jako je pořizování snímků, analýza souhrnných informací a přechod na jiná zobrazení. Když zastavíte shromažďování dat, graf paměti zmizí a zobrazí se pouze [zobrazení souhrnného](#view-a-snapshot-summary) zobrazení snímku.

 Graf paměti zobrazuje živé zobrazení procesní paměti aplikace, která zahrnuje soukromé bajty, nativní paměť a haldu JavaScriptu. Graf paměti je posuvné zobrazení paměti procesu. Jak to vypadá:

 ![Graf paměti JavaScript Analyzer](../profiling/media/js_mem_memory_graph.png "JS_Mem_Memory_Graph")

 Pokud jste do kódu aplikace přidali uživatelské značky (viz [Přidružení zdrojového kódu k datům o využití paměti),](#associate-source-code-with-memory-usage-data)zobrazí se v grafu využití paměti obrácený trojúhelník, který označuje, kdy je tato část kódu dosažena.

 Část paměti zobrazené v grafu paměti je přidělena v době runtime JavaScript. Toto využití paměti v aplikaci nelze řídit. Využití paměti zobrazené v grafu se zvyšuje při pořízení prvního snímku a potom se zvyšuje minimálně pro každý další snímek.

## <a name="view-a-snapshot-summary"></a>Zobrazení souhrnu snímku
 Chcete-li pořizovat snímek aktuálního stavu využití paměti vaší aplikace, zvolte **Pořizování snímků haldy** z grafu paměti. Dlaždice souhrnu snímků, která se zobrazí v souhrnu využití živé paměti (když je aplikace spuštěná) a souhrnu snímků (když je aplikace zastavena), poskytuje informace o haldě JavaScriptu a odkazy na podrobnější informace. Pokud pořizovat dva nebo více snímků, snímek poskytuje další informace porovnání jeho data s předchozí snímek.

> [!NOTE]
> Analyzátor paměti JavaScript vynutí uvolnění paměti před každým snímkem. To pomáhá zajistit konzistentnější výsledky mezi spuštěními.

 Tady je příklad souhrnu snímku, když pořizujete více snímků.

 ![Souhrn snímků](../profiling/media/js_mem_snapshot_summary.png "JS_Mem_Snapshot_Summary")

 Shrnutí snímku zahrnuje:

- Název snímku a časové razítko.

- Potenciální problémy se počítají (označeny modrou ikonou informací). Toto číslo, pokud je k dispozici, identifikuje potenciální problémy s pamětí, jako jsou uzly, které nejsou připojeny k dom. Počet odkazy na typy zobrazení snímku, který je seřazen podle typu problému zvýraznit potenciální problémy. Popis obsahuje popis problému.

- Velikost haldy. Toto číslo zahrnuje prvky modelu DOM a objekty, které modul modul u runtime javascriptu přidá do haldy JavaScriptu. Velikost haldy odkazy na typy zobrazení snímku.

- Velikost diferenciální haldy. Tato hodnota zobrazuje rozdíl mezi haldy velikost aktuální snímek a velikost haldy předchozí snímek. Hodnota je následována červenou šipkou nahoru, pokud je zvýšení paměti nebo zelená šipka dolů, pokud dojde ke snížení paměti. Pokud se velikost haldy mezi snímky nezměnila, zobrazí se text **Žádná změna** místo čísla. U prvního snímku se zobrazí text **Účaří**. Rozdílová velikost haldy odkazy na typy zobrazení snímek diff.

- Počet objektů. Tento počet zobrazuje pouze objekty vytvořené ve vaší aplikaci a filtruje předdefinované objekty vytvořené v době runtime javascriptu. Počet objektů odkazuje na zobrazení Typy podrobností snímku.

- Počet diferenciálních objektů. To ukazuje dvě hodnoty: První hodnota je počet nových objektů přidaných od předchozího snímku; a druhá hodnota je počet objektů odebraných od předchozího snímku. Například obrázek ukazuje, že byly přidány 1 859 objektů a 1 733 objektů byly odebrány od snímek #1. Za tímto údajem následuje červená šipka nahoru, pokud se celkový počet objektů zvýšil, nebo zelená šipka dolů, pokud se snížila. Pokud se počet objektů nezměnil, zobrazí se text **Žádná změna** místo čísla. U prvního snímku se zobrazí text **Účaří**. Rozdílový počet objektů odkazy na Typy zobrazení rozdíl snímku.

- Snímek obrazovky v době pořízení snímku.

## <a name="view-snapshot-details"></a>Zobrazit podrobnosti snímku
 Můžete zobrazit podrobné informace o využití paměti pro každý snímek v zobrazení podrobností snímku.

 Ze souhrnného zobrazení snímku zvolte odkaz, abyste viděli podrobnosti snímku. Například odkaz velikost haldy otevře podrobnosti snímku s typem zobrazení otevřené ve výchozím nastavení.

 Tento obrázek znázorňuje zobrazení Typy v detailu snímku s daty využití paměti seřazenými podle uchované velikosti.

 ![Zobrazení podrobností snímku zobrazující potenciální problémy](../profiling/media/js_mem_snapshot_details.png "JS_Mem_Snapshot_Details")

 V zobrazení podrobností snímku můžete zkontrolovat data využití paměti podle typu, kořenu nebo dominátoru výběrem možnosti z panelu nástrojů:

- **Typy**. Zobrazuje počet instancí a celkovou velikost objektů na haldě seskupených podle typu objektu. Ve výchozím nastavení jsou tyto jsou seřazeny podle počtu instancí.

  > [!TIP]
  > Rozdílové pohledy typů na haldě objektu jsou obvykle nejužitečnější zobrazení pro identifikaci nevracení paměti; Tato zobrazení poskytují filtr **Obor,** který pomáhá identifikovat zbývající objekty.

- **Kořeny**. Zobrazuje hierarchické zobrazení objektů od kořenových objektů přes podřízené odkazy. Ve výchozím nastavení jsou podřízené uzly seřazeny podle sloupce zachované velikosti, přičemž největší jsou nahoře.

- **Dominators**. Zobrazí seznam objektů na haldě, které mají výhradní odkazy na jiné objekty. Dominatory jsou seřazeny podle zachované velikosti.

  > [!TIP]
  > Při odebrání dominator z paměti, znovu získat všechny paměti, které objekt zachová. U několika aplikací může zobrazení Dominators pomoci objasnit velikosti uchované paměti, protože můžete prozkoumat celý řetězec odkazů na objekt.

  Všechna tři zobrazení zobrazují podobné typy hodnot, včetně:

- **Identifikátor (identifikátory)**. Název, který nejlépe identifikuje objekt. Například pro elementy HTML podrobnosti snímku zobrazit hodnotu atributu ID, pokud je použit.

- **Zadejte .** Typ objektu (například element propojení HTML nebo element div).

- **Velikost**. Velikost objektu, bez velikosti odkazovaných objektů.

- **Zachována velikost**. Velikost objektu plus velikost všech podřízených objektů, které nemají žádné další rodiče. Z praktických důvodů se jedná o velikost paměti uchované objektem, takže pokud odstraníte objekt, získáte zadané množství paměti.

- **Počet**. Počet instancí objektu. Tato hodnota se zobrazí pouze v zobrazení Typy.

## <a name="view-a-snapshot-diff"></a>Zobrazení rozdílu snímku
 V analyzátoru paměti JavaScript můžete porovnat snímek s předchozím snímku v zobrazení rozdílu snímku.

 V souhrnném zobrazení snímku můžete zobrazit podrobnosti diferenciálního snímku výběrem rozdílové velikosti haldy nebo propojení rozdílového počtu objektů po pořízení dvou nebo více snímků.

 Můžete zobrazit diferenciální informace o typech, kořenech a dominatorech. Rozdíl snímku zobrazuje informace, jako jsou například objekty, které byly přidány do haldy mezi dvěma snímky.

 Tento obrázek znázorňuje zobrazení Typy v rozdílu snímku.

 ![Zobrazení rozdílu snímků zobrazující typy](../profiling/media/js_mem_snapshot_diff.png "JS_Mem_Snapshot_Diff")

 V okně rozdíl snímku jsou zobrazení Dominators, Types a Roots stejné jako v okně [Zobrazit podrobnosti snímku.](#view-snapshot-details) Rozdíl snímku zobrazuje stejné informace jako podrobnosti snímku s těmito dalšími hodnotami:

- **Velikost rozdílu**. Rozdíl mezi velikostí objektu v aktuálním snímku a jeho velikostí v předchozím snímku, bez velikosti všech odkazovaných objektů.

- **Rozdíl zachované velikosti**. Rozdíl mezi zachojenou velikost objektu v aktuální snímek a jeho zachované velikosti v předchozím snímku. Zachovaná velikost zahrnuje velikost objektu plus velikost všech podřízených objektů, které nemají žádné další rodiče. For practical purposes, the retained size is the amount of memory retained by the object, so if you delete the object you reclaim the specified amount of memory.

  Chcete-li filtrovat rozdílové informace mezi snímky, zvolte jeden z filtrů **oboru** v horní části rozdílových pohledů.

- **Objekty, které\<zbyly z čísla snímku #>**. Tento filtr zobrazuje rozdíl mezi objekty přidanými do haldy a odebranými z haldy ve srovnání se snímkem účaří a předchozím snímkem. Například pokud souhrn snímku zobrazuje +205 / -195 v počtu objektů, tento filtr zobrazí deset objektů, které byly přidány, ale nebyly odebrány.

  > [!TIP]
  > Chcete-li zobrazit nejužitečnější informace v tomto filtru, postupujte podle kroků popsaných v [části Izolovat nevracení paměti](#isolate-a-memory-leak).

- **Objekty přidané\<mezi číslo\<snímku> a # číslo>**. Tento filtr zobrazuje všechny objekty přidané do haldy z předchozího snímku.

- **Všechny objekty\<v snímek # číslo>**. Toto nastavení filtru neodfiltruje žádné objekty na haldě.

  Chcete-li zobrazit odkazy na objekty, které neodpovídají aktuálnímu filtru **Obor,** vyberte v rozevíracím seznamu nastavení nastavení v&#45;seznamu nastavení v přehledu nastavení v ![analyzátoru paměti v](../profiling/media/js_mem_settings.png "JS_Mem_Settings") pravém horním rohu podokna možnost Zobrazit **neodpovídající odkazy.** Pokud toto nastavení povolíte, zobrazí se neodpovídající odkazy s šedým textem.

> [!TIP]
> Doporučujeme postupovat podle kroků v [izolovat nevracení paměti](#isolate-a-memory-leak) a potom použít objekty zbývající přes **scope** filtr k identifikaci objektů, které jsou nevracení paměti.

## <a name="view-objects-by-dominator"></a>Zobrazení objektů podle dominátoru
 V zobrazení Typy a Dominators můžete zvolit, zda chcete zobrazit objekty složené do jejich dominators (toto je výchozí zobrazení na kartě **Dominators).** Je-li vybráno toto zobrazení, zobrazí se v zobrazení objektů nejvyšší úrovně pouze dominátory. (Objekty, které jsou potomky objektů mimo globální, jsou v zobrazení nejvyšší úrovně skryty.) U některých aplikací to může objasnit, které objekty způsobují nevracení paměti snížením šumu v datech.

 Chcete-li přepnout zobrazení objektů pomocí dominátoru, zvolte **tlačítko Fold in objects pomocí tlačítka dominator.** ![Skládání předmětů do jejich dominatorů](../profiling/media/js_mem_fold_objects.png "JS_Mem_Fold_Objects")

 Další informace o dominatorech najdete v [tématu Zobrazení podrobností o snímku](#view-snapshot-details).

## <a name="filter-data-by-identifier"></a>Filtrování dat podle identifikátoru
 V zobrazení Dominators a Types můžete odfiltrovat data vyhledáním konkrétních identifikátorů. Chcete-li vyhledat identifikátor, stačí zadat jeho název do textového pole **filtru Identifikátor** v pravém horním. Když začnete psát, budou odfiltrovány identifikátory, které neobsahují zadané znaky.

 Každé zobrazení má svůj vlastní filtr, takže se při přepnutí do jiného zobrazení nezachová.

## <a name="find-an-object-in-the-object-tree"></a>Vyhledání objektu ve stromu objektů
 V zobrazení Typy a Dominators můžete zobrazit vztah určitého `Global` objektu k objektu. Objekty zakořeněné do objektu `Global` nebudou uvolněny. Známý objekt můžete snadno najít v zobrazení Kořeny, aniž byste museli prohledávat strom `Global` objektů. Chcete-li to provést, otevřete místní nabídku objektu v zobrazení Dominators nebo Type a pak zvolte **Zobrazit v zobrazení kořenů**.

## <a name="view-shared-object-references"></a>Zobrazení odkazů na sdílené objekty
 V zobrazení Typy a Dominators dolní podokno obsahuje seznam odkazů na objekty, který zobrazuje sdílené odkazy. Když vyberete objekt v horním podokně, seznam Odkazů na objekt zobrazí všechny objekty, které na tento objekt odkazují.

> [!NOTE]
> Cyklické odkazy jsou zobrazeny s hvězdičkou (*) a informačním popisem a nelze je rozbalit. V opačném případě by zabránit chůzi do referenčního stromu a identifikaci objektů, které jsou zachování paměti.

 Pokud chcete další pomoc s identifikací ekvivalentních objektů, zvolte V seznamu nastavení nastavení v **rozevíracím** seznamu ![nastavení&#45;seznam v analyzátoru paměti](../profiling/media/js_mem_settings.png "JS_Mem_Settings") v pravém horním rohu horního podokna. Tato možnost zobrazí ID objektů vedle názvů objektů v seznamu **Identifikátor(y)** (ID se zobrazí ve všech zobrazeních, nikoli pouze v seznamu odkazy na objekty). Objekty, které mají stejné ID jsou sdílené odkazy.

 Následující obrázek znázorňuje seznam Odkazů na objekty pro vybranou položku se zobrazenými ID.

 ![Odkazy na objekty se zobrazenými ID](../profiling/media/js_mem_shared_refs.png "JS_Mem_Shared_Refs")

## <a name="show-built-in-objects"></a>Zobrazit vestavěné objekty
 Ve výchozím nastavení zobrazení Dominators a Typy zobrazují pouze objekty, které vytvoříte v aplikaci. To vám pomůže odfiltrovat nepotřebné informace a izolovat problémy související s aplikací. Někdy však může být užitečné zobrazit všechny objekty, které javascriptový běh ový čas generuje pro vaši aplikaci.

 Chcete-li tyto objekty zobrazit, zvolte **Zobrazit předdefinované objekty** v seznamu ![nastavení Nastavení rozevíracího seznamu&#45;seznamu v analyzátoru paměti](../profiling/media/js_mem_settings.png "JS_Mem_Settings") v pravém horním rohu podokna.

## <a name="save-diagnostic-session-files"></a>Uložení souborů diagnostických relací
 Souhrny diagnostických snímků a jejich přidružená zobrazení podrobností jsou uložena jako . *soubory diagsession.* **Průzkumník řešení** zobrazuje předchozí diagnostické relace ve složce Diagnostické relace. V **Průzkumníku řešení**můžete otevřít předchozí relace nebo odebrat nebo přejmenovat soubory.

## <a name="associate-source-code-with-memory-usage-data"></a>Přidružení zdrojového kódu k datům využití paměti
 Chcete-li izolovat část kódu, který má problém s pamětí, použijte následující metody:

- Vyhledejte názvy tříd a ID pro prvky DOM v podrobnostech a diferenciální zobrazení.

- Vyhledejte hodnoty řetězce v podrobnostech a rozdílové zobrazení, které mohou být přidruženy ke zdrojovému kódu.

- Pomocí [příkazu Najít objekt v příkazu stromu objektů](#find-an-object-in-the-object-tree) se můžete procházet stromem objektů. To může pomoci identifikovat přidružený zdrojový kód.

- Přidejte příkazy analyzátoru paměti do zdrojového kódu.

  Ve zdrojovém kódu můžete použít následující příkazy:

- `console.takeHeapSnapshot`pořídí snímek haldy, který se zobrazí v analyzátoru paměti JavaScript. Tento příkaz je jedním z [příkazů konzoly JavaScript](../debugger/javascript-console-commands.md).

- `performance.mark`nastaví značku uživatele (obrácený trojúhelník), která se zobrazí v časové ose grafu paměti v souhrnném zobrazení, když je aplikace spuštěná. Tento příkaz trvá jeden řetězec argument, který popisuje událost a zobrazí se jako popis ekviací v grafu paměti. Tento popis nesmí přesáhnout 100 znaků.

> [!TIP]
> Slouží `console.takeHeapSnapshot` k urychlení analýzy při opakování scénářů využití paměti.

 Tyto příkazy vyvolat výjimku, pokud je přidáte do aplikace a spustit aplikaci mimo analyzátor paměti JavaScript. Můžete však otestovat, zda příkazy existují před jejich použitím. (Příkazy neexistují na začátku fáze spuštění relace.) Chcete-li zkontrolovat, `takeHeapSnapshot`zda můžete bezpečně volat , použijte tento kód:

```javascript
if (console && console.takeHeapSnapshot) {
    console.takeHeapSnapshot();
}
```

 Chcete-li zkontrolovat, `performance.mark`zda můžete bezpečně volat , použijte tento kód:

```javascript
if (performance && performance.mark) {
    performance.mark("message_string");
}

```

 Zde je graf paměti s několika uživatelskými značkami a popisem pro `performance.mark` aktuálně vybranou uživatelskou značku, pro kterou je argument řetězce nastaven na "data generovaná":

 ![Použití značky profilu](../profiling/media/js_mem_performance_marks.png "JS_Mem_Performance_Marks")

## <a name="tips-to-identify-memory-issues"></a>Tipy k identifikaci problémů s pamětí

- Postupujte podle pracovního postupu popsaného v [izolovat nevracení paměti](#isolate-a-memory-leak) a použít **objekty, které zbyly z snímek\<# číslo>** filtr v rozdílovém zobrazení k identifikaci pravděpodobných kandidátů pro nevracení paměti.

- Pomocí [funkce Najít objekt ve stromu objektů](#find-an-object-in-the-object-tree) můžete zjistit, na který objekt odkazuje v hierarchii paměti. Kořeny zobrazení ukazuje, jak je objekt zakořeněný do globálního objektu, což by zabránilo uvolnění paměti.

- Pokud je obtížné identifikovat příčinu problému s pamětí, použijte různá zobrazení (například dominatory a typy) k vyhledání společných rysů, zejména k identifikaci jednoho objektu (nebo několika objektů), který může obsahovat odkazy na mnoho jiných objektů, které se zobrazují v zobrazení.

- Vyhledejte objekty, které jsou neúmyslně uchovány v paměti poté, co uživatel přejde na novou stránku, což je běžná příčina problémů s pamětí. Například:

  - Nesprávné použití [adresy URL. CreateObjectUrl](https://developer.mozilla.org/docs/Web/API/URL/createObjectURL) může způsobit tento problém.

  - Některé objekty `dispose` mohou poskytnout metodu a doporučení pro použití. Například byste měli `dispose` volat na [WinJS.Binding.List,](/previous-versions/windows/apps/hh700774\(v\=win.10\)) pokud `createFiltered` zavoláte metodu seznamu a potom přejít od stránky.

  - Možná budete muset odebrat jeden nebo více posluchačů událostí. Další informace naleznete [v tématu Zobrazení posluchačů událostí dom](../debugger/quickstart-debug-html-and-css.md).

- Podívejte se na druhou část [tohoto videa](https://channel9.msdn.com/Events/Build/2013/3-316) z konference Build 2013 o analyzátoru paměti JavaScript.

- Přečtěte si [článek Správa paměti v aplikacích UPW](https://msdn.microsoft.com/magazine/jj651575.aspx).

- Zvažte dočasně úpravu kódu izolovat problémy. Můžete například chtít:

  - Použijte příkazy pro analyzátor `console.takeSnapshot` paměti `performance.mark`a . (Viz [Přidružení zdrojového kódu k datům o využití paměti](#associate-source-code-with-memory-usage-data).)

    Pomocí těchto příkazů můžete izolovat problémy, které nelze izolovat ručním pořízením snímku haldy.

  - Vytvořte testovací objekt a sledujte ho v zobrazeních analyzátoru paměti JavaScript, například v zobrazení Typy. Můžete například připojit velmi velký objekt k jinému objektu a zjistit, zda byl určitý objekt nebo prvek uvolněn.
