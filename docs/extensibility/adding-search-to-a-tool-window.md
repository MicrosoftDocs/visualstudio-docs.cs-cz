---
title: Přidání vyhledávání do panelu nástrojů | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- tool windows, adding search
ms.assetid: f78c4892-8060-49c4-8ecd-4360f1b4d133
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 3b060261bec61859f33d99ec3f666e1285413592
ms.sourcegitcommit: 1c2ed640512ba613b3bbbc9ce348e28be6ca3e45
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/03/2018
ms.locfileid: "39498561"
---
# <a name="add-search-to-a-tool-window"></a>Přidání vyhledávání do panelu nástrojů
Při vytváření nebo aktualizace panelu nástrojů v rozšíření, můžete přidat stejný integraci vyhledávacích funkcí, které se zobrazí jinde v sadě Visual Studio. Tato funkce zahrnuje následující funkce:  
  
-   Vyhledávací pole, která je vždy umístěny v vlastní oblast panelu nástrojů.  
  
-   Indikátor průběhu, který je jako překryvný obrázek na vyhledávací pole samotného.  
  
-   Umožňuje zobrazit výsledky jako při zadávání jednotlivých znaků (rychlé vyhledávání), nebo pouze po zvolení **Enter** klíč (vyhledávání na vyžádání).  
  
-   Seznam, který ukazuje podmínky, u kterých jste hledáte jako poslední.  
  
-   Možnost filtrovat hledání podle konkrétních polí nebo aspektů hledání cíle.  
  
Podle tohoto postupu se dozvíte, jak provádět následující úlohy:  
  
1.  Vytvořte projekt VSPackage.  
  
2.  Vytvoření okna nástroje, který obsahuje ovládací prvek UserControl u objektu TextBox jen pro čtení.  
  
3.  Přidání vyhledávacího pole na panel nástrojů.  
  
4.  Přidání implementace hledání.  
  
5.  Povolte rychlé vyhledávání a zobrazovat indikátor průběhu.  
  
6.  Přidat **rozlišovat velikost písmen** možnost.  
  
7.  Přidat **hledat pouze řádky** filtru.  
  
## <a name="to-create-a-vsix-project"></a>Vytvoření projektu VSIX  
  
1.  Vytvořte projekt VSIX s názvem `TestToolWindowSearch` pomocí panelu nástrojů s názvem **TestSearch**. Pokud potřebujete pomoc s tím, přečtěte si téma [vytváření rozšíření pomocí panelu nástrojů](../extensibility/creating-an-extension-with-a-tool-window.md).  
  
## <a name="to-create-a-tool-window"></a>Vytvoření panelu nástrojů  
  
1.  V `TestToolWindowSearch` projekt, otevřete *TestSearchControl.xaml* souboru.  
  
2.  Nahraďte existující `<StackPanel>` blok s následující blok, který přidává jen pro čtení <xref:System.Windows.Controls.TextBox> k <xref:System.Windows.Controls.UserControl> v panelu nástrojů.  
  
    ```xaml  
    <StackPanel Orientation="Vertical">  
        <TextBox Name="resultsTextBox" Height="800.0"  
            Width="800.0"  
            IsReadOnly="True">  
        </TextBox>  
    </StackPanel>  
    ```  
  
3.  V *TestSearchControl.xaml.cs* soubor, přidejte následující příkaz using:  
  
    ```csharp  
    using System.Text;  
    ```  
  
