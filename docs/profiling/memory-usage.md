---
title: Měření využití paměti v aplikacích
description: Najít nevracení paměti a neefektivní paměti při ladění pomocí diagnostického nástroje integrovaného ladicím programem.
ms.custom: seodec18
ms.date: 04/25/2018
ms.topic: tutorial
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 2876e1b25380719a4424c5828c8b37fb5bb72b41
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/20/2020
ms.locfileid: "75929235"
---
# <a name="measure-memory-usage-in-visual-studio"></a>Měření využití paměti v sadě Visual Studio

Najít nevracení paměti a neefektivní paměti při ladění pomocí ladicího programu integrované **využití paměti diagnostického** nástroje. Nástroj využití paměti umožňuje pořizovat jeden nebo více *snímků haldy* spravované a nativní paměti, abyste lépe porozuměli dopadu typů objektů na využití paměti. Můžete shromažďovat snímky aplikací .NET, nativní nebo smíšený režim (.NET a nativní).

Následující obrázek znázorňuje okno **Diagnostické nástroje** (k dispozici v aktualizaci Visual Studio 2015 Update 1 a novějších verzích):

![DiagnosticTools&#45;Update1](../profiling/media/diagnostictools-update1.png "DiagnosticTools-Update1")

I když můžete kdykoli shromažďovat snímky paměti v nástroji **využití paměti,** můžete použít ladicí program sady Visual Studio k řízení způsobu spuštění aplikace při zkoumání problémů s výkonem. Nastavení zarážek, krokování, break all a další akce ladicího programu vám může pomoci zaměřit vaše sledování výkonu na cesty kódu, které jsou nejrelevantnější. Provádění těchto akcí v době, kdy je aplikace spuštěná, může eliminovat šum z kódu, který vás nezajímá, a může výrazně zkrátit dobu, kterou trvá diagnostika problému.

Můžete také použít paměťový nástroj mimo ladicí program. Viz [Využití paměti bez ladění](../profiling/memory-usage-without-debugging2.md). Můžete použít profilovací nástroje bez ladicího programu připojeného k systému Windows 7 a novějším. Windows 8 a novější je nutné spustit profilování nástroje s ladicím programem **(Diagnostické nástroje** okna).

> [!NOTE]
> **Vlastní podpora přidělování** Profiler nativní paměti funguje tak, že shromažďuje data událostí přidělení [ETW](/windows-hardware/drivers/devtest/event-tracing-for-windows--etw-) vyzařovaná během běhu.  Alokátory v CRT a Windows SDK byly anotovány na zdrojové úrovni tak, aby jejich přidělení dat mohou být zachyceny. Pokud píšete vlastní alokátory, pak všechny funkce, které vrátí ukazatel na nově přidělené paměti haldy může být zdobené [__declspec](/cpp/cpp/declspec)(alokátor), jak je vidět v tomto příkladu pro myMalloc:
>
> `__declspec(allocator) void* myMalloc(size_t size)`

V tomto kurzu provedete následující:

> [!div class="checklist"]
> * Pořizování snímků paměti
> * Analýza dat využití paměti

## <a name="collect-memory-usage-data"></a>Shromažďování dat o využití paměti

1. Otevřete projekt, který chcete ladit v sadě Visual Studio a nastavte zarážku ve vaší aplikaci v místě, kde chcete začít zkoumat využití paměti.

    Pokud máte oblast, kde máte podezření na problém s pamětí, nastavte první zarážku před výskytem problému s pamětí.

    > [!TIP]
    > Vzhledem k tomu, že může být náročné zachytit profil paměti operace, která vás zajímá, když vaše aplikace často přiděluje a ruší přidělení paměti, nastavte zarážky na začátku a na konci operace (nebo krokujte operací) a najděte přesný bod, který paměť změněna.

2. Nastavte druhou zarážku na konci funkce nebo oblasti kódu, kterou chcete analyzovat (nebo po výskytu podezření na problém s pamětí).

3. Okno **Diagnostické nástroje** se zobrazí automaticky (pokud jste ho nevypnuli). Chcete-li okno znovu vyvolat, klepněte na tlačítko **Ladit** > **diagnostické nástroje služby****Windows** > Show .

4. Zvolte **Využití paměti** s nastavením **Vybrat nástroje** na panelu nástrojů.

     ![Zobrazit nástroje diagnostiky](../profiling/media/diag-tools-select-tool-2.png "DiagToolsSelectTool")

5. Klikněte na **Ladit / Spustit ladění** (nebo na panelu nástrojů stiskněte **Start** nebo **F5**).

     Jakmile se aplikace načte, zobrazí se souhrnný přehled diagnostických nástrojů.

     ![Karta Souhrn diagnostických nástrojů](../profiling/media/diag-tools-summary-tab-2.png "DiagToolsSummaryTab")

     > [!NOTE]
     > Vzhledem k tomu, že shromažďování paměťových dat může ovlivnit výkon ladění aplikací v nativním nebo smíšeném režimu, jsou snímky paměti ve výchozím nastavení zakázány. Chcete-li povolit snímky v aplikacích v nativním nebo smíšeném režimu, spusťte relaci ladění (Klávesová zkratka: **F5).** Po otevření okna **Diagnostické nástroje** zvolte kartu **Využití paměti** a pak zvolte **Profilování haldy**.
     >
     >  ![Povolení snímků](../profiling/media/dbgdiag_mem_mixedtoolbar_enablesnapshot.png "DBGDIAG_MEM_MixedToolbar_EnableSnapshot")
     >
     >  Stop (Klávesová zkratka: **Shift**+**F5)** a restartujte ladění.

6. Chcete-li pořizovat snímek na začátku relace ladění, zvolte **Pořizovat snímek** na panelu **souhrnu využití paměti.** (To může pomoci nastavit zarážku i zde.)

    ![Pořízení snímku](../profiling/media/dbgdiag_mem_mixedtoolbar_takesnapshot.png "DBGDIAG_MEM_MixedToolbar_TakeSnapshot")

     > [!TIP]
     > Chcete-li vytvořit směrný plán pro porovnání paměti, zvažte pořízení snímku na začátku relace ladění.

6. Spusťte scénář, který se zastaví u první zarážky.

7. Zatímco ladicí program je pozastavena na první zarážku, zvolte **Pořizovat snímek** na panelu nástrojů **souhrn využití paměti.**

8. Stisknutím **klávesy F5** spusťte aplikaci na druhou zarážku.

9. Nyní pořizovat další snímek.

     Teď můžete začít analyzovat data.

## <a name="analyze-memory-usage-data"></a>Analýza dat využití paměti
Řádky využití paměti souhrnné tabulky uvádí snímky, které jste provedli během relace ladění a poskytuje odkazy na podrobnější zobrazení.

![Souhrnná tabulka paměti](../profiling/media/dbgdiag_mem_summarytable.png "DBGDIAG_MEM_SummaryTable")

 Název sloupců závisí na režimu ladění, který zvolíte ve vlastnostech projektu: .NET, nativní nebo smíšené (rozhraní .NET i nativní).

- Sloupce **Objekty (Rozdíl)** a **Přidělení (Rozdíl)** zobrazují počet objektů v rozhraní .NET a nativní paměti při pořízení snímku.

- Sloupec **Velikost haldy (Diff)** zobrazuje počet bajtů v souboru .NET a nativních haldách.

Pokud jste provedli více snímků, buňky souhrnné tabulky obsahují změnu hodnoty mezi snímkem řádku a předchozím snímkem.

Chcete-li analyzovat využití paměti, klepněte na jeden z odkazů, které otevírají podrobnou zprávu o využití paměti:

- Chcete-li zobrazit podrobnosti o rozdílu mezi aktuálním a předchozím snímkem, zvolte odkaz na změnu vlevo od šipky (![Zvýšení využití paměti](../profiling/media/prof-tour-mem-usage-up-arrow.png "Zvýšení využití paměti")). Červená šipka označuje zvýšení využití paměti a zelená šipka označuje snížení.

> [!TIP]
> Chcete-li pomoci rychleji identifikovat problémy s pamětí, jsou sestavy rozdílů seřazeny podle typů objektů, které se nejvíce zvýšily v celkovém počtu (klikněte na odkaz změnit ve **sloupci Objekty (Rozdíl)** nebo které zvýšily nejvíce v celkové velikosti haldy (klikněte na odkaz na změnu ve **sloupci Velikost haldy (Rozdíl).**

- Chcete-li zobrazit podrobnosti pouze o vybraném snímku, klepněte na odkaz bez změny.

   Sestava se zobrazí v samostatném okně.

### <a name="managed-types-reports"></a>Sestavy spravovaných typů
 V souhrnné tabulce Využití paměti zvolte aktuální propojení **buňky Objekty (Rozdíl)** nebo **Přidělení (Rozdíl).**

 ![Sestava spravovaného typu ladicího programu &#45; cesty ke kořenům](../profiling/media/dbgdiag_mem_managedtypesreport_pathstoroot.png "DBGDIAG_MEM_ManagedTypesReport_PathsToRoot")

 Horní podokno zobrazuje počet a velikost typů ve snímku, včetně velikosti všech objektů, na které odkazuje typ (**Včetně velikosti**).

 Strom **Cesty ke kořenům** v dolním podokně zobrazuje objekty, které odkazují na typ vybraný v horním podokně. Systém uvolňování paměti rozhraní .NET Framework vyčistí paměť pro objekt pouze v případě, že byl vydán poslední typ, který na něj odkazuje.

 Strom **Odkazované objekty** zobrazuje odkazy, které jsou podrženy typem vybraným v horním podokně.

 ![Zobrazení sestavy spravované odkazované objekty](../profiling/media/dbgdiag_mem_managedtypesreport_referencedtypes.png "DBGDIAG_MEM_ManagedTypesReport_ReferencedTypes")

 Chcete-li zobrazit instance vybraného typu v horním podokně, zvolte ikonu ![ikony Instance.](../profiling/media/dbgdiag_mem_instanceicon.png "DBGDIAG_MEM_InstanceIcon")

 ![Zobrazení instance](../profiling/media/dbgdiag_mem_managedtypesreport_instances.png "DBGDIAG_MEM_ManagedTypesReport_Instances")

 Zobrazení **Instance** zobrazuje instance vybraného objektu ve snímku v horním podokně. Podokno **Cesty ke kořenovým** a **odkazovitým objektům** zobrazuje objekty, které odkazují na vybranou instanci, a typy, na které vybraná instance odkazuje. Když je ladicí program zastaven v bodě, kde byl snímek pořízen, můžete najet na **buňku Hodnota** a zobrazit hodnoty objektu v tipu nástroje.

### <a name="native-type-reports"></a>Sestavy nativního typu
 Zvolte aktuální odkaz **buňky Allocations (Diff)** nebo **Haldy (Diff)** v souhrnné tabulce Využití paměti v okně **Diagnostické nástroje.**

 ![Nativní zobrazení typu](../profiling/media/dbgdiag_mem_native_typesview.png "DBGDIAG_MEM_Native_TypesView")

 **Zobrazení typů** zobrazuje počet a velikost typů ve snímku.

- Zvolte ikonu instancí (![Ikona instance ve sloupci Typ objektu](../profiling/media/dbg_mma_instancesicon.png "DBG_MMA_InstancesIcon")) vybraného typu, chcete-li zobrazit informace o objektech vybraného typu ve snímku.

     Zobrazení Instance zobrazuje každou **instanci** vybraného typu. Výběrem instance se zobrazí zásobník volání, který vyústil ve vytvoření instance v podokně **Zásobník volání přidělení.**

     ![Zobrazení instance](../profiling/media/dbgdiag_mem_native_instances.png "DBGDIAG_MEM_Native_Instances")

- Chcete-li zobrazit **View Mode** zásobník přidělení pro vybraný typ, zvolte **zobrazení zásobníku zásobníků zásobníků** zásobníků zásobníků zásobníků.

     ![Zobrazení zásobníků](../profiling/media/dbgdiag_mem_native_stacksview.png "DBGDIAG_MEM_Native_StacksView")

### <a name="change-diff-reports"></a>Sestavy změn (rozdílů)

- Zvolte odkaz na změnu v buňce souhrnné tabulky karty **Využití paměti** v okně **Diagnostické nástroje.**

   ![Volba změny &#40;&#41; sestavy rozdílu](../profiling/media/dbgdiag_mem_choosediffreport.png "DBGDIAG_MEM_ChooseDiffReport")

- Vseznamu Porovnat **se** stavem spravované nebo nativní sestavy zvolte snímek.

   ![Výběr snímku ze seznamu Porovnat v](../profiling/media/dbgdiag_mem_choosecompareto.png "DBGDIAG_MEM_ChooseCompareTo")

Sestava změn přidá do základní sestavy sloupce (označené **(Diff),** které zobrazují rozdíl mezi hodnotou základního snímku a srovnávacím snímkem. Sestava rozdílu zobrazení nativního typu může vypadat takto:

![Nativní typy rozdílové zobrazení](../profiling/media/dbgdiag_mem_native_typesviewdiff.png "DBGDIAG_MEM_Native_TypesViewDiff")

## <a name="blogs-and-videos"></a>Blogy a videa

[Analýza procesoru a paměti při ladění](https://devblogs.microsoft.com/visualstudio/analyze-cpu-memory-while-debugging/)

[Visual C++ Blog: Profilování paměti ve Visual C++ 2015](https://devblogs.microsoft.com/cppblog/memory-profiling-in-visual-c-2015/)

## <a name="next-steps"></a>Další kroky

V tomto kurzu jste se naučili shromažďovat a analyzovat data využití paměti. Pokud jste již dokončili [prohlídku profileru](../profiling/profiling-feature-tour.md), můžete se rychle podívat na to, jak analyzovat využití procesoru ve vašich aplikacích.

> [!div class="nextstepaction"]
> [Analýza využití procesoru](../profiling/beginners-guide-to-performance-profiling.md)
