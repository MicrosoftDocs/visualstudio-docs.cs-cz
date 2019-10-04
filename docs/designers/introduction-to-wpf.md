---
title: Úvod do WPF
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: b8d7cf43-d1f2-4f3d-adb0-4f3a6428edc0
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- csharp
- vb
ms.workload:
- multiple
ms.openlocfilehash: bb88c5b718c0f949825a2542b5a084d4e8ca15b9
ms.sourcegitcommit: dc12a7cb66124596089f01d3e939027ae562ede9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/04/2019
ms.locfileid: "71962966"
---
# <a name="wpf-overview"></a>Přehled grafického subsystému WPF (Windows Presentation Foundation)

Windows Presentation Foundation (WPF) umožňuje vytváření klientských aplikací pro Windows s vizuálně poutavými uživatelskými prostředími.

![Ukázka uživatelského rozhraní pro zdravotní péče společnosti Contoso](../designers/media/wpfintrofigure24.png)

Jádrem WPF je modul vykreslování založený na rozlišení a vektorový vykreslovací modul, který je sestaven tak, aby využíval výhody moderního grafického hardwaru. WPF rozšiřuje jádro o komplexní sadu funkcí pro vývoj aplikací, které zahrnují jazyk Extensible Application Markup Language (XAML) (XAML), ovládací prvky, datové vazby, rozložení, 2D a 3D grafiku, animace, styly, šablony, dokumenty, multimédia, text a Typografie. WPF je součástí .NET, takže můžete sestavovat aplikace, které zahrnují další prvky rozhraní .NET API.

Tento přehled je určený pro Newcomers a pokrývá klíčové funkce a koncepty WPF.

## <a name="program-with-wpf"></a>Program s WPF

WPF existuje jako podmnožina typů .NET, které jsou (ve většině částí) nacházející se v oboru názvů <xref:System.Windows>. Pokud jste už dříve vytvořili aplikace s .NET pomocí spravovaných technologií, jako je ASP.NET a model Windows Forms, měli byste znát základní programovací prostředí WPF. můžete vytvářet instance tříd, nastavovat vlastnosti, volat metody a zpracovávat události pomocí oblíbeného programovacího jazyka .NET, například C# nebo Visual Basic.

WPF obsahuje další programovací konstrukce, které vylepšují vlastnosti a události: [vlastnosti závislosti](/dotnet/framework/wpf/advanced/dependency-properties-overview) a [směrované události](/dotnet/framework/wpf/advanced/routed-events-overview).

## <a name="markup-and-code-behind"></a>Značky a kód na pozadí

WPF umožňuje vyvíjet aplikace pomocí *značek* i *kódu na pozadí*, což je prostředí, se kterým by ASP.NET vývojáři měli znát. Obecně se používá kód XAML k implementaci vzhledu aplikace při použití spravovaných programovacích jazyků (kódu na pozadí) k implementaci jeho chování. Toto oddělení vzhledu a chování přináší následující výhody:

- Náklady na vývoj a údržbu jsou sníženy, protože označení specifické pro vzhled není pevně spojeno s kódem specifickým pro chování.

- Vývoj je efektivnější, protože návrháři můžou implementovat vzhled aplikace současně s vývojáři, kteří implementují chování aplikace.

- [Globalizace a lokalizace](/dotnet/framework/wpf/advanced/wpf-globalization-and-localization-overview) pro aplikace WPF je zjednodušená.

### <a name="markup"></a>Revize

XAML je značkovací jazyk založený na jazyce XML, který deklarativně implementuje vzhled aplikace. Obvykle ho používáte k vytváření oken, dialogových oken, stránek a uživatelských ovládacích prvků a k jejich vyplnění ovládacími prvky, tvary a grafikou.

Následující příklad používá XAML k implementaci vzhledu okna, které obsahuje jediné tlačítko.

```xaml
<Window
    xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
    Title="Window with Button"
    Width="250" Height="100">

  <!-- Add button to window -->
  <Button Name="button">Click Me!</Button>

</Window>
```

Konkrétně tento kód XAML definuje okno a tlačítko pomocí prvků `Window` a `Button` v uvedeném pořadí. Každý prvek je nakonfigurován s atributy, jako je například atribut `Title` elementu `Window` pro určení textu záhlaví okna. V době běhu převede WPF prvky a atributy, které jsou definovány v označení, na instance tříd WPF. Například prvek `Window` je převeden na instanci třídy <xref:System.Windows.Window>, jejíž vlastnost <xref:System.Windows.Window.Title%2A> je hodnotou atributu `Title`.

Následující obrázek ukazuje uživatelské rozhraní (UI), které je definováno XAML v předchozím příkladu.

![Okno obsahující tlačítko](../designers/media/wpfintrofigure10.png)

Vzhledem k tomu, že XAML je založen na formátu XML, uživatelské rozhraní, které v něm vytvoříte, je sestaveno v hierarchii vnořených elementů, které jsou označovány jako [strom elementu](/dotnet/framework/wpf/advanced/trees-in-wpf). Strom elementů poskytuje logický a intuitivní způsob, jak vytvořit a spravovat uživatelská rozhraní.

### <a name="code-behind"></a>Kód na pozadí

