---
title: Úvod do WPF
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-designers
ms.topic: conceptual
ms.assetid: b8d7cf43-d1f2-4f3d-adb0-4f3a6428edc0
author: gewarren
ms.author: gewarren
manager: douge
dev_langs:
- csharp
- vb
ms.workload:
- multiple
ms.openlocfilehash: db06323da8ccd3009c52be3ba9dd51478d1d722c
ms.sourcegitcommit: 96a6d1f16d06ca28d309d05b6e9fbd52f628cdbc
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/09/2018
ms.locfileid: "40008457"
---
# <a name="wpf-overview"></a>Přehled WPF

Windows Presentation Foundation (WPF) umožňuje vytvářet klasické pracovní plochy klienta aplikace pro Windows s vizuálně působivým uživatelským prostředím.

![Ukázka uživatelského rozhraní contoso zdravotní péče](../designers/media/wpfintrofigure24.png)

Základní WPF je nezávislé na řešení a vektorové vykreslování modul, který je sestaven využít moderní grafický hardware. WPF rozšiřuje základní s komplexní sadou funkcí vývoj aplikací, které zahrnují Extensible Application Markup Language (XAML), ovládací prvky, datové vazby, rozložení, 2D a 3D grafice, animace, styly, šablony, dokumenty, média, text, a Typografie. WPF je součástí rozhraní .NET Framework, takže můžete vytvářet aplikace, které zahrnují další prvky v knihovně tříd rozhraní .NET Framework.

Tento přehled je určená pro nové uživatele a popisuje klíčové funkce a koncepty WPF.

## <a name="program-with-wpf"></a>Program s WPF

WPF existuje jako podmnožinu typů rozhraní .NET Framework, které se nacházejí ve většině případů v <xref:System.Windows> oboru názvů. Pokud máte dříve vytvořenou aplikace pomocí rozhraní .NET Framework pomocí spravované technologie, jako je ASP.NET a Windows Forms, by měla být základní WPF programovací prostředí známých; Vytvoření instance třídy, nastavte vlastnosti, volání metody a události popisovač, všechny pomocí oblíbeného programovacího jazyka, jako je C# nebo Visual Basic .NET.

WPF obsahuje další programovací konstrukce, které zlepšují vlastnosti a události: [vlastnosti závislosti](/dotnet/framework/wpf/advanced/dependency-properties-overview) a [směrovaných událostí](/dotnet/framework/wpf/advanced/routed-events-overview).

## <a name="markup-and-code-behind"></a>Značky a modelu code-behind

WPF umožňuje vyvíjet aplikace pomocí obou *značek* a *použití modelu code-behind*, je v prostředí s ASP.NET, které vývojáři měli seznámit. Značky XAML se obvykle používají k implementaci vzhledu aplikace při používání spravovaného programovacích jazyků (použití modelu code-behind) k implementaci jeho chování. Toto oddělení vzhled a chování má následující výhody:

- Náklady na vývoj a údržbu jsou snížit, protože specifické pro vzhled značky není pevně spojená s konkrétní chování kódu.

- Vývoj je mnohem efektivnější, protože Návrháři můžete implementovat vzhled aplikace současně s vývojáři, kteří implementují chování aplikace.

- [Globalizace a lokalizace](/dotnet/framework/wpf/advanced/wpf-globalization-and-localization-overview) pro WPF aplikace zjednodušeno.

### <a name="markup"></a>Značky

XAML je jazyk založený na formátu XML kód, který implementuje vzhled aplikace deklarativně. Obvykle použijete ji k vytvoření systému windows, dialogová okna, stránky a uživatelské ovládací prvky a tak, aby vyplnil s ovládacími prvky, tvary a grafické.

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

![Okno, které obsahuje tlačítko](../designers/media/wpfintrofigure10.png)

Protože XAML je založený na formátu XML, rozhraní, které vytváříte s ním je sestavena v hierarchii označované jako vnořené elementy [stromem prvků](/dotnet/framework/wpf/advanced/trees-in-wpf). Strom prvku poskytuje logické a intuitivní způsob, jak vytvářet a spravovat uživatelská rozhraní.

### <a name="code-behind"></a>Použití modelu Code-behind

Hlavní chování aplikace je k implementaci funkcionality, která bude reagovat na akce uživatele, včetně zpracování událostí (například klepnutí na tlačítko, panel nástrojů nebo nabídky) a volání obchodní logika a logika přístupu k datům v odpovědi. V objektu WPF toto chování je implementované v kódu, který je přidružený kód. Tento typ kódu se označuje jako použití modelu code-behind. Následující příklad ukazuje aktualizovaný kód z předchozího příkladu a modelu code-behind.

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

![Pole MessageBox](../designers/media/wpfintrofigure25.png)

## <a name="controls"></a>Ovládací prvky

Uživatelské prostředí, které se dodávají pomocí aplikačního modelu se vytvořený ovládací prvky. V WPF *ovládací prvek* se o zastřešující pojem, který se vztahuje na kategorii WPF tříd, které jsou hostované v kterékoli z těchto oken nebo stránka, mít uživatelské rozhraní a implementaci některých chování.

Další informace najdete v tématu [ovládací prvky](/dotnet/framework/wpf/controls/index).

### <a name="wpf-controls-by-function"></a>Ovládací prvky WPF podle funkce

Tady jsou uvedené integrovaných ovládacích prvků WPF.

