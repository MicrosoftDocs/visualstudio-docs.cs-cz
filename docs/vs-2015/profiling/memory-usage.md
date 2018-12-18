---
title: Využití paměti | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: bbb58d6c-3362-4ca3-8e87-64b2d4415bf6
caps.latest.revision: 17
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f62137fcbc71df87fb0569ed0516a7ae36d8a30a
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51746194"
---
# <a name="memory-usage"></a>Využití paměti
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vyhledání nevrácené paměti a neefektivní paměti během ladění s integrovaný ladicí program **využití paměti** nástroj pro diagnostiku. Umožňuje nástroj využití paměti, můžete provést jeden nebo více *snímky* spravovaný a nativní paměti haldy. Můžete shromažďovat snímky technologie .NET, nativní nebo smíšený režim (.NET a nativní) aplikace.  
  
- Jeden snímek pochopit jeho relativní dopad typů objektů na využití paměti a vyhledání kódu vaší aplikace, která používá paměť neefektivně, můžete analyzovat.  
  
- Můžete také porovnat (rozdíl) dvěma snímky vyhledejte oblasti v kódu aplikace, které způsobují využití paměti časem zvětšuje.  
  
  Následující grafické ukazuje **diagnostické nástroje** okna v aplikaci Visual Studio 2015 Update 1:  
  
  ![DiagnosticTools&#45;Update1](../profiling/media/diagnostictools-update1.png "DiagnosticTools-Update1")  
  
  I když můžete shromažďovat snímky paměti v kdykoli **využití paměti** nástroj, ladicího programu sady Visual Studio můžete použít k řízení, jak vaše aplikace provádí při zkoumání problémů s výkonem. Nastavení zarážek, krokování, příkaz Pozastavit vše a další ladicí program akce pomáhá soustředit vaše vyšetřování výkonu cesty kódu, které jsou nejrelevantnější. Provádění těchto akcí, když vaše aplikace spuštěna, můžete eliminuje zbytečných kód, který vás nezajímají a můžete výrazně zkrátit čas potřebný k diagnostice problému.  
  
  Můžete také použít nástroj paměti mimo ladicí program. Zobrazit [využití paměti bez ladění](http://msdn.microsoft.com/library/8883bc5f-df86-4f84-aa2b-a21150f499b0).  
  
> [!NOTE]
>  **Podpora vlastního alokátoru** profiler nativní paměť funguje tak, že shromažďování přidělení [trasování událostí pro Windows](https://msdn.microsoft.com/library/windows/desktop/bb968803\(v=vs.85\).aspx) data událostí, protože ho vygeneroval za běhu.  Na úrovni zdroje byly anotované alokátorů CRT a sadu Windows SDK tak, aby jejich přidělení dat se dají zachytit.  Při psaní vlastních alokátorů, než všechny funkce, které vrací ukazatel na nově přidělenou haldy paměti může být doplněny pomocí [__declspec](http://msdn.microsoft.com/library/832db681-e8e1-41ca-b78c-cd9d265cdb87)(alokátoru), jak je znázorněno v následujícím příkladu myMalloc:  
>   
>  `__declspec(allocator) void* myMalloc(size_t size)`  
  
## <a name="analyze-memory-use-with-the-debugger"></a>Analýza využití paměti v ladicím programu  
  
> [!NOTE]
>  Protože shromažďování paměti, že data může ovlivnit výkon ladění ve smíšeném režimu nebo nativní aplikace, jsou ve výchozím nastavení zakázané snímky paměti. Pokud chcete povolit snímky smíšený režim nebo nativní aplikace, spustíte relaci ladění (Klávesová zkratka: **F5**). Když **diagnostické nástroje** okna se zobrazí, vyberte na kartě využití paměti a klikněte na tlačítko **povolit snímky**.  
>   
>  ![Povolit snímky](../profiling/media/dbgdiag-mem-mixedtoolbar-enablesnapshot.png "DBGDIAG_MEM_MixedToolbar_EnableSnapshot")  
>   
>  Zastavit (Klávesová zkratka: **Shift + F5**) a znovu spusťte ladění.  
  
 Pokaždé, když chcete zaznamenat stav paměti, vyberte **pořídit snímek** na **využití paměti** souhrnný panel nástrojů.  
  
 ![Pořídit snímek](../profiling/media/dbgdiag-mem-mixedtoolbar-takesnapshot.png "DBGDIAG_MEM_MixedToolbar_TakeSnapshot")  
  
> [!TIP]
> - Pokud chcete vytvořit standardní hodnoty pro porovnání paměti, vezměte v úvahu pořízení snímku na začátku vaší relace ladění.  
>   -   Vzhledem k tomu může být náročné k zaznamenání profilu paměti operace, která vás zajímá, když aplikace často přiděluje a zrušení přidělení paměti, nastavit zarážky na začátku a konci operace nebo krokovat operaci najít konkrétní bod, který paměť změněna.  
  
## <a name="viewing-memory-snapshot-details"></a>Zobrazení podrobností snímek paměti  
 Řádky tabulku souhrnu využití paměti obsahuje seznam snímků, které jste provedli během relace ladění.  
  
 Sloupce v řádku závisí na režim ladění zvolte ve vlastnostech projektu: .NET, nativní nebo smíšený (.NET a nativní).  
  
- **Spravovaných objektů**s a **nativní přidělení** sloupce zobrazují počet objektů v rozhraní .NET a nativní paměť při pořízení snímku.  
  
- **Spravovaná velikost haldy** a **nativní velikost haldy** sloupce zobrazují počet bajtů v rozhraní .NET a nativní haldy  
  
- Pokud jste provedli několik snímků, buňky ovládacího prvku souhrnnou tabulku zahrnují změnu hodnoty mezi řádek snímek a předchozí snímek.  
  
   ![Paměť souhrnnou tabulku buňky](../profiling/media/dbgdiag-mem-summarytablecell.png "DBGDIAG_MEM_SummaryTableCell")  
  
  **Chcete-li zobrazit podrobnou sestavu:**  
  
- Chcete-li zobrazit podrobnosti pouze vybraný snímek vyberte aktuální propojení.  
  
- Chcete-li zobrazit podrobnosti o rozdílu mezi aktuálním snímkem a předchozím snímkem, zvolte odkaz změnit.  
  
  Sestavy se zobrazí v samostatném okně.  
  
## <a name="memory-usage-details-reports"></a>Zprávy s podrobnostmi o využití paměti  
  
### <a name="managed-types-reports"></a>Spravované typy sestav  
 Vyberte aktuální propojení **spravovaným objektům** nebo **spravovaná velikost haldy** buňku v tabulce souhrnu využití paměti.  
  
 ![Ladicí program spravovaného typu sestavy &#45; cesty ke kořenu](../profiling/media/dbgdiag-mem-managedtypesreport-pathstoroot.png "DBGDIAG_MEM_ManagedTypesReport_PathsToRoot")  
  
 Horní podokno zobrazuje počet a velikost typů ve snímku, včetně velikosti všech objektů, na které odkazuje typ (**celkové velikosti**).  
  
 **Cesty ke kořenu** stromu v dolním podokně zobrazí objekty, které odkazují na vybraném v horním podokně typu. Paměť pro objekt vyčistí systému uvolňování paměti rozhraní .NET Framework, pouze v případě, že byly vydány poslední typ, který na ni odkazuje.  
  
 **Odkazované typy** Strom zobrazuje odkazy, které jsou uloženy ve vybraném v horním podokně typu.  
  
 ![Spravované eferenced typy zobrazení sestavy](../profiling/media/dbgdiag-mem-managedtypesreport-referencedtypes.png "DBGDIAG_MEM_ManagedTypesReport_ReferencedTypes")  
  
 K zobrazení instance vybraného typu v horním podokně, vyberte ![Instance ikonu](../profiling/media/dbgdiag-mem-instanceicon.png "DBGDIAG_MEM_InstanceIcon") ikonu.  
  
 ![Zobrazení instancí](../profiling/media/dbgdiag-mem-managedtypesreport-instances.png "DBGDIAG_MEM_ManagedTypesReport_Instances")  
  
 **Instance** zobrazení instancí vybraného objektu ve snímku v horním podokně. Cesty ke kořenové certifikáty a odkazované objekty podokně zobrazí objekty, které odkazují na vybranou instanci a typy, které se odkazuje vybraná instance. Když ladicí program se zastaví v místě, kde pořízení snímku, myší nad hodnota buňky pro zobrazení hodnoty objektu v popisu tlačítka.  
  
### <a name="native-type-reports"></a>Nativní typ sestavy  
 Vyberte aktuální propojení **nativní přidělení** nebo **nativní velikost haldy** buňku v tabulce souhrnu využití paměti z **diagnostické nástroje** okna.  
  
 ![Nativní typ zobrazení](../profiling/media/dbgdiag-mem-native-typesview.png "DBGDIAG_MEM_Native_TypesView")  
  
 **Zobrazení typů** zobrazuje počet a velikost typů ve snímku.  
  
-   Zvolte ikonu instance (![ikonu instance ve sloupci Typ objektu](../misc/media/dbg-mma-instancesicon.png "DBG_MMA_InstancesIcon")) z vybraného typu k zobrazení informací o objektech vybraného typu ve snímku.  
  
     **Instance** zobrazení zobrazí každou instanci daného typu. Výběr instance zobrazí, které vedlo k vytvoření instance v zásobníku volání **zásobník volání přidělení** podokně.  
  
     ![Zobrazení instancí](../profiling/media/dbgdiag-mem-native-instances.png "DBGDIAG_MEM_Native_Instances")  
  
-   Zvolte **zobrazení zásobníků** v **režim zobrazení** seznamu zobrazíte zásobník přidělení pro vybraný typ.  
  
     ![Stacks View](../profiling/media/dbgdiag-mem-native-stacksview.png "DBGDIAG_MEM_Native_StacksView")  
  
### <a name="change-diff-reports"></a>Změnit sestavy (rozdíl)  
  
- Zvolte odkaz změnit v buňce souhrnnou tabulku **využití paměti** kartě **diagnostické nástroje** okna.  
  
   ![Zvolte změnu &#40;dif&#41;f sestavy](../profiling/media/dbgdiag-mem-choosediffreport.png "DBGDIAG_MEM_ChooseDiffReport")  
  
- Zvolte snímek v **porovnat** seznam spravované nebo nativní sestavy.  
  
   ![Zvolte snímek ze seznamu porovnat](../profiling/media/dbgdiag-mem-choosecompareto.png "DBGDIAG_MEM_ChooseCompareTo")  
  
  Sestava změn přidává sloupce (označené **(rozdíl)**) základní sestavy, které zobrazují rozdíl mezi hodnotami základní snímek a snímek porovnání. Zde je, jak může vypadat sestavy rozdílu nativní typ zobrazení:  
  
  ![Nativní typy Diff Veiw](../profiling/media/dbgdiag-mem-native-typesviewdiff.png "DBGDIAG_MEM_Native_TypesViewDiff")  
  
## <a name="blogs-and-videos"></a>Blogy a videa  
 [Ladicí program okně diagnostické nástroje v sadě Visual Studio 2015](http://blogs.msdn.com/b/visualstudioalm/archive/2015/01/16/diagnostic-tools-debugger-window-in-visual-studio-2015.aspx)  
  
 [Blog: Nástroj využití paměti při ladění v sadě Visual Studio 2015](http://blogs.msdn.com/b/visualstudioalm/archive/2014/11/13/memory-usage-tool-while-debugging-in-visual-studio-2015.aspx)  
  
 [Visual C++ Blog: Nativní Diagnostika paměti ve verzi Preview VS2015](http://blogs.msdn.com/b/vcblog/archive/2014/11/21/native-memory-diagnostics-in-vs2015-preview.aspx)  
  
 [Visual C++ Blog: Nativní paměť diagnostické nástroje pro Visual Studio 2015 CTP](http://blogs.msdn.com/b/vcblog/archive/2014/06/04/native-memory-diagnostic-tools-for-visual-studio-14-ctp1.aspx)




