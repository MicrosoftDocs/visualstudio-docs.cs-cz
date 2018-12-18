---
title: Paměti jazyka JavaScript | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
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
manager: ghogen
ms.openlocfilehash: b2341e9cf0ca1494d8dad79cd521c283c2c23a06
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51798934"
---
# <a name="javascript-memory"></a>Paměti jazyka JavaScript
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Analyzátor paměti jazyka JavaScript je k dispozici v sadě Visual Studio, které vám pomohou porozumět využití paměti a najít nevracení paměti v aplikacích Store vytvořená pro Windows pomocí jazyka JavaScript. Podporované aplikace patří aplikace pro Windows Phone Store a Windows Store.  
  
 Analyzátor paměti jazyka JavaScript můžete využít tyto věci:  
  
- Vám pomůžou rychle najít paměti problémy využití ve vaší aplikaci kdy se klade důraz nejdůležitější data.  
  
   Získání těchto dat ve snímku souhrny, které ukazují rozdíly mezi dvěma snímky a poskytují odkazy na podrobnější zobrazení.  
  
- Zadejte zobrazení dominantních objektů, typy a kořenové adresáře, které vám pomůžou izolovat problémy.  
  
- Snižte-užitečné informace v datech haldy jazyka JavaScript.  
  
   Objekty, které nejsou vytvořené přímo v kódu vaší aplikace automaticky filtrují. Data můžete také filtrovat podle názvu objektu.  
  
  Kurz vás provede procesem identifikaci nevracení paměti v aplikaci funkční, najdete v tématu [návod: Vyhledání nevrácené paměti (JavaScript)](../profiling/walkthrough-find-a-memory-leak-javascript.md).  
  
  V tomto tématu:  
  
  [Spustit analýzu paměti jazyka JavaScript](#Run)   
  [Zkontrolujte využití paměti](#Check)   
  [Zjištění nevracení paměti](#Isolate)   
  [Zobrazení souhrnu využití paměti za provozu](#LiveMemory)   
  [Zobrazit souhrn snímku](#SnapshotSummary)   
  [Zobrazit podrobnosti o snímku](#SnapshotDetails)   
  [Zobrazit snímek diff](#SnapshotDiff)   
  [Zobrazit objekty podle dominantního objektu](#FoldObjects)   
  [Filtrování dat podle identifikátoru](#Filter)   
  [Najít objekt ve stromu objektů](#ShowInRootsView)   
  [Zobrazit odkazy na sdílené objekty](#References)   
  [Zobrazit předdefinované objekty](#BuiltInValues)   
  [Uložit soubory relací diagnostiky](#Save)   
  [Přidružit zdrojového kódu s daty o využití paměti](#JSConsoleCommands)   
  [Tipy k identifikaci problémů s pamětí](#Tips)  
  
##  <a name="Run"></a> Spustit analýzu paměti jazyka JavaScript  
 Analyzátor paměti můžete použít, když máte funkční aplikaci Windows Store, otevřete v sadě Visual Studio nebo nainstalovat na počítač, na kterém běží [!INCLUDE[win8](../includes/win8-md.md)] nebo novější.  
  
#### <a name="to-run-the-memory-analyzer"></a>Chcete-li spustit analýzu paměti  
  
1.  Otevřít Visual Studio.  
  
2.  Pokud spouštíte aplikaci z aplikace Visual Studio v **spustit ladění** seznamu **standardní** nástrojů vyberte cíl ladění pro projekt: buď emulátor Windows Phone nebo aplikace pro Windows Store, **Místního počítače**, **simulátor**, nebo **vzdálený počítač**.  
  
     Další informace o těchto možnostech najdete v tématu [spouštění aplikací v sadě Visual Studio](../debugger/run-store-apps-from-visual-studio.md).  
  
3.  V panelu nabídky zvolte **ladění**, **Profiler výkonu...** .  
  
     Ve výchozím nastavení se analyzují aktuální spouštěcí projekt. Pokud chcete změnit cíl analýzy, zvolte **změnit cíl**.  
  
     ![Změnit cíl analýzy](../profiling/media/js-tools-target.png "JS_Tools_Target")  
  
     Tyto možnosti jsou k dispozici pro cíl analýzy:  
  
    -   **Projekt po spuštění**. Analyzuje aktuální spouštěcí projekt. Pokud aplikaci spouštíte ve vzdáleném počítači, je třeba zvolit tuto možnost, což je výchozí hodnota.  
  
    -   **Spuštění aplikace**. Umožňuje vybrat aplikaci Windows Store ze seznamu spuštěných aplikací. Tuto možnost nelze použít, když aplikaci spouštíte ve vzdáleném počítači.  
  
         Tuto možnost použijte k analýze využití paměti aplikací, které jsou spuštěny v počítači, pokud nemáte přístup ke zdrojovému kódu.  
  
    -   **Nainstalované aplikace**. Umožňuje vybrat nainstalované aplikace Windows Store, který chcete analyzovat. Tuto možnost nelze použít, když aplikaci spouštíte ve vzdáleném počítači.  
  
         Tuto možnost použijte k analýze využití paměti aplikací, které jste nainstalovali v počítači, pokud nemáte přístup ke zdrojovému kódu. Tato možnost může být také užitečné, chcete-li pouze k analýze využití paměti libovolné aplikace mimo vývoje aplikací.  
  
4.  Z **dostupných nástrojů**, vyberte **paměti jazyka JavaScript** zaškrtněte políčko a klikněte na tlačítko **Start**.  
  
5.  Při spuštění analyzátoru paměti může vyžádat okno Řízení uživatelských účtů ke spuštění Collector.exe trasování událostí pro Windows Visual Studio. Zvolte **Ano**.  
  
     Interakci s aplikací k otestování scénářů využití paměti relevantní a zobrazení grafu paměti, jak je popsáno v následujících částech.  
  
6.  Přepnout do sady Visual Studio stisknutím klávesy Alt + Tab.  
  
7.  Chcete-li zobrazit data, která shromažďuje analyzátoru paměti, zvolte **trvat snímek haldy**. Zobrazit [zobrazit souhrn snímku](#SnapshotSummary) dále v tomto tématu.  
  
##  <a name="Check"></a> Zkontrolujte využití paměti  
 Můžete k identifikaci nevracení paměti pomocí různá zobrazení v analyzátoru paměti JavaScriptu. Pokud již máte podezření, že vaše aplikace není vracena paměť, přečtěte si téma [izolovat nevracení paměti](#Isolate) navrhované pracovního postupu.  
  
 K identifikaci nevracení paměti v aplikaci použijte následující zobrazení:  
  
-   [Zobrazení souhrnu využití paměti za provozu](#LiveMemory). Pomocí grafu využití paměti můžete hledat náhlé zvýšení využití paměti nebo průběžně zvýšení využití paměti, která je výsledkem konkrétní akce. Souhrnné zobrazení využití paměti za provozu můžete pořizovat snímky haldy. Snímky se zobrazí jako kolekci v části grafu využití paměti.  
  
    > [!TIP]
    >  Špička využití paměti se zobrazí při pořídíte snímek. Pomocí snímku souhrny pro přesnější údaj o růstu.  
  
-   [Zobrazit souhrn snímku](#SnapshotSummary). Můžete zobrazit souhrnné informace snímku během nebo po relaci profilace paměti. Odkaz na podrobnosti o snímku a rozdílové zobrazení snímků pomocí souhrny snímku.  
  
    > [!TIP]
    >  Snímek diff zobrazení obvykle poskytne velmi užitečné informace o nevracení paměti.  
  
-   [Zobrazit podrobnosti snímku](#SnapshotDetails). Zobrazí podrobné informace o data o využití paměti pro jeden snímek.  
  
-   [Zobrazit snímek diff](#SnapshotDiff). Zobrazuje rozdílové hodnoty mezi snímky. Tato zobrazení zobrazit rozdíly v objektu počty velikost a objekt.  
  
##  <a name="Isolate"></a> Zjištění nevracení paměti  
 Tyto kroky obsahují pracovního postupu, které můžou pomoct efektivněji používat analýzu paměti jazyka JavaScript. Tyto kroky může být užitečné, pokud se domníváte, že se vaše aplikace může nevracení paměti. Kurz vás provede procesem identifikaci nevracení paměti v aplikaci funkční, najdete v tématu [návod: Vyhledání nevrácené paměti (JavaScript)](../profiling/walkthrough-find-a-memory-leak-javascript.md).  
  
1. Otevření aplikace v sadě Visual Studio.  
  
2. Spusťte analýzu paměti jazyka JavaScript. Další informace najdete v tématu [spustit analýzu paměti jazyka JavaScript](#Run).  
  
3. Spuštění vaší aplikace prostřednictvím scénář, který chcete testovat. Například scénář může zahrnovat velké mutace modelu DOM, při načtení konkrétní stránky, nebo při spuštění aplikace.  
  
4. Opakujte tento scénář 1 – 4 dalších místech.  
  
   > [!TIP]
   >  Opakováním testovací scénář několikrát, může pomoci, ujistěte se, že inicializace práci je možné filtrovat mimo výsledky.  
  
5. Přepněte do aplikace Visual Studio (stisknutím klávesy Alt + Tab).  
  
6. Pořídit snímek haldy směrného plánu výběrem **trvat snímek haldy**.  
  
    Následující obrázek znázorňuje příklad snímek směrného plánu.  
  
    ![Snímek směrného plánu](../profiling/media/js-mem-leak-workflow-baseline.png "JS_Mem_Leak_Workflow_Baseline")  
  
   > [!TIP]
   >  Pro přesnější kontrolu nad časování snímky, můžete použít [přidružit zdrojového kódu s daty o využití paměti](#JSConsoleCommands) příkaz v kódu.  
  
7. Přepnout do vaší aplikace a opakujte scénář testování (pouze jednou znovu).  
  
8. Přepněte do aplikace Visual Studio a vytvořte druhý snímek.  
  
9. Přepnout do vaší aplikace a opakujte scénář testování (pouze jednou znovu).  
  
10. Přepněte do aplikace Visual Studio a vytvořte třetí snímek.  
  
     Následující obrázek znázorňuje příklad druhý a třetí snímek.  
  
     ![Druhý a třetí snímek](../profiling/media/js-mem-leak-workflow.png "JS_Mem_Leak_Workflow")  
  
     Provedením směrný plán, druhý a třetí snímku v tomto pracovním postupu se dá odfiltrovat změny, které nejsou přidruženy k nevracení paměti snadněji. Například může být očekávané změny, jako je aktualizace záhlaví a zápatí stránky, které budou generovat některé změny využití paměti, ale pravděpodobně nemá vztah k nevracení paměti.  
  
11. Třetí snímek zvolte odkaz na jedno z rozdílové zobrazení:  
  
    - Velikost rozdílové haldy (levý odkaz pod velikost haldy). Text odkazu zobrazuje rozdíl mezi velikost haldy aktuální snímek a velikost haldy z předchozího snímku.  
  
    - Počet rozdílové objektů (pravém odkaz pod počet objektů). Text odkazu zobrazuje dvě hodnoty (například +1858 /-1765): první hodnota je číslo nové objekty přidané od předchozího snímku, a druhá hodnota je počet objektů odebraných od předchozího snímku.  
  
      Tyto odkazy otevřít zobrazení podrobností rozdílové snímku typy v haldě, seřazené podle uchovávané velikosti nebo počet objektů, v závislosti na tom, které jste otevřeli.  
  
12. Vyberte jednu z následujících **oboru** možnosti vám pomůže identifikovat problémy s pamětí použití filtru:  
  
    -   **Objekty přetrvávající ze snímku č. 2**.  
  
    -   **Objekty přidané mezi snímku č. 2 a #3**  
  
    > [!TIP]
    >  Pomocí filtrované zobrazení objekty přetrvávající ze snímku předchozí nevracení paměti prozkoumat. Například, pokud je počet objektů rozdílové +205 /-195, toto zobrazení zobrazí 10 objekty zbyly a jedná se pravděpodobně kandidáty na nevracení paměti.  
  
     Následující obrázek znázorňuje rozdílové zobrazení objekty přetrvávající ze snímku č. 2.  
  
     ![Snímek diff zobrazení typů](../profiling/media/js-mem-snapshot-diff.png "JS_Mem_Snapshot_Diff")  
  
     Na předchozím obrázku uvidíme, že jsou dva objekty přetrvávající z předchozího snímku. Zjistěte, zda se jedná o očekávané chování u konkrétní aplikace. Pokud ne, může to naznačovat nevracení paměti.  
  
13. Pokud chcete zobrazit, ve kterém jsou objekty v rozdílových zobrazeních root na globální objekt, který brání je prováděno uvolnění paměti, otevřete místní nabídku pro objekt a klikněte na tlačítko **zobrazit v zobrazení kořenů**. Může uchovávat velký počet objektů v paměti, protože se na ně odkazuje jeden objekt (nebo několik objektů), který se zobrazuje na globální objekt.  
  
14. Pokud existuje příliš mnoho objektů v zobrazení objektů, které zbyly, zkuste dále izolovat období, ve kterém dochází k nevracení paměti a potom pro opakování tři snímky. Chcete-li dále izolovat nevracení paměti, použijte [přidružit zdrojového kódu s daty o využití paměti](#JSConsoleCommands), [přidružit zdrojového kódu s daty o využití paměti](#JSConsoleCommands)a dalších dat o využití paměti v analyzátoru paměti k dispozici.  
  
##  <a name="LiveMemory"></a> Zobrazení souhrnu využití paměti za provozu  
 Souhrnné zobrazení využití paměti za provozu poskytuje grafu využití paměti pro spuštěnou aplikaci a kolekce všechny dlaždice souhrnu snímku. V tomto zobrazení můžete provádět základní úkoly, jako je pořizování snímků, analyzuje souhrnné informace a navigace s dalšími zobrazeními. Při zastavení shromažďování dat paměti grafu zmizí a zobrazí pouze [zobrazit souhrn snímku](#SnapshotSummary) zobrazení.  
  
 Graf paměti zobrazuje okamžitým efektem paměti procesu aplikace, což zahrnuje Nesdílené bajty, nativní paměti a haldu využívanou jazykem JavaScript. Graf paměti je posuvný zobrazení paměti procesu. Zde je, jak to funguje:  
  
 ![Analýzu paměti jazyka JavaScript paměti grafu](../profiling/media/js-mem-memory-graph.png "JS_Mem_Memory_Graph")  
  
 Pokud jste přidali uživatelské značky do kódu aplikace (viz [přidružit zdrojového kódu s daty o využití paměti](#JSConsoleCommands)), obrácenou trojúhelník se zobrazí v grafu využití paměti označuje, kdy je dosaženo příslušné části kódu.  
  
 Některé z paměti zobrazená v grafu paměť je přidělena modulu runtime jazyka JavaScript. Nelze řídit toto využití paměti v aplikaci. Zobrazená v grafu využití paměti zvýší v případě, že je provést první snímek a potom se zvětší minimálně pro každý další snímek.  
  
##  <a name="SnapshotSummary"></a> Zobrazit souhrn snímku  
 K vytvoření snímku aktuálního stavu využití paměti vaší aplikace, zvolte **trvat snímek haldy** z paměti grafu. Souhrnnou dlaždici snímků, které se zobrazí v obou za využití paměti summary (když aplikace běží) a Souhrn snímku (když je aplikace pozastavená), poskytuje informace o haldu využívanou jazykem JavaScript a odkazy na podrobnější informace. Pokud budete postupovat dva nebo více snímků, snímku poskytuje další informace o porovnávání jeho data, která z předchozího snímku.  
  
> [!NOTE]
>  Analyzátor paměti jazyka JavaScript vynutí uvolňování paměti před jednotlivých snímků. To pomáhá zajistit konzistentní výsledky spuštění.  
  
 Tady je příklad snímku souhrnu při trvat několik snímků.  
  
 ![Snímek souhrnu](../profiling/media/js-mem-snapshot-summary.png "JS_Mem_Snapshot_Summary")  
  
 Snímek souhrn obsahuje:  
  
-   Název a časové razítko snímku.  
  
-   Počet potenciální problémy (označený modrou informační ikonu). Toto číslo, pokud jsou k dispozici, identifikuje potenciální problémy s pamětí, jako je například uzly, které nejsou připojené k modelu DOM. Počet odkazy na typy zobrazení snímku, který je seřazený podle typ problému, abyste měli na očích potenciální problémy. Popisek zobrazí popis problému.  
  
-   Velikost haldy. Toto číslo zahrnuje elementy modelu DOM a objekty, které modul runtime jazyka JavaScript se přidá do haldu využívanou jazykem JavaScript. Velikost haldy se odkazy na typy zobrazení snímku.  
  
-   Velikost rozdílové haldy. Tato hodnota ukazuje rozdíl mezi velikost haldy aktuální snímek a velikost haldy z předchozího snímku. Hodnota je následován červená šipka, pokud se zvýší paměti nahoru nebo zelená šipka dolů při snížení paměti. Pokud velikost haldy nedošlo ke změně mezi snímky, zobrazí se text **beze změny** místo čísla. Pro první snímkem, se zobrazí text **směrného plánu**. Velikost rozdílové haldy odkazy na typy zobrazení snímku rozdíl  
  
-   Počet objektů. Tento počet se zobrazí pouze objekty vytvořené v aplikaci a filtry předdefinované objekty, které Autor modulu runtime jazyka JavaScript. Objekt počet obsahuje odkazy na typy zobrazení Podrobnosti o snímku.  
  
-   Počet rozdílové objektů. To ukazuje dvě hodnoty: první hodnota je číslo nové objekty přidány od předchozí snímek; a druhá hodnota je počet objektů odebraných od předchozího snímku. Například na ilustraci, že byly přidány 1,859 objekty a 1,733 objekty byly odebrány od snímek č. 1. Tyto informace je a červená šipka nahoru Pokud zvýšil počet celkový počet objektů nebo zelenou šipku dolů, je-li se zkrátila. Pokud nedošlo ke změně počet objektů, zobrazí se text **beze změny** místo čísla. Pro první snímkem, se zobrazí text **směrného plánu**. Počet propojení rozdílové objektů na typy zobrazení snímku rozdíl  
  
-   Snímek obrazovky v době pořízení snímku.  
  
##  <a name="SnapshotDetails"></a> Zobrazit podrobnosti o snímku  
 Podrobné informace o využití paměti u jednotlivých snímků můžete zobrazit v zobrazení Podrobnosti o snímku.  
  
 V souhrnném zobrazení snímku zvolte odkaz zobrazíte podrobnosti o snímku. Například odkaz velikost haldy otevře snímek, který ve výchozím nastavení otevírat podrobnosti o typech zobrazení.  
  
 Tento obrázek ukazuje typy zobrazení v podrobnosti snímku, s daty o využití paměti, seřazené podle uchovávané velikosti.  
  
 ![Zobrazení snímku podrobností zobrazuje potenciálních problémů](../profiling/media/js-mem-snapshot-details.png "JS_Mem_Snapshot_Details")  
  
 V podrobném zobrazení snímku můžete zkontrolovat výběrem možnosti z panelu nástrojů dat o využití paměti podle dominantního objektu, root nebo typu:  
  
- **Typy**. Ukazuje instanci počet a celkovou velikost objektů v haldě, seskupené podle typu objektu. Ve výchozím nastavení ty jsou seřazené podle počtu instancí.  
  
  > [!TIP]
  >  Obvykle rozdílových zobrazeních typů na objekt haldy jsou nejužitečnější zobrazení pro identifikaci nevracení paměti; Tato zobrazení nabízejí **oboru** filtr vám pomůže identifikovat přes objekty vlevo.  
  
- **Kořeny**. Nachází hierarchické zobrazení objektů z kořenové objekty prostřednictvím podřízené odkazy. Ve výchozím nastavení podřízené uzly jsou seřazené podle uchovávané velikosti sloupce, s největší v horní části.  
  
- **Dominantní objekty**. Zobrazí seznam objektů v haldě, které mají exkluzivní odkazy na jiné objekty. Dominantní objekty jsou seřazené podle uchovávané velikosti.  
  
  > [!TIP]
  >  Když odeberete dominantního objektu z paměti, získáte zpět všechny paměti, který uchovává objekt. Pro několik aplikací zobrazení dominantních objektů může pomoci objasnit paměti uchovávané velikosti, protože můžete prozkoumat kompletní objekt řetězce odkazů.  
  
  Všechny tři zobrazení zobrazit podobné typy hodnot, včetně:  
  
- **Identifikátory**. Název, který nejlépe identifikuje objekt. Například pro prvky jazyka HTML podrobnosti snímku zobrazit hodnota atributu ID, pokud používá.  
  
- **Typ**. Typ objektu (například prvek odkazu HTML nebo div element).  
  
- **Velikost**. Velikost objektu, nikoli včetně velikosti všechny odkazované objekty.  
  
- **Uchovávané velikosti**. Velikost objektu včetně velikosti všech podřízených objektů, které mají bez nadřazených. Pro účely praktické Toto je množství paměti, které uchovávají objektem, takže při odstranění objektu uvolnit zadaného množství paměti.  
  
- **Počet**. Počet instancí objektů. Tato hodnota se zobrazí jenom v zobrazení typů.  
  
##  <a name="SnapshotDiff"></a> Zobrazit snímek diff  
 V analyzátoru paměti JavaScriptu můžete porovnat snímku s předchozím snímkem v rozdílových zobrazeních snímku.  
  
 V souhrnném zobrazení snímku můžete zobrazit podrobnosti snímku rozdílové výběrem velikost rozdílové haldy nebo rozdílové objekt počet odkazů po dvou nebo více snímků byla přijata.  
  
 Můžete zobrazit rozdílové informace o typech, kořeny a dominantních objektů. Snímek diff zobrazuje informace, jako jsou objekty, které byly přidány do haldy mezi dvěma snímky.  
  
 Tento obrázek ukazuje zobrazení typů ve snímku rozdíl  
  
 ![Snímek diff zobrazení typů](../profiling/media/js-mem-snapshot-diff.png "JS_Mem_Snapshot_Diff")  
  
 V okně snímek diff zobrazení dominantních objektů, typy a kořenové adresáře jsou stejné jako v [zobrazit podrobnosti snímku](#SnapshotDetails) okna. Snímek diff zobrazuje stejné informace jako podrobnosti snímku, s následující hodnoty:  
  
- **Rozdíl velikosti**. Rozdíl mezi velikost objektu v aktuálním snímku a jeho velikost v předchozím snímkem, nezahrnuje velikost všechny odkazované objekty.  
  
- **Rozdíl velikosti uchovávají**. Rozdíl uchovávané velikosti objektu v aktuálním snímku a jeho uchovávané velikosti v předchozím snímkem. Uchovávané velikosti zahrnuje velikost objektů včetně velikosti všech jeho podřízených objektů, které mají bez nadřazených. V zájmu praktické uchovávané velikosti je množství paměti, které uchovávají objektem, takže při odstranění objektu uvolnit zadaného množství paměti.  
  
  Chcete-li filtrovat rozdílové informace mezi snímky, vyberte jednu z **oboru** filtrů v horní části rozdílové zobrazení.  
  
- **Objekty přetrvávající ze snímku č\<číslo >**. Tento filtr ukazuje rozdíl mezi objekty do haldy přidávají nebo odebírají z haldy ve srovnání s referenčním snímkem a předchozí snímek. Například, pokud snímku souhrn zobrazuje +205 /-195 v počet objektů, tento filtr se seznámíte deset objekty, které byly přidány, ale neodeberou.  
  
  > [!TIP]
  >  K zobrazení velmi užitečné informace v tomto filtru, postupujte podle kroků popsaných v [izolovat nevracení paměti](#Isolate).  
  
- **Objekty přidané mezi snímek č\<číslo > a #\<číslo >**. Tento filtr zobrazí všechny objekty do haldy z předchozího snímku.  
  
- **Všechny objekty ve snímku č\<číslo >**. Toto nastavení filtru není odfiltrovat všechny objekty do haldy.  
  
  Chcete-li zobrazit odkazy na objekty, které se neshodují. aktuální **oboru** filtr, vyberte **zobrazit neshodné odkazy** v seznamu nastavení ![nastavení rozevírací&#45;dolů seznam v analyzátoru paměti ](../profiling/media/js-mem-settings.png "JS_Mem_Settings") v pravém horním rohu podokna. Pokud povolíte toto nastavení, neodpovídající odkazy se zobrazí s textem šedá.  
  
> [!TIP]
>  Doporučujeme, abyste postupovali podle kroků v [izolovat nevracení paměti](#Isolate) a pak použít objekty zbyly **oboru** filtr k identifikaci objektů, které jsou nevrácení paměti.  
  
##  <a name="FoldObjects"></a> Zobrazit objekty podle dominantního objektu  
 V zobrazení typů a dominantních objektů vyberte, jestli se má zobrazit objekty složeny do jejich dominantních objektů (Toto je výchozí zobrazení dominantních objektů kartě). Pokud je vybráno toto zobrazení, pouze dominantních objektů jsou uvedeny v zobrazení nejvyšší úrovně objektů. (Objekty, které jsou potomky – globální objekty jsou skryté zobrazení nejvyšší úrovně.) U některých aplikací to vysvětlit objektů, které způsobují nevracení paměti díky snížení šumu v datech.  
  
 Chcete-li přepnout zobrazení objektů podle dominantního objektu, zvolte **přeložte na objekty podle dominantního objektu** tlačítko. ![Skládání objektů do jejich dominantních objektů](../profiling/media/js-mem-fold-objects.png "JS_Mem_Fold_Objects")  
  
 Další informace o dominantních objektů naleznete v tématu [zobrazit podrobnosti snímku](#SnapshotDetails).  
  
##  <a name="Filter"></a> Filtrování dat podle identifikátoru  
 V zobrazení dominantních objektů a typy můžete filtrovat data tak, že konkrétní identifikátory. K vyhledání identifikátoru, stačí zadat jeho název **filtr identifikátorů** textového pole v pravém horním rohu. Když začnete psát, identifikátory, které neobsahují zadané znaky, budou odfiltrovány.  
  
 Každé zobrazení má svůj vlastní filtr tak filtr se zachová, i když můžete přepnout do jiného zobrazení.  
  
##  <a name="ShowInRootsView"></a> Najít objekt ve stromu objektů  
 V zobrazení typů a dominantních objektů můžete zobrazit relace pro daný objekt `Global` objektu. Objekty root na `Global` objekt nebude uklizena modulem. Známý objekt můžete snadno vyhledat v zobrazení kořenů bez prohledávat `Global` strom objektů. Provedete to tak, otevřete místní nabídku pro objekt v dominantních objektů nebo zadejte zobrazení a klikněte na tlačítko **zobrazit v zobrazení kořenů**.  
  
##  <a name="References"></a> Zobrazit odkazy na sdílené objekty  
 V zobrazení typů a dominantních objektů dolním podokně obsahuje seznam odkazů na objekt zobrazující sdílené odkazy. Při výběru objektu v horním podokně seznam odkazů na objekt zobrazí všechny objekty, které odkazují na tento objekt.  
  
> [!NOTE]
>  Cyklické odkazy jsou uvedeny hvězdičkou (*) a informační popisek a nelze rozšířit. By se jinak, zabránit vám v procházení stromu odkaz a identifikaci objektů, které se zachováním paměti.  
  
 Pokud chcete další pomoc určení ekvivalentních objektů, zvolte **zobrazit ID objektů** v seznamu nastavení ![nastavení rozevírací&#45;dolů seznam v analyzátoru paměti](../profiling/media/js-mem-settings.png "JS_Mem_Settings ") v pravém horním rohu v horním podokně. Tato možnost zobrazuje ID objektů vedle názvů objektů v **identifikátory** seznamu (ID se zobrazí ve všech zobrazeních, ne jenom odkazy na seznamu objektů). Objekty, které mají stejné ID. jsou sdílené odkazy.  
  
 Seznam odkazů na objekt pro vybranou položku s ID zobrazí na následujícím obrázku.  
  
 ![Objekt odkazy s zobrazené ID](../profiling/media/js-mem-shared-refs.png "JS_Mem_Shared_Refs")  
  
##  <a name="BuiltInValues"></a> Zobrazit předdefinované objekty  
 Ve výchozím zobrazení dominantních objektů a typy zobrazit pouze objekty, které vytvoříte ve vaší aplikaci. To vám pomůže vyfiltrovat nepotřebné informace a izolovat problémy související s aplikacemi. Ale v některých případech může být užitečné, chcete-li zobrazit všechny objekty, které generuje modul runtime jazyka JavaScript pro vaši aplikaci.  
  
 Chcete-li zobrazit tyto objekty, zvolte **zobrazit předdefinované** v seznamu nastavení ![nastavení rozevírací&#45;dolů seznam v analyzátoru paměti](../profiling/media/js-mem-settings.png "JS_Mem_Settings") v pravém horním rohu horním podokně.  
  
##  <a name="Save"></a> Uložit soubory relací diagnostiky  
 Shrnutí diagnostiky snímku a jejich přidružené podrobnosti zobrazení jsou uloženy jako soubory .diagsession. **Průzkumník řešení** předchozí relace diagnostiky se zobrazí ve složce relace diagnostiky. V **Průzkumníka řešení**, otevřete předchozí relace, odebrat nebo přejmenovat soubory.  
  
##  <a name="JSConsoleCommands"></a> Přidružit zdrojového kódu s daty o využití paměti  
 Snažte se určit části kódu, který má problém s paměti, použijte následující metody:  
  
- Hledat názvy tříd a ID pro elementy modelu DOM do podrobností a rozdílové zobrazení.  
  
- Vyhledejte řetězcové hodnoty na podrobnosti a rozdílové zobrazení, které mohou být přidruženy zdrojového kódu.  
  
- Použití [vyhledání objektu v rámci stromů objektů](#ShowInRootsView) příkazu nahoru stromem objektů. To může pomoct identifikovat přidružený zdrojový kód.  
  
- Přidání příkazů analyzátoru paměti pro váš zdrojový kód.  
  
  Ve zdrojovém kódu můžete použít následující příkazy:  
  
- `console.takeHeapSnapshot` pořídí snímek haldy, které se zobrazí v analyzátoru paměti JavaScriptu. Tento příkaz je jedním z [příkazy konzoly jazyka JavaScript](../debugger/javascript-console-commands.md).  
  
- `performance.mark` Nastaví uživatele mark (inverzní trojúhelník), který se zobrazí na časové ose grafu paměti v souhrnném zobrazení, zatímco je aplikace spuštěna. Tento příkaz má jeden argument řetězec, který popisuje události a se zobrazí jako popisek v grafu paměti. Tento popis nesmí překročit 100 znaků.  
  
> [!TIP]
>  Použití `console.takeHeapSnapshot` pro urychlení analýzy při opakování scénáře využití paměti.  
  
 Tyto příkazy vyvolat výjimku, pokud je přidat do vaší aplikace a spusťte aplikaci mimo analýzu paměti jazyka JavaScript. Však můžete zkontrolovat, jestli existují příkazy před jejich použitím. (Příkazy neexistují v rané fázi fáze spuštění relace.) Chcete-li zkontrolovat, jestli může bezpečně volat `takeHeapSnapshot`, použijte tento kód:  
  
```javascript  
if (console && console.takeHeapSnapshot) {  
    console.takeHeapSnapshot();  
}  
```  
  
 Chcete-li zkontrolovat, jestli může bezpečně volat `performance.mark`, použijte tento kód:  
  
```javascript  
if (performance && performance.mark) {  
    performance.mark("message_string");  
}  
  
```  
  
 Tady je graf paměti s několika uživatelskými značkami a popis pro značku aktuálně vybraného uživatele, pro kterou `performance.mark` argument řetězec je nastaven na "data generovaná":  
  
 ![Pomocí profilu označit](../profiling/media/js-mem-performance-marks.png "JS_Mem_Performance_Marks")  
  
##  <a name="Tips"></a> Tipy k identifikaci problémů s pamětí  
  
-   Postupujte podle pracovní postup popsaný v [izolovat nevracení paměti](#Isolate) a použít **objekty přetrvávající ze snímek č\<číslo >** filtru v rozdílovém zobrazení k identifikaci pravděpodobně kandidáty na nevracení paměti.  
  
-   Použití [vyhledání objektu v rámci stromů objektů](#ShowInRootsView) zobrazíte, kde se odkazuje objekt v paměti hierarchie. Zobrazení kořenů ukazuje, jak je objekt root na globální objekt, který by brání jeho uvolnění paměti.  
  
-   Když je obtížné určit příčinu problému paměti, použijte různá zobrazení (jako je například dominantních objektů a typy) k vyhledání commonalities, zejména vám pomůže identifikovat jeden objekt (nebo několik objektů), která mohou obsahovat odkazy na řadu dalších objektů, které se zobrazují v zobrazení.  
  
-   Hledejte objekty, které jsou zachovány v paměti neúmyslně po Uživatel přešel na novou stránku, což je běžné příčiny problémů s pamětí. Příklad:  
  
    -   Nesprávné použití [adresy URL. CreateObjectUrl](http://msdn.microsoft.com/library/windows/apps/hh453196.aspx) funkce může způsobit potíže.  
  
    -   Některé objekty můžou poskytovat `dispose` metoda a doporučení pro použití. Například byste měli volat `dispose` na [WinJS.Binding.List](http://msdn.microsoft.com/library/windows/apps/Hh700774.aspx) při volání v seznamu `createFiltered` metody a pak stránku opustit.  
  
    -   Můžete potřebovat k odebrání jedné nebo víc naslouchacích procesů událostí. Další informace najdete v tématu [naslouchacích procesů událostí DOM zobrazení](../debugger/view-dom-event-listeners.md).  
  
-   Podívejte se na druhé části [toto video](http://channel9.msdn.com/Events/Build/2013/3-316) z konference Build 2013 o analýzu paměti jazyka JavaScript.  
  
-   Čtení [správě paměti v aplikacích pro Windows Store](http://msdn.microsoft.com/magazine/jj651575.aspx).  
  
-   Vezměte v úvahu dočasná změna kódu k izolování problémů. Například můžete chtít:  
  
    -   Pomocí příkazů pro analyzátor paměti `console.takeSnapshot` a `performance.mark`. (Viz [přidružit zdrojového kódu s daty o využití paměti](#JSConsoleCommands).)  
  
         Můžete použít tyto příkazy a určit tak problémy, které nelze izolovat ručně provedením snímek haldy.  
  
    -   Vytvořte objekt testu a sledovat v zobrazeních analyzátoru paměti JavaScriptu, jako jsou typy zobrazení. Například můžete připojit velmi velké objekty na jiný objekt, pokud chcete zobrazit, zda určitý objekt nebo element byla uvolněna.  
  
## <a name="see-also"></a>Viz také  
 [Návod: Vyhledání nevrácené paměti (JavaScript)](../profiling/walkthrough-find-a-memory-leak-javascript.md)



