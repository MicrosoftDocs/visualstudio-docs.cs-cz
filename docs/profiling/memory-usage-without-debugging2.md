---
title: Analyzovat využití paměti bez ladění | Microsoft Docs
ms.custom: ''
ms.date: 04/02/2020
ms.topic: how-to
dev_langs:
- CSharp
- VB
- FSharp
- C++
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 62ac71a3aa707958bd0c7f107185d141e339b2b7
ms.sourcegitcommit: 57d96de120e0574e506dfd80bb7adfbac73f96be
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/24/2020
ms.locfileid: "85332145"
---
# <a name="analyze-memory-usage-without-the-debugger"></a>Analýza využití paměti bez ladicího programu

Nástroj **využití paměti** monitoruje využití paměti vaší aplikace. Pomocí tohoto nástroje můžete zkoumat účinky v paměti v reálném čase scénářů, které aktivně vyvíjíte v aplikaci Visual Studio. Můžete pořizovat podrobné snímky stavů paměti aplikace a porovnat snímky a najít hlavní příčiny problémů s pamětí.

Nástroj **využití paměti** lze spustit [s ladicím programem nebo bez něj](../profiling/running-profiling-tools-with-or-without-the-debugger.md). V tomto článku ukážeme, jak používat nástroj **využití paměti** bez ladicího programu v **profileru výkonu**sady Visual Studio.

## <a name="memory-usage-diagnostic-sessions"></a>Relace diagnostiky využití paměti

**Spuštění relace diagnostiky využití paměti:**

1. Otevřete projekt v aplikaci Visual Studio.

   Nástroj využití paměti podporuje aplikace .NET, ASP.NET, nativní nebo smíšený režim (.NET a nativní).

1. V nabídce ladění nastavte možnost konfigurace řešení na **release** a jako cíl nasazení vyberte **místní ladicí program systému Windows** (nebo **místní počítač**).

1. Na panelu nabídek vyberte **ladit**  >  **výkon Profiler**.

1. V části **dostupné nástroje**vyberte **využití paměti**a pak vyberte **Spustit**.

   ![Spustit relaci diagnostiky využití paměti](../profiling/media/memuse_start_diagnosticssession.png "Spustit relaci diagnostiky využití paměti")

### <a name="monitor-memory-use"></a>Monitorovat využití paměti

Když spustíte relaci diagnostiky, vaše aplikace se spustí a okno **diagnostické nástroje** zobrazí graf časové osy použití paměti vaší aplikace.

![Stránka s přehledem využití paměti](../profiling/media/memuse__reportoverview.png "MEMUSE__ReportOverview")

Graf časové osy zobrazuje kolísání paměti při spuštění aplikace. Špičky v grafu obvykle označují, že některé kódy shromažďují nebo vytvářejí data a pak je po dokončení zpracování zahodí. Velké špičky označují oblasti, které je možné optimalizovat. Další obavou je nárůst využití paměti, které se nevrátí, protože může znamenat neefektivní využití paměti nebo dokonce nevracení paměti.

### <a name="take-snapshots-of-app-memory-states"></a>Pořídit snímky paměti aplikací

Aplikace používá velký počet objektů a možná budete chtít soustředit analýzy na jeden scénář. Nebo můžete najít problémy paměti k prozkoumání. Během diagnostické relace můžete pořizovat snímky a zachytit tak využití paměti v konkrétním momentě. Je vhodné získat snímek základní hodnoty aplikace před zobrazením problému s pamětí, dalšího snímku po prvním výskytu problému a další snímky, pokud můžete scénář opakovat.

Chcete-li shromáždit snímky, vyberte možnost **pořídit snímek** , pokud chcete zachytit data paměti.

### <a name="close-the-diagnostic-session"></a><a name="BKMK_Close_a_monitoring_session"></a>Zavřít diagnostickou relaci

Chcete-li zastavit relaci monitorování bez vytváření sestavy, stačí zavřít okno diagnostiky. Pokud chcete vygenerovat sestavu po dokončení shromažďování nebo pořízení snímků, vyberte **Zastavit shromažďování**.

![Zastavit shromažďování](../profiling/media/memuse__stopcollection.png "Zastavit shromažďování")

