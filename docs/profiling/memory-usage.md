---
title: Míra využití paměti v aplikacích
description: Vyhledání nevrácené paměti a neefektivní paměti během ladění pomocí diagnostické nástroje integrované v ladicím programu.
ms.custom: seodec18
ms.date: 04/25/2018
ms.topic: tutorial
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 8c72b6749dcba857d9a5059a36adc0fae6e0bacf
ms.sourcegitcommit: e98db44f3a33529b0ba188d24390efd09e548191
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/25/2019
ms.locfileid: "71254618"
---
# <a name="measure-memory-usage-in-visual-studio"></a>Míra využití paměti v aplikaci Visual Studio

Vyhledání nevrácené paměti a neefektivní paměti během ladění s integrovaný ladicí program **využití paměti** nástroj pro diagnostiku. Umožňuje nástroj využití paměti, můžete provést jeden nebo více *snímky* spravovaný a nativní paměti haldy pro lepší porozumění tomu dopad využití paměti typy objektů. Můžete shromažďovat snímky technologie .NET, nativní nebo smíšený režim (.NET a nativní) aplikace.

Následující grafické ukazuje **diagnostické nástroje** okno (k dispozici v aplikaci Visual Studio 2015 Update 1 a novější):

![DiagnosticTools&#45;Update1](../profiling/media/diagnostictools-update1.png "DiagnosticTools-Update1")

I když můžete shromažďovat snímky paměti v kdykoli **využití paměti** nástroj, ladicího programu sady Visual Studio můžete použít k řízení, jak vaše aplikace provádí při zkoumání problémů s výkonem. Nastavení zarážek, krokování, příkaz Pozastavit vše a další ladicí program akce pomáhá soustředit vaše vyšetřování výkonu cesty kódu, které jsou nejrelevantnější. Provádění těchto akcí, když vaše aplikace spuštěna, můžete eliminovat zbytečných kód, který vás nezajímají a můžete výrazně zkrátit čas potřebný k diagnostice problému.

Můžete také použít nástroj paměti mimo ladicí program. Zobrazit [využití paměti bez ladění](../profiling/memory-usage-without-debugging2.md). Můžete použít nástroje pro profilaci s žádné ladicí program se připojil s Windows 7 a novější. Windows 8 a novější se vyžaduje pro spuštění nástrojů pro profilaci s ladicím programem (**diagnostické nástroje** okno).

> [!NOTE]
> **Podpora vlastního přidělování** Profil nativní paměti funguje tak, že shromažďuje data události trasování událostí pro [Windows](/windows-hardware/drivers/devtest/event-tracing-for-windows--etw-) , která se generují během běhu.  Na úrovni zdroje byly anotované alokátorů CRT a sadu Windows SDK tak, aby jejich přidělení dat se dají zachytit. Pokud vytváříte vlastní alokátory, pak všechny funkce, které vrací ukazatel na nově přidělenou haldě paměť může být doplněny pomocí [__declspec](/cpp/cpp/declspec)(alokátoru), jak je znázorněno v následujícím příkladu myMalloc:
>
> `__declspec(allocator) void* myMalloc(size_t size)`

V tomto kurzu se naučíte:

> [!div class="checklist"]
> * Pořídit snímky paměti
> * Analýza dat o využití paměti

## <a name="collect-memory-usage-data"></a>Shromažďování dat o využití paměti

1. Otevřete projekt, který chcete ladit v sadě Visual Studio a nastavte zarážku ve vaší aplikaci v místě, kde chcete začít, zkoumání využití paměti.

    Pokud máte oblasti, kde máte podezření na chybu paměti, nastavte k první zarážce, předtím, než dojde k problému paměti.

    > [!TIP]
    > Vzhledem k tomu může být náročné k zaznamenání profilu paměti operace, která vás zajímá, když aplikace často přiděluje a zrušení přidělení paměti, nastavte zarážky na začátku a konci operace (nebo krokovat operaci) k vyhledání konkrétní bod paměť změněna.

2. Nastavení druhé zarážky na konci funkce nebo kód, který chcete analyzovat oblasti (nebo když dojde k problému podezřelý paměti).

3. Okno **Diagnostické nástroje** se zobrazí automaticky (pokud jste ho nevypnuli). Otevřete okno znovu, klikněte na tlačítko **ladění** > **Windows** > **zobrazit diagnostické nástroje**.

4. Zvolte **využití paměti** s **vyberte nástroje** nastavení na panelu nástrojů.

     ![Zobrazení diagnostických nástrojů](../profiling/media/diag-tools-select-tool-2.png "DiagToolsSelectTool")

5. Klikněte na **Ladit / Spustit ladění** (nebo na panelu nástrojů stiskněte **Start** nebo **F5**).

     Jakmile se aplikace načte, zobrazí se souhrnný přehled diagnostických nástrojů.

     ![Karta Souhrn v diagnostických nástrojích](../profiling/media/diag-tools-summary-tab-2.png "DiagToolsSummaryTab")

     > [!NOTE]
     > Protože shromažďování paměti, že data může ovlivnit výkon ladění ve smíšeném režimu nebo nativní aplikace, jsou ve výchozím nastavení zakázané snímky paměti. Pokud chcete povolit snímky v nativních nebo smíšených aplikacích, spusťte relaci ladění (Klávesová zkratka: **F5**). Když **diagnostické nástroje** okna se zobrazí, zvolte **využití paměti** kartu a klikněte na tlačítko **profilace haldy**.
     >
     >  ![Povolit snímky](../profiling/media/dbgdiag_mem_mixedtoolbar_enablesnapshot.png "DBGDIAG_MEM_MixedToolbar_EnableSnapshot")
     >
     >  Stop (Klávesová zkratka:SHIFT+**F5**) a restartujte ladění.

6. K vytvoření snímku na začátku ladicí relaci, zvolte **pořídit snímek** na **využití paměti** souhrnný panel nástrojů. (To může pomoct s nastavte zarážku zde také).

    ![Pořídit snímek](../profiling/media/dbgdiag_mem_mixedtoolbar_takesnapshot.png "DBGDIAG_MEM_MixedToolbar_TakeSnapshot")

     > [!TIP]
     > Pokud chcete vytvořit standardní hodnoty pro porovnání paměti, vezměte v úvahu pořízení snímku na začátku vaší relace ladění.

6. Spusťte scénář, který se zastaví u první zarážky.

7. Když ladicí program je pozastaveno k první zarážce, zvolte **pořídit snímek** na **využití paměti** souhrnný panel nástrojů.

8. Stisknutím klávesy **F5** ke spuštění aplikace na druhém zarážku.

9. Teď vytvořte nový snímek.

     Teď můžete začít analyzovat data.

## <a name="analyze-memory-usage-data"></a>Analýza dat o využití paměti
Řádky tabulku souhrnu využití paměti obsahuje seznam snímků, které jste provedli během relace ladění a poskytuje odkazy na podrobnější zobrazení.

![Tabulka souhrnu paměti](../profiling/media/dbgdiag_mem_summarytable.png "DBGDIAG_MEM_SummaryTable")

 Název sloupce, které závisí na režim ladění zvolte ve vlastnostech projektu: .NET, nativní nebo smíšený (.NET a nativní).

- **Objekty (rozdíl)** a **přidělení (rozdíl)** sloupce zobrazují počet objektů v rozhraní .NET a nativní paměť při pořízení snímku.

- **Velikost haldy (rozdíl)** sloupec zobrazuje počet bajtů v rozhraní .NET a nativní haldy

Pokud jste provedli několik snímků, buňky ovládacího prvku souhrnnou tabulku zahrnují změnu hodnoty mezi řádek snímek a předchozí snímek.

Analýza využití paměti, klikněte na jeden z odkazů, které se otevře podrobnou sestavu využití paměti:

- Chcete-li zobrazit podrobnosti o rozdílu mezi aktuálním snímkem a předchozím snímkem, zvolte odkaz změnit na levé straně na šipku (![zvýšit využití paměti](../profiling/media/prof-tour-mem-usage-up-arrow.png "zvýšit využití paměti")). Červená šipka označuje zvýšení využití paměti a zelenou šipku znamená snížení.

> [!TIP]
> K identifikaci problémů paměti rychleji, diff sestavy jsou seřazeny podle typů objektů, které nejvíce zvýšit celkový počet (klikněte na odkaz změnit v **objekty (rozdíl)** sloupce) nebo, která zvýšil na maximum v celkovou velikost haldy (kliknutím odkaz změnit v **velikost haldy (rozdíl)** sloupec).

- Chcete-li zobrazit podrobnosti o pouze vybraný snímek, klikněte na odkaz jiné změny.

   Sestavy se zobrazí v samostatném okně.

### <a name="managed-types-reports"></a>Spravované typy sestav
 Vyberte aktuální propojení **objekty (rozdíl)** nebo **přidělení (rozdíl)** buňku v tabulce souhrnu využití paměti.

 ![Ladicí program spravovaného typu sestavy &#45; cesty ke kořenu](../profiling/media/dbgdiag_mem_managedtypesreport_pathstoroot.png "DBGDIAG_MEM_ManagedTypesReport_PathsToRoot")

 Horní podokno zobrazuje počet a velikost typů ve snímku, včetně velikosti všech objektů, na které odkazuje typ (**celkové velikosti**).

 **Cesty ke kořenu** stromu v dolním podokně zobrazí objekty, které odkazují na vybraném v horním podokně typu. Paměť pro objekt vyčistí systému uvolňování paměti rozhraní .NET Framework, pouze v případě, že byly vydány poslední typ, který na ni odkazuje.

 **Odkazované typy** Strom zobrazuje odkazy, které jsou uloženy ve vybraném v horním podokně typu.

 ![Zobrazení sestavy spravovaných odkazovaných typů](../profiling/media/dbgdiag_mem_managedtypesreport_referencedtypes.png "DBGDIAG_MEM_ManagedTypesReport_ReferencedTypes")

 K zobrazení instance vybraného typu v horním podokně, vyberte ![Instance ikonu](../profiling/media/dbgdiag_mem_instanceicon.png "DBGDIAG_MEM_InstanceIcon") ikonu.

 ![Zobrazení instancí](../profiling/media/dbgdiag_mem_managedtypesreport_instances.png "DBGDIAG_MEM_ManagedTypesReport_Instances")

 **Instance** zobrazení instancí vybraného objektu ve snímku v horním podokně. **Cesty ke kořenu** a **odkazované objekty** podokně zobrazí objekty, které odkazují na vybranou instanci a typy, které se odkazuje vybraná instance. Když ladicí program se zastaví v místě, kde pořízení snímku, může najedete myší **hodnotu** buněk k zobrazení hodnoty objektu v popisu tlačítka.

### <a name="native-type-reports"></a>Nativní typ sestavy
 Vyberte aktuální propojení **přidělení (rozdíl)** nebo **velikost haldy (rozdíl)** buňku v tabulce souhrnu využití paměti z **diagnostické nástroje** okna.

 ![Nativní typ zobrazení](../profiling/media/dbgdiag_mem_native_typesview.png "DBGDIAG_MEM_Native_TypesView")

 **Zobrazení typů** zobrazuje počet a velikost typů ve snímku.

- Zvolte ikonu instance (![ikonu instance ve sloupci Typ objektu](../profiling/media/dbg_mma_instancesicon.png "DBG_MMA_InstancesIcon")) z vybraného typu k zobrazení informací o objektech vybraného typu ve snímku.

     **Instance** zobrazení zobrazí každou instanci daného typu. Výběr instance zobrazí, které vedlo k vytvoření instance v zásobníku volání **zásobník volání přidělení** podokně.

     ![Zobrazení instancí](../profiling/media/dbgdiag_mem_native_instances.png "DBGDIAG_MEM_Native_Instances")

- Zvolte **zobrazení zásobníků** v **režim zobrazení** seznamu zobrazíte zásobník přidělení pro vybraný typ.

     ![Stacks View](../profiling/media/dbgdiag_mem_native_stacksview.png "DBGDIAG_MEM_Native_StacksView")

### <a name="change-diff-reports"></a>Změnit sestavy (rozdíl)

- Zvolte odkaz změnit v buňce souhrnnou tabulku **využití paměti** kartě **diagnostické nástroje** okna.

   ![Výběr sestavy &#40;rozdílů&#41; změn](../profiling/media/dbgdiag_mem_choosediffreport.png "DBGDIAG_MEM_ChooseDiffReport")

- Zvolte snímek v **porovnat** seznam spravované nebo nativní sestavy.

   ![Zvolte snímek ze seznamu porovnat](../profiling/media/dbgdiag_mem_choosecompareto.png "DBGDIAG_MEM_ChooseCompareTo")

Sestava změn přidává sloupce (označené **(rozdíl)** ) základní sestavy, které zobrazují rozdíl mezi hodnotami základní snímek a snímek porovnání. Zde je, jak může vypadat sestavy rozdílu nativní typ zobrazení:

![Native Types Diff View](../profiling/media/dbgdiag_mem_native_typesviewdiff.png "DBGDIAG_MEM_Native_TypesViewDiff")

## <a name="blogs-and-videos"></a>Blogy a videa

[Analýza využití procesoru a paměti během ladění](https://devblogs.microsoft.com/visualstudio/analyze-cpu-memory-while-debugging/)

[Blog C++ vizuálu: Profilace paměti v jazyce C++ Visual 2015](https://devblogs.microsoft.com/cppblog/memory-profiling-in-visual-c-2015/)

## <a name="next-steps"></a>Další kroky

V tomto kurzu jste zjistili, jak shromažďovat a analyzovat data o využití paměti. Pokud jste již dokončili [tour profiler](../profiling/profiling-feature-tour.md), možná budete chtít získat rychlý přehled postupu k analýze využití procesoru ve vašich aplikacích.

> [!div class="nextstepaction"]
> [Analýza využití procesoru](../profiling/beginners-guide-to-performance-profiling.md)
