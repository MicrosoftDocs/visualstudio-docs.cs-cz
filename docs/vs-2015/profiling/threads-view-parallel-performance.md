---
title: Vlákna zobrazení (paralelní výkon) | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.performance.view.threadblocking
helpviewer_keywords:
- Concurrency Visualizer, Threads View (Parallel Performance)
ms.assetid: 2e441103-a266-407b-88c3-fb58716257a3
caps.latest.revision: 26
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 39457684ba19ecbb0ad2ef82caa349e67cdaf8a7
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51756336"
---
# <a name="threads-view-parallel-performance"></a>Zobrazení vláken (paralelní výkon)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Zobrazení vláken je nejvíce podrobná a plně funkční zobrazení ve vizualizátoru souběžnosti. Pomocí tohoto zobrazení můžete identifikovat, jestli jsou vlákna provádění nebo blokování z důvodu synchronizace, vstupně-výstupních operací nebo z jiného důvodu.  
  
 Vizualizátor souběžnosti během analýzy profilu, zkontroluje všechny události přepnutí kontextu operačního systému pro každé vlákno aplikace. Přepnutí kontextu může dojít z mnoha důvodů, jako je například tyto:  
  
- Vlákno je blokována v primitiv synchronizace.  
  
- Vypršení platnosti quantum vlákna.  
  
