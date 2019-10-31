---
title: Analýza využití procesoru v univerzální aplikaci pro Windows | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
ms.assetid: c122b08e-e3bf-43e6-bd6c-e776e178fd9a
caps.latest.revision: 21
author: MikeJo5000
ms.author: mikejo
manager: jillfra
robots: noindex,nofollow
ms.openlocfilehash: 8d296c8803127cdbc2e6c72f86dcfba968e2b940
ms.sourcegitcommit: bdccab4c2dbd50ea8adaaf88c69c9ca32db88099
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73144784"
---
# <a name="analyze-cpu-usage-in-a-windows-universal-app"></a>Analýza využití procesoru v univerzální aplikaci pro Windows
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Platí pro Windows a Windows Phone] (.. /Image/windows_and_phone_content.png "windows_and_phone_content")  
  
 Pokud potřebujete prozkoumat problémy s výkonem ve vaší aplikaci, je dobrým místem, kde začít, je porozumění tomu, jak využívá procesor. Nástroj **využití CPU** vám ukáže, kde CPU stráví čas vykonávání kódu. Pokud se chcete zaměřit na konkrétní scénáře, můžete využití CPU spustit pomocí nástroje [rychlost odezvy v uživatelském rozhraní XAML](https://msdn.microsoft.com/library/4ff84cd1-4e63-4fda-b34f-3ef862a6e480) , nástroje [využití procesoru](../profiling/cpu-usage.md) nebo obou nástrojů v rámci jedné diagnostické relace.  
  
> [!NOTE]
> Nástroj **využití CPU** se nedá použít u Windows Phone aplikací Silverlight 8,1.  
  
 Tento návod vás provede shromažďováním a analýzou využití CPU pro jednoduchou aplikaci Windows Universal XAML.  
  
## <a name="BKMK_Create_the_CpuUseDemo_project"></a>Vytvoření projektu CpuUseDemo  
 **CpuUseDemo** je aplikace, která byla vytvořena za účelem demonstrující, jak shromažďovat a analyzovat data o využití procesoru. Tlačítka vygenerují číslo voláním metody, která vybere maximální hodnotu z více volání funkce. Volaná funkce vytvoří velmi velký počet náhodných hodnot a potom vrátí poslední. Data se zobrazí v textovém poli.  
  
1. Vytvořte nový C# projekt univerzální aplikace pro Windows s názvem **CpuUseDemo** pomocí šablony **BlankApp** .  
  
     ![Vytvoření CpuUseDemoProject](../profiling/media/cpu-use-newproject.png "CPU_USE_NewProject")  
  
2. Nahraďte MainPage. XAML [tímto kódem](#BKMK_MainPage_xaml).  
  
3. Nahraďte MainPage.xaml.cs [tímto kódem](#BKMK_MainPage_xaml_cs).  
  
4. Sestavte aplikaci a vyzkoušejte si ji. Aplikace je dostatečně jednoduchá, aby ukázala několik běžných případů analýzy dat využití procesoru.  
  
## <a name="BKMK_Collect_CPU_usage_data"></a>Shromažďování dat o využití procesoru  
 ![Spustit sestavení pro vydání aplikace v simulátoru](../profiling/media/cpu-use-wt-setsimulatorandretail.png "CPU_USE_WT_SetSimulatorAndRetail")  
  
1. V sadě Visual Studio nastavte cíl nasazení na **simulátor** a konfiguraci řešení na hodnotu **vydaná**.  
  
   - Spuštění aplikace v simulátoru umožňuje snadno přepínat mezi aplikací a IDE sady Visual Studio.  
  
   - Spuštění této aplikace v režimu **vydání** nabízí lepší pohled na skutečný výkon vaší aplikace.  
  
2. V nabídce **ladění** vyberte možnost **Profiler výkonnosti...** .  
  
3. V centru pro výkon a diagnostiku zvolte **využití CPU** a pak zvolte **Spustit**.  
  
    ![Spustit diagnostickou relaci CpuUsage](../profiling/media/cpu-use-wt-perfdiaghub.png "CPU_USE_WT_PerfDiagHub")  
  
4. Po spuštění aplikace klikněte na **získat maximální počet**. Po zobrazení výstupu počkat o sekundu a pak zvolte **získat Max Number Async**. Čekání mezi kliknutím na tlačítko usnadňuje izolaci rutin kliknutí na tlačítko v diagnostické sestavě.  
  
5. Po zobrazení druhé výstupní čáry vyberte možnost **Zastavit shromažďování** v centru výkonu a diagnostiky.  
  
   ![Zastavit shromažďování dat CpuUsage](../profiling/media/cpu-use-wt-stopcollection.png "CPU_USE_WT_StopCollection")  
  
   Nástroj využití CPU analyzuje data a zobrazí sestavu.  
  
   ![Sestava CpuUsage](../profiling/media/cpu-use-wt-report.png "CPU_USE_WT_Report")  
  
## <a name="BKMK_Analyze_the_CPU_Usage_report"></a>Analýza sestavy využití CPU  
  
### <a name="BKMK_CPU_utilization_timeline_graph"></a>Graf časové osy využití procesoru  
 ![Graf &#40;časové&#41; osy CpuUtilization%](../profiling/media/cpu-use-wt-timelinegraph.png "CPU_USE_WT_TimelineGraph")  
  
 Graf využití procesoru zobrazuje aktivitu CPU aplikace jako procento veškerého času procesoru ze všech jader procesoru v zařízení. Data této sestavy byla shromážděna na počítači se dvěma jádry. Dvě velké špičky reprezentují aktivitu CPU dvou kliknutí na tlačítko. `GetMaxNumberButton_Click` provádí synchronně na jednom jádru, takže má smysl, že výška grafu této metody nikdy nepřekračuje 50%. `GetMaxNumberAsycButton_Click` běží asynchronně napříč jádry, takže se tak znovu vyhledá, že se jeho špička blíží k využití všech prostředků procesoru v obou jádrech.  
  
#### <a name="BKMK_Select_timeline_segments_to_view_details"></a>Vyberte segmenty časové osy k zobrazení podrobností.  
 Pomocí pruhů pro výběr na časové ose **diagnostické relace** se zaměřte na GetMaxNumberButton_Click data:  
  
 ![GetMaxNumberButton&#95;klikněte na vybrat.](../profiling/media/cpu-use-wt-getmaxnumberreport.png "CPU_USE_WT_GetMaxNumberReport")  
  
 Časová osa **relace diagnostiky** nyní zobrazuje čas strávený vybraným segmentem (bit více než 2 sekundy v této sestavě) a filtruje strom volání s těmito metodami, které byly spuštěny ve výběru.  
  
 Nyní vyberte segment `GetMaxNumberAsyncButton_Click`.  
  
 ![GetMaxNumberAsyncButton&#95;kliknout na výběr sestavy](../profiling/media/cpu-use-wt-getmaxnumberasync-selected.png "CPU_USE_WT_GetMaxNumberAsync_Selected")  
  
 Tato metoda se dokončí o druhý rychlejší než `GetMaxNumberButton_Click`, ale význam položek stromu volání je méně zřejmý.  
  
### <a name="BKMK_The_CPU_Usage_call_tree"></a>Strom volání využití CPU  
 Chcete-li začít pochopit informace o stromu volání, vyberte segment `GetMaxNumberButton_Click` a podívejte se na podrobnosti o stromu volání.  
  
#### <a name="BKMK_Call_tree_structure"></a>Stromová struktura volání  
 ![GetMaxNumberButton&#95;kliknout na strom volání](../profiling/media/cpu-use-wt-getmaxnumbercalltree-annotated.png "CPU_USE_WT_GetMaxNumberCallTree_annotated")  
  
|||  
|-|-|  
|![Krok 1](../profiling/media/procguid-1.png "ProcGuid_1")|Nejvyšší uzel ve stromech volání Využití procesoru je fiktivní.|  
|![Krok 2](../profiling/media/procguid-2.png "ProcGuid_2")|Ve většině aplikací, ve kterých zakážete možnost **Zobrazit externí kód**, je v druhé úrovni uzel **[Externí kód]** , který obsahuje systémový kód a kód architektury, který spouští a zastavuje aplikaci, vykresluje uživatelské rozhraní, řídí plánování podprocesů a na nejnižší úrovni zajišťuje pro aplikaci další služby.|  
|![Krok 3](../profiling/media/procguid-3.png "ProcGuid_3")|Uzlu druhé úrovně jsou podřízeny metody uživatelského kódu a asynchronní rutiny, které volá nebo vytváří systémový kód a kód architektury druhé úrovně.|  
|![Krok 4](../profiling/media/procguid-4.png "ProcGuid_4")|Podřízené uzly metody obsahují jenom data pro volání nadřízené metody. Pokud zakážete **Zobrazit externí kód**, mohou metody aplikace obsahovat také uzel **[Externí kód]** .|  
  
#### <a name="BKMK_External_Code"></a>Externí kód  
 Externí kód obsahuje funkce v komponentách systému a rozhraní, které jsou spouštěny kódem, který píšete. Externí kód obsahuje funkce, které spouštějí a zastavují aplikaci, nakreslí uživatelské rozhraní, řídí vlákna a poskytují do aplikace další služby nižší úrovně. Ve většině případů nebudete mít zájem o externí kód, takže strom volání využití CPU shromáždí externí funkce uživatelské metody do jednoho uzlu **[externí kód]** .  
  
 Chcete-li zobrazit cesty volání externího kódu, zvolte možnost **Zobrazit externí kód** ze seznamu **zobrazení filtru** a pak zvolte možnost **použít**.  
  
 ![Zvolte možnost zobrazení filtru a pak zobrazit externí kód.](../profiling/media/cpu-use-wt-filterview.png "CPU_USE_WT_FilterView")  
  
 Myslete na to, že řetězy volání externího kódu je většinou hluboko vnořené, takže šířka sloupce Název funkce může na většině počítačových monitorů – s výjimkou těch největších – přesáhnout šířku zobrazení. Pokud k tomu dojde, názvy funkcí se zobrazí jako **[...]** :  
  
 ![Vnořený externí kód ve stromu volání](../profiling/media/cpu-use-wt-showexternalcodetoowide.png "CPU_USE_WT_ShowExternalCodeTooWide")  
  
 Pomocí vyhledávacího pole vyhledejte uzel, který hledáte, a pak pomocí vodorovného posuvníku přepněte data do zobrazení:  
  
 ![Hledání vnořeného externího kódu](../profiling/media/cpu-use-wt-showexternalcodetoowide-found.png "CPU_USE_WT_ShowExternalCodeTooWide_Found")  
  
### <a name="BKMK_Call_tree_data_columns"></a>Sloupce dat stromu volání  
  
|||  
|-|-|  
|**Celkový čas procesoru (%)**|![Total% data Equation – rovnice](../profiling/media/cpu-use-wt-totalpercentequation.png "CPU_USE_WT_TotalPercentEquation")<br /><br /> Procentuální podíl aktivity procesoru aplikace ve vybraném časovém rozsahu, který byl použit voláním funkce a funkcemi, které funkce volá. Všimněte si, že se liší od grafu časové osy **využití procesoru** , který porovnává celkovou aktivitu aplikace v časovém rozsahu s celkovou dostupnou kapacitou procesoru.|  
|**Samotný procesor (%)**|![% Rovnice sebe](../profiling/media/cpu-use-wt-selflpercentequation.png "CPU_USE_WT_SelflPercentEquation")<br /><br /> Procentuální podíl aktivity procesoru aplikace ve vybraném časovém rozsahu, který byl použit voláním funkce, s výjimkou aktivity funkcí volaných funkcí.|  
|**Celkový čas procesoru (MS)**|Počet milisekund strávených voláním funkce ve vybraném časovém rozsahu a funkcemi, které byly volány funkcí.|  
|**Samotný procesor (MS)**|Počet milisekund strávených voláním funkce ve vybraném časovém rozsahu a funkcemi, které byly volány funkcí.|  
|**Modul**|Název modulu obsahujícího funkci nebo počet modulů, které obsahují funkce v uzlu [externí kód].|  
  
### <a name="BKMK_Asynchronous_functions_in_the_CPU_Usage_call_tree"></a>Asynchronní funkce ve stromu volání využití CPU  
 Když kompilátor narazí na asynchronní metodu, vytvoří skrytou třídu pro řízení provádění metody. V koncepční úrovni je třída Stavový počítač, který obsahuje seznam funkcí generovaných kompilátorem, které volají asynchronní operace původní metody a zpětná volání, Scheduler a iterátory, které jsou pro ně požadovány. Pokud je původní metoda volána nadřazenou metodou, modul runtime odstraní metodu z kontextu spuštění nadřazeného objektu a spustí metody skryté třídy v kontextu systému a kódu rozhraní, který řídí provádění aplikace. Asynchronní metody jsou často, ale ne vždy, spouštěny v jednom nebo více různých vláknech. Tento kód je zobrazen ve stromu volání využití CPU jako podřízené objekty v uzlu **[External Code]** bezprostředně pod horním uzlem stromu.  
  
 Pokud to chcete vidět v našem příkladu, znovu vyberte segment `GetMaxNumberAsyncButton_Click` na časové ose.  
  
 ![GetMaxNumberAsyncButton&#95;kliknout na výběr sestavy](../profiling/media/cpu-use-wt-getmaxnumberasync-selected.png "CPU_USE_WT_GetMaxNumberAsync_Selected")  
  
 První dva uzly v **[External Code]** jsou metody generované kompilátorem třídy stavového stroje. Třetí je volání původní metody. Rozbalením vygenerovaných metod se dozvíte, co se chystá.  
  
 ![Rozbalený&#95;GetMaxNumberAsyncButton klikněte na strom volání.](../profiling/media/cpu-use-wt-getmaxnumberasync-expandedcalltree.png "CPU_USE_WT_GetMaxNumberAsync_ExpandedCallTree")  
  
- `MainPage::GetMaxNumberAsyncButton_Click` je velmi málo; spravuje seznam hodnot úkolů, vypočítá maximum výsledků a zobrazí výstup.  
  
- `MainPage+<GetMaxNumberAsyncButton_Click>d__3::MoveNext` zobrazuje aktivitu nutnou k naplánování a spuštění úloh 48, které zabalí volání do `GetNumberAsync`.  
  
- `MainPage::<GetNumberAsync>b__b` zobrazuje aktivitu úloh, které volají `GetNumber`.  
  
## <a name="BKMK_Next_steps"></a>Další kroky  
 Aplikace CpuUseDemo není nejvíc nejnáročnějších aplikací, ale můžete ji využít k experimentování s asynchronními operacemi a dalšími nástroji v centru pro výkon a diagnostiku.  
  
- Všimněte si, že `MainPage::<GetNumberAsync>b__b` stráví více času v [externím kódu], než provádí metodu GetNumber. Největší část tohoto času je režie asynchronních operací. Zkuste zvýšit počet úloh (nastavených v `NUM_TASKS` konstanta MainPage.xaml.cs) a snížit počet iterací v `GetNumber` (změňte hodnotu `MIN_ITERATIONS`). Spusťte scénář shromažďování a porovnejte aktivitu CPU `MainPage::<GetNumberAsync>b__b`s v původní relaci diagnostiky využití procesoru. Zkuste omezit úlohy a zvýšit počet iterací.  
  
- Uživatelé často nezáleží na skutečném výkonu vaší aplikace; postará se o vnímaný výkon a odezvu aplikace. Nástroj pro odezvu uživatelského rozhraní XAML zobrazuje podrobnosti o aktivitě na vlákně uživatelského rozhraní, které se projeví v důsledku pozorovaného odezvy.  
  
     Vytvořte novou relaci v centru diagnostiky a výkonu a přidejte Nástroj pro použití nástroje XAML UI a nástroj využití CPU. Spusťte scénář shromažďování. Pokud jste to ještě neudělali, zpráva pravděpodobně neoznamuje cokoli, co jste ještě neoznačili, ale rozdíly v grafu časové osy **využití vlákna uživatelského rozhraní** pro tyto dvě metody jsou působivý. V komplexních reálných aplikacích může být kombinace nástrojů velmi užitečná.  
  
## <a name="BKMK_MainPage_xaml"></a>MainPage. XAML  
  
```csharp  
<Page  
    x:Class="CpuUseDemo.MainPage"  
    xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"  
    xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"  
    xmlns:local="using:CpuUseDemo"  
    xmlns:d="http://schemas.microsoft.com/expression/blend/2008"  
    xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"  
    mc:Ignorable="d">  
  
    <Page.Resources>  
        <Style TargetType="TextBox">  
            <Setter Property="FontFamily"  Value="Lucida Console" />  
        </Style>  
    </Page.Resources>  
    <Grid Background="{ThemeResource ApplicationPageBackgroundThemeBrush}">  
        <Grid.RowDefinitions>  
            <RowDefinition Height="Auto" />  
            <RowDefinition Height="*" />  
        </Grid.RowDefinitions>  
        <StackPanel Grid.Row="0" Orientation="Horizontal"  Margin="0,40,0,0">  
            <Button Name="GetMaxNumberButton" Click="GetMaxNumberButton_Click"  Content="Get Max Number" />  
            <Button Name="GetMaxNumberAsyncButton" Click="GetMaxNumberAsyncButton_Click"  Content="Get Max Number Async" />  
        </StackPanel>  
        <StackPanel Grid.Row="1">  
            <TextBox Name="TextBox1" AcceptsReturn="True" />  
        </StackPanel>  
    </Grid>  
  
</Page>  
  
```  
  
## <a name="BKMK_MainPage_xaml_cs"></a>MainPage.xaml.cs  
  
```csharp  
using System;  
using System.Collections.Generic;  
using System.IO;  
using System.Linq;  
using System.Runtime.InteropServices.WindowsRuntime;  
using Windows.Foundation;  
using Windows.Foundation.Collections;  
using Windows.UI.Xaml;  
using Windows.UI.Xaml.Controls;  
using Windows.UI.Xaml.Controls.Primitives;  
using Windows.UI.Xaml.Data;  
using Windows.UI.Xaml.Input;  
using Windows.UI.Xaml.Media;  
using Windows.UI.Xaml.Navigation;  
using Windows.Foundation.Diagnostics;  
using System.Threading;  
using System.Threading.Tasks;  
using System.Collections.Concurrent;  
  
// The Blank Page item template is documented at http://go.microsoft.com/fwlink/?LinkId=234238  
  
namespace CpuUseDemo  
{  
    /// <summary>  
    /// An empty page that can be used on its own or navigated to within a Frame.  
    /// </summary>  
    public sealed partial class MainPage : Page  
    {  
        public MainPage()  
        {  
            this.InitializeComponent();  
        }  
  
        const int NUM_TASKS = 48;  
        const int MIN_ITERATIONS = int.MaxValue / 1000;  
        const int MAX_ITERATIONS = MIN_ITERATIONS + 10000;  
  
        long m_totalIterations = 0;  
        readonly object m_totalItersLock = new object();  
  
        private void GetMaxNumberButton_Click(object sender, RoutedEventArgs e)  
        {  
            GetMaxNumberAsyncButton.IsEnabled = false;  
            lock (m_totalItersLock)  
            {  
                m_totalIterations = 0;  
            }  
            List<int> tasks = new List<int>();  
            for (var i = 0; i < NUM_TASKS; i++)  
            {  
                var result = 0;  
                result = GetNumber();  
                tasks.Add(result);  
            }  
            var max = tasks.Max();  
            var s = GetOutputString("GetMaxNumberButton_Click", NUM_TASKS, max, m_totalIterations);  
            TextBox1.Text += s;  
            GetMaxNumberAsyncButton.IsEnabled = true;  
        }  
  
        private async void GetMaxNumberAsyncButton_Click(object sender, RoutedEventArgs e)  
        {  
            GetMaxNumberButton.IsEnabled = false;  
            GetMaxNumberAsyncButton.IsEnabled = false;  
            lock (m_totalItersLock)  
            {  
                m_totalIterations = 0;  
            }  
            var tasks = new ConcurrentBag<Task<int>>();  
            for (var i = 0; i < NUM_TASKS; i++)  
            {  
                tasks.Add(GetNumberAsync());  
            }  
            await Task.WhenAll(tasks.ToArray());  
            var max = 0;  
            foreach (var task in tasks)  
            {  
                max = Math.Max(max, task.Result);  
            }  
            var func = "GetMaxNumberAsyncButton_Click";  
            var outputText = GetOutputString(func, NUM_TASKS, max, m_totalIterations);  
            TextBox1.Text += outputText;  
            this.GetMaxNumberButton.IsEnabled = true;  
            GetMaxNumberAsyncButton.IsEnabled = true;  
        }  
  
        private int GetNumber()  
        {  
            var rand = new Random();  
            var iters = rand.Next(MIN_ITERATIONS, MAX_ITERATIONS);  
            var result = 0;  
            lock (m_totalItersLock)  
            {  
                m_totalIterations += iters;  
            }  
            // we're just spinning here  
            // and using Random to frustrate compiler optimizations  
            for (var i = 0; i < iters; i++)  
            {  
                result = rand.Next();  
            }  
            return result;  
        }  
  
        private Task<int> GetNumberAsync()  
        {  
            return Task<int>.Run(() =>  
            {  
                return GetNumber();  
            });  
        }  
  
        string GetOutputString(string func, int cycles, int max, long totalIters)  
        {  
            var fmt = "{0,-35}Tasks:{1,3}    Maximum:{2, 12}    Iterations:{3,12}\n";  
            return String.Format(fmt, func, cycles, max, totalIters);  
        }  
  
    }  
}  
  
```
