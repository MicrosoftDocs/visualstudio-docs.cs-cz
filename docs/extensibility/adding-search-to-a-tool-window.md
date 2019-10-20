---
title: Přidání vyhledávání do okna nástroje | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- tool windows, adding search
ms.assetid: f78c4892-8060-49c4-8ecd-4360f1b4d133
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 4414f6d907424a1abb56bccd1d1b125444e7c716
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72648003"
---
# <a name="add-search-to-a-tool-window"></a>Přidání vyhledávání do okna nástroje
Při vytváření nebo aktualizaci okna nástroje ve vašem rozšíření můžete přidat stejné funkce hledání, které se zobrazí jinde v aplikaci Visual Studio. Tato funkce zahrnuje tyto funkce:

- Vyhledávací pole, které je vždy umístěno ve vlastní oblasti panelu nástrojů.

- Indikátor průběhu, který je v samotném vyhledávacím poli překrytý

- Možnost Zobrazit výsledky hned po zadání jednotlivých znaků (okamžité hledání) nebo jenom po zvolení klávesy **ENTER** (hledání na vyžádání).

- Seznam zobrazující výrazy, pro které jste prohledali poslední.

- Možnost filtrovat hledání podle konkrétních polí nebo aspektů cílů hledání.

Podle tohoto návodu se dozvíte, jak provádět následující úlohy:

1. Vytvořte projekt VSPackage.

2. Vytvořte okno nástroje, které obsahuje UserControl s textovým polem jen pro čtení.

3. Přidejte vyhledávací pole do okna nástroje.

4. Přidejte implementaci vyhledávání.

5. Umožňuje okamžité vyhledávání a zobrazení indikátoru průběhu.

6. Přidejte možnost **případu shody** .

7. Přidejte filtr na **sudé řádky** .

## <a name="to-create-a-vsix-project"></a>Vytvoření projektu VSIX

1. Vytvořte projekt VSIX s názvem `TestToolWindowSearch` s oknem nástrojů s názvem **TestSearch**. Pokud potřebujete pomoc, přečtěte si téma [Vytvoření rozšíření pomocí okna nástroje](../extensibility/creating-an-extension-with-a-tool-window.md).

## <a name="to-create-a-tool-window"></a>Vytvoření okna nástroje

1. V projektu `TestToolWindowSearch` otevřete soubor *TestSearchControl. XAML* .

2. Existující blok `<StackPanel>` nahraďte následujícím blokem, který do <xref:System.Windows.Controls.UserControl> v okně nástroje přidá <xref:System.Windows.Controls.TextBox> jen pro čtení.

    ```xaml
    <StackPanel Orientation="Vertical">
        <TextBox Name="resultsTextBox" Height="800.0"
            Width="800.0"
            IsReadOnly="True">
        </TextBox>
    </StackPanel>
    ```

3. Do souboru *TestSearchControl.XAML.cs* přidejte následující direktivu using:

    ```csharp
    using System.Text;
    ```

