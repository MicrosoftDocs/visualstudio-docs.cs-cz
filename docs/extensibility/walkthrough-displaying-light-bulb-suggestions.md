---
title: 'Návod: zobrazení návrhů na žárovku | Microsoft Docs'
description: Naučte se, jak vytvořit žárovku v editoru sady Visual Studio, který se zobrazí na aktuálním slově a má dvě navrhované akce pomocí tohoto návodu.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: 99e5566d-450e-4660-9bca-454e1c056a02
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: e1c906b96f3bd20b72cf2b5eca92190e0ad42916
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99931289"
---
# <a name="walkthrough-display-light-bulb-suggestions"></a>Návod: zobrazení návrhů žárovky
Žárovky jsou ikony v editoru sady Visual Studio, které se rozbalí k zobrazení sady akcí, například opravy pro problémy identifikované vestavěnými analyzátory kódu nebo refaktoringu kódu.

 V editorech Visual C# a Visual Basic můžete také pomocí .NET Compiler Platform ("Roslyn") zapisovat a zabalit vlastní analyzátory kódu s akcemi, které automaticky zobrazují žárovky. Další informace naleznete v tématu:

- [Postupy: zápis diagnostiky kódu a opravy kódu v jazyce C#](https://github.com/dotnet/roslyn/blob/master/docs/wiki/How-To-Write-a-C%23-Analyzer-and-Code-Fix.md)

- [Postupy: zápis diagnostiky Visual Basic a opravy kódu](https://github.com/dotnet/roslyn/blob/master/docs/wiki/How-To-Write-a-Visual-Basic-Analyzer-and-Code-Fix.md)

  Jiné jazyky, jako je například C++, také poskytují žárovky pro některé rychlé akce, jako je například návrh k vytvoření zástupné implementace této funkce.

  To vypadá jako žárovka. V projektu Visual Basic nebo Visual C# se v názvu proměnné zobrazí červená vlnovka, pokud je neplatná. Pokud překročíte ukazatel myši na neplatný identifikátor, zobrazí se v blízkosti kurzoru žárovka.

  ![žárovka](../extensibility/media/lightbulb.png "Žárovky")

  Pokud kliknete na šipku dolů u žárovky, zobrazí se sada navrhovaných akcí spolu s náhledem vybrané akce. V tomto případě se v případě provedení akce zobrazí změny provedené v kódu.

  ![náhled návrhů](../extensibility/media/lightbulbpreview.png "LightBulbPreview")

  K poskytnutí vlastních navrhovaných akcí můžete použít žárovky. Můžete například zadat akce pro přesunutí počátečních složených závorek na nový řádek nebo jejich přesunutí na konec předcházejícího řádku. Následující návod ukazuje, jak vytvořit žárovku, která se zobrazí na aktuálním slově a má dvě navrhované akce: **převést na velká písmena** a **převést na malá písmena**.

## <a name="prerequisites"></a>Požadavky
 Od sady Visual Studio 2015 nenainstalujete sadu Visual Studio SDK z webu Stažení softwaru. V instalačním programu sady Visual Studio je zahrnutý jako volitelná funkce. Sadu VS SDK můžete také nainstalovat později. Další informace najdete v tématu [instalace sady Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="create-a-managed-extensibility-framework-mef-project"></a>Vytvořit projekt Managed Extensibility Framework (MEF)

1. Vytvoří projekt VSIX v jazyce C#. (V dialogovém okně **Nový projekt** vyberte **Visual C#/rozšiřitelnost** a potom **projekt VSIX**.) Pojmenujte řešení `LightBulbTest` .

2. Přidejte do projektu šablonu položky **klasifikátoru editoru** . Další informace naleznete v tématu [Vytvoření rozšíření pomocí šablony položky editoru](../extensibility/creating-an-extension-with-an-editor-item-template.md).

3. Odstraňte existující soubory třídy.

4. Do projektu přidejte následující odkaz a nastavte **Kopírovat místně** na `False` :

     *Microsoft. VisualStudio. Language. IntelliSense*

5. Přidejte nový soubor třídy a pojmenujte ho **LightBulbTest**.

6. Přidejte následující direktivy using:

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

1. V souboru třídy *LightBulbTest.cs* odstraňte třídu LightBulbTest. Přidejte třídu s názvem **TestSuggestedActionsSourceProvider** , která implementuje <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSourceProvider> . Exportujte s názvem **navrhované akce testu** a <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> "text".

    ```csharp
    [Export(typeof(ISuggestedActionsSourceProvider))]
    [Name("Test Suggested Actions")]
    [ContentType("text")]
    internal class TestSuggestedActionsSourceProvider : ISuggestedActionsSourceProvider
    ```

2. Uvnitř třídy poskytovatele zdroje importujte <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService> a přidejte ho jako vlastnost.

    ```csharp
    [Import(typeof(ITextStructureNavigatorSelectorService))]
    internal ITextStructureNavigatorSelectorService NavigatorService { get; set; }
    ```

3. Implementujte <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSourceProvider.CreateSuggestedActionsSource%2A> metodu pro vrácení <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSource> objektu. Zdroj je popsán v následující části.

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

## <a name="implement-the-isuggestedactionsource"></a>Implementace rozhraní ISuggestedActionSource
 Navrhovaný zdroj akce zodpovídá za shromáždění sady navrhovaných akcí a jejich přidání do správného kontextu. V tomto případě je kontext aktuální slovo a navrhované akce jsou **UpperCaseSuggestedAction** a **LowerCaseSuggestedAction**, které jsou popsány v následující části.

1. Přidejte třídu **TestSuggestedActionsSource** , která implementuje <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSource> .

    ```csharp
    internal class TestSuggestedActionsSource : ISuggestedActionsSource
    ```

2. Přidat soukromá pole, která jsou jen pro čtení pro navrhovaný zprostředkovatel zdroje akce, vyrovnávací paměť textu a textové zobrazení.

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

4. Přidejte soukromou metodu, která vrátí slovo, které je aktuálně pod kurzorem. Následující metoda prohledá aktuální umístění kurzoru a požádá navigátor textové struktury o rozsah slova. Pokud je kurzor na slovo, <xref:Microsoft.VisualStudio.Text.Operations.TextExtent> je vrácen v parametru out. v opačném případě je `out` parametr `null` a metoda vrátí `false` .

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

5. Implementujte <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSource.HasSuggestedActionsAsync%2A> metodu. Editor volá tuto metodu a zjistí, zda se má zobrazit žárovka. Toto volání je často prováděno například pokaždé, když se kurzor přesune z jednoho řádku na druhý nebo když ukazatel myši setrvá na chybové vlnovce. Je asynchronní, aby bylo možné provádět jiné operace uživatelského rozhraní v době, kdy tato metoda funguje. Ve většině případů tato metoda potřebuje provést analýzu a analýzu aktuálního řádku, takže zpracování může nějakou dobu trvat.

     V této implementaci asynchronně získá <xref:Microsoft.VisualStudio.Text.Operations.TextExtent> a určí, zda je rozsah významný, jako v, zda má nějaký text jiný než prázdný znak.

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

6. Implementujte <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedActionsSource.GetSuggestedActions%2A> metodu, která vrací pole <xref:Microsoft.VisualStudio.Language.Intellisense.SuggestedActionSet> objektů, které obsahují různé <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedAction> objekty. Tato metoda je volána při rozbalení žárovky.

    > [!WARNING]
    > Měli byste se ujistit, že implementace `HasSuggestedActionsAsync()` a `GetSuggestedActions()` jsou konzistentní; to znamená, že pokud se `HasSuggestedActionsAsync()` vrátí `true` , pak `GetSuggestedActions()` by měly mít nějaké akce, které se mají zobrazit. V mnoha případech `HasSuggestedActionsAsync()` je volána těsně před `GetSuggestedActions()` , ale to není vždy případ. Například pokud uživatel vyvolá akce žárovky pomocí klávesy (**CTRL +** .), `GetSuggestedActions()` je volána pouze.

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

8. K dokončení implementace přidejte implementace pro `Dispose()` `TryGetTelemetryId()` metody a. Nechcete provádět telemetrii, proto stačí vrátit `false` a nastavit identifikátor GUID na `Empty` .

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

## <a name="implement-light-bulb-actions"></a>Implementace akcí žárovky

1. V projektu přidejte odkaz na *Microsoft.VisualStudio.Imaging.Interop.14.0.DesignTime.dll* a nastavte **Kopírovat místně** na `False` .

2. Vytvořte dvě třídy, první pojmenovaný `UpperCaseSuggestedAction` a druhý s názvem `LowerCaseSuggestedAction` . Obě třídy implementují <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedAction> .

    ```csharp
    internal class UpperCaseSuggestedAction : ISuggestedAction
    internal class LowerCaseSuggestedAction : ISuggestedAction
    ```

     Obě třídy jsou podobné s tím rozdílem, že jedno volání <xref:System.String.ToUpper%2A> a další volání <xref:System.String.ToLower%2A> . Následující postup pokrývá pouze velké třídy akcí, ale je nutné implementovat obě třídy. Použijte postup pro implementaci velkých a malých písmen jako vzor pro implementaci akce s malými písmeny.

3. Přidejte následující direktivy using pro tyto třídy:

    ```csharp
    using Microsoft.VisualStudio.Imaging.Interop;
    using System.Windows;
    using System.Windows.Controls;
    using System.Windows.Documents;
    using System.Windows.Media;

    ```

4. Deklarovat sadu privátních polí

    ```csharp
    private ITrackingSpan m_span;
    private string m_upper;
    private string m_display;
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

6. Implementujte <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedAction.GetPreviewAsync%2A> metodu tak, aby se zobrazila náhled akce.

    ```csharp
    public Task<object> GetPreviewAsync(CancellationToken cancellationToken)
    {
        var textBlock = new TextBlock();
        textBlock.Padding = new Thickness(5);
        textBlock.Inlines.Add(new Run() { Text = m_upper });
        return Task.FromResult<object>(textBlock);
    }
    ```

7. Implementujte <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedAction.GetActionSetsAsync%2A> metodu tak, aby vrátila prázdný <xref:Microsoft.VisualStudio.Language.Intellisense.SuggestedActionSet> výčet.

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
    public string DisplayText
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

9. Implementujte <xref:Microsoft.VisualStudio.Language.Intellisense.ISuggestedAction.Invoke%2A> metodu tak, že nahradíte text v rozpětí velkými ekvivalenty.

    ```csharp
    public void Invoke(CancellationToken cancellationToken)
    {
        m_span.TextBuffer.Replace(m_span.GetSpan(m_snapshot), m_upper);
    }
    ```

    > [!WARNING]
    > Metoda **vyvolání** akce žárovky se neočekává pro zobrazení uživatelského rozhraní. Pokud vaše akce vyvolá nové uživatelské rozhraní (například dialogové okno náhledu nebo výběr), nezobrazujte uživatelské rozhraní přímo z metody **Invoke** , ale místo toho Naplánujte zobrazení uživatelského rozhraní po návratu z **vyvolání**.

10. K dokončení implementace přidejte `Dispose()` `TryGetTelemetryId()` metody a.

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

11. Nezapomeňte to samé udělat pro `LowerCaseSuggestedAction` změnu zobrazovaného textu na "převést" {0} na malý případ "a zavolat <xref:System.String.ToUpper%2A> na <xref:System.String.ToLower%2A> .

## <a name="build-and-test-the-code"></a>Sestavení a testování kódu
 Chcete-li otestovat tento kód, sestavte řešení LightBulbTest a spusťte ho v experimentální instanci.

1. Sestavte řešení.

2. Při spuštění tohoto projektu v ladicím programu se spustí druhá instance sady Visual Studio.

3. Vytvořte textový soubor a zadejte nějaký text. Nalevo od textu by se měla zobrazit žárovka.

     ![testování žárovky](../extensibility/media/testlightbulb.png "TestLIghtBulb")

4. Ukažte v žárovkě. Měla by se zobrazit šipka dolů.

5. Po kliknutí na žárovku by se měly zobrazit dvě navrhované akce spolu s náhledem vybrané akce.

     ![žárovka testu, rozbaleno](../extensibility/media/testlightbulbexpanded.gif "TestLIghtBulbExpanded")

6. Pokud kliknete na první akci, veškerý text v aktuálním slově by se měl převést na velká písmena. Pokud kliknete na druhou akci, veškerý text by měl být převeden na malá písmena.
