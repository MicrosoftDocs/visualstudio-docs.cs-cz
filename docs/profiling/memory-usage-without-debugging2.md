---
title: Analýza využití paměti bez ladění | Dokumenty společnosti Microsoft
ms.custom: ''
ms.date: 04/02/2020
ms.topic: conceptual
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
ms.openlocfilehash: 5af369669245bca9c5de74566dd8594164acf8bb
ms.sourcegitcommit: 9c1cecaff4d9955276eee7865b78d47679dd1e2a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/03/2020
ms.locfileid: "80638826"
---
# <a name="analyze-memory-usage-without-the-debugger"></a>Analýza využití paměti bez ladicího programu

Nástroj **využití paměti** monitoruje využití paměti vaší aplikace. Pomocí tohoto nástroje můžete studovat efekty paměti v reálném čase scénářů, které aktivně vyvíjíte v sadě Visual Studio. Můžete pořizovat podrobné snímky stavů paměti aplikace a porovnávat snímky a najít hlavní příčiny problémů s pamětí.

Nástroj **Využití paměti** lze spustit s [ladicím programem nebo bez něj](../profiling/running-profiling-tools-with-or-without-the-debugger.md). V tomto článku ukážeme, jak používat nástroj **využití paměti** bez ladicího programu v profileru visual studio **performance profiler**.

## <a name="memory-usage-diagnostic-sessions"></a>Diagnostické relace využití paměti

**Spuštění diagnostické relace využití paměti:**

1. Otevřete projekt v sadě Visual Studio.

   Nástroj využití paměti podporuje aplikace .NET, ASP.NET, nativní nebo smíšený režim (.NET a nativní).

1. V nabídce Ladění nastavte konfiguraci řešení na **Release** a jako cíl nasazení vyberte **místní debugger systému Windows** (nebo místní **počítač).**

1. Na řádku nabídek zvolte **Ladění** > **profileru výkonu**.

1. V části **Dostupné nástroje**vyberte **Využití paměti**a pak vyberte **Start**.

   ![Spuštění diagnostické relace využití paměti](../profiling/media/memuse_start_diagnosticssession.png "Spuštění diagnostické relace využití paměti")

### <a name="monitor-memory-use"></a>Monitorování využití paměti

Když spustíte diagnostickou relaci, spustí se aplikace a v okně **Diagnostické nástroje** se zobrazí graf časové osy o využití paměti aplikace.

![Stránka přehledu využití paměti](../profiling/media/memuse__reportoverview.png "MEMUSE__ReportOverview")

Graf časové osy zobrazuje kolísání paměti při spuštění aplikace. Špičky v grafu obvykle označují, že některé kód je shromažďování nebo vytváření dat a potom zahodit po dokončení zpracování. Velké špičky označují oblasti, které je možné optimalizovat. Větší obavy je zvýšení spotřeby paměti, která není vrácena, protože může znamenat neefektivní využití paměti nebo dokonce nevracení paměti.

### <a name="take-snapshots-of-app-memory-states"></a>Pořizování snímků stavů paměti aplikace

Aplikace používá velký počet objektů a můžete chtít soustředit analýzu na jeden scénář. Nebo můžete najít problémy s pamětí prozkoumat. Můžete pořizovat snímky během diagnostické relace zachytit využití paměti v určitých okamžicích. Je vhodné získat snímek směrného plánu aplikace před problém s pamětí se zobrazí, další snímek po prvním výskytu problému a další snímky, pokud můžete opakovat scénář.

Chcete-li shromažďovat snímky, vyberte **pořizovat snímek,** pokud chcete zachytit data paměti.

### <a name="close-the-diagnostic-session"></a><a name="BKMK_Close_a_monitoring_session"></a>Ukončení diagnostické relace

Chcete-li zastavit relaci monitorování bez vytvoření sestavy, zavřete diagnostické okno. Pokud chcete generovat sestavu po dokončení shromažďování nebo pořízení snímků, vyberte **Zastavit shromažďování**.

![Zastavit sběr](../profiling/media/memuse__stopcollection.png "Zastavit sběr")

## <a name="memory-usage-reports"></a>Sestavy využití paměti

