---
title: Analýza využití procesoru v univerzální aplikace pro Windows | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- FSharp
- VB
- CSharp
- C++
ms.assetid: c122b08e-e3bf-43e6-bd6c-e776e178fd9a
caps.latest.revision: 21
author: MikeJo5000
ms.author: mikejo
manager: ghogen
robots: noindex,nofollow
ms.openlocfilehash: 11e8587176ecc452f8f97132d296cff93b09b5ac
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51741319"
---
# <a name="analyze-cpu-usage-in-a-windows-universal-app"></a>Analýza využití procesoru v univerzální aplikace pro Windows
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Platí pro Windows a Windows Phone] (.. /Image/windows_and_phone_content.png "windows_and_phone_content")  
  
 Když budete potřebovat zjistit problémy s výkonem ve vaší aplikaci, je dobrým začátkem pochopení, jak využívá procesor. **Využití procesoru** nástroj ukazuje, kde procesor stráví času prováděním kódu. Zaměřit se na konkrétní scénáře, využití procesoru může běžet s [rychlost odezvy UI XAML](http://msdn.microsoft.com/library/4ff84cd1-4e63-4fda-b34f-3ef862a6e480) nástroj, [spotřeba energie](../profiling/analyze-energy-use-in-store-apps.md) nástroje nebo oba nástroje v jedné relaci diagnostiky.  
  
> [!NOTE]
>  **Využití procesoru** nástroj nelze použít s aplikacemi pro Windows Phone Silverlight 8.1.  
  
 Tento názorný postup vás provede shromažďování a analýza využití procesoru pro jednoduchou aplikaci Windows Universal XAML.  
  
##  <a name="BKMK_Create_the_CpuUseDemo_project"></a> Vytvoření projektu CpuUseDemo  
 **CpuUseDemo** je aplikace, který byl vytvořen za účelem ukazují, jak shromažďovat a analyzovat data o využití procesoru. Tlačítka vygenerovat číslo při volání metody, která vybere maximální hodnota z více volání funkce. Volaná funkce vytvoří velký počet náhodných hodnot a vrátí poslední z nich. Data se zobrazí v textovém poli.  
  
1.  Vytvoření nového projektu s C# Windows Universal aplikaci s názvem **CpuUseDemo** pomocí **BlankApp** šablony.  
  
     ![Vytvořte CpuUseDemoProject](../profiling/media/cpu-use-newproject.png "CPU_USE_NewProject")  
  
2.  Nahraďte souboru MainPage.xaml s [tento kód](#BKMK_MainPage_xaml).  
  
3.  Nahraďte MainPage.xaml.cs s [tento kód](#BKMK_MainPage_xaml_cs).  
  
4.  Vytvořte aplikaci a vyzkoušejte si to. Aplikace není dostatečně jednoduchá, až vám ukážeme některé běžné případy analýzy dat využití procesoru.  
  
##  <a name="BKMK_Collect_CPU_usage_data"></a> Shromažďování dat o využití procesoru  
 ![Spustit sestavení pro vydání aplikace v simulátoru](../profiling/media/cpu-use-wt-setsimulatorandretail.png "CPU_USE_WT_SetSimulatorAndRetail")  
  
1. V sadě Visual Studio, nastavte cíl nasazení na **simulátor** a konfigurace řešení **vydání**.  
  
   -   Spuštění aplikace v simulátoru umožňuje snadno přepínat mezi aplikací a rozhraní IDE sady Visual Studio.  
  
   -   Tuto aplikaci spustíte v **vydání** režim poskytuje lepší přehled aplikace skutečný výkon vaší aplikace.  
  
2. Na **ladění** nabídce zvolte **Profiler výkonu...** .  
  
3. V Centru pro výkon a diagnostiku, zvolte **využití procesoru** a klikněte na tlačítko **Start**.  
  
    ![Spuštění diagnostické relace CpuUsage](../profiling/media/cpu-use-wt-perfdiaghub.png "CPU_USE_WT_PerfDiagHub")  
  
4. Při spuštění aplikace, klikněte na tlačítko **získat maximální počet**. Počkejte asi sekundy po výstupu se zobrazí, a pak zvolte **získat maximální číslo asynchronní**. Čekání mezi kliknutí na tlačítko vytvoří je jednodušší oddělit tlačítko klikněte rutiny v diagnostickou sestavu.  
  
5. Až na druhém řádku výstupu se zobrazí, zvolte **zastavit shromažďování** v Centru pro výkon a Diagnostika.  
  
   ![Zastavit shromažďování dat CpuUsage](../profiling/media/cpu-use-wt-stopcollection.png "CPU_USE_WT_StopCollection")  
  
   Nástroj využití CPU analyzuje data a zobrazí sestavu.  
  
   ![Sestava CpuUsage](../profiling/media/cpu-use-wt-report.png "CPU_USE_WT_Report")  
  
##  <a name="BKMK_Analyze_the_CPU_Usage_report"></a> Analýza sestavy využití procesoru  
  
###  <a name="BKMK_CPU_utilization_timeline_graph"></a> Časová osa graf využití procesoru  
 ![CpuUtilization &#40;%&#41; časová osa grafu](../profiling/media/cpu-use-wt-timelinegraph.png "CPU_USE_WT_TimelineGraph")  
  
 Graf využití procesoru obsahuje informace o aktivitě využití procesoru aplikace jako procento všech čas procesoru ze všech jader procesoru na zařízení. Data této sestavy byl shromážděn dvoujádrový počítače. Dva extrémní představují aktivity procesoru kliknutí dvě tlačítka. `GetMaxNumberButton_Click` provede synchronně jednojádrový, takže je vhodné metody výška grafu nikdy přesáhne 50 %. `GetMaxNumberAsycButton_Click` běží asynchronně napříč obě jádra ho tak, že ho znovu vypadá hned, který získá blíž k využívání prostředků procesoru na obou jádrech všechny jeho zásobníku.  
  
####  <a name="BKMK_Select_timeline_segments_to_view_details"></a> Vyberte časovou osu segmenty, chcete-li zobrazit podrobnosti  
 Pomocí výběru panelů na **diagnostické relace** časové osy a zaměřte se na GetMaxNumberButton_Click data:  
  
 ![GetMaxNumberButton&#95;klikněte na vybraný](../profiling/media/cpu-use-wt-getmaxnumberreport.png "CPU_USE_WT_GetMaxNumberReport")  
  
 **Diagnostické relace** časová osa nyní zobrazuje čas strávený na vybraný úsek (trochu déle než 2 sekundy v této sestavě) a filtry strom volání těchto metod, které byly spuštěny ve výběru.  
  
 Teď vyberte `GetMaxNumberAsyncButton_Click` segmentu.  
  
 ![GetMaxNumberAsyncButton&#95;Click report selection](../profiling/media/cpu-use-wt-getmaxnumberasync-selected.png "CPU_USE_WT_GetMaxNumberAsync_Selected")  
  
 Tato metoda nedokončí asi sekundy rychlejší než `GetMaxNumberButton_Click`, ale jsou méně zřejmé, význam položky stromu volání.  
  
###  <a name="BKMK_The_CPU_Usage_call_tree"></a> Využití procesoru strom volání  
 Abyste mohli začít Principy informace o volání stromu, klikněte `GetMaxNumberButton_Click` segmentovat a podívejte se na Podrobnosti stromu volání.  
  
####  <a name="BKMK_Call_tree_structure"></a> Struktura stromu volání  
 ![GetMaxNumberButton&#95;klikněte na tlačítko volání stromu](../profiling/media/cpu-use-wt-getmaxnumbercalltree-annotated.png "CPU_USE_WT_GetMaxNumberCallTree_annotated")  
  
|||  
|-|-|  
|![1. krok](../profiling/media/procguid-1.png "ProcGuid_1")|Nejvyšší uzel ve stromech volání Využití procesoru je fiktivní.|  
|![2. krok](../profiling/media/procguid-2.png "ProcGuid_2")|Ve většině aplikací, ve kterých zakážete možnost **Zobrazit externí kód**, je v druhé úrovni uzel **[Externí kód]**, který obsahuje systémový kód a kód architektury, který spouští a zastavuje aplikaci, vykresluje uživatelské rozhraní, řídí plánování podprocesů a na nejnižší úrovni zajišťuje pro aplikaci další služby.|  
|![3. krok](../profiling/media/procguid-3.png "ProcGuid_3")|Uzlu druhé úrovně jsou podřízeny metody uživatelského kódu a asynchronní rutiny, které volá nebo vytváří systémový kód a kód architektury druhé úrovně.|  
|![4. krok](../profiling/media/procguid-4.png "ProcGuid_4")|Podřízené uzly metody obsahují jenom data pro volání nadřízené metody. Pokud zakážete **Zobrazit externí kód**, mohou metody aplikace obsahovat také uzel **[Externí kód]**.|  
  
####  <a name="BKMK_External_Code"></a> Externí kód  
 Externí kód se skládá z funkce v systému a komponenty rozhraní, které jsou spouštěny v kódu, který napíšete. Externí kód obsahuje funkce, které spuštění a zastavení aplikace, vykreslení uživatelského rozhraní, řízení práce s vlákny a poskytují další nižší úrovně služby do aplikace. Ve většině případů nebudete zájem o externí kód, a proto využití procesoru volání stromu shromáždí externí funkce metody uživatele do jednoho **[externí kód]** uzlu.  
  
 Pokud chcete zobrazit volání cesty z externího kódu, zvolte **zobrazit externí kód** z **filtrovat zobrazení** seznamu a klikněte na tlačítko **použít**.  
  
 ![Vyberte zobrazení filtru, pak si ukážeme, externí kód](../profiling/media/cpu-use-wt-filterview.png "CPU_USE_WT_FilterView")  
  
 Myslete na to, že řetězy volání externího kódu je většinou hluboko vnořené, takže šířka sloupce Název funkce může na většině počítačových monitorů – s výjimkou těch největších – přesáhnout šířku zobrazení. Pokud k tomu dojde, názvy funkcí jsou zobrazeny jako **[...]** :  
  
 ![Vnořené externí kód ve stromu volání](../profiling/media/cpu-use-wt-showexternalcodetoowide.png "CPU_USE_WT_ShowExternalCodeTooWide")  
  
 Pomocí vyhledávacího pole vyhledejte uzel, který hledáte, pak použít vodorovný posuvník přenést data do zobrazení:  
  
 ![Hledat vnořené externí kód](../profiling/media/cpu-use-wt-showexternalcodetoowide-found.png "CPU_USE_WT_ShowExternalCodeTooWide_Found")  
  
###  <a name="BKMK_Call_tree_data_columns"></a> Volání stromu datové sloupce  
  
|||  
|-|-|  
|**Celkový čas procesoru (%)**|![Celkem % dat rovnice](../profiling/media/cpu-use-wt-totalpercentequation.png "CPU_USE_WT_TotalPercentEquation")<br /><br /> Procento procesoru aktivita aplikace ve vybraném časovém rozsahu, který byl použit volání funkce a funkce volané funkce. Všimněte si, že se liší od **využití výkonu procesoru** graf časové osy, která porovnává celkové aktivity aplikace na celková dostupná kapacita procesoru časový rozsah.|  
|**Vlastní čas procesoru (%)**|![Vlastní % rovnice](../profiling/media/cpu-use-wt-selflpercentequation.png "CPU_USE_WT_SelflPercentEquation")<br /><br /> Procento procesoru aktivita aplikace ve vybraném časovém rozsahu, která byla použita ve volání funkce, s výjimkou aktivit funkce volané funkce.|  
|**Celkový čas procesoru (ms)**|Počet milisekund strávený ve volání funkce ve vybraném časovém rozsahu a funkce, které byly volány funkce.|  
|**Vlastní čas procesoru (ms)**|Počet milisekund strávený ve volání funkce ve vybraném časovém rozsahu a funkce, které byly volány funkce.|  
|**Modul**|Název modulu, který obsahuje funkce, nebo počet modulů, který obsahuje funkce v uzlu [externí kód].|  
  
###  <a name="BKMK_Asynchronous_functions_in_the_CPU_Usage_call_tree"></a> Strom volání asynchronní funkce v využití procesoru  
 Když kompilátor narazí na asynchronní metodu, vytvoří třídu skryté k řízení provádění metody. Třída je koncepčně stavového stroje, který obsahuje seznam vygenerovaný kompilátorem funkce, které volají operace původní metody asynchronně, a zpětná volání, Plánovač a iterátory, které jsou nutné k nim správně. Při původní metody je volána metodou nadřazeného, modul runtime odebere z kontextu spuštění nadřazené metody a metody třídy skryté běží v kontextu systému a rozhraní framework kód, který řídí spuštění aplikace. Asynchronní metody jsou často, ale ne vždy spouštěny na jeden nebo více různých vláken. Tento kód se zobrazí ve stromu volání procesoru jako podřízené objekty **[externí kód]** uzel bezprostředně pod nejvyšší uzel stromu.  
  
 Tento údaj zobrazíte v našem příkladu, znovu vyberte `GetMaxNumberAsyncButton_Click` segment na časové ose.  
  
 ![GetMaxNumberAsyncButton&#95;Click report selection](../profiling/media/cpu-use-wt-getmaxnumberasync-selected.png "CPU_USE_WT_GetMaxNumberAsync_Selected")  
  
 První dva uzly v rámci **[externí kód]** způsoby kompilátorem generované třídy stav počítače. Třetí je volání na původní metodu. Generované metody rozšíření se dozvíte, co se děje.  
  
 ![Rozbalit GetMaxNumberAsyncButton&#95;klikněte na tlačítko volání stromu](../profiling/media/cpu-use-wt-getmaxnumberasync-expandedcalltree.png "CPU_USE_WT_GetMaxNumberAsync_ExpandedCallTree")  
  
-   `MainPage::GetMaxNumberAsyncButton_Click` velmi malý; nemá spravuje seznam hodnot úloh, vypočítá maximální počet výsledků a zobrazí výstup.  
  
-   `MainPage+<GetMaxNumberAsyncButton_Click>d__3::MoveNext` ukazuje aktivit potřebných k naplánování a spuštění 48 úkoly, které obalují volání `GetNumberAsync`.  
  
-   `MainPage::<GetNumberAsync>b__b` ukazuje aktivitu úloh, které volají `GetNumber`.  
  
##  <a name="BKMK_Next_steps"></a> Další kroky  
 Aplikace CpuUseDemo není nejvíce vynikající aplikace, ale jeho nástroje můžete rozšířit pomocí můžete experimentovat s asynchronní operace a další nástroje v rozcestníku výkon a Diagnostika.  
  
-   Všimněte si, že `MainPage::<GetNumberAsync>b__b` tráví víc času [externí kód] než provádění metody GetNumber. Většina této doby je režie na asynchronní operace. Zkuste zvýšit počet těchto úloh (nastavit `NUM_TASKS` konstantu MainPage.xaml.cs) a snížení počtu iterací v `GetNumber` (změnit `MIN_ITERATIONS` hodnota). Spustit scénář kolekce a porovnat aktivitu procesoru `MainPage::<GetNumberAsync>b__b`, který v původní relaci diagnostiky využití procesoru. Zkuste snížení úkolů a zvýšit počet iterací.  
  
-   Uživatelé často nezáleží skutečný výkon vaší aplikace; nestarají o dosahovaný výkon a rychlost odezvy aplikace. Nástroj pro Responzivní uživatelské rozhraní XAML zobrazuje podrobnosti o aktivitě ve vlákně uživatelského rozhraní, efekt vnímané rychlost odezvy.  
  
     Vytvořit novou relaci v rozcestníku výkon a diagnostiku a přidat nástroj pro Responzivní uživatelské rozhraní XAML a nástroj využití CPU. Spusťte scénář kolekce. Pokud jste si přečetli to daleko, sestava pravděpodobně nemá zjistíte cokoli, co je ještě již bylo zajištěno, ale rozdíly mezi **využití vlákna UI** působivý časovou osu grafu pro tyto dvě metody. V reálné, komplexní aplikace může být kombinací nástroje velmi užitečné.  
  
##  <a name="BKMK_MainPage_xaml"></a> MainPage.xaml  
  
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
  
##  <a name="BKMK_MainPage_xaml_cs"></a> MainPage.xaml.cs  
  
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



