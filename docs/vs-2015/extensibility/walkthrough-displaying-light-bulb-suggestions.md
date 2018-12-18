---
title: 'Návod: Zobrazení návrhů | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 99e5566d-450e-4660-9bca-454e1c056a02
caps.latest.revision: 17
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: a7e5bf7ad795615e70e990dd29c05f5efe3a1c78
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51781098"
---
# <a name="walkthrough-displaying-light-bulb-suggestions"></a>Návod: Zobrazení návrhů v podobě žárovky
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Ikony žárovky jsou ikony používané v editoru sady Visual Studio, které rozbalí a zobrazí sadu akcí, například opravy problémů, které jsou identifikované analyzátorů integrované kódu a refaktoring kódu.  
  
 V editoru Visual C# a Visual Basic také můžete platformě kompilátoru .NET ("Roslyn") pro zápis a balíček vlastních analyzátorů kódu s akcemi, které se automaticky zobrazí návrhy. Další informace naleznete v tématu:  
  
- [Postupy: Zápis diagnostiky jazyka C# a oprava kódu](https://github.com/dotnet/roslyn/wiki/How-To-Write-a-C%23-Analyzer-and-Code-Fix)  
  
- [Postupy: Zápis diagnostiky jazyka Visual Basic a oprava kódu](https://github.com/dotnet/roslyn/wiki/How-To-Write-a-Visual-Basic-Analyzer-and-Code-Fix)  
  
  Dalších jazycích, například C++ také poskytují návrhy pro některé rychlé akce, jako je návrh na vytvoření zástupné procedury implementace této funkce.  
  
  Zde je, jak vypadá žárovky. V projektu jazyka Visual Basic nebo Visual C# zobrazí červená vlnovka za název proměnné, když je neplatný. Když myší neplatný identifikátor se zobrazí žárovka téměř kurzor.  
  
  ![žárovka](../extensibility/media/lightbulb.png "žárovky")  
  
  Pokud kliknete na šipku dolů ve žárovky, se zobrazí sada doporučené akce, spolu s náhled vybrané akce. V tomto případě zobrazuje změny, které se provádí do kódu, v případě, že provede akci.  
  
  ![Náhled návrhů](../extensibility/media/lightbulbpreview.png "LightBulbPreview")  
  
  Ikony žárovky můžete zadat vlastní doporučené akce. Například je možné zadat akce, které chcete přesunout otevření složené závorky na nový řádek nebo je přesunout na konec objektu na každém řádku. Následující návod ukazuje, jak vytvořit žárovky, který se zobrazí na aktuální slovo a má dvě navrhovaných akcí: **převést na velká písmena** a **převést na malá písmena**.  
  
## <a name="prerequisites"></a>Požadavky  
 Spouští se v sadě Visual Studio 2015, nenainstalujete sadu Visual Studio SDK ze služby Stažení softwaru. Je zahrnut jako volitelná funkce v instalačním programu sady Visual Studio. VS SDK můžete také nainstalovat později. Další informace najdete v tématu [instalace sady Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="creating-a-managed-extensibility-framework-mef-project"></a>Vytvoření projektu Managed Extensibility Framework (MEF)  
  
1.  Vytvořte projekt VSIX C#. (V **nový projekt** dialogového okna, vyberte **Visual C# / rozšíření**, pak **projekt VSIX**.) Pojmenujte řešení `LightBulbTest`.  
  
2.  Přidat **Editor třídění** šablonu položky projektu. Další informace najdete v tématu [vytváření rozšíření pomocí šablony položky editoru](../extensibility/creating-an-extension-with-an-editor-item-template.md).  
  
3.  Odstraníte existující soubory tříd.  
  
4.  Přidejte následující odkaz na projekt a nastavte **Kopírovat místně** k `False`:  
  
     Microsoft.VisualStudio.Language.Intellisense  
  
5.  Přidejte nový soubor třídy a pojmenujte ho **LightBulbTest**.  
  
6.  Přidejte následující příkazy using:  
  
    ```csharp  
    using System;  
    using System.Linq;  
    using System.Collections.Generic;  
    using System.Threading.Tasks;  
    using Microsoft.VisualStudio.Language.Intellisense;  
    using Microsoft.VisualStudio.Text;  
    using Microsoft.VisualStudio.Text.Editor;  
    using Microsoft.VisualStudio.Text.Operations;  
    using Microsoft.VisualStudio.Utilities;  
    using System.ComponentModel.Composition;  
    using System.Threading;  
  
    ```  
  
## <a name="implementing-the-light-bulb-source-provider"></a>Implementace zprostředkovatele návrhy zdroje  
  
1.  V souboru třídy LightBulbTest.cs odstraní LightBulbTest třídu. Přidejte třídu pojmenovanou **TestSuggestedActionsSourceProvider** , který implementuje <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSourceProvider>. Export s názvem **navrhované akce testu** a <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> "text".  
  
    ```csharp  
    [Export(typeof(ISuggestedActionsSourceProvider))]  
    [Name("Test Suggested Actions")]  
    [ContentType("text")]  
    internal class TestSuggestedActionsSourceProvider : ISuggestedActionsSourceProvider  
    ```  
  
2.  Uvnitř třídy zprostředkovatele zdroje, importovat <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService> a přidejte ho jako vlastnost.  
  
    ```csharp  
    [Import(typeof(ITextStructureNavigatorSelectorService))]  
    internal ITextStructureNavigatorSelectorService NavigatorService { get; set; }  
    ```  
  
3.  Implementace <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSourceProvider.CreateSuggestedActionsSource%2A> metodu pro návrat <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSource> objektu. Zdroj v další části se budeme zabývat.  
  
    ```csharp  
    public ISuggestedActionsSource CreateSuggestedActionsSource(ITextView textView, ITextBuffer textBuffer)  
    {  
        if (textBuffer == null && textView == null)  
        {  
            return null;  
        }  
        return new TestSuggestedActionsSource(this, textView, textBuffer);  
    }  
    ```  
  
## <a name="implementing-the-isuggestedactionsource"></a>Implementace ISuggestedActionSource  
 Navrhované akce zdroje je zodpovědná za shromažďování sadu doporučené akce a je přidali ve správném kontextu. V tomto případě se kontext aktuálního slova a doporučené akce jsou **UpperCaseSuggestedAction** a **LowerCaseSuggestedAction**, které se budeme zabývat v následující části.  
  
1.  Přidejte třídu **TestSuggestedActionsSource** , který implementuje <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSource>.  
  
    ```csharp  
    internal class TestSuggestedActionsSource : ISuggestedActionsSource  
    ```  
  
2.  Přidáte soukromé pole jen pro čtení pro zprostředkovatele zdrojového navrhovanou akci, textovou vyrovnávací paměť a zobrazení textu.  
  
    ```csharp  
    private readonly TestSuggestedActionsSourceProvider m_factory;  
    private readonly ITextBuffer m_textBuffer;  
    private readonly ITextView m_textView;  
    ```  
  
3.  Přidáte konstruktor, který nastaví privátní pole.  
  
    ```csharp  
    public TestSuggestedActionsSource(TestSuggestedActionsSourceProvider testSuggestedActionsSourceProvider, ITextView textView, ITextBuffer textBuffer)  
    {  
        m_factory = testSuggestedActionsSourceProvider;  
        m_textBuffer = textBuffer;  
        m_textView = textView;  
    }  
    ```  
  
4.  Přidejte privátní metodu, která vrátí slova, která je teď pod kurzorem. Následující metoda vypadá na aktuální pozici kurzoru a vyzve k zadání rozsahu slovo Navigátor struktury textu. Pokud je kurzor na slovo, <xref:Microsoft.VisualStudio.Text.Operations.TextExtent> je vrácený v parametru out; v opačném případě `out` parametr `null` a metoda vrátí `false`.  
  
    ```csharp  
    private bool TryGetWordUnderCaret(out TextExtent wordExtent)  
    {  
        ITextCaret caret = m_textView.Caret;  
        SnapshotPoint point;  
  
        if (caret.Position.BufferPosition > 0)  
        {  
            point = caret.Position.BufferPosition - 1;  
        }  
        else  
        {  
            wordExtent = default(TextExtent);  
            return false;  
        }  
  
        ITextStructureNavigator navigator = m_factory.NavigatorService.GetTextStructureNavigator(m_textBuffer);  
  
        wordExtent = navigator.GetExtentOfWord(point);  
        return true;  
    }  
    ```  
  
5.  Implementace <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSource.HasSuggestedActionsAsync%2A> metody. Editor volá tuto metodu a zjistěte, jestli se mají zobrazovat žárovky. Toto je provedeno volání poměrně často, například pokaždé, když se kurzor přesune z jeden řádek do jiného, nebo po umístění ukazatele myši nad vlnovku k chybě. Je asynchronní, aby bylo možné povolit další operace uživatelského rozhraní vykonávat, zatímco tato metoda funguje. Ve většině případů tuto metodu je potřeba provést některé analýzy a analýzy aktuálního řádku takže zpracování může nějakou dobu trvat.  
  
     V naší implementaci asynchronně získá <xref:Microsoft.VisualStudio.Text.Operations.TextExtent> a určuje, zda v rozsahu je důležité, to znamená, zda má nějaký text jiné než prázdné znaky.  
  
    ```csharp  
    public Task<bool> HasSuggestedActionsAsync(ISuggestedActionCategorySet requestedActionCategories, SnapshotSpan range, CancellationToken cancellationToken)  
    {  
        return Task.Factory.StartNew(() =>  
        {  
            TextExtent extent;  
            if (TryGetWordUnderCaret(out extent))  
            {  
                // don't display the action if the extent has whitespace  
                return extent.IsSignificant;  
              }  
            return false;  
        });  
    }  
    ```  
  
6.  Implementace <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSource.GetSuggestedActions%2A> metodu, která vrací pole <xref:Microsoft.VisualStudio.Language.Intellisense.SuggestedActionSet> objektů, které obsahují různé <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedAction> objekty. Tato metoda je volána při rozbalení žárovky.  
  
    > [!WARNING]
    >  Ujistěte se, že implementace `HasSuggestedActionsAsync()` a `GetSuggestedActions()` jsou konzistentní vzhledem k aplikacím; který je, pokud `HasSuggestedActionsAsync()` vrátí `true`, pak `GetSuggestedActions()` by měl mít některé akce pro zobrazení. V mnoha případech `HasSuggestedActionsAsync()` je volána těsně před `GetSuggestedActions()`, ale není to vždy. Například, pokud uživatel vyvolá akce žárovky stisknutím kombinace kláves (CTRL +.) pouze `GetSuggestedActions()` je volána.  
  
    ```csharp  
    public IEnumerable<SuggestedActionSet> GetSuggestedActions(ISuggestedActionCategorySet requestedActionCategories, SnapshotSpan range, CancellationToken cancellationToken)  
    {  
        TextExtent extent;  
        if (TryGetWordUnderCaret(out extent) && extent.IsSignificant)  
        {  
            ITrackingSpan trackingSpan = range.Snapshot.CreateTrackingSpan(extent.Span, SpanTrackingMode.EdgeInclusive);  
            var upperAction = new UpperCaseSuggestedAction(trackingSpan);  
            var lowerAction = new LowerCaseSuggestedAction(trackingSpan);  
            return new SuggestedActionSet[] { new SuggestedActionSet(new ISuggestedAction[] { upperAction, lowerAction }) };  
        }  
        return Enumerable.Empty<SuggestedActionSet>();  
    }   
    ```  
  
7.  Definování `SuggestedActionsChanged` událostí.  
  
    ```csharp  
    public event EventHandler<EventArgs> SuggestedActionsChanged;  
    ```  
  
8.  K dokončení provádění, přidání implementace `Dispose()` a `TryGetTelemetryId()` metody. Nechceme telemetrická data, tak, aby se vrátí false a nastavit na prázdný identifikátor GUID.  
  
    ```csharp  
    public void Dispose()  
    {  
    }  
  
    public bool TryGetTelemetryId(out Guid telemetryId)  
    {  
        // This is a sample provider and doesn't participate in LightBulb telemetry  
        telemetryId = Guid.Empty;  
        return false;  
    }  
    ```  
  
## <a name="implementing-light-bulb-actions"></a>Provádění akcí žárovky  
  
1.  V projektu přidejte odkaz na Microsoft.VisualStudio.Imaging.Interop.14.0.DesignTime.dll a nastavte **Kopírovat místně** k `False`.  
  
2.  Vytvořte dvě třídy s názvem první `UpperCaseSuggestedAction` a druhé s názvem `LowerCaseSuggestedAction`. Implementovat obě třídy <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedAction>.  
  
    ```csharp  
    internal class UpperCaseSuggestedAction : ISuggestedAction   
    internal class LowerCaseSuggestedAction : ISuggestedAction  
    ```  
  
     Obě třídy jsou stejné s tím rozdílem, že jeden volá <xref:System.String.ToUpper%2A> a jiných volání <xref:System.String.ToLower%2A>. Následujících krocích se dozvíte pouze třídu velká akce, ale je nutné implementovat obě třídy. Pomocí postupu pro implementaci velká akce jako vzor pro implementování malá akce.  
  
3.  Přidejte následující příkazy using pro tyto třídy:  
  
    ```csharp  
    using Microsoft.VisualStudio.Imaging.Interop;  
    using System.Windows;  
    using System.Windows.Controls;  
    using System.Windows.Documents;  
    using System.Windows.Media;  
  
    ```  
  
4.  Deklarujte sadu privátní pole.  
  
    ```csharp  
    private ITrackingSpan m_span;  
    private string m_upper;  
    private string m_display;  
    private ITextSnapshot m_snapshot;  
    ```  
  
5.  Přidáte konstruktor, který nastaví pole.  
  
    ```csharp  
    public UpperCaseSuggestedAction(ITrackingSpan span)  
    {  
        m_span = span;  
        m_snapshot = span.TextBuffer.CurrentSnapshot;  
        m_upper = span.GetText(m_snapshot).ToUpper();  
        m_display = string.Format("Convert '{0}' to upper case", span.GetText(m_snapshot));  
    }  
    ```  
  
6.  Implementace <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedAction.GetPreviewAsync%2A> metodu tak, že se zobrazí náhled akcí.  
  
    ```csharp  
    public Task<object> GetPreviewAsync(CancellationToken cancellationToken)  
    {  
        var textBlock = new TextBlock();  
        textBlock.Padding = new Thickness(5);  
        textBlock.Inlines.Add(new Run() { Text = m_upper });  
        return Task.FromResult<object>(textBlock);  
    }  
    ```  
  
7.  Implementace <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedAction.GetActionSetsAsync%2A> metodu tak, že vrátí prázdnou <xref:Microsoft.VisualStudio.Language.Intellisense.SuggestedActionSet> výčtu.  
  
    ```csharp  
    public Task<IEnumerable<SuggestedActionSet>> GetActionSetsAsync(CancellationToken cancellationToken)  
    {  
        return Task.FromResult<IEnumerable<SuggestedActionSet>>(null);  
    }  
    ```  
  
8.  Implementace vlastnosti následujícím způsobem.  
  
    ```csharp  
    public bool HasActionSets  
    {  
        get { return false; }  
    }  
    public string DisplayText  
    {  
        get { return m_display; }  
    }  
    public ImageMoniker IconMoniker  
    {  
       get { return default(ImageMoniker); }  
    }  
    public string IconAutomationText  
    {  
        get  
        {  
            return null;  
        }  
    }  
    public string InputGestureText  
    {  
        get  
        {  
            return null;  
        }  
    }  
    public bool HasPreview  
    {  
        get { return true; }  
    }  
    ```  
  
9. Implementace <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedAction.Invoke%2A> metodu nahrazením text v rozsahu ekvivalentem velká písmena.  
  
    ```csharp  
    public void Invoke(CancellationToken cancellationToken)  
    {  
        m_span.TextBuffer.Replace(m_span.GetSpan(m_snapshot), m_upper);  
    }  
    ```  
  
    > [!WARNING]
    >  Akce žárovky **Invoke** metoda neočekává se zobrazit uživatelské rozhraní.  Pokud vaše akce vyvolali nové uživatelské rozhraní (třeba ve verzi preview nebo výběr dialogové okno), nezobrazují přímo v rámci uživatelského rozhraní **Invoke** metoda, ale místo toho naplánovat zobrazit uživatelské rozhraní po návratu z **Invoke**.  
  
10. K dokončení provádění, přidejte `Dispose()` a `TryGetTelemetryId()` metody.  
  
    ```csharp  
    public void Dispose()  
    {  
    }  
  
    public bool TryGetTelemetryId(out Guid telemetryId)  
    {  
        // This is a sample action and doesn't participate in LightBulb telemetry  
        telemetryId = Guid.Empty;  
        return false;  
    }  
    ```  
  
11. Nezapomeňte stejnou věc udělat `LowerCaseSuggestedAction` změna zobrazovaný text "převést"{0}"na malá písmena" a volání <xref:System.String.ToUpper%2A> k <xref:System.String.ToLower%2A>.  
  
## <a name="building-and-testing-the-code"></a>Vytváření a testování kódu  
 K otestování tohoto kódu sestavte řešení LightBulbTest a spusťte v experimentální instanci.  
  
1.  Sestavte řešení.  
  
2.  Při spuštění tohoto projektu v ladicím programu, je vytvořena instance druhou instanci aplikace Visual Studio.  
  
3.  Vytvořte textový soubor a zadejte nějaký text. Měli byste vidět žárovky vlevo od textu.  
  
     ![testování žárovky](../extensibility/media/testlightbulb.png "TestLIghtBulb")  
  
4.  Přejděte na žárovky. Měli byste vidět šipku dolů.  
  
5.  Po kliknutí na žárovku dvě doporučené akce má být zobrazena, společně s verzí preview rozhraní vybrané akce.  
  
     ![testování žárovky rozšířit](../extensibility/media/testlightbulbexpanded.gif "TestLIghtBulbExpanded")  
  
6.  Pokud kliknete na první akci, veškerý text v aktuálního slova mají být převedeny na velká písmena. Pokud kliknete na druhou akci, veškerý text mají být převedeny na malá písmena.

