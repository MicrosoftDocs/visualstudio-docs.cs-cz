---
title: Paměť JavaScriptu | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- dominators, memory analyzer (JavaScript)
- memory leaks (JavaScript)
- heap memory, JavaScript
- leaks, memory (JavaScript)
- snapshots, memory analyzer (JavaScript)
- JavaScript Memory Analyzer
- analyzing memory, JavaScript
- memory analyzer, JavaScript
ms.assetid: 78f8532b-7b4e-4b50-b8b7-68ca0926dd4e
caps.latest.revision: 54
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: a71de3e425896c5f4394f28ecbf7f90866f383e7
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2019
ms.locfileid: "74302775"
---
# <a name="javascript-memory"></a>Paměť (JavaScript)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Analyzátor paměti JavaScriptu je k dispozici v aplikaci Visual Studio, které vám pomůžou pochopit využití paměti a najít nevracení paměti ve vašich aplikacích pro Store sestavených pro Windows pomocí JavaScriptu. Mezi podporované aplikace patří aplikace pro Windows Phone Store a Windows Store.  
  
 Analyzátor paměti JavaScriptu vám může udělat tyto věci:  
  
- Pomůže vám rychle najít problémy s využitím paměti ve vaší aplikaci tím, že zvýrazníte nejrelevantnější data.  
  
   Tato data získáte v souhrnech snímků, které znázorňují rozdíly mezi dvěma snímky a poskytují odkazy na podrobnější zobrazení.  
  
- Poskytněte zobrazení dominantních objektů, typů a kořenů, které vám pomůžou izolovat problémy.  
  
