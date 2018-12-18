---
title: 'Návod: Použití příkazů prostředí s rozšířením editoru | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - add a menu command
ms.assetid: 08526848-a442-4cd4-afa1-b2eac2005adb
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 02ff8a2be0d13af193a204ee6711bf7dfa11dee7
ms.sourcegitcommit: ef828606e9758c7a42a2f0f777c57b2d39041ac3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/06/2018
ms.locfileid: "39566957"
---
# <a name="walkthrough-use-a-shell-command-with-an-editor-extension"></a>Návod: Použití příkazů prostředí s rozšířením editoru
Z balíčku VSPackage můžete přidat funkce, jako jsou příkazy do editoru. Tento návod ukazuje, jak přidat dalších úprav k zobrazení textu v editoru tak, že vyvolá příkaz nabídky.  
  
 Tento návod demonstruje použití VSPackage spolu s součást Managed Extensibility Framework (MEF). Je nutné použít VSPackage zaregistrovat příkaz nabídky prostředí sady Visual Studio. A příkaz slouží pro přístup k součást MEF.  
  
## <a name="prerequisites"></a>Požadavky  
 Spouští se v sadě Visual Studio 2015, nenainstalujete sadu Visual Studio SDK ze služby Stažení softwaru. Je zahrnutý jako volitelná funkce v instalačním programu sady Visual Studio. VS SDK můžete také nainstalovat později. Další informace najdete v tématu [instalace sady Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="create-an-extension-with-a-menu-command"></a>Vytvoření rozšíření pomocí příkazu nabídky  
 Vytvoření balíčku VSPackage, která umístí příkaz nabídky s názvem **přidání dalších úprav** na **nástroje** nabídky.  
  
1.  Vytvořte projekt VSIX C# s názvem `MenuCommandTest`a přidejte název šablony položky příkazu vlastní **AddAdornment**. Další informace najdete v tématu [vytváření rozšíření pomocí příkazu nabídky](../extensibility/creating-an-extension-with-a-menu-command.md).  
  
2.  Řešení s názvem MenuCommandTest se otevře. MenuCommandTestPackage soubor obsahuje kód, který vytvoří příkaz nabídky a umístí ji na **nástroje** nabídky. V tomto okamžiku příkaz právě způsobí, že se zobrazí okno se zprávou. Dalších krocích se ukazují, jak změnit k zobrazení dalších úprav komentář.  
  
3.  Otevřít *source.extension.vsixmanifest* souboru v editoru manifestu VSIX. `Assets` Karta by měla obsahovat řádek pro Microsoft.VisualStudio.VsPackage s názvem MenuCommandTest.  
  
4.  Uložte a zavřete *source.extension.vsixmanifest* souboru.  
  
## <a name="add-a-mef-extension-to-the-command-extension"></a>Přidat rozšíření rozhraní MEF pro rozšíření příkazu  
  
1.  V **Průzkumníka řešení**, klikněte pravým tlačítkem na uzel řešení, klikněte na tlačítko **přidat**a potom klikněte na tlačítko **nový projekt**. V **přidat nový projekt** dialogové okno, klikněte na tlačítko **rozšiřitelnost** pod **Visual C#**, pak **projekt VSIX**. Pojmenujte projekt `CommentAdornmentTest`.  
  
2.  Protože tento projekt bude komunikovat s sestavení se silným názvem balíčku VSPackage, musíte podepsat sestavení. Můžete znovu použít soubor klíče, které jsou vytvořeny již pro sestavení VSPackage.  
  
    1.  Otevřete vlastnosti projektu a vyberte **podepisování** kartu.  
  
    2.  Vyberte **podepsat sestavení**.  
  
    3.  V části **vyberte soubor klíče se silným názvem**, vyberte *klíč.snk* soubor, který byl vygenerován pro MenuCommandTest sestavení.  
  
## <a name="refer-to-the-mef-extension-in-the-vspackage-project"></a>Odkazovat na rozšíření MEF v projektu VSPackage  
 Protože přidáváte komponentu MEF do sady VSPackage, je nutné zadat oba typy prostředků v manifestu.  
  
> [!NOTE]
>  Další informace o rozhraní MEF, naleznete v tématu [Managed Extensibility Framework (MEF)](/dotnet/framework/mef/index).  
  
### <a name="to-refer-to-the-mef-component-in-the-vspackage-project"></a>K odkazování na Komponenta MEF v projektu VSPackage  
  
1.  V projektu MenuCommandTest otevřete *source.extension.vsixmanifest* souboru v editoru manifestu VSIX.  
  
2.  Na **prostředky** klikněte na tlačítko **nový**.  
  
3.  V **typ** klikněte na položku **Microsoft.VisualStudio.MefComponent**.  
  
4.  V **zdroj** klikněte na položku **projekt v aktuálním řešení**.  
  
5.  V **projektu** klikněte na položku **CommentAdornmentTest**.  
  
6.  Uložte a zavřete *source.extension.vsixmanifest* souboru.  
  
7.  Ujistěte se, že MenuCommandTest projekt má odkaz na projekt CommentAdornmentTest.  
  
8.  V projektu CommentAdornmentTest nastavte projekt k vytvoření sestavení. V **Průzkumníka řešení**, vyberte projekt a podívejte se **vlastnosti** okně **Kopírovat výstup sestavení na OutputDirectory** vlastnost a nastavte ho na **true**.  
  
## <a name="define-a-comment-adornment"></a>Definování dalších úprav komentář  
 Se skládá z dalších úprav komentář, samotné <xref:Microsoft.VisualStudio.Text.ITrackingSpan> vybraný text a některé řetězce, které představují Autor a popis textu, který sleduje.  
  
#### <a name="to-define-a-comment-adornment"></a>K definování dalších úprav komentář  
  
1.  V projektu CommentAdornmentTest přidejte nový soubor třídy a pojmenujte ho `CommentAdornment`.  
  
2.  Přidejte následující odkazy:  
  
    1.  Microsoft.VisualStudio.CoreUtility  
  
    2.  Microsoft.VisualStudio.Text.Data  
  
    3.  Microsoft.VisualStudio.Text.Logic  
  
    4.  Microsoft.VisualStudio.Text.UI  
  
    5.  Microsoft.VisualStudio.Text.UI.Wpf  
  
    6.  System.ComponentModel.Composition  
  
    7.  PresentationCore  
  
    8.  PresentationFramework  
  
    9. WindowsBase  
  
3.  Přidejte následující `using` příkazu.  
  
    ```vb  
    using Microsoft.VisualStudio.Text;  
    ```  
  
4.  Soubor by měl obsahovat třídu s názvem `CommentAdornment`.  
  
    ```csharp  
    internal class CommentAdornment  
    ```  
  
5.  Přidejte tři pole `CommentAdornment` třídy pro <xref:Microsoft.VisualStudio.Text.ITrackingSpan>, autor a popis.  
  
    ```csharp  
    public readonly ITrackingSpan Span;  
    public readonly string Author;  
    public readonly string Text;  
    ```  
  
6.  Přidáte konstruktor, který inicializuje pole.  
  
    ```csharp  
    public CommentAdornment(SnapshotSpan span, string author, string text)  
    {  
        this.Span = span.Snapshot.CreateTrackingSpan(span, SpanTrackingMode.EdgeExclusive);  
        this.Author = author;  
        this.Text = text;  
    }  
    ```  
  
## <a name="create-a-visual-element-for-the-adornment"></a>Vytvořit vizuální prvek pro dalších úprav  
 Definování vizuální prvek pro vaše dalších úprav. V tomto návodu, definovat ovládací prvek, který dědí z třídy Windows Presentation Foundation (WPF) <xref:System.Windows.Controls.Canvas>.  
  
1.  Vytvořte třídu v projektu CommentAdornmentTest a pojmenujte ho `CommentBlock`.  
  
2.  Přidejte následující `using` příkazy.  
  
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
  
3.  Ujistěte se, `CommentBlock` třída dědí <xref:System.Windows.Controls.Canvas>.  
  
    ```csharp  
    internal class CommentBlock : Canvas  
    { }  
    ```  
  
4.  Přidáte některé soukromé pole k definování visual aspektů dalších úprav.  
  
    ```csharp  
    private Geometry textGeometry;  
    private Grid commentGrid;  
    private static Brush brush;  
    private static Pen solidPen;  
    private static Pen dashPen;  
    ```  
  
5.  Přidáte konstruktor, který definuje dalších úprav komentář a přidá odpovídající text.  
  
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
  
6.  Implementovat taky <xref:System.Windows.Controls.Panel.OnRender%2A> obslužná rutina události, který vykreslí dalších úprav.  
  
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
 <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewCreationListener> Je, můžete použít k naslouchání zobrazíte události vytváření součást MEF.  
  
1.  Přidejte soubor třídy do projektu CommentAdornmentTest a pojmenujte ho `Connector`.  
  
2.  Přidejte následující `using` příkazy.  
  
    ```csharp  
    using System.ComponentModel.Composition;  
    using Microsoft.VisualStudio.Text.Editor;  
    using Microsoft.VisualStudio.Utilities;  
    ```  
  
3.  Deklarace třídy, která implementuje <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewCreationListener>a exportujte ho pomocí <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> "text" a <xref:Microsoft.VisualStudio.Text.Editor.TextViewRoleAttribute> z <xref:Microsoft.VisualStudio.Text.Editor.PredefinedTextViewRoles.Document>. Atribut typu obsahu určuje typ obsahu, ke kterému se vztahuje komponentu. Text typ je základním typem pro všechny typy souborů není binární. Téměř každá zobrazení textu, který je vytvořen proto bude tohoto typu. Atribut text zobrazení role určuje druh textové zobrazení, ke kterému se vztahuje komponentu. Role zobrazení textu dokumentu obecně zobrazit text, který se skládá z řádků a je uložen v souboru.  
  
     [!code-vb[VSSDKMenuCommandTest#11](../extensibility/codesnippet/VisualBasic/walkthrough-using-a-shell-command-with-an-editor-extension_1.vb)]
     [!code-csharp[VSSDKMenuCommandTest#11](../extensibility/codesnippet/CSharp/walkthrough-using-a-shell-command-with-an-editor-extension_1.cs)]  
  
4.  Implementace <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewCreationListener.TextViewCreated%2A> tak, že volání statické metody `Create()` událost `CommentAdornmentManager`.  
  
    ```csharp  
    public void TextViewCreated(IWpfTextView textView)  
    {  
        CommentAdornmentManager.Create(textView);  
    }  
    ```  
  
5.  Přidejte metodu, která můžete použít ke spuštění příkazu.  
  
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
  
## <a name="define-an-adornment-layer"></a>Definování vrstvu dalších úprav  
 Chcete-li přidat nový dalších úprav, je nutné definovat vrstvu dalších úprav.  
  
### <a name="to-define-an-adornment-layer"></a>Chcete-li definovat vrstvu dalších úprav  
  
1.  V `Connector` třídy, deklarujte veřejné pole s typem <xref:Microsoft.VisualStudio.Text.Editor.AdornmentLayerDefinition>a exportujte ho pomocí <xref:Microsoft.VisualStudio.Utilities.NameAttribute> , který určuje jedinečný název pro vrstvu dalších úprav a <xref:Microsoft.VisualStudio.Utilities.OrderAttribute> , který definuje vztah pořadí vykreslování této vrstvy dalších úprav na text Zobrazit vrstvy (text, blikajícího kurzoru a výběru).  
  
    ```csharp  
    [Export(typeof(AdornmentLayerDefinition))]  
    [Name("CommentAdornmentLayer")]  
    [Order(After = PredefinedAdornmentLayers.Selection, Before = PredefinedAdornmentLayers.Text)]  
    public AdornmentLayerDefinition commentLayerDefinition;  
  
    ```  
  
## <a name="provide-comment-adornments"></a>Zadejte komentář grafických doplňků  
 Při definování dalších úprav také implementujte zprostředkovatele dalších úprav komentář a dalších úprav manažera komentář. Zprostředkovatel dalších úprav komentář udržuje seznam vylepšení komentářů, naslouchá <xref:Microsoft.VisualStudio.Text.ITextBuffer.Changed> události na základní textovou vyrovnávací paměť a vylepšení komentář odstraní při odstranění základní text.  
  
1.  Přidejte nový soubor třídy do projektu CommentAdornmentTest a pojmenujte ho `CommentAdornmentProvider`.  
  
2.  Přidejte následující `using` příkazy.  
  
    ```csharp  
    using System;  
    using System.Collections.Generic;  
    using System.Collections.ObjectModel;  
    using Microsoft.VisualStudio.Text;  
    using Microsoft.VisualStudio.Text.Editor;  
    ```  
  
3.  Přidejte třídu pojmenovanou `CommentAdornmentProvider`.  
  
    ```csharp  
    internal class CommentAdornmentProvider  
    {  
    }  
    ```  
  
4.  Přidáte soukromé pole pro textovou vyrovnávací paměť a seznam vylepšení komentáře týkající se do vyrovnávací paměti.  
  
    ```csharp  
    private ITextBuffer buffer;  
    private IList<CommentAdornment> comments = new List<CommentAdornment>();  
  
    ```  
  
5.  Přidejte konstruktor pro `CommentAdornmentProvider`. Tento konstruktor by měl mít privátní přístup, protože zprostředkovatel je vytvořena instance, tak `Create()` metody. Přidá konstruktoru `OnBufferChanged` obslužnou rutinu události <xref:Microsoft.VisualStudio.Text.ITextBuffer.Changed> událostí.  
  
    ```csharp  
    private CommentAdornmentProvider(ITextBuffer buffer)  
    {  
        this.buffer = buffer;  
        //listen to the Changed event so we can react to deletions.   
        this.buffer.Changed += OnBufferChanged;  
    }  
  
    ```  
  
6.  Přidat `Create()` metody.  
  
    ```csharp  
    public static CommentAdornmentProvider Create(IWpfTextView view)  
    {  
        return view.Properties.GetOrCreateSingletonProperty<CommentAdornmentProvider>(delegate { return new CommentAdornmentProvider(view.TextBuffer); });  
    }  
  
    ```  
  
7.  Přidat `Detach()` metody.  
  
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
  
8.  Přidat `OnBufferChanged` obslužné rutiny události.  
  
    ```csharp  
    private void OnBufferChanged(object sender, TextContentChangedEventArgs e)  
    {  
        //Make a list of all comments that have a span of at least one character after applying the change. There is no need to raise a changed event for the deleted adornments. The adornments are deleted only if a text change would cause the view to reformat the line and discard the adornments.  
        IList<CommentAdornment> keptComments = new List<CommentAdornment>(this.comments.Count);  
  
        foreach (CommentAdornment comment in this.comments)  
        {  
            Span span = comment.Span.GetSpan(e.After);  
            //if a comment does not span at least one character, its text was deleted.   
            if (span.Length != 0)  
            {  
                keptComments.Add(comment);  
            }  
        }  
  
        this.comments = keptComments;  
    }  
  
    ```  
  
     [!code-csharp[VSSDKMenuCommandTest#21](../extensibility/codesnippet/CSharp/walkthrough-using-a-shell-command-with-an-editor-extension_2.cs)]
     [!code-vb[VSSDKMenuCommandTest#21](../extensibility/codesnippet/VisualBasic/walkthrough-using-a-shell-command-with-an-editor-extension_2.vb)]  
  
9. Přidat deklaraci `CommentsChanged` událostí.  
  
    ```csharp  
    public event EventHandler<CommentsChangedEventArgs> CommentsChanged;  
    ```  
  
10. Vytvoření `Add()` způsob, jak přidat dalších úprav.  
  
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
  
11. Přidat `RemoveComments()` metody.  
  
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
  
12. Přidat `GetComments()` metodu, která vrátí všechny komentáře v rozpětí daného snímku.  
  
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
  
13. Přidejte třídu pojmenovanou `CommentsChangedEventArgs`, následujícím způsobem.  
  
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
  
## <a name="manage-comment-adornments"></a>Správa vylepšení komentářů  
 Správce dalších úprav komentář vytvoří dalších úprav a přidá ji do vrstvy dalších úprav. Naslouchá na <xref:Microsoft.VisualStudio.Text.Editor.ITextView.LayoutChanged> a <xref:Microsoft.VisualStudio.Text.Editor.ITextView.Closed> události tak, že můžete přesunout nebo odstranit dalších úprav. Je také naslouchá `CommentsChanged` událost, která je vyvolána dalších úprav poskytovatelem komentář při přidávání nebo odebírání komentářů.  
  
1.  Přidejte soubor třídy do projektu CommentAdornmentTest a pojmenujte ho `CommentAdornmentManager`.  
  
2.  Přidejte následující `using` příkazy.  
  
    ```csharp  
    using System;  
    using System.Collections.Generic;  
    using System.Windows.Media;  
    using Microsoft.VisualStudio.Text;  
    using Microsoft.VisualStudio.Text.Editor;  
    using Microsoft.VisualStudio.Text.Formatting;  
    ```  
  
3.  Přidejte třídu pojmenovanou `CommentAdornmentManager`.  
  
    ```csharp  
    internal class CommentAdornmentManager  
        {  
        }  
    ```  
  
4.  Přidáte některé soukromé pole.  
  
    ```csharp  
    private readonly IWpfTextView view;  
    private readonly IAdornmentLayer layer;  
    private readonly CommentAdornmentProvider provider;  
    ```  
  
5.  Přidat konstruktor, který správce přihlásí <xref:Microsoft.VisualStudio.Text.Editor.ITextView.LayoutChanged> a <xref:Microsoft.VisualStudio.Text.Editor.ITextView.Closed> události a také do `CommentsChanged` události. Konstruktor je privátní, protože správce je vytvořena instance ve statické `Create()` metody.  
  
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
  
6.  Přidat `Create()` metodu, která získá zprostředkovatele, nebo v případě potřeby ho vytvoří.  
  
    ```csharp  
    public static CommentAdornmentManager Create(IWpfTextView view)  
    {  
        return view.Properties.GetOrCreateSingletonProperty<CommentAdornmentManager>(delegate { return new CommentAdornmentManager(view); });  
    }  
    ```  
  
7.  Přidat `CommentsChanged` obslužné rutiny.  
  
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
  
8.  Přidat <xref:Microsoft.VisualStudio.Text.Editor.ITextView.Closed> obslužné rutiny.  
  
    ```csharp  
    private void OnClosed(object sender, EventArgs e)  
    {  
        this.provider.Detach();  
        this.view.LayoutChanged -= OnLayoutChanged;  
        this.view.Closed -= OnClosed;  
    }  
    ```  
  
9. Přidat <xref:Microsoft.VisualStudio.Text.Editor.ITextView.LayoutChanged> obslužné rutiny.  
  
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
  
10. Přidejte privátní metodu, který vykreslí komentář.  
  
     [!code-csharp[VSSDKMenuCommandTest#35](../extensibility/codesnippet/CSharp/walkthrough-using-a-shell-command-with-an-editor-extension_3.cs)]
     [!code-vb[VSSDKMenuCommandTest#35](../extensibility/codesnippet/VisualBasic/walkthrough-using-a-shell-command-with-an-editor-extension_3.vb)]  
  
## <a name="use-the-menu-command-to-add-the-comment-adornment"></a>Použijte příkaz pro přidání dalších úprav komentář  
 Příkaz slouží k vytvoření grafického doplňku komentář implementací `MenuItemCallback` metoda sady VSPackage.  
  
1.  Přidejte následující odkazy projektu MenuCommandTest:  
  
    -   Microsoft.VisualStudio.TextManager.Interop  
  
    -   Microsoft.VisualStudio.Editor  
  
    -   Microsoft.VisualStudio.Text.UI.Wpf  
  
2.  Otevřít *AddAdornment.cs* soubor a přidejte následující `using` příkazy.  
  
    ```csharp  
    using Microsoft.VisualStudio.TextManager.Interop;  
    using Microsoft.VisualStudio.Text.Editor;  
    using Microsoft.VisualStudio.Editor;  
    using CommentAdornmentTest;  
    ```  
  
3.  Odstranit `ShowMessageBox()` metoda a přidejte následující obslužná rutina příkazu.  
  
    ```csharp  
    private void AddAdornmentHandler(object sender, EventArgs e)  
    {  
    }  
    ```  
  
4.  Přidejte kód pro získání aktivního zobrazení. Musíte získat `SVsTextManager` z prostředí sady Visual Studio, chcete-li získat aktivní `IVsTextView`.  
  
    ```csharp  
    private void AddAdornmentHandler(object sender, EventArgs e)  
    {  
        IVsTextManager txtMgr = (IVsTextManager)ServiceProvider.GetService(typeof(SVsTextManager));  
        IVsTextView vTextView = null;  
        int mustHaveFocus = 1;  
        txtMgr.GetActiveView(mustHaveFocus, null, out vTextView);  
    }  
    ```  
  
5.  Pokud zobrazení tohoto textu je instance zobrazení textu v editoru, můžete přetypovat na <xref:Microsoft.VisualStudio.TextManager.Interop.IVsUserData> rozhraní a potom <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewHost> spolu s přidruženými <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextView>. Použití <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewHost> volat `Connector.Execute()` metodu, která získá zprostředkovatele dalších úprav komentář a přidá dalších úprav. Obslužná rutina příkazu by teď měl vypadat přibližně takto:  
  
    ```csharp  
    private void AddAdornmentHandler(object sender, EventArgs e)  
    {  
        IVsTextManager txtMgr = (IVsTextManager)ServiceProvider.GetService(typeof(SVsTextManager));  
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
  
6.  Nastavení AddAdornmentHandler metody jako obslužnou rutinu pro příkaz AddAdornment v konstruktoru AddAdornment.  
  
    ```csharp  
    private AddAdornment(Package package)  
    {  
        if (package == null)  
        {  
            throw new ArgumentNullException(nameof(package));  
        }  
  
        this.package = package;  
  
        OleMenuCommandService commandService = this.ServiceProvider.GetService(typeof(IMenuCommandService)) as OleMenuCommandService;  
        if (commandService != null)  
        {  
            CommandID menuCommandID = new CommandID(MenuGroup, CommandId);  
            EventHandler eventHandler = this.AddAdornmentHandler;  
            MenuCommand menuItem = new MenuCommand(eventHandler, menuCommandID);  
            commandService.AddCommand(menuItem);  
        }  
    }  
    ```  
  
## <a name="build-and-test-the-code"></a>Vytváření a testování kódu  
  
1.  Sestavte řešení a spusťte ladění. Experimentální instanci aplikace by se zobrazit.  
  
2.  Vytvořte textový soubor. Zadejte nějaký text a vyberte ji.  
  
3.  Na **nástroje** nabídky, klikněte na tlačítko **vyvolat přidání dalších úprav**. Bublina zobrazeno na pravé straně textového okna a měl by obsahovat text, který vypadá podobně jako následující text.  
  
     Uživatelské_jméno  
  
     Fourscore...  
  
## <a name="see-also"></a>Viz také:  
 [Návod: Propojení typ obsahu, který má příponu názvu souboru](../extensibility/walkthrough-linking-a-content-type-to-a-file-name-extension.md)