- **Tlačítka**: <xref:System.Windows.Controls.Button> a <xref:System.Windows.Controls.Primitives.RepeatButton>.

- **Zobrazení dat**: <xref:System.Windows.Controls.DataGrid>, <xref:System.Windows.Controls.ListView>, a <xref:System.Windows.Controls.TreeView>.

- **Data zobrazení a výběr**: <xref:System.Windows.Controls.Calendar> a <xref:System.Windows.Controls.DatePicker>.

- **Dialogová okna**: <xref:Microsoft.Win32.OpenFileDialog>, <xref:System.Windows.Controls.PrintDialog>, a <xref:Microsoft.Win32.SaveFileDialog>.

- **Digitální inkoust**: <xref:System.Windows.Controls.InkCanvas> a <xref:System.Windows.Controls.InkPresenter>.

- **Dokumenty**: <xref:System.Windows.Controls.DocumentViewer>, <xref:System.Windows.Controls.FlowDocumentPageViewer>, <xref:System.Windows.Controls.FlowDocumentReader>, <xref:System.Windows.Controls.FlowDocumentScrollViewer>, a <xref:System.Windows.Controls.StickyNoteControl>.

- **Vstup**: <xref:System.Windows.Controls.TextBox>, <xref:System.Windows.Controls.RichTextBox>, a <xref:System.Windows.Controls.PasswordBox>.

- **Rozložení**: <xref:System.Windows.Controls.Border>, <xref:System.Windows.Controls.Primitives.BulletDecorator>, <xref:System.Windows.Controls.Canvas>, <xref:System.Windows.Controls.DockPanel>, <xref:System.Windows.Controls.Expander>, <xref:System.Windows.Controls.Grid>, <xref:System.Windows.Controls.GridView>, <xref:System.Windows.Controls.GridSplitter>, <xref:System.Windows.Controls.GroupBox>, <xref:System.Windows.Controls.Panel>, <xref:System.Windows.Controls.Primitives.ResizeGrip>, <xref:System.Windows.Controls.Separator>, <xref:System.Windows.Controls.Primitives.ScrollBar>, <xref:System.Windows.Controls.ScrollViewer>, <xref:System.Windows.Controls.StackPanel>, <xref:System.Windows.Controls.Primitives.Thumb>, <xref:System.Windows.Controls.Viewbox>, <xref:System.Windows.Controls.VirtualizingStackPanel>, <xref:System.Windows.Window>, a <xref:System.Windows.Controls.WrapPanel>.

- **Média**: <xref:System.Windows.Controls.Image>, <xref:System.Windows.Controls.MediaElement>, a <xref:System.Windows.Controls.SoundPlayerAction>.

- **Nabídky**: <xref:System.Windows.Controls.ContextMenu>, <xref:System.Windows.Controls.Menu>, a <xref:System.Windows.Controls.ToolBar>.

- **Navigace**: <xref:System.Windows.Controls.Frame>, <xref:System.Windows.Documents.Hyperlink>, <xref:System.Windows.Controls.Page>, <xref:System.Windows.Navigation.NavigationWindow>, a <xref:System.Windows.Controls.TabControl>.

- **Výběr**: <xref:System.Windows.Controls.CheckBox>, <xref:System.Windows.Controls.ComboBox>, <xref:System.Windows.Controls.ListBox>, <xref:System.Windows.Controls.RadioButton>, a <xref:System.Windows.Controls.Slider>.

- **Informace o uživateli**: <xref:System.Windows.Controls.AccessText>, <xref:System.Windows.Controls.Label>, <xref:System.Windows.Controls.Primitives.Popup>, <xref:System.Windows.Controls.ProgressBar>, <xref:System.Windows.Controls.Primitives.StatusBar>, <xref:System.Windows.Controls.TextBlock>, a <xref:System.Windows.Controls.ToolTip>.

## <a name="input-and-commands"></a>Vstupu a příkazů

Ovládací prvky nejčastěji detekovat a reagovat na vstup uživatele. [WPF vstup systému](/dotnet/framework/wpf/advanced/input-overview) používá s přímým přístupem a směrovaných událostí pro podporu zadávání textu, správu fokus a umístění myši.

Aplikace mají často složité vstupní požadavky. Poskytuje WPF [příkaz systému](/dotnet/framework/wpf/advanced/commanding-overview) , který odděluje akce uživatelského vstupu z kódu, který reaguje na tyto akce.

## <a name="layout"></a>Rozložení

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