- Vlákno požádá blokování vstupně-výstupních operací.  
  
  Zobrazení vláken přiřadí kategorie každého přepnutí kontextu, když vlákno ukončila provádění. Kategorie jsou uvedeny v legendě v levé dolní části zobrazení. Vizualizátor souběžnosti kategorizuje přepněte kontext události tak, že dobře známé blokování rozhraní API zásobník volání vlákna. Pokud není nalezena žádná volání zásobníku shoda, Důvod čekání, která je poskytována [!INCLUDE[TLA#tla_mswin](../includes/tlasharptla-mswin-md.md)] se používá. Ale [!INCLUDE[TLA#tla_mswin](../includes/tlasharptla-mswin-md.md)] kategorie mohou být založeny na podrobnosti implementace a nemusí odrážet záměru uživatele. Například [!INCLUDE[TLA#tla_mswin](../includes/tlasharptla-mswin-md.md)] sestavy čekání důvod pro blokování zámku nativní tenký čtení a zápis jako vstupně-výstupní operace namísto synchronizace. Ve většině případů můžete identifikovat původní příčinu možných blokujících událostí prozkoumáním zásobníky volání, které odpovídají přepněte kontext události.  
  
  Zobrazení vláken také ukazuje závislosti mezi vlákny. Případě identifikujete vlákno, které je blokována v synchronizační objekt, můžete vyhledat vlákna, které ho odblokováno a aktivity v zásobníku volání pro toto vlákno v místě, můžete zkontrolovat při otevření druhou.  
  
  Při provádění vlákna Vizualizátor souběžnosti shromažďuje ukázky. V zobrazení vláken můžete analyzovat, jaký kód provádí jeden nebo více vláken během provádění segmentu. Můžete také prozkoumat blokování sestavy a sestavy, které profilu zásobník volání stromu spuštění.  
  
## <a name="usage"></a>Použití  
 Tady jsou některé způsoby, které můžete zobrazení vláken:  
  
-   Určení důvodů, proč uživatelského rozhraní (UI) aplikace během určité fáze spuštění nereaguje.  
  
-   Určete dobu, kterou má stráví blokování synchronizace, vstupně-výstupních operací, stránkování a dalších událostí.  
  
-   Identifikujte stupeň před rušením z jiných procesů, které jsou spuštěny v systému.  
  
-   Identifikujte problémy Vyrovnávání zatížení pro paralelní zpracování.  
  
-   Určení důvodů škálovatelnost, která je neoptimální nebo neexistující (třeba Proč se výkon paralelní aplikace se nezvyšuje, když jsou k dispozici více logických jader).  
  
-   Seznamte se s stupeň souběžnosti v aplikacích, které vám pomůžou paralelního zpracování.  
  
-   Pochopení závislostí mezi pracovních vláken a kritické cesty spuštění.  
  
## <a name="examining-specific-time-intervals-and-threads"></a>Zkoumání určitých časových intervalech a vlákna  
 Zobrazení vláken ukazuje časovou osu. Můžete přiblížení a posouvání v časové ose ke kontrole určitých intervalech a vlákna vaší aplikace. Na ose x čas a na ose y jsou několika kanálů:  
  
- Dva kanály vstupně-výstupních operací pro každou jednotku disku na systém, jeden kanál pro čtení a jeden pro zápis.  
  
- Kanál pro každé vlákno v procesu.  
  
- Kanály značky, pokud jsou značky událostí v trasování. Značky kanály zpočátku zobrazí v položce vláken kanály, které vygeneruje tyto události.  
  
- Kanály GPU.  
  
  Tady je ilustraci zobrazení vláken:  
  
  ![Zobrazit vlákna](../profiling/media/threadsviewnarrowing.png "ThreadsViewNarrowing")  
  Zobrazení vláken  
  
  Na začátku vlákna jsou seřazeny v pořadí, ve kterém jsou vytvořeny, tak, aby se první hlavního vlákna aplikace. Možnost řazení v levém horním rohu zobrazení můžete řadit vlákna podle jiného kritéria (například pomocí provádí většinu práce spuštění).  
  
  Můžete skrýt vlákna, která se provede práci výběrem jejich názvy ve sloupci na levé straně a potom kliknete **skrýt vybraná vlákna** tlačítko na panelu nástrojů. Doporučujeme, abyste skrytí vláken, které jsou zcela blokována, protože jejich statistiky nejsou relevantní a můžete clog sestavy.  
  
  Chcete-li identifikovat další vlákna skrýt v aktivní legenda, zvolte **Souhrn podle vláken** sestavy **Sestava profilu** kartu. Zobrazí rozpis spuštění grafu, který ukazuje stav vláken pro aktuálně vybraný časový interval. Na některých úrovních přiblížení nemusí být zobrazeny některá vlákna. Když k tomu dojde, symbol tří teček se zobrazí na pravé straně.  
  
  Po výběru intervalu a některá vlákna v ní můžete spustit analýzu výkonu.  
  
## <a name="analysis-tools"></a>Nástroje pro analýzu  
 Tato část popisuje sestavy a další nástroje pro analýzu.  
  
### <a name="thread-blocking-details"></a>Podrobnosti o blokování vlákna  
 Pokud chcete získat informace o blokování události v konkrétní oblasti ve vlákně, ponechte ukazatel na tuto oblast zobrazení popisu tlačítka. Obsahuje informace, jako jsou kategorie, oblasti počáteční čas, blokování trvání a blokování rozhraní API, pokud existuje. Pokud vyberete blokování oblast, zobrazí se v dolním podokně, společně s stejné informace, které se zobrazí v popisu zásobníku v daném okamžiku v čase. Tím, že kontroluje zásobníku volání, můžete určit základní příčina toho události blokování vlákna. Výběrem segmentu a zkoumání aktuální záložku můžete najít další proces a informace o vláknech.  
  
 Cesta provádění může mít více blokujících událostí. Můžete prozkoumat tyto podle kategorie blokování, abyste rychle našli problémových oblastí. Právě zvolte jednu z blokující kategorií v legendě na levé straně.  
  
### <a name="dependencies-between-threads"></a>Závislosti mezi vlákny  
 Vizualizátor souběžnosti můžete zobrazit závislosti mezi vlákny v procesu, tak, aby bylo možné určit, co se snažil blokovaná vlákna a zjistěte, jaké další vlákno povoleno ji ke spuštění. Pokud chcete zjistit, které vlákno odblokováno jiným vláknem, vyberte příslušné blokující segment. Pokud Vizualizátor souběžnosti lze určit odblokování vláken, nakreslí čáru mezi odblokování vláken a provádění segment, který následuje blokující segment. Kromě toho **Unblocking zásobníku** kartě se zobrazí zásobník volání relevantní.  
  
### <a name="thread-execution-details"></a>Podrobnosti spuštění vlákna  
 Časová osa grafu vlákna zobrazit zelená segmenty ji při provádění kódu. Můžete získat podrobnější informace o provádění segmentu.  
  
 Když vyberete bod v segmentu spuštění, Vizualizátor souběžnosti hledá tento bod v čase v zásobníku volání relevantní a pak zobrazí černé blikajícího kurzoru nad vybraný bod v segmentu spuštění a zásobník volání, samotný na  **Aktuální zásobník** kartu. Můžete vybrat několik bodů na segment spuštění.  
  
> [!NOTE]
>  Vizualizátor souběžnosti nemusí být schopni vyřešit výběr v segmentu spuštění. Obvykle to nastane, pokud doba trvání segmentu je menší než milisekunda.  
  
 Chcete-li získat profil spuštění pro všechny povolené (zobrazí) vlákna v aktuálně vybraném časovém rozsahu, zvolte **provádění** tlačítko v legendě aktivní.  
  
### <a name="timeline-graph"></a>Časová osa grafu  
 Časová osa graf zobrazuje aktivity všechna vlákna v procesu a všechna zařízení fyzického disku na hostitelském počítači. Také zobrazuje události GPU aktivity a značky.  Můžete přiblížit a zobrazit více podrobností dolů, chcete-li zobrazit tak delší interval času. Můžete také vybrat body v graphu a získat podrobnosti o kategorie, časy zahájení, dob trvání a stavy zásobníku volání.  
  
 V grafu časové osy barvy označuje stav vlákna v daném okamžiku. Například prováděla zelené segmenty, červenou segmentů se zablokoval pro synchronizaci, žlutý segmenty bylo přerušeno a fialové segmentů se zabývají zařízení vstupně-výstupních operací. Toto zobrazení můžete použít k prozkoumání zůstatek práci mezi vlákna, které jsou zahrnuty v paralelních smyčkách nebo souběžných úloh. Pokud vlákno trvá déle, než ostatní, může nevyváženou práce. Tyto informace můžete použít ke zlepšení výkonu programu díky distribuci práce více rovnoměrně mezi vlákna.  
  
 Pokud pouze jedno vlákno je zelenou (provedena) v bodě v čase, aplikace nemusí být plně využít souběžnost v systému. Časová osa grafu můžete použít k prozkoumání závislosti mezi vlákny a časové vztahy mezi blokování a zablokovat vlákna. Chcete-li uspořádat vlákna, vyberte vlákno a na panelu nástrojů zvolte nahoru nebo dolů. Chcete-li skrýt vlákna, vyberte je a klikněte na tlačítko **skrýt vlákna** tlačítko.  
  
### <a name="profile-reports"></a>Profilu, sestavy  
 Graf níže na časové ose je profil časové osy a podokno, které obsahuje karty pro různé sestavy. Sestavy se automaticky aktualizují po provedení změny zobrazení vláken. U velkých trasování může být podokna sestav není k dispozici během aktualizace se počítají. Každá sestava obsahuje dvě úpravy filtru: noise snížení a pouze můj kód. Můžete vyfiltrovat položky stromu volání trvají delší dobu málo snížení šumu. Výchozí hodnota filtru je % 2, ale můžete jej přizpůsobit v rozsahu 0 až 99 procent. Chcete-li zobrazit pouze strom volání pro kód, vyberte **pouze můj kód** zaškrtávací políčko. Chcete-li zobrazit všechny stromy nákladného volání, vymažte ho.  
  
#### <a name="profile-report"></a>Sestava profilu  
 Tato karta zobrazuje sestavy, které odpovídají položky v legendě aktivní. Pokud chcete zobrazit sestavy, zvolte jednu z položek.  
  
#### <a name="current-stack"></a>Aktuální zásobník  
 Tato karta zobrazuje zásobník volání pro vybraný bod na segment vlákna v časové osy grafu. Chcete-li zobrazit pouze aktivity týkající se programu jsou oříznut zásobníky volání.  
  
#### <a name="unblocking-stack"></a>Odblokování zásobníku  
 Vidět, které vlákno odblokováno zvoleném vlákně, a na jaké řádku kódu, zvolte **Unblocking zásobníku** kartu.  
  
#### <a name="execution"></a>Spuštění  
 Spuštění sestavy zobrazí rozpis čas strávený aplikace v provádění.  
  
 Najít řádek kódu, ve kterém byl stráven čas spuštění, rozbalte stromovou strukturu volání a pak v místní nabídce pro položka stromu volání, zvolte **zobrazit zdroj** nebo **lokalit volání zobrazení**. **Zobrazení zdroje** vyhledá spuštěných řádků kódu. **Zobrazit lokality volání** vyhledává řádek kódu, který volal spuštěných řádků kódu. Pokud existuje jedna lokalita volání jenom jeho řádek kódu je zvýrazněn. Pokud existuje více lokalit volání, můžete vybrat ten, který chcete v dialogovém okně, které se zobrazí a klikněte na tlačítko **přejít ke zdroji** tlačítko, abyste měli na očích kód lokality volání. Často je zvláště užitečná k vyhledání lokalitu volání, která má nejvíce instance nebo nejvíce času. Další informace najdete v tématu [Sestava profilu spuštění](../profiling/execution-profile-report.md).  
  
#### <a name="synchronization"></a>Synchronizace  
 Synchronizace sestava ukazuje volání, které jsou zodpovědné za synchronizaci bloky, společně s agregace blokování časy každý zásobník volání. Další informace najdete v tématu [čas synchronizace](../profiling/synchronization-time.md).  
  
#### <a name="io"></a>I/O  
 Vstupně-výstupních operací sestava ukazuje volání, které jsou zodpovědné za vstupně-výstupních operací bloky, společně s agregace blokování časy každý zásobník volání. Další informace najdete v tématu [čas I/O (zobrazení vláken)](../profiling/i-o-time-threads-view.md).  
  
#### <a name="sleep"></a>Přejít do režimu spánku  
 Sestava režimu spánku zobrazí volání, které jsou zodpovědné za z režimu spánku bloky, společně s agregace blokování časy každý zásobník volání. Další informace najdete v tématu [přejít do režimu spánku čas](../profiling/sleep-time.md).  
  
#### <a name="memory-management"></a>Správa paměti  
 Sestavy správy paměti ukazuje volání, kde Správa bloky paměti došlo k chybě, společně s agregace blokování časy každý zásobník volání. Tyto informace můžete použít k identifikaci oblasti, které mají nadměrné stránkování nebo uvolňování paměti kolekce problémy.  Další informace najdete v tématu [čas správy paměti](../profiling/memory-management-time.md).  
  
#### <a name="preemption"></a>Přerušení  
 Sestava přerušení ukazuje instance, kde procesy v systému přepnuto aktuální proces a jednotlivá vlákna, které nahradí vlákna v aktuálním procesu. Tyto informace můžete použít k identifikaci procesy a vlákna, které nejvíce odpovídají za přerušení. Další informace najdete v tématu [čas přerušení](../profiling/preemption-time.md).  
  
#### <a name="ui-processing"></a>Zpracování uživatelského rozhraní  
 Sestava zpracování uživatelského rozhraní obsahuje volání, které jsou zodpovědné za uživatelské rozhraní, zpracování bloky, společně s agregace blokování časy každý zásobník volání. Další informace najdete v tématu [doba zpracování uživatelského rozhraní](../profiling/ui-processing-time.md).  
  
#### <a name="per-thread-summary"></a>Souhrn podle vláken  
 Tato karta zobrazuje barevně sloupcové zobrazení celkového času, že každý podproces trvání běhu, zablokuje vstupně-výstupní operace a dalších státech. Sloupce jsou označeny v dolní části. Při úpravě úroveň zvětšení časové osy grafu se automaticky aktualizuje na této kartě. Na některých úrovních přiblížení nemusí být zobrazeny některá vlákna. Když k tomu dojde, symbol tří teček se zobrazí na pravé straně. Pokud vlákno, které chcete, aby se nezobrazí, můžete skrýt ostatní vlákna. Další informace najdete v tématu [za vlákna Souhrnná sestava](../profiling/per-thread-summary-report.md).  
  
#### <a name="disk-operations"></a>Operace disků  
 Tato karta zobrazuje, které procesy a vlákna byly zahrnuty v / v disku jménem aktuálního procesu, které soubory jsou některé (například knihovny DLL, které byly načteny), kolik bajtů načtených a další informace. Tato sestava slouží k vyhodnocení času, který byl stráven během provádění, přístup k souborům, zejména v případě, že váš proces zdá se, že se vstupně-výstupních operací, které jsou vázány. Další informace najdete v tématu [sestava diskových operací](../profiling/disk-operations-report-threads-view.md).  
  
## <a name="see-also"></a>Viz také  
 [Vizualizér souběžnosti](../profiling/concurrency-visualizer.md)