## <a name="memory-usage-reports"></a>Sestavy využití paměti

Po zastavení shromažďování dat nástroj **využití paměti** zastaví aplikaci a zobrazí stránku s přehledem **využití paměti** .

![Stránka s přehledem využití paměti](../profiling/media/memuse__reportoverview1.png "Stránka s přehledem využití paměti")

### <a name="memory-usage-snapshots"></a><a name="BKMK_Memory_Usage_snapshot_views"></a>Snímky využití paměti

Čísla v podoknech **snímků** zobrazují bajty a objekty v paměti při každém pořízení snímku a rozdíl mezi snímkem a předchozím snímkem.

Čísla jsou odkazy, které otevřou podrobné zobrazení sestavy **využití paměti** v nových oknech aplikace Visual Studio. [Sestava podrobností snímku](#snapshot-details-reports) zobrazuje typy a instance v jednom snímku. [Sestava rozdílového snímku (diff)](#snapshot-difference-diff-reports) porovnává typy a instance ve dvou snímcích.

  ![Odkazy na zobrazení snímků](../profiling/media/memuse__snapshotview_numbered.png "Odkazy na zobrazení snímků")

|||
|-|-|
|![Krok 1](../profiling/media/procguid_1.png "ProcGuid_1")|Celkový počet bajtů v paměti při pořízení snímku.<br /><br /> Kliknutím na tento odkaz zobrazíte sestavu s podrobnostmi o snímku, která je seřazená podle celkové velikosti instancí typu.|
|![Krok 2](../profiling/media/procguid_2.png "ProcGuid_2")|Celkový počet objektů v paměti, kdy byl snímek proveden.<br /><br /> Kliknutím na tento odkaz zobrazíte sestavu podrobností snímku seřazenou podle počtu instancí typů.|
|![Krok 3](../profiling/media/procguid_3.png "ProcGuid_3")|Rozdíl mezi celkovou velikostí paměťových objektů v tomto snímku a předchozím snímkem. <br /><br /> Kladné číslo znamená, že velikost paměti tohoto snímku je větší než předchozí a záporná hodnota znamená, že velikost je menší. **Směrný plán** znamená, že snímek je v relaci diagnostiky první. **Žádný rozdíl** znamená, že rozdíl je nulový.<br /><br /> Kliknutím na tento odkaz zobrazíte sestavu rozdílů snímků seřazenou podle rozdílů v celkové velikosti instancí typů.|
|![Krok 4](../profiling/media/procguid_4.png "ProcGuid_4")|Rozdíl mezi celkovým počtem paměťových objektů v tomto snímku a předchozím snímkem.<br /><br /> Kliknutím na tento odkaz zobrazíte sestavu rozdílů snímků seřazenou podle rozdílů v celkovém počtu instancí typů.|

## <a name="memory-usage-snapshot-reports"></a>Sestavy snímku využití paměti

<a name="BKMK_Snapshot_report_trees"></a>Když vyberete jeden z odkazů na snímky na stránce Přehled **využití paměti** , otevře se sestava snímku na nové stránce.

![Sestava snímku využití paměti](../profiling/media/memuse_snapshotreport_all.png "Sestava snímku využití paměti")

V sestavě snímku můžete rozbalit položky **typu objektu** pro zobrazení podřízených položek. Názvy instancí jsou jedinečné identifikátory, které jsou generovány nástrojem využití paměti.

Pokud je **typ objektu** modrý, můžete jej vybrat pro přechod na objekt ve zdrojovém kódu v samostatném okně.

Typy, které nemůžete identifikovat nebo jejichž zapojení do kódu nerozumíte, jsou pravděpodobně .NET, operační systém nebo objekty kompilátoru. Nástroj **využití paměti** zobrazí tyto objekty, pokud se účastní v řetězcích vlastnictví vašich objektů.

V sestavě snímku:

- Strom **spravované haldy** zobrazuje typy a instance v sestavě. Výběr typu nebo instance zobrazí **cesty k kořenu** a stromům **odkazovaných objektů** pro vybranou položku.

- **Cesta ke kořenovému** stromu zobrazuje řetězec objektů, které odkazují na typ nebo instanci. Systém uvolňování paměti .NET vyčistí paměť pro objekt pouze v případě, že byly vydány všechny odkazy na ni.

- **Odkazované typy** nebo **odkazované objekty** zobrazují objekty, na které je vybraný typ nebo odkazy na instance.

### <a name="report-tree-filters"></a><a name="BKMK_Report_tree_filters_"></a>Filtry stromu sestav

Mnoho typů v aplikacích není velice zajímavé pro vývojáře aplikací. Filtry sestavy snímku mohou skrýt většinu těchto typů ve **spravované haldě** a **cestách ke kořenovým** stromům.

![Možnosti řazení a filtrování](../profiling/media/memuse_sortandfilter.png "MEMUSE_SortAndFilter")

- <a name="BKMK_Filter"></a>Chcete-li filtrovat strom podle názvu typu, zadejte název do pole **filtru** . Filtr nerozlišuje velká a malá písmena a rozpoznává zadaný řetězec v jakékoli části názvu typu.

- <a name="BKMK_Collapse_Small_Objects"></a>Vyberte možnost **sbalení malých objektů** v rozevíracím seznamu **filtru** pro skrytí typů, jejichž **Velikost (bajty)** je menší než 0,5 procent celkové paměti.

- <a name="BKMK_Just_My_Code"></a>Výběrem **pouze můj kód** v rozevírací nabídce **Filtr** skryjte většinu instancí generovaných externím kódem. Externí typy patří k operačním systémům nebo komponentám rozhraní nebo jsou generovány kompilátorem.

## <a name="snapshot-details-reports"></a>Sestavy podrobností snímku

 Sestava podrobností snímku popisuje jeden snímek z relace diagnostiky. Pokud chcete sestavu otevřít, vyberte v podokně snímku odkaz velikost nebo objekty.

 ![Odkazy na sestavu snímku v podokně snímku](../profiling/media/memuse_snapshotview_snapshotdetailslinks.png "Odkazy na sestavu snímku v podokně snímku")

Oba odkazy otevřou stejnou sestavu. Jediným rozdílem je počáteční pořadí řazení stromu **spravované haldy** . Odkaz na velikost seřadí sestavu podle sloupce **Celková velikost (bajty)** . Odkaz objekty seřadí sestavu podle sloupce **Count (počet** ). Po otevření sestavy můžete změnit sloupec řazení nebo pořadí.

### <a name="managed-heap-tree-snapshot-details-reports"></a><a name="BKMK_Managed_Heap_tree__Snapshot_details_"></a>Spravovaný strom haldy (sestavy podrobností snímku)
 Strom **spravované haldy** obsahuje seznam typů objektů, které jsou uloženy v paměti. Rozbalením názvu typu zobrazíte deset největších instancí typu seřazené podle velikosti. Vyberte typ nebo instanci pro zobrazení **cest k kořenům** a stromům **odkazovaných objektů** pro vybranou položku.

 ![Spravovaný strom haldy](../profiling/media/memuse__snapshotdetails_managedheaptree.png "Spravovaný strom haldy")

Strom **spravované haldy** v sestavě podrobností snímku má následující sloupce:

|||
|-|-|
|**Typ objektu**|Název typu nebo instance objektu.|
|**Výpočtu**|Počet instancí objektu typu. **Počet** je vždy 1 pro instanci.|
|**Velikost (v bajtech)**|Pro typ je velikost všech instancí typu ve snímku menší než velikost objektů obsažených v instancích.<br /><br /> V případě instance je velikost objektu menší než velikost objektů obsažených v instanci. |
|**Celková velikost (bajty)**|Velikost instancí typu, nebo velikost jedné instance, včetně velikosti obsažených objektů.|
|**Modul**|Modul, který obsahuje objekt.|

### <a name="paths-to-root-tree-snapshot-details-reports"></a><a name="BKMK_Paths_to_Root_tree__Snapshot_details_"></a>Cesty ke kořenovému stromu (sestavy podrobností snímku)
**Cesta ke kořenovému stromu** zobrazuje řetězec objektů, které odkazují na typ nebo instanci. Systém uvolňování paměti .NET vyčistí paměť pro objekt pouze v případě, že byly vydány všechny odkazy na ni.

Pro typ v **cestě ke stromu kořene** se počet objektů, které obsahují odkazy na tento typ, zobrazí ve sloupci **počet odkazů** .

![Cesty ke kořenovému stromu pro typy](../profiling/media/memuse_snapshotdetails_type_pathstoroottree.png "Cesty ke kořenovému stromu pro typy")

### <a name="referenced-types-or-referenced-objects-tree-snapshot-details-reports"></a><a name="BKMK_Referenced_Objects_tree__Snapshot_details_"></a>Odkazované typy nebo odkazované objekty stromu (sestavy podrobností snímku)
**Odkazované typy** nebo **odkazované objekty** zobrazují objekty, na které je vybraný typ nebo odkazy na instance.

![Strom odkazovaných objektů pro instance](../profiling/media/memuse_snapshotdetails_referencedobjects_instance.png "Strom odkazovaných objektů pro instance")

**Odkazovaný strom typů** v sestavě podrobností snímku má následující sloupce. Strom **odkazovaných objektů** nemá sloupec **Count reference** .

|||
|-|-|
|**Typ** nebo **instance** objektu|Název typu nebo instance.|
|**Počet odkazů**|Pro typy počet instancí objektů typu.|
|**Velikost (v bajtech)**|Pro typ je velikost všech instancí typu menší než velikost objektů obsažených v typu.<br /><br /> V případě instance je velikost objektu menší než velikost objektů obsažených v objektu.|
|**Celková velikost (bajty)**|Celková velikost instancí typu, nebo velikost instance, včetně velikosti obsažených objektů.|
|**Modul**|Modul, který obsahuje objekt.|

## <a name="snapshot-difference-diff-reports"></a>Sestavy rozdílů snímků (diff)

Sestava rozdílového snímku (rozdíl) zobrazuje změny mezi primárním snímkem a předchozím snímkem. Chcete-li otevřít sestavu rozdílů, vyberte jeden z odkazů na rozdíl v podokně snímku.

Oba odkazy otevřou stejnou sestavu. Jediným rozdílem je počáteční pořadí řazení **spravovaného stromu haldy** v sestavě. Odkaz na velikost seřadí sestavu podle sloupce **rozdíl celkové velikosti (bajty)** . Odkaz objekty seřadí sestavu podle sloupce **počet rozdílů** . Po otevření sestavy můžete změnit sloupec řazení nebo pořadí.

 ![Odkazy na sestavu rozdílů v podokně snímků](../profiling/media/memuse_snapshotview_snapshotdifflinks.png "Odkazy na sestavu rozdílů v podokně snímků")

### <a name="managed-heap-tree-snapshot-diff-reports"></a><a name="BKMK_Managed_Heap_tree__Snapshot_diff_"></a>Spravovaný strom haldy (sestavy rozdílů snímků)

 Strom **spravované haldy** obsahuje seznam typů objektů, které jsou uloženy v paměti. Můžete rozšířit název typu a zobrazit deset největších instancí typu seřazený podle velikosti. Vyberte typ nebo instanci pro zobrazení **cest k kořenům** a stromům **odkazovaných objektů** pro vybranou položku.

 ![Spravovaný strom haldy pro typ v sestavě rozdíl](../profiling/media/memuse_snapshotdiff_type_heap.png "Spravovaný strom haldy pro typ v sestavě rozdíl")

Strom **spravované haldy** v sestavě rozdílového snímku má následující sloupce:

|||
|-|-|
|**Typ objektu**|Název typu nebo instance objektu.|
|**Výpočtu**|Počet instancí typu v primárním snímku. **Počet** je vždy 1 pro instanci.|
|**Rozdíl v počtu**|V případě typu se jedná o rozdíl v počtu instancí typu mezi primárním snímkem a předchozím snímkem. Pole je pro instanci prázdné.|
|**Velikost (v bajtech)**|Velikost objektů v primárním snímku a menší velikost objektů v objektech. Pro typ, **Velikost (bajty)** a **celkovou velikost (bajty)** jsou součty velikostí instancí typu.|
|**Rozdíl celkové velikosti (bajty)**|V případě typu je rozdíl v celkové velikosti instancí typu mezi primárním snímkem a předchozím snímkem menší než velikost objektů v instancích. Pole je pro instanci prázdné.|
|**Celková velikost (bajty)**|Velikost objektů v primárním snímku, včetně velikosti objektů v objektech.|
|**Rozdíl celkové velikosti (bajty)**|V případě typu se jedná o rozdíl mezi velikostí všech instancí typu mezi primárním snímkem a předchozím snímkem, včetně velikosti objektů v objektech. Pole je pro instanci prázdné.|
|**Modul**|Modul, který obsahuje objekt.|

### <a name="paths-to-root-tree-snapshot-diff-reports"></a><a name="BKMK_Paths_to_Root_tree__Snapshot_diff_"></a>Cesty ke kořenovému stromu (sestavy rozdílů snímků)

**Cesta ke kořenovému stromu** zobrazuje řetězec objektů, které odkazují na typ nebo instanci. Systém uvolňování paměti .NET vyčistí paměť pro objekt pouze v případě, že byly vydány všechny odkazy na ni.

Pro typ v **cestě ke stromu kořene** se počet objektů, které obsahují odkazy na tento typ, zobrazí ve sloupci **počet odkazů** . Rozdíl v počtu z předchozího snímku je ve sloupci **rozdíl odkazu** .

 ![Cesty ke kořenovému stromu v sestavě rozdílů](../profiling/media/memuse_snapshotdiff_pathstoroot_instance_all.png "Cesty ke kořenovému stromu v sestavě rozdílů")

### <a name="referenced-types-or-referenced-objects-tree-snapshot-diff-reports"></a><a name="BKMK_Referenced_Objects_tree__Snapshot_diff_"></a>Odkazované typy nebo odkazované objekty stromu (sestavy rozdílů snímků)

**Odkazované typy** nebo **odkazované objekty** zobrazují objekty, na které je vybraný typ nebo odkazy na instance.

![Odkazované typy v sestavě rozdílů](../profiling/media/memuse_snapshotdiff_referencedtypes.png "Odkazované typy v sestavě rozdílů")

**Odkazovaný strom typů** ve zprávě rozdílového snímku má následující sloupce. Strom **odkazovaných objektů** má pro sebe **instance**, **Velikost (bajty)**, **celkovou velikost (bajty) a počet**sloupců **modulu** .

|||
|-|-|
|**Typ** nebo **instance** objektu|Název typu nebo instance objektu.|
|**Počet odkazů**|Počet instancí typu v primárním snímku.|
|**Rozdíl počtu odkazů**|V případě typu se jedná o rozdíl v počtu instancí typu mezi primárním snímkem a předchozím snímkem.|
|**Velikost (v bajtech)**|Velikost objektů v primárním snímku a menší velikost objektů v objektech. Pro typ, **Velikost (bajty)** a **celkovou velikost (bajty)** jsou součty velikostí instancí typu.|
|**Rozdíl celkové velikosti (bajty)**|V případě typu je rozdíl v celkové velikosti instancí typu mezi primárním snímkem a předchozím snímkem menší než velikost objektů v instancích. |
|**Celková velikost (bajty)**|Velikost objektů v primárním snímku, včetně velikosti objektů v objektech.|
|**Rozdíl celkové velikosti (bajty)**|V případě typu se jedná o rozdíl mezi velikostí všech instancí typu mezi primárním snímkem a předchozím snímkem, včetně velikosti objektů v objektech.|
|**Modul**|Modul, který obsahuje objekt.|

## <a name="see-also"></a>Viz také
- [Paměť JavaScriptu](../profiling/javascript-memory.md)
- [Profilace v sadě Visual Studio](../profiling/index.yml)
- [První seznámení s nástroji pro profilaci](../profiling/profiling-feature-tour.md)
- [Osvědčené postupy výkonu pro aplikace pro UWP pomocí C++, C# a Visual Basic](/previous-versions/windows/apps/hh750313\(v\=win.10\))
- [Diagnostikování problémů s pamětí pomocí nového nástroje využití paměti v aplikaci Visual Studio](https://devblogs.microsoft.com/devops/diagnosing-memory-issues-with-the-new-memory-usage-tool-in-visual-studio/)