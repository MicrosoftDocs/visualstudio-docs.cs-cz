---
title: Úvod do WPF | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: b8d7cf43-d1f2-4f3d-adb0-4f3a6428edc0
caps.latest.revision: 7
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: b29e4e241589134c8dfa5b94e997d6603b075ee3
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49826346"
---
# <a name="introduction-to-wpf"></a>Úvod do WPF
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Windows Presentation Foundation (WPF) umožňuje vytvářet klasické pracovní plochy klienta aplikace pro Windows s vizuálně působivým uživatelským prostředím.  
  
 ![Ukázka uživatelského rozhraní Healthcare contoso](../designers/media/wpfintrofigure24.png "WPFIntroFigure24")  
  
 Základní WPF je nezávislé na řešení a vektorové vykreslování modul, který je sestaven využít moderní grafický hardware. WPF rozšiřuje základní s komplexní sadou funkcí vývoj aplikací, které zahrnují Extensible Application Markup Language (XAML), ovládací prvky, datové vazby, rozložení, 2D a 3D grafiky, animace, styly, šablony, dokumenty, média, text, a Typografie. WPF je součástí rozhraní .NET Framework, takže můžete vytvářet aplikace, které zahrnují další prvky v knihovně tříd rozhraní .NET Framework.  
  
 Tento přehled je určená pro nové uživatele a popisuje klíčové funkce a koncepty WPF.  
  
