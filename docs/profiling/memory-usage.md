---
title: Měření využití paměti ve vašich aplikacích
description: Při ladění pomocí diagnostického nástroje integrovaného s ladicím programem můžete najít nevracení paměti a neefektivní paměť.
ms.custom: seodec18
ms.date: 04/25/2018
ms.topic: tutorial
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 3d259c6fa69821d1fecd26944227bff86cc82104
ms.sourcegitcommit: 105e7b5a486262bc92939980383ceee068098a11
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/30/2020
ms.locfileid: "97815851"
---
# <a name="measure-memory-usage-in-visual-studio"></a>Měření paměti profilu v sadě Visual Studio

Najděte nevracení paměti a neefektivní paměť při ladění pomocí nástroje pro diagnostiku **využití paměti** integrovaného ladicího programu. Nástroj využití paměti umožňuje provést jeden nebo více *snímků* spravované a nativní haldy paměti, aby bylo možné pochopit využití paměti pro typy objektů. Využití paměti můžete také analyzovat bez připojeného ladicího programu nebo zacílení na spuštěnou aplikaci. Další informace najdete v tématu [spuštění nástrojů pro profilaci pomocí ladicího programu nebo bez něj](../profiling/running-profiling-tools-with-or-without-the-debugger.md).

I když můžete shromažďovat snímky paměti kdykoli v nástroji **využití paměti** , můžete použít ladicí program sady Visual Studio k řízení toho, jak se vaše aplikace spouští při zkoumání problémů s výkonem. Nastavení zarážek, krokování, přerušit vše a další akce ladicího programu vám umožní zaměřit se na vaše vyšetřování výkonnosti v případě nejdůležitějších cest kódu. Provedení těchto akcí v době, kdy je vaše aplikace spuštěná, může eliminovat šum z kódu, který vás neklade, a může výrazně zkrátit dobu, po kterou vám pomůže diagnostikovat problém.

> [!Important]
> Diagnostické nástroje integrované v ladicím programu se podporují pro vývoj pro .NET v aplikaci Visual Studio, včetně ASP.NET, ASP.NET Core, nativního vývoje/C++ a kombinovaného režimu (.NET a nativních) aplikací. Pro spuštění nástrojů pro profilaci pomocí ladicího programu (**diagnostické nástroje** okno) se vyžaduje systém Windows 8 nebo novější.

V tomto kurzu:

> [!div class="checklist"]
> * Pořídit snímky paměti
> * Analyzovat data o využití paměti

