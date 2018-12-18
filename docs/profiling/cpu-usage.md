---
title: Analýza využití procesoru | Dokumentace Microsoftu
ms.custom: seodec18
ms.date: 11/04/2018
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 7501a20d-04a1-480f-a69c-201524aa709d
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 4b3d4d6a352d2ff1b71796d64c34992af493867a
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/07/2018
ms.locfileid: "53063260"
---
# <a name="analyze-cpu-usage"></a>Analýza využití procesoru 

Dobrým způsobem, jak spustit šetření s problémy s výkonem v aplikaci je pochopit jeho využití procesoru. **Využití procesoru** nástroj výkon ukazuje čas procesoru a procentuální strávené prováděním kódu v jazyce C++, C#/Visual Basic a aplikacích JavaScript. 

**Využití procesoru** nástroj můžete spustit v otevřeném projektu sady Visual Studio na nainstalovanou aplikaci Microsoft Store nebo připojený ke spuštěné aplikace nebo proces. Nástroj můžete spustit na místních nebo vzdálených počítačích nebo na simulátoru nebo emulátoru. Další informace najdete v tématu [spustit s nebo bez ladicího programu nástroje pro profilaci](../profiling/running-profiling-tools-with-or-without-the-debugger.md). 

Můžete spustit **využití procesoru** nástroj s nebo bez ladění. V ladicím programu můžete zapnout a vypnout profilaci procesoru a zobrazit rozpis využití procesoru podle funkce. Můžete zobrazit výsledky pro využití procesoru při spuštění je pozastaveno, například zarážky.  

Následující pokyny ukazují, jak používat **využití procesoru** nástroje bez ladicího programu, pomocí sady Visual Studio **Profiler výkonu**. V příkladech se používá sestavení pro vydání v místním počítači. Sestavení pro vydání poskytují nejlepší zobrazení aplikace skutečný výkon. Analýza využití procesoru s sestavení pro ladění, naleznete v tématu [příručka začátečníka profilací výkonu](../profiling/beginners-guide-to-performance-profiling.md).

Obvykle místní počítač nejlepší replikuje provádění nainstalované aplikace. Pro aplikace Windows Phone shromažďovat data přímo ze zařízení poskytuje co nejvíce zpřesnili data. Chcete-li shromažďovat data ze vzdáleného zařízení, spusťte aplikaci přímo v zařízení, nikoli prostřednictvím připojení ke vzdálené ploše. 

>[!NOTE]
>Windows 7 nebo novější je nutné použít [Profiler výkonu](../profiling/profiling-feature-tour.md).
  
##  <a name="collect-cpu-usage-data"></a>Shromažďovat data o využití procesoru  
  
1. V projektu sady Visual Studio nastavte konfiguraci řešení na **vydání** a vyberte **místního počítače** jako cíl nasazení.  
  
    ![Vyberte verzi a místní počítač](../profiling/media/cpuuse_selectreleaselocalmachine.png "vyberte verzi a místní počítač")  
  
1. Vyberte **ladění** > **Profiler výkonu**.  
  
1. V části **dostupných nástrojů**vyberte **využití procesoru**a pak vyberte **Start**.  
  
    ![Vyberte využití procesoru](../profiling/media/cpuuse_lib_choosecpuusage.png "vyberte využití procesoru")  
  
4. Po spuštění aplikace diagnostické relace spustí a zobrazí data o využití procesoru. Po dokončení shromažďování dat, vyberte **zastavit shromažďování**.  
  
   ![Zastavit shromažďování dat o využití procesoru](../profiling/media/cpu_use_wt_stopcollection.png "využití procesoru zastavit shromažďování dat")  
  
   Nástroj využití CPU analyzuje data a zobrazí sestavu.  
  
   ![Sestava využití procesoru](../profiling/media/cpu_use_wt_report.png "sestava využití procesoru")  
  

## <a name="analyze-the-cpu-usage-report"></a>Analýza sestavy využití procesoru  
  
Diagnostické zprávy je seřazený podle **celkový čas procesoru**, od nejvyšší po nejnižší. Změníte pořadí řazení a řazení sloupců tak, že vyberete záhlaví sloupců. Použít **filtr** rozevírací nabídku a vyberte nebo zrušte výběr vláken k zobrazení a použití **hledání** políčka k vyhledání konkrétního vlákna nebo uzel. 

###  <a name="BKMK_Call_tree_data_columns"></a> Sloupce dat využití procesoru  

|||  
|-|-|  
|**Celkový čas procesoru [jednotka, %]**|![Celkem % dat rovnice](../profiling/media/cpu_use_wt_totalpercentequation.png "CPU_USE_WT_TotalPercentEquation")<br /><br /> Milisekund a % využití CPU ve volání funkce a funkcích volaných funkcí ve vybraném časovém rozsahu. Tím se liší od **využití výkonu procesoru** graf časové osy, která porovnává celkové aktivity procesoru v časový rozsah pro celkový čas procesoru k dispozici.|  
|**Vlastní čas procesoru [jednotka, %]**|![Vlastní % rovnice](../profiling/media/cpu_use_wt_selflpercentequation.png "CPU_USE_WT_SelflPercentEquation")<br /><br /> Milisekund a procento využití procesoru používá volání funkce ve vybraném časovém rozsahu, s výjimkou funkce volané funkce.|  
|**Modul**|Název modulu, který obsahuje funkci.   
  
###  <a name="BKMK_The_CPU_Usage_call_tree"></a> Využití procesoru strom volání 