- V datech haldy JavaScriptu snižte informace, které nechcete dělat.  
  
   Objekty, které nejsou vytvořeny přímo v kódu aplikace, jsou automaticky filtrovány. Data můžete také filtrovat podle názvu objektu.  
  
  Kurz, který vás provede procesem identifikace nevracení paměti v pracovní aplikaci, najdete v tématu [Návod: Vyhledání nevrácené paměti (JavaScript)](../profiling/walkthrough-find-a-memory-leak-javascript.md).  
  
  V tomto tématu:  
  
  [Spusťte  analyzátor paměti JavaScriptu](#Run) .  
  [Ověřit využití paměti](#Check)   
  [Izolace  nevracení paměti](#Isolate)  
  [Zobrazení souhrnu využití živé paměti](#LiveMemory)   
  [Zobrazit souhrn  snímku](#SnapshotSummary)  
  [Zobrazit podrobnosti o snímku](#SnapshotDetails)   
  [Zobrazit rozdíl  snímku](#SnapshotDiff)  
  [Zobrazit objekty podle dominantního objektu](#FoldObjects)   
  [Filtrovat data podle  identifikátorů](#Filter)  
  [Hledání objektu ve stromové struktuře objektů](#ShowInRootsView)   
  [Zobrazit odkazy na sdílené objekty](#References)   
  [Zobrazit předdefinované objekty](#BuiltInValues)   
  [Uložení souborů relace diagnostiky](#Save)   
  [Přidružte zdrojový kód k datům využití paměti](#JSConsoleCommands)   
  [Tipy pro identifikaci problémů s pamětí](#Tips)  
  
## <a name="Run"></a>Spuštění analyzátoru paměti JavaScriptu  
 Můžete použít analyzátor paměti, když máte pracovní aplikaci pro Windows Store otevřenou v aplikaci Visual Studio nebo nainstalovanou na počítači se systémem [!INCLUDE[win8](../includes/win8-md.md)] nebo novějším.  
  
#### <a name="to-run-the-memory-analyzer"></a>Spuštění analyzátoru paměti  
  
1. Otevřít Visual Studio.  
  
2. Pokud spouštíte aplikaci ze sady Visual Studio, v seznamu **Spustit ladění** na **standardním** panelu nástrojů vyberte cíl ladění pro váš projekt: buď emulátor Windows Phone, nebo, pro aplikaci pro Windows Store, **místní počítač**, **simulátor**nebo **vzdálený počítač**.  
  
     Další informace o těchto možnostech najdete v tématu [spuštění aplikací ze sady Visual Studio](../debugger/run-store-apps-from-visual-studio.md).  
  
3. Na řádku nabídek klikněte na položku **ladit**, **profilování výkonu..** ..  
  
     Ve výchozím nastavení se analyzuje aktuální projekt po spuštění. Chcete-li změnit cíl analýzy, vyberte možnost **změnit cíl**.  
  
     ![Změnit cíl analýzy](../profiling/media/js-tools-target.png "JS_Tools_Target")  
  
     Pro cíl analýzy jsou k dispozici následující možnosti:  
  
    - **Spouštěný projekt**. Analyzuje aktuální spouštěný projekt. Pokud aplikaci spouštíte na vzdáleném počítači, musíte zvolit tuto možnost, což je výchozí nastavení.  
  
    - **Spouští se aplikace**. Umožňuje vybrat aplikaci pro Windows Store ze seznamu spuštěných aplikací. Tuto možnost nemůžete použít, když aplikaci spouštíte na vzdáleném počítači.  
  
         Tato možnost slouží k analýze využití paměti aplikací, které jsou spuštěny v počítači, pokud nemáte přístup ke zdrojovému kódu.  
  
    - **Nainstalovaná aplikace**. Umožňuje vybrat nainstalovanou aplikaci pro Windows Store, kterou chcete analyzovat. Tuto možnost nemůžete použít, když aplikaci spouštíte na vzdáleném počítači.  
  
         Tuto možnost použijte k analýze využití paměti aplikací, které jste nainstalovali v počítači, když nemáte přístup ke zdrojovému kódu. Tato možnost může být užitečná také v případě, že chcete pouze analyzovat využití paměti jakékoli aplikace mimo vlastní vývoj aplikací.  
  
4. Z **dostupných nástrojů**zaškrtněte políčko **paměť JavaScriptu** a pak zvolte **Spustit**.  
  
5. Když spustíte nástroj pro analýzu paměti, může okno Řízení uživatelských účtů požádat o vaše oprávnění ke spuštění sady Visual Studio ETW. exe. Vyberte **Ano**.  
  
     V interakci s aplikací otestujete relevantní scénáře využití paměti a zobrazte graf paměti, jak je popsáno v následujících částech.  
  
6. Přepněte do sady Visual Studio stisknutím kláves ALT + TAB.  
  
7. Chcete-li zobrazit data, která analyzátor paměti shromažďuje, vyberte možnost **pořídit snímek haldy**. Viz téma [zobrazení souhrnu snímku](#SnapshotSummary) dále v tomto tématu.  
  
## <a name="Check"></a>Ověřit využití paměti  
 Můžete zkusit identifikovat nevracení paměti pomocí různých zobrazení v analyzátoru paměti JavaScriptu. Pokud už máte podezření, že vaše aplikace nevrací paměť, přečtěte si téma [izolování nevracení paměti](#Isolate) pro navrhovaný pracovní postup.  
  
 Pomocí následujících zobrazení můžete identifikovat nevracení paměti v aplikaci:  
  
- [Zobrazení souhrnu využití živé paměti](#LiveMemory) Pomocí grafu využití paměti můžete najít náhlé zvýšení využití paměti nebo průběžně zvyšovat využití paměti, které je výsledkem konkrétních akcí. K pořizování snímků haldy použijte zobrazení souhrnu využití paměti Live. Snímky se zobrazí jako kolekce v grafu využití paměti.  
  
    > [!TIP]
    > Při pořizování snímku se zobrazí Špička využití paměti. Použijte souhrny snímků pro přesnější indikaci růstu.  
  
- [Zobrazit souhrn snímku](#SnapshotSummary). Můžete zobrazit souhrnné informace o snímku během relace profilace paměti nebo po ní. Pomocí souhrnů snímků můžete propojit s podrobnostmi o snímku a zobrazeními rozdílů snímků.  
  
    > [!TIP]
    > Rozdílová zobrazení snímků mají typicky k dispozici nejužitečnější informace o nevracení paměti.  
  
- [Zobrazit podrobnosti o snímku](#SnapshotDetails). Zobrazuje podrobná data o využití paměti pro jeden snímek.  
  
- [Zobrazit rozdíl snímku](#SnapshotDiff) Zobrazuje rozdílové hodnoty mezi snímky. Tato zobrazení znázorňují rozdíly v velikosti objektů a počtu objektů.  
  
## <a name="Isolate"></a>Izolace nevrácené paměti  
 Tyto kroky poskytují pracovní postup, který vám může pomáhat efektivněji používat analyzátor paměti JavaScriptu. Tyto kroky můžou být užitečné, pokud máte podezření, že vaše aplikace má nevrácenou paměť. Kurz, který vás provede procesem identifikace nevracení paměti v pracovní aplikaci, najdete v tématu [Návod: Vyhledání nevrácené paměti (JavaScript)](../profiling/walkthrough-find-a-memory-leak-javascript.md).  
  
1. Otevřete aplikaci v aplikaci Visual Studio.  
  
2. Spusťte analyzátor paměti JavaScriptu. Další informace najdete v tématu [spuštění analyzátoru paměti JavaScriptu](#Run).  
  
3. Spusťte aplikaci ve scénáři, který chcete otestovat. Scénář může například zahrnovat velkou mutace modelu DOM, při načtení konkrétní stránky nebo při spuštění aplikace.  
  
4. Opakujte scénář 1-4 ještě jednou.  
  
   > [!TIP]
   > Opakováním testovacího scénáře několikrát pomůžete zajistit, aby bylo možné vyfiltrovat inicializační práci z výsledků.  
  
5. Přepněte do sady Visual Studio (stiskněte klávesovou zkratku ALT + TAB).  
  
6. Pořídit snímek základní haldy výběrem možnosti **pořídit snímek haldy**.  
  
    Následující ilustrace znázorňuje příklad snímku směrného plánu.  
  
    ![Snímek směrného plánu](../profiling/media/js-mem-leak-workflow-baseline.png "JS_Mem_Leak_Workflow_Baseline")  
  
   > [!TIP]
   > Pro přesnější kontrolu nad časováním snímků můžete použít příkaz [přidružit zdrojový kód s daty využití paměti](#JSConsoleCommands) ve vašem kódu.  
  
7. Přepněte do vaší aplikace a zopakujte scénář, který testujete (jenom jednou se opakuje).  
  
8. Přepněte do sady Visual Studio a proveďte druhý snímek.  
  
9. Přepněte do vaší aplikace a zopakujte scénář, který testujete (jenom jednou se opakuje).  
  
10. Přepněte do sady Visual Studio a proveďte třetí snímek.  
  
     Následující ilustrace znázorňuje příklad druhého a třetího snímku.  
  
     ![Druhý a třetí snímek](../profiling/media/js-mem-leak-workflow.png "JS_Mem_Leak_Workflow")  
  
     Když v tomto pracovním postupu převezmete směrný plán, druhý a třetí snímek, můžete vyfiltrovat změny, které nejsou spojené s nevracením paměti, snadněji. Například je možné očekávat změny, jako je aktualizace hlaviček a zápatí na stránce, což způsobí, že dojde k vygenerování některých změn využití paměti, ale nemusí souviset s nevracením paměti.  
  
11. Ve třetím snímku vyberte odkaz na jedno z rozdílového zobrazení:  
  
    - Velikost rozdílové haldy (levý odkaz pod velikostí haldy) Text odkazu zobrazuje rozdíl mezi velikostí haldy aktuálního snímku a velikostí haldy předchozího snímku.  
  
    - Počet rozdílových objektů (pravý odkaz pod počtem objektů). Text odkazu zobrazuje dvě hodnoty (například + 1858/-1765): první hodnota je počet nových objektů přidaných od předchozího snímku a druhá hodnota je počet odebraných objektů od předchozího snímku.  
  
      Tyto odkazy otevřou rozdílové zobrazení podrobností o snímcích na haldě seřazené podle velikosti zachované nebo počtu objektů v závislosti na tom, který odkaz jste otevřeli.  
  
12. Vyberte jednu z následujících možností filtrování **oboru** , které vám pomůžou identifikovat problémy s využitím paměti:  
  
    - **Objekty, které zůstaly ze #2 snímků**.  
  
    - **Objekty přidané mezi snímky #2 a #3**  
  
    > [!TIP]
    > Pomocí filtrovaného zobrazení objektů zbývajících z předchozího snímku můžete prozkoumat nevracení paměti. Například pokud je počet rozdílových objektů + 205/-195, zobrazí se v tomto zobrazení 10 objektů, které zůstaly při nevracení paměti.  
  
     Následující ilustrace znázorňuje rozdílové zobrazení objektů zbývajících ze snímku #2.  
  
     ![Zobrazení rozdílů snímků znázorňující typy](../profiling/media/js-mem-snapshot-diff.png "JS_Mem_Snapshot_Diff")  
  
     Na předchozí ilustraci vidíte, že se z předchozího snímku nacházely dva objekty. Zjistěte, jestli se jedná o očekávané chování vaší konkrétní aplikace. Pokud ne, může to znamenat nevracení paměti.  
  
13. Chcete-li zjistit, kde jsou objekty v zobrazení rozdílů rootem na globální objekt, což brání v uvolňování paměti, otevřete místní nabídku objektu a pak zvolte možnost **Zobrazit v zobrazení kořene**. Velký počet objektů může být zachován v paměti, protože na ně odkazuje jeden objekt (nebo několik objektů), který je rootem pro globální objekt.  
  
14. Pokud je v zobrazení objektů, které zůstaly, příliš mnoho objektů, zkuste dále izolovat období, ve kterém dochází k nevrácené paměti, a potom znovu Převezměte tři snímky. K další izolaci nevracení paměti použijte [přidružení zdrojového kódu k datům využití paměti](#JSConsoleCommands), [přidružte zdrojový kód k datům využití paměti](#JSConsoleCommands)a další data o využití paměti, která jsou k dispozici v analyzátoru paměti.  
  
## <a name="LiveMemory"></a>Zobrazit souhrn využití živé paměti  
 Zobrazení souhrnu využití paměti v reálném čase poskytuje graf využití paměti pro spuštěnou aplikaci a kolekci všech dlaždic souhrnů snímků. V tomto zobrazení můžete provádět základní úlohy, jako je pořízení snímků, Analýza souhrnných informací a přechod na další zobrazení. Když zastavíte shromažďování dat, graf paměti zmizí a zobrazí se pouze zobrazení [souhrnu snímků](#SnapshotSummary) .  
  
 Graf paměti ukazuje živý přehled paměti procesu aplikace, která zahrnuje soukromé bajty, nativní paměť a haldu JavaScriptu. Graf paměti je posuvný pohled na paměť procesu. Zde je, jak to funguje:  
  
 ![Graf paměti analyzátoru paměti JavaScriptu](../profiling/media/js-mem-memory-graph.png "JS_Mem_Memory_Graph")  
  
 Pokud jste přidali uživatelské značky do kódu aplikace (viz [přidružte zdrojový kód s daty o využití paměti](#JSConsoleCommands)), v grafu využití paměti se zobrazí opačný trojúhelník, který označuje, kdy je dosaženo této části kódu.  
  
 Některá z paměti zobrazená v grafu paměti je přidělena modulem runtime jazyka JavaScript. Toto využití paměti ve vaší aplikaci nemůžete řídit. Využití paměti zobrazené v grafu se zvětšuje při pořízení prvního snímku a pak se u každého dalšího snímku zvyšuje minimální.  
  
## <a name="SnapshotSummary"></a>Zobrazit souhrn snímku  
 Pokud chcete pořídit snímek aktuálního stavu využití paměti vaší aplikace, vyberte z grafu paměti možnost **pořídit snímek haldy** . Dlaždice souhrnu snímku, která se zobrazuje v souhrnu využití živé paměti (i když je aplikace spuštěná) a Souhrn snímku (když je aplikace zastavená), poskytuje informace o haldě JavaScriptu a odkazy na podrobnější informace. Pokud použijete dva nebo více snímků, snímek poskytne další informace, které porovnávají jeho data s předchozím snímkem.  
  
> [!NOTE]
> Analyzátor paměti JavaScriptu vynutí uvolňování paměti před každým snímkem. To pomáhá zajistit více konzistentních výsledků mezi spuštění.  
  
 Tady je příklad souhrnu snímku při převzetí více snímků.  
  
 ![Souhrn snímku](../profiling/media/js-mem-snapshot-summary.png "JS_Mem_Snapshot_Summary")  
  
 Shrnutí snímku zahrnuje:  
  
- Název snímku a časové razítko.  
  
- Počet potenciálních problémů (označený modrou informační ikonou) Toto číslo, pokud je k dispozici, identifikuje možné problémy s pamětí, například uzly, které nejsou připojeny k modelu DOM. Počet odkazuje na zobrazení typů snímku, který je seřazen podle typu problému a zvýrazní možné problémy. Popis problému je zobrazen pomocí popisku.  
  
- Velikost haldy. Toto číslo zahrnuje prvky modelu DOM a objekty, které modul runtime jazyka JavaScript přidá do haldy jazyka JavaScript. Velikost haldy odkazuje na zobrazení typů snímku.  
  
- Velikost rozdílové haldy Tato hodnota zobrazuje rozdíl mezi velikostí haldy aktuálního snímku a velikostí haldy předchozího snímku. Hodnota je následována červenou šipkou nahoru, pokud dojde k zmenšení paměti nebo zelenou šipku dolů. Pokud se velikost haldy mezi snímky nezměnila, zobrazí se místo čísla text **žádná změna** . Pro první snímek uvidíte **základní**text. Rozdílová velikost haldy odkazuje na zobrazení typů rozdílu snímku.  
  
- Počet objektů. Tento počet zobrazuje pouze objekty vytvořené ve vaší aplikaci a filtruje předdefinované objekty vytvořené modulem runtime jazyka JavaScript. Počet objektů odkazuje na zobrazení typů podrobností snímku.  
  
- Počet rozdílových objektů Zobrazí se dvě hodnoty: první hodnota je počet nových objektů přidaných od předchozího snímku; a druhá hodnota je počet objektů odebraných od předchozího snímku. Například ilustrace ukazuje, že byly přidány objekty 1 859 a byly od #1 snímku odebrány objekty 1 733. Tyto informace jsou následovány červenou šipkou nahoru, pokud je celkový počet objektů zvětšený nebo zelená šipka dolů, pokud se snížila. Pokud se počet objektů nezměnil, zobrazí se místo čísla text **žádná změna** . Pro první snímek uvidíte **základní**text. Počet rozdílových objektů odkazuje na zobrazení typů rozdílu snímku.  
  
- Snímek obrazovky obrazovky v době pořízení snímku.  
  
## <a name="SnapshotDetails"></a>Zobrazit podrobnosti o snímku  
 Můžete zobrazit podrobné informace o využití paměti pro každý snímek v zobrazení podrobností snímku.  
  
 V zobrazení souhrnu snímků klikněte na odkaz pro zobrazení podrobností o snímku. Například odkaz na velikost haldy otevírá podrobnosti o snímku pomocí zobrazení typy otevřené ve výchozím nastavení.  
  
 Tento obrázek znázorňuje zobrazení typů v podrobnostech snímku s daty o využití paměti seřazenými podle zachované velikosti.  
  
 ![Zobrazení podrobností snímku znázorňující možné problémy](../profiling/media/js-mem-snapshot-details.png "JS_Mem_Snapshot_Details")  
  
 V zobrazení podrobností snímku můžete zkontrolovat data o využití paměti podle typu, kořen nebo dominantního objektu výběrem možnosti z panelu nástrojů:  
  
- **Typy**. Zobrazuje počet instancí a celkovou velikost objektů v haldě seskupených podle typu objektu. Ve výchozím nastavení jsou tyto hodnoty seřazené podle počtu instancí.  
  
  > [!TIP]
  > Rozdílová zobrazení typů na haldě objektu jsou typicky nejužitečnější zobrazení pro identifikaci nevracení paměti. Tato zobrazení poskytují filtr **oboru** , který usnadňuje identifikaci objektů vlevo.  
  
- **Kořeny**. Zobrazuje hierarchické zobrazení objektů z kořenových objektů prostřednictvím podřízených odkazů. Ve výchozím nastavení jsou podřízené uzly seřazené podle sloupce zachovaná velikost, přičemž největší v horní části.  
  
- **Dominantní**objekty. Zobrazuje seznam objektů na haldě, které mají exkluzivní odkazy na jiné objekty. Dominantní objekty jsou seřazené podle zachované velikosti.  
  
  > [!TIP]
  > Při odebrání dominantního objektu z paměti dojde k uvolnění veškeré paměti, kterou objekt uchovává. Pro několik aplikací může zobrazení dominantních objektů pomáhat objasnit uchovávané velikosti paměti, protože můžete prozkoumat úplný řetěz odkazů na objekty.  
  
  Všechna tři zobrazení znázorňují podobné typy hodnot, včetně:  
  
- **Počet identifikátorů**:. Název, který nejlépe identifikuje objekt. Například pro prvky jazyka HTML zobrazuje podrobnosti o snímku hodnotu atributu ID, pokud je použit.  
  
- **Zadejte**. Typ objektu (například element odkazu HTML nebo element div).  
  
- **Velikost**. Velikost objektu, nezahrnuje velikost žádné odkazované objekty.  
  
- **Velikost zachovaná**. Velikost objektu a velikost všech podřízených objektů, které nemají jiné nadřazené objekty. Pro praktické účely se jedná o množství paměti uchovávané objektem, takže pokud odstraníte objekt, který uvolní určenou velikost paměti.  
  
- **Počet**. Počet instancí objektů. Tato hodnota se zobrazí pouze v zobrazení typů.  
  
## <a name="SnapshotDiff"></a>Zobrazit rozdíl snímku  
 V analyzátoru paměti JavaScriptu můžete porovnat snímek s předchozím snímkem v zobrazeních rozdílů snímků.  
  
 V zobrazení se souhrnnými snímky můžete zobrazit rozdílové podrobnosti o snímku kliknutím na odkazy na rozdílové velikosti haldy nebo rozdílového počtu objektů po pořízení dvou nebo více snímků.  
  
 Můžete zobrazit rozdílové informace o typech, kořenech a dominantních objektů. Rozdíl snímku zobrazuje informace, jako například objekty, které byly přidány do haldy mezi dvěma snímky.  
  
 Tento obrázek znázorňuje zobrazení typů ve rozdílovém snímku.  
  
 ![Zobrazení rozdílů snímků znázorňující typy](../profiling/media/js-mem-snapshot-diff.png "JS_Mem_Snapshot_Diff")  
  
 V okně rozdíl snímku jsou podokenní, typy a kořenová zobrazení stejná jako v okně [Zobrazit podrobnosti snímku](#SnapshotDetails) . Rozdíl snímku zobrazuje stejné informace jako detaily snímku s těmito dalšími hodnotami:  
  
- **Rozdíl velikosti** Rozdíl mezi velikostí objektu v aktuálním snímku a jeho velikostí v předchozím snímku, bez zahrnutí velikosti žádné odkazované objekty.  
  
- **Rozdíl uchovávané velikosti** Rozdíl mezi zachovaná velikost objektu v aktuálním snímku a jeho zachovaná velikost v předchozím snímku. Zadržovaná velikost zahrnuje velikost objektu a velikost všech jeho podřízených objektů, které nemají jiné nadřazené objekty. Pro praktické účely je zachovaná velikost velikost paměti uchovávané objektem, takže pokud odstraníte objekt, který uvolní určenou velikost paměti.  
  
  Chcete-li filtrovat rozdílové informace mezi snímky, vyberte jeden z filtrů **oboru** v horní části rozdílového zobrazení.  
  
- **Objekty, které zůstaly ze snímku #\<číslo >** . Tento filtr znázorňuje rozdíl mezi objekty přidanými do haldy a odebranými z haldy v porovnání s snímkem standardních hodnot a předchozím snímkem. Pokud například Souhrn snímku v počtu objektů zobrazuje + 205/-195, tento filtr vám zobrazí deset objektů, které byly přidány, ale nebyly odebrány.  
  
  > [!TIP]
  > Chcete-li zobrazit nejužitečnější informace v tomto filtru, postupujte podle kroků popsaných v části [izolování nevracení paměti](#Isolate).  
  
- **Objekty přidané mezi čísly snímku #\<číslo > a #\<číslo >** . Tento filtr zobrazuje všechny objekty přidané do haldy z předchozího snímku.  
  
- **Všechny objekty ve snímku #\<číslo >** . Toto nastavení filtru nevyfiltruje žádné objekty v haldě.  
  
  Chcete-li zobrazit odkazy na objekty, které neodpovídají aktuálnímu filtru **oboru** , vyberte možnost **Zobrazit neshodné odkazy** v ![rozevíracím&#45;seznamu nastavení seznamu nastavení v části analyzátor paměti](../profiling/media/js-mem-settings.png "JS_Mem_Settings") v pravém horním rohu podokna. Pokud povolíte toto nastavení, zobrazí se neshodné odkazy s šedým textem.  
  
> [!TIP]
> Doporučujeme, abyste postupovali podle kroků v části [izolování nevracení paměti](#Isolate) a pak použijete filtr objekty nalevo od **rozsahu** , který pomůže identifikovat objekty, které nevrací paměť.  
  
## <a name="FoldObjects"></a>Zobrazit objekty podle dominantního objektu  
 V zobrazení typy a dominantního objektu můžete zvolit, zda chcete zobrazit objekty přeložené do jejich dominantních objektů (Toto je výchozí zobrazení na kartě dominantní objekty). Pokud je vybráno toto zobrazení, zobrazí se pouze dominantní objekty v zobrazení objektů na nejvyšší úrovni. (Objekty, které jsou následníky jiných než globálních objektů, jsou v zobrazení nejvyšší úrovně skryté.) U některých aplikací to může vyjasnit, které objekty způsobují nevracení paměti snížením hluku dat.  
  
 Chcete-li přepnout zobrazení objektů podle dominantního objektu, klikněte na tlačítko **přeložení v Objects by dominantního objektu** . ![Skládání objektů do jejich dominantních objektů](../profiling/media/js-mem-fold-objects.png "JS_Mem_Fold_Objects ")  
  
 Další informace o dominantních sestavách najdete v tématu [zobrazení podrobností o snímku](#SnapshotDetails).  
  
## <a name="Filter"></a>Filtrovat data podle identifikátoru  
 V zobrazeních dominantního a typů můžete vyfiltrovat data hledáním konkrétních identifikátorů. Chcete-li vyhledat identifikátor, stačí zadat jeho název do textového pole **Filtr identifikátorů** v pravém horním rohu. Když začnete psát, identifikátory, které neobsahují zadané znaky, se odfiltrují.  
  
 Každé zobrazení má vlastní filtr, takže při přepnutí do jiného zobrazení se filtr nezachová.  
  
## <a name="ShowInRootsView"></a>Hledání objektu ve stromu objektů  
 V zobrazení typy a dominantních objektů můžete zobrazit vztah konkrétního objektu k objektu `Global`. Objekty, které jsou zavedené do objektu `Global`, nebudou shromažďovány do paměti. Známý objekt můžete snadno najít v zobrazení kořene bez prohledávání stromu `Global` objektů. Provedete to tak, že otevřete místní nabídku pro objekt v částice nebo zobrazení typu a pak zvolíte **Zobrazit v zobrazení kořene**.  
  
## <a name="References"></a>Zobrazit odkazy na sdílené objekty  
 V zobrazení typy a dominantního prvku obsahuje dolní podokno seznam odkazů na objekty, který zobrazuje sdílené odkazy. Když vyberete objekt v horním podokně, seznam odkazy na objekt zobrazí všechny objekty, které odkazují na tento objekt.  
  
> [!NOTE]
> Cyklické odkazy jsou zobrazeny pomocí hvězdičky (*) a informativního popisu a nelze je rozšířit. V opačném případě by vám zabránilo v procházení stromu odkazů a určení objektů, které uchovávají paměť.  
  
 Chcete-li získat další informace, které identifikují ekvivalentní objekty, vyberte možnost **Zobrazit ID objektů** v ![&#45;rozevíracím seznamu nastavení seznamu nastavení v části analyzátor paměti](../profiling/media/js-mem-settings.png "JS_Mem_Settings") v pravém horním rohu horního podokna. Tato možnost zobrazí ID objektů vedle názvů objektů v seznamu **identifikátorů** (ID se zobrazí ve všech zobrazeních, nikoli pouze v seznamu odkazů na objekty). Objekty, které mají stejné ID, jsou sdílené odkazy.  
  
 Následující ilustrace znázorňuje seznam odkazů na objekty pro vybranou položku se zobrazenými ID.  
  
 ![Odkazy na objekty se zobrazenými ID](../profiling/media/js-mem-shared-refs.png "JS_Mem_Shared_Refs")  
  
## <a name="BuiltInValues"></a>Zobrazit předdefinované objekty  
 Ve výchozím nastavení jsou zobrazení dominantních objektů a typů zobrazeny pouze objekty, které vytvoříte ve vaší aplikaci. To vám pomůže vyfiltrovat nepotřebné informace a izolovat problémy související s aplikacemi. V některých případech ale může být užitečné zobrazit všechny objekty, které modul runtime jazyka JavaScript generuje pro vaši aplikaci.  
  
 Chcete-li zobrazit tyto objekty, vyberte možnost **Zobrazit předdefinované** v ![rozevíracím&#45;seznamu nastavení seznamu nastavení v části analyzátor paměti](../profiling/media/js-mem-settings.png "JS_Mem_Settings") v pravém horním rohu podokna.  
  
## <a name="Save"></a>Uložit soubory diagnostické relace  
 Souhrny snímků diagnostiky a jejich související zobrazení podrobností se ukládají jako soubory. diagsession. **Průzkumník řešení** zobrazuje předchozí diagnostické relace ve složce relace diagnostiky. V **Průzkumník řešení**můžete otevřít předchozí relace nebo soubory odebrat nebo přejmenovat.  
  
## <a name="JSConsoleCommands"></a>Přidružit zdrojový kód k datům využití paměti  
 Pro snazší izolaci oddílu kódu, který má problém s pamětí, použijte následující metody:  
  
- Vyhledejte názvy tříd a ID pro prvky modelu DOM v zobrazení Details a Differential.  
  
- Vyhledejte řetězcové hodnoty v zobrazení podrobností a rozdílů, které mohou být přidruženy ke zdrojovému kódu.  
  
- Pomocí příkazu [najít objekt v rámci stromu objektu](#ShowInRootsView) můžete projít strom objektů. To může přispět k identifikaci přidruženého zdrojového kódu.  
  
- Přidejte příkazy analyzátoru paměti do zdrojového kódu.  
  
  Ve zdrojovém kódu můžete použít následující příkazy:  
  
- `console.takeHeapSnapshot` převezme snímek haldy, který se zobrazí v analyzátoru paměti JavaScriptu. Tento příkaz je jedním z [příkazů konzoly JavaScriptu](../debugger/javascript-console-commands.md).  
  
- `performance.mark` nastaví uživatelskou značku (Obrácený trojúhelník), která se zobrazí na časové ose grafu paměti v zobrazení souhrnu, zatímco je aplikace spuštěná. Tento příkaz přebírá jeden řetězcový argument, který popisuje událost a zobrazuje se jako popis v grafu paměti. Tento popis nesmí být delší než 100 znaků.  
  
> [!TIP]
> Použijte `console.takeHeapSnapshot` k urychlení analýzy při opakujících se scénářích použití paměti.  
  
 Tyto příkazy vyvolávají výjimku, pokud je přidáte do aplikace a spustíte aplikaci mimo nástroj JavaScript Memory Analyzer. Můžete ale otestovat, zda tyto příkazy existují, než je použijete. (Příkazy neexistují v počáteční fázi spuštění relace.) Chcete-li ověřit, zda lze `takeHeapSnapshot`bezpečně volat, použijte tento kód:  
  
```javascript  
if (console && console.takeHeapSnapshot) {  
    console.takeHeapSnapshot();  
}  
```  
  
 Chcete-li ověřit, zda lze `performance.mark`bezpečně volat, použijte tento kód:  
  
```javascript  
if (performance && performance.mark) {  
    performance.mark("message_string");  
}  
  
```  
  
 Zde je graf paměti s několika uživatelskými značkami a popisem pro aktuálně vybranou značku uživatele, pro který je argument `performance.mark` řetězec nastaven na "vygenerovaná data":  
  
 ![Použití značky Profile](../profiling/media/js-mem-performance-marks.png "JS_Mem_Performance_Marks")  
  
## <a name="Tips"></a>Tipy pro identifikaci problémů s pamětí  
  
- Sledujte pracovní postup, který je popsaný v části [izolování nevracení paměti](#Isolate) a použití **objektů zbývajících z snímku #\<číslo >** filtru v zobrazení rozdílů k identifikaci pravděpodobných kandidátů na nevracení paměti.  
  
- Chcete-li zjistit, kde je objekt v hierarchii paměti odkazován, použijte [hledání objektu ve stromu objektů](#ShowInRootsView) . Zobrazení kořenových adresářů ukazuje, jak je objekt rootem globálního objektu, což by zabránilo uvolňování paměti.  
  
- V případě obtížné identifikace příčiny problému s pamětí použijte různá zobrazení (například dominantní objekty a typy) k vyhledání commonalities, zejména k identifikaci jednoho objektu (nebo několika objektů), který může obsahovat odkazy na mnoho ostatních objektů, které se zobrazí v zobrazení.  
  
- Hledejte objekty, které se nechtěně uchovávají v paměti, poté, co uživatel přejde na novou stránku, což je běžná příčina problémů s pamětí. Příklad:  
  
  - Nesprávné použití [adresy URL. ](https://msdn.microsoft.com/library/windows/apps/hh453196.aspx)Tato chyba může být způsobena funkcí CreateObjectUrl.  

  - Některé objekty můžou poskytovat `dispose` metodu a doporučení pro použití. Například byste měli volat `dispose` v [WinJS. Binding. list](https://msdn.microsoft.com/library/windows/apps/Hh700774.aspx) , pokud zavoláte metodu `createFiltered` seznamu a potom opustíte stránku.  

  - Možná budete muset odebrat jednu nebo více posluchačů událostí. Další informace najdete v tématu [zobrazení posluchačů událostí modelu DOM](../debugger/view-dom-event-listeners.md).  
  
- Podívejte se na druhou část [tohoto videa](https://channel9.msdn.com/Events/Build/2013/3-316) ze konferenci Build 2013 o programu JavaScript Memory Analyzer.  
  
- Přečtěte si téma [Správa paměti v aplikacích pro Windows Store](https://msdn.microsoft.com/magazine/jj651575.aspx).  
  
- Zvažte dočasné úpravy kódu pro izolaci problémů. Můžete například potřebovat:  
  
  - Použijte příkazy pro analyzátor paměti `console.takeSnapshot` a `performance.mark`. (Viz [přidružení zdrojového kódu k datům využití paměti](#JSConsoleCommands).)  

    Pomocí těchto příkazů můžete izolovat problémy, které nelze izolovat, ručním vytvořením snímku haldy.  

  - Vytvořte testovací objekt a sledujte ho v zobrazeních analyzátoru paměti JavaScriptu, jako je například zobrazení typů. Například můžete připojit velmi velký objekt k jinému objektu, abyste viděli, zda určitý objekt nebo prvek byl uvolněn do paměti.  

## <a name="see-also"></a>Viz také  
 [Návod: Vyhledání nevrácené paměti (JavaScript)](../profiling/walkthrough-find-a-memory-leak-javascript.md)
