---
title: 'Návod: Zvýraznění textu | Dokumenty společnosti Microsoft'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - highlight text
ms.assetid: 64b772ad-4392-42e9-a237-5137f0384bf0
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c35b1a032993a6c183191aafff77d8adeba4a3ef
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80697392"
---
# <a name="walkthrough-highlight-text"></a>Návod: Zvýraznění textu
Do editoru můžete přidat různé vizuální efekty vytvořením součástí součásti Rozhraní MEF (Managed Extensibility Framework). Tento návod ukazuje, jak zvýraznit každý výskyt aktuálního slova v textovém souboru. Pokud se slovo v textovém souboru vyskytuje více než jednou a umístíte stříšku do jednoho výskytu, zvýrazní se každý výskyt.

## <a name="prerequisites"></a>Požadavky
 Počínaje Visual Studio 2015, nenainstalujete Visual Studio SDK ze služby stažení. Je součástí volitelné funkce v nastavení sady Visual Studio. VS SDK můžete také nainstalovat později. Další informace naleznete [v tématu Instalace sady Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="create-a-mef-project"></a>Vytvoření projektu MEF

1. Vytvořte projekt C# VSIX. (V dialogovém okně **Nový projekt** vyberte možnost **Vizuální C# / Rozšiřitelnost**a potom **v six projectu**.) Pojmenujte `HighlightWordTest`řešení .

2. Přidejte do projektu šablonu položky třídění editoru. Další informace naleznete [v tématu Vytvoření rozšíření se šablonou položky editoru](../extensibility/creating-an-extension-with-an-editor-item-template.md).

3. Odstraňte existující soubory tříd.

## <a name="define-a-textmarkertag"></a>Definování textovéznačky
 Prvním krokem při zvýrazňování <xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag> textu je podtřídy a definování jeho vzhledu.

### <a name="to-define-a-textmarkertag-and-a-markerformatdefinition"></a>Definování textmarkerové značky a definice markeru

1. Přidejte soubor třídy a pojmenujte jej **HighlightWordTag**.

2. Přidejte následující odkazy:

    1. Microsoft.VisualStudio.CoreUtility

    2. Microsoft.VisualStudio.Text.Data

    3. Microsoft.VisualStudio.Text.Logic

    4. Microsoft.VisualStudio.Text.UI

    5. Microsoft.VisualStudio.Text.UI.Wpf

    6. System.ComponentModel.Složení

    7. Prezentace.Jádro

    8. Prezentace.Rámec

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

4. Vytvořte třídu, <xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag> která dědí z a pojmenujte ji `HighlightWordTag`.

    ```csharp
    internal class HighlightWordTag : TextMarkerTag
    {

    }
    ```

5. Vytvořte druhou třídu, <xref:Microsoft.VisualStudio.Text.Classification.MarkerFormatDefinition>která dědí z , a pojmenujte ji `HighlightWordFormatDefinition`. Chcete-li použít tuto definici formátu pro značku, musíte ji exportovat s následujícími atributy:

    - <xref:Microsoft.VisualStudio.Utilities.NameAttribute>: značky používají tento odkaz na tento formát

    - <xref:Microsoft.VisualStudio.Text.Classification.UserVisibleAttribute>: To způsobí, že formát se zobrazí v ui

    ```csharp

    [Export(typeof(EditorFormatDefinition))]
    [Name("MarkerFormatDefinition/HighlightWordFormatDefinition")]
    [UserVisible(true)]
    internal class HighlightWordFormatDefinition : MarkerFormatDefinition
    {

    }
    ```

6. V konstruktoru pro HighlightWordFormatDefinition definujte jeho zobrazovaný název a vzhled. Vlastnost Pozadí definuje barvu výplně, zatímco vlastnost Popředí definuje barvu ohraničení.

    ```csharp
    public HighlightWordFormatDefinition()
    {
                this.BackgroundColor = Colors.LightBlue;
        this.ForegroundColor = Colors.DarkBlue;
        this.DisplayName = "Highlight Word";
        this.ZOrder = 5;
    }
    ```

7. V konstruktoru pro HighlightWordTag předaj název definice formátu, kterou jste vytvořili.

    ```
    public HighlightWordTag() : base("MarkerFormatDefinition/HighlightWordFormatDefinition") { }
    ```

## <a name="implement-an-itagger"></a>Implementace iTaggeru
 Dalším krokem je implementace <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601> rozhraní. Toto rozhraní přiřazuje dané textové vyrovnávací paměti tagy, které poskytují zvýraznění textu a další vizuální efekty.

### <a name="to-implement-a-tagger"></a>Implementace taggeru

1. Vytvořte třídu, <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601> která `HighlightWordTag`implementuje `HighlightWordTagger`typ a pojmenujte ji .

    ```csharp
    internal class HighlightWordTagger : ITagger<HighlightWordTag>
    {

    }
    ```

2. Do třídy přidejte následující soukromá pole a vlastnosti:

    - A <xref:Microsoft.VisualStudio.Text.Editor.ITextView>, který odpovídá aktuálnímu zobrazení textu.

    - <xref:Microsoft.VisualStudio.Text.ITextBuffer>, který odpovídá textové vyrovnávací paměti, která je základem zobrazení textu.

    - A <xref:Microsoft.VisualStudio.Text.Operations.ITextSearchService>, který se používá k vyhledání textu.

    - A <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigator>, který má metody pro navigaci v rámci textu rozpětí.

    - A <xref:Microsoft.VisualStudio.Text.NormalizedSnapshotSpanCollection>, který obsahuje sadu slov, která chcete zvýraznit.

    - A <xref:Microsoft.VisualStudio.Text.SnapshotSpan>, který odpovídá aktuálnímu slovu.

    - A <xref:Microsoft.VisualStudio.Text.SnapshotPoint>, což odpovídá aktuální poloze stříšky.

    - Objekt zámku.

    ```csharp
    ITextView View { get; set; }
    ITextBuffer SourceBuffer { get; set; }
    ITextSearchService TextSearchService { get; set; }
    ITextStructureNavigator TextStructureNavigator { get; set; }
    NormalizedSnapshotSpanCollection WordSpans { get; set; }
    SnapshotSpan? CurrentWord { get; set; }
    SnapshotPoint RequestedPoint { get; set; }
    object updateLock = new object();

    ```

3. Přidejte konstruktor, který inicializuje dříve <xref:Microsoft.VisualStudio.Text.Editor.ITextView.LayoutChanged> <xref:Microsoft.VisualStudio.Text.Editor.ITextCaret.PositionChanged> uvedené vlastnosti a přidá a obslužné rutiny událostí.

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

4. Obslužné rutiny události oba volání `UpdateAtCaretPosition` metody.

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

5. Je také nutné `TagsChanged` přidat událost, která je volána metodou aktualizace.

     [!code-csharp[VSSDKHighlightWordTest#10](../extensibility/codesnippet/CSharp/walkthrough-highlighting-text_1.cs)]
     [!code-vb[VSSDKHighlightWordTest#10](../extensibility/codesnippet/VisualBasic/walkthrough-highlighting-text_1.vb)]

6. Metoda `UpdateAtCaretPosition()` vyhledá každé slovo v textové vyrovnávací paměti, která je shodná se <xref:Microsoft.VisualStudio.Text.SnapshotSpan> slovem, kde je umístěn kurzor a vytvoří seznam objektů, které odpovídají výskytu slova. Potom volá `SynchronousUpdate`, který `TagsChanged` vyvolá událost.

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
        //If we've selected something not worth highlighting, we might have missed a "word" by a little bit
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
    static bool WordExtentIsValid(SnapshotPoint currentRequest, TextExtent word)
    {
        return word.IsSignificant
            && currentRequest.Snapshot.GetText(word.Span).Any(c => char.IsLetter(c));
    }

    ```

7. Provede `SynchronousUpdate` synchronní aktualizaci `WordSpans` vlastností `CurrentWord` a vyvolá `TagsChanged` událost.

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

8. Je nutné <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601.GetTags%2A> implementovat metodu. Tato metoda přebírá <xref:Microsoft.VisualStudio.Text.SnapshotSpan> kolekci objektů a vrátí výčet rozsahy značek.

     V C#implementujte tuto metodu jako iterátor výtěžku, který umožňuje opožděné vyhodnocení (to znamená vyhodnocení sady pouze v případě, že jsou přístupné jednotlivé položky) značek. V jazyce Visual Basic přidejte značky do seznamu a vraťte seznam.

     Zde metoda vrátí <xref:Microsoft.VisualStudio.Text.Tagging.TagSpan%601> objekt, který má <xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag>"modré" , který poskytuje modré pozadí.

    ```csharp
    public IEnumerable<ITagSpan<HighlightWordTag>> GetTags(NormalizedSnapshotSpanCollection spans)
    {
        if (CurrentWord == null)
            yield break;

        // Hold on to a "snapshot" of the word spans and current word, so that we maintain the same
        // collection throughout
        SnapshotSpan currentWord = CurrentWord.Value;
        NormalizedSnapshotSpanCollection wordSpans = WordSpans;

        if (spans.Count == 0 || wordSpans.Count == 0)
            yield break;

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
            yield return new TagSpan<HighlightWordTag>(currentWord, new HighlightWordTag());

        // Second, yield all the other words in the file 
        foreach (SnapshotSpan span in NormalizedSnapshotSpanCollection.Overlap(spans, wordSpans))
        {
            yield return new TagSpan<HighlightWordTag>(span, new HighlightWordTag());
        }
    }
    ```

## <a name="create-a-tagger-provider"></a>Vytvoření poskytovatele taggeru
 Chcete-li vytvořit tagger, <xref:Microsoft.VisualStudio.Text.Tagging.IViewTaggerProvider>je nutné implementovat . Tato třída je součástí MEF, takže je nutné nastavit správné atributy tak, aby toto rozšíření bylo rozpoznáno.

> [!NOTE]
> Další informace o MEF naleznete [v tématu Spravované rozšíření framework (MEF)](/dotnet/framework/mef/index).

### <a name="to-create-a-tagger-provider"></a>Vytvoření poskytovatele taggeru

1. Vytvořte třídu `HighlightWordTaggerProvider` s <xref:Microsoft.VisualStudio.Text.Tagging.IViewTaggerProvider>názvem, která <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> implementuje a <xref:Microsoft.VisualStudio.Text.Tagging.TagTypeAttribute> exportujte ji s "text" a a . <xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag>

    ```csharp
    [Export(typeof(IViewTaggerProvider))]
    [ContentType("text")]
    [TagType(typeof(TextMarkerTag))]
    internal class HighlightWordTaggerProvider : IViewTaggerProvider
    { }
    ```

2. Chcete-li vytvořit instanci <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService>tagger, je nutné importovat dvě služby editoru <xref:Microsoft.VisualStudio.Text.Operations.ITextSearchService> a a .

    ```csharp
    [Import]
    internal ITextSearchService TextSearchService { get; set; }

    [Import]
    internal ITextStructureNavigatorSelectorService TextStructureNavigatorSelector { get; set; }

    ```

3. Implementujte <xref:Microsoft.VisualStudio.Text.Tagging.IViewTaggerProvider.CreateTagger%2A> metodu vrátit `HighlightWordTagger`instanci .

    ```csharp
    public ITagger<T> CreateTagger<T>(ITextView textView, ITextBuffer buffer) where T : ITag
    {
        //provide highlighting only on the top buffer 
        if (textView.TextBuffer != buffer)
            return null;

        ITextStructureNavigator textStructureNavigator =
            TextStructureNavigatorSelector.GetTextStructureNavigator(buffer);

        return new HighlightWordTagger(textView, buffer, TextSearchService, textStructureNavigator) as ITagger<T>;
    }
    ```

## <a name="build-and-test-the-code"></a>Sestavení a testování kódu
 Chcete-li tento kód otestovat, vytvořte řešení HighlightWordTest a spusťte jej v experimentální instanci.

### <a name="to-build-and-test-the-highlightwordtest-solution"></a>Vytvoření a testování řešení HighlightWordTest

1. Sestavte řešení.

2. Při spuštění tohoto projektu v ladicím programu je spuštěna druhá instance sady Visual Studio.

3. Vytvořte textový soubor a zadejte nějaký text, ve kterém se slova opakují, například "hello hello hello".

4. Umístěte kurzor do jednoho z výskytů "hello". Každý výskyt by měl být zvýrazněn modře.

## <a name="see-also"></a>Viz také
- [Návod: Propojení typu obsahu s příponou názvu souboru](../extensibility/walkthrough-linking-a-content-type-to-a-file-name-extension.md)