Po zastavení shromažďování dat nástroj **využití paměti** zastaví aplikaci a zobrazí stránku Přehled **využití paměti.**

![Stránka přehledu využití paměti](../profiling/media/memuse__reportoverview1.png "Stránka přehledu využití paměti")

### <a name="memory-usage-snapshots"></a><a name="BKMK_Memory_Usage_snapshot_views"></a>Snímky využití paměti

Čísla v podokně **snímek** zobrazit bajty a objekty v paměti při každém snímku byla pořízena a rozdíl mezi snímek a předchozí.

Čísla jsou odkazy, které otevírají podrobná zobrazení sestavy **Využití paměti** v nových oknech sady Visual Studio. [Sestava podrobností snímku](#snapshot-details-reports) zobrazuje typy a instance v jednom snímku. Sestava [rozdílu snímků (diff)](#snapshot-difference-diff-reports) porovnává typy a instance ve dvou snímcích.

  ![Odkazy ze zobrazení snímku](../profiling/media/memuse__snapshotview_numbered.png "Odkazy ze zobrazení snímku")

|||
|-|-|
|![Krok 1](../profiling/media/procguid_1.png "ProcGuid_1")|Celkový počet bajtů v paměti při pořízení snímku.<br /><br /> Vyberte tento odkaz, chcete-li zobrazit sestavu podrobností snímku seřazenou podle celkové velikosti instancí typu.|
|![Krok 2](../profiling/media/procguid_2.png "ProcGuid_2")|Celkový počet objektů v paměti při pořízení snímku.<br /><br /> Vyberte tento odkaz, chcete-li zobrazit sestavu podrobností snímku seřazenou podle počtu instancí typů.|
|![Krok 3](../profiling/media/procguid_3.png "ProcGuid_3")|Rozdíl mezi celkovou velikost objektů paměti v tomto snímku a předchozí snímek. <br /><br /> Kladné číslo znamená, že velikost paměti tohoto snímku je větší než předchozí a záporné číslo znamená, že velikost je menší. **Směrný plán** znamená, že snímek je první v diagnostické relaci. **Žádný rozdíl** znamená, že rozdíl je nula.<br /><br /> Vyberte tento odkaz, chcete-li zobrazit sestavu rozdílový snímek seřazenou podle rozdílu v celkové velikosti instancí typů.|
|![Krok 4](../profiling/media/procguid_4.png "ProcGuid_4")|Rozdíl mezi celkový počet objektů paměti v tomto snímku a předchozí snímek.<br /><br /> Vyberte tento odkaz, chcete-li zobrazit sestavu rozdílový snímek seřazenou podle rozdílu v celkovém počtu instancí typů.|

## <a name="memory-usage-snapshot-reports"></a>Sestavy snímků využití paměti

<a name="BKMK_Snapshot_report_trees"></a>Když vyberete jeden z odkazů snímku na stránce **Přehled využití paměti,** otevře se sestava snímku na nové stránce.

![Sestava snímku využití paměti](../profiling/media/memuse_snapshotreport_all.png "Sestava snímku využití paměti")

V sestavě snímku můžete rozbalit položky **typu objektu** a zobrazit podřízené položky. Názvy instancí jsou jedinečná ID, která jsou generována nástrojem využití paměti.

Pokud je **typ objektu** modrý, můžete jej vybrat a přejít na objekt ve zdrojovém kódu v samostatném okně.

Typy, které nelze identifikovat nebo jejichž zapojení do kódu nerozumíte jsou pravděpodobně .NET, operační systém nebo objekty kompilátoru. Nástroj **využití paměti** zobrazí tyto objekty, pokud jsou zapojeny do řetězců vlastnictví objektů.

V sestavě snímek:

- Strom **spravované haldy** zobrazuje typy a instance v sestavě. Výběrem typu nebo instance se zobrazí stromy **Cesty ke kořenovým** a **odkazovaných objektů** pro vybranou položku.

- **Cesta ke kořenovému** stromu zobrazuje řetězec objektů, které odkazují na typ nebo instanci. Systém uvolňování paměti .NET vyčistí paměť pro objekt pouze v případě, že byly vydány všechny odkazy na něj.

- Strom **Odkazované typy** nebo **Odkazované objekty** zobrazuje objekty, na které odkazuje vybraný typ nebo instance.

### <a name="report-tree-filters"></a><a name="BKMK_Report_tree_filters_"></a>Filtry stromu sestavy

Mnoho typů v aplikacích není pro vývojáře aplikací příliš zajímavé. Filtry sestavy snímek můžete skrýt většinu těchto typů v **spravované haldy** a **cesty ke kořenovým stromům.**

![Možnosti řazení a filtrování](../profiling/media/memuse_sortandfilter.png "MEMUSE_SortAndFilter")

- <a name="BKMK_Filter"></a>Chcete-li strom filtrovat podle názvu typu, zadejte název do pole **Filtr.** Filtr nerozlišuje malá a velká písmena a rozpozná zadaný řetězec v libovolné části názvu typu.

- <a name="BKMK_Collapse_Small_Objects"></a>V rozevíracím souboru **Filtr** vyberte **Sbalit malé objekty,** chcete-li skrýt typy, jejichž **velikost (bajty)** je menší než 0,5 procenta celkové paměti.

- <a name="BKMK_Just_My_Code"></a>V rozevíracím souboru **Filtr** vyberte **Pouze můj kód,** chcete-li skrýt většinu instancí generovaných externím kódem. Externí typy patří do operačního systému nebo součásti architektury nebo jsou generovány kompilátorem.

## <a name="snapshot-details-reports"></a>Sestavy podrobností snímku

 Sestava podrobností snímku popisuje jeden snímek z diagnostické relace. Chcete-li sestavu otevřít, vyberte vazbu velikosti nebo objektů v podokně snímků.

 ![Odkazy na sestavu snímků v podokně snímků](../profiling/media/memuse_snapshotview_snapshotdetailslinks.png "Odkazy na sestavu snímků v podokně snímků")

Oba odkazy otevírají stejnou sestavu. Jediným rozdílem je počáteční pořadí řazení stromu **spravované haldy.** Odkaz velikosti seřadí sestavu podle sloupce **Včetně velikosti (Bajty).** Objekty propojují sestavu podle sloupce **Počet.** Po otevření sestavy můžete změnit sloupec řazení nebo pořadí.

### <a name="managed-heap-tree-snapshot-details-reports"></a><a name="BKMK_Managed_Heap_tree__Snapshot_details_"></a>Strom spravované haldy (sestavy podrobností snímku)
 Strom **spravované haldy** uvádí typy objektů, které jsou uloženy v paměti. Rozbalte název typu a zobrazte deset největších instancí typu seřazených podle velikosti. Vyberte typ nebo instanci, chcete-li zobrazit stromy **Cesty ke kořenovým** a **odkazovaných objektů** pro vybranou položku.

 ![Strom spravované haldy](../profiling/media/memuse__snapshotdetails_managedheaptree.png "Strom spravované haldy")

Strom **spravované haldy** v sestavě podrobností snímku má následující sloupce:

|||
|-|-|
|**Typ objektu**|Název instance typu nebo objektu.|
|**Počet**|Počet instancí objektu typu. **Count** je vždy 1 pro instanci.|
|**Velikost (bajty)**|Pro typ, velikost všech instancí typu ve snímku, menší velikost objektů obsažených v instancích.<br /><br /> Pro instanci velikost objektu, menší velikost objektů obsažených v instanci. |
|**Včetně velikosti (bajty)**|Velikost instancí typu nebo velikost jedné instance, včetně velikosti obsažených objektů.|
|**Modul**|Modul, který obsahuje objekt.|

### <a name="paths-to-root-tree-snapshot-details-reports"></a><a name="BKMK_Paths_to_Root_tree__Snapshot_details_"></a>Cesty ke kořenovému stromu (sestavy podrobností snímku)
**Cesta ke kořenovému stromu** zobrazuje řetězec objektů, které odkazují na typ nebo instanci. Systém uvolňování paměti .NET vyčistí paměť pro objekt pouze v případě, že byly vydány všechny odkazy na něj.

U typu ve stromu **Cesty ke kořenovému** stromu se ve sloupci **Počet odkazů** zobrazí počet objektů, které uchovávají odkazy na tento typ.

![Cesty ke kořenovému stromu pro typy](../profiling/media/memuse_snapshotdetails_type_pathstoroottree.png "Cesty ke kořenovému stromu pro typy")

### <a name="referenced-types-or-referenced-objects-tree-snapshot-details-reports"></a><a name="BKMK_Referenced_Objects_tree__Snapshot_details_"></a>Strom odkazovaných typů nebo odkazovaných objektů (sestavy podrobností snímku)
Strom **Odkazované typy** nebo **Odkazované objekty** zobrazuje objekty, na které odkazuje vybraný typ nebo instance.

![Strom odkazovaných objektů pro instance](../profiling/media/memuse_snapshotdetails_referencedobjects_instance.png "Strom odkazovaných objektů pro instance")

Strom **Odkazované typy** v sestavě podrobností snímku má následující sloupce. Strom **Odkazovaných objektů** nemá sloupec **Počet odkazů.**

|||
|-|-|
|**Typ nebo** instance **objektu**|Název typu nebo instance.|
|**Počet odkazů**|Pro typy počet instancí objektu typu.|
|**Velikost (bajty)**|Pro typ, velikost všech instancí typu, menší velikost objektů obsažených v textu.<br /><br /> Pro instanci velikost objektu, menší velikost objektů obsažených v objektu.|
|**Včetně velikosti (bajty)**|Celková velikost instancí typu nebo velikost instance, včetně velikosti obsažených objektů.|
|**Modul**|Modul, který obsahuje objekt.|

## <a name="snapshot-difference-diff-reports"></a>Sestavy rozdílu snímků (rozdílu)

Sestava rozdílu snímků (diff) zobrazuje změny mezi primárním a předchozím snímekem. Chcete-li otevřít sestavu rozdílů, vyberte jeden z odkazů rozdílů v podokně snímků.

Oba odkazy otevírají stejnou sestavu. Jediným rozdílem je počáteční pořadí řazení stromu **spravované haldy** v sestavě. Odkaz velikosti seřadí sestavu podle sloupce **Rozdíl velikosti včetně (Bajtů).** Objekty propojují sestavu podle sloupce **Počítat rozdíl.** Po otevření sestavy můžete změnit sloupec řazení nebo pořadí.

 ![Odkazy na sestavu rozdílů v podokně snímků](../profiling/media/memuse_snapshotview_snapshotdifflinks.png "Odkazy na sestavu rozdílů v podokně snímků")

### <a name="managed-heap-tree-snapshot-diff-reports"></a><a name="BKMK_Managed_Heap_tree__Snapshot_diff_"></a>Strom spravované haldy (sestavy rozdílu snímků)

 Strom **spravované haldy** uvádí typy objektů, které jsou uloženy v paměti. Název typu můžete rozbalit a zobrazit deset největších instancí typu seřazených podle velikosti. Vyberte typ nebo instanci, chcete-li zobrazit stromy **Cesty ke kořenovým** a **odkazovaných objektů** pro vybranou položku.

 ![Strom spravované haldy pro sestavu rozdílu typu](../profiling/media/memuse_snapshotdiff_type_heap.png "Strom spravované haldy pro sestavu rozdílu typu")

Strom **spravované haldy** v sestavě rozdíl u snímku má následující sloupce:

|||
|-|-|
|**Typ objektu**|Název instance typu nebo objektu.|
|**Počet**|Počet instancí typu v primární snímek. **Count** je vždy 1 pro instanci.|
|**Počítat rozdíl**|Pro typ rozdíl v počtu instancí typu mezi primární snímek a předchozí snímek. Pole je pro instanci prázdné.|
|**Velikost (bajty)**|Velikost objektů v primární snímek, menší velikost objektů v objektech. Pro typ **velikost (bajty)** a **včetně velikost (bajty)** jsou součty velikostí instance typu.|
|**Rozdíl celkové velikosti (bajty)**|Pro typ rozdíl v celkové velikosti instancí typu mezi primární snímek a předchozí snímek, menší velikost objektů v instancích. Pole je pro instanci prázdné.|
|**Včetně velikosti (bajty)**|Velikost objektů v primární snímek, včetně velikosti objektů v objektech.|
|**Rozdíl velikosti včetně (bajty)**|Pro typ rozdíl ve velikosti všech instancí typu mezi primární snímek a předchozí snímek, včetně velikosti objektů v objektech. Pole je pro instanci prázdné.|
|**Modul**|Modul, který obsahuje objekt.|

### <a name="paths-to-root-tree-snapshot-diff-reports"></a><a name="BKMK_Paths_to_Root_tree__Snapshot_diff_"></a>Cesty ke kořenovému stromu (sestavy rozdílu snímků)

**Cesta ke kořenovému stromu** zobrazuje řetězec objektů, které odkazují na typ nebo instanci. Systém uvolňování paměti .NET vyčistí paměť pro objekt pouze v případě, že byly vydány všechny odkazy na něj.

U typu ve stromu **Cesty ke kořenovému** stromu se ve sloupci **Počet odkazů** zobrazí počet objektů, které uchovávají odkazy na tento typ. Rozdíl v počtu od předchozího snímku je ve sloupci **Odkaz diff.**

 ![Cesty ke kořenovému stromu v seestavě rozdílů](../profiling/media/memuse_snapshotdiff_pathstoroot_instance_all.png "Cesty ke kořenovému stromu v seestavě rozdílů")

### <a name="referenced-types-or-referenced-objects-tree-snapshot-diff-reports"></a><a name="BKMK_Referenced_Objects_tree__Snapshot_diff_"></a>Odkazované typy nebo strom odkazovaných objektů (sestavy rozdílu snímků)

Strom **Odkazované typy** nebo **Odkazované objekty** zobrazuje objekty, na které odkazuje vybraný typ nebo instance.

![Odkazované typy v seestavě rozdílu](../profiling/media/memuse_snapshotdiff_referencedtypes.png "Odkazované typy v seestavě rozdílu")

A **Odkazuje typy** stromu v sestavě rozdíl snímek má následující sloupce. Strom **Odkazovaných objektů** má sloupce **Instance**, **Velikost (Bajty),** **Včetně velikosti (Bajty)** a **Modul.**

|||
|-|-|
|**Typ nebo** instance **objektu**|Název instance typu nebo objektu.|
|**Počet odkazů**|Počet instancí typu v primární snímek.|
|**Rozdíl počtu odkazů**|Pro typ rozdíl v počtu instancí typu mezi primární snímek a předchozí snímek.|
|**Velikost (bajty)**|Velikost objektů v primární snímek, menší velikost objektů v objektech. Pro typ **velikost (bajty)** a **včetně velikost (bajty)** jsou součty velikostí instance typu.|
|**Rozdíl celkové velikosti (bajty)**|Pro typ rozdíl v celkové velikosti instancí typu mezi primární snímek a předchozí snímek, menší velikost objektů v instancích. |
|**Včetně velikosti (bajty)**|Velikost objektů v primární snímek, včetně velikosti objektů v objektech.|
|**Rozdíl velikosti včetně (bajty)**|Pro typ rozdíl ve velikosti všech instancí typu mezi primární snímek a předchozí snímek, včetně velikosti objektů v objektech.|
|**Modul**|Modul, který obsahuje objekt.|

## <a name="see-also"></a>Viz také
- [Paměť JavaScriptu](../profiling/javascript-memory.md)
- [Profilace v sadě Visual Studio](../profiling/index.yml)
- [První seznámení s nástroji pro profilaci](../profiling/profiling-feature-tour.md)
- [Doporučené postupy pro výkon pro aplikace UPW pomocí aplikací C++, C# a Visual Basic](/previous-versions/windows/apps/hh750313\(v\=win.10\))
- [Diagnostika problémů s pamětí pomocí nového nástroje využití paměti v sadě Visual Studio](https://devblogs.microsoft.com/devops/diagnosing-memory-issues-with-the-new-memory-usage-tool-in-visual-studio/)