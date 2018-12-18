---
title: Analýza využití paměti bez ladění | Dokumentace Microsoftu
ms.custom: H1Hack27Feb2017
ms.date: 11/15/2018
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 4dcc5c66998501044b04e4a8265d669927e3368a
ms.sourcegitcommit: 54c65f81a138fc1e8ff1826f7bd9dcec710618cc
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/19/2018
ms.locfileid: "51948930"
---
# <a name="analyze-memory-usage-without-the-debugger"></a>Analýza využití paměti bez ladicího programu

**Využití paměti** nástroj monitoruje využití paměti vaší aplikace. Můžete použít nástroj pro zkoumání v reálném čase paměti účinky scénáře, které aktivně vyvíjíte v sadě Visual Studio. Je možné provést podrobné snímky stavu paměti aplikace a porovnat snímky můžete najít původní příčiny problémů paměti.  
  
**Využití paměti** nástroj můžete spustit s nebo bez ladicího programu. Následující pokyny ukazují, jak používat **využití paměti** nástroje bez ladicího programu v sadě Visual Studio **Profiler výkonu**. 

>[!NOTE]
>- K měření využití paměti pro aplikace .NET Core, je nutné použít **využití paměti** nástroj s ladicím programem. Pokyny najdete v tématu [profil využití paměti v aplikaci Visual Studio](memory-usage.md). 
>- Analýza využití paměti v aplikacích jazyka JavaScript a HTML UPW, použijte [paměti jazyka JavaScript](../profiling/javascript-memory.md) nástroj v **Profiler výkonu**.
  
## <a name="memory-usage-diagnostic-sessions"></a>Relace diagnostiky paměti využití  

**Spuštění diagnostické relace využití paměti:**

1. Otevřít C# Universal Windows (UPW) projektu v sadě Visual Studio.  
   
1. V panelu nabídky zvolte **ladění** > **Profiler výkonu**.  
   
1. Vyberte **využití paměti**a pak vyberte **Start**.  
   
   ![Spuštění diagnostické relace využití paměti](../profiling/media/memuse_start_diagnosticssession.png "spuštění diagnostické relace využití paměti")  
  
### <a name="monitor-memory-use"></a>Monitorovat využití paměti 

Při spuštění diagnostické relace spuštění vaší aplikace a **diagnostické nástroje** okna zobrazuje časové osy grafu využití paměti vaší aplikace.  

![Stránka s přehledem využití paměti](../profiling/media/memuse__reportoverview.png "MEMUSE__ReportOverview")  

Časová osa graf ukazuje kolísání paměti jako spuštění aplikace. Poraďte se špičkami grafu obvykle naznačují, že nějaký kód je shromažďování nebo vytváření dat a po dokončení zpracování se odstraní. Extrémní značit kritický bod, ke které je možné optimalizovat. Další případných potíží totiž nárůst využití paměti, která nevrátí, může to znamenat neefektivní využití paměti nebo dokonce nevracení paměti.  
  
### <a name="take-snapshots-of-app-memory-states"></a>Pořizovat snímky stavu paměti aplikace 

Aplikace používá velký počet objektů a může být vhodné soustředit se na jeden scénář analýzy. Nebo můžete zjistit problémy s pamětí o prověření. Můžete také pořizovat snímky během diagnostické relace zachycení využití paměti v určité chvíli. Je vhodné získat snímek směrného plánu aplikace předtím, než problém paměti se zobrazí, jiný snímek po prvním výskytu tohoto problému a další snímky, pokud scénář, můžete opakovat.  

Chcete-li shromažďovat snímky, vyberte **pořídit snímek** když potřebujete zachytit data paměti.  

###  <a name="BKMK_Close_a_monitoring_session"></a> Ukončete relaci diagnostiky  

Zastavit relaci sledování bez vytváření sestav, pouze zavřete okno diagnostiky. Aby se vygenerovala sestava, až to budete mít shromažďování nebo jste pořídili snímky, vyberte **zastavit shromažďování**.  

![Zastavit shromažďování](../profiling/media/memuse__stopcollection.png "zastavit shromažďování")  