Zobrazení stromu volání, vyberte nadřazený uzel v sestavě. **Využití procesoru** stránka se otevře **volající/volaný** zobrazení. V **aktuální zobrazení** rozevíracího seznamu vyberte **stromu volání**.  
  
####  <a name="BKMK_Call_tree_structure"></a> Struktura stromu volání  

 ![Volání stromovou strukturu](../profiling/media/cpu_use_wt_getmaxnumbercalltree_annotated.png "volání stromové struktury")  
  
|||  
|-|-|  
|![1. krok](../profiling/media/procguid_1.png "ProcGuid_1")|Uzel nejvyšší úrovně ve stromu volání procesoru je pseudo uzel.|  
|![2. krok](../profiling/media/procguid_2.png "ProcGuid_2")|Ve většině aplikací když **zobrazit externí kód** možnost je zakázaná, je uzel druhé úrovně **[externí kód]** uzlu. Uzel obsahuje kód systému a rozhraní, který se spustí a zastaví aplikace, nakreslí uživatelského rozhraní, ovládací prvky, plánování vláken a poskytuje další nižší úrovně služby do aplikace.|  
|![3. krok](../profiling/media/procguid_3.png "ProcGuid_3")|Uzlu druhé úrovně jsou podřízeny metody uživatelského kódu a asynchronní rutiny, které volá nebo vytváří systémový kód a kód architektury druhé úrovně.|  
|![4. krok](../profiling/media/procguid_4.png "ProcGuid_4")|Podřízené uzly metody mají data pouze pro volání metody nadřazené. Pokud zakážete **Zobrazit externí kód**, mohou metody aplikace obsahovat také uzel **[Externí kód]**.|  
  
####  <a name="BKMK_External_Code"></a> Externí kód  

 Systém a o funkcích rozhraní, které jsou spouštěny ve vašem kódu, se nazývají *externí kód*. Externí kód funkce spuštění a zastavení aplikace, vykreslení uživatelského rozhraní, řízení práce s vlákny a poskytují další nižší úrovně služby do aplikace. Ve většině případů nepotřebujete externí kód, takže využití procesoru volání stromu shromáždí externí funkce metody uživatele do jednoho **[externí kód]** uzlu.  
  
 Chcete-li zobrazit cesty volání externí kód, na stránce hlavní diagnostickou sestavu, vyberte **zobrazit externí kód** z **filtr** rozevírací seznam a pak vyberte **použít**. **Stromu volání** zobrazení **využití procesoru** stránce poté rozbalí volání externí kód.  
  
 ![Zobrazit externí kód](../profiling/media/cpu_use_wt_filterview.png "zobrazit externí kód")  
  
 Mnoho řetězců volání externí kód jsou vnořeny hluboko, takže šířku řetězce může být delší než šířka zobrazení **název funkce** sloupce. Názvy funkcí se potom zobrazí jako **...** .  
  
 ![Vnořené externí kód ve stromu volání](../profiling/media/cpu_use_wt_showexternalcodetoowide.png "vnořené externí kód ve stromu volání")  
  
 Chcete-li najít název funkce, které hledáte, použijte vyhledávací pole. Najeďte myší vybraný řádek nebo zobrazení dat pomocí vodorovný posuvník.  
  
 ![Hledat vnořené externí kód](../profiling/media/cpu_use_wt_showexternalcodetoowide_found.png "vyhledávání pro vnořené externí kód")  
  
###  <a name="BKMK_Asynchronous_functions_in_the_CPU_Usage_call_tree"></a> Asynchronní funkce ve stromu volání využití procesoru  

 Když kompilátor narazí na asynchronní metodu, vytvoří třídu skryté k řízení provádění metody. Třída je koncepčně stavového stroje. Třída má vygenerovaný kompilátorem funkce, které volají asynchronní metody původní a zpětná volání, Plánovač a iterátory, které jsou potřebné k jejich spuštění. Když nadřazené metody volá původní metody, kompilátor odebere metodu z kontextu spuštění nadřazeného elementu a spustí třídy skryté metody v kontextu systému a rozhraní framework kód, který určuje provádění aplikace. Asynchronní metody jsou často, ale ne vždy spouštěny na jeden nebo více různých vláken. Tento kód se zobrazí v **využití procesoru** strom volání jako podřízené objekty **[externí kód]** uzel bezprostředně pod nejvyšší uzel stromu.  

V následujícím příkladu první dva uzly v rámci **[externí kód]** způsoby kompilátorem generované třídy stav počítače. Třetí uzlu je volání na původní metodu. 
  
![Asynchronní uzel](media/cpu_use_wt_getmaxnumberasync_selected.png "asynchronní uzlu")  

Rozbalte generované metody, chcete-li zobrazit, co se děje:

![Asynchronní uzel rozšířené](media/cpu_use_wt_getmaxnumberasync_expandedcalltree.png "rozšířené asynchronní uzlu")  

- `MainPage::GetMaxNumberAsyncButton_Click` právě spravuje seznam hodnot úloh, vypočítá maximální počet výsledků a zobrazí výstup.
  
- `MainPage+<GetMaxNumberAsyncButton_Click>d__3::MoveNext` ukazuje aktivit potřebných k naplánování a spuštění 48 úkoly, které obalují volání `GetNumberAsync`.
  
- `MainPage::<GetNumberAsync>b__b` obsahuje informace o aktivitě úkoly, které volají `GetNumber`.