[!code-xaml[IntroToWPFSnippets#LayoutMARKUP](../designers/codesnippet/Xaml/introduction-to-wpf_1.xaml)]

<xref:System.Windows.Controls.DockPanel> Umožňuje podřízené <xref:System.Windows.Controls.TextBox> ovládací prvky určit, jak uspořádat je. K tomu, <xref:System.Windows.Controls.DockPanel> implementuje `Dock` přidružená vlastnost, která je vystavena do podřízených ovládacích prvků, aby každý z nich určit styl ukotvení.

> [!NOTE]
> Vlastnost, která je implementována pomocí nadřazený ovládací prvek pro použití podřízených ovládacích prvků je konstrukce WPF s názvem [přidružená vlastnost](/dotnet/framework/wpf/advanced/attached-properties-overview).

Následující obrázek ukazuje výsledek z kódu XAML v předchozím příkladu.

![Stránka DockPanel](../designers/media/wpfintrofigure11.png)

## <a name="data-binding"></a>Vytváření datových vazeb

Většina aplikací se vytvoří uživatelům poskytnout způsob, jak zobrazit a upravit data. Pro aplikace WPF práci při ukládání a přístup k datům je již podle technologie, jako je SQL Server a ADO .NET. Po přístupu k datům a načtena do aplikací spravovaných objektů, začne těžkou práci pro aplikace WPF. V podstatě to zahrnuje dvě věci:

1.  Kopírování dat ze spravovaných objektů do ovládacích prvků, kde můžete zobrazit a upravovat data.

2.  Zajištění, že změny dat s použitím ovládacích prvků jsou zkopírovány zpět na spravované objekty.

Pro zjednodušení vývoje aplikací poskytuje WPF modul vazby dat automaticky provádět tyto kroky. Je základní jednotkou modul vazby dat <xref:System.Windows.Data.Binding> třídy, jehož úkolem je vytvoření vazby ovládacího prvku (cíl vazby) na datový objekt (zdroje připojení). Tento vztah je znázorněn v následujícím obrázku:

![Diagram základní datové vazby](../designers/media/databindingmostbasic.png)

Následující příklad ukazuje, jak vytvořit vazbu <xref:System.Windows.Controls.TextBox> do instance vlastního `Person` objektu. `Person` Implementace je znázorněno v následujícím kódu:

[!code-vb[SimpleDataBindingSnippets#PersonClassCODE](../designers/codesnippet/VisualBasic/introduction-to-wpf_2.vb)]
[!code-csharp[SimpleDataBindingSnippets#PersonClassCODE](../designers/codesnippet/CSharp/introduction-to-wpf_2.cs)]

Následující kód vytvoří vazbu <xref:System.Windows.Controls.TextBox> do instance vlastního `Person` objektu.

 ```xaml
 <Window
     xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
     xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
     x:Class="SDKSample.DataBindingWindow">

   <!-- Bind the TextBox to the data source (TextBox.Text to Person.Name) -->
   <TextBox Name="personNameTextBox" Text="{Binding Path=Name}" />

 </Window>
 ```

[!code-vb[SimpleDataBindingSnippets#DataBindingCODEBEHIND](../designers/codesnippet/VisualBasic/introduction-to-wpf_6.vb)]
[!code-csharp[SimpleDataBindingSnippets#DataBindingCODEBEHIND](../designers/codesnippet/CSharp/introduction-to-wpf_6.cs)]

V tomto příkladu `Person` třídy je vytvořena instance v kódu a je nastaven jako kontext dat pro `DataBindingWindow`. V kódu <xref:System.Windows.Controls.TextBox.Text%2A> vlastnost <xref:System.Windows.Controls.TextBox> je vázán na `Person.Name` vlastnosti (pomocí "`{Binding ... }`" syntaxe XAML). Tento XAML říká WPF se vytvořit vazbu <xref:System.Windows.Controls.TextBox> ovládací prvek `Person` objekt, který je uložen v <xref:System.Windows.FrameworkElement.DataContext%2A> vlastnost okna.

Modul vazby WPF dat poskytuje další podporu, která zahrnuje ověření, řazení, filtrování a seskupování. Kromě toho vytváření datových vazeb podporuje použití šablony k vytvoření vlastního uživatelského rozhraní pro vázaných dat při uživatelské rozhraní zobrazí standardní ovládací prvky WPF není vhodná.

Další informace najdete v tématu [přehled datových vazeb](/dotnet/framework/wpf/data/data-binding-overview).

## <a name="graphics"></a>Grafika

WPF zavádí rozsáhlé, škálovatelné a flexibilní sadu grafické funkce, které mají následující výhody:

- **Nezávislé na řešení a nezávislé na zařízení grafiky**. Základní jednotka měření v systému WPF grafiky, je pixel nezávislých na zařízení, což je 1/96 palce, bez ohledu na skutečné rozlišení obrazovky a poskytuje základ pro vykreslování nezávislé na řešení a nezávislé na zařízení. Každý pixel nezávislých na zařízení se automaticky škáluje tak, aby odpovídaly nastavení bodů na palec (dpi), který se vykreslí v systému.

- **Zlepšení přesnosti**. Systém souřadnic WPF se měří pomocí dvojité přesnosti s plovoucí desetinnou čárkou čísla spíše než s jednoduchou přesností. Transformace a krytí hodnoty jsou také vyjádřena dvojitou přesností. WPF také podporuje široká barevná škála (scRGB) a poskytuje integrovanou podporu pro správu vstupy od prostory jinou barvu.

- **Přidává rozšířenou podporu grafika a animace**. WPF zjednodušuje programování grafiky tím, že správa scén animace pro vás. není nutné se starat o zpracování scény, smyčky vykreslování a varianty interpolace. Kromě toho WPF poskytuje podporu pro spuštění testu a úplné skládání alfa.

- **Hardwarovou akceleraci**. Systém grafiky WPF využívá hardwarovou akceleraci k minimalizaci využití procesoru.

### <a name="2d-shapes"></a>2D obrazce

WPF poskytuje knihovnu běžných vykreslovaných vektoru 2D tvary, třeba obdélníky a symbol tří teček, která jsou zobrazena na následujícím obrázku:

![Symbol tří teček a obdélníky](../designers/media/wpfintrofigure4.PNG)

Zajímavé funkce tvarů je, že se nejedná jenom pro zobrazení; tvary implementovat řadu funkcí, které očekáváte, že z ovládacích prvků, včetně klávesnice a myši. Následující příklad ukazuje <xref:System.Windows.UIElement.MouseUp> události <xref:System.Windows.Shapes.Ellipse> zpracovává.

[!code-xaml[IntroToWPFSnippets#HandleEllipseMouseUpEventMARKUP](../designers/codesnippet/Xaml/introduction-to-wpf_7.xaml)]

[!code-vb[IntroToWPFSnippets#HandleEllipseMouseUpEventCODEBEHIND](../designers/codesnippet/VisualBasic/introduction-to-wpf_8.vb)]
[!code-csharp[IntroToWPFSnippets#HandleEllipseMouseUpEventCODEBEHIND](../designers/codesnippet/CSharp/introduction-to-wpf_8.cs)]

Následující obrázek znázorňuje, co je vytvořený v předchozím kódu.

![Okno s textem "kliknutí na tři tečky&#33;"](../designers/media/wpfintrofigure12.png)

Další informace najdete v tématu [tvary a základní kresby v přehledu WPF](/dotnet/framework/wpf/data/data-binding-overview).

### <a name="2d-geometries"></a>2D geometrie

2D obrazce poskytované WPF zahrnují standardní sadu základních tvarů. Můžete však vytvořit vlastní tvary, které usnadňují návrh přizpůsobené uživatelské rozhraní. K tomuto účelu poskytuje WPF geometrie. Následující obrázek znázorňuje použití geometrie vytvoříte vlastní obrazec, který lze vykreslit přímo, používá jako štětce nebo použít na jiné tvary a ovládací prvky.

<xref:System.Windows.Shapes.Path> objekty lze použít pro kreslení tvarů uzavřeného nebo otevřít, více tvarů a dokonce i zakřivené obrazce.

<xref:System.Windows.Media.Geometry> objekty lze použít pro oříznutí, spuštění testu a 2D grafická datech pro vykreslení.

![Různé možnosti použití cesty](../designers/media/wpfintrofigure5.png)

Další informace najdete v tématu [přehled geometrie](/dotnet/framework/wpf/graphics-multimedia/geometry-overview).

### <a name="2d-effects"></a>2D efekty

Obsahuje podmnožinu WPF 2D možnosti vizuálních efektů, jako je například přechody, rastrových obrázků, kreseb Malování s využitím videí, otáčení, škálování a zkosení. Tyto jsou všechny dosáhnout pomocí štětců; Následující obrázek znázorňuje několik příkladů.

![Znázornění různých štětců](../designers/media/wpfintrofigure6.png)

Další informace najdete v tématu [WPF stopy přehled](/dotnet/framework/wpf/graphics-multimedia/wpf-brushes-overview).

### <a name="3d-rendering"></a>3D vykreslování

WPF obsahuje také možnosti 3D vykreslování, které se integrují s 2D grafika, aby se mohly vytvářet zajímavé a zajímavé uživatelská rozhraní. Například následující obrázek znázorňuje 2D imagí vykresleny také na 3D obrazce.

![Snímek obrazovky ukázkové Visual3D](../designers/media/wpfintrofigure13.png)

Další informace najdete v tématu [přehled 3D grafiky](/dotnet/framework/wpf/graphics-multimedia/3-d-graphics-overview).

## <a name="animation"></a>Animace

Umožňuje podporu animace WPF, které provedete ovládací prvky zvětšení, zatřeste, typu číselník a fade, chcete-li vytvořit zajímavé stránce přechody a další. Lze animovat Většina tříd WPF, dokonce i vlastní třídy. Následující obrázek znázorňuje jednoduché animace v akci.

![Bitové kopie animovaný datové krychle](../designers/media/wpfintrofigure7.png)

Další informace najdete v tématu [přehled animace](/dotnet/framework/wpf/graphics-multimedia/animation-overview).

## <a name="media"></a>Média

Jedním ze způsobů předání formátovaného obsahu je prostřednictvím audiovizuální média. WPF podporuje speciální obrázky, videa a zvuku.

### <a name="images"></a>Obrázky

Bitové kopie jsou společné pro většinu aplikací a WPF poskytuje několik způsobů, jak je používat. Následující obrázek ukazuje uživatelské rozhraní pomocí seznamu, který obsahuje obrázky miniatur. Pokud je vybrána miniatury, zobrazení obrázku reklamy.

![Obrázky miniatur a úplné&#45;velikost obrázku](../designers/media/wpfintrofigure8.png)

Další informace najdete v tématu [přehled obrázků](/dotnet/framework/wpf/graphics-multimedia/imaging-overview).

### <a name="video-and-audio"></a>Videa a zvuku

<xref:System.Windows.Controls.MediaElement> Ovládací prvek je schopen přehrávání videa a zvuku, a je dostatečně flexibilní, aby se základ pro vlastní přehrávač. Následující kód XAML implementuje přehrávač médií.

[!code-xaml[IntroToWPFSnippets#MediaElementMARKUP](../designers/codesnippet/Xaml/introduction-to-wpf_9.xaml)]

V okně v následující obrázek ukazuje <xref:System.Windows.Controls.MediaElement> ovládacího prvku v akci.

![Řízení elementu MediaElement pomocí zvuku a videa](../designers/media/wpfintrofigure1.png)

Další informace najdete v tématu [grafika a multimédia](/dotnet/framework/wpf/graphics-multimedia).

## <a name="text-and-typography"></a>Text a typografie

Pro usnadnění vykreslování textu v vysoce kvalitní, WPF nabízí následující funkce:

- Podpora písmo OpenType.

- ClearType – vylepšení.

- Vysoký výkon, který využívá hardwarovou akceleraci.

- Integrace textu pomocí média, grafika a animace.

- Mezinárodní písma podpory a nouzového řešení ověření mechanismy.

Jako ukázkový text integrace s grafikou následující obrázek znázorňuje použití dekorace textu.

![Text pomocí různých dekorace textu](../designers/media/wpfintrofigure23.png)

Další informace najdete v tématu [Typografie ve Windows Presentation Foundation](/dotnet/framework/wpf/advanced/typography-in-wpf).

## <a name="customize-wpf-apps"></a>Přizpůsobení aplikace WPF

Do této chvíle jste viděli základní WPF stavební bloky pro vývoj aplikací. Aplikační model můžete použít k hostování a doručovat obsah aplikace, který se skládá převážně z ovládacích prvků. Pro zjednodušení uspořádání ovládacích prvků v uživatelském rozhraní a k Ujistěte se, že i v případě změny velikosti okna se udržuje uspořádání a nastavení zobrazení, použijete systém rozložení WPF. Vzhledem k tomu, že většina aplikací uživatelům interakci s daty, použít datovou vazbu ke snížení práci integrovat uživatelské rozhraní s daty. Pokud chcete zlepšit vzhled vaší aplikace, použijte komplexní rozsah obrázky, animace a média podpora poskytovaná WPF.

Často ale základní informace nejsou dostatečná pro vytváření a správa skutečně samostatný a vizuálně působivým činnost koncového uživatele. Standardní ovládací prvky WPF nemusí integrovat požadovaný vzhled vaší aplikace. Data nemusí zobrazit v nejúčinnějším způsobem. Celkové uživatelské prostředí pro vaše aplikace nemusí být vhodné výchozí vzhled a chování Windows motivů. V mnoha způsoby prezentace technologie musí rozšíření produktu visual co jakéhokoli jiného typu rozšíření.

Z tohoto důvodu WPF poskytuje širokou škálu mechanismy pro vytvoření jedinečné uživatelské prostředí, včetně bohatých obsahu modelu pro ovládací prvky, aktivační události, řízení a datové šablony, styly, prostředky uživatelského rozhraní a motivy a skinů v šablonách.

### <a name="content-model"></a>Model obsahu

Je hlavním účelem většinou ovládacích prvků WPF k zobrazení obsahu. V WPF, typ a počet položek, které mohou představovat obsahu ovládacího prvku se označuje jako ovládací prvek *modelu obsahu*. Některé ovládací prvky mohou obsahovat jednu položku a typu obsahu; například, obsah <xref:System.Windows.Controls.TextBox> je řetězcová hodnota, která je přiřazena <xref:System.Windows.Controls.TextBox.Text%2A> vlastnost. Následující příklad nastaví obsah <xref:System.Windows.Controls.TextBox>.

```xaml
<Window
    xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
    xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
    x:Class="SDKSample.TextBoxContentWindow"
    Title="TextBox Content">

    <TextBox Text="This is the content of a TextBox." />
</Window>
```

Následující obrázek ukazuje výsledek.

![TextBox – ovládací prvek, který obsahuje text](../designers/media/wpfintrofigure21.png)

Další ovládací prvky, ale může obsahovat několik položek různých typů obsahu; obsah <xref:System.Windows.Controls.Button>, určená <xref:System.Windows.Controls.ContentControl.Content%2A> vlastnost, může obsahovat různé položky, včetně rozložení ovládacích prvků, text, obrázky a tvary. Následující příklad ukazuje <xref:System.Windows.Controls.Button> s obsahem, který zahrnuje <xref:System.Windows.Controls.DockPanel>, <xref:System.Windows.Controls.Label>, <xref:System.Windows.Controls.Border>a <xref:System.Windows.Controls.MediaElement>.

```xaml
<Window
    xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
    xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
    x:Class="SDKSample.ButtonContentWindow"
    Title="Button Content">

  <Button Margin="20">
    <!-- Button Content -->
    <DockPanel Width="200" Height="180">
      <Label DockPanel.Dock="Top" HorizontalAlignment="Center">Click Me!</Label>
      <Border Background="Black" BorderBrush="Yellow" BorderThickness="2"
        CornerRadius="2" Margin="5">
        <MediaElement Source="media/wpf.wmv" Stretch="Fill" />
      </Border>
    </DockPanel>
  </Button>
</Window>
```

Následující obrázek znázorňuje obsah toto tlačítko.

![Tlačítko, které obsahuje více typů obsahu](../designers/media/wpfintrofigure22.png)

Další informace o obsahu, který podporuje různé ovládací prvky najdete v tématu [model obsahu WPF](/dotnet/framework/wpf/controls/wpf-content-model).

### <a name="triggers"></a>Aktivační procedury

I když je hlavním účelem značky XAML k implementaci vzhled aplikace, můžete také použít XAML provádět některé aspekty chování aplikace. Jedním z příkladů je použití triggerů a změňte vzhled aplikace na základě interakcí uživatele. Další informace najdete v tématu [styly a šablony](/dotnet/framework/wpf/controls/styling-and-templating).

### <a name="control-templates"></a>Šablony ovládacích prvků

Výchozí uživatelská rozhraní pro ovládací prvky WPF se obvykle vytvářejí na základě jiné ovládací prvky a tvary. Například <xref:System.Windows.Controls.Button> se skládá z obou <xref:Microsoft.Windows.Themes.ButtonChrome> a <xref:System.Windows.Controls.ContentPresenter> ovládací prvky. <xref:Microsoft.Windows.Themes.ButtonChrome> Poskytuje standardní tlačítko vzhled, zatímco <xref:System.Windows.Controls.ContentPresenter> zobrazí obsah, na tlačítko, jak jsou určené <xref:System.Windows.Controls.ContentControl.Content%2A> vlastnost.

Výchozí vzhled ovládacího prvku může být někdy incongruent s celkový vzhled aplikace. V takovém případě můžete použít <xref:System.Windows.Controls.ControlTemplate> změnit vzhled ovládacího prvku uživatelského rozhraní aplikace beze změny jeho obsahu a chování.

Například následující příklad ukazuje, jak změnit vzhled <xref:System.Windows.Controls.Button> pomocí <xref:System.Windows.Controls.ControlTemplate>.

[!code-xaml[IntroToWPFSnippets#ButtonControlTemplateWindowMARKUP](../designers/codesnippet/Xaml/introduction-to-wpf_16.xaml)]

[!code-csharp[IntroToWPFSnippets#ButtonControlTemplateWindowCODEBEHIND](../designers/codesnippet/CSharp/introduction-to-wpf_17.cs)]
[!code-vb[IntroToWPFSnippets#ButtonControlTemplateWindowCODEBEHIND](../designers/codesnippet/VisualBasic/introduction-to-wpf_17.vb)]

V tomto příkladu výchozí tlačítko uživatelské rozhraní se nahradil údajem <xref:System.Windows.Shapes.Ellipse> , který má tmavě modrým ohraničením a naplní pomocí <xref:System.Windows.Media.RadialGradientBrush>. <xref:System.Windows.Controls.ContentPresenter> Ovládací prvek zobrazí obsah <xref:System.Windows.Controls.Button>, "Kliknutí sem!" Když <xref:System.Windows.Controls.Button> dojde ke kliknutí na, <xref:System.Windows.Controls.Primitives.ButtonBase.Click> událost se vyvolá, stále jako součást <xref:System.Windows.Controls.Button> výchozí chování ovládacího prvku. Výsledkem je vidět na následujícím obrázku:

![Elipsy tlačítko a druhé okno](../designers/media/wpfintrofigure2.png)

### <a name="data-templates"></a>Datové šablony

Zatímco šablonu ovládacího prvku umožňuje určit vzhled ovládacího prvku, datové šablony vám umožní určit vzhled ovládacího prvku obsahu. Datové šablony se často používají k vylepšení jak vázaných dat se zobrazí. Následující obrázek ukazuje výchozí vzhled <xref:System.Windows.Controls.ListBox> , který je vázán na kolekci `Task` objektů, kde každý úkol má název, popis a priority.

![Seznam s výchozí vzhled](../designers/media/wpfintrofigure18.png)

Výchozí vzhled je, co očekáváte od <xref:System.Windows.Controls.ListBox>. Výchozí vzhled jednotlivých úloh však obsahuje pouze název úlohy. Chcete-li zobrazit název úlohy, popisu a priority, výchozí vzhled <xref:System.Windows.Controls.ListBox> vázaného ovládacího prvku položky musí změnit pomocí <xref:System.Windows.DataTemplate>. Následující XAML například definuje <xref:System.Windows.DataTemplate>, které platí pro každý úkol s použitím <xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A> atribut.

```xaml
<Window
  xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
  xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
  x:Class="SDKSample.DataTemplateWindow"
  Title="With a Data Template">
  <Window.Resources>
    <!-- Data Template (applied to each bound task item in the task collection) -->
    <DataTemplate x:Key="myTaskTemplate">
      <Border Name="border" BorderBrush="DarkSlateBlue" BorderThickness="2"
        CornerRadius="2" Padding="5" Margin="5">
        <Grid>
          <Grid.RowDefinitions>
            <RowDefinition/>
            <RowDefinition/>
            <RowDefinition/>
          </Grid.RowDefinitions>
          <Grid.ColumnDefinitions>
            <ColumnDefinition Width="Auto" />
            <ColumnDefinition />
          </Grid.ColumnDefinitions>
          <TextBlock Grid.Row="0" Grid.Column="0" Padding="0,0,5,0" Text="Task Name:"/>
          <TextBlock Grid.Row="0" Grid.Column="1" Text="{Binding Path=TaskName}"/>
          <TextBlock Grid.Row="1" Grid.Column="0" Padding="0,0,5,0" Text="Description:"/>
          <TextBlock Grid.Row="1" Grid.Column="1" Text="{Binding Path=Description}"/>
          <TextBlock Grid.Row="2" Grid.Column="0" Padding="0,0,5,0" Text="Priority:"/>
          <TextBlock Grid.Row="2" Grid.Column="1" Text="{Binding Path=Priority}"/>
        </Grid>
      </Border>
    </DataTemplate>
  </Window.Resources>

  <!-- UI -->
  <DockPanel>
    <!-- Title -->
    <Label DockPanel.Dock="Top" FontSize="18" Margin="5" Content="My Task List:"/>

    <!-- Data template is specified by the ItemTemplate attribute -->
    <ListBox
      ItemsSource="{Binding}"
      ItemTemplate="{StaticResource myTaskTemplate}"
      HorizontalContentAlignment="Stretch"
      IsSynchronizedWithCurrentItem="True"
      Margin="5,0,5,5" />

 </DockPanel>
</Window>
```

Následující obrázek znázorňuje vliv tohoto kódu.

![Pole se seznamem, který používá šablonu dat](../designers/media/wpfintrofigure19.png)

Všimněte si, že <xref:System.Windows.Controls.ListBox> nastavil jeho chování a celkový vzhled; došlo ke změně vzhledu obsah se zobrazí v seznamu.

Další informace najdete v tématu [přehled datových šablon](/dotnet/framework/wpf/data/data-templating-overview).

### <a name="styles"></a>Styly

Styly umožňují vývojářům a návrhářům standardizovat používání na konkrétní vzhled pro svůj produkt. WPF poskytuje silné styl model, je základem všeho <xref:System.Windows.Style> elementu. Následující příklad vytvoří styl, který nastavuje barvu pozadí pro každý <xref:System.Windows.Controls.Button> na okno `Orange`.

```xaml
<Window
    xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
    xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
    x:Class="SDKSample.StyleWindow"
    Title="Styles">
  <!-- Style that will be applied to all buttons -->
  <Style TargetType="{x:Type Button}">
    <Setter Property="Background" Value="Orange" />
    <Setter Property="BorderBrush" Value="Crimson" />
    <Setter Property="FontSize" Value="20" />
    <Setter Property="FontWeight" Value="Bold" />
    <Setter Property="Margin" Value="5" />
  </Style>
  <!-- This button will have the style applied to it -->
  <Button>Click Me!</Button>

  <!-- This label will not have the style applied to it -->
  <Label>Don't Click Me!</Label>

  <!-- This button will have the style applied to it -->
  <Button>Click Me!</Button>
</Window>
```

Protože tento styl, zaměřuje všechny <xref:System.Windows.Controls.Button> ovládací prvky stylu se automaticky využije na všechna tlačítka v okně, jak je znázorněno na následujícím obrázku:

![Dvě tlačítka oranžová](../designers/media/wpfintrofigure20.png)

Další informace najdete v tématu [styly a šablony](/dotnet/framework/wpf/controls/styling-and-templating).

### <a name="resources"></a>Prostředky

Ovládací prvky v aplikaci by měly sdílet stejný vzhled, který může obsahovat cokoli z písma a barvy pozadí řídit šablon, šablony a styly. Podpora pro WPF pro prostředky uživatelského rozhraní můžete použít k zapouzdření těchto zdrojů na jednom místě pro další použití.

Následující příklad definuje běžnou barvu pozadí, které jsou sdíleny <xref:System.Windows.Controls.Button> a <xref:System.Windows.Controls.Label>.

```xaml
<Window
    xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
    xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
    x:Class="SDKSample.ResourcesWindow"
    Title="Resources Window">

  <!-- Define window-scoped background color resource -->
  <Window.Resources>
    <SolidColorBrush x:Key="defaultBackground" Color="Red" />
  </Window.Resources>

  <!-- Button background is defined by window-scoped resource -->
  <Button Background="{StaticResource defaultBackground}">One Button</Button>

  <!-- Label background is defined by window-scoped resource -->
  <Label Background="{StaticResource defaultBackground}">One Label</Label>
</Window>
```

V tomto příkladu implementuje pomocí prostředek barvy pozadí `Window.Resources` element vlastnosti. Tento prostředek je k dispozici pro všechny podřízené objekty <xref:System.Windows.Window>. Existuje řada různých prostředků obory, včetně následujících, uvedeny v pořadí, ve kterém jsou vyřešeny:

1.  Jednotlivé ovládací prvky (použití zděděnou <xref:System.Windows.FrameworkElement.Resources%2A?displayProperty=fullName> vlastnost).

2.  A <xref:System.Windows.Window> nebo <xref:System.Windows.Controls.Page> (také pomocí zděděnou <xref:System.Windows.FrameworkElement.Resources%2A?displayProperty=fullName> vlastnost).

3.  <xref:System.Windows.Application> (Pomocí <xref:System.Windows.Application.Resources%2A?displayProperty=fullName> vlastnost).

Řadu oborů poskytuje flexibilitu s ohledem na způsob, ve kterém můžete definovat a sdílení vašich prostředků.

Jako alternativu k vašich prostředků přímo přidružením určitého oboru, můžete balíček jeden nebo více zdrojů pomocí samostatné <xref:System.Windows.ResourceDictionary> , který může být odkazováno v ostatních částech aplikace. Například následující příklad definuje výchozí barva pozadí ve slovníku prostředků.

```xaml
<ResourceDictionary
    xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
    xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml">

  <!-- Define background color resource -->
  <SolidColorBrush x:Key="defaultBackground" Color="Red" />

  <!-- Define other resources -->
</ResourceDictionary>
```

 Následující příklad odkazuje na slovník prostředků, které jsou definované v předchozím příkladu tak, aby byl se sdílel napříč aplikace.

```xaml
<Application
    xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
    xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
    x:Class="SDKSample.App">

  <Application.Resources>
    <ResourceDictionary>
      <ResourceDictionary.MergedDictionaries>
        <ResourceDictionary Source="BackgroundColorResources.xaml"/>
      </ResourceDictionary.MergedDictionaries>
    </ResourceDictionary>
  </Application.Resources>
</Application>
```

Slovníky prostředků a prostředky jsou základem pro podporu WPF motivy a skinů v šablonách.

Další informace najdete v tématu [prostředky](/dotnet/framework/wpf/advanced/xaml-resources).

### <a name="custom-controls"></a>Vlastní ovládací prvky

Přestože WPF poskytuje celou řadu podpory vlastního nastavení, mohou nastat situace, ve kterém existujících ovládacích prvků WPF nebudou vyhovovat potřebám vaší aplikace nebo jejich uživatele. Tato situace může nastat při:

- Přizpůsobení vzhledu a chování existujících implementací WPF nelze vytvořit uživatelské rozhraní, které potřebujete.

- Chování, které budete potřebovat se nepodporuje (nebo podporovány nejsou snadno) existujících implementací WPF.

V tomto okamžiku však můžete využít výhod jeden ze tří modelů WPF k vytvoření nového ovládacího prvku. Každý model, zaměřuje na konkrétní scénář a vyžaduje vlastního ovládacího prvku k odvození z určité základní třídy WPF. Tady jsou uvedené všechny tři modely:

- **Uživatelského ovládacího prvku modelu**. Pomocí vlastního ovládacího prvku je odvozena z <xref:System.Windows.Controls.UserControl> a se skládá z jednoho nebo více dalších ovládacích prvků.

- **Ovládací prvek modelu**. Pomocí vlastního ovládacího prvku je odvozena z <xref:System.Windows.Controls.Control> a slouží k sestavení implementace, které oddělují jejich chování z jejich výskytu pomocí šablon, podobně jako většinou ovládacích prvků WPF. Odvozování z <xref:System.Windows.Controls.Control> vám dává větší svobodu pro vytvoření vlastní uživatelské rozhraní než uživatelské ovládací prvky, ale můžou vyžadovat další úsilí.

- **Element modelu Framework**. Pomocí vlastního ovládacího prvku je odvozena z <xref:System.Windows.FrameworkElement> při její vzhled definoval vlastní vykreslování logiky (nikoli na šablony).

Následující příklad ukazuje vlastní číselné nahoru/dolů ovládací prvek, který je odvozen od <xref:System.Windows.Controls.UserControl>.

[!code-xaml[IntroToWPFSnippets#UserControlMARKUP](../designers/codesnippet/Xaml/introduction-to-wpf_33.xaml)]

[!code-csharp[IntroToWPFSnippets#UserControlCODEBEHIND1](../designers/codesnippet/CSharp/introduction-to-wpf_34.cs)]
[!code-vb[IntroToWPFSnippets#UserControlCODEBEHIND1](../designers/codesnippet/VisualBasic/introduction-to-wpf_34.vb)]

Následující příklad znázorňuje XAML, který je potřeba začlenit uživatelského ovládacího prvku do <xref:System.Windows.Window>.

[!code-xaml[IntroToWPFSnippets#UserControlWindowMARKUP1](../designers/codesnippet/Xaml/introduction-to-wpf_37.xaml)]

Následující obrázek ukazuje `NumericUpDown` konání ovládacího prvku <xref:System.Windows.Window>.

![Vlastní uživatelský ovládací prvek](../designers/media/wpfintrofigure3.png)

Další informace o vlastních ovládacích prvcích najdete v tématu [ovládací prvek vytvoření přehledu](/dotnet/framework/wpf/controls/control-authoring-overview).

## <a name="wpf-best-practices"></a>Osvědčené postupy pro WPF

Stejně jako u jakékoli vývojovou platformu WPF je možné v různých způsobů, jak dosáhnout požadovaného výsledku. Jako způsob, jak zajistit, aby vaše WPF aplikace zadejte požadované uživatelské prostředí a obecně splňují požadavky na cílovou skupinu, jsou doporučené osvědčené postupy pro usnadnění přístupu, globalizace a lokalizace a výkonu. Další informace naleznete v tématu:

- [Usnadnění](/dotnet/framework/ui-automation/accessibility-best-practices)
- [WPF globalizace a lokalizace](/dotnet/framework/wpf/advanced/wpf-globalization-and-localization-overview)
- [Výkon aplikace WPF](/dotnet/framework/wpf/advanced/optimizing-wpf-application-performance)
- [Zabezpečení WPF](/dotnet/framework/wpf/security-wpf)

## <a name="next-steps"></a>Další kroky

Podívali jsme se na klíčové funkce WPF. Nyní je čas vytvořit svoji první aplikaci WPF.

> [!div class="nextstepaction"]
> [Návod: Moje první desktopová aplikace WPF](/dotnet/framework/wpf/getting-started/walkthrough-my-first-wpf-desktop-application)

## <a name="see-also"></a>Viz také:

- [Začínáme s WPF (Windows Presentation Foundation)](../designers/getting-started-with-wpf.md)
- [Windows Presentation Foundation](/dotnet/framework/wpf/index)
- [Komunitní materiály pro WPF](/dotnet/framework/wpf/getting-started/community-feedback)
