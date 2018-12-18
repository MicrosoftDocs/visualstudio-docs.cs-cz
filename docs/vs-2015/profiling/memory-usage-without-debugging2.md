---
title: Využití paměti bez Debugging2 | Dokumentace Microsoftu
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
ms.assetid: 24238fc0-40b8-4079-8579-698211db9a26
caps.latest.revision: 18
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ebd4dd187f2b976ca7861f95609dd6ce8d8d318f
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51808573"
---
# <a name="memory-usage-without-debugging"></a>Využití paměti bez ladění
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Můžete použít **využití paměti** nástroje bez ladění můžete provádět následující  
  
- Sledování vaší aplikace paměti při vývoji scénáři použít přímo v sadě Visual Studio.  
  
- Vytvořte podrobný snímek stavu paměti aplikace.  
  
- Porovnejte snímky k nalezení původní příčiny problémů s pamětí.  
  
  Toto téma popisuje, jak pomocí nástroje využití paměti analýza XAML Universal Windows app. Pokud chcete analyzovat využití paměti ve Windows Universal apps, které používají jazyk JavaScript a HTML, naleznete v tématu [analýza využití paměti (JavaScript)](http://msdn.microsoft.com/library/windows/apps/jj819176.aspx).  
  
##  <a name="BKMK_Start_a_Memory_Usage_diagnostic_session"></a> Spuštění diagnostické relace využití paměti  
  
1.  Otevřete projekt Windows Universal C# v sadě Visual Studio.  
  
2.  V panelu nabídky zvolte **ladění / Profiler výkonu...** .  
  
3.  Vyberte **využití paměti** a klikněte na tlačítko **Start** tlačítko v dolní části stránky.  
  
     ![Spuštění diagnostické relace využití paměti](../profiling/media/memuse-start-diagnosticssession.png "MEMUSE_Start_DiagnosticsSession")  
  
##  <a name="BKMK_Monitor_memory_use"></a> Monitorovat využití paměti  
 Přestože lze použít **využití paměti** nástroj pro generování podrobných sestav, které můžete najít a opravit problémy, také vám pomůže ho v reálném čase paměti účinky scénář aktivně vyvíjíte.  
  
 Při spuštění diagnostické relace spuštění vaší aplikace a **diagnostické nástroje** okna zobrazuje časové osy grafu využití paměti vaší aplikace.  
  
 ![Stránka s přehledem využití paměti](../profiling/media/memuse-reportoverview.png "MEMUSE__ReportOverview")  
  
 Časová osa graf ukazuje kolísání v paměti aplikace při jejím spuštění. Poraďte se špičkami grafu obvykle naznačují, že nějaký kód je shromažďování nebo vytváření dat a po dokončení zpracování se odstraní. Extrémní značit kritický bod, ke které je možné optimalizovat. Důležitější je nárůst využití paměti, která nevrátí, protože to může znamenat neefektivní využití paměti nebo dokonce nevracení paměti.  
  
###  <a name="BKMK_Close_a_monitoring_session"></a> Ukončit relaci sledování  
 ![Zastavit shromažďování](../profiling/media/memuse-stopcollection.png "MEMUSE__StopCollection")  
  
 Zastavit relaci sledování bez vytváření sestav, pouze zavřete okno diagnostiky. Chcete-li generovat sestavu, když jste pořídili snímky paměti, zvolte **Zastavit**.  
  
##  <a name="BKMK_Take_snapshots_to_analyze_the_memory_state_of_your_app"></a> Pořizovat snímky stavu paměti aplikace  
 Pokud zjistíte chybu paměti, kterou chcete prozkoumat, můžete také pořizovat snímky během diagnostické relace zachycení objektů v paměti v určité chvíli. Vzhledem k tomu, že aplikace používá velké množství mnoha typů objektů, může být vhodné soustředit se na jeden scénář analýzy. Je také vhodné získat snímek směrného plánu aplikace, než se zobrazí paměť problém, jiný snímek po prvním výskytu tohoto problému a nejmíň jeden další snímky Pokud scénář, můžete opakovat.  
  
 Shromažďování snímků, spusťte novou relaci diagnostiky. Zvolte **snímku trvat** když potřebujete zachytit data paměti. Chcete-li generovat sestavy, zvolte **Zastavit**.  
  
##  <a name="BKMK_Memory_Usage_overview_page"></a> Stránka s přehledem využití paměti  
 Poté, co zastavíte shromažďování dat, nástroj využití paměti aplikace ukončí a zobrazí přehled sestav.  
  
 ![Stránka s přehledem využití paměti](../profiling/media/memuse-reportoverview.png "MEMUSE__ReportOverview")  
  
###  <a name="BKMK_Memory_Usage_snapshot_views"></a> Zobrazení snímku využití paměti  
 Pomocí zobrazení snímku v nových oknech sady Visual Studio otevřete podrobné sestavy. Existují dva druhy zobrazení snímku:  
  
- A [snímku podrobnosti sestavy](../profiling/memory-usage-without-debugging2.md#BKMK_Snapshot_details_reports) ukazuje typy a instance v jeden snímek.  
  
- A [rozdíl (rozdíl) sestavy snímků](../profiling/memory-usage-without-debugging2.md#BKMK_Snapshot_difference__diff__reports) porovnává typy a instance v dvěma snímky.  
  
  ![Zobrazit odkazy na pořízení snímku](../profiling/media/memuse-snapshotview-numbered.png "MEMUSE__SnapshotView_Numbered")  
  
  Číslované položky obrázku zobrazení snímku jsou odkazy, které otevřete zobrazení sestav využití paměti.  
  
|||  
|-|-|  
|![1. krok](../profiling/media/procguid-1.png "ProcGuid_1")|Text odkazu zobrazuje celkový počet bajtů v paměti při pořízení snímku.<br /><br /> Vyberte tento odkaz zobrazíte podrobnosti sestavy snímku, který je seřazen podle celkové velikosti instance typu.|  
|![2. krok](../profiling/media/procguid-2.png "ProcGuid_2")|Text odkazu zobrazuje celkový počet objektů v paměti při pořízení snímku.<br /><br /> Vyberte tento odkaz zobrazíte podrobnosti sestavy snímku, který je seřazen podle počtu instancí typů.|  
|![3. krok](../profiling/media/procguid-3.png "ProcGuid_3")|Text odkazu zobrazuje rozdíl mezi celková velikost objektů v paměti v tuto chvíli tento snímek a celkovou velikost předchozí snímek.<br /><br /> Text odkazu je kladné číslo, pokud velikost paměti snímku je větší než předchozí a záporné číslo, pokud velikost je menší. Text odkazu **směrného plánu** označuje, že tento snímek je první v relaci diagnostiky. **Žádný rozdíl** označuje, že rozdíl je nula.<br /><br /> Vyberte tento odkaz zobrazíte sestavu snímku rozdíl, který je seřazen podle rozdíl celkové velikosti instance typů.|  
|![4. krok](../profiling/media/procguid-4.png "ProcGuid_4")|Text odkazu zobrazuje rozdíl mezi celkový počet objektů v paměti v tomto snímku a počet objektů v předchozím snímkem.<br /><br /> Vyberte tento odkaz zobrazíte sestavu snímku rozdíl, který je seřazen podle rozdíl v celkovém počtu instancí typů.|  
  
##  <a name="BKMK_Snapshot_reports"></a> Sestavy snímků  
 ![Sestavu snímku využití paměti](../profiling/media/memuse-snapshotreport-all.png "MEMUSE_SnapshotReport_All")  
  
###  <a name="BKMK_Snapshot_report_trees"></a> Stromy sestavy snímku  
  
####  <a name="BKMK_Managed_Heap"></a> Spravovaná halda  
 Spravovaná halda stromu [stromu spravované haldy (podrobnosti o snímku)](../profiling/memory-usage-without-debugging2.md#BKMK_Managed_Heap_tree__Snapshot_details_) a [stromu spravované haldy (rozdíl snímku)](../profiling/memory-usage-without-debugging2.md#BKMK_Managed_Heap_tree__Snapshot_diff_) zobrazit typy a instance v sestavě. Výběr typu nebo instance zobrazí **cesty ke kořenu** a **odkazované objekty** stromů pro vybranou položku.  
  
####  <a name="BKMK_Paths_to_Root"></a> Cesty ke kořenu  
 [Cesty ke kořenové stromu (podrobnosti o snímku)](../profiling/memory-usage-without-debugging2.md#BKMK_Paths_to_Root_tree__Snapshot_details_) a [cesty ke kořenové stromu (snímek diff)](../profiling/memory-usage-without-debugging2.md#BKMK_Paths_to_Root_tree__Snapshot_diff_) zobrazit řetězec objekty, které odkazují na tento typ nebo instance. Paměť pro objekt vyčistí systému uvolňování paměti rozhraní .NET Framework, pouze v případě, že všechny odkazy na něj byly vydány.  
  
####  <a name="BKMK_Referenced_Objects"></a> Odkazované objekty  
 [Stromu odkazované objekty (podrobnosti o snímku)](../profiling/memory-usage-without-debugging2.md#BKMK_Referenced_Objects_tree__Snapshot_details_) a [stromu odkazované objekty (rozdíl snímku)](../profiling/memory-usage-without-debugging2.md#BKMK_Referenced_Objects_tree__Snapshot_diff_) zobrazit objekty, které se odkazuje vybraný typ nebo instance.  
  
###  <a name="BKMK_Object_Type_and_Instance_fields"></a> Typ objektu a Instance pole  
 Když **typ objektu** položka obsahuje podřízené položky, můžete vybrat ikonu šipky k jejich zobrazení. Pokud barvu **typ objektu** text je modrá, můžete ho chcete přejít na objekt v jeho souboru se zdrojovým kódem. Zdrojový soubor se otevře v samostatném okně.  
  
 Názvy instancí jsou jedinečné identifikátory, které jsou generovány pomocí nástroje využití paměti.  
  
 Pokud si všimnete typ, který nelze snadno identifikovat, nebo pokud si nejste jisti, jak je zahrnuta ve vašem kódu, je pravděpodobně objektu z rozhraní .NET Framework, operační systém nebo kompilátoru, která zobrazuje nástroj využití paměti, protože je součástí řetězce vlastnictví objekty.  
  
###  <a name="BKMK_Report_tree_filters_"></a> Filtry sestav stromu  
 Většina aplikací obsahuje překvapivě velký počet typů, z nichž většina nejsou velmi zajímavé pro vývojáře aplikace. **Využití paměti** nástroj definuje dva filtry, které můžete použít ke skrytí většina z těchto typů v **spravované haldy** a **cesty ke kořenu** stromové struktury. Větve můžete také filtrovat podle názvu typu.  
  
 ![Možnosti řazení a filtrování](../profiling/media/memuse-sortandfilter.png "MEMUSE_SortAndFilter")  
  
####  <a name="BKMK_Filter"></a> Filtr  
 Zadejte řetězec **filtr** políčka můžete omezit stromu se zobrazí na typy, které obsahují zadaný text. Filtr není velká a malá písmena a rozpozná zadaného řetězce v libovolné části názvu typu.  
  
####  <a name="BKMK_Collapse_Small_Objects"></a> Sbalit malé objekty  
 Při použití tohoto filtru, typy, jejichž **velikost (bajty)** je menší než 0,5 procent celkové velikosti paměti snímku jsou skryté v **spravované haldy** seznamu.  
  
####  <a name="BKMK_Just_My_Code"></a> Pouze můj kód  
 **Pouze můj kód** filtr skryje největším množstvím instancí, které se vygenerovaly externí kód. Externí typy jsou vlastní operační systém nebo komponentami rozhraní nebo jsou generovány kompilátorem.  
  
##  <a name="BKMK_Snapshot_details_reports"></a> Podrobnosti sestavy snímku  
 Sestava podrobnosti o snímku vám soustředit se na jeden snímek z diagnostické relace. Podrobnosti chcete sestavu otevřít, zvolte jeden z odkazů v zobrazení snímku, jak je znázorněno na následujícím obrázku. Oba odkazy otevřít stejné sestavy. jediným rozdílem je výchozí pořadí řazení **spravované haldy** stromu v sestavě. V obou případech můžete změnit pořadí řazení po sestava se otevře.  
  
 ![Odkazy na sestavy snímku v zobrazení snímku](../profiling/media/memuse-snapshotview-snapshotdetailslinks.png "MEMUSE_SnapshotView_SnapshotDetailsLinks")  
  
-   **MB** seřadí sestavy podle odkazu **celkové velikosti (bajty)** sloupce.  
  
-   **Objekty** seřadí sestavy podle odkazu **počet** sloupce.  
  
###  <a name="BKMK_Managed_Heap_tree__Snapshot_details_"></a> Spravovaná halda stromu (podrobnosti o snímku)  
 **Spravované haldy** stromu jsou uvedeny typy objektů, které jsou uložené v paměti. Můžete rozbalit název typu, chcete-li zobrazit deset největších instance daného typu, seřazené podle velikosti. Výběr typu nebo instance zobrazí **cesty ke kořenu** a **odkazované objekty** stromů pro vybranou položku.  
  
 ![Spravované haldy stromu](../profiling/media/memuse-snapshotdetails-managedheaptree.png "MEMUSE__SnapshotDetails_ManagedHeapTree")  
  
|||  
|-|-|  
|**Typ objektu**|Název instance typu nebo objekt.|  
|**Počet**|Počet instancí objektu typu. Číslo je vždy 1 pro instanci.|  
|**Velikost (bajty)**|Pro typ, velikost všechny instance daného typu v snímek paměti, s výjimkou velikost objektů obsažených v instancích.<br /><br /> Pro instance, typ, velikost objektu s výjimkou velikost objekty obsažené v instanci. instance.|  
|**Celková velikost (bajty)**|Velikost instance daného typu nebo velikosti jednu instanci, včetně velikosti obsažené objekty.|  
  
###  <a name="BKMK_Paths_to_Root_tree__Snapshot_details_"></a> Cesty ke kořenové stromu (podrobnosti o snímku)  
 **Cesty do stromové struktury kořenové** ukazuje řetězec objekty, které odkazují na tento typ nebo instance. Paměť pro objekt vyčistí systému uvolňování paměti rozhraní .NET Framework, pouze v případě, že všechny odkazy na něj byly vydány.  
  
 ![Cesty ke kořenu stromu pro typy](../profiling/media/memuse-snapshotdetails-type-pathstoroottree.png "MEMUSE_SnapshotDetails_Type_PathsToRootTree")  
  
 Při zobrazení typu v **cesty ke kořenu** stromu, počet objektů typy, které obsahují odkazy na tento typ se zobrazí v **počet odkazů** sloupce. Sloupec nezobrazí při analýze instance.  
  
###  <a name="BKMK_Referenced_Objects_tree__Snapshot_details_"></a> Odkazovaný stromové struktury objektů (podrobnosti o snímku)  
 **Odkazované objekty** Strom zobrazuje objekty, které se odkazuje vybraný typ nebo instance.  
  
 ![Odkazovaný stromové struktury Objjects pro instance](../profiling/media/memuse-snapshotdetails-referencedobjects-instance.png "MEMUSE_SnapshotDetails_ReferencedObjects_Instance")  
  
|||  
|-|-|  
|**Typ objektu / Instance**|Název instance typu nebo objekt.|  
|**Velikost (bajty)**|Pro typ, velikost všechny instance daného typu, s výjimkou velikost objektů obsažených v typu.<br /><br /> Pro instance, velikost objektu, s výjimkou velikost objektů obsažených v objektu.|  
|**Celková velikost (bajty)**|Celková velikost instance daného typu nebo velikosti instance, včetně velikosti obsažené objekty.|  
  
##  <a name="BKMK_Snapshot_difference__diff__reports"></a> Sestavy snímku rozdíl (rozdíl)  
 Sestavy snímku rozdíl (rozdíl) ukazuje změny mezi primární snímek a snímek, který byla pořízen bezprostředně před. Otevřete sestavu změn, zvolte jeden z odkazů v zobrazení snímku, jak je znázorněno na následujícím obrázku. Oba odkazy otevřít stejné sestavy. jediným rozdílem je výchozí pořadí řazení **spravované haldy** stromu v sestavě. Po otevření sestavy můžete změnit pořadí řazení.  
  
 ![Odkazy na rozdíl sestava v zobrazení snímku](../profiling/media/memuse-snapshotview-snapshotdifflinks.png "MEMUSE_SnapshotView_SnapshotDiffLinks")  
  
-   **MB** seřadí sestavy podle odkazu **celkové velikosti (bajty)** sloupce.  
  
-   **Objekty** seřadí sestavy podle odkazu **počet** sloupce.  
  
###  <a name="BKMK_Managed_Heap_tree__Snapshot_diff_"></a> Spravovaná halda stromu (snímek diff)  
 **Spravované haldy** stromu jsou uvedeny typy objektů, které jsou uložené v paměti. Můžete rozbalit název typu, chcete-li zobrazit deset největších instance daného typu, seřazené podle velikosti. Výběr typu nebo instance zobrazí **cesty ke kořenu** a **odkazované objekty** stromů pro vybranou položku.  
  
 ![Spravované haldy strom pro typ v sestavě rozdíl](../profiling/media/memuse-snapshotdiff-type-heap.png "MEMUSE_SnapshotDiff_Type_Heap")  
  
 Všimněte si, že **počet**, **velikost (bajty)**, a **celkové velikosti (bajty)** sloupce mají došlo ke sbalení na obrázku.  
  
|||  
|-|-|  
|**Typ objektu**|Název instance typu nebo objekt.|  
|**Počet**|Počet instancí určitého typu ve primárního snímku. **Počet** je vždy 1 pro instanci.|  
|**Počet změn**|Pro typ, rozdíl v počtu instancí typu mezi primární snímek a předchozí snímek. Je toto pole prázdné pro instanci.|  
|**Velikost (bajty)**|Velikost objektů ve primárního snímku, s výjimkou velikost objekty obsažené v objektech. Pro typ **velikost (bajty)** a **celkové velikosti (bajty)** jsou celkový součet velikostí instancí typu.|  
|**Rozdíl celkové velikosti (bajty)**|Pro typ, rozdíl celkové velikosti instance daného typu mezi primární snímek a předchozí snímek, s výjimkou velikost objektů obsažených v instancích. Je toto pole prázdné pro instanci.|  
|**Celková velikost (bajty)**|Velikost objektů ve primárního snímku, včetně velikosti objekty obsažené v objektech.|  
|**Rozdíl celkové velikosti (bajty)**|Pro typ, velikosti všechny instance daného typu rozdíl mezi primární snímek a předchozí snímek, včetně velikosti objekty obsažené v objektech. Je toto pole prázdné pro instanci.|  
  
###  <a name="BKMK_Paths_to_Root_tree__Snapshot_diff_"></a> Cesty ke kořenové stromu (snímek diff)  
 **Cesty do stromové struktury kořenové** ukazuje řetězec objekty, které odkazují na tento typ nebo instance. Paměť pro objekt vyčistí systému uvolňování paměti rozhraní .NET Framework, pouze v případě, že všechny odkazy na něj byly vydány.  
  
 ![Cesty k kořenové strom pro instance v rozdílovém zobrazení](../profiling/media/memuse-snapshotdiff-pathstoroot-instance-all.png "MEMUSE_SnapshotDiff_PathsToRoot_Instance_All")  
  
###  <a name="BKMK_Referenced_Objects_tree__Snapshot_diff_"></a> Odkazovaný stromové struktury objektů (snímek diff)  
 **Odkazované objekty** Strom zobrazuje objekty, které odkazuje na primární typu nebo instance.  
  
 ![Odkazovaný stromové struktury Objjects pro instance](../profiling/media/memuse-snapshotdetails-referencedobjects-instance.png "MEMUSE_SnapshotDetails_ReferencedObjects_Instance")  
  
|||  
|-|-|  
|**Typ objektu / Instance**|Název instance typu nebo objekt.|  
|**Velikost (bajty)**|Pro instance, velikost objektu ve primárního snímku, s výjimkou velikost objekty obsažené v instanci.<br /><br /> Pro typ, celková velikost instance daného typu ve primárního snímku, s výjimkou velikost objekty obsažené v instanci.|  
|**Celková velikost (bajty)**|Velikost objektů ve primárního snímku, včetně velikosti objekty obsažené v objektech.|  
  
## <a name="see-also"></a>Viz také  
 [Paměti jazyka JavaScript](../profiling/javascript-memory.md)   
 [Analýza výkonu aplikace](http://msdn.microsoft.com/library/58acb30b-8428-41a6-b195-b0fdedb89575)   
 [Spustit výkonu a diagnostické nástroje](http://msdn.microsoft.com/library/788279d8-f56b-40a0-9bef-facc3dfba471)   
 [Osvědčené postupy z hlediska výkonu pro aplikace Windows Store pomocí jazyka C++, C# a Visual Basic](http://msdn.microsoft.com/library/windows/apps/hh750313.aspx)   
 [Diagnostika problémů s pamětí pomocí nového nástroje využití paměti v aplikaci Visual Studio](http://go.microsoft.com/fwlink/p/?LinkId=394706)



