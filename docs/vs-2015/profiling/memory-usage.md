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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "74298365"
---
# <a name="memory-usage"></a>Využití paměti
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Najděte nevracení paměti a neefektivní paměť při ladění pomocí nástroje pro diagnostiku **využití paměti** integrovaného ladicího programu. Nástroj využití paměti umožňuje provést jeden nebo více *snímků* spravované a nativní haldy paměti. Můžete shromažďovat snímky pro .NET, nativní nebo smíšený režim (.NET a nativní) aplikace.  
  
- Můžete analyzovat jeden snímek a pochopit relativní dopad typů objektů při použití paměti a vyhledat kód v aplikaci, která používá paměť neefektivně.  
  
- Můžete také porovnat (diff) dva snímky aplikace a vyhledat oblasti v kódu, které způsobí, že se využití paměti zvýší v čase.  
  
  Následující obrázek znázorňuje okno **diagnostické nástroje** v aplikaci Visual Studio 2015 Update 1:  
  
  ![DiagnosticTools&#45;-datum1](../profiling/media/diagnostictools-update1.png "DiagnosticTools-v-datum1")  
  
  I když můžete shromažďovat snímky paměti kdykoli v nástroji **využití paměti** , můžete použít ladicí program sady Visual Studio k řízení toho, jak se vaše aplikace spouští při zkoumání problémů s výkonem. Nastavení zarážek, krokování, přerušit vše a další akce ladicího programu vám umožní zaměřit se na vaše vyšetřování výkonnosti v případě nejdůležitějších cest kódu. Provedení těchto akcí v době, kdy je vaše aplikace spuštěná, může eliminovat hluk kódu, který vás zajímá, a může významně zkrátit dobu, po kterou vám pomůže diagnostikovat problém.  
  
  Můžete také použít nástroj paměti mimo ladicí program. Zobrazit [využití paměti bez ladění](https://msdn.microsoft.com/library/8883bc5f-df86-4f84-aa2b-a21150f499b0).  
  
> [!NOTE]
> **Podpora vlastního přidělování** Profil nativní paměti funguje tak, že shromažďuje data události trasování událostí pro [Windows](https://msdn.microsoft.com/library/windows/desktop/bb968803\(v=vs.85\).aspx) vygenerovaná během běhu.  Alokátory v CRT a Windows SDK byly opatřeny poznámkami na zdrojové úrovni, aby bylo možné zachytit jejich alokační data.  Pokud píšete vlastní přidělování, než jsou jakékoli funkce, které vracejí ukazatel na nově přidělenou paměť haldy, mohou být upraveny pomocí [__declspec](https://msdn.microsoft.com/library/832db681-e8e1-41ca-b78c-cd9d265cdb87)(přidělování), jak je vidět v tomto příkladu pro myMalloc:  
>   
> `__declspec(allocator) void* myMalloc(size_t size)`  
  
## <a name="analyze-memory-use-with-the-debugger"></a>Analýza využití paměti pomocí ladicího programu  
  
> [!NOTE]
> Vzhledem k tomu, že shromažďování dat o paměti může ovlivnit výkon ladění vašich aplikací v nativním nebo kombinovaném režimu, jsou snímky paměti ve výchozím nastavení zakázány. Pokud chcete povolit snímky v nativním režimu nebo v kombinovaných režimech, spusťte ladicí relaci (Klávesová zkratka: **F5**). Jakmile se zobrazí okno **diagnostické nástroje** , zvolte kartu využití paměti a zvolte možnost **Povolit snímky**.  
>   
> ![Povolit snímky](../profiling/media/dbgdiag-mem-mixedtoolbar-enablesnapshot.png "DBGDIAG_MEM_MixedToolbar_EnableSnapshot")  
>   
> Stop (Klávesová zkratka: **SHIFT + F5**) a opětovné spuštění ladění.  
  
 Kdykoli chcete zachytit stav paměti, vyberte možnost **pořídit snímek** na panelu nástrojů souhrn **využití paměti** .  
  
 ![Pořídit snímek](../profiling/media/dbgdiag-mem-mixedtoolbar-takesnapshot.png "DBGDIAG_MEM_MixedToolbar_TakeSnapshot")  
  
> [!TIP]
> - Chcete-li vytvořit směrný plán pro porovnání paměti, zvažte možnost pořízení snímku na začátku relace ladění.  
>   - Vzhledem k tomu, že může být náročné zachytit profil paměti operace, která vás zajímá, když vaše aplikace často přiděluje paměť, nastavovat zarážky na začátku a na konci operace nebo krokovat přes operaci, aby bylo možné najít přesný bod, který se změnil v paměti.  
  
## <a name="viewing-memory-snapshot-details"></a>Zobrazení podrobností o snímku paměti  
 Tabulka souhrnu využití paměti obsahuje seznam snímků, které jste provedli během relace ladění.  
  
 Sloupce řádku závisí na režimu ladění, který zvolíte ve vlastnostech projektu: .NET, Native nebo Mixed (rozhraní .NET i nativní).  
  
- Sloupce **spravovaných objektů**a **nativní alokace** zobrazují počet objektů v rozhraní .NET a nativní paměti při pořízení snímku.  
  
- Sloupce velikost **spravované haldy** a **nativní haldy velikosti haldy** zobrazují počet bajtů v rozhraní .NET a nativních haldách.  
  
- Když jste převzali více snímků, buňky souhrnné tabulky obsahují změnu hodnoty mezi snímkem řádku a předchozím snímkem.  
  
   ![Buňka tabulky souhrnu paměti](../profiling/media/dbgdiag-mem-summarytablecell.png "DBGDIAG_MEM_SummaryTableCell")  
  
  **Zobrazení podrobné sestavy:**  
  
- Chcete-li zobrazit podrobnosti pouze vybraného snímku, vyberte aktuální odkaz.  
  
- Chcete-li zobrazit podrobnosti o rozdílu mezi aktuálním snímkem a předchozím snímkem, klikněte na odkaz změnit.  
  
  Sestava se zobrazí v samostatném okně.  
  
## <a name="memory-usage-details-reports"></a>Sestavy podrobností využití paměti  
  
### <a name="managed-types-reports"></a>Sestavy spravovaných typů  
 V tabulce Souhrn využití paměti vyberte aktuální odkaz na **spravované objekty** nebo buňku **velikosti spravované haldy** .  
  
 ![Sestava spravovaného typu ladicího programu &#45; cesty ke kořenu](../profiling/media/dbgdiag-mem-managedtypesreport-pathstoroot.png "DBGDIAG_MEM_ManagedTypesReport_PathsToRoot")  
  
 V horním podokně se zobrazuje počet a velikost typů ve snímku, včetně velikosti všech objektů, na které se odkazuje typ (**Celková velikost**).  
  
 **Cesta ke kořenovému** stromu v dolním podokně zobrazuje objekty, které odkazují na typ vybraný v horním podokně. Systém uvolňování paměti .NET Framework vyčistí paměť objektu pouze v případě, že byl vydán poslední typ, který na něj odkazuje.  
  
 Stromová struktura **odkazovaného** typu zobrazuje odkazy, které jsou uloženy podle typu vybraného v horním podokně.  
  
 ![Zobrazení sestavy spravovaných typů eferenced](../profiling/media/dbgdiag-mem-managedtypesreport-referencedtypes.png "DBGDIAG_MEM_ManagedTypesReport_ReferencedTypes")  
  
 Chcete-li zobrazit instance vybraného typu v horním podokně, klikněte na ikonu ![ikony instance](../profiling/media/dbgdiag-mem-instanceicon.png "DBGDIAG_MEM_InstanceIcon") .  
  
 ![Zobrazení instancí](../profiling/media/dbgdiag-mem-managedtypesreport-instances.png "DBGDIAG_MEM_ManagedTypesReport_Instances")  
  
 Zobrazení **instance** zobrazuje instance vybraného objektu ve snímku v horním podokně. Podokno cesty k kořenu a odkazované objekty zobrazuje objekty, které odkazují na vybranou instanci a typy, na které odkazuje vybraná instance. Když je ladicí program zastaven v místě, kde byl snímek vytvořen, můžete umístit ukazatel myši nad buňku Value a zobrazit tak hodnoty objektu v popisu tlačítka.  
  
### <a name="native-type-reports"></a>Sestavy nativního typu  
 Vyberte aktuální odkaz na **nativní přidělení** nebo buňku **velikosti nativního haldy** v tabulce souhrn využití paměti okna **diagnostické nástroje** .  
  
 ![Zobrazení nativního typu](../profiling/media/dbgdiag-mem-native-typesview.png "DBGDIAG_MEM_Native_TypesView")  
  
 **Zobrazení typy** zobrazuje počet a velikost typů ve snímku.  
  
- Vyberte ikonu instance (![ikona instance ve sloupci Typ objektu](../misc/media/dbg-mma-instancesicon.png "DBG_MMA_InstancesIcon")) vybraného typu pro zobrazení informací o objektech vybraného typu ve snímku.  
  
     Zobrazení **instance** zobrazuje všechny instance vybraného typu. Výběr instance zobrazí zásobník volání, jehož výsledkem bylo vytvoření instance v podokně **zásobník volání přidělení** .  
  
     ![Zobrazení instancí](../profiling/media/dbgdiag-mem-native-instances.png "DBGDIAG_MEM_Native_Instances")  
  
- Výběrem možnosti **zobrazení zásobníků** v seznamu **režim zobrazení** zobrazíte zásobník přidělení pro vybraný typ.  
  
     ![Zobrazení zásobníků](../profiling/media/dbgdiag-mem-native-stacksview.png "DBGDIAG_MEM_Native_StacksView")  
  
### <a name="change-diff-reports"></a>Změny (rozdílové) sestavy  
  
- Vyberte odkaz změnit v buňce tabulky souhrn na kartě **využití paměti** v okně **diagnostické nástroje** .  
  
   ![Zvolit změnu &#40;DIF&#41;f Report](../profiling/media/dbgdiag-mem-choosediffreport.png "DBGDIAG_MEM_ChooseDiffReport")  
  
- Vyberte snímek v seznamu **porovnat se** správou nebo nativní sestavou.  
  
   ![Výběr snímku ze seznamu porovnat s](../profiling/media/dbgdiag-mem-choosecompareto.png "DBGDIAG_MEM_ChooseCompareTo")  
  
  Sestava změny přidá sloupce (označené jako **(diff)**) do základní sestavy, která zobrazuje rozdíl mezi základní hodnotou snímku a snímkem porovnání. Tady je příklad, jak může vypadat rozdílová sestava zobrazení nativního typu:  
  
  ![Veiw rozdílu nativních typů](../profiling/media/dbgdiag-mem-native-typesviewdiff.png "DBGDIAG_MEM_Native_TypesViewDiff")  
  
## <a name="blogs-and-videos"></a>Blogy a videa  
 [Okno ladicího programu Diagnostické nástroje v aplikaci Visual Studio 2015](https://devblogs.microsoft.com/devops/diagnostic-tools-debugger-window-in-visual-studio-2015/)  
  
 [Blog: nástroj využití paměti při ladění v aplikaci Visual Studio 2015](https://devblogs.microsoft.com/devops/memory-usage-tool-while-debugging-in-visual-studio-2015/)  
  
 [Visual C++ blog: Diagnostika nativní paměti v VS2015 Preview](https://devblogs.microsoft.com/cppblog/native-memory-diagnostics-in-vs2015-preview/)  
  
 [Visual C++ blog: nativní Diagnostické nástroje paměti pro Visual Studio 2015 CTP](https://devblogs.microsoft.com/cppblog/native-memory-diagnostic-tools-for-visual-studio-14-ctp/)
