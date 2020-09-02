---
title: Zobrazení vláken (paralelní výkon) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.performance.view.threadblocking
helpviewer_keywords:
- Concurrency Visualizer, Threads View (Parallel Performance)
ms.assetid: 2e441103-a266-407b-88c3-fb58716257a3
caps.latest.revision: 26
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 0d685dc39f5e07840a5995f7fe67988840c3f50a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "64821990"
---
# <a name="threads-view-parallel-performance"></a>Zobrazení vláken (paralelní výkon)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Zobrazení vlákna je nejpodrobnější zobrazení a funkce s bohatou funkcí v Vizualizátor souběžnosti. Pomocí tohoto zobrazení můžete zjistit, zda jsou vlákna spouštěna nebo blokována z důvodu synchronizace, vstupně-výstupních operací nebo z jiného důvodu.  
  
 V průběhu analýzy profilů Vizualizér souběžnosti ověřuje všechny události kontextového přepínače operačního systému pro každé vlákno aplikace. K přepínáním kontextu může dojít z mnoha důvodů, jako jsou například:  
  
- Vlákno je blokováno v rámci synchronizačního primitiva.  
  
- Doba platnosti vlákna vyprší.  
  
- Vlákno provádí blokující požadavek na vstupně-výstupní operace.  
  
  Zobrazení vlákna přiřadí kategorii každému kontextu přepínači, když vlákno zastavilo provádění. Kategorie se zobrazí v legendě v levé dolní části zobrazení. Vizualizátor souběžnosti rozděluje události kontextového přepínače hledáním zásobníku volání vlákna pro známá blokující rozhraní API. Pokud se neshoduje zásobník volání, je použit důvod čekání, který je poskytován pomocí [!INCLUDE[TLA#tla_mswin](../includes/tlasharptla-mswin-md.md)] . [!INCLUDE[TLA#tla_mswin](../includes/tlasharptla-mswin-md.md)]Kategorie však může být založena na podrobnostech implementace a nemusí odrážet záměr uživatele. Například [!INCLUDE[TLA#tla_mswin](../includes/tlasharptla-mswin-md.md)] hlásí důvod čekání pro blokování na nativním zámku funkce Slim Reader jako vstup/výstup namísto synchronizace. Ve většině případů můžete identifikovat hlavní příčinu blokující události zkoumáním zásobníků volání, které odpovídají událostem kontextu přepínače.  
  
  Zobrazení vlákna také zobrazuje závislosti mezi vlákny. Například pokud identifikujete vlákno blokované na objektu synchronizace, můžete vyhledat vlákno, které ho odblokuje, a můžete zkontrolovat aktivitu v zásobníku volání pro toto vlákno v okamžiku, kdy odblokuje druhý.  
  
  Když se spouštějí vlákna, Vizualizér souběžnosti shromažďuje ukázky. V zobrazení vláken můžete analyzovat, který kód je spuštěn jedním nebo více vlákny během spouštěcího segmentu. Můžete také kontrolovat blokující sestavy a sestavy, které profiluje volání – spuštění stromu zásobníku.  
  
## <a name="usage"></a>Využití  
 Tady je několik způsobů, jak můžete použít zobrazení vlákna:  
  
- Identifikujte důvody, proč uživatelské rozhraní (UI) aplikace nereaguje během určitých fází provádění.  
  
- Identifikujte čas strávený blokováním při synchronizaci, vstupně-výstupních chyb stránek a dalších událostí.  
  
- Identifikujte stupeň rušení z jiných procesů, které jsou spuštěny v systému.  
  
- Identifikujte problémy s vyrovnáváním zatížení pro paralelní spuštění.  
  
- Identifikujte důvody pro škálovatelnost, která je nekonzistentní nebo neexistující (například proč výkon paralelní aplikace nemůžete zlepšit, pokud jsou k dispozici více logických jader).  
  
- Pochopení stupně souběžnosti v aplikaci, aby bylo možné lépe rozumělost.  
  
- Pochopení závislostí mezi pracovními vlákny a kritickými cestami provádění.  
  
## <a name="examining-specific-time-intervals-and-threads"></a>Zkoumání konkrétních časových intervalů a vláken  
 Zobrazení vlákna znázorňuje časovou osu. V časové ose můžete přiblížit a posunout, abyste prozkoumali konkrétní intervaly a vlákna vaší aplikace. Na ose x je čas a na ose y je několik kanálů:  
  
- Dva vstupně-výstupní kanály pro každou diskovou jednotku v systému, jeden kanál pro čtení a jeden pro zápis.  
  
- Kanál pro každé vlákno v procesu.  
  
- Kanály značek, pokud se v trasování nacházejí události značek. Kanály značek se zpočátku zobrazí pod kanály vláken, které tyto události vygenerovaly.  
  
- Kanály GPU.  
  
  Tady je ilustrace zobrazení vlákna:  
  
  ![Zobrazení vláken](../profiling/media/threadsviewnarrowing.png "ThreadsViewNarrowing")  
  Zobrazení vláken  
  
  Zpočátku jsou vlákna seřazena v pořadí, ve kterém jsou vytvořena, takže hlavní vlákno aplikace je nejprve. Pomocí možnosti řazení v levém horním rohu zobrazení můžete řadit vlákna podle jiného kritéria (například při provádění většiny provedených úloh).  
  
  Vlákna, která neprovádí práci, můžete skrýt tak, že vyberete jejich názvy v levém sloupci a kliknete na panelu nástrojů na tlačítko **Skrýt vybraná vlákna** . Doporučujeme skrýt vlákna, která jsou zcela zablokovaná, protože jejich statistiky mají nevýznamné a můžou CLOG sestavy.  
  
  Chcete-li identifikovat další vlákna ke skrytí, v aktivní legendě vyberte sestavu **souhrnu jednotlivých vláken** na kartě **Sestava profilu** . Tím se zobrazí graf rozpis spuštění, který zobrazuje stav vláken pro aktuálně vybraný časový interval. V některých úrovních přiblížení nemusí být některá vlákna zobrazená. V takovém případě se na pravé straně zobrazí tři tečky.  
  
  Pokud jste vybrali časový interval a některá vlákna v něm, můžete spustit analýzu výkonu.  
  
## <a name="analysis-tools"></a>Analytické nástroje  
 Tato část popisuje sestavy a další nástroje pro analýzu.  
  
### <a name="thread-blocking-details"></a>Podrobnosti o blokování vláken  
 Chcete-li získat informace o blokující události v konkrétní oblasti vlákna, umístěte ukazatel myši na tuto oblast, abyste zobrazili popis tlačítka. Obsahuje informace, jako je kategorie, čas zahájení oblasti, doba blokování a blokující rozhraní API, pokud je nějaký. Pokud vyberete oblast blokování, v dolním podokně se zobrazí zásobník, ve kterém se zobrazí stejné informace, které se zobrazují v popisu tlačítka. Prozkoumáním zásobníku volání můžete určit základní důvod pro událost blokující vlákna. Další informace o procesu a vlákně můžete najít tak, že vyberete segment a prozkoumáte aktuální kartu.  
  
 Cesta spuštění může mít několik blokujících událostí. Můžete je prozkoumávat blokováním kategorie, abyste mohli rychleji najít problematické oblasti. Stačí zvolit jednu z kategorií blokování v legendě vlevo.  
  
### <a name="dependencies-between-threads"></a>Závislosti mezi vlákny  
 Vizualizátor souběžnosti může zobrazit závislosti mezi vlákny v procesu tak, aby bylo možné určit, co se zablokované vlákno snažilo udělat, a zjistit, jaké další vlákno povolilo provádění. Chcete-li určit, které vlákno odblokuje jiné vlákno, vyberte příslušný blokující segment. Pokud Vizualizér souběžnosti může určit vlákno odblokování, nakreslí čáru mezi podprocesem odblokování a zpracovávaným segmentem, který následuje po blokujícím segmentu. Kromě toho karta **Zásobník odblokování** zobrazuje příslušný zásobník volání.  
  
### <a name="thread-execution-details"></a>Podrobnosti spuštění vlákna  
 V grafu časové osy vlákna se zelené segmenty zobrazí při provádění kódu. Můžete získat podrobnější informace o segmentu spuštění.  
  
 Když vyberete bod v segmentu spuštění, Vizualizér souběžnosti vyhledá daný bod v čase v příslušném zásobníku volání a poté zobrazí černý blikající kurzor nad vybraným bodem v segmentu spuštění a zobrazí přímo zásobník volání na **aktuální kartě zásobníku** . V segmentu spuštění můžete vybrat více bodů.  
  
> [!NOTE]
> Vizualizátor souběžnosti nemusí být schopný vyřešit výběr v segmentu spuštění. Obvykle k tomu dochází, pokud je doba trvání segmentu menší než 1 milisekunda.  
  
 Chcete-li získat profil spuštění pro všechna povolená (neskrytá) vlákna v aktuálně vybraném časovém rozsahu, klikněte na tlačítko **spuštění** v aktivní legendě.  
  
### <a name="timeline-graph"></a>Graf časové osy  
 Graf časové osy zobrazuje aktivity všech vláken v procesu a všech zařízeních fyzického disku v hostitelském počítači. Zobrazuje také události GPU a aktivity značek.  Můžete přiblížit a Zobrazit více podrobností nebo zobrazení delšího časového intervalu. Můžete také vybrat body v grafu, abyste získali podrobnosti o kategoriích, časech spuštění, trváních a stavech zásobníku volání.  
  
 V grafu časové osy barva indikuje stav vlákna v daném čase. Například byly spuštěny zelené segmenty, byly pro synchronizaci zablokovány červené segmenty, byly pozastaveny žluté segmenty a fialové segmenty byly zařazeny do vstupně-výstupních operací zařízení. Toto zobrazení můžete použít k prohlédnutí rovnováhy mezi vlákny, které jsou zapojeny do paralelní smyčky nebo v souběžných úlohách. Pokud je vlákno delší než ostatní, je možné, že je tato práce nevyvážená. Tyto informace můžete použít ke zlepšení výkonu programu tím, že mezi vlákny rovnoměrně distribuujete práci.  
  
 Pokud je v určitém časovém okamžiku pouze jeden podproces zelený (probíhá), aplikace nemusí plně využít výhod souběžnosti systému. Pomocí grafu časové osy můžete prozkoumávat závislosti mezi vlákny a dočasnou relací mezi blokujícím a blokovaným vláknem. Chcete-li změnit uspořádání vláken, vyberte vlákno a pak na panelu nástrojů klikněte na tlačítko nahoru nebo dolů. Chcete-li skrýt vlákna, vyberte je a pak klikněte na tlačítko **Skrýt vlákna** .  
  
### <a name="profile-reports"></a>Sestavy profilů  
 Pod grafem časové osy je profil časové osy a podokno, které obsahuje karty pro různé sestavy. Sestavy se automaticky aktualizují při změně zobrazení vláken. V případě rozsáhlých trasování může být podokno sestavy během výpočtu aktualizací nedostupné. Každá sestava má dvě úpravy filtru: omezení šumu a Pouze můj kód. Snížení šumu použijte pro odfiltrování položek stromu volání, kde je málo času stráveno. Výchozí hodnota filtru je 2%, ale můžete ji upravit z 0% na 99 procent. Chcete-li zobrazit pouze strom volání pro váš kód, zaškrtněte políčko **pouze můj kód** . Chcete-li zobrazit všechny stromy volání, zrušte ji.  
  
#### <a name="profile-report"></a>Sestava profilu  
 Tato karta zobrazuje sestavy, které odpovídají položkám v aktivní legendě. Chcete-li zobrazit sestavu, vyberte jednu z položek.  
  
#### <a name="current-stack"></a>Aktuální zásobník  
 Tato karta zobrazuje zásobník volání pro vybraný bod na segmentu vlákna v grafu časové osy. Zásobníky volání jsou oříznuty, aby se zobrazila pouze aktivita, která souvisí s vaším programem.  
  
#### <a name="unblocking-stack"></a>Odblokování zásobníku  
 Chcete-li zjistit, které vlákno odblokuje vybrané vlákno, a v jakém řádku kódu, klikněte na kartu **Zásobník odblokování** .  
  
#### <a name="execution"></a>Spuštění  
 Sestava spuštění zobrazuje rozpis času stráveného prováděním aplikace.  
  
 Chcete-li najít řádek kódu, v němž je doba provádění vyčerpána, rozbalte strom volání a potom v místní nabídce položky stromu volání zvolte možnost **Zobrazit zdroj** nebo **Zobrazit weby volání**. **Zdroj zobrazení** vyhledá spouštěný řádek kódu. **Zobrazení lokality volání** vyhledá řádek kódu, který se nazývá spuštěný řádek kódu. Pokud existuje pouze jeden web volání, jeho řádek kódu je zvýrazněn. Pokud existuje více webů volání, můžete vybrat požadovanou položku v dialogovém okně, které se zobrazí, a potom kliknutím na tlačítko **Přejít do zdroje** zvýraznit kód webu volání. Je často užitečné najít web volání, který má nejvíce instancí, nejvíce času nebo obojího. Další informace najdete v tématu [Sestava profilu spuštění](../profiling/execution-profile-report.md).  
  
#### <a name="synchronization"></a>Synchronizace  
 Zpráva o synchronizaci zobrazuje volání, která jsou zodpovědná za bloky synchronizace, spolu s agregovanou dobou blokování každého zásobníku volání. Další informace najdete v tématu [čas synchronizace](../profiling/synchronization-time.md).  
  
#### <a name="io"></a>I/O  
 Sestava vstup/výstup zobrazuje volání, která jsou zodpovědná za bloky v/v, spolu s agregovanou dobou blokování každého zásobníku volání. Další informace naleznete v části [vstupně-výstupní čas (zobrazení vláken)](../profiling/i-o-time-threads-view.md).  
  
#### <a name="sleep"></a>Režim spánku  
 Sestava režimu spánku zobrazuje volání, která jsou zodpovědná za bloky režimu spánku, spolu s agregovanou dobou blokování každého zásobníku volání. Další informace najdete v tématu [Doba spánku](../profiling/sleep-time.md).  
  
#### <a name="memory-management"></a>Správa paměti  
 Sestava správy paměti zobrazuje volání, kde došlo k blokům správy paměti, spolu s agregovanými časy blokování jednotlivých zásobníků volání. Tyto informace můžete použít k identifikaci oblastí, které mají nadměrné problémy stránkování nebo uvolňování paměti.  Další informace najdete v tématu [čas správy paměti](../profiling/memory-management-time.md).  
  
#### <a name="preemption"></a>Přerušení  
 Sestava přerušení zobrazuje případy, kdy procesy v systému zrušily aktuální proces a jednotlivá vlákna, která nahradila vlákna v aktuálním procesu. Tyto informace můžete použít k identifikaci procesů a vláken, která jsou nejvíc zodpovědná za přerušení. Další informace najdete v tématu [čas přerušení](../profiling/preemption-time.md).  
  
#### <a name="ui-processing"></a>Zpracování uživatelského rozhraní  
 Sestava zpracování uživatelského rozhraní zobrazuje volání, která jsou zodpovědná za bloky pro zpracování uživatelského rozhraní, spolu s agregovanými dobami blokování každého zásobníku volání. Další informace najdete v tématu [Doba zpracování uživatelského rozhraní](../profiling/ui-processing-time.md).  
  
#### <a name="per-thread-summary"></a>Souhrn podle vláken  
 Tato karta zobrazuje barevně kódované zobrazení sloupce celkového času, který jednotlivá vlákna strávila v běhu, blokovaném, vstupně-výstupních a dalších stavech. Sloupce jsou označeny v dolní části. Když upravíte úroveň přiblížení v grafu časové osy, tato karta se automaticky aktualizuje. V některých úrovních přiblížení nemusí být některá vlákna zobrazená. V takovém případě se na pravé straně zobrazí tři tečky. Pokud se požadované vlákno nezobrazí, můžete skrýt další vlákna. Další informace naleznete v tématu [Souhrnná sestava jednotlivých vláken](../profiling/per-thread-summary-report.md).  
  
#### <a name="disk-operations"></a>Diskové operace  
 Tato karta zobrazuje, které procesy a vlákna byly zapojeny do vstupně-výstupních operací disku jménem aktuálního procesu, které soubory (například načtené knihovny DLL), Počet přečtených bajtů a další informace. Tuto sestavu můžete použít k vyhodnocení času stráveného při přístupu k souborům během provádění, zejména v případě, že se váš proces jeví jako vázané na vstupně-výstupní operace. Další informace najdete v tématu [Sestava diskových operací](../profiling/disk-operations-report-threads-view.md).  
  
## <a name="see-also"></a>Viz také  
 [Vizualizér souběžnosti](../profiling/concurrency-visualizer.md)