##  <a name="Programming_with_WPF"></a> Programování s WPF  
 WPF existuje jako podmnožinu typů rozhraní .NET Framework, které se nacházejí ve většině případů v <xref:System.Windows> oboru názvů. Pokud máte dříve vytvořenou aplikace pomocí rozhraní .NET Framework pomocí spravované technologie, jako je ASP.NET a Windows Forms, by měla být základní WPF programovací prostředí známých; Vytvoření instance třídy, nastavte vlastnosti, volání metody a události popisovač, všechny pomocí oblíbeného programovacího jazyka, jako je C# nebo Visual Basic .NET.  
  
 WPF obsahuje další programovací konstrukce, které zlepšují vlastnosti a události: [vlastnosti závislosti](https://msdn.microsoft.com/library/ms752914\(v=vs.100\).aspx) a [směrovaných událostí](https://msdn.microsoft.com/library/ms742806\(v=vs.100\).aspx).  
  
##  <a name="Markup_And_Codebehind"></a> Značky a modelu Code-Behind  
 WPF umožňuje vyvíjet aplikace pomocí obou *značek* a *použití modelu code-behind*, prostředí, které by měl být obeznámeni s vývojáře využívající technologii ASP.NET. Značky XAML se obvykle používají k implementaci vzhledu aplikace při používání spravovaného programovacích jazyků (použití modelu code-behind) k implementaci jeho chování. Toto oddělení vzhled a chování má následující výhody:  
  
- Náklady na vývoj a údržbu jsou snížit, protože specifické pro vzhled značky není pevně spojená s konkrétní chování kódu.  
  
- Vývoj je mnohem efektivnější, protože Návrháři můžete implementovat vzhled aplikace současně s vývojáři, kteří implementují chování aplikace.  
  
- [Globalizace a lokalizace](https://msdn.microsoft.com/library/ms788718\(v=vs.100\).aspx) pro WPF aplikace zjednodušeno.  
  
  Následuje stručný úvod do WPF značek a kódu.  
  
### <a name="markup"></a>Značky  
 XAML je jazyk založený na formátu XML kód, který se používá k implementaci aplikace vzhled deklarativně. To se obvykle používá k vytvoření systému windows, dialogová okna, stránky a uživatelské ovládací prvky a jejich vyplníte ovládací prvky, tvary a grafické.  
  
 Následující příklad používá k implementaci vzhled okno, které obsahuje jedno tlačítko XAML.  
  
```xaml  
<Window  
    xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"  
    Title="Window with Button"  
    Width="250" Height="100">  
  
  <!-- Add button to window -->  
  <Button Name="button">Click Me!</Button>  
  
</Window>  
```  
  
 Konkrétně tento XAML definuje tlačítka a okna s použitím `Window` a `Button` prvků, v uvedeném pořadí. Každý prvek má nakonfigurovanou atributy, jako například `Window` elementu `Title` atribut zadat text záhlaví okna. WPF v době běhu, převede prvky a atributy, které jsou definovány ve značkách pro instance tříd WPF. Například `Window` element je převeden na instanci <xref:System.Windows.Window> třídy, jejichž <xref:System.Windows.Window.Title%2A> vlastnost je hodnota `Title` atribut.  
  
 Následující obrázek ukazuje uživatelské rozhraní (UI), který je definován pomocí XAML v předchozím příkladu.  
  
 ![Okno, které obsahuje tlačítko](../designers/media/wpfintrofigure10.png "WPFIntroFigure10")  
  
 Protože XAML je založený na formátu XML, rozhraní, které vytváříte s ním je sestavena v hierarchii označované jako vnořené elementy [stromem prvků](https://msdn.microsoft.com/library/ms753391\(v=vs.100\).aspx). Strom prvku poskytuje logické a intuitivní způsob, jak vytvářet a spravovat uživatelská rozhraní.  
  
### <a name="code-behind"></a>Použití modelu Code-Behind  
 Hlavní chování aplikace je k implementaci funkcionality, která bude reagovat na akce uživatele, včetně zpracování událostí (například klepnutí na tlačítko, panel nástrojů nebo nabídky) a volání obchodní logika a logika přístupu k datům v odpovědi. V objektu WPF toto chování obecně implementovat v kódu, který je přidružený kód. Tento typ kódu se označuje jako použití modelu code-behind. Následující příklad ukazuje aktualizovaný kód z předchozího příkladu a modelu code-behind.  
  
```xaml  
<Window  
    xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"  
    xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"  
    x:Class="SDKSample.AWindow"  
    Title="Window with Button"  
    Width="250" Height="100">  
  
  <!-- Add button to window -->  
  <Button Name="button" Click="button_Click">Click Me!</Button>  
  
</Window>  
```  
  
```csharp  
using System.Windows; // Window, RoutedEventArgs, MessageBox   
  
namespace SDKSample  
{  
    public partial class AWindow : Window  
    {  
        public AWindow()  
        {  
            // InitializeComponent call is required to merge the UI   
            // that is defined in markup with this class, including    
            // setting properties and registering event handlers  
            InitializeComponent();  
        }  
  
        void button_Click(object sender, RoutedEventArgs e)  
        {  
            // Show message box when button is clicked  
            MessageBox.Show("Hello, Windows Presentation Foundation!");  
        }  
    }  
}  
```  
  
```vb  
Namespace SDKSample  
  
    Partial Public Class AWindow  
        Inherits System.Windows.Window  
  
        Public Sub New()  
  
            ' InitializeComponent call is required to merge the UI   
            ' that is defined in markup with this class, including    
            ' setting properties and registering event handlers  
            InitializeComponent()  
  
        End Sub   
  
        Private Sub button_Click(ByVal sender As Object, ByVal e As RoutedEventArgs)  
  
            ' Show message box when button is clicked  
            MessageBox.Show("Hello, Windows Presentation Foundation!")  
  
        End Sub   
  
    End Class   
  
End Namespace  
  
```  
  
 V tomto příkladu modelu code-behind implementuje třídu, která je odvozena z <xref:System.Windows.Window> třídy. `x:Class` Atribut se používá k použití modelu code-behind třídě přiřadit značky. `InitializeComponent` je volána z konstruktoru třídy modelu code-behind sloučit uživatelského rozhraní, která je definována v kódu pomocí třídy modelu code-behind. (`InitializeComponent` se vygeneruje pro vás, když vaše aplikace je sestavena, proto není nutné provádět ručně.) Kombinace `x:Class` a `InitializeComponent` Ujistěte se, že implementace je správně inicializována pokaždé, když se vytvoří. Použití modelu code-behind třída také implementuje obslužné rutiny události na tlačítku pro <xref:System.Windows.Controls.Primitives.ButtonBase.Click> událostí. Při kliknutí na tlačítko obslužná rutina události se zobrazí okno se zprávou voláním <xref:System.Windows.MessageBox.Show%2A?displayProperty=fullName> metody.  
  
 Následující obrázek ukazuje výsledek, po kliknutí na tlačítko.  
  
 ![Pole MessageBox](../designers/media/wpfintrofigure25.png "WPFIntroFigure25")  
  
##  <a name="Controls"></a> Ovládací prvky  
 Uživatelské prostředí, které se dodávají pomocí aplikačního modelu se vytvořený ovládací prvky. V subsystému WPF "control" se o zastřešující pojem, který se vztahuje na kategorii WPF tříd, které jsou hostované v okně nebo na stránce, uživatelské rozhraní a implementaci některých chování.  
  
 Další informace najdete v tématu [ovládací prvky](http://msdn.microsoft.com/library/3f255a8a-35a8-4712-9065-472ff7d75599).  
  
### <a name="wpf-controls-by-function"></a>Ovládací prvky WPF podle funkce  
 Tady jsou uvedené integrovaných ovládacích prvků WPF.  
  
-   **Tlačítka**: <xref:System.Windows.Controls.Button> a <xref:System.Windows.Controls.Primitives.RepeatButton>.  
  
-   **Zobrazení dat**: <xref:System.Windows.Controls.DataGrid>, <xref:System.Windows.Controls.ListView>, a <xref:System.Windows.Controls.TreeView>.  
  
-   **Data zobrazení a výběr**: <xref:System.Windows.Controls.Calendar> a <xref:System.Windows.Controls.DatePicker>.  
  
-   **Dialogová okna**: <xref:Microsoft.Win32.OpenFileDialog>, <xref:System.Windows.Controls.PrintDialog>, a <xref:Microsoft.Win32.SaveFileDialog>.  
  
-   **Digitální inkoust**: <xref:System.Windows.Controls.InkCanvas> a <xref:System.Windows.Controls.InkPresenter>.  
  
-   **Dokumenty**: <xref:System.Windows.Controls.DocumentViewer>, <xref:System.Windows.Controls.FlowDocumentPageViewer>, <xref:System.Windows.Controls.FlowDocumentReader>, <xref:System.Windows.Controls.FlowDocumentScrollViewer>, a <xref:System.Windows.Controls.StickyNoteControl>.  
  
-   **Vstup**: <xref:System.Windows.Controls.TextBox>, <xref:System.Windows.Controls.RichTextBox>, a <xref:System.Windows.Controls.PasswordBox>.  
  
-   **Rozložení**: <xref:System.Windows.Controls.Border>, <xref:System.Windows.Controls.Primitives.BulletDecorator>, <xref:System.Windows.Controls.Canvas>, <xref:System.Windows.Controls.DockPanel>, <xref:System.Windows.Controls.Expander>, <xref:System.Windows.Controls.Grid>, <xref:System.Windows.Controls.GridView>, <xref:System.Windows.Controls.GridSplitter>, <xref:System.Windows.Controls.GroupBox>, <xref:System.Windows.Controls.Panel>, <xref:System.Windows.Controls.Primitives.ResizeGrip>, <xref:System.Windows.Controls.Separator>, <xref:System.Windows.Controls.Primitives.ScrollBar>, <xref:System.Windows.Controls.ScrollViewer>, <xref:System.Windows.Controls.StackPanel>, <xref:System.Windows.Controls.Primitives.Thumb>, <xref:System.Windows.Controls.Viewbox>, <xref:System.Windows.Controls.VirtualizingStackPanel>, <xref:System.Windows.Window>, a <xref:System.Windows.Controls.WrapPanel>.  
  
-   **Média**: <xref:System.Windows.Controls.Image>, <xref:System.Windows.Controls.MediaElement>, a <xref:System.Windows.Controls.SoundPlayerAction>.  
  
-   **Nabídky**: <xref:System.Windows.Controls.ContextMenu>, <xref:System.Windows.Controls.Menu>, a <xref:System.Windows.Controls.ToolBar>.  
  
-   **Navigace**: <xref:System.Windows.Controls.Frame>, <xref:System.Windows.Documents.Hyperlink>, <xref:System.Windows.Controls.Page>, <xref:System.Windows.Navigation.NavigationWindow>, a <xref:System.Windows.Controls.TabControl>.  
  
-   **Výběr**: <xref:System.Windows.Controls.CheckBox>, <xref:System.Windows.Controls.ComboBox>, <xref:System.Windows.Controls.ListBox>, <xref:System.Windows.Controls.RadioButton>, a <xref:System.Windows.Controls.Slider>.  
  
-   **Informace o uživateli**: <xref:System.Windows.Controls.AccessText>, <xref:System.Windows.Controls.Label>, <xref:System.Windows.Controls.Primitives.Popup>, <xref:System.Windows.Controls.ProgressBar>, <xref:System.Windows.Controls.Primitives.StatusBar>, <xref:System.Windows.Controls.TextBlock>, a <xref:System.Windows.Controls.ToolTip>.  
  
##  <a name="Input_And_Commanding"></a> Vstup a příkazů  
 Ovládací prvky nejčastěji detekovat a reagovat na vstup uživatele. [WPF vstup systému](https://msdn.microsoft.com/library/ms754010\(v=vs.100\).aspx) používá s přímým přístupem a směrovaných událostí pro podporu zadávání textu, správu fokus a umístění myši.  
  
 Aplikace mají často složité vstupní požadavky. Poskytuje WPF [příkaz systému](https://msdn.microsoft.com/library/ms752308\(v=vs.100\).aspx) , který odděluje vstupní akcí uživatele z kódu, který reaguje na tyto akce.  
  
##  <a name="Layout"></a> Rozložení  
 Při vytváření uživatelského rozhraní, je uspořádat své ovládací prvky podle umístění a velikost formuláře rozložení. Klíčovým požadavkem žádné rozložení je a reagovat na změny velikosti okna nastavení zobrazení. Místo psaní kódu pro přizpůsobení rozložení v těchto případech je vynuceno, WPF poskytuje prvotřídní a rozšiřitelné rozložení systém za vás.  
  
 Základní kámen systém rozložení je relativní umístění, což zvyšuje schopnost přizpůsobit měnícím se okno a zobrazit podmínky. Kromě toho spravuje systém rozložení vyjednávání mezi ovládacími prvky k určení rozložení. Vyjednávání je dvoustupňový proces: nejprve ovládací prvek říká svého nadřazeného objektu, jaké umístění a velikost vyžaduje; za druhé nadřazené říká ovládací prvek jaké prostor může mít.  
  
 Systém rozložení je přístupný podřízených ovládacích prvků prostřednictvím základní třídy pro WPF. Pro běžné rozložení, jako je například mřížky, ukládání a dokování WPF obsahuje několik ovládacích prvků rozložení:  
  
- <xref:System.Windows.Controls.Canvas>: Podřízené ovládací prvky poskytují jejich vlastní rozložení.  
  
- <xref:System.Windows.Controls.DockPanel>: Podřízených ovládacích prvků je zarovnán okrajů panelu.  
  
- <xref:System.Windows.Controls.Grid>: Podřízené ovládací prvky jsou umístěny podle řádků a sloupců.  
  
- <xref:System.Windows.Controls.StackPanel>: Podřízené ovládací prvky jsou uspořádány vedle svisle nebo vodorovně.  
  
- <xref:System.Windows.Controls.VirtualizingStackPanel>: Podřízené ovládací prvky jsou virtualizované a uspořádány na jeden řádek, který je orientovaný buď vodorovně nebo svisle.  
  
- <xref:System.Windows.Controls.WrapPanel>: Podřízené ovládací prvky jsou umístěny v pořadí zleva doprava a zabalen na další řádek, když existují další ovládací prvky na aktuálním řádku než umožňuje místo.  
  
  Následující příklad používá <xref:System.Windows.Controls.DockPanel> rozložení několik <xref:System.Windows.Controls.TextBox> ovládacích prvků.  
  
  [!code-xml[IntroToWPFSnippets#LayoutMARKUP](../snippets/csharp/VS_Snippets_Wpf/IntroToWPFSnippets/CSharp/LayoutWindow.xaml#layoutmarkup)]  
  
  <xref:System.Windows.Controls.DockPanel> Umožňuje podřízené <xref:System.Windows.Controls.TextBox> ovládací prvky určit, jak uspořádat je. K tomu, <xref:System.Windows.Controls.DockPanel> implementuje <xref:System.Windows.Controls.DockPanel.Dock%2A> vlastnost, která je vystavena podřízených ovládacích prvků, aby každý z nich určit styl ukotvení.  
  
> [!NOTE]
>  Vlastnost, která je implementována pomocí nadřazený ovládací prvek pro použití podřízených ovládacích prvků je konstrukce WPF s názvem [přidružená vlastnost](https://msdn.microsoft.com/library/ms749011\(v=vs.100\).aspx).  
  
 Následující obrázek ukazuje výsledek z kódu XAML v předchozím příkladu.  
  
 ![Stránka DockPanel](../designers/media/wpfintrofigure11.png "WPFIntroFigure11")  
  
##  <a name="Data_Binding"></a> Vytváření datových vazeb  
 Většina aplikací se vytvoří uživatelům poskytnout způsob, jak zobrazit a upravit data. Pro aplikace WPF práci při ukládání a přístup k datům je již podle technologie, jako je SQL Server a ADO .NET. Po přístupu k datům a načtena do aplikací spravovaných objektů, začne těžkou práci pro aplikace WPF. V podstatě to zahrnuje dvě věci:  
  
1. Kopírování dat ze spravovaných objektů do ovládacích prvků, kde můžete zobrazit a upravovat data.  
  
2. Zajištění, že změny dat s použitím ovládacích prvků jsou zkopírovány zpět na spravované objekty.  
  
   Pro zjednodušení vývoje aplikací poskytuje WPF modul vazby dat automaticky provádět tyto kroky. Je základní jednotkou modul vazby dat <xref:System.Windows.Data.Binding> třídy, jehož úkolem je vytvoření vazby ovládacího prvku (cíl vazby) na datový objekt (zdroje připojení). Tento vztah je znázorněn v následujícím obrázku.  
  
   ![Diagram základní datové vazby](../designers/media/databindingmostbasic.png "DataBindingMostBasic")  
  
   Následující příklad ukazuje, jak vytvořit vazbu <xref:System.Windows.Controls.TextBox> do instance vlastního `Person` objektu. `Person` Implementace je znázorněno v následujícím kódu.  
  
   [!code-csharp[SimpleDataBindingSnippets#PersonClassCODE](../snippets/csharp/VS_Snippets_Wpf/SimpleDataBindingSnippets/CSharp/Person.cs#personclasscode)]
   [!code-vb[SimpleDataBindingSnippets#PersonClassCODE](../snippets/visualbasic/VS_Snippets_Wpf/SimpleDataBindingSnippets/VisualBasic/Person.vb#personclasscode)]  
  
   Následující kód vytvoří vazbu <xref:System.Windows.Controls.TextBox> do instance vlastního `Person` objektu.  
  
   [!code-xml[SimpleDataBindingSnippets#DataBindingMARKUP1](../snippets/csharp/VS_Snippets_Wpf/SimpleDataBindingSnippets/CSharp/DataBindingWindow.xaml#databindingmarkup1)]  
   [!code-xml[SimpleDataBindingSnippets#DataBindingMARKUP2](../snippets/csharp/VS_Snippets_Wpf/SimpleDataBindingSnippets/CSharp/DataBindingWindow.xaml#databindingmarkup2)]  
   [!code-xml[SimpleDataBindingSnippets#DataBindingMARKUP3](../snippets/csharp/VS_Snippets_Wpf/SimpleDataBindingSnippets/CSharp/DataBindingWindow.xaml#databindingmarkup3)]  
  
   [!code-csharp[SimpleDataBindingSnippets#DataBindingCODEBEHIND](../snippets/csharp/VS_Snippets_Wpf/SimpleDataBindingSnippets/CSharp/DataBindingWindow.xaml.cs#databindingcodebehind)]
   [!code-vb[SimpleDataBindingSnippets#DataBindingCODEBEHIND](../snippets/visualbasic/VS_Snippets_Wpf/SimpleDataBindingSnippets/VisualBasic/DataBindingWindow.xaml.vb#databindingcodebehind)]  
  
   V tomto příkladu `Person` třídy je vytvořena instance v kódu a je nastaven jako kontext dat pro `DataBindingWindow`. V kódu <xref:System.Windows.Controls.TextBox.Text%2A> vlastnost <xref:System.Windows.Controls.TextBox> je vázán na `Person.Name` vlastnosti (pomocí "`{Binding ... }`" syntaxe XAML). Tento XAML říká WPF se vytvořit vazbu <xref:System.Windows.Controls.TextBox> ovládací prvek `Person` objekt, který je uložen v <xref:System.Windows.FrameworkElement.DataContext%2A> vlastnost okna.  
  
   Modul vazby WPF dat poskytuje další podporu, která zahrnuje ověření, řazení, filtrování a seskupování. Kromě toho vytváření datových vazeb podporuje použití šablony k vytvoření vlastního uživatelského rozhraní pro vázaných dat při uživatelské rozhraní zobrazí standardní ovládací prvky WPF není vhodná.  
  
   Další informace najdete v tématu [přehled datových vazeb](https://msdn.microsoft.com/library/ms752347\(v=vs.100\).aspx).  
  
##  <a name="Graphics"></a> Grafika  
 WPF zavádí rozsáhlé, škálovatelné a flexibilní sadu grafické funkce, které mají následující výhody:  
  
-   **Nezávislé na řešení a nezávislé na zařízení grafiky**. Základní jednotka měření v systému WPF grafiky je nezávislé pixelů zařízení, což je 1/96 palce, bez ohledu na skutečné rozlišení obrazovky a poskytuje základ pro vykreslování nezávislé na řešení a nezávislé na zařízení. Každý pixel nezávislých na zařízení se automaticky škáluje tak, aby odpovídaly nastavení bodů na palec (dpi), který se vykreslí v systému.  
  
-   **Zlepšení přesnosti**. Systém souřadnic WPF se měří pomocí dvojité přesnosti s plovoucí desetinnou čárkou čísla spíše než s jednoduchou přesností. Transformace a krytí hodnoty jsou také vyjádřena dvojitou přesností. WPF také podporuje široká barevná škála (scRGB) a poskytuje integrovanou podporu pro správu vstupy od prostory jinou barvu.  
  
-   **Přidává rozšířenou podporu grafika a animace**. WPF zjednodušuje programování grafiky tím, že správa scén animace pro vás. není nutné se starat o zpracování scény, smyčky vykreslování a varianty interpolace. Kromě toho WPF poskytuje podporu pro spuštění testu a úplné skládání alfa.  
  
-   **Hardwarovou akceleraci**. Systém grafiky WPF využívá hardwarovou akceleraci k minimalizaci využití procesoru.  
  
### <a name="2-d-shapes"></a>2D obrazce  
 WPF poskytuje knihovnu běžných vykreslovaných vektoru 2D tvary, třeba obdélníky a symbol tří teček, která jsou zobrazena na následujícím obrázku.  
  
 ![Symbol tří teček a obdélníky](../designers/media/wpfintrofigure4.PNG "WPFIntroFigure4")  
  
 Zajímavé funkce tvarů je, že se nejedná jenom pro zobrazení; tvary implementovat řadu funkcí, které očekáváte, že z ovládacích prvků, včetně klávesnice a myši. Následující příklad ukazuje <xref:System.Windows.UIElement.MouseUp> události <xref:System.Windows.Shapes.Ellipse> zpracovává.  
  
 [!code-xml[IntroToWPFSnippets#HandleEllipseMouseUpEventMARKUP](../snippets/csharp/VS_Snippets_Wpf/IntroToWPFSnippets/CSharp/EllipseEventHandlingWindow.xaml#handleellipsemouseupeventmarkup)]  
  
 [!code-csharp[IntroToWPFSnippets#HandleEllipseMouseUpEventCODEBEHIND](../snippets/csharp/VS_Snippets_Wpf/IntroToWPFSnippets/CSharp/EllipseEventHandlingWindow.xaml.cs#handleellipsemouseupeventcodebehind)]
 [!code-vb[IntroToWPFSnippets#HandleEllipseMouseUpEventCODEBEHIND](../snippets/visualbasic/VS_Snippets_Wpf/IntroToWPFSnippets/VisualBasic/EllipseEventHandlingWindow.xaml.vb#handleellipsemouseupeventcodebehind)]  
  
 Následující obrázek znázorňuje, co je vytvořený v předchozím kódu.  
  
 ![Okno s textem "kliknutí na tři tečky&#33;"](../designers/media/wpfintrofigure12.png "WPFIntroFigure12")  
  
 Další informace najdete v tématu [tvary a základní kresby v přehledu WPF](https://msdn.microsoft.com/library/ms747393\(v=vs.100\).aspx).  
  
### <a name="2-d-geometries"></a>2D geometrie  
 2D obrazce poskytované WPF zahrnují standardní sadu základních tvarů. Můžete však vytvořit vlastní tvary, které usnadňují návrh přizpůsobené uživatelské rozhraní. K tomuto účelu poskytuje WPF geometrie. Následující obrázek znázorňuje použití geometrie vytvoříte vlastní obrazec, který lze vykreslit přímo, používá jako štětce nebo použít na jiné tvary a ovládací prvky.  
  
 <xref:System.Windows.Shapes.Path> objekty lze použít pro kreslení tvarů uzavřeného nebo otevřít, více tvarů a dokonce i zakřivené obrazce.  
  
 <xref:System.Windows.Media.Geometry> objekty lze použít pro oříznutí, spuštění testu a vykreslování 2D grafická data.  
  
 ![Různé možnosti použití cesty](../designers/media/wpfintrofigure5.PNG "WPFIntroFigure5")  
  
 Další informace najdete v tématu [přehled geometrie](https://msdn.microsoft.com/library/ms751808\(v=vs.100\).aspx)  
  
### <a name="2-d-effects"></a>2D efekty  
 Obsahuje podmnožinu WPF 2D možnosti vizuálních efektů, jako je například přechody, rastrových obrázků, kreseb Malování s využitím videí, otáčení, škálování a zkosení. Tyto jsou všechny dosáhnout pomocí štětců; Následující obrázek znázorňuje několik příkladů.  
  
 ![Znázornění různých štětců](../designers/media/wpfintrofigure6.PNG "WPFIntroFigure6")  
  
 Další informace najdete v tématu [přehled štětců WPF](https://msdn.microsoft.com/library/aa970904\(v=vs.100\).aspx).  
  
### <a name="3-d-rendering"></a>3D vykreslování  
 WPF obsahuje také možnosti 3D vykreslování, které se integrují s 2D grafika, aby se mohly vytvářet zajímavé a zajímavé uživatelská rozhraní. Například následující obrázek znázorňuje 2D imagí vykresleny také na tvarů 3D.  
  
 ![Snímek obrazovky ukázkové Visual3D](../designers/media/wpfintrofigure13.png "WPFIntroFigure13")  
  
 Další informace najdete v tématu [přehled 3D grafiky](https://msdn.microsoft.com/library/ms747437\(v=vs.100\).aspx).  
  
##  <a name="Animation"></a> Animace  
 Umožňuje podporu animace WPF, které provedete ovládací prvky zvětšení, zatřeste, typu číselník a fade, chcete-li vytvořit zajímavé stránce přechody a další. Lze animovat Většina tříd WPF, dokonce i vlastní třídy. Následující obrázek znázorňuje jednoduché animace v akci.  
  
 ![Bitové kopie animovaný datové krychle](../designers/media/wpfintrofigure7.png "WPFIntroFigure7")  
  
 Další informace najdete v tématu [přehled animace](https://msdn.microsoft.com/library/ms752312\(v=vs.100\).aspx).  
  
##  <a name="Media"></a> Média  
 Jedním ze způsobů předání formátovaného obsahu je prostřednictvím audiovizuální média. WPF podporuje speciální obrázky, videa a zvuku.  
  
### <a name="images"></a>Obrázky  
 Bitové kopie jsou společné pro většinu aplikací a WPF poskytuje několik způsobů, jak je používat. Následující obrázek ukazuje uživatelské rozhraní pomocí seznamu, který obsahuje obrázky miniatur. Pokud je vybrána miniatury, zobrazení obrázku reklamy.  
  
 ![Obrázky miniatur a úplné&#45;velikost obrázku](../designers/media/wpfintrofigure8.PNG "WPFIntroFigure8")  
  
 Další informace najdete v tématu [Imaging přehled](https://msdn.microsoft.com/library/ms748873\(v=vs.100\).aspx).  
  
### <a name="video-and-audio"></a>Videa a zvuku  
 <xref:System.Windows.Controls.MediaElement> Ovládací prvek je schopen přehrávání videa a zvuku, a je dostatečně flexibilní, aby se základ pro vlastní přehrávač. Následující kód XAML implementuje přehrávač médií.  
  
 [!code-xml[IntroToWPFSnippets#MediaElementMARKUP](../snippets/csharp/VS_Snippets_Wpf/IntroToWPFSnippets/CSharp/MediaElementWindow.xaml#mediaelementmarkup)]  
  
 V okně v následující obrázek ukazuje <xref:System.Windows.Controls.MediaElement> ovládacího prvku v akci.  
  
 ![Řízení elementu MediaElement pomocí audio a video](../designers/media/wpfintrofigure1.png "WPFIntroFigure1")  
  
 Další informace najdete v tématu [přehled média, animace a grafiky WPF](https://msdn.microsoft.com/library/ms742562\(v=vs.100\).aspx).  
  
##  <a name="Text_and_Typography"></a> Text a typografie  
 Pro usnadnění vykreslování textu v vysoce kvalitní, WPF nabízí následující funkce:  
  
- Podpora písmo OpenType.  
  
- ClearType – vylepšení.  
  
- Vysoký výkon, který využívá hardwarovou akceleraci.  
  
- Integrace textu pomocí média, grafika a animace.  
  
- Mezinárodní písma podpory a nouzového řešení ověření mechanismy.  
  
  Jako ukázkový text integrace s grafikou následující obrázek znázorňuje použití dekorace textu.  
  
  ![Text s různé textové dekorace](../designers/media/wpfintrofigure23.png "WPFIntroFigure23")  
  
  Další informace najdete v tématu [Typografie ve Windows Presentation Foundation](https://msdn.microsoft.com/library/ms742190\(v=vs.100\).aspx).  
  
##  <a name="WPF_Customization"></a> Přizpůsobení aplikace WPF  
 Do této chvíle jste viděli základní WPF stavební bloky pro vývoj aplikací. Aplikační model můžete použít k hostování a doručovat obsah aplikace, který se skládá převážně z ovládacích prvků. Pro zjednodušení uspořádání ovládacích prvků v uživatelském rozhraní a k Ujistěte se, že i v případě změny velikosti okna se udržuje uspořádání a nastavení zobrazení, použijete systém rozložení WPF. Vzhledem k tomu, že většina aplikací mít uživatelé povolenou interakci s daty, použít datovou vazbu ke snížení práci integrovat uživatelské rozhraní s daty. Pokud chcete zlepšit vzhled vaší aplikace, použijte komplexní rozsah obrázky, animace a média podpora poskytovaná WPF.  
  
 Často ale základní informace nejsou dostatečná pro vytváření a správa skutečně samostatný a vizuálně působivým činnost koncového uživatele. Standardní ovládací prvky WPF nebude možné integrovat požadovaný vzhled vaší aplikace. Data se nemusí zobrazit v nejúčinnějším způsobem. Celkové uživatelské prostředí pro vaše aplikace nemusí být vhodné výchozí vzhled a chování Windows motivů. Prezentace technologie mnoha způsoby, musí rozšíření produktu visual co jakýkoli jiný typ rozšíření.  
  
 Z tohoto důvodu WPF poskytuje širokou škálu mechanismy pro vytvoření jedinečné uživatelské prostředí, včetně bohatých obsahu modelu pro ovládací prvky, aktivační události, řízení a datové šablony, styly, prostředky uživatelského rozhraní a motivy a skinů v šablonách.  
  
### <a name="content-model"></a>Model obsahu  
 Je hlavním účelem většinou ovládacích prvků WPF k zobrazení obsahu. V WPF, typ a počet položek, které mohou představovat obsahu ovládacího prvku se označuje jako ovládací prvek *modelu obsahu*. Některé ovládací prvky mohou obsahovat jednu položku a typu obsahu; například, obsah <xref:System.Windows.Controls.TextBox> je řetězcová hodnota, která je přiřazena <xref:System.Windows.Controls.TextBox.Text%2A> vlastnost. Následující příklad nastaví obsah <xref:System.Windows.Controls.TextBox>.  
  
 [!code-xml[IntroToWPFSnippets#TextBoxContentMARKUP1](../snippets/csharp/VS_Snippets_Wpf/IntroToWPFSnippets/CSharp/TextBoxContentWindow.xaml#textboxcontentmarkup1)]  
[!code-xml[IntroToWPFSnippets#TextBoxContentMARKUP2](../snippets/csharp/VS_Snippets_Wpf/IntroToWPFSnippets/CSharp/TextBoxContentWindow.xaml#textboxcontentmarkup2)]  
[!code-xml[IntroToWPFSnippets#TextBoxContentMARKUP3](../snippets/csharp/VS_Snippets_Wpf/IntroToWPFSnippets/CSharp/TextBoxContentWindow.xaml#textboxcontentmarkup3)]  
  
 Následující obrázek ukazuje výsledek.  
  
 ![TextBox – ovládací prvek, který obsahuje text](../designers/media/wpfintrofigure21.png "WPFIntroFigure21")  
  
 Další ovládací prvky, ale může obsahovat několik položek různých typů obsahu; obsah <xref:System.Windows.Controls.Button>, určená <xref:System.Windows.Controls.ContentControl.Content%2A> vlastnost, může obsahovat různé položky, včetně rozložení ovládacích prvků, text, obrázky a tvary. Následující příklad ukazuje <xref:System.Windows.Controls.Button> s obsahem, který zahrnuje <xref:System.Windows.Controls.DockPanel>, <xref:System.Windows.Controls.Label>, <xref:System.Windows.Controls.Border>a <xref:System.Windows.Controls.MediaElement>.  
  
 [!code-xml[IntroToWPFSnippets#ButtonContentMARKUP1](../snippets/csharp/VS_Snippets_Wpf/IntroToWPFSnippets/CSharp/ButtonContentWindow.xaml#buttoncontentmarkup1)]  
[!code-xml[IntroToWPFSnippets#ButtonContentMARKUP2](../snippets/csharp/VS_Snippets_Wpf/IntroToWPFSnippets/CSharp/ButtonContentWindow.xaml#buttoncontentmarkup2)]  
[!code-xml[IntroToWPFSnippets#ButtonContentMARKUP3](../snippets/csharp/VS_Snippets_Wpf/IntroToWPFSnippets/CSharp/ButtonContentWindow.xaml#buttoncontentmarkup3)]  
  
 Následující obrázek znázorňuje obsah toto tlačítko.  
  
 ![Tlačítko, které obsahuje více typů obsahu](../designers/media/wpfintrofigure22.png "WPFIntroFigure22")  
  
 Další informace o obsahu, který podporuje různé ovládací prvky najdete v tématu [Model obsahu WPF](https://msdn.microsoft.com/library/bb613548\(v=vs.100\).aspx).  
  
### <a name="triggers"></a>Aktivační procedury  
 I když je hlavním účelem značky XAML k implementaci vzhled aplikace, můžete také použít XAML provádět některé aspekty chování aplikace. Jedním z příkladů je použití triggerů a změňte vzhled aplikace na základě interakcí uživatele. Další informace najdete v tématu [styly a šablony](https://msdn.microsoft.com/library/ms745683\(v=vs.100\).aspx).  
  
### <a name="control-templates"></a>Šablony ovládacích prvků  
 Výchozí uživatelská rozhraní pro ovládací prvky WPF se obvykle vytvářejí na základě jiné ovládací prvky a tvary. Například <xref:System.Windows.Controls.Button> se skládá z obou <xref:Microsoft.Windows.Themes.ButtonChrome> a <xref:System.Windows.Controls.ContentPresenter> ovládací prvky. <xref:Microsoft.Windows.Themes.ButtonChrome> Poskytuje standardní tlačítko vzhled, zatímco <xref:System.Windows.Controls.ContentPresenter> zobrazí obsah, na tlačítko, jak jsou určené <xref:System.Windows.Controls.ContentControl.Content%2A> vlastnost.  
  
 Výchozí vzhled ovládacího prvku může být někdy incongruent s celkový vzhled aplikace. V takovém případě můžete použít <xref:System.Windows.Controls.ControlTemplate> změnit vzhled ovládacího prvku uživatelského rozhraní aplikace beze změny jeho obsahu a chování.  
  
 Například následující příklad ukazuje, jak změnit vzhled <xref:System.Windows.Controls.Button> pomocí <xref:System.Windows.Controls.ControlTemplate>.  
  
 [!code-xml[IntroToWPFSnippets#ButtonControlTemplateWindowMARKUP](../snippets/csharp/VS_Snippets_Wpf/IntroToWPFSnippets/CSharp/ControlTemplateButtonWindow.xaml#buttoncontroltemplatewindowmarkup)]  
  
 [!code-csharp[IntroToWPFSnippets#ButtonControlTemplateWindowCODEBEHIND](../snippets/csharp/VS_Snippets_Wpf/IntroToWPFSnippets/CSharp/ControlTemplateButtonWindow.xaml.cs#buttoncontroltemplatewindowcodebehind)]
 [!code-vb[IntroToWPFSnippets#ButtonControlTemplateWindowCODEBEHIND](../snippets/visualbasic/VS_Snippets_Wpf/IntroToWPFSnippets/VisualBasic/ControlTemplateButtonWindow.xaml.vb#buttoncontroltemplatewindowcodebehind)]  
  
 V tomto příkladu výchozí tlačítko uživatelské rozhraní se nahradil údajem <xref:System.Windows.Shapes.Ellipse> , který má tmavě modrým ohraničením a naplní pomocí <xref:System.Windows.Media.RadialGradientBrush>. <xref:System.Windows.Controls.ContentPresenter> Ovládací prvek zobrazí obsah <xref:System.Windows.Controls.Button>, "Kliknutí sem!" Když <xref:System.Windows.Controls.Button> dojde ke kliknutí na, <xref:System.Windows.Controls.Primitives.ButtonBase.Click> událost se vyvolá, stále jako součást <xref:System.Windows.Controls.Button> výchozí chování ovládacího prvku. Výsledek je znázorněno na následujícím obrázku.  
  
 ![Elipsy tlačítko a druhé okno](../designers/media/wpfintrofigure2.png "WPFIntroFigure2")  
  
### <a name="data-templates"></a>Datové šablony  
 Zatímco šablonu ovládacího prvku umožňuje určit vzhled ovládacího prvku, datové šablony vám umožní určit vzhled ovládacího prvku obsahu. Datové šablony se často používají k vylepšení jak vázaných dat se zobrazí. Následující obrázek ukazuje výchozí vzhled <xref:System.Windows.Controls.ListBox> , který je vázán na kolekci `Task` objektů, kde každý úkol má název, popis a priority.  
  
 ![Seznam s výchozí vzhled](../designers/media/wpfintrofigure18.png "WPFIntroFigure18")  
  
 Výchozí vzhled je, co očekáváte od <xref:System.Windows.Controls.ListBox>. Výchozí vzhled jednotlivých úloh však obsahuje pouze název úlohy. Chcete-li zobrazit název úlohy, popisu a priority, výchozí vzhled <xref:System.Windows.Controls.ListBox> vázaného ovládacího prvku položky musí změnit pomocí <xref:System.Windows.DataTemplate>. Následující XAML například definuje <xref:System.Windows.DataTemplate>, které platí pro každý úkol s použitím <xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A> atribut.  
  
 [!code-xml[IntroToWPFSnippets#DataTemplateMARKUP1](../snippets/csharp/VS_Snippets_Wpf/IntroToWPFSnippets/CSharp/DataTemplateWindow.xaml#datatemplatemarkup1)]  
[!code-xml[IntroToWPFSnippets#DataTemplateMARKUP2](../snippets/csharp/VS_Snippets_Wpf/IntroToWPFSnippets/CSharp/DataTemplateWindow.xaml#datatemplatemarkup2)]  
[!code-xml[IntroToWPFSnippets#DataTemplateMARKUP3](../snippets/csharp/VS_Snippets_Wpf/IntroToWPFSnippets/CSharp/DataTemplateWindow.xaml#datatemplatemarkup3)]  
[!code-xml[IntroToWPFSnippets#DataTemplateMARKUP4](../snippets/csharp/VS_Snippets_Wpf/IntroToWPFSnippets/CSharp/DataTemplateWindow.xaml#datatemplatemarkup4)]  
  
 Následující obrázek znázorňuje vliv tohoto kódu.  
  
 ![Llist pole, který používá šablonu dat](../designers/media/wpfintrofigure19.png "WPFIntroFigure19")  
  
 Všimněte si, že <xref:System.Windows.Controls.ListBox> nastavil jeho chování a celkový vzhled; došlo ke změně vzhledu obsah se zobrazí v seznamu.  
  
 Další informace najdete v tématu [přehled datových šablon](https://msdn.microsoft.com/library/ms742521\(v=vs.100\).aspx).  
  
### <a name="styles"></a>Styly  
 Styly umožňují vývojářům a návrhářům standardizovat používání na konkrétní vzhled pro svůj produkt. WPF poskytuje silné styl model, je základem všeho <xref:System.Windows.Style> elementu. Následující příklad vytvoří styl, který nastavuje barvu pozadí pro každý <xref:System.Windows.Controls.Button> na okno `Orange`.  
  
 [!code-xml[IntroToWPFSnippets#StyleMARKUP1](../snippets/csharp/VS_Snippets_Wpf/IntroToWPFSnippets/CSharp/StyleWindow.xaml#stylemarkup1)]  
[!code-xml[IntroToWPFSnippets#StyleMARKUP2](../snippets/csharp/VS_Snippets_Wpf/IntroToWPFSnippets/CSharp/StyleWindow.xaml#stylemarkup2)]  
[!code-xml[IntroToWPFSnippets#StyleMARKUP3](../snippets/csharp/VS_Snippets_Wpf/IntroToWPFSnippets/CSharp/StyleWindow.xaml#stylemarkup3)]  
[!code-xml[IntroToWPFSnippets#StyleMARKUP4](../snippets/csharp/VS_Snippets_Wpf/IntroToWPFSnippets/CSharp/StyleWindow.xaml#stylemarkup4)]  
  
 Protože tento styl, zaměřuje všechny <xref:System.Windows.Controls.Button> ovládací prvky stylu se automaticky využije na všechna tlačítka v okně, jak je znázorněno na následujícím obrázku.  
  
 ![Dvě tlačítka oranžové](../designers/media/wpfintrofigure20.png "WPFIntroFigure20")  
  
 Další informace najdete v tématu [styly a šablony](https://msdn.microsoft.com/library/ms745683\(v=vs.100\).aspx).  
  
### <a name="resources"></a>Prostředky  
 Ovládací prvky v aplikaci by měly sdílet stejný vzhled, který může obsahovat cokoli z písma a barvy pozadí řídit šablon, šablony a styly. Podpora pro WPF pro prostředky uživatelského rozhraní můžete použít k zapouzdření těchto zdrojů na jednom místě pro další použití.  
  
 Následující příklad definuje běžnou barvu pozadí, které jsou sdíleny <xref:System.Windows.Controls.Button> a <xref:System.Windows.Controls.Label>.  
  
 [!code-xml[IntroToWPFSnippets#ResourceWindowMARKUP1](../snippets/csharp/VS_Snippets_Wpf/IntroToWPFSnippets/CSharp/ResourcesWindow.xaml#resourcewindowmarkup1)]  
[!code-xml[IntroToWPFSnippets#ResourceWindowMARKUP2](../snippets/csharp/VS_Snippets_Wpf/IntroToWPFSnippets/CSharp/ResourcesWindow.xaml#resourcewindowmarkup2)]  
[!code-xml[IntroToWPFSnippets#ResourceWindowMARKUP3](../snippets/csharp/VS_Snippets_Wpf/IntroToWPFSnippets/CSharp/ResourcesWindow.xaml#resourcewindowmarkup3)]  
  
 V tomto příkladu implementuje pomocí prostředek barvy pozadí `Window.Resources` element vlastnosti. Tento prostředek je k dispozici pro všechny podřízené objekty <xref:System.Windows.Window>. Existuje řada různých prostředků obory, včetně následujících, uvedeny v pořadí, ve kterém jsou vyřešeny:  
  
1. Jednotlivé ovládací prvky (použití zděděnou <xref:System.Windows.FrameworkElement.Resources%2A?displayProperty=fullName> vlastnost).  
  
2. A <xref:System.Windows.Window> nebo <xref:System.Windows.Controls.Page> (také pomocí zděděnou <xref:System.Windows.FrameworkElement.Resources%2A?displayProperty=fullName> vlastnost).  
  
3. <xref:System.Windows.Application> (Pomocí <xref:System.Windows.Application.Resources%2A?displayProperty=fullName> vlastnost).  
  
   Řadu oborů poskytuje flexibilitu s ohledem na způsob, ve kterém můžete definovat a sdílení vašich prostředků.  
  
   Jako alternativu k vašich prostředků přímo přidružením určitého oboru, můžete balíček jeden nebo více zdrojů pomocí samostatné <xref:System.Windows.ResourceDictionary> , který může být odkazováno v ostatních částech aplikace. Například následující příklad definuje výchozí barva pozadí ve slovníku prostředků.  
  
   [!code-xml[IntroToWPFSnippets#ResourceDictionaryMARKUP1](../snippets/csharp/VS_Snippets_Wpf/IntroToWPFSnippets/CSharp/BackgroundColorResources.xaml#resourcedictionarymarkup1)]  
   [!code-xml[IntroToWPFSnippets#ResourceDictionaryMARKUP2](../snippets/csharp/VS_Snippets_Wpf/IntroToWPFSnippets/CSharp/BackgroundColorResources.xaml#resourcedictionarymarkup2)]  
  
   Následující příklad odkazuje na slovník prostředků, které jsou definované v předchozím příkladu tak, aby byl se sdílel napříč aplikace.  
  
   [!code-xml[IntroToWPFSnippets#ApplicationScopedResourceDictionaryMARKUP1](../snippets/csharp/VS_Snippets_Wpf/IntroToWPFSnippets/CSharp/App.xaml#applicationscopedresourcedictionarymarkup1)]  
   [!code-xml[IntroToWPFSnippets#ApplicationScopedResourceDictionaryMARKUP2](../snippets/csharp/VS_Snippets_Wpf/IntroToWPFSnippets/CSharp/App.xaml#applicationscopedresourcedictionarymarkup2)]  
  
   Slovníky prostředků a prostředky jsou základem pro podporu WPF motivy a skinů v šablonách.  
  
   Další informace najdete v tématu [Přehled prostředků](https://msdn.microsoft.com/library/ms750613\(v=vs.100\).aspx).  
  
### <a name="custom-controls"></a>Vlastní ovládací prvky  
 Přestože WPF poskytuje celou řadu podpory vlastního nastavení, mohou nastat situace, ve kterém existujících ovládacích prvků WPF nebudou vyhovovat potřebám vaší aplikace nebo jejich uživatele. Tato situace může nastat při:  
  
- Přizpůsobení vzhledu a chování existujících implementací WPF nelze vytvořit uživatelské rozhraní, které potřebujete.  
  
- Chování, které budete potřebovat se nepodporuje (nebo podporovány nejsou snadno) existujících implementací WPF.  
  
  V tomto okamžiku však můžete využít výhod jeden ze tří modelů WPF k vytvoření nového ovládacího prvku. Každý model, zaměřuje na konkrétní scénář a vyžaduje vlastního ovládacího prvku k odvození z určité základní třídy WPF. Tady jsou uvedené všechny tři modely:  
  
- **Uživatelského ovládacího prvku modelu**. Pomocí vlastního ovládacího prvku je odvozena z <xref:System.Windows.Controls.UserControl> a se skládá z jednoho nebo více dalších ovládacích prvků.  
  
- **Ovládací prvek modelu**. Pomocí vlastního ovládacího prvku je odvozena z <xref:System.Windows.Controls.Control> a slouží k sestavení implementace, které oddělují jejich chování z jejich výskytu pomocí šablon, podobně jako většinou ovládacích prvků WPF. Odvozování z <xref:System.Windows.Controls.Control> vám dává větší svobodu pro vytvoření vlastní uživatelské rozhraní než uživatelské ovládací prvky, ale můžou vyžadovat další úsilí.  
  
- **Element modelu Framework**. Pomocí vlastního ovládacího prvku je odvozena z <xref:System.Windows.FrameworkElement> při její vzhled definoval vlastní vykreslování logiky (nikoli na šablony).  
  
  Následující příklad ukazuje vlastní číselné nahoru/dolů ovládací prvek, který je odvozen od <xref:System.Windows.Controls.UserControl>.  
  
  [!code-xml[IntroToWPFSnippets#UserControlMARKUP](../snippets/csharp/VS_Snippets_Wpf/IntroToWPFSnippets/CSharp/NumericUpDown.xaml#usercontrolmarkup)]  
  
  [!code-csharp[IntroToWPFSnippets#UserControlCODEBEHIND1](../snippets/csharp/VS_Snippets_Wpf/IntroToWPFSnippets/CSharp/NumericUpDown.xaml.cs#usercontrolcodebehind1)]
  [!code-vb[IntroToWPFSnippets#UserControlCODEBEHIND1](../snippets/visualbasic/VS_Snippets_Wpf/IntroToWPFSnippets/VisualBasic/NumericUpDown.xaml.vb#usercontrolcodebehind1)]  
  [!code-csharp[IntroToWPFSnippets#UserControlCODEBEHIND2](../snippets/csharp/VS_Snippets_Wpf/IntroToWPFSnippets/CSharp/NumericUpDown.xaml.cs#usercontrolcodebehind2)]
  [!code-vb[IntroToWPFSnippets#UserControlCODEBEHIND2](../snippets/visualbasic/VS_Snippets_Wpf/IntroToWPFSnippets/VisualBasic/NumericUpDown.xaml.vb#usercontrolcodebehind2)]  
  
  
 Následující příklad znázorňuje XAML, který je potřeba začlenit uživatelského ovládacího prvku do <xref:System.Windows.Window>.  
  
 [!code-xml[IntroToWPFSnippets#UserControlWindowMARKUP1](../snippets/csharp/VS_Snippets_Wpf/IntroToWPFSnippets/CSharp/UserControlWindow.xaml#usercontrolwindowmarkup1)]  
[!code-xml[IntroToWPFSnippets#UserControlWindowMARKUP2](../snippets/csharp/VS_Snippets_Wpf/IntroToWPFSnippets/CSharp/UserControlWindow.xaml#usercontrolwindowmarkup2)]  
[!code-xml[IntroToWPFSnippets#UserControlWindowMARKUP3](../snippets/csharp/VS_Snippets_Wpf/IntroToWPFSnippets/CSharp/UserControlWindow.xaml#usercontrolwindowmarkup3)]  
  
 Následující obrázek ukazuje `NumericUpDown` konání ovládacího prvku <xref:System.Windows.Window>.  
  
 ![Vlastní ovládací prvek UserControl](../designers/media/wpfintrofigure3.png "WPFIntroFigure3")  
  
 Další informace o vlastních ovládacích prvcích najdete v tématu [Přehled vytváření ovládacího prvku](https://msdn.microsoft.com/library/ms745025\(v=vs.100\).aspx).  
  
##  <a name="WPF_Best_Practices"></a> Osvědčené postupy pro WPF  
 Stejně jako u jakékoli vývojovou platformu WPF je možné v různých způsobů, jak dosáhnout požadovaného výsledku. Jako způsob, jak zajistit, aby vaše WPF aplikace zadejte požadované uživatelské prostředí a obecně splňují požadavky na cílovou skupinu, jsou doporučené osvědčené postupy pro usnadnění přístupu, globalizace a lokalizace a výkonu. Si přečtěte následující informace:  
  
-   [Usnadnění – doporučené postupy](https://msdn.microsoft.com/library/aa350483\(v=vs.100\).aspx)usnadnění – doporučené postupy  
  
-   [Přehled globalizace a lokalizace WPF](https://msdn.microsoft.com/library/ms788718\(v=vs.100\).aspx)  
  
-   [Optimalizace výkonu aplikace WPF](https://msdn.microsoft.com/library/aa970683\(v=vs.100\).aspx)  
  
-   [Zabezpečení Windows Presentation Foundation](https://msdn.microsoft.com/library/aa970906\(v=vs.100\).aspx)  
  
##  <a name="Summary"></a> Souhrn  
 WPF je komplexní prezentace technologie pro vytváření nejrůznějších vizuálně působivým klientské aplikace. Tento úvod poskytuje pohled na klíčové funkce WPF.  
  
 Dalším krokem je vytvoření aplikace WPF!  
  
 Jak je vytvářet, můžete se vrátit na tento úvod pro aktualizačního programu na klíčové funkce a vyhledat odkazy na podrobnější pokrytí funkce popsané v tomto úvodu.  
  
## <a name="see-also"></a>Viz také  
 [Začínáme se subsystémem WPF](../designers/getting-started-with-wpf.md)   
 [Vytvoření moderních desktopových aplikací pomocí Windows Presentation Foundation](../designers/create-modern-desktop-applications-with-windows-presentation-foundation.md)   
 [Windows Presentation Foundation](https://msdn.microsoft.com/library/ms754130\(v=vs.100\).aspx)