Pokud **využití paměti** neposkytuje data, která potřebujete, další nástroje pro profilování v [profileru výkonu](../profiling/profiling-feature-tour.md#post_mortem) poskytují různé druhy informací, které mohou být pro vás užitečné. V mnoha případech může být problém s výkonem vaší aplikace způsoben jinou výjimkou paměti, jako je například CPU, uživatelské rozhraní pro vykreslování nebo doba požadavku na síť.

> [!NOTE]
> **Podpora vlastního přidělování** Profil nativní paměti funguje tak, že shromažďuje data události trasování událostí pro [Windows](/windows-hardware/drivers/devtest/event-tracing-for-windows--etw-) , která se generují během běhu.  Alokátory v CRT a Windows SDK byly opatřeny poznámkami na zdrojové úrovni, aby bylo možné zachytit jejich alokační data. Pokud píšete vlastní přidělování, pak všechny funkce, které vracejí ukazatel na nově přidělenou paměť haldy, mohou být upraveny pomocí [__declspec](/cpp/cpp/declspec)(přidělování), jak je vidět v tomto příkladu pro myMalloc:
>
> `__declspec(allocator) void* myMalloc(size_t size)`

## <a name="collect-memory-usage-data"></a>Shromažďování dat o využití paměti

1. Otevřete projekt, který chcete ladit v sadě Visual Studio, a nastavte zarážku v aplikaci v místě, kde chcete začít zkoumat využití paměti.

    Pokud máte oblast, kde máte podezření, že dojde k potížím s pamětí, nastavte první zarážku předtím, než dojde k problému s pamětí.

    > [!TIP]
    > Vzhledem k tomu, že může být náročné zachytit profil paměti operace, která vás zajímá, když vaše aplikace často přiděluje paměť, nastavovat zarážky na začátku a na konci operace (nebo krokovat s operací), aby bylo možné přesně určit, jakým bodem se paměť změnila.

2. Nastavte druhou zarážku na konci funkce nebo oblasti kódu, který chcete analyzovat (nebo po výskytu problému s podezřelou pamětí).

3. Okno **Diagnostické nástroje** se zobrazí automaticky (pokud jste ho nevypnuli). Chcete-li okno znovu zobrazit, klikněte na tlačítko **ladit**  >  **Windows**  >  **show diagnostické nástroje**.

4. Zvolte **využití paměti** pomocí nastavení **nástroje vybrat** na panelu nástrojů.

     ![Zobrazit diagnostické nástroje](../profiling/media/diag-tools-select-tool-2.png "DiagToolsSelectTool")

5. Klikněte na **Ladit / Spustit ladění** (nebo na panelu nástrojů stiskněte **Start** nebo **F5**).

     Jakmile se aplikace načte, zobrazí se souhrnný přehled diagnostických nástrojů.

     ![Karta souhrn nástrojů pro diagnostiku](../profiling/media/diag-tools-summary-tab-2.png "DiagToolsSummaryTab")

     > [!NOTE]
     > Vzhledem k tomu, že shromažďování dat o paměti může ovlivnit výkon ladění vašich aplikací v nativním nebo kombinovaném režimu, jsou snímky paměti ve výchozím nastavení zakázány. Pokud chcete povolit snímky v nativních nebo smíšených aplikacích, spusťte relaci ladění (Klávesová zkratka: **F5**). Jakmile se zobrazí okno **diagnostické nástroje** , zvolte kartu **využití paměti** a pak zvolte **profilace haldy**.
     >
     >  ![Povolit snímky](../profiling/media/dbgdiag_mem_mixedtoolbar_enablesnapshot.png "DBGDIAG_MEM_MixedToolbar_EnableSnapshot")
     >
     >  Stop (Klávesová zkratka: **SHIFT** + **F5**) a opětovné spuštění ladění.

6. Chcete-li pořídit snímek na začátku relace ladění, vyberte možnost **pořídit snímek** na panelu nástrojů souhrn **využití paměti** . (Můžete také nastavit zarážku.)

    ![Pořídit snímek](../profiling/media/dbgdiag_mem_mixedtoolbar_takesnapshot.png "DBGDIAG_MEM_MixedToolbar_TakeSnapshot")

     > [!TIP]
     > Chcete-li vytvořit směrný plán pro porovnání paměti, zvažte možnost pořízení snímku na začátku relace ladění.

6. Spusťte scénář, který se zastaví u první zarážky.

7. I když je ladicí program pozastaven při první zarážce, vyberte možnost **pořídit snímek** na panelu nástrojů souhrn **využití paměti** .

8. Stisknutím klávesy **F5** spusťte aplikaci pro druhou zarážku.

9. Nyní proveďte jiný snímek.

     Teď můžete začít analyzovat data.

## <a name="analyze-memory-usage-data"></a>Analyzovat data o využití paměti
Tabulka souhrnu využití paměti obsahuje seznam snímků, které jste provedli během relace ladění, a poskytuje odkazy na podrobnější zobrazení.

![Tabulka souhrnu paměti](../profiling/media/dbgdiag_mem_summarytable.png "DBGDIAG_MEM_SummaryTable")

 Název sloupců závisí na režimu ladění, který zvolíte ve vlastnostech projektu: .NET, Native nebo Mixed (rozhraní .NET i nativní).

- Sloupce **objektů (diff)** a **alokace (diff)** zobrazují počet objektů v rozhraní .NET a nativní paměti při pořízení snímku.

- Sloupec **velikosti haldy (diff)** zobrazuje počet bajtů v rozhraní .NET a nativních haldách.

Když jste převzali více snímků, buňky souhrnné tabulky obsahují změnu hodnoty mezi snímkem řádku a předchozím snímkem.

Pokud chcete analyzovat využití paměti, klikněte na jeden z odkazů, který otevře podrobnou sestavu využití paměti:

- Chcete-li zobrazit podrobnosti o rozdílu mezi aktuálním snímkem a předchozím snímkem, klikněte na odkaz změnit nalevo od šipky (![zvýšení využití paměti](../profiling/media/prof-tour-mem-usage-up-arrow.png "Zvýšení využití paměti")). Červená šipka indikuje zvýšení využití paměti a zelenou šipku, která označuje snížení.

> [!TIP]
> Aby bylo možné rychleji identifikovat problémy s pamětí, je rozdílové sestavy seřazeny podle typů objektů, které zvýšily největší počet (klikněte na sloupec změnit odkaz ve sloupci **objekty** ) nebo na hodnotu větší v celkové velikosti haldy (klikněte na odkaz změnit odkaz ve sloupci **Velikost haldy (diff)** ).

- Chcete-li zobrazit podrobnosti pouze vybraného snímku, klikněte na odkaz bez změny.

   Sestava se zobrazí v samostatném okně.

### <a name="managed-types-reports"></a>Sestavy spravovaných typů
 V tabulce Souhrn využití paměti vyberte aktuální odkaz na buňku **objektů (diff)** nebo **přidělení (diff)** .

 ![Sestava spravovaného typu ladicího programu &#45; cesty ke kořenu](../profiling/media/dbgdiag_mem_managedtypesreport_pathstoroot.png "DBGDIAG_MEM_ManagedTypesReport_PathsToRoot")

 V horním podokně se zobrazuje počet a velikost typů ve snímku, včetně velikosti všech objektů, na které se odkazuje typ (**Celková velikost**).

 **Cesta ke kořenovému** stromu v dolním podokně zobrazuje objekty, které odkazují na typ vybraný v horním podokně. Systém uvolňování paměti .NET vyčistí paměť objektu pouze v případě, že byl vydán poslední typ, který na něj odkazuje.

 Strom **odkazovaných objektů** zobrazuje odkazy, které jsou uchovávány typem vybraným v horním podokně.

 ![Zobrazení sestavy spravovaných odkazovaných objektů](../profiling/media/dbgdiag_mem_managedtypesreport_referencedtypes.png "DBGDIAG_MEM_ManagedTypesReport_ReferencedTypes")

 Chcete-li zobrazit instance vybraného typu v horním podokně, klikněte na ikonu ![ikony instance](../profiling/media/dbgdiag_mem_instanceicon.png "DBGDIAG_MEM_InstanceIcon") .

 ![Snímek obrazovky zobrazení instance v nástroji využití paměti sady Visual Studio, který zobrazuje podokno instance a podokno cesty ke kořenu a odkazované objekty.](../profiling/media/dbgdiag_mem_managedtypesreport_instances.png "DBGDIAG_MEM_ManagedTypesReport_Instances")

 Zobrazení **instance** zobrazuje instance vybraného objektu ve snímku v horním podokně. Podokno **cesty k kořenu** a **odkazované objekty** zobrazuje objekty, které odkazují na vybranou instanci a typy, na které odkazuje vybraná instance. Když je ladicí program zastaven v místě, kde byl snímek vytvořen, můžete umístit ukazatel myši nad buňku **Value** a zobrazit tak hodnoty objektu v popisu tlačítka.

### <a name="native-type-reports"></a>Sestavy nativního typu
 Vyberte aktuální odkaz na buňku **přidělení (diff)** nebo **Velikost haldy (diff)** v tabulce souhrn využití paměti okna **diagnostické nástroje** .

 ![Zobrazení nativního typu](../profiling/media/dbgdiag_mem_native_typesview.png "DBGDIAG_MEM_Native_TypesView")

 **Zobrazení typy** zobrazuje počet a velikost typů ve snímku.

- Vyberte ikonu instance (![ikona instance ve sloupci Typ objektu](../profiling/media/dbg_mma_instancesicon.png "DBG_MMA_InstancesIcon")) vybraného typu pro zobrazení informací o objektech vybraného typu ve snímku.

     Zobrazení **instance** zobrazuje všechny instance vybraného typu. Výběr instance zobrazí zásobník volání, jehož výsledkem bylo vytvoření instance v podokně **zásobník volání přidělení** .

     ![Snímek obrazovky zobrazení instance v nástroji využití paměti sady Visual Studio se zobrazením podokna instance a zásobníku volání alokace.](../profiling/media/dbgdiag_mem_native_instances.png "DBGDIAG_MEM_Native_Instances")

- Výběrem možnosti **zobrazení zásobníků** v seznamu **režim zobrazení** zobrazíte zásobník přidělení pro vybraný typ.

     ![Zobrazení zásobníků](../profiling/media/dbgdiag_mem_native_stacksview.png "DBGDIAG_MEM_Native_StacksView")

### <a name="change-diff-reports"></a>Změny (rozdílové) sestavy

- Vyberte odkaz změnit v buňce tabulky souhrn na kartě **využití paměti** v okně **diagnostické nástroje** .

   ![Zvolit sestavu rozdíl&#41; &#40;změn](../profiling/media/dbgdiag_mem_choosediffreport.png "DBGDIAG_MEM_ChooseDiffReport")

- Vyberte snímek v seznamu **porovnat se** správou nebo nativní sestavou.

   ![Výběr snímku ze seznamu porovnat s](../profiling/media/dbgdiag_mem_choosecompareto.png "DBGDIAG_MEM_ChooseCompareTo")

Sestava změny přidá sloupce (označené jako **(diff)**) do základní sestavy, která zobrazuje rozdíl mezi základní hodnotou snímku a snímkem porovnání. Tady je příklad, jak může vypadat rozdílová sestava zobrazení nativního typu:

![Zobrazení rozdílu nativních typů](../profiling/media/dbgdiag_mem_native_typesviewdiff.png "DBGDIAG_MEM_Native_TypesViewDiff")

## <a name="blogs-and-videos"></a>Blogy a videa

[Analyzovat procesor a paměť během ladění](https://devblogs.microsoft.com/visualstudio/analyze-cpu-memory-while-debugging/)

[Visual C++ blog: profilace paměti v Visual C++ 2015](https://devblogs.microsoft.com/cppblog/memory-profiling-in-visual-c-2015/)

## <a name="next-steps"></a>Další kroky

V tomto kurzu jste se naučili, jak shromažďovat a analyzovat data o využití paměti. Pokud jste už dokončili [prohlídku profileru](../profiling/profiling-feature-tour.md), možná budete chtít získat rychlý přehled o tom, jak analyzovat využití procesoru ve vašich aplikacích.

> [!div class="nextstepaction"]
> [Analýza využití procesoru](../profiling/beginners-guide-to-performance-profiling.md)