4.  Odeberte `button1_Click()` metody.  
  
     V **TestSearchControl** třídy, přidejte následující kód.  
  
     Tento kód přidá veřejnou <xref:System.Windows.Controls.TextBox> vlastnost s názvem **SearchResultsTextBox** a řetězec veřejného vlastnost s názvem **SearchContent**. V konstruktoru SearchResultsTextBox nastavená na textové pole a SearchContent je inicializován na sadu řetězců oddělených znaku nového řádku. Obsah textového pole je také inicializován na sadu řetězců.  
  
     [!code-csharp[ToolWindowSearch#1](../extensibility/codesnippet/CSharp/adding-search-to-a-tool-window_1.cs)]
     [!code-vb[ToolWindowSearch#1](../extensibility/codesnippet/VisualBasic/adding-search-to-a-tool-window_1.vb)]  
  
5.  Sestavte projekt a spusťte ladění. Experimentální instanci sady Visual Studio se zobrazí.  
  
6.  V panelu nabídky zvolte **zobrazení** > **ostatní Windows** > **TestSearch**.  
  
     Zobrazí se panel nástrojů, ale ještě ovládací prvek hledání nezobrazí.  
  
## <a name="to-add-a-search-box-to-the-tool-window"></a>Přidání vyhledávacího pole na panel nástrojů  
  
1.  V *TestSearch.cs* přidejte následující kód, který `TestSearch` třídy. Přepíše kód <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowSearch.SearchEnabled%2A> vlastnost tak, aby přístupový objekt get vrací `true`.  
  
     Chcete-li povolit vyhledávání, je nutné přepsat <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowSearch.SearchEnabled%2A> vlastnost. <xref:Microsoft.VisualStudio.Shell.ToolWindowPane> Implementuje třída <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowSearch> a poskytuje výchozí implementaci, která neumožňuje vyhledávání.  
  
    ```csharp  
    public override bool SearchEnabled  
    {  
        get { return true; }  
    }  
    ```  
  
2.  Sestavte projekt a spusťte ladění. Zobrazí se experimentální instance.  
  
3.  V experimentální instanci sady Visual Studio, otevřete **TestSearch**.  
  
     V horní části okna nástroje, ovládací prvek vyhledávání se zobrazí s **hledání** mezí a s ikonou lupy zvětšení. Ale hledání ještě nefunguje vzhledem k tomu, že proces hledání ještě nebyla implementována.  
  
## <a name="to-add-the-search-implementation"></a>Chcete-li přidat implementace hledání  
 Když povolíte hledání na <xref:Microsoft.VisualStudio.Shell.ToolWindowPane>, jako v předchozím postupu, vytvoří panel nástrojů hledání hostitele. Tento hostitel nastavit a spravovat procesy, vyhledávání, které vždy odehrávat na vlákně na pozadí. Vzhledem k tomu, <xref:Microsoft.VisualStudio.Shell.ToolWindowPane> třída spravuje vytváření hostitele vyhledávání a nastavení hledání, potřebujete jenom vytvoření vyhledávací úlohy a nabízejí způsob vyhledávání. Proces vyhledávání se provádí na vlákně na pozadí a volání do ovládacího prvku okno nástroje, ke kterým dochází na vlákně UI. Proto je nutné použít <xref:Microsoft.VisualStudio.Shell.ThreadHelper.Invoke%2A> metoda spravovat všechna volání, které provedete v práci s ovládacím prvkem.  
  
1.  V *TestSearch.cs* soubor, přidejte následující `using` příkazy:  
  
    ```csharp  
    using System;  
    using System.Collections.Generic;  
    using System.Runtime.InteropServices;  
    using System.Text;  
    using System.Windows.Controls;  
    using Microsoft.Internal.VisualStudio.PlatformUI;  
    using Microsoft.VisualStudio;  
    using Microsoft.VisualStudio.PlatformUI;  
    using Microsoft.VisualStudio.Shell;  
    using Microsoft.VisualStudio.Shell.Interop;  
    ```  
  
2.  V `TestSearch` třídy, přidejte následující kód, který provede následující akce:  
  
    -   Přepsání <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowSearch.CreateSearch%2A> metodu pro vytvoření vyhledávací úlohy.  
  
    -   Přepsání <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowSearch.ClearSearch%2A> metodou pro obnovení stavu v textovém poli. Tato metoda je volána, když uživatel zruší úlohu vyhledávání a pokud uživatel nastaví nebo unsets možnosti nebo filtry. Obě <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowSearch.CreateSearch%2A> a <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowSearch.ClearSearch%2A> se nazývají na vlákně UI. Proto není nutné pro přístup k textovém poli prostřednictvím <xref:Microsoft.VisualStudio.Shell.ThreadHelper.Invoke%2A> metody.  
  
    -   Vytvoří třídu s názvem `TestSearchTask` , která dědí z <xref:Microsoft.VisualStudio.Shell.VsSearchTask>, která poskytuje výchozí implementaci třídy <xref:Microsoft.VisualStudio.Shell.Interop.IVsSearchTask>.  
  
         V `TestSearchTask`, konstruktor nastaví soukromé pole, která odkazuje na panel nástrojů. Poskytnout metodu vyhledávání, můžete přepsat <xref:Microsoft.VisualStudio.Shell.VsSearchTask.OnStartSearch%2A> a <xref:Microsoft.VisualStudio.Shell.VsSearchTask.OnStopSearch%2A> metody. <xref:Microsoft.VisualStudio.Shell.VsSearchTask.OnStartSearch%2A> Metody je, kde implementovat proces vyhledávání. Tento proces zahrnuje hledání, zobrazení výsledků hledání v textovém poli a volání implementace základní třídy tuto metodu za účelem hlášení, že hledání je dokončeno.  
  
    ```csharp  
    public override IVsSearchTask CreateSearch(uint dwCookie, IVsSearchQuery pSearchQuery, IVsSearchCallback pSearchCallback)  
    {  
        if (pSearchQuery == null || pSearchCallback == null)  
            return null;  
         return new TestSearchTask(dwCookie, pSearchQuery, pSearchCallback, this);  
    }  
  
    public override void ClearSearch()  
    {  
        TestSearchControl control = (TestSearchControl)this.Content;  
        control.SearchResultsTextBox.Text = control.SearchContent;  
    }  
  
    internal class TestSearchTask : VsSearchTask  
    {  
        private TestSearch m_toolWindow;  
  
        public TestSearchTask(uint dwCookie, IVsSearchQuery pSearchQuery, IVsSearchCallback pSearchCallback, TestSearch toolwindow)  
            : base(dwCookie, pSearchQuery, pSearchCallback)  
        {  
            m_toolWindow = toolwindow;  
        }  
  
        protected override void OnStartSearch()  
        {  
            // Use the original content of the text box as the target of the search.   
            var separator = new string[] { Environment.NewLine };  
            TestSearchControl control = (TestSearchControl)m_toolWindow.Content;  
            string[] contentArr = control.SearchContent.Split(separator, StringSplitOptions.None);  
  
            // Get the search option.   
            bool matchCase = false;  
            // matchCase = m_toolWindow.MatchCaseOption.Value;   
  
                // Set variables that are used in the finally block.  
                StringBuilder sb = new StringBuilder("");  
                uint resultCount = 0;  
                this.ErrorCode = VSConstants.S_OK;  
  
                try  
                {  
                    string searchString = this.SearchQuery.SearchString;  
  
                    // Determine the results.   
                    uint progress = 0;  
                    foreach (string line in contentArr)  
                    {  
                        if (matchCase == true)  
                        {  
                            if (line.Contains(searchString))  
                            {  
                                sb.AppendLine(line);  
                                resultCount++;  
                            }  
                        }  
                        else  
                            {  
                                if (line.ToLower().Contains(searchString.ToLower()))  
                                {  
                                    sb.AppendLine(line);  
                                    resultCount++;  
                                }  
                            }  
  
                            // SearchCallback.ReportProgress(this, progress++, (uint)contentArr.GetLength(0));   
  
                            // Uncomment the following line to demonstrate the progress bar.   
                            // System.Threading.Thread.Sleep(100);  
                        }  
                    }  
                    catch (Exception e)  
                    {  
                        this.ErrorCode = VSConstants.E_FAIL;  
                    }  
                    finally  
                    {  
                        ThreadHelper.Generic.Invoke(() =>  
                        { ((TextBox)((TestSearchControl)m_toolWindow.Content).SearchResultsTextBox).Text = sb.ToString(); });  
  
                        this.SearchResults = resultCount;  
                    }  
  
            // Call the implementation of this method in the base class.   
            // This sets the task status to complete and reports task completion.   
            base.OnStartSearch();  
        }  
  
        protected override void OnStopSearch()  
        {  
            this.SearchResults = 0;  
        }  
    }  
    ```  
  
3.  Testování vaší implementace hledání podle následujících kroků:  
  
    1.  Projekt znovu sestavte a spusťte ladění.  
  
    2.  V experimentální instanci sady Visual Studio, otevřete znovu okno nástroje, zadejte nějaký text hledání v okně hledání a klikněte na tlačítko **ENTER**.  
  
         Správné výsledky by se zobrazit.  
  
## <a name="to-customize-the-search-behavior"></a>Chcete-li přizpůsobit chování vyhledávání  
 Tak, že změníte nastavení vyhledávání, můžete provést řadu změn v tom, jak se zobrazí ovládací prvek pro hledání a jak se provádí vyhledávání. Můžete například změnit meze (výchozí text, který se zobrazí v poli vyhledat), minimální a maximální šířku ovládacího prvku vyhledávání a zda zobrazuje indikátor průběhu. Můžete také změnit bod, ve které výsledky hledání začnou objevovat (na vyžádání nebo podle rychlého vyhledávání) a, jestli se má zobrazit seznam termínů, pro které jste nedávno prohledávat. Úplný seznam nastavení najdete <xref:Microsoft.VisualStudio.PlatformUI.SearchSettingsDataSource> třídy.  
  
1.  V * TestSearch.cs* přidejte následující kód, který `TestSearch` třídy. Tento kód umožňuje okamžité vyhledávání namísto hledání na vyžádání (to znamená, že uživatel nemá na **ENTER**). Přepíše kód `ProvideSearchSettings` metodu `TestSearch` třídu, která je potřeba změnit výchozí nastavení.  
  
    ```csharp  
    public override void ProvideSearchSettings(IVsUIDataSource pSearchSettings)  
    {  
        Utilities.SetValue(pSearchSettings,   
            SearchSettingsDataSource.SearchStartTypeProperty.Name,   
            (uint)VSSEARCHSTARTTYPE.SST_INSTANT);}  
    ```  
  
2.  Testování nového nastavení tak, že znovu sestavit řešení a restartování ladicího programu.  
  
     Výsledky hledání zobrazeny pokaždé, když zadejte znak do vyhledávacího pole.  
  
3.  V `ProvideSearchSettings` metodu, přidejte následující řádek, který umožňuje zobrazovat indikátor průběhu.  
  
    ```csharp  
    public override void ProvideSearchSettings(IVsUIDataSource pSearchSettings)  
    {  
        Utilities.SetValue(pSearchSettings,   
            SearchSettingsDataSource.SearchStartTypeProperty.Name,   
             (uint)VSSEARCHSTARTTYPE.SST_INSTANT);  
        Utilities.SetValue(pSearchSettings,   
            SearchSettingsDataSource.SearchProgressTypeProperty.Name,   
             (uint)VSSEARCHPROGRESSTYPE.SPT_DETERMINATE);  
    }  
    ```  
  
     U panelu průběh zobrazit průběh musí být uvedena. Chcete-li vykazovat průběh, Odkomentujte následující kód do `OnStartSearch` metodu `TestSearchTask` třídy:  
  
    ```csharp  
    SearchCallback.ReportProgress(this, progress++, (uint)contentArr.GetLength(0));  
    ```  
  
4.  Zpomalit zpracování dostatek, průběh je zobrazen panel zrušte komentář u následujícího řádku `OnStartSearch` metodu `TestSearchTask` třídy:  
  
    ```csharp  
    System.Threading.Thread.Sleep(100);  
    ```  
  
5.  Nové nastavení testu řešení znovu sestavit a spustit ladění.  
  
     Indikátor průběhu se zobrazí v okně hledání (jako modrá čára pod vyhledávacím polem text) pokaždé, když provést hledání.  
  
## <a name="to-enable-users-to-refine-their-searches"></a>Povolit uživatelům upřesněte své hledání  
 Můžete povolit uživatelům upřesněte své hledání prostřednictvím možnosti, jako **rozlišovat velikost písmen** nebo **celá slova**. Možnosti mohou být logická hodnota, která se zobrazí jako zaškrtávací políčka nebo příkazy, které se zobrazí jako tlačítka. V tomto návodu vytvoříte logickou možnost.  
  
1.  V *TestSearch.cs* přidejte následující kód, který `TestSearch` třídy. Přepíše kód `SearchOptionsEnum` metodu, která umožňuje implementace hledání ke zjištění, zda je daný možnost zapnutí nebo vypnutí. Kód v `SearchOptionsEnum` přidává možnost rozlišovat velikost písmen pro <xref:Microsoft.VisualStudio.Shell.Interop.IVsEnumWindowSearchOptions> enumerátor. Je také k dispozici jako možnost rozlišovat velikost písmen `MatchCaseOption` vlastnost.  
  
    ```csharp  
    private IVsEnumWindowSearchOptions m_optionsEnum;  
    public override IVsEnumWindowSearchOptions SearchOptionsEnum  
    {  
        get  
        {  
            if (m_optionsEnum == null)  
            {  
                List<IVsWindowSearchOption> list = new List<IVsWindowSearchOption>();  
  
                list.Add(this.MatchCaseOption);  
  
                m_optionsEnum = new WindowSearchOptionEnumerator(list) as IVsEnumWindowSearchOptions;  
            }  
            return m_optionsEnum;  
        }  
    }  
  
    private WindowSearchBooleanOption m_matchCaseOption;  
    public WindowSearchBooleanOption MatchCaseOption  
    {  
        get  
        {  
            if (m_matchCaseOption == null)  
            {  
                m_matchCaseOption = new WindowSearchBooleanOption("Match case", "Match case", false);  
            }  
            return m_matchCaseOption;  
        }  
    }  
    ```  
  
2.  V `TestSearchTask` třídy, zrušte komentář u následující řádek v `OnStartSearch` metody:  
  
    ```csharp
    matchCase = m_toolWindow.MatchCaseOption.Value;
    ```
  
3.  Otestujte možnost:  
  
    1.  Sestavte projekt a spusťte ladění. Zobrazí se experimentální instance.  
  
    2.  V panelu nástrojů klikněte na šipku dolů na pravé straně textového pole.  
  
         **Rozlišovat velikost písmen** se zobrazí zaškrtávací políčko.  
  
    3.  Vyberte **rozlišovat velikost písmen** zaškrtněte políčko a potom k vyhledávání.  
  
## <a name="to-add-a-search-filter"></a>Chcete-li přidat vyhledávací filtr  
 Můžete přidat vyhledávací filtry, které umožňují uživatelům upřesnění sady hledání cíle. Například můžete filtrovat soubory v Průzkumníku souborů tak, že data, na kterých byly naposledy změněna a jejich přípony názvů souborů. V tomto názorném postupu přidáte filtr i pouze pro řádky. Když uživatele vybere tento filtr, přidá hostitele vyhledávání řetězce, které zadáte do vyhledávacího dotazu. Potom můžete identifikovat tyto řetězce uvnitř metodu vyhledávání a filtrovat hledání cíle odpovídajícím způsobem.  
  
1.  V *TestSearch.cs* přidejte následující kód, který `TestSearch` třídy. Kód implementuje `SearchFiltersEnum` tak, že přidáte <xref:Microsoft.VisualStudio.PlatformUI.WindowSearchSimpleFilter> , který určuje filtrování výsledků hledání, aby se zobrazovala pouze řádky.  
  
    ```csharp  
    public override IVsEnumWindowSearchFilters SearchFiltersEnum  
    {  
        get  
        {  
            List<IVsWindowSearchFilter> list = new List<IVsWindowSearchFilter>();  
            list.Add(new WindowSearchSimpleFilter("Search even lines only", "Search even lines only", "lines", "even"));  
            return new WindowSearchFilterEnumerator(list) as IVsEnumWindowSearchFilters;  
        }  
    }  
  
    ```  
  
     Nyní se zobrazí ovládací prvek hledání vyhledávací filtr `Search even lines only`. Pokud uživatel zvolí filtr řetězec `lines:"even"` se zobrazí na panelu hledání. Další kritéria vyhledávání můžete zobrazit ve stejnou dobu jako filtr. Hledání řetězců se můžou objevit před filtru, po filtr, nebo obojí.  
  
2.  V *TestSearch.cs* přidejte následující metody, které `TestSearchTask` třídy, která je v `TestSearch` třídy. Tyto metody podporují `OnStartSearch` metodu, která upravíte v dalším kroku.  
  
    ```csharp  
    private string RemoveFromString(string origString, string stringToRemove)  
    {  
        int index = origString.IndexOf(stringToRemove);  
        if (index == -1)  
            return origString;  
        else   
             return (origString.Substring(0, index) + origString.Substring(index + stringToRemove.Length)).Trim();  
    }  
  
    private string[] GetEvenItems(string[] contentArr)  
    {  
        int length = contentArr.Length / 2;  
        string[] evenContentArr = new string[length];  
  
        int indexB = 0;  
        for (int index = 1; index < contentArr.Length; index += 2)  
        {  
            evenContentArr[indexB] = contentArr[index];  
            indexB++;  
        }  
  
        return evenContentArr;  
    }  
    ```  
  
3.  V `TestSearchTask` třídy, aktualizujte `OnStartSearch` metodu s následujícím kódem. Tato změna aktualizuje kód pro podporu filtru.  
  
    ```csharp  
    protected override void OnStartSearch()  
    {  
        // Use the original content of the text box as the target of the search.   
        var separator = new string[] { Environment.NewLine };  
        string[] contentArr = ((TestSearchControl)m_toolWindow.Content).SearchContent.Split(separator, StringSplitOptions.None);  
  
        // Get the search option.   
        bool matchCase = false;  
        matchCase = m_toolWindow.MatchCaseOption.Value;  
  
        // Set variables that are used in the finally block.  
        StringBuilder sb = new StringBuilder("");  
        uint resultCount = 0;  
        this.ErrorCode = VSConstants.S_OK;  
  
        try  
        {  
            string searchString = this.SearchQuery.SearchString;  
  
            // If the search string contains the filter string, filter the content array.   
            string filterString = "lines:\"even\"";  
  
            if (this.SearchQuery.SearchString.Contains(filterString))  
            {  
                // Retain only the even items in the array.  
                contentArr = GetEvenItems(contentArr);  
  
                // Remove 'lines:"even"' from the search string.  
                searchString = RemoveFromString(searchString, filterString);  
            }  
  
            // Determine the results.   
            uint progress = 0;  
            foreach (string line in contentArr)  
            {  
                if (matchCase == true)  
                {  
                    if (line.Contains(searchString))  
                    {  
                        sb.AppendLine(line);  
                        resultCount++;  
                    }  
                }  
                else  
                {  
                    if (line.ToLower().Contains(searchString.ToLower()))  
                    {  
                        sb.AppendLine(line);  
                        resultCount++;  
                    }  
                }  
  
                SearchCallback.ReportProgress(this, progress++, (uint)contentArr.GetLength(0));  
  
                // Uncomment the following line to demonstrate the progress bar.   
                // System.Threading.Thread.Sleep(100);  
            }  
        }  
        catch (Exception e)  
        {  
            this.ErrorCode = VSConstants.E_FAIL;  
        }  
        finally  
        {  
            ThreadHelper.Generic.Invoke(() =>  
            { ((TextBox)((TestSearchControl)m_toolWindow.Content).SearchResultsTextBox).Text = sb.ToString(); });  
  
            this.SearchResults = resultCount;  
        }  
  
        // Call the implementation of this method in the base class.   
        // This sets the task status to complete and reports task completion.   
        base.OnStartSearch();  
    }  
    ```  
  
4.  Otestujte svůj kód.  
  
5.  Sestavte projekt a spusťte ladění. V experimentální instanci sady Visual Studio otevřete panel nástrojů a klikněte na šipku dolů na ovládacím prvku hledání.  
  
     **Rozlišovat velikost písmen** zaškrtávací políčko a **hledat pouze řádky** filtru se zobrazí.  
  
6.  Zvolte požadovaný filtr.  
  
     Do vyhledávacího pole obsahuje **řádky: "i"**, a zobrazí se následující výsledky:  
  
     dobré 2  
  
     4 v pořádku  
  
     6 goodbye  
  
7.  Odstranit `lines:"even"` z vyhledávacího pole, vyberte **rozlišovat velikost písmen** zaškrtněte políčko a potom zadejte `g` do vyhledávacího pole.  
  
     Zobrazí se následující výsledky:  
  
     1 go  
  
     dobré 2  
  
     5 goodbye  
  
8.  Zvolte na X vpravo od pole hledání.  
  
     Vymazat hledání a zobrazí původní obsah. Ale **rozlišovat velikost písmen** zaškrtávací políčko je stále vybrán.