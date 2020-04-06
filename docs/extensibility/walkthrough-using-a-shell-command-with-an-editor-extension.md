---
title: 'Návod: Použití příkazu prostředí s rozšířením editoru | Dokumenty společnosti Microsoft'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - add a menu command
ms.assetid: 08526848-a442-4cd4-afa1-b2eac2005adb
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 52b151b09c1bb7306b4270f9408d0f04a7600aa2
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80697169"
---
# <a name="walkthrough-use-a-shell-command-with-an-editor-extension"></a>Návod: Použití příkazu prostředí s rozšířením editoru
Z Balíčku VSPackage můžete do editoru přidat funkce, jako jsou příkazy nabídky. Tento návod ukazuje, jak přidat vylepšení do zobrazení textu v editoru vyvoláním příkazu nabídky.

 Tento návod ukazuje použití Součásti VSPackage společně s komponentou Mef (Managed Extensibility Framework). K registraci příkazu nabídky pomocí prostředí Sady Visual Studio je nutné použít příkaz VSPackage. A můžete použít příkaz pro přístup k součásti MEF.

## <a name="prerequisites"></a>Požadavky
 Počínaje Visual Studio 2015, nenainstalujete Visual Studio SDK ze služby stažení. Je součástí volitelné funkce v nastavení sady Visual Studio. VS SDK můžete také nainstalovat později. Další informace naleznete [v tématu Instalace sady Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="create-an-extension-with-a-menu-command"></a>Vytvoření rozšíření pomocí příkazu nabídky
 Vytvořte VSPackage, který umístí příkaz nabídky s názvem **Přidat vylepšení** v nabídce **Nástroje.**

1. Vytvořte projekt C# `MenuCommandTest`VSIX s názvem a přidejte název šablony položky custom command **addadornment**. Další informace naleznete [v tématu Vytvoření rozšíření pomocí příkazu nabídky](../extensibility/creating-an-extension-with-a-menu-command.md).

2. Otevře se řešení s názvem MenuCommandTest. Soubor MenuCommandTestPackage má kód, který vytvoří příkaz nabídky a umístí jej do nabídky **Nástroje.** V tomto okamžiku příkaz pouze způsobí, že se zobrazí okno se zprávou. Pozdější kroky ukazují, jak to změnit, aby se zobrazila ozdoba komentáře.

3. Otevřete soubor *source.extension.vsixmanifest* v editoru manifestů VSIX. Karta `Assets` by měla mít řádek pro Microsoft.VisualStudio.VsPackage s názvem MenuCommandTest.

4. Uložte a zavřete soubor *source.extension.vsixmanifest.*

## <a name="add-a-mef-extension-to-the-command-extension"></a>Přidání rozšíření MEF do rozšíření příkazů

1. V **Průzkumníku řešení**klikněte pravým tlačítkem myši na uzel řešení , klikněte na **přidat**a potom klikněte na **Nový projekt**. V dialogovém okně **Přidat nový projekt** klepněte na položku **Rozšiřitelnost** v části **Visual C#** a potom na **položku VSIX Project**. Pojmenujte `CommentAdornmentTest`projekt .

2. Vzhledem k tomu, že tento projekt bude pracovat se silným názvem VSPackage sestavení, musíte podepsat sestavení. Můžete znovu použít soubor klíče, který již byl vytvořen pro sestavení VSPackage.

    1. Otevřete vlastnosti projektu a vyberte kartu **Podpis.**

    2. Vyberte **Podepsat sestavení**.

    3. V části **Zvolte soubor klíče silného názvu**vyberte soubor *Key.snk,* který byl vygenerován pro sestavení MenuCommandTest.

## <a name="refer-to-the-mef-extension-in-the-vspackage-project"></a>Odkazovat na rozšíření MEF v projektu VSPackage
 Vzhledem k tomu, že přidáváte komponentu MEF do balíčku VSPackage, je nutné zadat oba druhy prostředků v manifestu.

> [!NOTE]
> Další informace o MEF naleznete [v tématu Spravované rozšíření framework (MEF)](/dotnet/framework/mef/index).

### <a name="to-refer-to-the-mef-component-in-the-vspackage-project"></a>Chcete-li odkazovat na součást MEF v projektu VSPackage

1. V projektu MenuCommandTest otevřete soubor *source.extension.vsixmanifest* v Editoru manifestů VSIX.

2. Na kartě **Datové zdroje** klikněte na **Nový**.

3. V seznamu **Typ** zvolte **Microsoft.VisualStudio.MefComponent**.

4. V seznamu **Zdroj** zvolte **Projekt A v aktuálním řešení**.

5. V seznamu **Projekt** zvolte **CommentAdornmentTest**.

6. Uložte a zavřete soubor *source.extension.vsixmanifest.*

7. Ujistěte se, že projekt MenuCommandTest obsahuje odkaz na projekt CommentAdornmentTest.

8. V projektu CommentAdornmentTest nastavte projekt k vytvoření sestavení. V **Průzkumníku řešení**vyberte projekt a vyhledejte v okně **Vlastnosti** **vlastnost Kopírovat výstup sestavení do outputdirectory** a nastavte ji na **hodnotu true**.

## <a name="define-a-comment-adornment"></a>Definování vylepšení komentáře
 Komentář adornment sám se <xref:Microsoft.VisualStudio.Text.ITrackingSpan> skládá z, který sleduje vybraný text a některé řetězce, které představují autora a popis textu.

#### <a name="to-define-a-comment-adornment"></a>Definování vylepšení komentáře

1. V projektu CommentAdornmentTest přidejte nový soubor `CommentAdornment`třídy a pojmenujte jej .

2. Přidejte následující odkazy:

    1. Microsoft.VisualStudio.CoreUtility

    2. Microsoft.VisualStudio.Text.Data

    3. Microsoft.VisualStudio.Text.Logic

    4. Microsoft.VisualStudio.Text.UI

    5. Microsoft.VisualStudio.Text.UI.Wpf

    6. System.ComponentModel.Složení

    7. Presentationcore

    8. Presentationframework

    9. Windowsbase

3. Přidejte `using` následující direktivu.

    ```csharp
    using Microsoft.VisualStudio.Text;
    ```

4. Soubor by měl obsahovat třídu s názvem `CommentAdornment`.

    ```csharp
    internal class CommentAdornment
    ```

5. Přidejte do `CommentAdornment` třídy <xref:Microsoft.VisualStudio.Text.ITrackingSpan>tři pole pro , autora a popis.

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

## <a name="create-a-visual-element-for-the-adornment"></a>Vytvoření vizuálního prvku pro vylepšení
 Definujte vizuální prvek pro vylepšení. Pro tento návod definujte ovládací prvek, který dědí z <xref:System.Windows.Controls.Canvas>třídy WPF (Windows Presentation Foundation).

1. Vytvořte třídu v projektu CommentAdornmentTest `CommentBlock`a pojmenujte ji .

2. Přidejte `using` následující direktivy.

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

3. Aby `CommentBlock` třída dědila z <xref:System.Windows.Controls.Canvas>.

    ```csharp
    internal class CommentBlock : Canvas
    { }
    ```

4. Přidejte některá soukromá pole a definujte vizuální aspekty vylepšení.

    ```csharp
    private Geometry textGeometry;
    private Grid commentGrid;
    private static Brush brush;
    private static Pen solidPen;
    private static Pen dashPen;
    ```

5. Přidejte konstruktor, který definuje vylepšení komentáře a přidá příslušný text.

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

6. Také implementovat obslužnou rutinu <xref:System.Windows.Controls.Panel.OnRender%2A> události, která kreslí vylepšení.

    ```csharp
    protected override void OnRender(DrawingContext dc)
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

## <a name="add-an-iwpftextviewcreationlistener"></a>Přidání iWpfTextViewCreationListener
 Je <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewCreationListener> součást součásti MEF, kterou můžete použít k zobrazení událostí vytváření.

1. Přidejte soubor třídy do projektu CommentAdornmentTest a pojmenujte jej `Connector`.

2. Přidejte `using` následující direktivy.

    ```csharp
    using System.ComponentModel.Composition;
    using Microsoft.VisualStudio.Text.Editor;
    using Microsoft.VisualStudio.Utilities;
    ```

3. Deklarujte třídu, která <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewCreationListener>implementuje , a exportujte ji s a <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> "text" a a <xref:Microsoft.VisualStudio.Text.Editor.TextViewRoleAttribute> . <xref:Microsoft.VisualStudio.Text.Editor.PredefinedTextViewRoles.Document> Atribut typu obsahu určuje druh obsahu, na který se komponenta vztahuje. Typ textu je základním typem pro všechny nebinární typy souborů. Proto téměř každé zobrazení textu, který je vytvořen bude tohoto typu. Atribut role zobrazení textu určuje druh zobrazení textu, na které se komponenta vztahuje. Role zobrazení textu dokumentu obvykle zobrazují text, který se skládá z řádků a je uložen v souboru.

     [!code-vb[VSSDKMenuCommandTest#11](../extensibility/codesnippet/VisualBasic/walkthrough-using-a-shell-command-with-an-editor-extension_1.vb)]
     [!code-csharp[VSSDKMenuCommandTest#11](../extensibility/codesnippet/CSharp/walkthrough-using-a-shell-command-with-an-editor-extension_1.cs)]

4. Implementujte <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewCreationListener.TextViewCreated%2A> metodu tak, `Create()` aby volá `CommentAdornmentManager`statickou událost .

    ```csharp
    public void TextViewCreated(IWpfTextView textView)
    {
        CommentAdornmentManager.Create(textView);
    }
    ```

5. Přidejte metodu, kterou můžete použít ke spuštění příkazu.

    ```csharp
    static public void Execute(IWpfTextViewHost host)
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

## <a name="define-an-adornment-layer"></a>Definování vrstvy vylepšení
 Chcete-li přidat novou vylepšení, musíte definovat vrstvu vylepšení.

### <a name="to-define-an-adornment-layer"></a>Definování vrstvy vylepšení

1. Ve `Connector` třídě deklarujte veřejné <xref:Microsoft.VisualStudio.Text.Editor.AdornmentLayerDefinition>pole typu a <xref:Microsoft.VisualStudio.Utilities.NameAttribute> exportujte jej s a, který <xref:Microsoft.VisualStudio.Utilities.OrderAttribute> určuje jedinečný název vrstvy vylepšení a který definuje vztah pořadí vykreslování této vrstvy vylepšení k ostatním vrstvám zobrazení textu (text, stříška a výběr).

    ```csharp
    [Export(typeof(AdornmentLayerDefinition))]
    [Name("CommentAdornmentLayer")]
    [Order(After = PredefinedAdornmentLayers.Selection, Before = PredefinedAdornmentLayers.Text)]
    public AdornmentLayerDefinition commentLayerDefinition;

    ```

## <a name="provide-comment-adornments"></a>Poskytnout vylepšení komentářů
 Při definování vylepšení, také implementovat zprostředkovatele vylepšení komentáře a správce vylepšení komentáře. Zprostředkovatel vylepšení komentáře udržuje seznam vylepšení komentáře, naslouchá <xref:Microsoft.VisualStudio.Text.ITextBuffer.Changed> událostem v základní textové vyrovnávací paměti a odstraní vylepšení komentáře při odstranění podkladového textu.

1. Přidejte nový soubor třídy do projektu CommentAdornmentTest a pojmenujte jej `CommentAdornmentProvider`.

2. Přidejte `using` následující direktivy.

    ```csharp
    using System;
    using System.Collections.Generic;
    using System.Collections.ObjectModel;
    using Microsoft.VisualStudio.Text;
    using Microsoft.VisualStudio.Text.Editor;
    ```

3. Přidejte třídu s názvem `CommentAdornmentProvider`.

    ```csharp
    internal class CommentAdornmentProvider
    {
    }
    ```

4. Přidejte soukromá pole pro textovou vyrovnávací paměť a seznam vylepšení komentářů souvisejících s vyrovnávací pamětí.

    ```csharp
    private ITextBuffer buffer;
    private IList<CommentAdornment> comments = new List<CommentAdornment>();

    ```

5. Přidejte konstruktor `CommentAdornmentProvider`pro . Tento konstruktor by měl mít soukromý přístup, protože `Create()` zprostředkovatel je vytvořena instance metodou. Konstruktor přidá `OnBufferChanged` obslužnou rutinu události do <xref:Microsoft.VisualStudio.Text.ITextBuffer.Changed> události.

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
    public static CommentAdornmentProvider Create(IWpfTextView view)
    {
        return view.Properties.GetOrCreateSingletonProperty<CommentAdornmentProvider>(delegate { return new CommentAdornmentProvider(view.TextBuffer); });
    }

    ```

7. Přidejte `Detach()` metodu.

    ```csharp
    public void Detach()
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

9. Přidejte deklaraci `CommentsChanged` události.

    ```csharp
    public event EventHandler<CommentsChangedEventArgs> CommentsChanged;
    ```

10. Vytvořte `Add()` metodu pro přidání vylepšení.

    ```csharp
    public void Add(SnapshotSpan span, string author, string text)
    {
        if (span.Length == 0)
            throw new ArgumentOutOfRangeException("span");
        if (author == null)
            throw new ArgumentNullException("author");
        if (text == null)
            throw new ArgumentNullException("text");

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
    public void RemoveComments(SnapshotSpan span)
    {
        EventHandler<CommentsChangedEventArgs> commentsChanged = this.CommentsChanged;

        //Get a list of all the comments that are being kept
        IList<CommentAdornment> keptComments = new List<CommentAdornment>(this.comments.Count);

        foreach (CommentAdornment comment in this.comments)
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
        foreach (CommentAdornment comment in this.comments)
        {
            if (comment.Span.GetSpan(span.Snapshot).OverlapsWith(span))
                overlappingComments.Add(comment);
        }

        return new Collection<CommentAdornment>(overlappingComments);
    }
    ```

13. Přidejte třídu s názvem `CommentsChangedEventArgs`, takto.

    ```csharp
    internal class CommentsChangedEventArgs : EventArgs
    {
        public readonly CommentAdornment CommentAdded;

        public readonly CommentAdornment CommentRemoved;

        public CommentsChangedEventArgs(CommentAdornment added, CommentAdornment removed)
        {
            this.CommentAdded = added;
            this.CommentRemoved = removed;
        }
    }
    ```

## <a name="manage-comment-adornments"></a>Správa vylepšení komentářů
 Správce vylepšení komentáře vytvoří vylepšení a přidá ji do vrstvy vylepšení. Naslouchá <xref:Microsoft.VisualStudio.Text.Editor.ITextView.LayoutChanged> události a <xref:Microsoft.VisualStudio.Text.Editor.ITextView.Closed> tak, aby jej můžete přesunout nebo odstranit vylepšení. Naslouchá také `CommentsChanged` události, která je aktivována zprostředkovatele vylepšení komentáře při přidávání nebo odebírání komentáře.

1. Přidejte soubor třídy do projektu CommentAdornmentTest a pojmenujte jej `CommentAdornmentManager`.

2. Přidejte `using` následující direktivy.

    ```csharp
    using System;
    using System.Collections.Generic;
    using System.Windows.Media;
    using Microsoft.VisualStudio.Text;
    using Microsoft.VisualStudio.Text.Editor;
    using Microsoft.VisualStudio.Text.Formatting;
    ```

3. Přidejte třídu s názvem `CommentAdornmentManager`.

    ```csharp
    internal class CommentAdornmentManager
        {
        }
    ```

4. Přidejte některá soukromá pole.

    ```csharp
    private readonly IWpfTextView view;
    private readonly IAdornmentLayer layer;
    private readonly CommentAdornmentProvider provider;
    ```

5. Přidejte konstruktor, který odečte <xref:Microsoft.VisualStudio.Text.Editor.ITextView.LayoutChanged> <xref:Microsoft.VisualStudio.Text.Editor.ITextView.Closed> správce a události `CommentsChanged` a také události. Konstruktor je soukromý, protože správce je vytvořen `Create()` statickou metodou.

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

6. Přidejte `Create()` metodu, která získá zprostředkovatele nebo jej v případě potřeby vytvoří.

    ```csharp
    public static CommentAdornmentManager Create(IWpfTextView view)
    {
        return view.Properties.GetOrCreateSingletonProperty<CommentAdornmentManager>(delegate { return new CommentAdornmentManager(view); });
    }
    ```

7. Přidejte `CommentsChanged` obslužnou rutinu.

    ```csharp
    private void OnCommentsChanged(object sender, CommentsChangedEventArgs e)
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
    private void OnClosed(object sender, EventArgs e)
    {
        this.provider.Detach();
        this.view.LayoutChanged -= OnLayoutChanged;
        this.view.Closed -= OnClosed;
    }
    ```

9. Přidejte <xref:Microsoft.VisualStudio.Text.Editor.ITextView.LayoutChanged> obslužnou rutinu.

    ```csharp
    private void OnLayoutChanged(object sender, TextViewLayoutChangedEventArgs e)
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

## <a name="use-the-menu-command-to-add-the-comment-adornment"></a>Přidání vylepšení komentáře pomocí příkazu menu
 Příkaz nabídky můžete použít k vytvoření vylepšení komentáře `MenuItemCallback` implementací metody VSPackage.

1. Přidejte následující odkazy do projektu MenuCommandTest:

    - Microsoft.VisualStudio.TextManager.Interop

    - Microsoft.VisualStudio.Editor

    - Microsoft.VisualStudio.Text.UI.Wpf

2. Otevřete soubor *AddAdornment.cs* a `using` přidejte následující direktivy.

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

4. Přidáním kódu získáte aktivní zobrazení. Chcete-li `SVsTextManager` získat aktivní prostředí sady Visual `IVsTextView`Studio, musíte získat prostředí Visual Studio.

    ```csharp
    private async void AddAdornmentHandler(object sender, EventArgs e)
    {
        IVsTextManager txtMgr = (IVsTextManager) await ServiceProvider.GetServiceAsync(typeof(SVsTextManager));
        IVsTextView vTextView = null;
        int mustHaveFocus = 1;
        txtMgr.GetActiveView(mustHaveFocus, null, out vTextView);
    }
    ```

5. Pokud je toto textové zobrazení instancí třídy textového zobrazení editoru, můžete jej přetypovat do <xref:Microsoft.VisualStudio.TextManager.Interop.IVsUserData> rozhraní a potom získat <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewHost> a jeho přidružené <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextView>. Použijte <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewHost> volání `Connector.Execute()` metody, která získá zprostředkovatele vylepšení komentáře a přidá vylepšení. Obslužná rutina příkazu by nyní měla vypadat jako tento kód:

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

6. Nastavte metodu AddAdornmentHandler jako obslužnou rutinu příkazu AddAdornment v konstruktoru AddAdornment.

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

1. Sestavte řešení a začněte ladit. Experimentální instance by se měla zobrazit.

2. Vytvořte textový soubor. Zadejte nějaký text a vyberte ho.

3. V nabídce **Nástroje** klepněte na **tlačítko Vyvolat přidání ozdoby**. Bublina by se měla zobrazit na pravé straně textového okna a měla by obsahovat text, který se podobá následujícímu textu.

     Vašeuživatelské jméno

     Čtyřka...

## <a name="see-also"></a>Viz také
- [Návod: Propojení typu obsahu s příponou názvu souboru](../extensibility/walkthrough-linking-a-content-type-to-a-file-name-extension.md)
