---
title: 'Návod: Zvýraznění textu | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], new - highlight text
ms.assetid: 64b772ad-4392-42e9-a237-5137f0384bf0
caps.latest.revision: 43
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: d4fad243b109cb8522f15e30d628d5eb27c09c07
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51790718"
---
# <a name="walkthrough-highlighting-text"></a>Návod: Zvýraznění textu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Různých vizuálních efektů můžete přidat do editoru tak, že vytvoříte Managed Extensibility Framework (MEF) součásti. Tento návod ukazuje, jak zvýraznit všechny výskyty aktuálního slova v textovém souboru. Pokud dojde u slov velká k více než jednou do textového souboru a umístěte blikající kurzor o jeden výskyt, je zvýrazněn výskyt.  
  
## <a name="prerequisites"></a>Požadavky  
 Spouští se v sadě Visual Studio 2015, nenainstalujete sadu Visual Studio SDK ze služby Stažení softwaru. Je zahrnut jako volitelná funkce v instalačním programu sady Visual Studio. VS SDK můžete také nainstalovat později. Další informace najdete v tématu [instalace sady Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="creating-a-mef-project"></a>Vytvoření projektu rozhraní MEF  
  
1.  Vytvořte projekt VSIX C#. (V **nový projekt** dialogového okna, vyberte **Visual C# / rozšíření**, pak **projekt VSIX**.) Pojmenujte řešení `HighlightWordTest`.  
  
2.  Přidejte do projektu šablony položky editoru třídění. Další informace najdete v tématu [vytváření rozšíření pomocí šablony položky editoru](../extensibility/creating-an-extension-with-an-editor-item-template.md).  
  
3.  Odstraníte existující soubory tříd.  
  
## <a name="defining-a-textmarkertag"></a>Definování TextMarkerTag  
 Prvním krokem při zvýraznění textu je podtřídou <xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag> a definují jeho vzhled.  
  
#### <a name="to-define-a-textmarkertag-and-a-markerformatdefinition"></a>Chcete-li definovat TextMarkerTag a MarkerFormatDefinition  
  
1.  Přidejte soubor třídy a pojmenujte ho **HighlightWordTag**.  
  
2.  Přidejte následující odkazy:  
  
    1.  Microsoft.VisualStudio.CoreUtility  
  
    2.  Microsoft.VisualStudio.Text.Data  
  
    3.  Microsoft.VisualStudio.Text.Logic  
  
    4.  Microsoft.VisualStudio.Text.UI  
  
    5.  Microsoft.VisualStudio.Text.UI.Wpf  
  
    6.  System.ComponentModel.Composition  
  
    7.  Presentation.Core  
  
    8.  Presentation.Framework  
  
3.  Importujte následující obory názvů.  
  
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
  
4.  Vytvořte třídu, která dědí z <xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag> a pojmenujte ho `HighlightWordTag`.  
  
    ```csharp  
    internal class HighlightWordTag : TextMarkerTag  
    {  
  
    }  
    ```  
  
5.  Vytvořte druhé třídu, která dědí z <xref:Microsoft.VisualStudio.Text.Classification.MarkerFormatDefinition>a pojmenujte ho HighlightWordFormatDefinition. Chcete-li použít tento formát definice pro vaši značku, je nutné ho exportovat s následujícími atributy:  
  
    -   <xref:Microsoft.VisualStudio.Utilities.NameAttribute>: značky využit k odkazují na tento formát  
  
    -   <xref:Microsoft.VisualStudio.Text.Classification.UserVisibleAttribute>: To způsobí, že formát, který se zobrazí v uživatelském rozhraní  
  
    ```csharp  
  
    [Export(typeof(EditorFormatDefinition))]  
    [Name("MarkerFormatDefinition/HighlightWordFormatDefinition")]  
    [UserVisible(true)]  
    internal class HighlightWordFormatDefinition : MarkerFormatDefinition  
    {  
  
    }  
    ```  
  
6.  V konstruktoru pro HighlightWordFormatDefinition Definujte zobrazovaný název a vzhled. Vlastnost pozadí definuje barvu výplně, zatímco popředí vlastnost určuje barvu ohraničení.  
  
    ```csharp  
    public HighlightWordFormatDefinition()  
    {  
                this.BackgroundColor = Colors.LightBlue;  
        this.ForegroundColor = Colors.DarkBlue;  
        this.DisplayName = "Highlight Word";  
        this.ZOrder = 5;  
    }  
    ```  
  
7.  V konstruktoru pro HighlightWordTag předejte název formátu definice, kterou jste právě vytvořili.  
  
    ```  
    public HighlightWordTag() : base("MarkerFormatDefinition/HighlightWordFormatDefinition") { }  
    ```  
  
## <a name="implementing-an-itagger"></a>Implementace ITagger  
 Dalším krokem je implementace <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601> rozhraní. Toto rozhraní se přiřadí k dané textovou vyrovnávací paměť, značky, které poskytují zvýraznění textu a jiných vizuálních efektů.  
  
#### <a name="to-implement-a-tagger"></a>K implementaci označovatel  
  
1.  Vytvořte třídu, která implementuje <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601> typu `HighlightWordTag`a pojmenujte ho `HighlightWordTagger`.  
  
    ```csharp  
    internal class HighlightWordTagger : ITagger<HighlightWordTag>  
    {  
  
    }  
    ```  
  
2.  Přidejte následující soukromé pole a vlastnosti do třídy:  
  
    -   <xref:Microsoft.VisualStudio.Text.Editor.ITextView>, Která odpovídá aktuálnímu zobrazení textu.  
  
    -   <xref:Microsoft.VisualStudio.Text.ITextBuffer>, Která odpovídá textové vyrovnávací paměti, které je základem zobrazení textu.  
  
    -   <xref:Microsoft.VisualStudio.Text.Operations.ITextSearchService>, Který se používá k vyhledání textu.  
  
    -   <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigator>, Která obsahuje metody pro navigaci v textu rozsahy.  
  
    -   A <xref:Microsoft.VisualStudio.Text.NormalizedSnapshotSpanCollection>, který obsahuje sadu slov, abyste měli na očích.  
  
    -   A <xref:Microsoft.VisualStudio.Text.SnapshotSpan>, která odpovídá aktuálního slova.  
  
    -   A <xref:Microsoft.VisualStudio.Text.SnapshotPoint>, která odpovídá aktuální pozici blikajícího kurzoru.  
  
    -   Zámek objektu.  
  
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
  
3.  Přidat konstruktor, který inicializuje vlastností uvedených výše a přidá <xref:Microsoft.VisualStudio.Text.Editor.ITextView.LayoutChanged> a <xref:Microsoft.VisualStudio.Text.Editor.ITextCaret.PositionChanged> obslužných rutin událostí.  
  
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
  
4.  Obě volání obslužné rutiny událostí `UpdateAtCaretPosition` metody.  
  
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
  
5.  Musíte taky přidat `TagsChanged` událost, která bude volat metodu aktualizace.  
  
     [!code-csharp[VSSDKHighlightWordTest#10](../snippets/csharp/VS_Snippets_VSSDK/vssdkhighlightwordtest/cs/highlightwordtag.cs#10)]
     [!code-vb[VSSDKHighlightWordTest#10](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkhighlightwordtest/vb/highlightwordtag.vb#10)]  
  
6.  `UpdateAtCaretPosition()` Metoda vyhledá ve vyrovnávací paměti textu, který je stejný jako word, kde je umístěn ukazatel a vytvoří seznam všech slov <xref:Microsoft.VisualStudio.Text.SnapshotSpan> objekty, které odpovídají výskyty slova. Poté zavolá `SynchronousUpdate`, která vyvolává `TagsChanged` událostí.  
  
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
  
7.  `SynchronousUpdate` Provádí synchronní aktualizace `WordSpans` a `CurrentWord` vlastnosti a vyvolá `TagsChanged` událostí.  
  
    ```vb  
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
  
8.  Je nutné implementovat <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601.GetTags%2A> metody. Tato metoda vezme kolekci <xref:Microsoft.VisualStudio.Text.SnapshotSpan> objekty a vrátí výčet značku rozpětí.  
  
     V jazyce C# Implementujte tuto metodu jako iterátor příkazu yield, která umožňuje opožděné vyhodnocení (to znamená, vyhodnocení sady pouze v případě, že jednotlivé položky jsou přístupné) značek. V jazyce Visual Basic přidání značek do seznamu a vrátí seznam.  
  
     Tady metoda vrátí <xref:Microsoft.VisualStudio.Text.Tagging.TagSpan%601> objekt, který má "blue" <xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag>, poskytující modrým pozadím.  
  
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
  
## <a name="creating-a-tagger-provider"></a>Vytvoření zprostředkovatele Označovatel  
 Pokud chcete vytvořit váš označovatel, je nutné implementovat <xref:Microsoft.VisualStudio.Text.Tagging.IViewTaggerProvider>. Tato třída je součást MEF, proto musíte nastavit správné atributy tak, aby toto rozšíření je rozpoznán.  
  
> [!NOTE]
>  Další informace o rozhraní MEF, naleznete v tématu [Managed Extensibility Framework (MEF)](http://msdn.microsoft.com/library/6c61b4ec-c6df-4651-80f1-4854f8b14dde).  
  
#### <a name="to-create-a-tagger-provider"></a>K vytvoření poskytovatele označovatel  
  
1.  Vytvořte třídu s názvem `HighlightWordTaggerProvider` , který implementuje <xref:Microsoft.VisualStudio.Text.Tagging.IViewTaggerProvider>a exportujte ho pomocí <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> "text" a <xref:Microsoft.VisualStudio.Text.Tagging.TagTypeAttribute> z <xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag>.  
  
    ```csharp  
    [Export(typeof(IViewTaggerProvider))]  
    [ContentType("text")]  
    [TagType(typeof(TextMarkerTag))]  
    internal class HighlightWordTaggerProvider : IViewTaggerProvider  
    { }  
    ```  
  
2.  Je nutné naimportovat dvě služby editoru <xref:Microsoft.VisualStudio.Text.Operations.ITextSearchService> a <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService>, k vytvoření instance označovatel.  
  
    ```csharp  
    [Import]  
    internal ITextSearchService TextSearchService { get; set; }  
  
    [Import]  
    internal ITextStructureNavigatorSelectorService TextStructureNavigatorSelector { get; set; }  
  
    ```  
  
3.  Implementace <xref:Microsoft.VisualStudio.Text.Tagging.IViewTaggerProvider.CreateTagger%2A> metoda vrátí instanci `HighlightWordTagger`.  
  
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
  
## <a name="building-and-testing-the-code"></a>Vytváření a testování kódu  
 K otestování tohoto kódu sestavte řešení HighlightWordTest a spusťte v experimentální instanci.  
  
#### <a name="to-build-and-test-the-highlightwordtest-solution"></a>Pro vytváření a testování HighlightWordTest řešení  
  
1.  Sestavte řešení.  
  
2.  Při spuštění tohoto projektu v ladicím programu, je vytvořena instance druhou instanci aplikace Visual Studio.  
  
3.  Vytvořte textový soubor a zadejte nějaký text, ve které se opakují slova, například "hello hello hello".  
  
4.  Umístěte kurzor do jednoho z výskytů řetězce "hello". Každý výskyt by měl být zvýrazněn modrá.  
  
## <a name="see-also"></a>Viz také  
 [Návod: Propojení typu obsahu s příponou názvu souboru](../extensibility/walkthrough-linking-a-content-type-to-a-file-name-extension.md)

