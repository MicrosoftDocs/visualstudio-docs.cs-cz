---
title: Použití příkazu shell s rozšířením editoru
description: Naučte se, jak přidat Doplňky do zobrazení textu v editoru vyvoláním příkazu nabídky. Z VSPackage můžete přidat funkce, jako jsou příkazy nabídky, do editoru.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- editors [Visual Studio SDK], new - add a menu command
ms.assetid: 08526848-a442-4cd4-afa1-b2eac2005adb
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 38d855ebe34c54d06159ecd958a8b1d31ae0131f
ms.sourcegitcommit: 0c9155e9b9408fb7481d79319bf08650b610e719
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/05/2021
ms.locfileid: "97877816"
---
# <a name="walkthrough-use-a-shell-command-with-an-editor-extension"></a>Návod: použití příkazu shell s rozšířením editoru
Z VSPackage můžete do editoru přidat funkce, jako například příkazy nabídky. Tento návod ukazuje, jak přidat Doplňky do zobrazení textu v editoru vyvoláním příkazu nabídky.

 Tento návod ukazuje použití VSPackage společně s částí komponenty Managed Extensibility Framework (MEF). K registraci příkazu nabídky v prostředí sady Visual Studio je nutné použít VSPackage. A můžete použít příkaz pro přístup k části komponenty MEF.

