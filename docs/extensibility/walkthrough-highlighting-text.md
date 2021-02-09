---
title: 'Návod: zvýraznění textu | Microsoft Docs'
description: Naučte se, jak zvýraznit všechny výskyty aktuálního slova v textovém souboru přidáním vizuálních efektů do editoru v tomto návodu.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- editors [Visual Studio SDK], new - highlight text
ms.assetid: 64b772ad-4392-42e9-a237-5137f0384bf0
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 95bc250219c59d4db21fcb086cdf43e0ba7800e3
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99838627"
---
# <a name="walkthrough-highlight-text"></a>Návod: zvýraznění textu
Můžete přidat různé vizuální efekty do editoru vytvořením částí komponenty Managed Extensibility Framework (MEF). Tento návod ukazuje, jak zvýraznit všechny výskyty aktuálního slova v textovém souboru. Pokud se v textovém souboru vyskytne slovo více než jednou, a umístíte blikající kurzor do jednoho výskytu, zvýrazní se všechny výskyty.

## <a name="prerequisites"></a>Požadavky
 Od sady Visual Studio 2015 nenainstalujete sadu Visual Studio SDK z webu Stažení softwaru. V instalačním programu sady Visual Studio je zahrnutý jako volitelná funkce. Sadu VS SDK můžete také nainstalovat později. Další informace najdete v tématu [instalace sady Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="create-a-mef-project"></a>Vytvořit projekt MEF

1. Vytvoří projekt VSIX v jazyce C#. (V dialogovém okně **Nový projekt** vyberte **Visual C#/rozšiřitelnost** a potom **projekt VSIX**.) Pojmenujte řešení `HighlightWordTest` .

2. Přidejte do projektu šablonu položky klasifikátoru editoru. Další informace naleznete v tématu [Vytvoření rozšíření pomocí šablony položky editoru](../extensibility/creating-an-extension-with-an-editor-item-template.md).

3. Odstraňte existující soubory třídy.

## <a name="define-a-textmarkertag"></a>Definovat TextMarkerTag
 První krok zvýraznění textu je podtřídou <xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag> a definuje jeho vzhled.

### <a name="to-define-a-textmarkertag-and-a-markerformatdefinition"></a>Definování TextMarkerTag a MarkerFormatDefinition

1. Přidejte soubor třídy a pojmenujte ho **HighlightWordTag**.

2. Přidejte následující odkazy:

    1. Microsoft. VisualStudio. CoreUtility

    2. Microsoft. VisualStudio. text. data

    3. Microsoft. VisualStudio. text. Logic

    4. Microsoft. VisualStudio. text. UI

    5. Microsoft. VisualStudio. text. UI. WPF

    6. System. ComponentModel. složení

    7. Prezentace. Core

    8. Presentation. Framework

3. Importujte následující obory názvů.

    ```csharp
    using System;
    using System.Collections.Generic;
    using System.ComponentModel.Composition;
    using System.Linq;
    using System.Threading;
    using Microsoft.VisualStudio.Text;
    using Microsoft.VisualStudio.Text.Classification;
    using Microsoft.VisualStudio.Text.Editor;
    using Microsoft.VisualStudio.Text.Operations;
    using Microsoft.VisualStudio.Text.Tagging;
    using Microsoft.VisualStudio.Utilities;
    using System.Windows.Media;
    ```

4. Vytvořte třídu, která dědí z <xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag> , a pojmenujte ji `HighlightWordTag` .

    ```csharp
    internal class HighlightWordTag : TextMarkerTag
    {

    }
    ```

5. Vytvořte druhou třídu, která dědí z <xref:Microsoft.VisualStudio.Text.Classification.MarkerFormatDefinition> , a pojmenujte ji `HighlightWordFormatDefinition` . Aby bylo možné použít tuto definici formátu pro značku, je nutné ji exportovat s následujícími atributy:

    - <xref:Microsoft.VisualStudio.Utilities.NameAttribute>: Tags používá tuto informaci k odkazování na tento formát.

    - <xref:Microsoft.VisualStudio.Text.Classification.UserVisibleAttribute>: způsobí zobrazení formátu v uživatelském rozhraní.

    ```csharp

    [Export(typeof(EditorFormatDefinition))]
    [Name("MarkerFormatDefinition/HighlightWordFormatDefinition")]
    [UserVisible(true)]
    internal class HighlightWordFormatDefinition : MarkerFormatDefinition
    {

    }
    ```

6. V konstruktoru pro HighlightWordFormatDefinition definujte jeho zobrazované jméno a vzhled. Vlastnost Background definuje barvu výplně, zatímco vlastnost popředí definuje barvu ohraničení.

    ```csharp
    public HighlightWordFormatDefinition()
    {
        this.BackgroundColor = Colors.LightBlue;
        this.ForegroundColor = Colors.DarkBlue;
        this.DisplayName = "Highlight Word";
        this.ZOrder = 5;
    }
    ```

7. V konstruktoru pro HighlightWordTag předejte název definice formátu, kterou jste vytvořili.

    ```
    public HighlightWordTag() : base("MarkerFormatDefinition/HighlightWordFormatDefinition") { }
    ```

## <a name="implement-an-itagger"></a>Implementace ITagger
 Dalším krokem je implementace <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601> rozhraní. Toto rozhraní přiřadí k dané textové vyrovnávací paměti značky, které poskytují zvýraznění textu a jiné vizuální efekty.

### <a name="to-implement-a-tagger"></a>Implementace autor značky

1. Vytvořte třídu, která implementuje <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601> typ `HighlightWordTag` a pojmenujte ji `HighlightWordTagger` .

    ```csharp
    internal class HighlightWordTagger : ITagger<HighlightWordTag>
    {

    }
    ```

2. Do třídy přidejte následující soukromá pole a vlastnosti:

    - Objekt <xref:Microsoft.VisualStudio.Text.Editor.ITextView> , který odpovídá aktuálnímu zobrazení textu.

    - <xref:Microsoft.VisualStudio.Text.ITextBuffer>, Který odpovídá textové vyrovnávací paměti, která je umístěná v textovém zobrazení.

    - Objekt <xref:Microsoft.VisualStudio.Text.Operations.ITextSearchService> , který se používá k vyhledání textu.

    - Objekt <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigator> , který obsahuje metody pro navigaci v rámci jednotlivých textů.

    - A <xref:Microsoft.VisualStudio.Text.NormalizedSnapshotSpanCollection> , který obsahuje sadu slov, která mají být zvýrazněna.

    - A <xref:Microsoft.VisualStudio.Text.SnapshotSpan> , který odpovídá aktuálnímu slovu.

    - A <xref:Microsoft.VisualStudio.Text.SnapshotPoint> , který odpovídá aktuální pozici blikajícího kurzoru.

    - Objekt zámku.

    ```csharp
    ITextView View { get; set; }
    ITextBuffer SourceBuffer { get; set; }
    ITextSearchService TextSearchService { get; set; }
    ITextStructureNavigator TextStructureNavigator { get; set; }
    NormalizedSnapshotSpanCollection WordSpans { get; set; }
    SnapshotSpan? CurrentWord { get; set; }
    SnapshotPoint RequestedPoint { get; set; }
    object updateLock = new object();

    ```

3. Přidejte konstruktor, který inicializuje výše uvedené vlastnosti a přidá <xref:Microsoft.VisualStudio.Text.Editor.ITextView.LayoutChanged> <xref:Microsoft.VisualStudio.Text.Editor.ITextCaret.PositionChanged> obslužné rutiny události a.

    ```csharp
    public HighlightWordTagger(ITextView view, ITextBuffer sourceBuffer, ITextSearchService textSearchService,
    ITextStructureNavigator textStructureNavigator)
    {
        this.View = view;
        this.SourceBuffer = sourceBuffer;
        this.TextSearchService = textSearchService;
        this.TextStructureNavigator = textStructureNavigator;
        this.WordSpans = new NormalizedSnapshotSpanCollection();
        this.CurrentWord = null;
        this.View.Caret.PositionChanged += CaretPositionChanged;
        this.View.LayoutChanged += ViewLayoutChanged;
    }

    ```

4. Obslužné rutiny událostí volají `UpdateAtCaretPosition` metodu.

    ```csharp
    void ViewLayoutChanged(object sender, TextViewLayoutChangedEventArgs e)
    {
        // If a new snapshot wasn't generated, then skip this layout 
        if (e.NewSnapshot != e.OldSnapshot)
        {
            UpdateAtCaretPosition(View.Caret.Position);
        }
    }

    void CaretPositionChanged(object sender, CaretPositionChangedEventArgs e)
    {
        UpdateAtCaretPosition(e.NewPosition);
    }
    ```

5. Je také nutné přidat `TagsChanged` událost, která je volána metodou Update.

     [!code-csharp[VSSDKHighlightWordTest#10](../extensibility/codesnippet/CSharp/walkthrough-highlighting-text_1.cs)]
     [!code-vb[VSSDKHighlightWordTest#10](../extensibility/codesnippet/VisualBasic/walkthrough-highlighting-text_1.vb)]

6. `UpdateAtCaretPosition()`Metoda najde každé slovo v textové vyrovnávací paměti, které je identické se slovem, kde je kurzor umístěn, a vytvoří seznam <xref:Microsoft.VisualStudio.Text.SnapshotSpan> objektů, které odpovídají výskytům slova. Potom volá `SynchronousUpdate` , což vyvolá `TagsChanged` událost.

    ```csharp
    void UpdateAtCaretPosition(CaretPosition caretPosition)
    {
        SnapshotPoint? point = caretPosition.Point.GetPoint(SourceBuffer, caretPosition.Affinity);

        if (!point.HasValue)
            return;

        // If the new caret position is still within the current word (and on the same snapshot), we don't need to check it 
        if (CurrentWord.HasValue
            && CurrentWord.Value.Snapshot == View.TextSnapshot
            && point.Value >= CurrentWord.Value.Start
            && point.Value <= CurrentWord.Value.End)
        {
            return;
        }

        RequestedPoint = point.Value;
        UpdateWordAdornments();
    }

    void UpdateWordAdornments()
    {
        SnapshotPoint currentRequest = RequestedPoint;
        List<SnapshotSpan> wordSpans = new List<SnapshotSpan>();
        //Find all words in the buffer like the one the caret is on
        TextExtent word = TextStructureNavigator.GetExtentOfWord(currentRequest);
        bool foundWord = true;
        //If we've selected something not worth highlighting, we might have missed a "word" by a little bit
        if (!WordExtentIsValid(currentRequest, word))
        {
            //Before we retry, make sure it is worthwhile 
            if (word.Span.Start != currentRequest
                 || currentRequest == currentRequest.GetContainingLine().Start
                 || char.IsWhiteSpace((currentRequest - 1).GetChar()))
            {
                foundWord = false;
            }
            else
            {
                // Try again, one character previous.  
                //If the caret is at the end of a word, pick up the word.
                word = TextStructureNavigator.GetExtentOfWord(currentRequest - 1);

                //If the word still isn't valid, we're done 
                if (!WordExtentIsValid(currentRequest, word))
                    foundWord = false;
            }
        }

        if (!foundWord)
        {
            //If we couldn't find a word, clear out the existing markers
            SynchronousUpdate(currentRequest, new NormalizedSnapshotSpanCollection(), null);
            return;
        }

        SnapshotSpan currentWord = word.Span;
        //If this is the current word, and the caret moved within a word, we're done. 
        if (CurrentWord.HasValue && currentWord == CurrentWord)
            return;

        //Find the new spans
        FindData findData = new FindData(currentWord.GetText(), currentWord.Snapshot);
        findData.FindOptions = FindOptions.WholeWord | FindOptions.MatchCase;

        wordSpans.AddRange(TextSearchService.FindAll(findData));

        //If another change hasn't happened, do a real update 
        if (currentRequest == RequestedPoint)
            SynchronousUpdate(currentRequest, new NormalizedSnapshotSpanCollection(wordSpans), currentWord);
    }
    static bool WordExtentIsValid(SnapshotPoint currentRequest, TextExtent word)
    {
        return word.IsSignificant
            && currentRequest.Snapshot.GetText(word.Span).Any(c => char.IsLetter(c));
    }

    ```

7. `SynchronousUpdate`Provede synchronní aktualizaci `WordSpans` vlastností a a `CurrentWord` vyvolá `TagsChanged` událost.

    ```csharp
    void SynchronousUpdate(SnapshotPoint currentRequest, NormalizedSnapshotSpanCollection newSpans, SnapshotSpan? newCurrentWord)
    {
        lock (updateLock)
        {
            if (currentRequest != RequestedPoint)
                return;

            WordSpans = newSpans;
            CurrentWord = newCurrentWord;

            var tempEvent = TagsChanged;
            if (tempEvent != null)
                tempEvent(this, new SnapshotSpanEventArgs(new SnapshotSpan(SourceBuffer.CurrentSnapshot, 0, SourceBuffer.CurrentSnapshot.Length)));
        }
    }
    ```

8. Je nutné implementovat <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601.GetTags%2A> metodu. Tato metoda přebírá kolekci <xref:Microsoft.VisualStudio.Text.SnapshotSpan> objektů a vrací výčet rozsahů značek.

     V jazyce C# Implementujte tuto metodu jako iterátor yield, který umožňuje opožděné vyhodnocení (tj. vyhodnocení sady pouze v případě, že jsou k dispozici jednotlivé položky) značek. V Visual Basic přidejte značky do seznamu a vraťte seznam.

     V tomto případě metoda vrátí <xref:Microsoft.VisualStudio.Text.Tagging.TagSpan%601> objekt, který má "modrý" <xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag> , který poskytuje modré pozadí.

    ```csharp
    public IEnumerable<ITagSpan<HighlightWordTag>> GetTags(NormalizedSnapshotSpanCollection spans)
    {
        if (CurrentWord == null)
            yield break;

        // Hold on to a "snapshot" of the word spans and current word, so that we maintain the same
        // collection throughout
        SnapshotSpan currentWord = CurrentWord.Value;
        NormalizedSnapshotSpanCollection wordSpans = WordSpans;

        if (spans.Count == 0 || wordSpans.Count == 0)
            yield break;

        // If the requested snapshot isn't the same as the one our words are on, translate our spans to the expected snapshot 
        if (spans[0].Snapshot != wordSpans[0].Snapshot)
        {
            wordSpans = new NormalizedSnapshotSpanCollection(
                wordSpans.Select(span => span.TranslateTo(spans[0].Snapshot, SpanTrackingMode.EdgeExclusive)));

            currentWord = currentWord.TranslateTo(spans[0].Snapshot, SpanTrackingMode.EdgeExclusive);
        }

        // First, yield back the word the cursor is under (if it overlaps) 
        // Note that we'll yield back the same word again in the wordspans collection; 
        // the duplication here is expected. 
        if (spans.OverlapsWith(new NormalizedSnapshotSpanCollection(currentWord)))
            yield return new TagSpan<HighlightWordTag>(currentWord, new HighlightWordTag());

        // Second, yield all the other words in the file 
        foreach (SnapshotSpan span in NormalizedSnapshotSpanCollection.Overlap(spans, wordSpans))
        {
            yield return new TagSpan<HighlightWordTag>(span, new HighlightWordTag());
        }
    }
    ```

## <a name="create-a-tagger-provider"></a>Vytvoření poskytovatele autor značky
 Chcete-li vytvořit autor značky, musíte implementovat <xref:Microsoft.VisualStudio.Text.Tagging.IViewTaggerProvider> . Tato třída je součástí komponenty MEF, takže musíte nastavit správné atributy, aby bylo toto rozšíření rozpoznáno.

> [!NOTE]
> Další informace o MEF naleznete v tématu [Managed Extensibility Framework (MEF)](/dotnet/framework/mef/index).

### <a name="to-create-a-tagger-provider"></a>Vytvoření poskytovatele autor značky

1. Vytvořte třídu s názvem `HighlightWordTaggerProvider` , která implementuje <xref:Microsoft.VisualStudio.Text.Tagging.IViewTaggerProvider> , a exportujte ji s <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> "text" a <xref:Microsoft.VisualStudio.Text.Tagging.TagTypeAttribute> <xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag> .

    ```csharp
    [Export(typeof(IViewTaggerProvider))]
    [ContentType("text")]
    [TagType(typeof(TextMarkerTag))]
    internal class HighlightWordTaggerProvider : IViewTaggerProvider
    { }
    ```

2. Chcete <xref:Microsoft.VisualStudio.Text.Operations.ITextSearchService> -li vytvořit instanci autor značky, je nutné importovat dvě služby editoru, a <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService> .

    ```csharp
    [Import]
    internal ITextSearchService TextSearchService { get; set; }

    [Import]
    internal ITextStructureNavigatorSelectorService TextStructureNavigatorSelector { get; set; }

    ```

3. Implementujte <xref:Microsoft.VisualStudio.Text.Tagging.IViewTaggerProvider.CreateTagger%2A> metodu pro vrácení instance `HighlightWordTagger` .

    ```csharp
    public ITagger<T> CreateTagger<T>(ITextView textView, ITextBuffer buffer) where T : ITag
    {
        //provide highlighting only on the top buffer 
        if (textView.TextBuffer != buffer)
            return null;

        ITextStructureNavigator textStructureNavigator =
            TextStructureNavigatorSelector.GetTextStructureNavigator(buffer);

        return new HighlightWordTagger(textView, buffer, TextSearchService, textStructureNavigator) as ITagger<T>;
    }
    ```

## <a name="build-and-test-the-code"></a>Sestavení a testování kódu
 Chcete-li otestovat tento kód, sestavte řešení HighlightWordTest a spusťte ho v experimentální instanci.

### <a name="to-build-and-test-the-highlightwordtest-solution"></a>Sestavení a testování řešení HighlightWordTest

1. Sestavte řešení.

2. Při spuštění tohoto projektu v ladicím programu se spustí druhá instance sady Visual Studio.

3. Vytvořte textový soubor a zadejte nějaký text, ve kterém se slova opakují, například Hello Hello Hello.

4. Umístěte kurzor do jednoho z výskytů "Hello". Všechny výskyty by měly být zvýrazněny modře.

## <a name="see-also"></a>Viz také
- [Návod: propojení typu obsahu s příponou názvu souboru](../extensibility/walkthrough-linking-a-content-type-to-a-file-name-extension.md)
