---
title: Přidání hledání do okna nástroje | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- tool windows, adding search
ms.assetid: f78c4892-8060-49c4-8ecd-4360f1b4d133
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f9112a3368ba604c4291f9018e763022e953c4fc
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80740148"
---
# <a name="add-search-to-a-tool-window"></a>Přidání hledání do okna nástroje
Když v rozšíření vytvoříte nebo aktualizujete okno nástroje, můžete přidat stejnou funkci hledání, která se zobrazí jinde v sadě Visual Studio. Tato funkce zahrnuje následující funkce:

- Vyhledávací pole, které je vždy umístěno ve vlastní oblasti panelu nástrojů.

- Indikátor průběhu, který je překrytý na samotném vyhledávacím poli.

- Možnost zobrazit výsledky, jakmile zadáte každý znak (okamžité vyhledávání) nebo pouze po výběru klávesy **Enter** (vyhledávání na vyžádání).

- Seznam, který zobrazuje termíny, pro které jste hledali naposledy.

- Možnost filtrovat vyhledávání podle konkrétních polí nebo aspektů cílů vyhledávání.

Podle tohoto návodu se dozvíte, jak provádět následující úkoly:

1. Vytvořte projekt VSPackage.

2. Vytvořte okno nástroje, které obsahuje UserControl s textbox jen pro čtení.

3. Přidejte vyhledávací pole do okna nástroje.

4. Přidejte implementaci hledání.

5. Povolte okamžité vyhledávání a zobrazení indikátoru průběhu.

6. Přidejte možnost **Spárovat případ.**

7. Přidejte **filtr pro rovné řádky hledání.**

## <a name="to-create-a-vsix-project"></a>Vytvoření projektu VSIX

1. Vytvořte projekt VSIX s názvem `TestToolWindowSearch` s oknem nástroje s názvem **TestSearch**. Pokud potřebujete pomoc, přečtěte si téma [Vytvoření rozšíření pomocí okna nástroje](../extensibility/creating-an-extension-with-a-tool-window.md).

## <a name="to-create-a-tool-window"></a>Vytvoření okna nástroje

1. V `TestToolWindowSearch` projektu otevřete soubor *TestSearchControl.xaml.*

2. Nahraďte `<StackPanel>` existující blok následujícím blokem, který <xref:System.Windows.Controls.TextBox> přidá <xref:System.Windows.Controls.UserControl> jen pro čtení do okna nástroje.

    ```xaml
    <StackPanel Orientation="Vertical">
        <TextBox Name="resultsTextBox" Height="800.0"
            Width="800.0"
            IsReadOnly="True">
        </TextBox>
    </StackPanel>
    ```

3. Do *TestSearchControl.xaml.cs* souboru přidejte následující příkaz using směrnice:

    ```csharp
    using System.Text;
    ```