4. Odeberte metodu `button1_Click()`.

     Do třídy **TestSearchControl** přidejte následující kód.

     Tento kód přidá vlastnost Public <xref:System.Windows.Controls.TextBox> s názvem **SearchResultsTextBox** a vlastnost veřejného řetězce s názvem **SearchContent**. V konstruktoru je SearchResultsTextBox nastaveno na textové pole a SearchContent je inicializována na sadu řetězců oddělenými na nový řádek. Obsah textového pole je také inicializován do sady řetězců.

     [!code-csharp[ToolWindowSearch#1](../extensibility/codesnippet/CSharp/adding-search-to-a-tool-window_1.cs)]
     [!code-vb[ToolWindowSearch#1](../extensibility/codesnippet/VisualBasic/adding-search-to-a-tool-window_1.vb)]

5. Sestavte projekt a spusťte ladění. Zobrazí se experimentální instance aplikace Visual Studio.

6. Na panelu nabídek vyberte možnost **zobrazit**  > **jiné Windows**  > **TestSearch**.

     Zobrazí se okno nástroje, ale ovládací prvek hledání ještě není zobrazen.

## <a name="to-add-a-search-box-to-the-tool-window"></a>Přidání vyhledávacího pole do okna nástroje

1. Do souboru *TestSearch.cs* přidejte následující kód do třídy `TestSearch`. Kód Přepisuje vlastnost <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowSearch.SearchEnabled%2A> tak, aby přistupující objekt get vrátil `true`.

     Chcete-li povolit hledání, je nutné přepsat vlastnost <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowSearch.SearchEnabled%2A>. Třída <xref:Microsoft.VisualStudio.Shell.ToolWindowPane> implementuje <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowSearch> a poskytuje výchozí implementaci, která neumožňuje vyhledávání.

    ```csharp
    public override bool SearchEnabled
    {
        get { return true; }
    }
    ```

2. Sestavte projekt a spusťte ladění. Objeví se experimentální instance.

3. V experimentální instanci aplikace Visual Studio otevřete **TestSearch**.

     V horní části okna nástroje se zobrazí ovládací prvek hledání s vodoznakem **vyhledávání** a ikonou lupy. Hledání ale ještě nefunguje, protože proces vyhledávání není implementovaný.

## <a name="to-add-the-search-implementation"></a>Přidání implementace vyhledávání
 Pokud povolíte vyhledávání na <xref:Microsoft.VisualStudio.Shell.ToolWindowPane>, jako v předchozím postupu, okno nástroje vytvoří hostitele vyhledávání. Tento hostitel nastavuje a spravuje procesy hledání, které se vždy vyskytují ve vlákně na pozadí. Vzhledem k tomu, že třída <xref:Microsoft.VisualStudio.Shell.ToolWindowPane> spravuje vytváření hostitele vyhledávání a nastavení hledání, potřebujete pouze vytvořit úlohu vyhledávání a zadat metodu hledání. Proces vyhledávání probíhá ve vlákně na pozadí a volání ovládacího prvku okna nástroje se vyskytnou ve vlákně uživatelského rozhraní. Proto je nutné použít metodu [ThreadHelper. Invoke *](https://msdn.microsoft.com/data/ee197798(v=vs.85)) ke správě všech volání, která jste provedli při práci s ovládacím prvkem.

1. Do souboru *TestSearch.cs* přidejte následující direktivy `using`:

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

2. Ve třídě `TestSearch` přidejte následující kód, který provede následující akce:

    - Přepíše metodu <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowSearch.CreateSearch%2A> pro vytvoření úlohy vyhledávání.

    - Přepíše metodu <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowSearch.ClearSearch%2A>, aby obnovila stav textového pole. Tato metoda je volána, když uživatel zruší úkol vyhledávání a když uživatel nastaví nebo zruší nastavení možností nebo filtrů. @No__t_0 i <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowSearch.ClearSearch%2A> jsou volány ve vlákně uživatelského rozhraní. Proto nemusíte přistupovat k textovému poli prostřednictvím metody [ThreadHelper. Invoke *](https://msdn.microsoft.com/data/ee197798(v=vs.85)) .

    - Vytvoří třídu s názvem `TestSearchTask`, která dědí z <xref:Microsoft.VisualStudio.Shell.VsSearchTask>, která poskytuje výchozí implementaci <xref:Microsoft.VisualStudio.Shell.Interop.IVsSearchTask>.

         V `TestSearchTask` konstruktor nastaví soukromé pole, které odkazuje na okno nástroje. Chcete-li poskytnout metodu hledání, přepište metody <xref:Microsoft.VisualStudio.Shell.VsSearchTask.OnStartSearch%2A> a <xref:Microsoft.VisualStudio.Shell.VsSearchTask.OnStopSearch%2A>. @No__t_0 metoda je místo, kde implementujete proces vyhledávání. Tento proces zahrnuje provedení hledání, zobrazení výsledků hledání v textovém poli a volání implementace základní třídy této metody, která oznamuje, že vyhledávání bylo dokončeno.

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

3. Otestujte svou implementaci hledání provedením následujících kroků:

    1. Znovu sestavte projekt a spusťte ladění.

    2. V experimentální instanci aplikace Visual Studio otevřete znovu okno nástroje, do okna hledání zadejte nějaký hledaný text a klikněte na tlačítko **ENTER**.

         Měly by se zobrazit správné výsledky.

## <a name="to-customize-the-search-behavior"></a>Přizpůsobení chování hledání
 Změnou nastavení vyhledávání můžete vytvořit nejrůznější změny v tom, jak se ovládací prvek hledání zobrazí a jak se bude hledání provádět. Můžete například změnit vodoznak (výchozí text, který se zobrazí v poli hledání), minimální a maximální šířka ovládacího prvku hledání a zda se má zobrazit indikátor průběhu. Můžete také změnit bod, ve kterém se výsledky hledání začnou zobrazovat (na vyžádání nebo okamžité hledání) a jestli se má zobrazit seznam podmínek, pro které jste v poslední době prohledali. Úplný seznam nastavení najdete ve třídě <xref:Microsoft.VisualStudio.PlatformUI.SearchSettingsDataSource>.

1. V souboru * TestSearch.cs * přidejte následující kód do třídy `TestSearch`. Tento kód umožňuje okamžité hledání namísto vyhledávání na vyžádání (to znamená, že uživatel nemusí kliknout na tlačítko **ENTER**). Kód přepíše metodu `ProvideSearchSettings` ve třídě `TestSearch`, která je nutná ke změně výchozího nastavení.

    ```csharp
    public override void ProvideSearchSettings(IVsUIDataSource pSearchSettings)
    {
        Utilities.SetValue(pSearchSettings,
            SearchSettingsDataSource.SearchStartTypeProperty.Name,
            (uint)VSSEARCHSTARTTYPE.SST_INSTANT);}
    ```

2. Otestujte nové nastavení tak, že znovu sestavíte řešení a restartujete ladicí program.

     Výsledky hledání se zobrazí pokaždé, když do vyhledávacího pole zadáte nějaký znak.

3. Do metody `ProvideSearchSettings` přidejte následující řádek, který umožňuje zobrazení indikátoru průběhu.

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

     Aby se indikátor průběhu zobrazil, musí být průběh nahlášený. Chcete-li ohlásit průběh, odkomentujte následující kód v metodě `OnStartSearch` `TestSearchTask` třídy:

    ```csharp
    SearchCallback.ReportProgress(this, progress++, (uint)contentArr.GetLength(0));
    ```

4. Chcete-li zpomalit zpracování dostatečně tak, že indikátor průběhu je viditelný, odkomentujte následující řádek v metodě `OnStartSearch` `TestSearchTask` třídy:

    ```csharp
    System.Threading.Thread.Sleep(100);
    ```

5. Otestujte nové nastavení tak, že znovu sestavíte řešení a začnete ladit.

     Indikátor průběhu se zobrazí v okně hledání (jako modrý řádek pod textovým polem hledání) pokaždé, když provedete hledání.

## <a name="to-enable-users-to-refine-their-searches"></a>Umožnění uživatelům Upřesnit jejich hledání
 Uživatelům můžete dovolit Upřesnit jejich hledání pomocí možností, jako je například **rozlišovat velká a malá písmena** nebo **Vyhledat celé slovo**. Možnosti mohou být logická hodnota, která se zobrazí jako zaškrtávací políčka nebo příkazy, které se zobrazí jako tlačítka. V tomto návodu vytvoříte logickou možnost.

1. Do souboru *TestSearch.cs* přidejte následující kód do třídy `TestSearch`. Kód přepíše metodu `SearchOptionsEnum`, která umožňuje, aby implementace vyhledávání zjistila, zda je daná možnost zapnutá nebo vypnutá. Kód v `SearchOptionsEnum` přidá možnost pro párování <xref:Microsoft.VisualStudio.Shell.Interop.IVsEnumWindowSearchOptions> enumerátoru. Možnost rozlišovat velikost písmen je také k dispozici jako vlastnost `MatchCaseOption`.

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

2. V `TestSearchTask` třídy odkomentujte následující řádek v metodě `OnStartSearch`:

    ```csharp
    matchCase = m_toolWindow.MatchCaseOption.Value;
    ```

3. Otestujte možnost:

    1. Sestavte projekt a spusťte ladění. Objeví se experimentální instance.

    2. V okně nástroje klikněte na šipku dolů na pravé straně textového pole.

         Zobrazí se zaškrtávací políčko Rozlišovat **velikost písmen** .

    3. Zaškrtněte políčko Rozlišovat **velká a malá písmena** a pak proveďte několik hledání.

## <a name="to-add-a-search-filter"></a>Přidání vyhledávacího filtru
 Můžete přidat vyhledávací filtry, které uživatelům umožňují upřesnit sadu cílů hledání. Můžete například filtrovat soubory v Průzkumníku souborů podle data, kdy byly naposledy upraveny a jejich přípony názvů souborů. V tomto návodu přidáte filtr jenom pro sudé řádky. Když uživatel zvolí tento filtr, hostitel vyhledávání přidá řetězce, které zadáte do vyhledávacího dotazu. Pak můžete identifikovat tyto řetězce v metodě hledání a odpovídajícím způsobem filtrovat cíle hledání.

1. Do souboru *TestSearch.cs* přidejte následující kód do třídy `TestSearch`. Kód implementuje `SearchFiltersEnum` přidáním <xref:Microsoft.VisualStudio.PlatformUI.WindowSearchSimpleFilter>, který určuje filtrování výsledků hledání tak, aby se zobrazily pouze sudé řádky.

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

     Nyní ovládací prvek hledání zobrazí `Search even lines only` vyhledávacího filtru. Když uživatel zvolí filtr, zobrazí se `lines:"even"` řetězec ve vyhledávacím poli. Další kritéria hledání se mohou objevit ve stejnou dobu jako filtr. Vyhledávací řetězce mohou být zobrazeny před filtrem, za filtrem nebo obojím.

2. V souboru *TestSearch.cs* přidejte následující metody do třídy `TestSearchTask`, která je ve třídě `TestSearch`. Tyto metody podporují metodu `OnStartSearch`, kterou upravíte v dalším kroku.

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

3. Ve třídě `TestSearchTask` aktualizujte metodu `OnStartSearch` pomocí následujícího kódu. Tato změna aktualizuje kód tak, aby podporoval filtr.

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

5. Sestavte projekt a spusťte ladění. V experimentální instanci aplikace Visual Studio otevřete okno nástroje a pak zvolte šipku dolů v ovládacím prvku hledání.

     Políčko Rozlišovat **velikost písmen** a zobrazit pouze filtr na **stejné řádky** .

6. Vyberte filtr.

     Vyhledávací pole obsahuje **řádky: "i"** a zobrazí se následující výsledky:

     2 dobré

     4 dobré

     6

7. Odstraňte `lines:"even"` z vyhledávacího pole, zaškrtněte políčko Rozlišovat **velikost písmen** a potom do vyhledávacího pole zadejte `g`.

     Zobrazí se následující výsledky:

     1 přejít

     2 dobré

     5 nejenom

8. Na pravé straně vyhledávacího pole vyberte X.

     Hledání se vymaže a zobrazí se původní obsah. Je však stále zaškrtnuto políčko Rozlišovat **velikost písmen** .