Hlavním chováním aplikace je implementovat funkcionalitu, která reaguje na interakce uživatele, včetně zpracování událostí (například kliknutí na nabídku, panel nástrojů nebo tlačítko) a volání obchodní logiky a logiky přístupu k datům v reakci. V jazyce WPF je toto chování implementováno v kódu, který je spojen s označením. Tento typ kódu je známý jako kód na pozadí. Následující příklad ukazuje aktualizovaný kód z předchozího příkladu a kód na pozadí.

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
    public partial class AWindow : Window
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

    Partial Public Class AWindow
        Inherits System.Windows.Window

        Public Sub New()

            ' InitializeComponent call is required to merge the UI 
            ' that is defined in markup with this class, including  
            ' setting properties and registering event handlers
            InitializeComponent()

        End Sub 

        Private Sub button_Click(ByVal sender As Object, ByVal e As RoutedEventArgs)

            ' Show message box when button is clicked
            MessageBox.Show("Hello, Windows Presentation Foundation!")

        End Sub 

    End Class 

End Namespace
```

V tomto příkladu kód na pozadí implementuje třídu, která je odvozena od třídy <xref:System.Windows.Window>. Atribut `x:Class` slouží k přidružení značky ke třídě s kódem na pozadí. `InitializeComponent` je volána z konstruktoru třídy kódu na pozadí pro sloučení uživatelského rozhraní, které je definováno v kódu pomocí třídy kódu na pozadí. (`InitializeComponent` se vygeneruje při sestavení vaší aplikace, což znamená, že je nemusíte implementovat ručně.) Kombinace `x:Class` a `InitializeComponent` zajistí, že se vaše implementace správně inicializuje při každém vytvoření. Třída kódu na pozadí implementuje také obslužnou rutinu události pro událost <xref:System.Windows.Controls.Primitives.ButtonBase.Click> tlačítka. Po kliknutí na tlačítko, obslužná rutina události zobrazí okno se zprávou voláním metody <xref:System.Windows.MessageBox.Show%2A?displayProperty=fullName>.

Následující obrázek ukazuje výsledek při kliknutí na tlačítko.

![MessageBox](../designers/media/wpfintrofigure25.png)

## <a name="controls"></a>Ovládací prvky

Uživatelské prostředí, které jsou dodávány aplikačním modelem, jsou konstruovány ovládací prvky. V rámci WPF je *ovládací prvek* výrazem zastřešující, který se vztahuje na kategorii tříd WPF, které jsou hostovány buď v okně, nebo na stránce, mají uživatelské rozhraní a implementují určité chování.

Další informace najdete v tématu [ovládací prvky](/dotnet/framework/wpf/controls/index).

### <a name="wpf-controls-by-function"></a>Ovládací prvky WPF podle funkcí

Tady jsou uvedené předdefinované ovládací prvky WPF.

- **Buttons**: <xref:System.Windows.Controls.Button> a <xref:System.Windows.Controls.Primitives.RepeatButton>.

- **Zobrazení dat**: <xref:System.Windows.Controls.DataGrid>, <xref:System.Windows.Controls.ListView> a <xref:System.Windows.Controls.TreeView>.

- **Zobrazení data a výběr**: <xref:System.Windows.Controls.Calendar> a <xref:System.Windows.Controls.DatePicker>.

- **Dialogová okna**: <xref:Microsoft.Win32.OpenFileDialog>, <xref:System.Windows.Controls.PrintDialog> a <xref:Microsoft.Win32.SaveFileDialog>.

- **Digitální inkoust**: <xref:System.Windows.Controls.InkCanvas> a <xref:System.Windows.Controls.InkPresenter>.

- **Dokumenty**: <xref:System.Windows.Controls.DocumentViewer>, <xref:System.Windows.Controls.FlowDocumentPageViewer>, <xref:System.Windows.Controls.FlowDocumentReader>, <xref:System.Windows.Controls.FlowDocumentScrollViewer> a <xref:System.Windows.Controls.StickyNoteControl>.

- **Vstup**: <xref:System.Windows.Controls.TextBox>, <xref:System.Windows.Controls.RichTextBox> a <xref:System.Windows.Controls.PasswordBox>.

- **Rozložení**: <xref:System.Windows.Controls.Border>, <xref:System.Windows.Controls.Primitives.BulletDecorator>, <xref:System.Windows.Controls.Canvas>, <xref:System.Windows.Controls.DockPanel>, <xref:System.Windows.Controls.Expander>, <xref:System.Windows.Controls.Grid>, <xref:System.Windows.Controls.GridView>, <xref:System.Windows.Controls.GridSplitter>, <xref:System.Windows.Controls.GroupBox>, 0, 1, 2, 3, 5, 6, 7, 8, 9 a 0.

- **Media**: <xref:System.Windows.Controls.Image>, <xref:System.Windows.Controls.MediaElement> a <xref:System.Windows.Controls.SoundPlayerAction>.

- **Nabídky**: <xref:System.Windows.Controls.ContextMenu>, <xref:System.Windows.Controls.Menu> a <xref:System.Windows.Controls.ToolBar>.

- **Navigace**: <xref:System.Windows.Controls.Frame>, <xref:System.Windows.Documents.Hyperlink>, <xref:System.Windows.Controls.Page>, <xref:System.Windows.Navigation.NavigationWindow> a <xref:System.Windows.Controls.TabControl>.

- **Výběr**: <xref:System.Windows.Controls.CheckBox>, <xref:System.Windows.Controls.ComboBox>, <xref:System.Windows.Controls.ListBox>, <xref:System.Windows.Controls.RadioButton> a <xref:System.Windows.Controls.Slider>.

- **Informace o uživateli**: <xref:System.Windows.Controls.AccessText>, <xref:System.Windows.Controls.Label>, <xref:System.Windows.Controls.Primitives.Popup>, <xref:System.Windows.Controls.ProgressBar>, <xref:System.Windows.Controls.Primitives.StatusBar>, <xref:System.Windows.Controls.TextBlock> a <xref:System.Windows.Controls.ToolTip>.

## <a name="input-and-commands"></a>Vstupní příkazy a

Ovládací prvky nejčastěji zjišťují a reagují na vstup uživatele. [Vstupní systém WPF](/dotnet/framework/wpf/advanced/input-overview) používá přímé i směrované události pro podporu zadávání textu, správy fokusu a umístění myši.

Aplikace často mají komplexní požadavky na vstupy. WPF poskytuje [systém příkazů](/dotnet/framework/wpf/advanced/commanding-overview) , který odděluje akce vstupu uživatele od kódu, který reaguje na tyto akce.

## <a name="layout"></a>Rozložení

Když vytváříte uživatelské rozhraní, uspořádáte ovládací prvky podle umístění a velikosti pro vytvoření rozložení. Klíčovým požadavkem pro jakékoli rozložení je přizpůsobení změn velikosti okna a nastavení zobrazení. Namísto vynucení psaní kódu za účelem přizpůsobení rozložení za těchto okolností nabízí WPF pro vás špičkové rozšiřitelné systémové rozložení.

Základem systému rozložení je relativní umístění, které zvyšuje schopnost přizpůsobit se změnám oken a zobrazení podmínek. Kromě toho systém rozložení spravuje vyjednávání mezi ovládacími prvky pro určení rozložení. Vyjednávání je dvoustupňový proces: nejprve ovládací prvek oznamuje své nadřazené umístění a velikost, které vyžaduje. za druhé nadřazená položka oznamuje ovládacím prvkům, kolik místa může mít.

Systém rozložení je vystaven podřízeným ovládacím prvkům prostřednictvím základních tříd WPF. Pro společná rozložení, jako jsou mřížky, skládání a ukotvení, WPF obsahuje několik ovládacích prvků rozložení:

- <xref:System.Windows.Controls.Canvas>: Podřízené ovládací prvky poskytují své vlastní rozložení.

- <xref:System.Windows.Controls.DockPanel>: Podřízené ovládací prvky jsou zarovnány k okrajům panelu.

- <xref:System.Windows.Controls.Grid>: Podřízené ovládací prvky jsou umístěny podle řádků a sloupců.

- <xref:System.Windows.Controls.StackPanel>: Podřízené ovládací prvky jsou skládané buď svisle, nebo vodorovně.

- <xref:System.Windows.Controls.VirtualizingStackPanel>: Podřízené ovládací prvky jsou virtualizované a uspořádány na jednom řádku, který je buď vodorovně nebo svisle orientovaný na sebe.

- <xref:System.Windows.Controls.WrapPanel>: Podřízené ovládací prvky jsou umístěny v pořadí zleva doprava a zabaleny na další řádek, pokud existuje více ovládacích prvků na aktuálním řádku, než povoluje prostor.

Následující příklad používá <xref:System.Windows.Controls.DockPanel> k rozložení několika ovládacích prvků <xref:System.Windows.Controls.TextBox>.

[!code-xaml[IntroToWPFSnippets#LayoutMARKUP](../designers/codesnippet/Xaml/introduction-to-wpf_1.xaml)]

@No__t-0 umožňuje podřízeným ovládacím prvkům <xref:System.Windows.Controls.TextBox> sdělit, jak se mají uspořádat. K tomu <xref:System.Windows.Controls.DockPanel> implementuje připojenou vlastnost `Dock`, která je vystavena podřízeným ovládacím prvkům, aby každému z nich bylo možné zadat styl ukotvení.

> [!NOTE]
> Vlastnost, která je implementována nadřazeným ovládacím prvkem pro použití podřízenými ovládacími prvky, je konstrukce WPF nazývaná [připojená vlastnost](/dotnet/framework/wpf/advanced/attached-properties-overview).

Následující obrázek ukazuje výsledek kódu XAML v předchozím příkladu.

![Stránka DockPanel](../designers/media/wpfintrofigure11.png)

## <a name="data-binding"></a>Vytváření datových vazeb

Většina aplikací je vytvořená tak, aby uživatelům poskytovala prostředky k zobrazení a úpravám dat. V případě aplikací WPF je pro technologie, jako je SQL Server a ADO .NET, k dispozici práce s daty, která jsou již k dispozici. Po otevření dat a jejich načtení do spravovaných objektů aplikace je zahájena pevná práce pro aplikace WPF. V podstatě to zahrnuje dvě věci:

1. Kopírování dat ze spravovaných objektů do ovládacích prvků, kde lze data zobrazit a upravit.

2. Zajištění, že se změny provedené u dat pomocí ovládacích prvků zkopírují zpátky do spravovaných objektů.

Pro zjednodušení vývoje aplikací poskytuje WPF modul datových vazeb k automatickému provedení těchto kroků. Základní jednotkou modulu datových vazeb je třída @no__t 0, jejíž úkolem je vytvořit vazbu ovládacího prvku (cíl vazby) k datovému objektu (zdroj vazby). Tento vztah je znázorněný na následujícím obrázku:

![Základní diagram datových vazeb](../designers/media/databindingmostbasic.png)

Další příklad ukazuje, jak vytvořit navázání <xref:System.Windows.Controls.TextBox> na instanci vlastního objektu `Person`. Implementace `Person` je uvedena v následujícím kódu:

[!code-vb[SimpleDataBindingSnippets#PersonClassCODE](../designers/codesnippet/VisualBasic/introduction-to-wpf_2.vb)]
[!code-csharp[SimpleDataBindingSnippets#PersonClassCODE](../designers/codesnippet/CSharp/introduction-to-wpf_2.cs)]

Následující kód váže <xref:System.Windows.Controls.TextBox> do instance vlastního objektu `Person`.

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

V tomto příkladu je vytvořena instance třídy `Person` v kódu na pozadí a je nastavena jako datový kontext pro `DataBindingWindow`. V kódu je vlastnost <xref:System.Windows.Controls.TextBox.Text%2A> <xref:System.Windows.Controls.TextBox> svázána s vlastností `Person.Name` (pomocí syntaxe jazyka XAML "`{Binding ... }`"). Tento kód XAML oznamuje, že má WPF navazovat řízení <xref:System.Windows.Controls.TextBox> na objekt `Person`, který je uložený ve vlastnosti <xref:System.Windows.FrameworkElement.DataContext%2A> okna.

Modul datových vazeb WPF poskytuje další podporu, která zahrnuje ověřování, řazení, filtrování a seskupování. Kromě toho datová vazba podporuje použití datových šablon k vytvoření vlastního uživatelského rozhraní pro vázaná data v případě, že uživatelské rozhraní zobrazené standardními ovládacími prvky WPF není vhodné.

Další informace najdete v tématu [Přehled datových vazeb](/dotnet/framework/wpf/data/data-binding-overview).

## <a name="graphics"></a>Grafika

WPF přináší rozsáhlou, škálovatelnou a flexibilní sadu grafických funkcí, které mají následující výhody:

- Grafika nezávislá na **rozlišení a zařízení**. Základní jednotkou v grafickém systému WPF je pixel nezávislý na zařízení, který je 1/1/96 palce, bez ohledu na skutečné rozlišení obrazovky a poskytuje základ pro vykreslování nezávisle na rozlišení a na zařízení. Každé pixely nezávislé na zařízení se automaticky škáluje tak, aby se shodovalo s nastavením bodů na palec (dpi) systému, na kterém se vykreslí.

- **Vylepšená přesnost**. Systém souřadnic WPF se měří s čísly s plovoucí desetinnou čárkou s dvojitou přesností, nikoli s jednoduchou přesností. Transformace a hodnoty neprůhlednosti se také vyjadřují jako dvojitá přesnost. WPF také podporuje šířku barevné škály (scRGB) a poskytuje integrovanou podporu pro správu vstupů z různých barevných prostorů.

- **Pokročilá podpora grafiky a animací** WPF zjednodušuje programování grafiky tím, že vám umožní spravovat animace na pozadí. Nemusíte se starat o zpracování scény, vykreslování smyček a varianty interpolaci. Kromě toho WPF poskytuje podporu testování testů a úplnou podporu pro skládání v alfa.

- **Hardwarová akcelerace**. Grafický systém WPF využívá grafický hardware k minimalizaci využití procesoru.

### <a name="2d-shapes"></a>2D obrazce

WPF poskytuje knihovnu běžných 2D nakreslených 2D tvarů, jako jsou obdélníky a tři tečky, které jsou zobrazeny na následujícím obrázku:

![Elipsy a obdélníky](../designers/media/wpfintrofigure4.PNG)

Zajímavou schopností tvarů je, že nejsou jenom pro zobrazení; obrazce implementují mnoho funkcí, které očekáváte od ovládacích prvků, včetně vstupu klávesnice a myši. Následující příklad ukazuje <xref:System.Windows.UIElement.MouseUp> událost zpracování <xref:System.Windows.Shapes.Ellipse>.

[!code-xaml[IntroToWPFSnippets#HandleEllipseMouseUpEventMARKUP](../designers/codesnippet/Xaml/introduction-to-wpf_7.xaml)]

[!code-vb[IntroToWPFSnippets#HandleEllipseMouseUpEventCODEBEHIND](../designers/codesnippet/VisualBasic/introduction-to-wpf_8.vb)]
[!code-csharp[IntroToWPFSnippets#HandleEllipseMouseUpEventCODEBEHIND](../designers/codesnippet/CSharp/introduction-to-wpf_8.cs)]

Následující obrázek ukazuje, co je vyrobeno v předchozím kódu.

![Okno s textem "kliknuli jste na elipsu&#33;"](../designers/media/wpfintrofigure12.png)

Další informace naleznete v tématu [Shapes and Basic Drawing in WPF Overview](/dotnet/framework/wpf/data/data-binding-overview).

### <a name="2d-geometries"></a>2D geometrií

2D obrazce, které poskytuje WPF, se týkají standardní sady základních tvarů. Je však možné, že budete muset vytvořit vlastní tvary, aby bylo usnadněno navrhování přizpůsobeného uživatelského rozhraní. Pro účely tohoto účelu WPF poskytuje geometrií. Následující obrázek ukazuje použití geometrií k vytvoření vlastního tvaru, který lze vykreslit přímo, použít jako štětec nebo použít k Vystřižení jiných tvarů a ovládacích prvků.

objekty <xref:System.Windows.Shapes.Path> lze použít k vykreslení uzavřených nebo otevřených tvarů, více tvarů a dokonce i zakřivených tvarů.

objekty <xref:System.Windows.Media.Geometry> lze použít pro oříznutí, testování přístupů a vykreslování 2D grafických dat.

![Různá použití cesty](../designers/media/wpfintrofigure5.png)

Další informace najdete v tématu [geometrie Overview](/dotnet/framework/wpf/graphics-multimedia/geometry-overview).

### <a name="2d-effects"></a>2D efekty

Podmnožina možností WPF 2D zahrnuje vizuální efekty, jako jsou barevné přechody, bitmapy, kresby, Malování s videi, otočení, škálování a zkosení. Všechny jsou dosaženy pomocí štětců; Následující obrázek ukazuje několik příkladů.

![Ilustrace různých štětců](../designers/media/wpfintrofigure6.png)

Další informace najdete v tématu [Přehled štětců WPF](/dotnet/framework/wpf/graphics-multimedia/wpf-brushes-overview).

### <a name="3d-rendering"></a>Prostorové vykreslování

WPF také zahrnuje možnosti prostorového vykreslování, které se integrují s 2D grafikou, aby bylo možné vytvářet zajímavější a zajímavá uživatelská rozhraní. Například následující obrázek znázorňuje 2D obrázky vykreslené na 3D tvary.

![Snímek obrazovky ukázka Visual3D](../designers/media/wpfintrofigure13.png)

Další informace najdete v tématu [Přehled 3D grafiky](/dotnet/framework/wpf/graphics-multimedia/3-d-graphics-overview).

## <a name="animation"></a>Animace

Podpora animace WPF umožňuje řídit, protřepání, otočení a zmizení ovládacích prvků, aby bylo možné vytvářet zajímavé přechody stránky a další. Můžete animovat většinu tříd WPF, dokonce i vlastní třídy. Na následujícím obrázku je znázorněna jednoduchá animace v akci.

![Obrázky animované datové krychle](../designers/media/wpfintrofigure7.png)

Další informace najdete v tématu [Přehled animací](/dotnet/framework/wpf/graphics-multimedia/animation-overview).

## <a name="media"></a>Média

Jedním ze způsobů, jak vyjádřit bohatou část obsahu, je použití audiovizuálních médií. WPF poskytuje speciální podporu pro obrázky, video a zvuk.

### <a name="images"></a>Obrázky

Obrázky jsou společné pro většinu aplikací a WPF nabízí několik způsobů jejich použití. Následující obrázek ukazuje uživatelské rozhraní se seznamem, které obsahuje miniatury obrázků. Když je vybraná Miniatura, zobrazí se obrázek v plné velikosti.

![Obrázky miniatur a obrázek plné&#45;velikosti](../designers/media/wpfintrofigure8.png)

Další informace najdete v tématu [Přehled imagí](/dotnet/framework/wpf/graphics-multimedia/imaging-overview).

### <a name="video-and-audio"></a>Video a zvuk

Ovládací prvek <xref:System.Windows.Controls.MediaElement> je schopný přehrávat video i zvuk a je dostatečně flexibilní, aby byl základem pro vlastní přehrávač médií. Následující kód XAML implementuje přehrávač médií.

[!code-xaml[IntroToWPFSnippets#MediaElementMARKUP](../designers/codesnippet/Xaml/introduction-to-wpf_9.xaml)]

Okno na následujícím obrázku ukazuje ovládací prvek <xref:System.Windows.Controls.MediaElement> v akci.

![Ovládací prvek MediaElement se zvukem a videem](../designers/media/wpfintrofigure1.png)

Další informace najdete v tématu [grafika a multimédia](/dotnet/framework/wpf/graphics-multimedia).

## <a name="text-and-typography"></a>Text a typografie

Pro usnadnění vysoce kvalitního vykreslování textu nabízí WPF tyto funkce:

- Podpora písma OpenType.

- Vylepšení technologie ClearType.

- Vysoký výkon, který využívá hardwarovou akceleraci.

- Integrace textu s médii, grafikou a animací

- Mezinárodní podpora písem a nouzové mechanismy.

Jako ukázku integrace textu s grafikou ukazuje následující obrázek použití dekorace textu.

![Text s různými dekoracemi textu](../designers/media/wpfintrofigure23.png)

Další informace najdete v tématu [Typografie v Windows Presentation Foundation](/dotnet/framework/wpf/advanced/typography-in-wpf).

## <a name="customize-wpf-apps"></a>Přizpůsobení aplikací WPF

Až do tohoto okamžiku jste viděli základní stavební bloky WPF pro vývoj aplikací. Model aplikace použijete k hostování a dodávání obsahu aplikace, který se skládá hlavně z ovládacích prvků. Chcete-li zjednodušit uspořádání ovládacích prvků v uživatelském rozhraní a zajistit, aby bylo uspořádání udržováno v tvář změny velikosti okna a nastavení zobrazení, použijte systém rozložení WPF. Vzhledem k tomu, že většina aplikací umožňuje uživatelům pracovat s daty, můžete použít datovou vazbu k omezení práce v rámci integrace uživatelského rozhraní s daty. Chcete-li zlepšit vizuální vzhled aplikace, použijte komplexní škálu grafiky, animace a podpory médií, které poskytuje WPF.

Většinou ale nemusíte vytvářet a spravovat skutečně odlišná a vizuálně působivé uživatelské prostředí. Standardní ovládací prvky WPF nemusí být integrovány s požadovaným vzhledem aplikace. Data se nemusí zobrazovat v nejúčinnějším způsobu. Celkové uživatelské prostředí vaší aplikace nemusí být vhodné pro výchozí vzhled a chování motivů systému Windows. V mnoha způsobech prezentace potřebuje vizuální rozšiřitelnost, a to podobně jako jakýkoli jiný typ rozšiřitelnosti.

Z tohoto důvodu WPF poskytuje řadu mechanismů pro vytváření jedinečných uživatelských prostředí, včetně modelu bohatých obsahu pro ovládací prvky, triggery, ovládací prvky a šablony dat, styly, prostředky uživatelského rozhraní a motivy a vzhledy.

### <a name="content-model"></a>Model obsahu

Hlavním účelem většiny ovládacích prvků WPF je zobrazení obsahu. V WPF je typ a počet položek, které mohou být obsahem ovládacího prvku, označovány jako *model obsahu*ovládacího prvku. Některé ovládací prvky mohou obsahovat jednu položku a typ obsahu; například obsah <xref:System.Windows.Controls.TextBox> je řetězcová hodnota, která je přiřazena vlastnosti <xref:System.Windows.Controls.TextBox.Text%2A>. Následující příklad nastaví obsah <xref:System.Windows.Controls.TextBox>.

```xaml
<Window
    xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
    xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
    x:Class="SDKSample.TextBoxContentWindow"
    Title="TextBox Content">

    <TextBox Text="This is the content of a TextBox." />
