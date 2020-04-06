---
title: 'Návod: Zobrazení návrhů žárovek | Dokumenty společnosti Microsoft'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 99e5566d-450e-4660-9bca-454e1c056a02
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 09773e2be81ce51971709db590a07ca9960104fa
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80697476"
---
# <a name="walkthrough-display-light-bulb-suggestions"></a>Návod: Zobrazení návrhů žárovek
Žárovky jsou ikony v editoru Sady Visual Studio, které rozbalí zobrazení sady akcí, například opravy problémů identifikovaných integrovanými analyzátory kódu nebo refaktoringkódu kódu.

 V editorech Visual C# a Visual Basic můžete také použít platformu kompilátoru .NET ("Roslyn") k zápisu a balení vlastních analyzátorů kódu s akcemi, které automaticky zobrazují žárovky. Další informace naleznete v tématu:

- [Postup: Napište diagnostiku a opravu kódu jazyka C#](https://github.com/dotnet/roslyn/wiki/How-To-Write-a-C%23-Analyzer-and-Code-Fix)

- [Postup: Napište diagnostiku a opravu kódu jazyka Visual Basic](https://github.com/dotnet/roslyn/wiki/How-To-Write-a-Visual-Basic-Analyzer-and-Code-Fix)

  Jiné jazyky, jako je například C++ také poskytují žárovky pro některé rychlé akce, jako je například návrh na vytvoření se zakázaným inzerováním implementace této funkce.

  Zde je to, co žárovka vypadá. V projektu jazyka Visual Basic nebo Visual C# se pod názvem proměnné zobrazí červená vlnovka, pokud je neplatná. Pokud najedete myší na neplatný identifikátor, zobrazí se v blízkosti kurzoru žárovka.

  ![Žárovky](../extensibility/media/lightbulb.png "Žárovka")

  Pokud kliknete na šipku dolů u žárovky, zobrazí se sada navrhovaných akcí spolu s náhledem vybrané akce. V tomto případě se zobrazí změny, které jsou provedeny v kódu, pokud provedete akci.

  ![náhled žárovky](../extensibility/media/lightbulbpreview.png "Náhled žárovky")

  Pomocí žárovek můžete poskytnout vlastní navrhované akce. Můžete například poskytnout akce pro přesunutí úvodních složených závorek na nový řádek nebo jejich přesunutí na konec předchozího řádku. Následující návod ukazuje, jak vytvořit žárovku, která se zobrazí na aktuální slovo a má dvě navrhované akce: **Převést na velká písmena** a **převést na malá písmena**.

## <a name="prerequisites"></a>Požadavky
 Počínaje Visual Studio 2015, nenainstalujete Visual Studio SDK ze služby stažení. Je součástí volitelné funkce v nastavení sady Visual Studio. VS SDK můžete také nainstalovat později. Další informace naleznete [v tématu Instalace sady Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="create-a-managed-extensibility-framework-mef-project"></a>Vytvoření projektu spravovaného rámce rozšiřitelnosti (MEF)

1. Vytvořte projekt C# VSIX. (V dialogovém okně **Nový projekt** vyberte možnost **Vizuální C# / Rozšiřitelnost**a potom **v six projectu**.) Pojmenujte `LightBulbTest`řešení .

2. Přidejte do projektu šablonu **položky třídění editoru.** Další informace naleznete [v tématu Vytvoření rozšíření se šablonou položky editoru](../extensibility/creating-an-extension-with-an-editor-item-template.md).

3. Odstraňte existující soubory tříd.

4. Přidejte do projektu následující odkaz a `False`nastavte nastavení Kopírovat **místní** na :

     *Microsoft.VisualStudio.Language.Intellisense*

5. Přidejte nový soubor třídy a pojmenujte jej **LightBulbTest**.

6. Pomocí direktiv přidejte následující příkazy:

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

## <a name="implement-the-light-bulb-source-provider"></a>Implementace poskytovatele zdroje žárovky

1. V *souboru třídy LightBulbTest.cs* odstraňte třídu LightBulbTest. Přidejte třídu s názvem **TestSuggestedActionsSourceProvider,** která implementuje <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSourceProvider>. Exportujte jej s názvem **testovaných navrhovaných akcí** a "text". <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>

    ```csharp
    [Export(typeof(ISuggestedActionsSourceProvider))]
    [Name("Test Suggested Actions")]
    [ContentType("text")]
    internal class TestSuggestedActionsSourceProvider : ISuggestedActionsSourceProvider
    ```

2. Uvnitř třídy zdrojového <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService> zprostředkovatele importujte a přidejte ji jako vlastnost.

    ```csharp
    [Import(typeof(ITextStructureNavigatorSelectorService))]
    internal ITextStructureNavigatorSelectorService NavigatorService { get; set; }
    ```

3. Implementujte <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSourceProvider.CreateSuggestedActionsSource%2A> metodu <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSource> k vrácení objektu. Zdroj je popsán v další části.

    ```csharp
    public ISuggestedActionsSource CreateSuggestedActionsSource(ITextView textView, ITextBuffer textBuffer)
    {
        if (textBuffer == null || textView == null)
        {
            return null;
        }
        return new TestSuggestedActionsSource(this, textView, textBuffer);
    }
    ```

## <a name="implement-the-isuggestedactionsource"></a>Implementace zdroje ISuggestedActionSource
 Navrhovaný zdroj akce je zodpovědný za shromažďování sady navrhovaných akcí a jejich přidání do správného kontextu. V tomto případě kontext je aktuální slovo a navrhované akce jsou **UpperCaseSuggestedAction** a **LowerCaseSuggestedAction**, který je popsán v následující části.

1. Přidejte třídu **TestSuggestedActionsSource,** který implementuje <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSource>.

    ```csharp
    internal class TestSuggestedActionsSource : ISuggestedActionsSource
    ```

2. Přidejte soukromá pole jen pro čtení pro navrhovaného zprostředkovatele zdroje akcí, vyrovnávací paměť textu a zobrazení textu.

    ```csharp
    private readonly TestSuggestedActionsSourceProvider m_factory;
    private readonly ITextBuffer m_textBuffer;
    private readonly ITextView m_textView;
    ```

3. Přidejte konstruktor, který nastaví soukromá pole.

    ```csharp
    public TestSuggestedActionsSource(TestSuggestedActionsSourceProvider testSuggestedActionsSourceProvider, ITextView textView, ITextBuffer textBuffer)
    {
        m_factory = testSuggestedActionsSourceProvider;
        m_textBuffer = textBuffer;
        m_textView = textView;
    }
    ```

4. Přidejte soukromou metodu, která vrací slovo, které je aktuálně pod kurzorem. Následující metoda se dívá na aktuální umístění kurzoru a požádá navigátor struktury textu o rozsah slova. Pokud je kurzor na <xref:Microsoft.VisualStudio.Text.Operations.TextExtent> slovo, je vrácena v out parametr; jinak je `out` `null` parametr a metoda `false`vrátí .

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

5. Implementujte <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSource.HasSuggestedActionsAsync%2A> metodu. Editor volá tuto metodu zjistit, zda chcete zobrazit žárovku. Toto volání se provádí často, například vždy, když kurzor přesune z jedné čáry na druhou, nebo když myši najede myší nad chybovou vlnovkou. Je asynchronní, aby bylo možné pokračovat v jiných operacích s uznamamství, zatímco tato metoda funguje. Ve většině případů je třeba provést některé analýzy a analýzy aktuálnířádek, takže zpracování může nějakou dobu trvat.

     V této implementaci asynchronně získá <xref:Microsoft.VisualStudio.Text.Operations.TextExtent> a určuje, zda je rozsah významný, jako v, zda má nějaký text než mezery.

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

6. Implementujte <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSource.GetSuggestedActions%2A> metodu, která <xref:Microsoft.VisualStudio.Language.Intellisense.SuggestedActionSet> vrací pole objektů, které obsahují různé <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedAction> objekty. Tato metoda se nazývá při rozbalení žárovky.

    > [!WARNING]
    > Měli byste se ujistit, `HasSuggestedActionsAsync()` `GetSuggestedActions()` že implementace a jsou konzistentní; to znamená, `HasSuggestedActionsAsync()` `true`že `GetSuggestedActions()` pokud vrátí , pak by měl mít některé akce k zobrazení. V mnoha `HasSuggestedActionsAsync()` případech se `GetSuggestedActions()`nazývá těsně před , ale to není vždy případ. Například pokud uživatel vyvolá akce žárovky stisknutím tlačítka ( `GetSuggestedActions()` CTRL **+** .) se nazývá pouze.

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

7. Definujte `SuggestedActionsChanged` událost.

    ```csharp
    public event EventHandler<EventArgs> SuggestedActionsChanged;
    ```

8. Chcete-li dokončit implementaci, přidejte implementace pro `Dispose()` metody a. `TryGetTelemetryId()` Nechcete dělat telemetrii, takže `false` stačí vrátit a `Empty`nastavit identifikátor GUID na .

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

## <a name="implement-light-bulb-actions"></a>Implementace akcí s žárovkami

1. V projektu přidejte odkaz na *Microsoft.VisualStudio.Imaging.Interop.14.0.DesignTime.dll* a `False`nastavte Kopírovat **místní** na .

2. Vytvořte dvě třídy, první s názvem `UpperCaseSuggestedAction` a druhou s názvem `LowerCaseSuggestedAction`. Obě třídy implementovat <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedAction>.

    ```csharp
    internal class UpperCaseSuggestedAction : ISuggestedAction
    internal class LowerCaseSuggestedAction : ISuggestedAction
    ```

     Obě třídy jsou stejné <xref:System.String.ToUpper%2A> kromě toho, <xref:System.String.ToLower%2A>že jeden volání a ostatní volání . Následující kroky se týkají pouze velké třídy akce, ale je nutné implementovat obě třídy. Použijte kroky pro implementaci akce velkých písmen jako vzor pro implementaci akce malá písmena.

3. Přidejte následující pomocí direktiv pro tyto třídy:

    ```csharp
    using Microsoft.VisualStudio.Imaging.Interop;
    using System.Windows;
    using System.Windows.Controls;
    using System.Windows.Documents;
    using System.Windows.Media;

    ```

4. Deklarujte sadu soukromých polí.

    ```csharp
    private ITrackingSpan m_span;
    private string m_upper;
    private string m_display;
    private ITextSnapshot m_snapshot;
    ```

5. Přidejte konstruktor, který nastaví pole.

    ```csharp
    public UpperCaseSuggestedAction(ITrackingSpan span)
    {
        m_span = span;
        m_snapshot = span.TextBuffer.CurrentSnapshot;
        m_upper = span.GetText(m_snapshot).ToUpper();
        m_display = string.Format("Convert '{0}' to upper case", span.GetText(m_snapshot));
    }
    ```

6. Implementujte <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedAction.GetPreviewAsync%2A> metodu tak, aby se zobrazil náhled akce.

    ```csharp
    public Task<object> GetPreviewAsync(CancellationToken cancellationToken)
    {
        var textBlock = new TextBlock();
        textBlock.Padding = new Thickness(5);
        textBlock.Inlines.Add(new Run() { Text = m_upper });
        return Task.FromResult<object>(textBlock);
    }
    ```

7. Implementujte <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedAction.GetActionSetsAsync%2A> metodu tak, <xref:Microsoft.VisualStudio.Language.Intellisense.SuggestedActionSet> aby vrátí prázdný výčet.

    ```csharp
    public Task<IEnumerable<SuggestedActionSet>> GetActionSetsAsync(CancellationToken cancellationToken)
    {
        return Task.FromResult<IEnumerable<SuggestedActionSet>>(null);
    }
    ```

8. Implementujte vlastnosti následujícím způsobem.

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

9. Implementujte <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedAction.Invoke%2A> metodu nahrazením textu v rozsahu jeho ekvivalentem velkých písmen.

    ```csharp
    public void Invoke(CancellationToken cancellationToken)
    {
        m_span.TextBuffer.Replace(m_span.GetSpan(m_snapshot), m_upper);
    }
    ```

    > [!WARNING]
    > Akce žárovky **Invoke** metoda se neočekává, že zobrazit uI. Pokud vaše akce vyvolá nové uhlavní nastavení (například náhled nebo dialogové okno výběru), nezobrazujte ui přímo z metody **Invoke,** ale místo toho naplánujte zobrazení vašeho hlavního nastavení po návratu z **Invoke**.

10. Chcete-li dokončit implementaci, přidejte metody `Dispose()` a. `TryGetTelemetryId()`

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

11. Nezapomeňte `LowerCaseSuggestedAction` udělat totéž pro změnu textu zobrazení na{0}"Převést ' ' <xref:System.String.ToUpper%2A> na <xref:System.String.ToLower%2A>malá písmena " a volání .

## <a name="build-and-test-the-code"></a>Sestavení a testování kódu
 Chcete-li otestovat tento kód, vytvořte řešení LightBulbTest a spusťte jej v instanci Experimental.

1. Sestavte řešení.

2. Při spuštění tohoto projektu v ladicím programu je spuštěna druhá instance sady Visual Studio.

3. Vytvořte textový soubor a zadejte nějaký text. Vlevo od textu byste měli vidět žárovku.

     ![otestovat žárovku](../extensibility/media/testlightbulb.png "TestLIghtBulb")

4. Namiřte na žárovku. Měl bys vidět šipku dolů.

5. Po klepnutí na žárovku by se měly zobrazit dvě navrhované akce spolu s náhledem vybrané akce.

     ![zkušební žárovka, rozšířená](../extensibility/media/testlightbulbexpanded.gif "TestLIghtBulbExpanded")

6. Pokud klepnete na první akci, veškerý text v aktuálním slově by měl být převeden na velká písmena. Pokud klepnete na druhou akci, veškerý text by měl být převeden na malá písmena.
