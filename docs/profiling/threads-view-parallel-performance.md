---
title: Vlákna zobrazení ve vizualizátoru souběžnosti | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2018
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.performance.view.threadblocking
helpviewer_keywords:
- Concurrency Visualizer, Threads View (Parallel Performance)
ms.assetid: 2e441103-a266-407b-88c3-fb58716257a3
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: ce7cf5cf0534a0e989b65d6e67451fe2a7c496ab
ms.sourcegitcommit: dd839de3aa24ed7cd69f676293648c6c59c6560a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/27/2018
ms.locfileid: "52388902"
---
# <a name="threads-view-in-the-concurrency-visualizer"></a>Zobrazení vláken ve vizualizátoru souběžnosti

**Vlákna** zobrazení je nejvíce podrobná a plně funkční zobrazení ve vizualizátoru souběžnosti. V **vlákna** zobrazení, můžete určit, která vlákna jsou během segmentu spuštění provádění kódu a zjistit, zda jsou vlákna provádění nebo blokování z důvodu synchronizace, vstupně-výstupních operací nebo z jiných důvodů. **Vlákna** zobrazení sestavy také Profilovat zásobník volání stromu spuštění a odblokování vláken.

Při provádění vlákna Vizualizátor souběžnosti shromažďuje ukázky. Když vlákno ukončila provádění, vizualizéru prozkoumá všechny události přepnutí kontextu operačního systému pro vlákno. Přepnutí kontextu může dojít, protože:  
  
- Vlákno je blokována v primitiv synchronizace.  
- Vypršení platnosti quantum vlákna.  
- Vlákno požádá blokování vstupně-výstupních operací.  

Vizualizátor souběžnosti rozděluje vlákna a přepněte kontext události a zásobníky volání vláken hledá dobře známé blokování rozhraní API. Zobrazí kategorie vlákna v aktivní legendu v levém dolním **vlákna** zobrazení. Ve většině případů můžete identifikovat původní příčinu možných blokujících událostí prozkoumáním zásobníky volání, které odpovídají přepněte kontext události.