</Window>
```

Výsledek je znázorněn na následujícím obrázku.

![Ovládací prvek TextBox, který obsahuje text](../designers/media/wpfintrofigure21.png)

Jiné ovládací prvky však mohou obsahovat více položek různých typů obsahu; obsah <xref:System.Windows.Controls.Button> určený vlastností <xref:System.Windows.Controls.ContentControl.Content%2A> může obsahovat různé položky, včetně ovládacích prvků rozložení, textu, obrázků a tvarů. Následující příklad ukazuje <xref:System.Windows.Controls.Button> s obsahem, který obsahuje <xref:System.Windows.Controls.DockPanel>, <xref:System.Windows.Controls.Label>, <xref:System.Windows.Controls.Border> a <xref:System.Windows.Controls.MediaElement>.

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

Následující obrázek ukazuje obsah tohoto tlačítka.

![Tlačítko, které obsahuje více typů obsahu](../designers/media/wpfintrofigure22.png)

Další informace o typech obsahu, které jsou podporovány různými ovládacími prvky, naleznete v tématu [model obsahu WPF](/dotnet/framework/wpf/controls/wpf-content-model).

### <a name="triggers"></a>Aktivační procedury

I když hlavní účel kódu XAML je implementovat vzhled aplikace, můžete také použít XAML k implementaci některých aspektů chování aplikace. Jedním z příkladů je použití triggerů ke změně vzhledu aplikace na základě interakcí uživatelů. Další informace najdete v tématu [styly a šablony](/dotnet/desktop-wpf/fundamentals/styles-templates-overview).

### <a name="control-templates"></a>Šablony ovládacích prvků

Výchozí uživatelská rozhraní pro ovládací prvky WPF jsou obvykle vytvořena z jiných ovládacích prvků a tvarů. Například <xref:System.Windows.Controls.Button> se skládá z ovládacích prvků <xref:Microsoft.Windows.Themes.ButtonChrome> a <xref:System.Windows.Controls.ContentPresenter>. @No__t-0 poskytuje standardní vzhled tlačítka, zatímco <xref:System.Windows.Controls.ContentPresenter> zobrazuje obsah tlačítka, jak určuje vlastnost <xref:System.Windows.Controls.ContentControl.Content%2A>.

Někdy se může stát, že výchozí vzhled ovládacího prvku bude incongruent s celkovým vzhledem aplikace. V tomto případě můžete použít <xref:System.Windows.Controls.ControlTemplate> ke změně vzhledu uživatelského rozhraní ovládacího prvku, aniž byste museli měnit jeho obsah a chování.

Například následující příklad ukazuje, jak změnit vzhled <xref:System.Windows.Controls.Button> pomocí <xref:System.Windows.Controls.ControlTemplate>.

[!code-xaml[IntroToWPFSnippets#ButtonControlTemplateWindowMARKUP](../designers/codesnippet/Xaml/introduction-to-wpf_16.xaml)]

[!code-csharp[IntroToWPFSnippets#ButtonControlTemplateWindowCODEBEHIND](../designers/codesnippet/CSharp/introduction-to-wpf_17.cs)]
[!code-vb[IntroToWPFSnippets#ButtonControlTemplateWindowCODEBEHIND](../designers/codesnippet/VisualBasic/introduction-to-wpf_17.vb)]

V tomto příkladu bylo tlačítko výchozí uživatelské rozhraní nahrazeno hodnotou <xref:System.Windows.Shapes.Ellipse> s tmavě modrým ohraničením a je vyplněno pomocí <xref:System.Windows.Media.RadialGradientBrush>. Ovládací prvek <xref:System.Windows.Controls.ContentPresenter> zobrazí obsah <xref:System.Windows.Controls.Button> a "Click to!". Když se klikne na <xref:System.Windows.Controls.Button>, událost <xref:System.Windows.Controls.Primitives.ButtonBase.Click> se stále vyvolá jako součást výchozího chování ovládacího prvku <xref:System.Windows.Controls.Button>. Výsledek je znázorněn na následujícím obrázku:

![Eliptické tlačítko a druhé okno](../designers/media/wpfintrofigure2.png)

### <a name="data-templates"></a>Datové šablony

Zatímco šablona ovládacího prvku umožňuje určit vzhled ovládacího prvku, šablona data umožňuje určit vzhled obsahu ovládacího prvku. Šablony dat se často používají k vylepšení způsobu zobrazení vázaných dat. Následující obrázek ukazuje výchozí vzhled pro <xref:System.Windows.Controls.ListBox>, který je svázán s kolekcí objektů `Task`, kde každá úloha má název, popis a prioritu.

![Rozevírací seznam s výchozím vzhledem](../designers/media/wpfintrofigure18.png)

Výchozí vzhled je to, co byste očekávali od <xref:System.Windows.Controls.ListBox>. Výchozí vzhled jednotlivých úloh však obsahuje pouze název úlohy. Chcete-li zobrazit název, popis a prioritu úlohy, je třeba změnit výchozí vzhled položek vázaného seznamu ovládacího prvku <xref:System.Windows.Controls.ListBox> pomocí <xref:System.Windows.DataTemplate>. Následující kód XAML definuje takový <xref:System.Windows.DataTemplate>, který je použit pro každý úkol pomocí atributu <xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A>.

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

Následující obrázek ukazuje účinek tohoto kódu.

![Seznam, který používá šablonu dat](../designers/media/wpfintrofigure19.png)

Všimněte si, že <xref:System.Windows.Controls.ListBox> zachovává chování a celkový vzhled; změnil se pouze vzhled obsahu zobrazeného v poli se seznamem.

Další informace najdete v tématu [Přehled šablonování dat](/dotnet/framework/wpf/data/data-templating-overview).

### <a name="styles"></a>Styly

Styly umožňují vývojářům a návrhářům standardizovat konkrétní vzhled pro svůj produkt. WPF poskytuje model silného stylu, který je základem elementu <xref:System.Windows.Style>. Následující příklad vytvoří styl, který nastaví barvu pozadí pro každé <xref:System.Windows.Controls.Button> v okně na `Orange`.

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

Vzhledem k tomu, že tento styl cílí na všechny ovládací prvky <xref:System.Windows.Controls.Button>, je styl automaticky použit pro všechna tlačítka v okně, jak je znázorněno na následujícím obrázku:

![Dvě oranžová tlačítka](../designers/media/wpfintrofigure20.png)

Další informace najdete v tématu [styly a šablony](/dotnet/desktop-wpf/fundamentals/styles-templates-overview).

### <a name="resources"></a>Zdroje a prostředky

Ovládací prvky v aplikaci by měly sdílet stejný vzhled, který může obsahovat cokoli z písma a barev pozadí pro řízení šablon, šablon dat a stylů. Můžete použít podporu WPF pro prostředky uživatelského rozhraní k zapouzdření těchto prostředků v jednom umístění pro opakované použití.

Následující příklad definuje společnou barvu pozadí, která je sdílena pomocí <xref:System.Windows.Controls.Button> a <xref:System.Windows.Controls.Label>.

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

Tento příklad implementuje zdroj barvy pozadí pomocí elementu vlastnosti `Window.Resources`. Tento prostředek je k dispozici všem podřízeným objektům <xref:System.Windows.Window>. Existují různé obory prostředků, včetně následujících, v pořadí, ve kterém jsou vyřešeny:

1. Individuální ovládací prvek (pomocí zděděné vlastnosti <xref:System.Windows.FrameworkElement.Resources%2A?displayProperty=fullName>).

2. @No__t-0 nebo <xref:System.Windows.Controls.Page> (používá se také zděděná vlastnost <xref:System.Windows.FrameworkElement.Resources%2A?displayProperty=fullName>).

3. @No__t-0 (pomocí vlastnosti <xref:System.Windows.Application.Resources%2A?displayProperty=fullName>).

Různé obory vám umožňují flexibilitu v závislosti na způsobu, jakým definujete a sdílíte své prostředky.

Jako alternativu k přímému přiřazení prostředků k určitému oboru můžete jeden nebo víc prostředků zabalit pomocí samostatného <xref:System.Windows.ResourceDictionary>, na které se dá odkazovat v jiných částech aplikace. Například následující příklad definuje výchozí barvu pozadí ve slovníku prostředků.

```xaml
<ResourceDictionary
    xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
    xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml">

  <!-- Define background color resource -->
  <SolidColorBrush x:Key="defaultBackground" Color="Red" />

  <!-- Define other resources -->
