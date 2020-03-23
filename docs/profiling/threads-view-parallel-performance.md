---
title: Zobrazení vláken ve vizualizéru souběžnosti | Dokumenty společnosti Microsoft
ms.date: 11/04/2018
ms.topic: conceptual
f1_keywords:
- vs.performance.view.threadblocking
helpviewer_keywords:
- Concurrency Visualizer, Threads View (Parallel Performance)
ms.assetid: 2e441103-a266-407b-88c3-fb58716257a3
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 4382a21a68848a758f3d4cd37a8528722927691c
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "62973748"
---
# <a name="threads-view-in-the-concurrency-visualizer"></a>Zobrazení vláken ve vizualizéru souběžnosti

**Zobrazení vláken** je nejpodrobnější zobrazení s bohatým rysem v vizualizéru souběžnosti. V zobrazení **Vlákna** můžete určit, která vlákna provádějí kód během segmentu spuštění, a analyzovat, zda vlákna jsou spuštěná nebo blokovaná z důvodu synchronizace, vstupně-va nebo z jiných důvodů. **Vlákna** zobrazit sestavy také profil volání zásobníku stromu spuštění a odblokování podprocesů.

Zatímco vlákna jsou spuštěny, Vizualizér souběžnosti shromažďuje vzorky. Když vlákno zastavilo provádění, vizualizér zkontroluje všechny události přepnutí kontextu operačního systému pro vlákno. Přepnutí kontextu může dojít, protože:

- Vlákno je blokováno na primitivní synchronizaci.
- Kvantové vlákno vyprší.
- Vlákno provede požadavek blokování vstupně-v.a.

Souběžnost Visualizer kategorizuje události přepínače vláken a kontextu a prohledává zásobníky volání vláken pro dobře známá blokovací rozhraní API. Zobrazí kategorie vláken v aktivní legendě vlevo dole v zobrazení **Vlákna.** Ve většině případů můžete identifikovat hlavní příčinu blokování události kontrolou zásobníky volání, které odpovídají události přepnutí kontextu.