## <a name="prerequisites"></a>Předpoklady
 Od sady Visual Studio 2015 nenainstalujete sadu Visual Studio SDK z webu Stažení softwaru. V instalačním programu sady Visual Studio je zahrnutý jako volitelná funkce. Sadu VS SDK můžete také nainstalovat později. Další informace najdete v tématu [instalace sady Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="create-an-extension-with-a-menu-command"></a>Vytvoření rozšíření pomocí příkazu nabídky
 Vytvořte VSPackage, který vloží příkaz nabídky s názvem **Přidat** doplňky v nabídce **nástroje** .

1. Vytvořte projekt VSIX v jazyce C# s názvem `MenuCommandTest` a přidejte vlastní název šablony položky příkazu **AddAdornment**. Další informace najdete v tématu [Vytvoření rozšíření pomocí příkazu nabídky](../extensibility/creating-an-extension-with-a-menu-command.md).

2. Otevře se řešení s názvem MenuCommandTest. Soubor MenuCommandTestPackage obsahuje kód, který vytvoří příkaz nabídky a umístí jej do nabídky **nástroje** . V tomto okamžiku příkaz vyvolá pouze okno se zprávou. V dalších krocích se dozvíte, jak tuto změnu zobrazit, aby se zobrazila přízpůsobování komentářů.

3. V editoru manifestu VSIX otevřete soubor *source. extension. vsixmanifest* . `Assets`Karta by měla obsahovat řádek pro Microsoft. VisualStudio. VSPackage s názvem MenuCommandTest.

4. Uložte a zavřete soubor *source. extension. vsixmanifest* .

## <a name="add-a-mef-extension-to-the-command-extension"></a>Přidat rozšíření MEF do rozšíření příkazu

1. V **Průzkumník řešení** klikněte pravým tlačítkem myši na uzel řešení, klikněte na položku **Přidat** a poté klikněte na možnost **Nový projekt**. V dialogovém okně **Přidat nový projekt** klikněte na **rozšiřitelnost** v části **Visual C#** a pak na **projekt VSIX**. Pojmenujte projekt `CommentAdornmentTest` .

2. Vzhledem k tomu, že tento projekt bude pracovat se sestavením VSPackage se silným názvem, je nutné sestavení podepsat. Můžete znovu použít soubor klíče, který již byl vytvořen pro sestavení VSPackage.

    1. Otevřete vlastnosti projektu a vyberte kartu **podepisování** .

    2. Vyberte **podepsat sestavení**.

    3. V části **zvolit soubor klíče se silným názvem** vyberte soubor *Key. snk* , který byl vygenerován pro sestavení MenuCommandTest.

## <a name="refer-to-the-mef-extension-in-the-vspackage-project"></a>Odkaz na rozšíření MEF v projektu VSPackage
 Vzhledem k tomu, že přidáváte komponentu MEF do balíčku VSPackage, je nutné v manifestu zadat oba druhy prostředků.

> [!NOTE]
> Další informace o MEF naleznete v tématu [Managed Extensibility Framework (MEF)](/dotnet/framework/mef/index).

### <a name="to-refer-to-the-mef-component-in-the-vspackage-project"></a>Chcete-li odkazovat na komponentu MEF v projektu VSPackage

1. V projektu MenuCommandTest otevřete soubor *source. extension. vsixmanifest* v editoru manifestu VSIX.

2. Na kartě **assety** klikněte na **Nový**.

3. V seznamu **typ** vyberte možnost **Microsoft. VisualStudio. MefComponent**.

4. V seznamu **zdroj** vyberte **projekt v aktuálním řešení**.

5. V seznamu **projekt** vyberte možnost **CommentAdornmentTest**.

6. Uložte a zavřete soubor *source. extension. vsixmanifest* .

7. Ujistěte se, že projekt MenuCommandTest má odkaz na projekt CommentAdornmentTest.

8. V projektu CommentAdornmentTest nastavte projekt tak, aby vytvořil sestavení. V **Průzkumník řešení** vyberte projekt a v okně **vlastnosti** vyhledejte vlastnost **Kopírovat výstup sestavení do vlastnosti OutputDirectory** a nastavte ji na **hodnotu true**.

## <a name="define-a-comment-adornment"></a>Definování přívylepšení komentářů
 Vlastní označení komentáře se skládá z objektu <xref:Microsoft.VisualStudio.Text.ITrackingSpan> , který sleduje vybraný text, a některých řetězců, které reprezentují autor a popis textu.

#### <a name="to-define-a-comment-adornment"></a>Definování přívylepšení komentáře

1. V projektu CommentAdornmentTest přidejte nový soubor třídy a pojmenujte ho `CommentAdornment` .

2. Přidejte následující odkazy:

    1. Microsoft. VisualStudio. CoreUtility

    2. Microsoft. VisualStudio. text. data

    3. Microsoft. VisualStudio. text. Logic

    4. Microsoft. VisualStudio. text. UI

    5. Microsoft. VisualStudio. text. UI. WPF

    6. System. ComponentModel. složení

    7. PresentationCore

    8. PresentationFramework

    9. WindowsBase

3. Přidejte následující `using` direktivu.

    ```csharp
    using Microsoft.VisualStudio.Text;
    ```

4. Soubor by měl obsahovat třídu s názvem `CommentAdornment` .

    ```csharp
    internal class CommentAdornment
    ```

5. Přidejte tři pole do `CommentAdornment` třídy pro <xref:Microsoft.VisualStudio.Text.ITrackingSpan> , autora a popis.

    ```csharp
    public readonly ITrackingSpan Span;
    public readonly string Author;
    public readonly string Text;
    ```

6. Přidejte konstruktor, který inicializuje pole.

    ```csharp
    public CommentAdornment(SnapshotSpan span, string author, string text)
    {
        this.Span = span.Snapshot.CreateTrackingSpan(span, SpanTrackingMode.EdgeExclusive);
        this.Author = author;
        this.Text = text;
    }
    ```

## <a name="create-a-visual-element-for-the-adornment"></a>Vytvoření vizuálního prvku pro Doplňky
 Definujte vizuální prvek pro vaše vylepšení. Pro tento návod definujte ovládací prvek, který dědí z třídy Windows Presentation Foundation (WPF) <xref:System.Windows.Controls.Canvas> .

1. Vytvořte třídu v projektu CommentAdornmentTest a pojmenujte ji `CommentBlock` .

2. Přidejte následující `using` direktivy.

    ```csharp
    using Microsoft.VisualStudio.Text;
    using System;
    using System.Windows;
    using System.Windows.Controls;
    using System.Windows.Media;
    using System.Windows.Shapes;
    using System.ComponentModel.Composition;
    using Microsoft.VisualStudio.Text.Editor;
    using Microsoft.VisualStudio.Utilities;
    ```

3. Nastavit `CommentBlock` třídu jako děděnou z <xref:System.Windows.Controls.Canvas> .

    ```csharp
    internal class CommentBlock : Canvas
    { }
    ```

4. Přidejte některá soukromá pole, abyste mohli definovat vizuální aspekty přívylepšení.

    ```csharp
    private Geometry textGeometry;
    private Grid commentGrid;
    private static Brush brush;
    private static Pen solidPen;
    private static Pen dashPen;
    ```

5. Přidejte konstruktor definující dodatečnou hodnotu komentáře a přidejte příslušný text.

    ```csharp
    public CommentBlock(double textRightEdge, double viewRightEdge,
            Geometry newTextGeometry, string author, string body)
    {
        if (brush == null)
        {
            brush = new SolidColorBrush(Color.FromArgb(0x20, 0x00, 0xff, 0x00));
            brush.Freeze();
            Brush penBrush = new SolidColorBrush(Colors.Green);
            penBrush.Freeze();
            solidPen = new Pen(penBrush, 0.5);
            solidPen.Freeze();
            dashPen = new Pen(penBrush, 0.5);
            dashPen.DashStyle = DashStyles.Dash;
            dashPen.Freeze();
        }

        this.textGeometry = newTextGeometry;

        TextBlock tb1 = new TextBlock();
        tb1.Text = author;
        TextBlock tb2 = new TextBlock();
        tb2.Text = body;

        const int MarginWidth = 8;
        this.commentGrid = new Grid();
        this.commentGrid.RowDefinitions.Add(new RowDefinition());
        this.commentGrid.RowDefinitions.Add(new RowDefinition());
        ColumnDefinition cEdge = new ColumnDefinition();
        cEdge.Width = new GridLength(MarginWidth);
        ColumnDefinition cEdge2 = new ColumnDefinition();
        cEdge2.Width = new GridLength(MarginWidth);
        this.commentGrid.ColumnDefinitions.Add(cEdge);
        this.commentGrid.ColumnDefinitions.Add(new ColumnDefinition());
        this.commentGrid.ColumnDefinitions.Add(cEdge2);

        System.Windows.Shapes.Rectangle rect = new System.Windows.Shapes.Rectangle();
        rect.RadiusX = 6;
        rect.RadiusY = 3;
        rect.Fill = brush;
        rect.Stroke = Brushes.Green;

            Size inf = new Size(double.PositiveInfinity, double.PositiveInfinity);
            tb1.Measure(inf);
            tb2.Measure(inf);
            double middleWidth = Math.Max(tb1.DesiredSize.Width, tb2.DesiredSize.Width);
            this.commentGrid.Width = middleWidth + 2 * MarginWidth;

        Grid.SetColumn(rect, 0);
        Grid.SetRow(rect, 0);
        Grid.SetRowSpan(rect, 2);
        Grid.SetColumnSpan(rect, 3);
        Grid.SetRow(tb1, 0);
        Grid.SetColumn(tb1, 1);
        Grid.SetRow(tb2, 1);
        Grid.SetColumn(tb2, 1);
        this.commentGrid.Children.Add(rect);
        this.commentGrid.Children.Add(tb1);
        this.commentGrid.Children.Add(tb2);

        Canvas.SetLeft(this.commentGrid, Math.Max(viewRightEdge - this.commentGrid.Width - 20.0, textRightEdge + 20.0));
        Canvas.SetTop(this.commentGrid, textGeometry.GetRenderBounds(solidPen).Top);

        this.Children.Add(this.commentGrid);
    }
    ```

6. Také implementujte <xref:System.Windows.Controls.Panel.OnRender%2A> obslužnou rutinu události, která kreslí doplňky.

    ```csharp
    protected override void OnRender(DrawingContext dc)
    {
        base.OnRender(dc);
        if (this.textGeometry != null)
        {
            dc.DrawGeometry(brush, solidPen, this.textGeometry);
            Rect textBounds = this.textGeometry.GetRenderBounds(solidPen);
            Point p1 = new Point(textBounds.Right, textBounds.Bottom);
            Point p2 = new Point(Math.Max(Canvas.GetLeft(this.commentGrid) - 20.0, p1.X), p1.Y);
            Point p3 = new Point(Math.Max(Canvas.GetLeft(this.commentGrid), p1.X), (Canvas.GetTop(this.commentGrid) + p1.Y) * 0.5);
            dc.DrawLine(dashPen, p1, p2);
            dc.DrawLine(dashPen, p2, p3);
        }
    }
    ```

## <a name="add-an-iwpftextviewcreationlistener"></a>Přidat IWpfTextViewCreationListener
 <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewCreationListener>Je část komponenty MEF, kterou můžete použít k naslouchání událostem vytváření.

1. Přidejte soubor třídy do projektu CommentAdornmentTest a pojmenujte ho `Connector` .

2. Přidejte následující `using` direktivy.

    ```csharp
    using System.ComponentModel.Composition;
    using Microsoft.VisualStudio.Text.Editor;
    using Microsoft.VisualStudio.Utilities;
    ```

3. Deklarujte třídu, která implementuje <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewCreationListener> , a exportujte ji s <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> "text" a <xref:Microsoft.VisualStudio.Text.Editor.TextViewRoleAttribute> <xref:Microsoft.VisualStudio.Text.Editor.PredefinedTextViewRoles.Document> . Atribut typ obsahu určuje druh obsahu, na který se komponenta vztahuje. Typ textu je základní typ pro všechny typy bez binárních souborů. Proto budou téměř všechna vytvořená textová zobrazení tohoto typu. Atribut role zobrazení textu určuje druh textového zobrazení, na které se komponenta vztahuje. Role zobrazení textu dokumentu obecně zobrazují text složený z řádků a jsou uloženy v souboru.

     [!code-vb[VSSDKMenuCommandTest#11](../extensibility/codesnippet/VisualBasic/walkthrough-using-a-shell-command-with-an-editor-extension_1.vb)]
     [!code-csharp[VSSDKMenuCommandTest#11](../extensibility/codesnippet/CSharp/walkthrough-using-a-shell-command-with-an-editor-extension_1.cs)]

4. Implementujte <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewCreationListener.TextViewCreated%2A> metodu tak, aby volala statickou `Create()` událost `CommentAdornmentManager` .

    ```csharp
    public void TextViewCreated(IWpfTextView textView)
    {
        CommentAdornmentManager.Create(textView);
    }
    ```

5. Přidejte metodu, kterou můžete použít ke spuštění příkazu.

    ```csharp
    static public void Execute(IWpfTextViewHost host)
    {
        IWpfTextView view = host.TextView;
        //Add a comment on the selected text. 
        if (!view.Selection.IsEmpty)
        {
            //Get the provider for the comment adornments in the property bag of the view.
            CommentAdornmentProvider provider = view.Properties.GetProperty<CommentAdornmentProvider>(typeof(CommentAdornmentProvider));

            //Add some arbitrary author and comment text. 
            string author = System.Security.Principal.WindowsIdentity.GetCurrent().Name;
            string comment = "Four score....";

            //Add the comment adornment using the provider.
            provider.Add(view.Selection.SelectedSpans[0], author, comment);
        }
    }
    ```

## <a name="define-an-adornment-layer"></a>Definovat vrstvu doplňků
 Chcete-li přidat nové doplňky, je nutné definovat vrstvu přípráv.

### <a name="to-define-an-adornment-layer"></a>Definování vrstvy doplňků

1. Ve `Connector` třídě deklarujte veřejné pole typu <xref:Microsoft.VisualStudio.Text.Editor.AdornmentLayerDefinition> a exportujte jej pomocí typu <xref:Microsoft.VisualStudio.Utilities.NameAttribute> , který určuje jedinečný název pro vrstvu navýšení a <xref:Microsoft.VisualStudio.Utilities.OrderAttribute> definující vztah pořadí vykreslování této vrstvy úprav na jiné vrstvy zobrazení textu (text, kurzor a výběr).

    ```csharp
    [Export(typeof(AdornmentLayerDefinition))]
    [Name("CommentAdornmentLayer")]
    [Order(After = PredefinedAdornmentLayers.Selection, Before = PredefinedAdornmentLayers.Text)]
    public AdornmentLayerDefinition commentLayerDefinition;

    ```

## <a name="provide-comment-adornments"></a>Zadat vylepšení komentářů
 Při definování doplňku se také implementují poskytovatelé přidaných komentářů a Správce doplňků komentářů. Poskytovatel vylepšení komentáře uchovává seznam vylepšení komentářů, naslouchá <xref:Microsoft.VisualStudio.Text.ITextBuffer.Changed> událostem v podkladové vyrovnávací paměti textu a při odstranění podkladového textu odstraní Další doplňky komentářů.

1. Přidejte do projektu CommentAdornmentTest nový soubor třídy a pojmenujte ho `CommentAdornmentProvider` .

2. Přidejte následující `using` direktivy.

    ```csharp
    using System;
    using System.Collections.Generic;
    using System.Collections.ObjectModel;
    using Microsoft.VisualStudio.Text;
    using Microsoft.VisualStudio.Text.Editor;
    ```

3. Přidejte třídu s názvem `CommentAdornmentProvider` .

    ```csharp
    internal class CommentAdornmentProvider
    {
    }
    ```

4. Přidejte soukromá pole pro textovou vyrovnávací paměť a seznam doplňků komentářů souvisejících s vyrovnávací pamětí.

    ```csharp
    private ITextBuffer buffer;
    private IList<CommentAdornment> comments = new List<CommentAdornment>();

    ```

5. Přidejte konstruktor pro `CommentAdornmentProvider` . Tento konstruktor by měl mít privátní přístup, protože poskytovatel je vytvořen `Create()` metodou. Konstruktor přidá `OnBufferChanged` do události obslužnou rutinu události <xref:Microsoft.VisualStudio.Text.ITextBuffer.Changed> .

    ```csharp
    private CommentAdornmentProvider(ITextBuffer buffer)
    {
        this.buffer = buffer;
        //listen to the Changed event so we can react to deletions. 
        this.buffer.Changed += OnBufferChanged;
    }

    ```

6. Přidejte `Create()` metodu.

    ```csharp
    public static CommentAdornmentProvider Create(IWpfTextView view)
    {
        return view.Properties.GetOrCreateSingletonProperty<CommentAdornmentProvider>(delegate { return new CommentAdornmentProvider(view.TextBuffer); });
    }

    ```

7. Přidejte `Detach()` metodu.

    ```csharp
    public void Detach()
    {
        if (this.buffer != null)
        {
            //remove the Changed listener 
            this.buffer.Changed -= OnBufferChanged;
            this.buffer = null;
        }
    }
    ```

8. Přidejte `OnBufferChanged` obslužnou rutinu události.

     [!code-csharp[VSSDKMenuCommandTest#21](../extensibility/codesnippet/CSharp/walkthrough-using-a-shell-command-with-an-editor-extension_2.cs)]
     [!code-vb[VSSDKMenuCommandTest#21](../extensibility/codesnippet/VisualBasic/walkthrough-using-a-shell-command-with-an-editor-extension_2.vb)]

9. Přidejte deklaraci pro `CommentsChanged` událost.

    ```csharp
    public event EventHandler<CommentsChangedEventArgs> CommentsChanged;
    ```

10. Vytvořte `Add()` metodu pro přidání vylepšení.

    ```csharp
    public void Add(SnapshotSpan span, string author, string text)
    {
        if (span.Length == 0)
            throw new ArgumentOutOfRangeException("span");
        if (author == null)
            throw new ArgumentNullException("author");
        if (text == null)
            throw new ArgumentNullException("text");

        //Create a comment adornment given the span, author and text.
        CommentAdornment comment = new CommentAdornment(span, author, text);

        //Add it to the list of comments. 
        this.comments.Add(comment);

        //Raise the changed event.
        EventHandler<CommentsChangedEventArgs> commentsChanged = this.CommentsChanged;
        if (commentsChanged != null)
            commentsChanged(this, new CommentsChangedEventArgs(comment, null));
    }

    ```

11. Přidejte `RemoveComments()` metodu.

    ```csharp
    public void RemoveComments(SnapshotSpan span)
    {
        EventHandler<CommentsChangedEventArgs> commentsChanged = this.CommentsChanged;

        //Get a list of all the comments that are being kept
        IList<CommentAdornment> keptComments = new List<CommentAdornment>(this.comments.Count);

        foreach (CommentAdornment comment in this.comments)
        {
            //find out if the given span overlaps with the comment text span. If two spans are adjacent, they do not overlap. To consider adjacent spans, use IntersectsWith. 
            if (comment.Span.GetSpan(span.Snapshot).OverlapsWith(span))
            {
                //Raise the change event to delete this comment. 
                if (commentsChanged != null)
                    commentsChanged(this, new CommentsChangedEventArgs(null, comment));
            }
            else
                keptComments.Add(comment);
        }

        this.comments = keptComments;
    }
    ```

12. Přidejte `GetComments()` metodu, která vrátí všechny komentáře v daném rozsahu snímku.

    ```csharp
    public Collection<CommentAdornment> GetComments(SnapshotSpan span)
    {
        IList<CommentAdornment> overlappingComments = new List<CommentAdornment>();
        foreach (CommentAdornment comment in this.comments)
        {
            if (comment.Span.GetSpan(span.Snapshot).OverlapsWith(span))
                overlappingComments.Add(comment);
        }

        return new Collection<CommentAdornment>(overlappingComments);
    }
    ```

13. Následujícím způsobem přidejte třídu s názvem `CommentsChangedEventArgs` .

    ```csharp
    internal class CommentsChangedEventArgs : EventArgs
    {
        public readonly CommentAdornment CommentAdded;

        public readonly CommentAdornment CommentRemoved;

        public CommentsChangedEventArgs(CommentAdornment added, CommentAdornment removed)
        {
            this.CommentAdded = added;
            this.CommentRemoved = removed;
        }
    }
    ```

## <a name="manage-comment-adornments"></a>Spravovat vylepšení komentářů
 Správce přidaných komentářů vytvoří doplňky a přidá ji do vrstvy pro doplňky. Naslouchá <xref:Microsoft.VisualStudio.Text.Editor.ITextView.LayoutChanged> <xref:Microsoft.VisualStudio.Text.Editor.ITextView.Closed> událostem a, aby mohl přesunout nebo odstranit doplňky. Také poslouchá `CommentsChanged` událost, která je vyvolána poskytovatelem přízvuku komentáře při přidání nebo odebrání komentářů.

1. Přidejte soubor třídy do projektu CommentAdornmentTest a pojmenujte ho `CommentAdornmentManager` .

2. Přidejte následující `using` direktivy.

    ```csharp
    using System;
    using System.Collections.Generic;
    using System.Windows.Media;
    using Microsoft.VisualStudio.Text;
    using Microsoft.VisualStudio.Text.Editor;
    using Microsoft.VisualStudio.Text.Formatting;
    ```

3. Přidejte třídu s názvem `CommentAdornmentManager` .

    ```csharp
    internal class CommentAdornmentManager
        {
        }
    ```

4. Přidejte některá soukromá pole.

    ```csharp
    private readonly IWpfTextView view;
    private readonly IAdornmentLayer layer;
    private readonly CommentAdornmentProvider provider;
    ```

5. Přidejte konstruktor, který přihlašuje správce k <xref:Microsoft.VisualStudio.Text.Editor.ITextView.LayoutChanged> <xref:Microsoft.VisualStudio.Text.Editor.ITextView.Closed> událostem a, a také k `CommentsChanged` události. Konstruktor je privátní, protože má správce vytvořenou statickou `Create()` metodou.

    ```csharp
    private CommentAdornmentManager(IWpfTextView view)
    {
        this.view = view;
        this.view.LayoutChanged += OnLayoutChanged;
        this.view.Closed += OnClosed;

        this.layer = view.GetAdornmentLayer("CommentAdornmentLayer");

        this.provider = CommentAdornmentProvider.Create(view);
        this.provider.CommentsChanged += OnCommentsChanged;
    }
    ```

6. Přidejte `Create()` metodu, která získá zprostředkovatele, nebo ho v případě potřeby vytvořte.

    ```csharp
    public static CommentAdornmentManager Create(IWpfTextView view)
    {
        return view.Properties.GetOrCreateSingletonProperty<CommentAdornmentManager>(delegate { return new CommentAdornmentManager(view); });
    }
    ```

7. Přidejte `CommentsChanged` obslužnou rutinu.

    ```csharp
    private void OnCommentsChanged(object sender, CommentsChangedEventArgs e)
    {
        //Remove the comment (when the adornment was added, the comment adornment was used as the tag). 
        if (e.CommentRemoved != null)
            this.layer.RemoveAdornmentsByTag(e.CommentRemoved);

        //Draw the newly added comment (this will appear immediately: the view does not need to do a layout). 
        if (e.CommentAdded != null)
            this.DrawComment(e.CommentAdded);
    }
    ```

8. Přidejte <xref:Microsoft.VisualStudio.Text.Editor.ITextView.Closed> obslužnou rutinu.

    ```csharp
    private void OnClosed(object sender, EventArgs e)
    {
        this.provider.Detach();
        this.view.LayoutChanged -= OnLayoutChanged;
        this.view.Closed -= OnClosed;
    }
    ```

9. Přidejte <xref:Microsoft.VisualStudio.Text.Editor.ITextView.LayoutChanged> obslužnou rutinu.

    ```csharp
    private void OnLayoutChanged(object sender, TextViewLayoutChangedEventArgs e)
    {
        //Get all of the comments that intersect any of the new or reformatted lines of text.
        List<CommentAdornment> newComments = new List<CommentAdornment>();

        //The event args contain a list of modified lines and a NormalizedSpanCollection of the spans of the modified lines.  
        //Use the latter to find the comments that intersect the new or reformatted lines of text. 
        foreach (Span span in e.NewOrReformattedSpans)
        {
            newComments.AddRange(this.provider.GetComments(new SnapshotSpan(this.view.TextSnapshot, span)));
        }

        //It is possible to get duplicates in this list if a comment spanned 3 lines, and the first and last lines were modified but the middle line was not. 
        //Sort the list and skip duplicates.
        newComments.Sort(delegate(CommentAdornment a, CommentAdornment b) { return a.GetHashCode().CompareTo(b.GetHashCode()); });

        CommentAdornment lastComment = null;
        foreach (CommentAdornment comment in newComments)
        {
            if (comment != lastComment)
            {
                lastComment = comment;
                this.DrawComment(comment);
            }
        }
    }
    ```

10. Přidejte soukromou metodu, která nakreslí komentář.

     [!code-csharp[VSSDKMenuCommandTest#35](../extensibility/codesnippet/CSharp/walkthrough-using-a-shell-command-with-an-editor-extension_3.cs)]
     [!code-vb[VSSDKMenuCommandTest#35](../extensibility/codesnippet/VisualBasic/walkthrough-using-a-shell-command-with-an-editor-extension_3.vb)]

## <a name="use-the-menu-command-to-add-the-comment-adornment"></a>Pomocí příkazu nabídky přidejte doplňky komentáře.
 Pomocí příkazu nabídky můžete vytvořit dodatečnou poznámku implementací `MenuItemCallback` metody VSPackage.

1. Do projektu MenuCommandTest přidejte následující odkazy:

    - Microsoft. VisualStudio. TextManager. Interop

    - Microsoft. VisualStudio. Editor

    - Microsoft. VisualStudio. text. UI. WPF

2. Otevřete soubor *AddAdornment.cs* a přidejte následující `using` direktivy.

    ```csharp
    using Microsoft.VisualStudio.TextManager.Interop;
    using Microsoft.VisualStudio.Text.Editor;
    using Microsoft.VisualStudio.Editor;
    using CommentAdornmentTest;
    ```

3. Odstraňte `Execute()` metodu a přidejte následující obslužnou rutinu příkazu.

    ```csharp
    private async void AddAdornmentHandler(object sender, EventArgs e)
    {
    }
    ```

4. Přidejte kód pro získání aktivního zobrazení. `SVsTextManager`Chcete-li získat aktivní, musíte získat prostředí sady Visual Studio `IVsTextView` .

    ```csharp
    private async void AddAdornmentHandler(object sender, EventArgs e)
    {
        IVsTextManager txtMgr = (IVsTextManager) await ServiceProvider.GetServiceAsync(typeof(SVsTextManager));
        IVsTextView vTextView = null;
        int mustHaveFocus = 1;
        txtMgr.GetActiveView(mustHaveFocus, null, out vTextView);
    }
    ```

5. Pokud je toto textové zobrazení instancí zobrazení textu editoru, můžete ho přetypovat na <xref:Microsoft.VisualStudio.TextManager.Interop.IVsUserData> rozhraní a následně získat <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewHost> a jeho přidruženou hodnotu <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextView> . Použijte <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewHost> k volání `Connector.Execute()` metody, která získá poskytovatele přípravení komentáře a přidá doplňky. Obslužná rutina příkazu by teď měla vypadat jako tento kód:

    ```csharp
    private async void AddAdornmentHandler(object sender, EventArgs e)
    {
        IVsTextManager txtMgr = (IVsTextManager) await ServiceProvider.GetServiceAsync(typeof(SVsTextManager));
        IVsTextView vTextView = null;
        int mustHaveFocus = 1;
        txtMgr.GetActiveView(mustHaveFocus, null, out vTextView);
        IVsUserData userData = vTextView as IVsUserData;
         if (userData == null)
        {
            Console.WriteLine("No text view is currently open");
            return;
        }
        IWpfTextViewHost viewHost;
        object holder;
        Guid guidViewHost = DefGuidList.guidIWpfTextViewHost;
        userData.GetData(ref guidViewHost, out holder);
        viewHost = (IWpfTextViewHost)holder;
        Connector.Execute(viewHost);
    }
    ```

6. Nastavte metodu AddAdornmentHandler jako obslužnou rutinu pro příkaz AddAdornment v konstruktoru AddAdornment.

    ```csharp
    private AddAdornment(AsyncPackage package, OleMenuCommandService commandService)
    {
        this.package = package ?? throw new ArgumentNullException(nameof(package));
        commandService = commandService ?? throw new ArgumentNullException(nameof(commandService));

        var menuCommandID = new CommandID(CommandSet, CommandId);
        var menuItem = new MenuCommand(this.AddAdornmentHandler, menuCommandID);
        commandService.AddCommand(menuItem);
    }
    ```

## <a name="build-and-test-the-code"></a>Sestavení a testování kódu

1. Sestavte řešení a spusťte ladění. Měla by se zobrazit experimentální instance.

2. Vytvořte textový soubor. Zadejte nějaký text a pak ho vyberte.

3. V nabídce **nástroje** klikněte na **vyvolat přidat vylepšení**. Bublina by se měla zobrazit na pravé straně textového okna a měla by obsahovat text, který se podobá následujícímu textu.

     Uživatelské_jméno

     Fourscore...

## <a name="see-also"></a>Viz také
- [Návod: propojení typu obsahu s příponou názvu souboru](../extensibility/walkthrough-linking-a-content-type-to-a-file-name-extension.md)