4. Odeberte metodu. `button1_Click()`

     Do třídy **TestSearchControl** přidejte následující kód.

     Tento kód přidá <xref:System.Windows.Controls.TextBox> veřejnou vlastnost s názvem **SearchResultsTextBox** a vlastnost veřejného řetězce s názvem **SearchContent**. V konstruktoru je SearchResultsTextBox nastaven na textové pole a SearchContent je inicializován na novou sadu řetězců oddělených novým řádkem. Obsah textového pole je také inicializován na sadu řetězců.

     [!code-csharp[ToolWindowSearch#1](../extensibility/codesnippet/CSharp/adding-search-to-a-tool-window_1.cs)]
     [!code-vb[ToolWindowSearch#1](../extensibility/codesnippet/VisualBasic/adding-search-to-a-tool-window_1.vb)]

5. Sestavení projektu a začít ladění. Zobrazí se experimentální instance sady Visual Studio.

6. Na řádku nabídek zvolte **Zobrazit** > jiné**testovací vyhledávání systému****Windows** > .

     Zobrazí se okno nástroje, ale ovládací prvek hledání se ještě nezobrazí.

## <a name="to-add-a-search-box-to-the-tool-window"></a>Přidání vyhledávacího pole do okna nástroje

1. V *souboru TestSearch.cs* přidejte do `TestSearch` třídy následující kód. Kód přepíše <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowSearch.SearchEnabled%2A> vlastnost tak, aby get `true`přistupující objekt vrátí .

     Chcete-li povolit vyhledávání, <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowSearch.SearchEnabled%2A> je nutné přepsat vlastnost. Třída <xref:Microsoft.VisualStudio.Shell.ToolWindowPane> implementuje <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowSearch> a poskytuje výchozí implementaci, která neumožňuje vyhledávání.

    ```csharp
    public override bool SearchEnabled
    {
        get { return true; }
    }
    ```

2. Sestavení projektu a začít ladění. Zobrazí se experimentální instance.

3. V experimentální instanci sady Visual Studio otevřete **testSearch**.

     V horní části okna nástroje se zobrazí ovládací prvek hledání s vodoznakem **Hledat** a ikonou lupy. Hledání však ještě nefunguje, protože proces hledání nebyl implementován.

## <a name="to-add-the-search-implementation"></a>Přidání implementace hledání
 Pokud povolíte hledání <xref:Microsoft.VisualStudio.Shell.ToolWindowPane>v souboru , stejně jako v předchozím postupu, okno nástroje vytvoří hostitele hledání. Tento hostitel nastavuje a spravuje procesy vyhledávání, které se vždy vyskytují ve vlákně na pozadí. Vzhledem <xref:Microsoft.VisualStudio.Shell.ToolWindowPane> k tomu, že třída spravuje vytvoření hostitele vyhledávání a nastavení hledání, stačí vytvořit úlohu hledání a poskytnout metodu hledání. Proces hledání probíhá ve vlákně na pozadí a volání ovládacího prvku okna nástroje dochází ve vlákně uživatelského rozhraní. Proto je nutné použít [ThreadHelper.Invoke *](https://msdn.microsoft.com/data/ee197798(v=vs.85)) metoda ke správě všechna volání, která provedete při práci s ovládacím prvkem.

1. Do souboru *TestSearch.cs* přidejte následující `using` direktivy:

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

2. Do `TestSearch` třídy přidejte následující kód, který provádí následující akce:

    - Přepíše <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowSearch.CreateSearch%2A> metodu a vytvoří úlohu hledání.

    - Přepíše <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowSearch.ClearSearch%2A> metodu k obnovení stavu textového pole. Tato metoda se nazývá, když uživatel zruší úlohu hledání a když uživatel nastaví nebo zruší nastavení možností nebo filtrů. Oba <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowSearch.CreateSearch%2A> <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowSearch.ClearSearch%2A> a jsou volány na vlákno uživatelského rozhraní. Proto není nutné získat přístup k textovému poli pomocí [ThreadHelper.Invoke*metoda.](https://msdn.microsoft.com/data/ee197798(v=vs.85))

    - Vytvoří třídu s `TestSearchTask` názvem, která <xref:Microsoft.VisualStudio.Shell.VsSearchTask>dědí z , <xref:Microsoft.VisualStudio.Shell.Interop.IVsSearchTask>která poskytuje výchozí implementaci .

         V `TestSearchTask`aplikace nastaví konstruktor soukromé pole, které odkazuje na okno nástroje. Chcete-li poskytnout metodu hledání, přepište metody <xref:Microsoft.VisualStudio.Shell.VsSearchTask.OnStartSearch%2A> a. <xref:Microsoft.VisualStudio.Shell.VsSearchTask.OnStopSearch%2A> Metoda <xref:Microsoft.VisualStudio.Shell.VsSearchTask.OnStartSearch%2A> je místo, kde implementovat proces hledání. Tento proces zahrnuje provedení hledání, zobrazení výsledků hledání v textovém poli a volání implementace základní třídy této metody k oznámení, že hledání je dokončeno.

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

3. Otestujte implementaci vyhledávání provedením následujících kroků:

    1. Znovu sestavte projekt a začněte ladění.

    2. V experimentální instanci sady Visual Studio znovu otevřete okno nástroje, zadejte do vyhledávacího okna nějaký hledaný text a klepněte na tlačítko **ENTER**.

         Měly by se zobrazit správné výsledky.

## <a name="to-customize-the-search-behavior"></a>Přizpůsobení chování hledání
 Změnou nastavení vyhledávání můžete provést různé změny ve způsobu, jakým se ovládací prvek vyhledávání zobrazuje a jak se vyhledávání provádí. Můžete například změnit vodoznak (výchozí text, který se zobrazí ve vyhledávacím poli), minimální a maximální šířku ovládacího prvku hledání a zda se má zobrazit indikátor průběhu. Můžete také změnit bod, ve kterém se začnou zobrazovat výsledky hledání (na vyžádání nebo okamžité vyhledávání) a zda chcete zobrazit seznam výrazů, pro které jste nedávno hledali. Kompletní seznam nastavení najdete ve <xref:Microsoft.VisualStudio.PlatformUI.SearchSettingsDataSource> třídě.

1. V souboru* TestSearch.cs* přidejte do `TestSearch` třídy následující kód. Tento kód umožňuje okamžité vyhledávání namísto vyhledávání na vyžádání (což znamená, že uživatel nemusí klepnout na **klávesu ENTER**). Kód přepíše `ProvideSearchSettings` metodu `TestSearch` ve třídě, která je nezbytná ke změně výchozího nastavení.

    ```csharp
    public override void ProvideSearchSettings(IVsUIDataSource pSearchSettings)
    {
        Utilities.SetValue(pSearchSettings,
            SearchSettingsDataSource.SearchStartTypeProperty.Name,
            (uint)VSSEARCHSTARTTYPE.SST_INSTANT);}
    ```

2. Otestujte nové nastavení opětovným sestavením řešení a restartováním ladicího programu.

     Výsledky hledání se zobrazí pokaždé, když zadáte znak do vyhledávacího pole.

3. Do `ProvideSearchSettings` metody přidejte následující řádek, který umožňuje zobrazení indikátoru průběhu.

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

     Aby se panel průběhu zobrazil, musí být hlášen průběh. Chcete-li ohlásit průběh, odkomentujte následující kód v metodě `OnStartSearch` třídy: `TestSearchTask`

    ```csharp
    SearchCallback.ReportProgress(this, progress++, (uint)contentArr.GetLength(0));
    ```

4. Chcete-li zpomalit zpracování natolik, že indikátor průběhu `OnStartSearch` je viditelný, odkomentujte následující řádek v metodě `TestSearchTask` třídy:

    ```csharp
    System.Threading.Thread.Sleep(100);
    ```

5. Otestujte nové nastavení opětovným sestavením řešení a zahájením ladění.

     Indikátor průběhu se zobrazí v okně hledání (jako modrá čára pod vyhledávacím textovým polem) při každém hledání.

## <a name="to-enable-users-to-refine-their-searches"></a>Povolení uživatelům upřesnit jejich hledání
 Uživatelům můžete povolit, aby upřesnili svá hledání pomocí možností, jako je **například případ shody** nebo **shoda celého slova**. Možnosti mohou být logické, které se zobrazují jako zaškrtávací políčka, nebo příkazy, které se zobrazují jako tlačítka. V tomto návodu vytvoříte logickou možnost.

1. V *souboru TestSearch.cs* přidejte do `TestSearch` třídy následující kód. Kód přepíše `SearchOptionsEnum` metodu, která umožňuje implementaci hledání zjistit, zda je daná možnost zapnuta nebo vypnuta. Kód v `SearchOptionsEnum` přidá možnost spárovat <xref:Microsoft.VisualStudio.Shell.Interop.IVsEnumWindowSearchOptions> případ čítače výčtu. Možnost shody případu je také `MatchCaseOption` k dispozici jako vlastnost.

    ```csharp
    private IVsEnumWindowSearchOptions m_optionsEnum;
    public override IVsEnumWindowSearchOptions SearchOptionsEnum
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

2. Ve `TestSearchTask` třídě odkomentujte následující `OnStartSearch` řádek v metodě:

    ```csharp
    matchCase = m_toolWindow.MatchCaseOption.Value;
    ```

3. Otestujte možnost:

    1. Sestavení projektu a začít ladění. Zobrazí se experimentální instance.

    2. V okně nástroje zvolte šipku dolů na pravé straně textového pole.

         Zobrazí se políčko **Spárovat případ.**

    3. Zaškrtněte políčko **Srovnat malá a velká písmena** a proveďte některá hledání.

## <a name="to-add-a-search-filter"></a>Přidání vyhledávacího filtru
 Můžete přidat vyhledávací filtry, které uživatelům umožní upřesnit sadu cílů hledání. Můžete například filtrovat soubory v Průzkumníkovi souborů podle dat, kdy byly naposledy upraveny, a podle jejich přípon názvů souborů. V tomto návodu přidáte filtr pouze pro sudé řádky. Když uživatel vybere tento filtr, hostitel hledání přidá řetězce, které zadáte do vyhledávacího dotazu. Tyto řetězce pak můžete identifikovat uvnitř metody vyhledávání a odpovídajícím způsobem filtrovat cíle hledání.

1. V *souboru TestSearch.cs* přidejte do `TestSearch` třídy následující kód. Kód implementuje `SearchFiltersEnum` <xref:Microsoft.VisualStudio.PlatformUI.WindowSearchSimpleFilter> přidáním, který určuje filtrovat výsledky hledání tak, aby se zobrazily pouze sudé řádky.

    ```csharp
    public override IVsEnumWindowSearchFilters SearchFiltersEnum
    {
        get
        {
            List<IVsWindowSearchFilter> list = new List<IVsWindowSearchFilter>();
            list.Add(new WindowSearchSimpleFilter("Search even lines only", "Search even lines only", "lines", "even"));
            return new WindowSearchFilterEnumerator(list) as IVsEnumWindowSearchFilters;
        }
    }

    ```

     Nyní ovládací prvek hledání `Search even lines only`zobrazí vyhledávací filtr . Když uživatel vybere filtr, řetězec `lines:"even"` se zobrazí ve vyhledávacím poli. Další kritéria vyhledávání se mohou zobrazit současně s filtrem. Vyhledávací řetězce se mohou zobrazit před filtrem, za filtrem nebo obojím.

2. V *souboru TestSearch.cs* přidejte do `TestSearchTask` třídy následující `TestSearch` metody, které jsou ve třídě. Tyto metody `OnStartSearch` podporují metodu, kterou upravíte v dalším kroku.

    ```csharp
    private string RemoveFromString(string origString, string stringToRemove)
    {
        int index = origString.IndexOf(stringToRemove);
        if (index == -1)
            return origString;
        else 
             return (origString.Substring(0, index) + origString.Substring(index + stringToRemove.Length)).Trim();
    }

    private string[] GetEvenItems(string[] contentArr)
    {
        int length = contentArr.Length / 2;
        string[] evenContentArr = new string[length];

        int indexB = 0;
        for (int index = 1; index < contentArr.Length; index += 2)
        {
            evenContentArr[indexB] = contentArr[index];
            indexB++;
        }

        return evenContentArr;
    }
    ```

3. Ve `TestSearchTask` třídě aktualizujte `OnStartSearch` metodu následujícím kódem. Tato změna aktualizuje kód pro podporu filtru.

    ```csharp
    protected override void OnStartSearch()
    {
        // Use the original content of the text box as the target of the search. 
        var separator = new string[] { Environment.NewLine };
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

4. Otestujte svůj kód.

5. Sestavení projektu a začít ladění. V experimentální instanci sady Visual Studio otevřete okno nástroje a pak v ovládacím prvku hledání zvolte šipku dolů.

     Zobrazí se **políčko Spárovat případ** a pouze filtr **Hledat sudé řádky.**

6. Zvolte filtr.

     Vyhledávací pole obsahuje **řádky:"sudý"** a zobrazí se následující výsledky:

     2 dobré

     4 Dobrý

     6 Sbohem

7. Odstranit `lines:"even"` z vyhledávacího pole zaškrtněte políčko **Srovnat případ** a zadejte `g` do vyhledávacího pole.

     Zobrazí se následující výsledky:

     1 jít

     2 dobré

     5 sbohem

8. Zvolte X na pravé straně vyhledávacího pole.

     Hledání je vymazáno a zobrazí se původní obsah. Je však stále zaškrtnuto políčko **Spárovat případ.**