Pokud neexistuje žádná shoda zásobníku volání, vizualizátor [!INCLUDE[TLA#tla_mswin](../code-quality/includes/tlasharptla_mswin_md.md)]souběžnosti používá důvod čekání poskytnutý . [!INCLUDE[TLA#tla_mswin](../code-quality/includes/tlasharptla_mswin_md.md)] Kategorie však může být založena na podrobnostech implementace a nemusí odrážet záměr uživatele. Například [!INCLUDE[TLA#tla_mswin](../code-quality/includes/tlasharptla_mswin_md.md)] hlásí důvod čekání pro blokování na nativní tenký zámek čtečky a zápisu jako V/V místo synchronizace.

**Zobrazení vláken** také zobrazuje závislosti mezi vlákny. Pokud například identifikujete vlákno, které je blokováno v objektu synchronizace, můžete najít vlákno, které jej odblokovalo. Můžete prozkoumat zásobník volání pro odblokování podprocesu v okamžiku, kdy odblokované druhé.

Zobrazení **Vlákna** můžete použít k:

- Určete důvody, proč uživatelské rozhraní (UI) aplikace nereaguje během určitých fází provádění.
- Určete dobu, kterou strávíte blokováním synchronizace, vstupně-va, chyb stránky a dalších událostí.
- Zjistěte stupeň rušení z jiných procesů, které jsou prováděny v systému.
- Identifikujte problémy vyrovnávání zatížení pro paralelní spuštění.
- Najděte důvody neoptimální nebo neexistující škálovatelnosti. Například proč se výkon paralelní aplikace nezlepší, když jsou k dispozici další logická jádra.
- Pochopit stupeň souběžnosti v aplikaci, které vám pomohou při paralelizaci.
- Identifikujte závislosti mezi pracovními vlákny a kritickými cestami provádění.

## <a name="use-threads-view"></a>Použití zobrazení Vláken

Chcete-li spustit vizualizér souběžnosti, vyberte **možnost Analyzovat** > **vizualizér souběžnosti**a vyberte možnost, například **Spustit nový proces**.

Souběžnost Visualizer spustí aplikaci a shromažďuje trasování, dokud nevyberete **Zastavit kolekci**. Vizualizér pak analyzuje trasování a zobrazí výsledky na stránce sestavy trasování.

Chcete-li otevřít zobrazení **Vlákna,** vyberte kartu **Vlákna** v levém horním rohu sestavy.

![zobrazení vláken](../profiling/media/threadsviewnarrowing.png "zobrazení vláken")

Vyberte časové intervaly a vlákna a spusťte analýzu výkonu.

## <a name="timeline-analysis"></a>Analýza časové osy

Horní část zobrazení **Vlákna** je časová osa. Časová osa zobrazuje aktivitu všech vláken v procesu a všech fyzických diskových zařízení v hostitelském počítači. Zobrazuje také aktivitu GPU a události značky.

Na časové ose je osa x čas a na ose y je několik kanálů:

- Dva vstupně-v., pro každou diskovou jednotku v systému, jeden kanál pro čtení a jeden pro zápisy.
- Kanál pro každé vlákno v procesu.
- Marker kanály, pokud jsou marker události v trasování. Kanály značek se zpočátku zobrazují pod kanály vláken, které tyto události generovaly.
- gpu kanály.

Zpočátku jsou vlákna seřazena v pořadí, ve kterém jsou vytvořeny, takže hlavní vlákno aplikace je první. Vrozené **možnosti seřadit** podle jiného kritéria, například **Spuštění**, vyberte jinou možnost .

Barvy časové osy označují stav vlákna v daném čase. Zelené segmenty jsou spuštěny, červené segmenty jsou blokovány pro synchronizaci, žluté segmenty jsou preempted, a fialové segmenty jsou zapojeny do zařízení V/O.

Chcete-li zobrazit více podrobností, můžete zobrazení podrobností nebo zobrazení delšího časového intervalu oddálit. Vyberte segmenty a body v grafu, abyste získali podrobnosti o kategoriích, časech zahájení, zpožděních a stavech zásobníku volání.

Pomocí časové osy prozkoumejte rovnováhu práce mezi podprocesy, které jsou součástí paralelní smyčky nebo souběžných úloh. Pokud dokončení jednoho vlákna trvá déle než ostatní, práce může být nevyvážená. Můžete zlepšit výkon aplikace tím, že distribuuje práci rovnoměrněji mezi vlákny.

Pokud pouze jedno vlákno je spuštěna v určitém okamžiku, aplikace nemusí být plně využívají souběžnosti v systému. Graf časové osy můžete použít ke kontrole závislostí mezi vlákny a časové vztahy mezi blokování matných a blokovaných vláken. Chcete-li změnit uspořádání vláken, vyberte vlákno a pak vyberte ikonu nahoru nebo dolů na panelu nástrojů.

Můžete skrýt vlákna, která nedělají práci nebo jsou zcela blokovány, protože jejich statistiky jsou irelevantní a mohou ucpat sestavy. Skrytí vláken výběrem jejich názvů a výběrem **možnosti Skrýt vybraná vlákna** nebo **Skrýt všechny ikony vybraných vláken** na panelu nástrojů. Chcete-li identifikovat vlákna, která chcete skrýt, vyberte odkaz **Na souhrn vlákna** vlevo dole. Vlákna, která nemají žádnou aktivitu, můžete skrýt v grafu **Souhrn podle vlákna.**

### <a name="thread-execution-details"></a>Podrobnosti spuštění vlákna
Chcete-li získat podrobnější informace o segmentu provádění, vyberte bod na zeleném segmentu časové osy. Vizualizér souběžnosti zobrazí černou stříšku nad vybraným bodem a zobrazí její zásobník volání na kartě **Aktuální** v dolním podokně. V segmentu spuštění můžete vybrat více bodů.

>[!NOTE]
>Vizualizér souběžnosti nemusí být schopen vyřešit výběr v segmentu spuštění, pokud je doba trvání segmentu menší než jedna milisekunda.

Chcete-li získat profil spuštění pro všechna neskrytá vlákna v aktuálně vybraném časovém rozsahu, vyberte **možnost Spuštění** v legendě vlevo dole.

### <a name="thread-blocking-details"></a>Podrobnosti o blokování vláken
Chcete-li získat informace o určité oblasti ve vlákně, najeďte na tuto oblast na časové ose a zobrazte popis. Popis ekvizumů má informace, jako je kategorie, čas zahájení a zpoždění. Vyberte oblast, ve které chcete zobrazit zásobník volání v daném okamžiku v čase na kartě **Aktuální** v dolním podokně. Podokno také zobrazuje kategorii, zpoždění, blokování rozhraní API, pokud existuje, a odblokování vlákna, pokud existuje. Prozkoumáním zásobníku volání můžete určit základní důvody pro události blokování vláken.

Cesta spuštění může mít několik blokování událostí. Chcete-li je prozkoumat blokováním kategorie a rychleji vyhledat problémové oblasti, vyberte kategorii blokování v legendě vlevo.

### <a name="dependencies-between-threads"></a>Závislosti mezi vlákny
Vizualizér souběžnosti zobrazuje závislosti mezi vlákny, takže můžete určit, co se blokované vlákno pokoušelo provést a jaké jiné vlákno povolilo jeho spuštění.

Chcete-li zjistit, které vlákno odblokovalo jiné vlákno, vyberte blokující segment na časové ose. Pokud vizualizér souběžnosti může určit odblokovací vlákno, nakreslí čáru mezi odblokovacím vláknem a spuštěným segmentem, který následuje za blokačním segmentem. V dolním podokně vyberte kartu **Odblokování zásobníku,** abyste viděli příslušný zásobník volání.

## <a name="profile-reports"></a>Sestavy profilů
Pod grafem časové osy je podokno s kartami **sestavy Sestavy profilů**, **Aktuální**a **Odblokování snopů.** Sestavy se automaticky aktualizují při změně výběru časové osy a vláken. U rozsáhlých trasování může být podokno sestav dočasně nedostupné při výpočtu aktualizací.

### <a name="profile-report-tab"></a>Karta Sestava profilu

**Sestava profilu** má dva filtry:

- Chcete-li odfiltrovat položky stromu volání, kde bylo vynaloženo málo času, zadejte hodnotu filtru mezi 0 a 99 procent do pole **Snížení šumu v** poli. Výchozí hodnota je 2 procenta.
- Chcete-li zobrazit stromy volání pouze pro váš kód, zaškrtněte políčko **Jen můj kód.** Chcete-li zobrazit všechny stromy volání, zrušte zaškrtnutí políčka.

Karta **Sestava profilu** zobrazuje sestavy pro kategorie a odkazy v legendě. Chcete-li sestavu zobrazit, vyberte jednu z položek vlevo:

- **Provedení** Sestava **spuštění** zobrazuje rozdělení času, který aplikace strávila v provádění.

  Chcete-li najít řádek kódu, ve kterém je čas spuštění strávený, rozbalte strom volání a v místní nabídce položky stromu volání vyberte **Zobrazit zdroj** nebo **Zobrazit weby volání**. **Zdroj zobrazení** vyhledá schovaný řádek kódu. **Zobrazit weby volání** vyhledá řádek kódu, který volal na schovaný řádek. Pokud existuje pouze jedna linka webu volání, její kód je zvýrazněn. Pokud existuje několik webů pro volání, vyberte v dialogovém okně požadovaný web a pak vyberte **Přejít na zdroj**. Často je nejužitečnější vyhledat web volání, který má nejvíce instancí, nejvíce času nebo obojí. Další informace naleznete v [tématu Sestava profilu spuštění](../profiling/execution-profile-report.md).

- **Synchronizace** Sestava **synchronizace** zobrazuje volání, které jsou zodpovědné za synchronizační bloky, spolu s celkovým počtem blokování každého zásobníku volání. Další informace naleznete v [tématu Doba synchronizace](../profiling/synchronization-time.md).

- **Vstupně-no** **Vstupně-v.** sestava zobrazuje volání, které jsou odpovědné za vstupně-v bloky, spolu s celkovým blokování časy každého zásobníku volání. Další informace naleznete v [tématu V/V čas (Zobrazení vláken)](../profiling/i-o-time-threads-view.md).

- **Spánek** Sestava **spánku** zobrazuje volání, které jsou zodpovědné za bloky spánku, spolu s celkovým blokováním časy každého zásobníku volání. Další informace naleznete v [tématu Doba spánku](../profiling/sleep-time.md).

- **Správa paměti** Sestava **správy paměti** zobrazuje volání, kde došlo k blokům správy paměti, spolu s celkovým počtem blokování každého zásobníku volání. Tyto informace slouží k identifikaci oblastí, které mají nadměrné stránkování nebo uvolňování paměti problémy.  Další informace naleznete v [tématu Memory management time](../profiling/memory-management-time.md).

- **Prevence** Sestava **Preemption** ukazuje, kde procesy v systému předcvažovaly aktuální proces a jednotlivá vlákna, která nahradila vlákna v aktuálním procesu. Tyto informace můžete použít k identifikaci procesů a vláken, které jsou nejvíce zodpovědné za preemption. Další informace naleznete v tématu [Preemption time](../profiling/preemption-time.md).

- **Zpracování ui** Sestava **zpracování ui** zobrazuje volání, které jsou zodpovědné za bloky zpracování ui, spolu s celkovým blokování mů řešit každý zásobník volání. Další informace naleznete [v tématu doba zpracování ui](../profiling/ui-processing-time.md).

- **Souhrn podle vlákna** Výběrem **možnosti Souhrn podle vlákna** zobrazíte graf zobrazující stav vláken pro aktuálně vybraný časový interval. Barevně odlišené sloupce zobrazují celkový čas, který každé vlákno strávilo v běhu, blokováno, vstupně-va a dalších stavech. Závity jsou označeny v dolní části. Když upravíte úroveň zvětšení v grafu časové osy, tento graf se automaticky aktualizuje.

  Při některých úrovních přiblížení se některá vlákna nemusí v grafu zobrazit. Když k tomu dojde, vpravo se objeví elipsy (**...**). Pokud se požadované vlákno nezobrazí, můžete skrýt další vlákna. Další informace naleznete [v tématu souhrnná sestava podle vlákna](../profiling/per-thread-summary-report.md).

- **Operace na disku** Vyberte **Operace disku,** chcete-li zobrazit procesy a vlákna zapojená do vstupně-out disků pro aktuální proces, soubory, kterých se dotkli (například knihovny DLL, které načetli), kolik bajtů čtou a další informace. Tuto sestavu můžete použít k vyhodnocení času stráveného přístupem k souborům během provádění, zejména v případě, že se proces zdá být vázán na vstupně-výstupní chod. Další informace naleznete v tématu [Sestava operací disku](../profiling/disk-operations-report-threads-view.md).

### <a name="current-tab"></a>Aktuální karta
Tato karta zobrazuje zásobník volání pro vybraný bod v segmentu vlákna v grafu časové osy. Balíčky volání jsou oříznuty tak, aby zobrazovaly jenom aktivitu, která souvisí s vaší aplikací.

### <a name="unblocking-stack-tab"></a>Odblokování karty Zásobník
Tato karta ukazuje, které vlákno odblokovalo vybrané vlákno a odblokovalo zásobník volání.

## <a name="see-also"></a>Viz také
- [Vizualizér souběžnosti](../profiling/concurrency-visualizer.md)