Pokud neexistuje žádná shoda zásobníku volání, Vizualizátor souběžnosti používá Důvod čekání poskytované [!INCLUDE[TLA#tla_mswin](../code-quality/includes/tlasharptla_mswin_md.md)]. Ale [!INCLUDE[TLA#tla_mswin](../code-quality/includes/tlasharptla_mswin_md.md)] kategorie mohou být založeny na podrobnosti implementace a nemusí odrážet záměru uživatele. Například [!INCLUDE[TLA#tla_mswin](../code-quality/includes/tlasharptla_mswin_md.md)] sestavy čekání důvod pro blokování zámku nativní tenký čtení a zápis jako vstupně-výstupní operace namísto synchronizace.  
  
**Vlákna** zobrazení uvádí také závislosti mezi vlákny. Například případě identifikujete vlákno, které je blokována v synchronizační objekt, můžete najít dané vlákno, odblokovaný ho. Při otevření další můžete prozkoumat zásobník volání odblokování vláken v okamžiku.  

Můžete použít **vlákna** se můžete podívat na:  

- Zjistit důvody pro uživatelské rozhraní (UI) aplikace během určité fáze spuštění nereaguje.  
- Určují dobu, kterou má stráví blokování synchronizace, vstupně-výstupních operací, stránkování a dalších událostí.  
- Zjistěte, do jaké míry před rušením z jiných procesů, které jsou spuštěny v systému.  
- Identifikujte problémy Vyrovnávání zatížení pro paralelní zpracování.  
- Najdete důvodů neoptimální nebo neexistující škálovatelnost. Například, proč výkon paralelní aplikace nezvyšuje když jsou k dispozici více logických jader.  
- Seznamte se s stupeň souběžnosti v aplikacích, které vám pomůžou paralelního zpracování.  
- Určení závislostí mezi pracovních vláken a kritické cesty spuštění.  
  
## <a name="use-threads-view"></a>Použití zobrazení vláken 

Chcete-li spustit nástroj Vizualizátor souběžnosti, vyberte **analyzovat** > **Vizualizátor souběžnosti**a potom vyberte možnost, jako je například **spuštění nového procesu**. 

Vizualizátor souběžnosti spustí aplikaci a shromažďuje trasování, dokud nevyberete **zastavit shromažďování**. Vizualizér pak analyzuje trasování a zobrazí výsledky na stránce sestavy trasování. 

Vyberte **vlákna** vlevo nahoře v sestavě a otevřete kartu **vlákna** zobrazení. 

![Zobrazit vlákna](../profiling/media/threadsviewnarrowing.png "vlákna zobrazení")  
  
Vyberte časové intervaly a vlákna se spustit analýzu výkonu.  
  
## <a name="timeline-analysis"></a>Časová osa analýzy  

Horní části **vlákna** zobrazení je časové ose. Časová osa ukazuje aktivitu všechna vlákna v procesu a všechna zařízení fyzického disku na hostitelském počítači. Také zobrazuje události GPU aktivity a značky.  

Na časové ose osy x je čas a na ose y jsou několika kanály:  
  
- Dva kanály vstupně-výstupních operací pro každou jednotku disku na systém, jeden kanál pro čtení a jeden pro zápis.  
- Kanál pro každé vlákno v procesu.  
- Kanály značky, pokud jsou značky událostí v trasování. Značky kanály zpočátku zobrazí v položce vláken kanály, které vygeneruje tyto události.  
- Kanály GPU.  
  
Na začátku vlákna jsou seřazeny v pořadí, ve které jste vytvořili, tedy první vlákno hlavní aplikace. Vyberte jinou možnost v **řadit** rozevírací nabídku a řadit vlákna podle jiného kritéria, například **provádění**. 

Časová osa barvy označují stav vlákna v daném okamžiku. Zelená segmenty spouštíte, red segmenty jsou blokovány pro synchronizaci, jsou žlutým segmenty přerušeno a fialové segmentů se zabývají zařízení vstupně-výstupních operací. 

Můžete přiblížit a zobrazit více podrobností, nebo oddálit, a zobrazit tak delší interval času. Vyberte segmentů a bodům graphu a získat informace o kategoriích, časy, zpoždění, spuštění a stavy zásobníku volání.  

Zkontrolujte pracovní rovnováhu mezi vlákny, které jsou zahrnuty v paralelních smyčkách nebo v souběžných úloh pomocí časové osy. Pokud jedno vlákno trvá déle, než ostatní, může nevyváženou práce. Díky distribuci práce více rovnoměrně mezi vláken může zlepšit výkon vaší aplikace.  
  
Pokud pouze jedno vlákno provádí v bodě v čase, aplikace nemusí být plně využít souběžnosti v systému. Časová osa grafu můžete použít k prozkoumání závislosti mezi vlákny a časové vztahy mezi blokování a zablokovat vlákna. Chcete-li uspořádat vlákna, vyberte vlákno a vyberte nahoru nebo dolů na panelu nástrojů. 

Skrýt vlákna, která nejsou provádějící práce nebo zcela bylo zablokováno, protože jejich statistiky nejsou relevantní a můžete clog sestavy. Skrýt vlákna výběrem jejich názvy a pak vyberete **skrýt vybraná vlákna** nebo **Skrýt vše kromě vybraných vláken** ikon na panelu nástrojů. Chcete-li identifikovat vlákna, které chcete skrýt, vyberte **Souhrn podle vláken** odkaz v levé dolní části. Můžete skrýt, které mají žádná aktivita vláken **Souhrn podle vláken** grafu. 

### <a name="thread-execution-details"></a>Podrobnosti spuštění vlákna  
Chcete-li získat podrobnější informace o provádění segmentu, vyberte bod na zelený segment časové osy. Vizualizátor souběžnosti zobrazí černé blikajícího kurzoru nad vybraný bod a zobrazuje svůj zásobník volání na **aktuální** kartu v dolním podokně. Můžete vybrat několik bodů na segment spuštění.  
  
>[!NOTE]
>Vizualizátor souběžnosti nemusí být schopni vyřešit výběr v segmentu spuštění, pokud doba trvání segmentu je menší než milisekunda.  
  
Chcete-li získat profil spuštění všech vláken zobrazí v aktuálně vybraném časovém rozsahu, vyberte **provádění** v legendě v levé dolní části.  
  
### <a name="thread-blocking-details"></a>Podrobnosti o blokování vlákna  
Pokud chcete získat informace o konkrétní oblasti ve vlákně, najeďte myší dané oblasti na ose zobrazení popisu tlačítka. Popisek obsahuje informace, jako je například kategorie, počáteční čas a zpoždění. Vyberte oblast pro zobrazení zásobníku volání v daném okamžiku v čase **aktuální** kartu v dolním podokně. V podokně se zobrazí také kategorie, zpoždění, blokování rozhraní API, pokud existuje a odblokování vláken, pokud existuje. Tím, že kontroluje zásobníku volání, můžete určit základní příčiny zablokování vlákna události.  
  
Cesta provedení může mít několik blokujících událostí. Prozkoumejte tyto podle kategorie blokování a rychleji najít problémové oblasti, vyberte kategorii blokování v legendě na levé straně.  
  
### <a name="dependencies-between-threads"></a>Závislosti mezi vlákny  
Vizualizátor souběžnosti zobrazí závislosti mezi vlákny, takže můžete určit, co blokovaná vlákna snažil provést, a jaké vlákno povoleno ji ke spuštění. 

Pokud chcete zjistit, které vlákno odblokováno jiným vláknem, vyberte blokující segment na časové ose. Pokud Vizualizátor souběžnosti lze určit odblokování vláken, nakreslí čáru mezi odblokování vláken a provádění segment, který následuje blokující segment. Vyberte **odblokování zásobníku** kartu v dolním podokně, chcete-li zobrazit zásobník volání relevantní.  
  
## <a name="profile-reports"></a>Profilu, sestavy 
Graf níže na časové ose je podokno s **Sestava profilu**, **aktuální**, a **odblokování zásobníku** sestavy karty. Sestavy automaticky aktualizuje při změně vybrané časové osy a vlákna. U velkých trasování může být podokna sestavy není dočasně k dispozici během aktualizace se počítají. 

### <a name="profile-report-tab"></a>Na kartě sestavy profil 

**Sestava profilu** má dva filtry:

- Chcete-li vyfiltrovat položky stromu volání kde byl stráven čas malý, zadejte filtr hodnotu mezi 0 a 99 procent v **Noise snížení** pole. Výchozí hodnota je % 2. 
- Chcete-li zobrazit stromy nákladného volání pro pouze váš kód, vyberte **pouze můj kód** zaškrtávací políčko. Chcete-li zobrazit všechny stromy nákladného volání, zrušte zaškrtnutí políčka.  

**Sestava profilu** karta zobrazuje sestavy kategorií a odkazy v legendě. Pokud chcete zobrazit sestavy, vyberte jednu z položek na levé straně:  

- **Spuštění**  
  **Provádění** sestava ukazuje rozdělení času aplikace stráví v provádění.  
  
  Najít řádek kódu, ve kterém byl stráven čas spuštění, rozbalte stromovou strukturu volání a na místní nabídku pro položku volání stromu, vyberte **zobrazit zdroj** nebo **lokalit volání zobrazení**. **Zobrazení zdroje** vyhledá spuštěných řádků kódu. **Zobrazit lokality volání** vyhledává řádek kódu, který volal spuštěných řádků. Pokud pouze jeden řádek lokality volání existuje, jeho kódu je zvýrazněn. Několik volání lokality neexistuje, vyberte v dialogovém okně a pak vyberte **přejít ke zdroji**. Často je zvláště užitečná k vyhledání lokalitu volání, která má nejvíce instance nebo nejvíce času. Další informace najdete v tématu [Sestava profilu spuštění](../profiling/execution-profile-report.md).  
  
- **Synchronizace**  
  **Synchronizace** sestava ukazuje volání, která je zodpovědná za synchronizaci bloky, společně s celkový blokování časy každý zásobník volání. Další informace najdete v tématu [čas synchronizace](../profiling/synchronization-time.md).  
  
- **VSTUPNĚ-VÝSTUPNÍCH OPERACÍ**  
  **Vstupně-výstupních operací** sestava ukazuje volání, které jsou zodpovědné za vstupně-výstupních operací bloky, společně s celkový blokování časy každý zásobník volání. Další informace najdete v tématu [čas I/O (zobrazení vláken)](../profiling/i-o-time-threads-view.md).  
  
- **Přejít do režimu spánku**  
  **z režimu spánku** sestava ukazuje volání, které jsou zodpovědné za z režimu spánku bloky, společně s celkový blokování časy každý zásobník volání. Další informace najdete v tématu [doba spánku](../profiling/sleep-time.md).  
  
- **Správa paměti**  
  **Správa paměti** sestava ukazuje volání, kde Správa bloky paměti došlo k chybě, spolu s celkem blokování časy každý zásobník volání. Tyto informace slouží k identifikaci oblasti, které mají nadměrné stránkování nebo uvolňování paměti kolekce problémy.  Další informace najdete v tématu [čas správy paměti](../profiling/memory-management-time.md).  
  
- **Přerušení**  
  **Přerušení** sestava zobrazí aktuální proces přepnuto procesy v systému, kde jednotlivé vlákna, která nahradí vlákna v aktuálním procesu. Tyto informace můžete použít k identifikaci procesy a vlákna, které nejvíce odpovídají za přerušení. Další informace najdete v tématu [čas přerušení](../profiling/preemption-time.md).  
  
- **Zpracování uživatelského rozhraní**  
  **Zpracování uživatelského rozhraní** sestava ukazuje volání, které jsou zodpovědné za uživatelské rozhraní zpracování bloky, společně s celkový blokování časy každý zásobník volání. Další informace najdete v tématu [doba zpracování uživatelského rozhraní](../profiling/ui-processing-time.md).  
  
- **Souhrn podle vláken**  
  Vyberte **Souhrn podle vláken** zobrazit graf zobrazující stav vláken pro aktuálně vybraný časový interval. Barevně rozlišená sloupce zobrazit celkový čas, po každé vlákno trvání spuštění, zablokuje vstupně-výstupní operace a dalších státech. Vláken jsou označeny jako v dolní části. Při úpravě úroveň zvětšení v grafu časovou osu tohoto grafu se automaticky aktualizuje. 
  
  Na některých úrovních přiblížení nemusí zobrazit některá vlákna v grafu. Pokud k tomu dojde, symbol tří teček (**...** ) se zobrazí na pravé straně. Pokud vlákno, které chcete, aby se nezobrazí, můžete skrýt ostatní vlákna. Další informace najdete v tématu [sestava souhrnu podle vláken](../profiling/per-thread-summary-report.md).  
  
- **Operace disků**  
  Vyberte **diskových operací** Zobrazit procesy a vlákna zahrnutých v / v disku pro aktuální proces, soubory, dotčená (například byly načteny knihovny DLL), kolik bajtů se číst a další informace. Tato sestava slouží k vyhodnocení času stráveného přístup k souborů během provádění, zejména v případě, že váš proces zdá se, že se vstupně-výstupní. Další informace najdete v tématu [sestavu operací disku](../profiling/disk-operations-report-threads-view.md).  
  
### <a name="current-tab"></a>Aktuální karta  
Tato karta zobrazuje zásobník volání pro vybraný bod na segment vlákna v časové osy grafu. Zásobníky volání se ořízne na Zobrazit pouze aktivity, které se vztahují k vaší aplikaci.  
  
### <a name="unblocking-stack-tab"></a>Karta odblokování zásobníku 
Tato karta ukazuje, které vlákno odblokováno zvoleném vlákně a odblokování zásobníku volání.  
  
## <a name="see-also"></a>Viz také:  
 [Vizualizér souběžnosti](../profiling/concurrency-visualizer.md)
