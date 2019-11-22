---
title: Využití paměti | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: bbb58d6c-3362-4ca3-8e87-64b2d4415bf6
caps.latest.revision: 17
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 0feabad8dfa3b086c9ed5a1a58e231719774f9cc
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2019
ms.locfileid: "74298365"
---
# <a name="memory-usage"></a>Využití paměti
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Najděte nevracení paměti a neefektivní paměť při ladění pomocí nástroje pro diagnostiku **využití paměti** integrovaného ladicího programu. Umožňuje nástroj využití paměti, můžete provést jeden nebo více *snímky* spravovaný a nativní paměti haldy. Můžete shromažďovat snímky technologie .NET, nativní nebo smíšený režim (.NET a nativní) aplikace.  
  
- Jeden snímek pochopit jeho relativní dopad typů objektů na využití paměti a vyhledání kódu vaší aplikace, která používá paměť neefektivně, můžete analyzovat.  
  
- Můžete také porovnat (rozdíl) dvěma snímky vyhledejte oblasti v kódu aplikace, které způsobují využití paměti časem zvětšuje.  
  
  Následující obrázek znázorňuje okno **diagnostické nástroje** v aplikaci Visual Studio 2015 Update 1:  
  
  ![DiagnosticTools&#45;-datum1](../profiling/media/diagnostictools-update1.png "DiagnosticTools-v-datum1")  
  
  I když můžete shromažďovat snímky paměti v kdykoli **využití paměti** nástroj, ladicího programu sady Visual Studio můžete použít k řízení, jak vaše aplikace provádí při zkoumání problémů s výkonem. Nastavení zarážek, krokování, příkaz Pozastavit vše a další ladicí program akce pomáhá soustředit vaše vyšetřování výkonu cesty kódu, které jsou nejrelevantnější. Provedení těchto akcí v době, kdy je vaše aplikace spuštěná, může eliminovat hluk kódu, který vás zajímá, a může významně zkrátit dobu, po kterou vám pomůže diagnostikovat problém.  
  
  Můžete také použít nástroj paměti mimo ladicí program. Zobrazit [využití paměti bez ladění](https://msdn.microsoft.com/library/8883bc5f-df86-4f84-aa2b-a21150f499b0).  
  
> [!NOTE]
> **Podpora vlastního alokátoru** profiler nativní paměť funguje tak, že shromažďování přidělení [trasování událostí pro Windows](https://msdn.microsoft.com/library/windows/desktop/bb968803\(v=vs.85\).aspx) data událostí, protože ho vygeneroval za běhu.  Na úrovni zdroje byly anotované alokátorů CRT a sadu Windows SDK tak, aby jejich přidělení dat se dají zachytit.  Pokud píšete vlastní přidělování, než jsou jakékoli funkce, které vracejí ukazatel na nově přidělenou paměť haldy, mohou být upraveny pomocí [__declspec](https://msdn.microsoft.com/library/832db681-e8e1-41ca-b78c-cd9d265cdb87)(přidělování), jak je vidět v tomto příkladu pro myMalloc:  
>   
> `__declspec(allocator) void* myMalloc(size_t size)`  
  
## <a name="analyze-memory-use-with-the-debugger"></a>Analýza využití paměti pomocí ladicího programu  
  
> [!NOTE]
> Protože shromažďování paměti, že data může ovlivnit výkon ladění ve smíšeném režimu nebo nativní aplikace, jsou ve výchozím nastavení zakázané snímky paměti. Pokud chcete povolit snímky v nativním režimu nebo v kombinovaných režimech, spusťte ladicí relaci (Klávesová zkratka: **F5**). Jakmile se zobrazí okno **diagnostické nástroje** , zvolte kartu využití paměti a zvolte možnost **Povolit snímky**.  
>   
> ![Povolit snímky](../profiling/media/dbgdiag-mem-mixedtoolbar-enablesnapshot.png "DBGDIAG_MEM_MixedToolbar_EnableSnapshot")  
>   
> Stop (Klávesová zkratka: **SHIFT + F5**) a opětovné spuštění ladění.  
  
 Kdykoli chcete zachytit stav paměti, vyberte možnost **pořídit snímek** na panelu nástrojů souhrn **využití paměti** .  
  
 ![Pořídit snímek](../profiling/media/dbgdiag-mem-mixedtoolbar-takesnapshot.png "DBGDIAG_MEM_MixedToolbar_TakeSnapshot")  
  
> [!TIP]
> - Pokud chcete vytvořit standardní hodnoty pro porovnání paměti, vezměte v úvahu pořízení snímku na začátku vaší relace ladění.  
>   - Vzhledem k tomu, že může být náročné zachytit profil paměti operace, která vás zajímá, když vaše aplikace často přiděluje paměť, nastavovat zarážky na začátku a na konci operace nebo krokovat přes operaci, aby bylo možné najít přesný bod, který paměť se změnila.  
  
## <a name="viewing-memory-snapshot-details"></a>Zobrazení podrobností o snímku paměti  
 Tabulka souhrnu využití paměti obsahuje seznam snímků, které jste provedli během relace ladění.  
  
 Sloupce řádku závisí na režimu ladění, který zvolíte ve vlastnostech projektu: .NET, Native nebo Mixed (rozhraní .NET i nativní).  
  
- Sloupce **spravovaných objektů**a **nativní alokace** zobrazují počet objektů v rozhraní .NET a nativní paměti při pořízení snímku.  
  
- Sloupce velikost **spravované haldy** a **nativní haldy velikosti haldy** zobrazují počet bajtů v rozhraní .NET a nativních haldách.  
  
- Pokud jste provedli několik snímků, buňky ovládacího prvku souhrnnou tabulku zahrnují změnu hodnoty mezi řádek snímek a předchozí snímek.  
  
   ![Buňka tabulky souhrnu paměti](../profiling/media/dbgdiag-mem-summarytablecell.png "DBGDIAG_MEM_SummaryTableCell")  
  
  **Zobrazení podrobné sestavy:**  
  
- Chcete-li zobrazit podrobnosti pouze vybraného snímku, vyberte aktuální odkaz.  
  
- Chcete-li zobrazit podrobnosti o rozdílu mezi aktuálním snímkem a předchozím snímkem, klikněte na odkaz změnit.  
  
  Sestavy se zobrazí v samostatném okně.  
  
## <a name="memory-usage-details-reports"></a>Sestavy podrobností využití paměti  
  
### <a name="managed-types-reports"></a>Spravované typy sestav  
 V tabulce Souhrn využití paměti vyberte aktuální odkaz na **spravované objekty** nebo buňku **velikosti spravované haldy** .  
  
 ![Správa cest sestav &#45; spravovaného typu ladicího programu do kořenového adresáře](../profiling/media/dbgdiag-mem-managedtypesreport-pathstoroot.png "DBGDIAG_MEM_ManagedTypesReport_PathsToRoot")  
  
 Horní podokno zobrazuje počet a velikost typů ve snímku, včetně velikosti všech objektů, na které odkazuje typ (**celkové velikosti**).  
  
 **Cesty ke kořenu** stromu v dolním podokně zobrazí objekty, které odkazují na vybraném v horním podokně typu. Paměť pro objekt vyčistí systému uvolňování paměti rozhraní .NET Framework, pouze v případě, že byly vydány poslední typ, který na ni odkazuje.  
  
 **Odkazované typy** Strom zobrazuje odkazy, které jsou uloženy ve vybraném v horním podokně typu.  
  
 ![Zobrazení sestavy spravovaných typů eferenced](../profiling/media/dbgdiag-mem-managedtypesreport-referencedtypes.png "DBGDIAG_MEM_ManagedTypesReport_ReferencedTypes")  
  
 Chcete-li zobrazit instance vybraného typu v horním podokně, klikněte na ikonu ![ikony instance](../profiling/media/dbgdiag-mem-instanceicon.png "DBGDIAG_MEM_InstanceIcon") .  
  
 ![Zobrazení instancí](../profiling/media/dbgdiag-mem-managedtypesreport-instances.png "DBGDIAG_MEM_ManagedTypesReport_Instances")  
  
 **Instance** zobrazení instancí vybraného objektu ve snímku v horním podokně. Podokno cesty k kořenu a odkazované objekty zobrazuje objekty, které odkazují na vybranou instanci a typy, na které odkazuje vybraná instance. Když je ladicí program zastaven v místě, kde byl snímek vytvořen, můžete umístit ukazatel myši nad buňku Value a zobrazit tak hodnoty objektu v popisu tlačítka.  
  
### <a name="native-type-reports"></a>Nativní typ sestavy  
 Vyberte aktuální odkaz na **nativní přidělení** nebo buňku **velikosti nativního haldy** v tabulce souhrn využití paměti okna **diagnostické nástroje** .  
  
 ![Zobrazení nativního typu](../profiling/media/dbgdiag-mem-native-typesview.png "DBGDIAG_MEM_Native_TypesView")  
  
 **Zobrazení typů** zobrazuje počet a velikost typů ve snímku.  
  
- Vyberte ikonu instance (![ikona instance ve sloupci Typ objektu](../misc/media/dbg-mma-instancesicon.png "DBG_MMA_InstancesIcon")) vybraného typu pro zobrazení informací o objektech vybraného typu ve snímku.  
  
     **Instance** zobrazení zobrazí každou instanci daného typu. Výběr instance zobrazí, které vedlo k vytvoření instance v zásobníku volání **zásobník volání přidělení** podokně.  
  
     ![Zobrazení instancí](../profiling/media/dbgdiag-mem-native-instances.png "DBGDIAG_MEM_Native_Instances")  
  
- Zvolte **zobrazení zásobníků** v **režim zobrazení** seznamu zobrazíte zásobník přidělení pro vybraný typ.  
  
     ![Zobrazení zásobníků](../profiling/media/dbgdiag-mem-native-stacksview.png "DBGDIAG_MEM_Native_StacksView")  
  
### <a name="change-diff-reports"></a>Změnit sestavy (rozdíl)  
  
- Zvolte odkaz změnit v buňce souhrnnou tabulku **využití paměti** kartě **diagnostické nástroje** okna.  
  
   ![Zvolit změnu &#40;sestavy DIF&#41;f](../profiling/media/dbgdiag-mem-choosediffreport.png "DBGDIAG_MEM_ChooseDiffReport")  
  
- Zvolte snímek v **porovnat** seznam spravované nebo nativní sestavy.  
  
   ![Výběr snímku ze seznamu porovnat s](../profiling/media/dbgdiag-mem-choosecompareto.png "DBGDIAG_MEM_ChooseCompareTo")  
  
  Sestava změn přidává sloupce (označené **(rozdíl)** ) základní sestavy, které zobrazují rozdíl mezi hodnotami základní snímek a snímek porovnání. Tady je příklad, jak může vypadat rozdílová sestava zobrazení nativního typu:  
  
  ![Veiw rozdílu nativních typů](../profiling/media/dbgdiag-mem-native-typesviewdiff.png "DBGDIAG_MEM_Native_TypesViewDiff")  
  
## <a name="blogs-and-videos"></a>Blogy a videa  
 [Okno ladicího programu Diagnostické nástroje v aplikaci Visual Studio 2015](https://devblogs.microsoft.com/devops/diagnostic-tools-debugger-window-in-visual-studio-2015/)  
  
 [Blog: nástroj využití paměti při ladění v aplikaci Visual Studio 2015](https://devblogs.microsoft.com/devops/memory-usage-tool-while-debugging-in-visual-studio-2015/)  
  
 [Blog C++ Visual: Diagnostika nativní paměti v VS2015 Preview](https://devblogs.microsoft.com/cppblog/native-memory-diagnostics-in-vs2015-preview/)  
  
 [Blog C++ vizuálu: nativní diagnostické nástroje paměti pro Visual Studio 2015 CTP](https://devblogs.microsoft.com/cppblog/native-memory-diagnostic-tools-for-visual-studio-14-ctp/)