##  <a name="memory-usage-reports"></a>Sestavy využití paměti 

Poté, co zastavíte shromažďování dat **využití paměti** nástroj aplikace ukončí a zobrazí **využití paměti** stránka s přehledem.  

![Stránka s přehledem využití paměti](../profiling/media/memuse__reportoverview1.png "stránka s přehledem využití paměti")  

### <a name="BKMK_Memory_Usage_snapshot_views"></a> Snímky využití paměti 

Čísla v **snímku** podokna zobrazení bajtů a objektů v paměti při pořízení jednotlivých snímků a rozdíl mezi předchozí a snímku. 

Čísla jsou odkazy, které otevřete podrobné **využití paměti** sestavy zobrazení v nových oknech sady Visual Studio. A [podrobnosti sestavu snímku](#snapshot-details-report) ukazuje typy a instance v jeden snímek. A [rozdíl (rozdíl) sestavu snímku](#snapshot-difference-diff-reports) porovnává typy a instance v dvěma snímky.  
  
  ![Zobrazit odkazy na pořízení snímku](../profiling/media/memuse__snapshotview_numbered.png "snímku zobrazit odkazy")  
  
|||  
|-|-|  
|![1. krok](../profiling/media/procguid_1.png "ProcGuid_1")|Celkový počet bajtů v paměti při pořízení snímku.<br /><br /> Vyberte tento odkaz zobrazíte podrobnosti sestavy snímku seřazené podle celkové velikosti instance typu.|  
|![2. krok](../profiling/media/procguid_2.png "ProcGuid_2")|Celkový počet objektů v paměti při pořízení snímku.<br /><br /> Vyberte tento odkaz zobrazíte podrobnosti sestavy snímku seřazené podle počtu instancí typů.|  
|![3. krok](../profiling/media/procguid_3.png "ProcGuid_3")|Rozdíl mezi celkovou velikost paměti objektů v tomto snímku a předchozí snímek. <br /><br /> Kladné číslo znamená velikosti paměti tohoto snímku je větší než předchozí verze a záporné číslo znamená velikost je menší. **Směrný plán** znamená, že snímku je první v diagnostické relace. **Žádný rozdíl** znamená, že rozdíl je nula.<br /><br /> Vyberte tento odkaz zobrazíte sestavu snímku diff seřazené podle rozdíl celkové velikosti instance typů.|  
|![4. krok](../profiling/media/procguid_4.png "ProcGuid_4")|Rozdíl mezi celkový počet objektů v paměti v tomto snímku a předchozí snímek.<br /><br /> Vyberte tento odkaz zobrazíte sestavu snímku diff seřazené podle rozdíl v celkovém počtu instancí typů.|  
  
## <a name="memory-usage-snapshot-reports"></a>Sestavy snímku využití paměti 

<a name="BKMK_Snapshot_report_trees"></a> Když vyberete jeden z odkazů snímku v **využití paměti** stránka s přehledem, se otevře na nové stránce sestavy snímku. 

![Sestavu snímku využití paměti](../profiling/media/memuse_snapshotreport_all.png "sestavu snímku využití paměti")  
  
V sestavě snímku, můžete rozbalit **typ objektu** položky k zobrazení podřízených položek. Názvy instancí jsou jedinečné identifikátory, které jsou generovány pomocí nástroje využití paměti. 

Pokud **typ objektu** je modrá, můžete ho vybrat přejít na objekt ve zdrojovém kódu v samostatném okně.  

Typy, které nelze identifikovat nebo jejichž zapojení ve vašem kódu, nevíte, jsou pravděpodobně v rozhraní .NET Framework, operační systém nebo objekty kompilátoru. **Využití paměti** nástroj zobrazí tyto objekty v případě, že jsou součástí řetězce vlastnictví objektů.  

V sestavě snímku: 

- **Spravované haldy** Strom zobrazuje typy a instance v sestavě. Výběr typu nebo instance zobrazí **cesty ke kořenu** a **odkazované objekty** stromů pro vybranou položku.  
  
- **Cesty ke kořenu** Strom zobrazuje řetězu objekty, které odkazují na typu nebo instance. Paměť pro objekt vyčistí systému uvolňování paměti rozhraní .NET Framework, pouze v případě, že všechny odkazy na něj byly vydány.  
  
- **Odkazované typy** nebo **odkazované objekty** Strom zobrazuje objekty, které se odkazuje vybraný typ nebo instance.  
  
###  <a name="BKMK_Report_tree_filters_"></a> Filtry sestav stromu  

Mnoho typů aplikací nejsou velmi zajímavé pro vývojáře aplikací. Filtry sestav snímků můžete skrýt většina z těchto typů v **spravované haldy** a **cesty ke kořenu** stromové struktury.   

![Možnosti řazení a filtrování](../profiling/media/memuse_sortandfilter.png "MEMUSE_SortAndFilter")  

- <a name="BKMK_Filter"></a> Chcete-li filtrovat podle názvu typu stromu, zadejte název do **filtr** pole. Filtr se velká a malá písmena a rozpozná zadaného řetězce v libovolné části názvu typu.  
  
- <a name="BKMK_Collapse_Small_Objects"></a> Vyberte **sbalit malé objekty** v **filtr** rozevírací nabídku a skrýt typy, jejichž **velikost (bajty)** je menší než 0,5 procento celkové paměti.  
  
- <a name="BKMK_Just_My_Code"></a> Vyberte **pouze můj kód** v **filtr** rozevírací nabídku a skrýt největším množstvím instancí, které se vygenerovaly externí kód. Externí typy patří do operačního systému nebo komponenty rozhraní nebo jsou generovány kompilátorem.  
  
## <a name="snapshot-details-reports"></a>Podrobnosti sestavy snímku  

 Sestava podrobnosti o snímku popisuje jeden snímek z diagnostické relace. Otevřete sestavu, výběrem odkazu velikost nebo objektů v podokně snímku. 

 ![Odkazy na sestavy snímku v podokně snímku](../profiling/media/memuse_snapshotview_snapshotdetailslinks.png "odkazy na sestavy snímku v podokně snímku")  
  
Oba odkazy otevřít stejnou sestavu. Jediným rozdílem je výchozí pořadí řazení **spravované haldy** stromu. Odkaz na velikost seřadí záznamy podle **celkové velikosti (bajty)** sloupce. Odkaz na objekty seřadí záznamy podle **počet** sloupce. Sloupec pro řazení nebo pořadí můžete změnit po otevření sestavy.  
  
###  <a name="BKMK_Managed_Heap_tree__Snapshot_details_"></a> Spravovaná halda stromu (podrobnosti sestavy snímků)  
 **Spravované haldy** stromu jsou uvedeny typy objektů, které jsou uložené v paměti. Rozbalte název typu, chcete-li zobrazit deset největších instance daného typu, seřazené podle velikosti. Vyberte typ nebo instanci. Chcete-li zobrazit **cesty ke kořenu** a **odkazované objekty** stromů pro vybranou položku.  
  
 ![Spravované haldy stromu](../profiling/media/memuse__snapshotdetails_managedheaptree.png "stromu spravované haldy")  
  
**Spravované haldy** stromu v podrobnosti sestavy snímku má následující sloupce:

|||  
|-|-|  
|**Typ objektu**|Název instance typu nebo objekt.|  
|**Počet**|Počet instancí objektu typu. **Počet** je vždy 1 pro instanci.|  
|**Velikost (bajty)**|Pro typ, velikost všechny instance typu ve snímku, menší velikost objektů obsažených v instancích.<br /><br /> Pro instance, velikost objektu menší velikost objekty obsažené v instanci. |  
|**Celková velikost (bajty)**|Velikost instance daného typu nebo velikosti jednu instanci, včetně velikosti obsažené objekty.|  
|**Modul**|Modul, který obsahuje objekt.|  
  
###  <a name="BKMK_Paths_to_Root_tree__Snapshot_details_"></a> Cesty ke kořenové stromu (snímek podrobnosti sestavy)  
**Cesty do stromové struktury kořenové** ukazuje řetězec objekty, které odkazují na typu nebo instance. Paměť pro objekt vyčistí systému uvolňování paměti rozhraní .NET Framework, pouze v případě, že všechny odkazy na něj byly vydány.  
  
Pro typ v **cesty ke kořenu** stromu se zobrazí v počtu objektů, které obsahují odkazy na daný typ **počet odkazů** sloupce. 

![Cesty ke kořenu stromu pro typy](../profiling/media/memuse_snapshotdetails_type_pathstoroottree.png "cesty ke kořenu stromu pro typy")  
  
###  <a name="BKMK_Referenced_Objects_tree__Snapshot_details_"></a> Odkazované typy nebo odkazované objekty stromové struktury (snímek podrobnosti sestavy)  
**Odkazované typy** nebo **odkazované objekty** Strom zobrazuje objekty, které se odkazuje vybraný typ nebo instance.  
  
![Odkazovaný stromové struktury objektů pro instance](../profiling/media/memuse_snapshotdetails_referencedobjects_instance.png "odkazované objekty strom pro instance")  
  
A **odkazované typy** stromu v podrobnosti sestavy snímku má následující sloupce. A **odkazované objekty** stromu nemá **počet odkazů** sloupce.

|||  
|-|-|  
|**Typ objektu** nebo **Instance**|Název typu nebo instance.|  
|**Počet odkazů**|U typů, počet instancí objektu typu.|  
|**Velikost (bajty)**|Pro typ, velikost všechny instance typu menší velikost objektů obsažených v typu.<br /><br /> Pro instance, velikost objektu menší velikost objektů obsažených v objektu.|  
|**Celková velikost (bajty)**|Celková velikost instance daného typu nebo velikosti instance, včetně velikosti obsažené objekty.|  
|**Modul**|Modul, který obsahuje objekt.|  
  
## <a name="snapshot-difference-diff-reports"></a>Sestavy snímku rozdíl (rozdíl)  

Sestavy snímku rozdíl (rozdíl) ukazuje změny mezi primární snímek a předchozí snímek. Otevřete sestavu změn, vyberte jeden z odkazů rozdíl v podokně snímku. 

Oba odkazy otevřít stejnou sestavu. Jediným rozdílem je výchozí pořadí řazení **spravované haldy** stromu v sestavě. Odkaz na velikost seřadí záznamy podle **rozdíl celkové velikosti (bajty)** sloupce. Odkaz na objekty seřadí záznamy podle **počet Diff** sloupce. Sloupec pro řazení nebo pořadí můžete změnit po otevření sestavy.  
  
 ![Odkazy na rozdíl sestav v podokně snímku](../profiling/media/memuse_snapshotview_snapshotdifflinks.png "odkazy na rozdíl sestav v podokně snímku")  
  
###  <a name="BKMK_Managed_Heap_tree__Snapshot_diff_"></a> Spravované haldy stromu (snímek diff sestav) 

 **Spravované haldy** stromu jsou uvedeny typy objektů, které jsou uložené v paměti. Můžete rozbalit název typu, chcete-li zobrazit deset největších instance daného typu, seřazené podle velikosti. Vyberte typ nebo instanci. Chcete-li zobrazit **cesty ke kořenu** a **odkazované objekty** stromů pro vybranou položku.  
  
 ![Strom spravované haldy pro typ v sestavě rozdíl](../profiling/media/memuse_snapshotdiff_type_heap.png "stromu spravované haldy pro typ v sestavě rozdíl")  
  
**Spravované haldy** stromu v sestavě snímek diff má následující sloupce:

|||  
|-|-|  
|**Typ objektu**|Název instance typu nebo objekt.|  
|**Počet**|Počet instancí určitého typu ve primárního snímku. **Počet** je vždy 1 pro instanci.|  
|**Počet změn**|Pro typ, rozdíl v počtu instancí typu mezi primární snímek a předchozí snímek. Je toto pole prázdné pro instanci.|  
|**Velikost (bajty)**|Velikost objektů ve primárního snímku menší velikost objektů v objektech. Pro typ **velikost (bajty)** a **celkové velikosti (bajty)** jsou celkový součet velikostí instancí typu.|  
|**Rozdíl celkové velikosti (bajty)**|Pro typ, rozdíl celkové velikosti instance daného typu mezi primární snímek a předchozí snímek menší velikost objektů v instancích. Je toto pole prázdné pro instanci.|  
|**Celková velikost (bajty)**|Velikost objektů ve primárního snímku, včetně velikost objektů v objektech.|  
|**Rozdíl celkové velikosti (bajty)**|Pro typ, velikosti všechny instance daného typu rozdíl mezi primární snímek a předchozí snímek, včetně velikost objektů v objektech. Je toto pole prázdné pro instanci.|  
|**Modul**|Modul, který obsahuje objekt.|  
  
###  <a name="BKMK_Paths_to_Root_tree__Snapshot_diff_"></a> Cesty ke kořenové stromu (snímek diff sestav)  

**Cesty do stromové struktury kořenové** ukazuje řetězec objekty, které odkazují na typu nebo instance. Paměť pro objekt vyčistí systému uvolňování paměti rozhraní .NET Framework, pouze v případě, že všechny odkazy na něj byly vydány. 

Pro typ v **cesty ke kořenu** stromu se zobrazí v počtu objektů, které obsahují odkazy na daný typ **počet odkazů** sloupce. Rozdíl v počtu z předchozího snímku je **odkaz Diff** sloupec. 

 ![Cesty k kořenové stromu v sestavě diff](../profiling/media/memuse_snapshotdiff_pathstoroot_instance_all.png "cesty do kořenové větve v diff sestavy")  
  
###  <a name="BKMK_Referenced_Objects_tree__Snapshot_diff_"></a> Odkazované typy nebo odkazované objekty stromu (snímek diff sestav)  

**Odkazované typy** nebo **odkazované objekty** Strom zobrazuje objekty, které se odkazuje vybraný typ nebo instance.  

![Odkazované typy v sestavě diff](../profiling/media/memuse_snapshotdiff_referencedtypes.png "odkazované typy v sestavě diff")  

A **odkazované typy** stromu v sestavě snímek diff má následující sloupce. A **odkazované objekty** strom má **Instance**, **velikost (bajty)**, **celkové velikosti (bajty)**, a **modulu** sloupce.

|||  
|-|-|  
|**Typ objektu** nebo **Instance**|Název instance typu nebo objekt.|  
|**Počet odkazů**|Počet instancí určitého typu ve primárního snímku.|  
|**Rozdíl počtu odkazů**|Pro typ, rozdíl v počtu instancí typu mezi primární snímek a předchozí snímek.|  
|**Velikost (bajty)**|Velikost objektů ve primárního snímku menší velikost objektů v objektech. Pro typ **velikost (bajty)** a **celkové velikosti (bajty)** jsou celkový součet velikostí instancí typu.|  
|**Rozdíl celkové velikosti (bajty)**|Pro typ, rozdíl celkové velikosti instance daného typu mezi primární snímek a předchozí snímek menší velikost objektů v instancích. |  
|**Celková velikost (bajty)**|Velikost objektů ve primárního snímku, včetně velikost objektů v objektech.|  
|**Rozdíl celkové velikosti (bajty)**|Pro typ, velikosti všechny instance daného typu rozdíl mezi primární snímek a předchozí snímek, včetně velikost objektů v objektech.|  
|**Modul**|Modul, který obsahuje objekt.|  

## <a name="see-also"></a>Viz také:  
 [Paměti jazyka JavaScript](../profiling/javascript-memory.md)  
 [Profilace v sadě Visual Studio](../profiling/index.md)  
 [Nejdřív se podívejte na nástroje pro profilaci](../profiling/profiling-feature-tour.md)  
 [Osvědčené postupy z hlediska výkonu pro aplikace pro UPW pomocí jazyka C++, C# a Visual Basic](/previous-versions/windows/apps/hh750313\(v\=win.10\))   
 [Diagnostika problémů s pamětí pomocí nového nástroje využití paměti v aplikaci Visual Studio](http://go.microsoft.com/fwlink/p/?LinkId=394706)