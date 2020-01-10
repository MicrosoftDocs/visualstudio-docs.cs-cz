---
title: Využití paměti bez Debugging2 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
ms.assetid: 24238fc0-40b8-4079-8579-698211db9a26
caps.latest.revision: 18
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 37db8a095e8f7b420f14df29de30f265aee49bb6
ms.sourcegitcommit: c150d0be93b6f7ccbe9625b41a437541502560f5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/10/2020
ms.locfileid: "75850809"
---
# <a name="memory-usage-without-debugging"></a>Využití paměti bez ladění
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Nástroj **využití paměti** bez ladění můžete použít k následujícím akcím:  
  
- Monitorujte přímo využití paměti vaší aplikace v aplikaci Visual Studio při vývoji scénáře.  
  
- Vytvořte podrobné snímky stavu paměti vaší aplikace.  
  
- Porovnejte snímky a najděte hlavní příčinu problémů s pamětí.  
  
  Toto téma popisuje, jak používat nástroj využití paměti k analýze aplikace Windows Universal XAML. Pokud chcete analyzovat využití paměti v univerzálních aplikacích pro Windows, které používají JavaScript a HTML, přečtěte si téma [Analýza využití paměti (JavaScript)](https://msdn.microsoft.com/library/windows/apps/jj819176.aspx).  
  
## <a name="BKMK_Start_a_Memory_Usage_diagnostic_session"></a>Spustit relaci diagnostiky využití paměti  
  
1. Otevřete C# univerzální projekt pro Windows v aplikaci Visual Studio.  
  
2. Na panelu nabídek vyberte **ladit/výkon Profiler...** .  
  
3. Vyberte **využití paměti** a pak klikněte na tlačítko **Start** v dolní části stránky.  
  
     ![Spustit relaci diagnostiky využití paměti](../profiling/media/memuse-start-diagnosticssession.png "MEMUSE_Start_DiagnosticsSession")  
  
## <a name="BKMK_Monitor_memory_use"></a>Monitorovat využití paměti  
 I když můžete použít nástroj **využití paměti** ke generování podrobných sestav, které můžete použít k vyhledání a opravě problémů, můžete ho také použít k prozkoumání dopadů paměti v reálném čase scénáře, který aktivně vyvíjíte.  
  
 Když spustíte relaci diagnostiky, vaše aplikace se spustí a okno **diagnostické nástroje** zobrazí graf časové osy použití paměti vaší aplikace.  
  
 ![Stránka s přehledem využití paměti](../profiling/media/memuse-reportoverview.png "MEMUSE__ReportOverview")  
  
 Graf časové osy zobrazuje kolísání paměti vaší aplikace při jejich spuštění. Špičky v grafu obvykle označují, že některé kódy shromažďují nebo vytvářejí data a pak je po dokončení zpracování zahodí. Velké špičky označují oblasti, které je možné optimalizovat. Další obavy je nárůst spotřeby paměti, která se nevrátí, protože může indikovat neefektivní využití paměti nebo dokonce nevracení paměti.  
  
### <a name="BKMK_Close_a_monitoring_session"></a>Ukončení relace monitorování  
 ![Zastavit shromažďování](../profiling/media/memuse-stopcollection.png "MEMUSE__StopCollection")  
  
 Chcete-li zastavit relaci monitorování bez vytváření sestavy, stačí zavřít okno diagnostiky. Pokud chcete vygenerovat sestavu, když máte snímky paměti, klikněte na **zastavit**.  
  
## <a name="BKMK_Take_snapshots_to_analyze_the_memory_state_of_your_app"></a>Pořizovat snímky stavu paměti vaší aplikace  
 Pokud zjistíte problém s pamětí, který chcete prozkoumat, můžete během diagnostické relace pořizovat snímky a zachytit objekty v paměti v konkrétním momentě. Vzhledem k tomu, že aplikace používá velký počet různých typů objektů, možná budete chtít soustředit analýzu na jeden scénář. Je také vhodné získat snímek základní hodnoty aplikace před zobrazením problému s pamětí, dalšího snímku po prvním výskytu problému a jedním nebo více snímky, pokud můžete scénář opakovat.  
  
 Chcete-li shromáždit snímky, spusťte novou relaci diagnostiky. Pokud chcete zachytit data paměti, vyberte možnost **pořídit snímek** . Chcete-li vygenerovat sestavu, klikněte na tlačítko **zastavit**.  
  
## <a name="BKMK_Memory_Usage_overview_page"></a>Stránka s přehledem využití paměti  
 Po zastavení shromažďování dat nástroj využití paměti zastaví aplikaci a zobrazí sestavu přehledu.  
  
 ![Stránka s přehledem využití paměti](../profiling/media/memuse-reportoverview.png "MEMUSE__ReportOverview")  
  
### <a name="BKMK_Memory_Usage_snapshot_views"></a>Zobrazení snímků využití paměti  
 Zobrazení snímků slouží k otevření podrobných sestav v nových oknech aplikace Visual Studio. Existují dva druhy zobrazení snímků:  
  
- [Sestavy podrobností snímku](../profiling/memory-usage-without-debugging2.md#BKMK_Snapshot_details_reports) zobrazují typy a instance v jednom snímku.  
  
- [Sestavy rozdílů snímků (diff)](../profiling/memory-usage-without-debugging2.md#BKMK_Snapshot_difference__diff__reports) porovnávají typy a instance ve dvou snímcích.  
  
  ![Odkazy na zobrazení snímků](../profiling/media/memuse-snapshotview-numbered.png "MEMUSE__SnapshotView_Numbered")  
  
  Číslované položky na obrázku zobrazení snímku jsou odkazy, které zobrazují zobrazení sestavy využití paměti.  
  
|||  
|-|-|  
|![Krok 1](../profiling/media/procguid-1.png "ProcGuid_1")|Text odkazu zobrazuje celkový počet bajtů v paměti při pořízení snímku.<br /><br /> Kliknutím na tento odkaz zobrazíte sestavu s podrobnostmi o snímku, která je seřazená podle celkové velikosti instancí typu.|  
|![Krok 2](../profiling/media/procguid-2.png "ProcGuid_2")|Text odkazu zobrazuje celkový počet objektů v paměti při pořízení snímku.<br /><br /> Kliknutím na tento odkaz zobrazíte sestavu s podrobnostmi o snímku, která je seřazená podle počtu instancí typů.|  
|![Krok 3](../profiling/media/procguid-3.png "ProcGuid_3")|Text odkazu zobrazuje rozdíl mezi celkovou velikostí objektů v paměti v okamžiku tohoto snímku a celkovou velikostí předchozího snímku.<br /><br /> Text odkazu je kladné číslo, pokud je velikost paměti tohoto snímku větší než předchozí a záporná hodnota, pokud je velikost menší. **Základní** text odkazu označuje, že tento snímek je v relaci diagnostiky první. **Žádný rozdíl** neindikuje, že rozdíl je nulový.<br /><br /> Kliknutím na tento odkaz zobrazíte sestavu rozdílů snímků, která je seřazená podle rozdílů v celkové velikosti instancí typů.|  
|![Krok 4](../profiling/media/procguid-4.png "ProcGuid_4")|Text odkazu zobrazuje rozdíl mezi celkovým počtem paměťových objektů v tomto snímku a počtem objektů v předchozím snímku.<br /><br /> Kliknutím na tento odkaz zobrazíte sestavu rozdílů snímků, která je seřazená podle rozdílů v celkovém počtu instancí typů.|  
  
## <a name="BKMK_Snapshot_reports"></a>Sestavy snímků  
 ![Sestava snímku využití paměti](../profiling/media/memuse-snapshotreport-all.png "MEMUSE_SnapshotReport_All")  
  
### <a name="BKMK_Snapshot_report_trees"></a>Stromy sestav snímků  
  
#### <a name="BKMK_Managed_Heap"></a>Spravovaná halda  
 Ve stromové struktuře haldy spravovaného stromu haldy [(podrobnosti snímku)](../profiling/memory-usage-without-debugging2.md#BKMK_Managed_Heap_tree__Snapshot_details_) a [spravovaného stromu haldy (rozdíl snímku)](../profiling/memory-usage-without-debugging2.md#BKMK_Managed_Heap_tree__Snapshot_diff_) se zobrazí typy a instance v sestavě. Výběr typu nebo instance zobrazí **cesty k kořenu** a stromům **odkazovaných objektů** pro vybranou položku.  
  
#### <a name="BKMK_Paths_to_Root"></a>Cesty ke kořenu  
 [Cesty ke kořenovému stromu (podrobnosti snímku)](../profiling/memory-usage-without-debugging2.md#BKMK_Paths_to_Root_tree__Snapshot_details_) a [cesty ke kořenovému stromu (rozdíl snímku)](../profiling/memory-usage-without-debugging2.md#BKMK_Paths_to_Root_tree__Snapshot_diff_) znázorňují řetězec objektů, které odkazují na typ nebo instanci. Systém uvolňování paměti .NET Framework vyčistí paměť pro objekt pouze v případě, že byly vydány všechny odkazy na ni.  
  
#### <a name="BKMK_Referenced_Objects"></a>Odkazované objekty  
 [Strom odkazovaných objektů (podrobnosti snímku)](../profiling/memory-usage-without-debugging2.md#BKMK_Referenced_Objects_tree__Snapshot_details_) a [strom odkazovaných objektů (rozdíl snímku)](../profiling/memory-usage-without-debugging2.md#BKMK_Referenced_Objects_tree__Snapshot_diff_) zobrazuje objekty, na které se vybraný typ nebo odkazy na instance odkazuje.  
  
### <a name="BKMK_Object_Type_and_Instance_fields"></a>Pole typ objektu a instance  
 Pokud položka **typu objektu** obsahuje podřízené položky, můžete je zobrazit kliknutím na ikonu šipky. Pokud je barva textu **typu objektu** modrá, můžete zvolit, zda chcete přejít k objektu v souboru zdrojového kódu. Zdrojový soubor se otevře v samostatném okně.  
  
 Názvy instancí jsou jedinečné identifikátory, které jsou generovány nástrojem využití paměti.  
  
 Pokud si všimnete typu, že nemůžete snadno identifikovat, nebo Pokud nevíte, jak je součástí kódu, je pravděpodobné, že se jedná o objekt z .NET Framework, operačního systému nebo kompilátoru, který nástroj využití paměti zobrazuje, protože se účastní řetězů vlastnictví. vaše objekty.  
  
### <a name="BKMK_Report_tree_filters_"></a>Filtry stromu sestav  
 Většina aplikací obsahuje překvapivě velký počet typů, přičemž většina z nich není pro vývojáře aplikací velmi zajímavá. Nástroj **využití paměti** definuje dva filtry, které můžete použít ke skrytí většiny těchto typů ve **spravované haldě** a **cestách ke kořenovým** stromům. Strom můžete také filtrovat podle názvu typu.  
  
 ![Možnosti řazení a filtrování](../profiling/media/memuse-sortandfilter.png "MEMUSE_SortAndFilter")  
  
#### <a name="BKMK_Filter"></a>Filtrovací  
 Zadejte řetězec do pole **filtru** , chcete-li omezit zobrazení stromu na typy, které obsahují zadaný text. Ve filtru se nerozlišují velká a malá písmena a rozpoznává zadaný řetězec v jakékoli části názvů typů.  
  
#### <a name="BKMK_Collapse_Small_Objects"></a>Sbalit malé objekty  
 Při použití tohoto filtru jsou typy, jejichž **Velikost (bajty)** je menší než 0,5 procent celkové velikosti paměti snímku, skryté v seznamu **spravované haldy** .  
  
#### <a name="BKMK_Just_My_Code"></a>Pouze můj kód  
 Filtr **pouze můj kód** skrývá většinu instancí generovaných externím kódem. Externí typy jsou vlastněny operačním systémem nebo komponentami rozhraní nebo jsou generovány kompilátorem.  
  
## <a name="BKMK_Snapshot_details_reports"></a>Sestavy podrobností snímku  
 Pomocí sestavy Podrobnosti o snímku se můžete soustředit na jeden snímek z relace diagnostiky. Chcete-li otevřít sestavu podrobností, vyberte jeden z odkazů v zobrazení snímku, jak je znázorněno na následujícím obrázku. Oba odkazy otevřou stejnou sestavu; Jediným rozdílem je počáteční pořadí řazení **spravovaného stromu haldy** v sestavě. V obou případech můžete změnit pořadí řazení po otevření sestavy.  
  
 ![Odkazy na sestavu snímku v zobrazení snímku](../profiling/media/memuse-snapshotview-snapshotdetailslinks.png "MEMUSE_SnapshotView_SnapshotDetailsLinks")  
  
- Propojení **MB** seřadí sestavu podle sloupce **Celková velikost (bajty)** .  
  
- Odkaz **objekty** seřadí sestavu podle sloupce **Count (počet** ).  
  
### <a name="BKMK_Managed_Heap_tree__Snapshot_details_"></a>Spravovaný strom haldy (podrobnosti snímku)  
 Strom **spravované haldy** obsahuje seznam typů objektů, které jsou uloženy v paměti. Můžete rozšířit název typu a zobrazit deset největších instancí typu seřazený podle velikosti. Výběr typu nebo instance zobrazí **cesty k kořenu** a stromům **odkazovaných objektů** pro vybranou položku.  
  
 ![Spravovaný strom haldy](../profiling/media/memuse-snapshotdetails-managedheaptree.png "MEMUSE__SnapshotDetails_ManagedHeapTree")  
  
|||  
|-|-|  
|**Typ objektu**|Název typu nebo instance objektu.|  
|**Výpočtu**|Počet instancí objektu typu. Číslo je vždy 1 pro instanci.|  
|**Velikost (v bajtech)**|Pro typ je velikost všech instancí typu ve snímku paměti bez velikosti objektů obsažených v instancích.<br /><br /> V případě instance zadejte velikost objektu s výjimkou velikosti objektů obsažených v instanci. instance.|  
|**Celková velikost (bajty)**|Velikost instancí typu nebo velikost jedné instance, včetně velikosti obsažených objektů.|  
  
### <a name="BKMK_Paths_to_Root_tree__Snapshot_details_"></a>Cesty ke kořenovému stromu (podrobnosti snímku)  
 **Cesta ke kořenovému stromu** zobrazuje řetězec objektů, které odkazují na typ nebo instanci. Systém uvolňování paměti .NET Framework vyčistí paměť pro objekt pouze v případě, že byly vydány všechny odkazy na ni.  
  
 ![Cesty ke kořenovému stromu pro typy](../profiling/media/memuse-snapshotdetails-type-pathstoroottree.png "MEMUSE_SnapshotDetails_Type_PathsToRootTree")  
  
 Pokud zobrazíte typ ve stromové struktuře **cesty ke kořenu** , zobrazí se ve sloupci **počet odkazů** počet objektů typů, které obsahují odkazy na tento typ. Sloupec se nezobrazí při analýze instance.  
  
### <a name="BKMK_Referenced_Objects_tree__Snapshot_details_"></a>Strom odkazovaných objektů (podrobnosti snímku)  
 Strom **odkazovaných objektů** zobrazuje objekty, na které se vybraný typ nebo odkazy na instance odkazuje.  
  
 ![Odkazovaný Objjects strom pro instance](../profiling/media/memuse-snapshotdetails-referencedobjects-instance.png "MEMUSE_SnapshotDetails_ReferencedObjects_Instance")  
  
|||  
|-|-|  
|**Typ nebo instance objektu**|Název typu nebo instance objektu.|  
|**Velikost (v bajtech)**|Pro typ je velikost všech instancí typu bez velikosti objektů obsažených v typu.<br /><br /> V případě instance velikost objektu s výjimkou velikosti objektů obsažených v objektu.|  
|**Celková velikost (bajty)**|Celková velikost instancí typu nebo velikost instance, včetně velikosti obsažených objektů.|  
  
## <a name="BKMK_Snapshot_difference__diff__reports"></a>Sestavy rozdílů snímků (diff)  
 Sestava rozdílového snímku (rozdíl) zobrazuje změny mezi primárním snímkem a snímkem, který byl proveden těsně před ním. Chcete-li otevřít sestavu rozdílů, vyberte jednu z odkazů v zobrazení snímku, jak je znázorněno na následujícím obrázku. Oba odkazy otevřou stejnou sestavu; Jediným rozdílem je počáteční pořadí řazení **spravovaného stromu haldy** v sestavě. Po otevření sestavy můžete změnit pořadí řazení.  
  
 ![Odkazy na sestavu rozdílů v zobrazení snímků](../profiling/media/memuse-snapshotview-snapshotdifflinks.png "MEMUSE_SnapshotView_SnapshotDiffLinks")  
  
- Propojení **MB** seřadí sestavu podle sloupce **Celková velikost (bajty)** .  
  
- Odkaz **objekty** seřadí sestavu podle sloupce **Count (počet** ).  
  
### <a name="BKMK_Managed_Heap_tree__Snapshot_diff_"></a>Spravovaný strom haldy (rozdíl snímku)  
 Strom **spravované haldy** obsahuje seznam typů objektů, které jsou uloženy v paměti. Můžete rozšířit název typu a zobrazit deset největších instancí typu seřazený podle velikosti. Výběr typu nebo instance zobrazí **cesty k kořenu** a stromům **odkazovaných objektů** pro vybranou položku.  
  
 ![Spravovaný strom haldy pro typ v sestavě rozdíl](../profiling/media/memuse-snapshotdiff-type-heap.png "MEMUSE_SnapshotDiff_Type_Heap")  
  
 Všimněte si, že sloupce **počet**, **Velikost (bajty)** a **Celková velikost (bajty)** byly na obrázku sbaleny.  
  
|||  
|-|-|  
|**Typ objektu**|Název typu nebo instance objektu.|  
|**Výpočtu**|Počet instancí typu v primárním snímku. **Počet** je vždy 1 pro instanci.|  
|**Rozdíl v počtu**|V případě typu se jedná o rozdíl v počtu instancí typu mezi primárním snímkem a předchozím snímkem. Pole je pro instanci prázdné.|  
|**Velikost (v bajtech)**|Velikost objektů v primárním snímku s výjimkou velikosti objektů obsažených v objektech. Pro typ, **Velikost (bajty)** a **celkovou velikost (bajty)** jsou součty velikostí instancí typu.|  
|**Rozdíl celkové velikosti (bajty)**|V případě typu se jedná o rozdíl v celkové velikosti instancí typu mezi primárním snímkem a předchozím snímkem, s výjimkou velikosti objektů obsažených v instancích. Pole je pro instanci prázdné.|  
|**Celková velikost (bajty)**|Velikost objektů v primárním snímku, včetně velikosti objektů obsažených v objektech.|  
|**Rozdíl celkové velikosti (bajty)**|V případě typu se jedná o rozdíl mezi velikostí všech instancí typu mezi primárním snímkem a předchozím snímkem, včetně velikosti objektů obsažených v objektech. Pole je pro instanci prázdné.|  
  
### <a name="BKMK_Paths_to_Root_tree__Snapshot_diff_"></a>Cesty ke kořenovému stromu (rozdíl snímku)  
 **Cesta ke kořenovému stromu** zobrazuje řetězec objektů, které odkazují na typ nebo instanci. Systém uvolňování paměti .NET Framework vyčistí paměť pro objekt pouze v případě, že byly vydány všechny odkazy na ni.  
  
 ![Cesty ke kořenovému stromu pro instance v zobrazení rozdílů](../profiling/media/memuse-snapshotdiff-pathstoroot-instance-all.png "MEMUSE_SnapshotDiff_PathsToRoot_Instance_All")  
  
### <a name="BKMK_Referenced_Objects_tree__Snapshot_diff_"></a>Strom odkazovaných objektů (rozdíl snímku)  
 Strom **odkazovaných objektů** zobrazuje objekty, na které odkazuje primární typ nebo instance.  
  
 ![Odkazovaný Objjects strom pro instance](../profiling/media/memuse-snapshotdetails-referencedobjects-instance.png "MEMUSE_SnapshotDetails_ReferencedObjects_Instance")  
  
|||  
|-|-|  
|**Typ nebo instance objektu**|Název typu nebo instance objektu.|  
|**Velikost (v bajtech)**|V případě instance je velikost objektu v primárním snímku bez velikosti objektů obsažených v instanci.<br /><br /> Pro typ je celková velikost instancí typu v primárním snímku bez velikosti objektů obsažených v instanci.|  
|**Celková velikost (bajty)**|Velikost objektů v primárním snímku, včetně velikosti objektů obsažených v objektech.|  
  
## <a name="see-also"></a>Viz také  
   [paměti JavaScriptu](../profiling/javascript-memory.md)  
 [Analýza  výkonu aplikace](https://msdn.microsoft.com/library/58acb30b-8428-41a6-b195-b0fdedb89575)  
 [Spustit nástroje pro sledování výkonu a diagnostiky](https://msdn.microsoft.com/library/788279d8-f56b-40a0-9bef-facc3dfba471)   
 [Osvědčené postupy výkonu pro aplikace pro Windows C++Store C#, které používají, a Visual Basic](https://msdn.microsoft.com/library/windows/apps/hh750313.aspx)   
 [Diagnostikování problémů s pamětí pomocí nového nástroje využití paměti v aplikaci Visual Studio](https://blogs.msdn.com/b/visualstudioalm/archive/2014/04/02/diagnosing-memory-issues-with-the-new-memory-usage-tool-in-visual-studio.aspx)