</ResourceDictionary>
```

Následující příklad odkazuje na slovník prostředků definovaný v předchozím příkladu tak, aby byl sdílen napříč aplikací.

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

Prostředky a slovníky prostředků jsou základem podpory WPF pro motivy a vzhledy.

Další informace najdete v tématu [prostředky](/dotnet/framework/wpf/advanced/xaml-resources).

### <a name="custom-controls"></a>Vlastní ovládací prvky

I když WPF poskytuje hostitele podpory přizpůsobení, může dojít k situacím, kdy existující ovládací prvky WPF nesplňují požadavky vaší aplikace nebo jejích uživatelů. K tomu může dojít v těchto případech:

- Uživatelské rozhraní, které požadujete, nelze vytvořit přizpůsobením vzhledu a chování stávajících implementací WPF.

- Požadované chování není podporováno (nebo není podporováno) stávajícími implementacemi WPF.

V tuto chvíli ale můžete využít jeden ze tří modelů WPF pro vytvoření nového ovládacího prvku. Každý model cílí na konkrétní scénář a vyžaduje, aby váš vlastní ovládací prvek byl odvozen z konkrétní základní třídy WPF. Tady jsou uvedené tři modely:

- **Model uživatelského ovládacího prvku**. Vlastní ovládací prvek je odvozen z <xref:System.Windows.Controls.UserControl> a skládá se z jednoho nebo více dalších ovládacích prvků.

- **Model ovládacího prvku**. Vlastní ovládací prvek je odvozen z <xref:System.Windows.Controls.Control> a používá se k sestavování implementací, které oddělují své chování od jejich vzhledu pomocí šablon, podobně jako většina ovládacích prvků WPF. Odvození z <xref:System.Windows.Controls.Control> umožňuje vytvořit vlastní uživatelské rozhraní než uživatelské ovládací prvky, ale může to vyžadovat více úsilí.

- **Model elementu rozhraní**. Vlastní ovládací prvek je odvozen z <xref:System.Windows.FrameworkElement>, pokud je jeho vzhled definován pomocí vlastní logiky vykreslování (ne šablon).

Následující příklad ukazuje vlastní číselnou kontrolu nahoru/dolů, která je odvozena z <xref:System.Windows.Controls.UserControl>.

[!code-xaml[IntroToWPFSnippets#UserControlMARKUP](../designers/codesnippet/Xaml/introduction-to-wpf_33.xaml)]

[!code-csharp[IntroToWPFSnippets#UserControlCODEBEHIND1](../designers/codesnippet/CSharp/introduction-to-wpf_34.cs)]
[!code-vb[IntroToWPFSnippets#UserControlCODEBEHIND1](../designers/codesnippet/VisualBasic/introduction-to-wpf_34.vb)]

Následující příklad ilustruje kód XAML, který je požadován pro zahrnutí uživatelského ovládacího prvku do <xref:System.Windows.Window>.

[!code-xaml[IntroToWPFSnippets#UserControlWindowMARKUP1](../designers/codesnippet/Xaml/introduction-to-wpf_37.xaml)]

Následující obrázek znázorňuje ovládací prvek `NumericUpDown` hostovaný v <xref:System.Windows.Window>.

![Vlastní UserControl](../designers/media/wpfintrofigure3.png)

Další informace o vlastních ovládacích prvcích najdete v tématu [Přehled vytváření ovládacích](/dotnet/framework/wpf/controls/control-authoring-overview)prvků.

## <a name="wpf-best-practices"></a>Osvědčené postupy pro WPF

Stejně jako u jakékoli vývojové platformy je možné WPF použít různými způsoby, abyste dosáhli požadovaného výsledku. Jako způsob, jak zajistit, aby vaše aplikace WPF poskytovaly požadované uživatelské prostředí a splňovaly požadavky cílové skupiny obecně, existují Doporučené osvědčené postupy pro přístupnost, globalizaci a lokalizaci a výkon. Další informace naleznete v tématu:

- [Usnadnění](/dotnet/framework/ui-automation/accessibility-best-practices)
- [Globalizace a lokalizace WPF](/dotnet/framework/wpf/advanced/wpf-globalization-and-localization-overview)
- [Výkon aplikace WPF](/dotnet/framework/wpf/advanced/optimizing-wpf-application-performance)
- [Zabezpečení WPF](/dotnet/framework/wpf/security-wpf)

## <a name="next-steps"></a>Další kroky

Prohlédli jsme si klíčové funkce WPF. Nyní je čas vytvořit svou první aplikaci WPF.

> [!div class="nextstepaction"]
> [Návod: Moje první desktopová aplikace WPF @ no__t-0

## <a name="see-also"></a>Viz také:

- [Začínáme s WPF (Windows Presentation Foundation)](../designers/getting-started-with-wpf.md)
- [Windows Presentation Foundation](/dotnet/framework/wpf/index)
- [Komunitní materiály pro WPF](/dotnet/framework/wpf/getting-started/community-feedback)