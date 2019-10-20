---
title: Úvod do WPF | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-designers
ms.topic: conceptual
ms.assetid: b8d7cf43-d1f2-4f3d-adb0-4f3a6428edc0
caps.latest.revision: 7
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 8b33c558187fd32ef7cbd420dce8d627ddc944d6
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72664339"
---
# <a name="introduction-to-wpf"></a>Úvod do WPF
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Windows Presentation Foundation (WPF) umožňuje vytváření klientských aplikací pro Windows s vizuálně poutavými uživatelskými prostředími.

 ![Ukázka uživatelského rozhraní pro zdravotní péče společnosti Contoso](../designers/media/wpfintrofigure24.png "WPFIntroFigure24")

 Jádrem WPF je modul vykreslování založený na rozlišení a vektorový vykreslovací modul, který je sestaven tak, aby využíval výhody moderního grafického hardwaru. WPF rozšiřuje jádro o komplexní sadu funkcí pro vývoj aplikací, které zahrnují jazyk Extensible Application Markup Language (XAML) (XAML), ovládací prvky, datové vazby, rozložení, 2D a 3D grafiky, animace, styly, šablony, dokumenty, multimédia, text a Typografie. WPF je součástí .NET Framework, takže můžete sestavovat aplikace, které zahrnují další prvky knihovny tříd .NET Framework.

 Tento přehled je určený pro Newcomers a pokrývá klíčové funkce a koncepty WPF.

## <a name="Programming_with_WPF"></a>Programování pomocí WPF
 WPF existuje jako podmnožina .NET Frameworkch typů, které jsou pro většinu nacházející se v oboru názvů <xref:System.Windows>. Pokud jste dříve vytvořili aplikace s .NET Framework pomocí spravovaných technologií, jako je ASP.NET a model Windows Forms, měli byste znát základní programovací prostředí WPF. můžete vytvářet instance tříd, nastavovat vlastnosti, volat metody a zpracovávat události, a to C# vše pomocí vašeho oblíbeného programovacího jazyka .NET, například nebo Visual Basic.

 WPF obsahuje další programovací konstrukce, které vylepšují vlastnosti a události: [vlastnosti závislosti](https://msdn.microsoft.com/library/ms752914\(v=vs.100\).aspx) a [směrované události](https://msdn.microsoft.com/library/ms742806\(v=vs.100\).aspx).

## <a name="Markup_And_Codebehind"></a>Značky a kód na pozadí
 WPF umožňuje vyvíjet aplikace pomocí *značek* i *kódu na pozadí*, což je prostředí, ve kterém by ASP.NET vývojáři měli znát. Obecně se používá kód XAML k implementaci vzhledu aplikace při použití spravovaných programovacích jazyků (kódu na pozadí) k implementaci jeho chování. Toto oddělení vzhledu a chování přináší následující výhody:

- Náklady na vývoj a údržbu jsou sníženy, protože označení specifické pro vzhled není pevně spojeno s kódem specifickým pro chování.

- Vývoj je efektivnější, protože návrháři můžou implementovat vzhled aplikace současně s vývojáři, kteří implementují chování aplikace.

- [Globalizace a lokalizace](https://msdn.microsoft.com/library/ms788718\(v=vs.100\).aspx) pro aplikace WPF je zjednodušená.

  Následuje stručný úvod do kódu WPF a kódu na pozadí.

### <a name="markup"></a>Revize
 XAML je značkovací jazyk založený na jazyce XML, který se používá k deklarativní implementaci vzhledu aplikace. Obvykle se používá k vytváření oken, dialogových oken, stránek a uživatelských ovládacích prvků a k jejich vyplnění ovládacími prvky, tvary a grafikou.

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

 Konkrétně tento kód XAML definuje okno a tlačítko pomocí prvků `Window` a `Button` v uvedeném pořadí. Každý element je nakonfigurován s atributy, jako je `Title` atribut `Window` elementu pro určení textu záhlaví okna. V době běhu převede WPF prvky a atributy, které jsou definovány v označení, na instance tříd WPF. Například `Window` element je převeden na instanci <xref:System.Windows.Window> třídy, jejíž vlastnost <xref:System.Windows.Window.Title%2A> je hodnota atributu `Title`.

 Následující obrázek ukazuje uživatelské rozhraní (UI), které je definováno XAML v předchozím příkladu.

 ![Okno obsahující tlačítko](../designers/media/wpfintrofigure10.png "WPFIntroFigure10")

 Vzhledem k tomu, že XAML je založen na formátu XML, uživatelské rozhraní, které v něm vytvoříte, je sestaveno v hierarchii vnořených elementů, které jsou označovány jako [strom elementu](https://msdn.microsoft.com/library/ms753391\(v=vs.100\).aspx). Strom elementů poskytuje logický a intuitivní způsob, jak vytvořit a spravovat uživatelská rozhraní.

### <a name="code-behind"></a>Kód na pozadí
 Hlavním chováním aplikace je implementovat funkcionalitu, která reaguje na interakce uživatele, včetně zpracování událostí (například kliknutí na nabídku, panel nástrojů nebo tlačítko) a volání obchodní logiky a logiky přístupu k datům v reakci. V jazyce WPF je toto chování obecně implementováno v kódu, který je spojen s označením. Tento typ kódu je známý jako kód na pozadí. Následující příklad ukazuje aktualizovaný kód z předchozího příkladu a kód na pozadí.

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

 V tomto příkladu kód na pozadí implementuje třídu, která je odvozena od třídy <xref:System.Windows.Window>. Atribut `x:Class` slouží k přidružení značky ke třídě s kódem na pozadí. `InitializeComponent` je volána z konstruktoru třídy kódu na pozadí pro sloučení uživatelského rozhraní, které je definováno v označení pomocí třídy kódu na pozadí. (`InitializeComponent` se vygeneruje při sestavení vaší aplikace, což znamená, že je nemusíte implementovat ručně.) Kombinace `x:Class` a `InitializeComponent` zajistí, že se vaše implementace správně inicializuje při každém vytvoření. Třída kódu na pozadí implementuje také obslužnou rutinu události pro událost <xref:System.Windows.Controls.Primitives.ButtonBase.Click> tlačítka. Po kliknutí na tlačítko, obslužná rutina události zobrazí okno se zprávou voláním metody <xref:System.Windows.MessageBox.Show%2A?displayProperty=fullName>.

 Následující obrázek ukazuje výsledek při kliknutí na tlačítko.

 ![MessageBox](../designers/media/wpfintrofigure25.png "WPFIntroFigure25")

## <a name="Controls"></a>Ovládací prvky
 Uživatelské prostředí, které jsou dodávány aplikačním modelem, jsou konstruovány ovládací prvky. V rámci WPF je "ovládacím prvkem" výraz, který se vztahuje na kategorii tříd WPF, které jsou hostovány buď v okně, nebo na stránce, mají uživatelské rozhraní a implementují určité chování.

 Další informace najdete v tématu [ovládací prvky](https://msdn.microsoft.com/library/3f255a8a-35a8-4712-9065-472ff7d75599).

### <a name="wpf-controls-by-function"></a>Ovládací prvky WPF podle funkcí
 Tady jsou uvedené předdefinované ovládací prvky WPF.

- **Buttons**: <xref:System.Windows.Controls.Button> a <xref:System.Windows.Controls.Primitives.RepeatButton>.

- **Zobrazení dat**: <xref:System.Windows.Controls.DataGrid>, <xref:System.Windows.Controls.ListView> a <xref:System.Windows.Controls.TreeView>.

- **Zobrazení data a výběr**: <xref:System.Windows.Controls.Calendar> a <xref:System.Windows.Controls.DatePicker>.

- **Dialogová okna**: <xref:Microsoft.Win32.OpenFileDialog>, <xref:System.Windows.Controls.PrintDialog> a <xref:Microsoft.Win32.SaveFileDialog>.

- **Digitální inkoust**: <xref:System.Windows.Controls.InkCanvas> a <xref:System.Windows.Controls.InkPresenter>.

- **Documents**: <xref:System.Windows.Controls.DocumentViewer>, <xref:System.Windows.Controls.FlowDocumentPageViewer>, <xref:System.Windows.Controls.FlowDocumentReader>, <xref:System.Windows.Controls.FlowDocumentScrollViewer> a <xref:System.Windows.Controls.StickyNoteControl>.

- **Input**: <xref:System.Windows.Controls.TextBox>, <xref:System.Windows.Controls.RichTextBox> a <xref:System.Windows.Controls.PasswordBox>.

- **Rozložení**: <xref:System.Windows.Controls.Border>, <xref:System.Windows.Controls.Primitives.BulletDecorator>, <xref:System.Windows.Controls.Canvas>, <xref:System.Windows.Controls.DockPanel>, <xref:System.Windows.Controls.Expander>, <xref:System.Windows.Controls.Grid>, <xref:System.Windows.Controls.GridView>, <xref:System.Windows.Controls.GridSplitter>, <xref:System.Windows.Controls.GroupBox>, 0, 1, 2, 3, 4, 5 , 6, 7, 8, 9 a 0.

- **Media**: <xref:System.Windows.Controls.Image>, <xref:System.Windows.Controls.MediaElement> a <xref:System.Windows.Controls.SoundPlayerAction>.

- **Nabídky**: <xref:System.Windows.Controls.ContextMenu>, <xref:System.Windows.Controls.Menu> a <xref:System.Windows.Controls.ToolBar>.

- **Navigace**: <xref:System.Windows.Controls.Frame>, <xref:System.Windows.Documents.Hyperlink>, <xref:System.Windows.Controls.Page>, <xref:System.Windows.Navigation.NavigationWindow> a <xref:System.Windows.Controls.TabControl>.

- **Výběr**: <xref:System.Windows.Controls.CheckBox>, <xref:System.Windows.Controls.ComboBox>, <xref:System.Windows.Controls.ListBox>, <xref:System.Windows.Controls.RadioButton> a <xref:System.Windows.Controls.Slider>.

- **Informace o uživateli**: <xref:System.Windows.Controls.AccessText>, <xref:System.Windows.Controls.Label>, <xref:System.Windows.Controls.Primitives.Popup>, <xref:System.Windows.Controls.ProgressBar>, <xref:System.Windows.Controls.Primitives.StatusBar>, <xref:System.Windows.Controls.TextBlock> a <xref:System.Windows.Controls.ToolTip>.

## <a name="Input_And_Commanding"></a>Vstup a příkazy
 Ovládací prvky nejčastěji zjišťují a reagují na vstup uživatele. [Vstupní systém WPF](https://msdn.microsoft.com/library/ms754010\(v=vs.100\).aspx) používá přímé i směrované události pro podporu zadávání textu, správy fokusu a umístění myši.

 Aplikace často mají komplexní požadavky na vstupy. WPF poskytuje [systém příkazů](https://msdn.microsoft.com/library/ms752308\(v=vs.100\).aspx) , který odděluje akce vstupu uživatele od kódu, který reaguje na tyto akce.

## <a name="Layout"></a>Rozložení
 Když vytváříte uživatelské rozhraní, uspořádáte ovládací prvky podle umístění a velikosti pro vytvoření rozložení. Klíčovým požadavkem pro jakékoli rozložení je přizpůsobení změn velikosti okna a nastavení zobrazení. Namísto vynucení psaní kódu za účelem přizpůsobení rozložení za těchto okolností nabízí WPF pro vás špičkové rozšiřitelné systémové rozložení.

 Základem systému rozložení je relativní umístění, které zvyšuje schopnost přizpůsobit se změnám oken a zobrazení podmínek. Kromě toho systém rozložení spravuje vyjednávání mezi ovládacími prvky pro určení rozložení. Vyjednávání je dvoustupňový proces: nejprve ovládací prvek oznamuje své nadřazené umístění a velikost, které vyžaduje. za druhé nadřazená položka oznamuje ovládacím prvkům, kolik místa může mít.

 Systém rozložení je vystaven podřízeným ovládacím prvkům prostřednictvím základních tříd WPF. Pro společná rozložení, jako jsou mřížky, skládání a ukotvení, WPF obsahuje několik ovládacích prvků rozložení:

- <xref:System.Windows.Controls.Canvas>: podřízené ovládací prvky poskytují své vlastní rozložení.

- <xref:System.Windows.Controls.DockPanel>: podřízené ovládací prvky jsou zarovnány k okrajům panelu.

- <xref:System.Windows.Controls.Grid>: podřízené ovládací prvky jsou umístěny podle řádků a sloupců.

- <xref:System.Windows.Controls.StackPanel>: podřízené ovládací prvky jsou skládané buď svisle nebo vodorovně.

- <xref:System.Windows.Controls.VirtualizingStackPanel>: podřízené ovládací prvky jsou virtualizované a uspořádány na jednom řádku, který je buď vodorovně, nebo svisle orientovaný.

- <xref:System.Windows.Controls.WrapPanel>: podřízené ovládací prvky jsou umístěny v pořadí zleva doprava a zabaleny na další řádek, pokud existuje více ovládacích prvků na aktuálním řádku, než umožňuje prostor.

  Následující příklad používá <xref:System.Windows.Controls.DockPanel> k rozložení několika ovládacích prvků <xref:System.Windows.Controls.TextBox>.

  [!code-xml[IntroToWPFSnippets#LayoutMARKUP](../snippets/csharp/VS_Snippets_Wpf/IntroToWPFSnippets/CSharp/LayoutWindow.xaml#layoutmarkup)]

  @No__t_0 umožňuje podřízeným ovládacím prvkům <xref:System.Windows.Controls.TextBox> sdělit, jak se mají uspořádat. K tomu <xref:System.Windows.Controls.DockPanel> implementuje vlastnost <xref:System.Windows.Controls.DockPanel.Dock%2A>, která je vystavena podřízeným ovládacím prvkům, aby každému z nich bylo možné zadat styl ukotvení.

> [!NOTE]
> Vlastnost, která je implementována nadřazeným ovládacím prvkem pro použití podřízenými ovládacími prvky, je konstrukce WPF nazývaná [připojená vlastnost](https://msdn.microsoft.com/library/ms749011\(v=vs.100\).aspx).

 Následující obrázek ukazuje výsledek kódu XAML v předchozím příkladu.

 ![Stránka DockPanel](../designers/media/wpfintrofigure11.png "WPFIntroFigure11")

## <a name="Data_Binding"></a>Datová vazba
 Většina aplikací je vytvořená tak, aby uživatelům poskytovala prostředky k zobrazení a úpravám dat. V případě aplikací WPF je pro technologie, jako je SQL Server a ADO .NET, k dispozici práce s daty, která jsou již k dispozici. Po otevření dat a jejich načtení do spravovaných objektů aplikace je zahájena pevná práce pro aplikace WPF. V podstatě to zahrnuje dvě věci:

1. Kopírování dat ze spravovaných objektů do ovládacích prvků, kde lze data zobrazit a upravit.

2. Zajištění, že se změny provedené u dat pomocí ovládacích prvků zkopírují zpátky do spravovaných objektů.

   Pro zjednodušení vývoje aplikací poskytuje WPF modul datových vazeb k automatickému provedení těchto kroků. Základní jednotkou modulu datové vazby je třída <xref:System.Windows.Data.Binding>, jejíž úkolem je vytvořit vazbu ovládacího prvku (cíl vazby) k datovému objektu (zdroj vazby). Tento vztah je znázorněný na následujícím obrázku.

   ![Základní diagram datových vazeb](../designers/media/databindingmostbasic.png "DataBindingMostBasic")

   Následující příklad ukazuje, jak vytvořit vazby <xref:System.Windows.Controls.TextBox> k instanci vlastního objektu `Person`. @No__t_0 implementace je zobrazená v následujícím kódu.

   [!code-csharp[SimpleDataBindingSnippets#PersonClassCODE](../snippets/csharp/VS_Snippets_Wpf/SimpleDataBindingSnippets/CSharp/Person.cs#personclasscode)]
   [!code-vb[SimpleDataBindingSnippets#PersonClassCODE](../snippets/visualbasic/VS_Snippets_Wpf/SimpleDataBindingSnippets/VisualBasic/Person.vb#personclasscode)]

   Následující kód váže <xref:System.Windows.Controls.TextBox> k instanci vlastního objektu `Person`.

   [!code-xml[SimpleDataBindingSnippets#DataBindingMARKUP1](../snippets/csharp/VS_Snippets_Wpf/SimpleDataBindingSnippets/CSharp/DataBindingWindow.xaml#databindingmarkup1)]
   [!code-xml[SimpleDataBindingSnippets#DataBindingMARKUP2](../snippets/csharp/VS_Snippets_Wpf/SimpleDataBindingSnippets/CSharp/DataBindingWindow.xaml#databindingmarkup2)]
   [!code-xml[SimpleDataBindingSnippets#DataBindingMARKUP3](../snippets/csharp/VS_Snippets_Wpf/SimpleDataBindingSnippets/CSharp/DataBindingWindow.xaml#databindingmarkup3)]

   [!code-csharp[SimpleDataBindingSnippets#DataBindingCODEBEHIND](../snippets/csharp/VS_Snippets_Wpf/SimpleDataBindingSnippets/CSharp/DataBindingWindow.xaml.cs#databindingcodebehind)]
   [!code-vb[SimpleDataBindingSnippets#DataBindingCODEBEHIND](../snippets/visualbasic/VS_Snippets_Wpf/SimpleDataBindingSnippets/VisualBasic/DataBindingWindow.xaml.vb#databindingcodebehind)]

   V tomto příkladu je vytvořena instance `Person` třídy v kódu na pozadí a je nastavena jako datový kontext pro `DataBindingWindow`. V kódu je vlastnost <xref:System.Windows.Controls.TextBox.Text%2A> <xref:System.Windows.Controls.TextBox> svázána s vlastností `Person.Name` (pomocí syntaxe XAML "`{Binding ... }`"). Tento kód XAML oznamuje, že má WPF navazovat ovládací prvek <xref:System.Windows.Controls.TextBox> na objekt `Person`, který je uložený v vlastnosti <xref:System.Windows.FrameworkElement.DataContext%2A> okna.

   Modul datových vazeb WPF poskytuje další podporu, která zahrnuje ověřování, řazení, filtrování a seskupování. Kromě toho datová vazba podporuje použití datových šablon k vytvoření vlastního uživatelského rozhraní pro vázaná data v případě, že uživatelské rozhraní zobrazené standardními ovládacími prvky WPF není vhodné.

   Další informace najdete v tématu [Přehled datových vazeb](https://msdn.microsoft.com/library/ms752347\(v=vs.100\).aspx).

## <a name="Graphics"></a>Prvky
 WPF přináší rozsáhlou, škálovatelnou a flexibilní sadu grafických funkcí, které mají následující výhody:

- Grafika nezávislá na **rozlišení a zařízení**. Základní jednotkou v grafickém systému WPF je pixel nezávislý na zařízení, což je 1/1/96 palce, bez ohledu na skutečné rozlišení obrazovky a poskytuje základ pro vykreslování nezávisle na rozlišení a na zařízení. Každé pixely nezávislé na zařízení se automaticky škáluje tak, aby se shodovalo s nastavením bodů na palec (dpi) systému, na kterém se vykreslí.

- **Vylepšená přesnost**. Systém souřadnic WPF se měří s čísly s plovoucí desetinnou čárkou s dvojitou přesností, nikoli s jednoduchou přesností. Transformace a hodnoty neprůhlednosti se také vyjadřují jako dvojitá přesnost. WPF také podporuje šířku barevné škály (scRGB) a poskytuje integrovanou podporu pro správu vstupů z různých barevných prostorů.

- **Pokročilá podpora grafiky a animací** WPF zjednodušuje programování grafiky tím, že vám umožní spravovat animace na pozadí. Nemusíte se starat o zpracování scény, vykreslování smyček a varianty interpolaci. Kromě toho WPF poskytuje podporu testování testů a úplnou podporu pro skládání v alfa.

- **Hardwarová akcelerace**. Grafický systém WPF využívá grafický hardware k minimalizaci využití procesoru.

### <a name="2-d-shapes"></a>2D obrazce
 WPF poskytuje knihovnu běžně nakreslených 2D tvarů, jako jsou obdélníky a tři tečky, které jsou zobrazeny na následujícím obrázku.

 ![Elipsy a obdélníky](../designers/media/wpfintrofigure4.PNG "WPFIntroFigure4")

 Zajímavou schopností tvarů je, že nejsou jenom pro zobrazení; obrazce implementují mnoho funkcí, které očekáváte od ovládacích prvků, včetně vstupu klávesnice a myši. Následující příklad ukazuje <xref:System.Windows.UIElement.MouseUp> událost <xref:System.Windows.Shapes.Ellipse> zpracovávána.

 [!code-xml[IntroToWPFSnippets#HandleEllipseMouseUpEventMARKUP](../snippets/csharp/VS_Snippets_Wpf/IntroToWPFSnippets/CSharp/EllipseEventHandlingWindow.xaml#handleellipsemouseupeventmarkup)]

 [!code-csharp[IntroToWPFSnippets#HandleEllipseMouseUpEventCODEBEHIND](../snippets/csharp/VS_Snippets_Wpf/IntroToWPFSnippets/CSharp/EllipseEventHandlingWindow.xaml.cs#handleellipsemouseupeventcodebehind)]
 [!code-vb[IntroToWPFSnippets#HandleEllipseMouseUpEventCODEBEHIND](../snippets/visualbasic/VS_Snippets_Wpf/IntroToWPFSnippets/VisualBasic/EllipseEventHandlingWindow.xaml.vb#handleellipsemouseupeventcodebehind)]

 Následující obrázek ukazuje, co je vyrobeno v předchozím kódu.

 ![Okno s textem "kliknuli jste na elipsu&#33;"](../designers/media/wpfintrofigure12.png "WPFIntroFigure12")

 Další informace naleznete v tématu [Shapes and Basic Drawing in WPF Overview](https://msdn.microsoft.com/library/ms747393\(v=vs.100\).aspx).

### <a name="2-d-geometries"></a>2D geometrií
 2D obrazce, které poskytuje WPF, se týkají standardní sady základních tvarů. Je však možné, že budete muset vytvořit vlastní tvary, aby bylo usnadněno navrhování přizpůsobeného uživatelského rozhraní. Pro účely tohoto účelu WPF poskytuje geometrií. Následující obrázek ukazuje použití geometrií k vytvoření vlastního tvaru, který lze vykreslit přímo, použít jako štětec nebo použít k Vystřižení jiných tvarů a ovládacích prvků.

 objekty <xref:System.Windows.Shapes.Path> lze použít k vykreslení uzavřených nebo otevřených tvarů, více tvarů a dokonce i zakřivených tvarů.

 <xref:System.Windows.Media.Geometry> objekty lze použít pro účely oříznutí, testování přístupů a vykreslování 2D grafických dat.

 ![Různá použití cesty](../designers/media/wpfintrofigure5.PNG "WPFIntroFigure5")

 Další informace najdete v tématu [geometrie – přehled](https://msdn.microsoft.com/library/ms751808\(v=vs.100\).aspx) .

### <a name="2-d-effects"></a>2D efekty
 Podmnožina funkcí WPF 2-D zahrnuje vizuální efekty, jako jsou barevné přechody, bitmapy, kresby, Malování s videi, otočení, škálování a zkosení. Všechny jsou dosaženy pomocí štětců; Následující obrázek ukazuje několik příkladů.

 ![Ilustrace různých štětců](../designers/media/wpfintrofigure6.PNG "WPFIntroFigure6")

 Další informace najdete v tématu [Přehled štětců WPF](https://msdn.microsoft.com/library/aa970904\(v=vs.100\).aspx).

### <a name="3-d-rendering"></a>trojrozměrné vykreslování
 WPF také obsahuje 3D možnosti vykreslování, které se integrují s 2D grafikou, aby bylo možné vytvářet zajímavější a zajímavá uživatelská rozhraní. Následující obrázek například ukazuje 2D obrázky vykreslené na 3D obrazce.

 ![Snímek obrazovky ukázka Visual3D](../designers/media/wpfintrofigure13.png "WPFIntroFigure13")

 Další informace najdete v tématu [Přehled 3D grafiky](https://msdn.microsoft.com/library/ms747437\(v=vs.100\).aspx).

## <a name="Animation"></a>Animaci
 Podpora animace WPF umožňuje řídit, protřepání, otočení a zmizení ovládacích prvků, aby bylo možné vytvářet zajímavé přechody stránky a další. Můžete animovat většinu tříd WPF, dokonce i vlastní třídy. Na následujícím obrázku je znázorněna jednoduchá animace v akci.

 ![Obrázky animované datové krychle](../designers/media/wpfintrofigure7.png "WPFIntroFigure7")

 Další informace najdete v tématu [Přehled animací](https://msdn.microsoft.com/library/ms752312\(v=vs.100\).aspx).

## <a name="Media"></a>Média
 Jedním ze způsobů, jak vyjádřit bohatou část obsahu, je použití audiovizuálních médií. WPF poskytuje speciální podporu pro obrázky, video a zvuk.

### <a name="images"></a>Obrázky
 Obrázky jsou společné pro většinu aplikací a WPF nabízí několik způsobů jejich použití. Následující obrázek ukazuje uživatelské rozhraní se seznamem, které obsahuje miniatury obrázků. Když je vybraná Miniatura, zobrazí se obrázek v plné velikosti.

 ![Obrázky miniatur a obrázek plné&#45;velikosti](../designers/media/wpfintrofigure8.PNG "WPFIntroFigure8")

 Další informace najdete v tématu [Přehled imagí](https://msdn.microsoft.com/library/ms748873\(v=vs.100\).aspx).

### <a name="video-and-audio"></a>Video a zvuk
 Ovládací prvek <xref:System.Windows.Controls.MediaElement> může přehrávat video i zvuk a je dostatečně flexibilní, aby byl základem pro vlastní přehrávač médií. Následující kód XAML implementuje přehrávač médií.

 [!code-xml[IntroToWPFSnippets#MediaElementMARKUP](../snippets/csharp/VS_Snippets_Wpf/IntroToWPFSnippets/CSharp/MediaElementWindow.xaml#mediaelementmarkup)]

 Okno na následujícím obrázku ukazuje <xref:System.Windows.Controls.MediaElement> ovládacího prvku v akci.

 ![Ovládací prvek MediaElement se zvukem a videem](../designers/media/wpfintrofigure1.png "WPFIntroFigure1")

 Další informace najdete v tématu [Přehled grafiky, animací a multimédií pro WPF](https://msdn.microsoft.com/library/ms742562\(v=vs.100\).aspx).

## <a name="Text_and_Typography"></a>Text a typografie
 Pro usnadnění vysoce kvalitního vykreslování textu nabízí WPF tyto funkce:

- Podpora písma OpenType.

- Vylepšení technologie ClearType.

- Vysoký výkon, který využívá hardwarovou akceleraci.

- Integrace textu s médii, grafikou a animací

- Mezinárodní podpora písem a nouzové mechanismy.

  Jako ukázku integrace textu s grafikou ukazuje následující obrázek použití dekorace textu.

  ![Text s různými dekoracemi textu](../designers/media/wpfintrofigure23.png "WPFIntroFigure23")

  Další informace najdete v tématu [Typografie v Windows Presentation Foundation](https://msdn.microsoft.com/library/ms742190\(v=vs.100\).aspx).

## <a name="WPF_Customization"></a>Přizpůsobení aplikací WPF
 Až do tohoto okamžiku jste viděli základní stavební bloky WPF pro vývoj aplikací. Model aplikace použijete k hostování a dodávání obsahu aplikace, který se skládá hlavně z ovládacích prvků. Chcete-li zjednodušit uspořádání ovládacích prvků v uživatelském rozhraní a zajistit, aby bylo uspořádání udržováno v tvář změny velikosti okna a nastavení zobrazení, použijte systém rozložení WPF. Vzhledem k tomu, že většina aplikací umožňuje uživatelům pracovat s daty, můžete použít datovou vazbu k omezení práce s daty v integraci uživatelského rozhraní. Chcete-li zlepšit vizuální vzhled aplikace, použijte komplexní škálu grafiky, animace a podpory médií, které poskytuje WPF.

 Většinou ale nemusíte vytvářet a spravovat skutečně odlišná a vizuálně působivé uživatelské prostředí. Standardní ovládací prvky WPF se nemusí integrovat s požadovaným vzhledem vaší aplikace. Data se nemusí zobrazovat v nejúčinnějším způsobu. Celkové uživatelské prostředí vaší aplikace nemusí být vhodné pro výchozí vzhled a chování motivů systému Windows. V mnoha způsobech prezentace potřebuje vizuální rozšiřitelnost, a to podobně jako jakýkoli jiný druh rozšiřitelnosti.

 Z tohoto důvodu WPF poskytuje řadu mechanismů pro vytváření jedinečných uživatelských prostředí, včetně modelu bohatých obsahu pro ovládací prvky, triggery, ovládací prvky a šablony dat, styly, prostředky uživatelského rozhraní a motivy a vzhledy.

### <a name="content-model"></a>Model obsahu
 Hlavním účelem většiny ovládacích prvků WPF je zobrazení obsahu. V WPF je typ a počet položek, které mohou být obsahem ovládacího prvku, označovány jako *model obsahu*ovládacího prvku. Některé ovládací prvky mohou obsahovat jednu položku a typ obsahu; například obsah <xref:System.Windows.Controls.TextBox> je řetězcová hodnota, která je přiřazena vlastnosti <xref:System.Windows.Controls.TextBox.Text%2A>. Následující příklad nastaví obsah <xref:System.Windows.Controls.TextBox>.

 [!code-xml[IntroToWPFSnippets#TextBoxContentMARKUP1](../snippets/csharp/VS_Snippets_Wpf/IntroToWPFSnippets/CSharp/TextBoxContentWindow.xaml#textboxcontentmarkup1)]
[!code-xml[IntroToWPFSnippets#TextBoxContentMARKUP2](../snippets/csharp/VS_Snippets_Wpf/IntroToWPFSnippets/CSharp/TextBoxContentWindow.xaml#textboxcontentmarkup2)]
[!code-xml[IntroToWPFSnippets#TextBoxContentMARKUP3](../snippets/csharp/VS_Snippets_Wpf/IntroToWPFSnippets/CSharp/TextBoxContentWindow.xaml#textboxcontentmarkup3)]

 Výsledek je znázorněn na následujícím obrázku.

 ![Ovládací prvek TextBox, který obsahuje text](../designers/media/wpfintrofigure21.png "WPFIntroFigure21")

 Jiné ovládací prvky však mohou obsahovat více položek různých typů obsahu; obsah <xref:System.Windows.Controls.Button> určený vlastností <xref:System.Windows.Controls.ContentControl.Content%2A> může obsahovat různé položky, včetně ovládacích prvků rozložení, textu, obrázků a tvarů. Následující příklad ukazuje <xref:System.Windows.Controls.Button> s obsahem, který obsahuje <xref:System.Windows.Controls.DockPanel>, <xref:System.Windows.Controls.Label>, <xref:System.Windows.Controls.Border> a <xref:System.Windows.Controls.MediaElement>.

 [!code-xml[IntroToWPFSnippets#ButtonContentMARKUP1](../snippets/csharp/VS_Snippets_Wpf/IntroToWPFSnippets/CSharp/ButtonContentWindow.xaml#buttoncontentmarkup1)]
[!code-xml[IntroToWPFSnippets#ButtonContentMARKUP2](../snippets/csharp/VS_Snippets_Wpf/IntroToWPFSnippets/CSharp/ButtonContentWindow.xaml#buttoncontentmarkup2)]
[!code-xml[IntroToWPFSnippets#ButtonContentMARKUP3](../snippets/csharp/VS_Snippets_Wpf/IntroToWPFSnippets/CSharp/ButtonContentWindow.xaml#buttoncontentmarkup3)]

 Následující obrázek ukazuje obsah tohoto tlačítka.

 ![Tlačítko, které obsahuje více typů obsahu](../designers/media/wpfintrofigure22.png "WPFIntroFigure22")

 Další informace o typech obsahu, které jsou podporovány různými ovládacími prvky, naleznete v tématu [model obsahu WPF](https://msdn.microsoft.com/library/bb613548\(v=vs.100\).aspx).

### <a name="triggers"></a>Aktivační procedury
 I když hlavní účel kódu XAML je implementovat vzhled aplikace, můžete také použít XAML k implementaci některých aspektů chování aplikace. Jedním z příkladů je použití triggerů ke změně vzhledu aplikace na základě interakcí uživatelů. Další informace najdete v tématu [stylování a šablonování](https://msdn.microsoft.com/library/ms745683\(v=vs.100\).aspx).

### <a name="control-templates"></a>Šablony ovládacích prvků
 Výchozí uživatelská rozhraní pro ovládací prvky WPF jsou obvykle vytvořena z jiných ovládacích prvků a tvarů. Například <xref:System.Windows.Controls.Button> se skládá z ovládacích prvků <xref:Microsoft.Windows.Themes.ButtonChrome> a <xref:System.Windows.Controls.ContentPresenter>. @No__t_0 poskytuje standardní vzhled tlačítka, zatímco <xref:System.Windows.Controls.ContentPresenter> zobrazuje obsah tlačítka, jak je určeno vlastností <xref:System.Windows.Controls.ContentControl.Content%2A>.

 Někdy se může stát, že výchozí vzhled ovládacího prvku bude incongruent s celkovým vzhledem aplikace. V takovém případě můžete použít <xref:System.Windows.Controls.ControlTemplate> ke změně vzhledu uživatelského rozhraní ovládacího prvku, aniž byste museli měnit jeho obsah a chování.

 Například následující příklad ukazuje, jak změnit vzhled <xref:System.Windows.Controls.Button> pomocí <xref:System.Windows.Controls.ControlTemplate>.

 [!code-xml[IntroToWPFSnippets#ButtonControlTemplateWindowMARKUP](../snippets/csharp/VS_Snippets_Wpf/IntroToWPFSnippets/CSharp/ControlTemplateButtonWindow.xaml#buttoncontroltemplatewindowmarkup)]

 [!code-csharp[IntroToWPFSnippets#ButtonControlTemplateWindowCODEBEHIND](../snippets/csharp/VS_Snippets_Wpf/IntroToWPFSnippets/CSharp/ControlTemplateButtonWindow.xaml.cs#buttoncontroltemplatewindowcodebehind)]
 [!code-vb[IntroToWPFSnippets#ButtonControlTemplateWindowCODEBEHIND](../snippets/visualbasic/VS_Snippets_Wpf/IntroToWPFSnippets/VisualBasic/ControlTemplateButtonWindow.xaml.vb#buttoncontroltemplatewindowcodebehind)]

 V tomto příkladu bylo tlačítko výchozí uživatelské rozhraní nahrazeno <xref:System.Windows.Shapes.Ellipse>, které má tmavě modré ohraničení a je vyplněno pomocí <xref:System.Windows.Media.RadialGradientBrush>. Ovládací prvek <xref:System.Windows.Controls.ContentPresenter> zobrazí obsah <xref:System.Windows.Controls.Button> "klikněte na mě!". Při kliknutí na <xref:System.Windows.Controls.Button> je událost <xref:System.Windows.Controls.Primitives.ButtonBase.Click> stále vyvolána jako součást výchozího chování ovládacího prvku <xref:System.Windows.Controls.Button>. Výsledek je znázorněn na následujícím obrázku.

 ![Eliptické tlačítko a druhé okno](../designers/media/wpfintrofigure2.png "WPFIntroFigure2")

### <a name="data-templates"></a>Šablony dat
 Zatímco šablona ovládacího prvku umožňuje určit vzhled ovládacího prvku, šablona data umožňuje určit vzhled obsahu ovládacího prvku. Šablony dat se často používají k vylepšení způsobu zobrazení vázaných dat. Následující obrázek ukazuje výchozí vzhled pro <xref:System.Windows.Controls.ListBox>, která je svázána s kolekcí objektů `Task`, kde každá úloha má název, popis a prioritu.

 ![Rozevírací seznam s výchozím vzhledem](../designers/media/wpfintrofigure18.png "WPFIntroFigure18")

 Výchozí vzhled je to, co byste očekávali od <xref:System.Windows.Controls.ListBox>. Výchozí vzhled jednotlivých úloh však obsahuje pouze název úlohy. Chcete-li zobrazit název, popis a prioritu úkolu, musí být výchozí vzhled položek vázaného seznamu ovládacího prvku <xref:System.Windows.Controls.ListBox> změněn pomocí <xref:System.Windows.DataTemplate>. Následující kód XAML definuje takový <xref:System.Windows.DataTemplate>, který je použit pro každý úkol pomocí atributu <xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A>.

 [!code-xml[IntroToWPFSnippets#DataTemplateMARKUP1](../snippets/csharp/VS_Snippets_Wpf/IntroToWPFSnippets/CSharp/DataTemplateWindow.xaml#datatemplatemarkup1)]
[!code-xml[IntroToWPFSnippets#DataTemplateMARKUP2](../snippets/csharp/VS_Snippets_Wpf/IntroToWPFSnippets/CSharp/DataTemplateWindow.xaml#datatemplatemarkup2)]
[!code-xml[IntroToWPFSnippets#DataTemplateMARKUP3](../snippets/csharp/VS_Snippets_Wpf/IntroToWPFSnippets/CSharp/DataTemplateWindow.xaml#datatemplatemarkup3)]
[!code-xml[IntroToWPFSnippets#DataTemplateMARKUP4](../snippets/csharp/VS_Snippets_Wpf/IntroToWPFSnippets/CSharp/DataTemplateWindow.xaml#datatemplatemarkup4)]

 Následující obrázek ukazuje účinek tohoto kódu.

 ![Seznamy pole, které používá šablonu dat](../designers/media/wpfintrofigure19.png "WPFIntroFigure19")

 Všimněte si, že <xref:System.Windows.Controls.ListBox> zachovala chování a celkový vzhled; změnil se pouze vzhled obsahu zobrazeného v poli se seznamem.

 Další informace najdete v tématu [Přehled šablonování dat](https://msdn.microsoft.com/library/ms742521\(v=vs.100\).aspx).

### <a name="styles"></a>Styly
 Styly umožňují vývojářům a návrhářům standardizovat konkrétní vzhled pro svůj produkt. WPF poskytuje model silného stylu, který je základem prvku <xref:System.Windows.Style>. Následující příklad vytvoří styl, který nastaví barvu pozadí pro každé <xref:System.Windows.Controls.Button> okna na `Orange`.

 [!code-xml[IntroToWPFSnippets#StyleMARKUP1](../snippets/csharp/VS_Snippets_Wpf/IntroToWPFSnippets/CSharp/StyleWindow.xaml#stylemarkup1)]
[!code-xml[IntroToWPFSnippets#StyleMARKUP2](../snippets/csharp/VS_Snippets_Wpf/IntroToWPFSnippets/CSharp/StyleWindow.xaml#stylemarkup2)]
[!code-xml[IntroToWPFSnippets#StyleMARKUP3](../snippets/csharp/VS_Snippets_Wpf/IntroToWPFSnippets/CSharp/StyleWindow.xaml#stylemarkup3)]
[!code-xml[IntroToWPFSnippets#StyleMARKUP4](../snippets/csharp/VS_Snippets_Wpf/IntroToWPFSnippets/CSharp/StyleWindow.xaml#stylemarkup4)]

 Vzhledem k tomu, že tento styl cílí na všechny <xref:System.Windows.Controls.Button> ovládací prvky, styl je automaticky použit pro všechna tlačítka v okně, jak je znázorněno na následujícím obrázku.

 ![Dvě oranžová tlačítka](../designers/media/wpfintrofigure20.png "WPFIntroFigure20")

 Další informace najdete v tématu [stylování a šablonování](https://msdn.microsoft.com/library/ms745683\(v=vs.100\).aspx).

### <a name="resources"></a>Prostředky
 Ovládací prvky v aplikaci by měly sdílet stejný vzhled, který může obsahovat cokoli z písma a barev pozadí pro řízení šablon, šablon dat a stylů. Můžete použít podporu WPF pro prostředky uživatelského rozhraní k zapouzdření těchto prostředků v jednom umístění pro opakované použití.

 Následující příklad definuje společnou barvu pozadí, která je sdílena <xref:System.Windows.Controls.Button> a <xref:System.Windows.Controls.Label>.

 [!code-xml[IntroToWPFSnippets#ResourceWindowMARKUP1](../snippets/csharp/VS_Snippets_Wpf/IntroToWPFSnippets/CSharp/ResourcesWindow.xaml#resourcewindowmarkup1)]
[!code-xml[IntroToWPFSnippets#ResourceWindowMARKUP2](../snippets/csharp/VS_Snippets_Wpf/IntroToWPFSnippets/CSharp/ResourcesWindow.xaml#resourcewindowmarkup2)]
[!code-xml[IntroToWPFSnippets#ResourceWindowMARKUP3](../snippets/csharp/VS_Snippets_Wpf/IntroToWPFSnippets/CSharp/ResourcesWindow.xaml#resourcewindowmarkup3)]

 Tento příklad implementuje zdroj barvy pozadí pomocí elementu vlastnosti `Window.Resources`. Tento prostředek je k dispozici všem podřízeným objektům <xref:System.Windows.Window>. Existují různé obory prostředků, včetně následujících, v pořadí, ve kterém jsou vyřešeny:

1. Individuální ovládací prvek (pomocí zděděné vlastnosti <xref:System.Windows.FrameworkElement.Resources%2A?displayProperty=fullName>).

2. @No__t_0 nebo <xref:System.Windows.Controls.Page> (používá se také zděděná vlastnost <xref:System.Windows.FrameworkElement.Resources%2A?displayProperty=fullName>).

3. @No__t_0 (pomocí vlastnosti <xref:System.Windows.Application.Resources%2A?displayProperty=fullName>).

   Různé obory vám umožňují flexibilitu v závislosti na způsobu, jakým definujete a sdílíte své prostředky.

   Jako alternativu k přímému přidružení prostředků k určitému oboru můžete jeden nebo víc prostředků zabalit pomocí samostatné <xref:System.Windows.ResourceDictionary>, na kterou se dá odkazovat v jiných částech aplikace. Například následující příklad definuje výchozí barvu pozadí ve slovníku prostředků.

   [!code-xml[IntroToWPFSnippets#ResourceDictionaryMARKUP1](../snippets/csharp/VS_Snippets_Wpf/IntroToWPFSnippets/CSharp/BackgroundColorResources.xaml#resourcedictionarymarkup1)]
   [!code-xml[IntroToWPFSnippets#ResourceDictionaryMARKUP2](../snippets/csharp/VS_Snippets_Wpf/IntroToWPFSnippets/CSharp/BackgroundColorResources.xaml#resourcedictionarymarkup2)]

   Následující příklad odkazuje na slovník prostředků definovaný v předchozím příkladu tak, aby byl sdílen napříč aplikací.

   [!code-xml[IntroToWPFSnippets#ApplicationScopedResourceDictionaryMARKUP1](../snippets/csharp/VS_Snippets_Wpf/IntroToWPFSnippets/CSharp/App.xaml#applicationscopedresourcedictionarymarkup1)]
   [!code-xml[IntroToWPFSnippets#ApplicationScopedResourceDictionaryMARKUP2](../snippets/csharp/VS_Snippets_Wpf/IntroToWPFSnippets/CSharp/App.xaml#applicationscopedresourcedictionarymarkup2)]

   Prostředky a slovníky prostředků jsou základem podpory WPF pro motivy a vzhledy.

   Další informace najdete v tématu [Přehled prostředků](https://msdn.microsoft.com/library/ms750613\(v=vs.100\).aspx).

### <a name="custom-controls"></a>Vlastní ovládací prvky
 I když WPF poskytuje hostitele podpory přizpůsobení, může dojít k situacím, kdy existující ovládací prvky WPF nesplňují požadavky vaší aplikace nebo jejích uživatelů. K tomu může dojít v těchto případech:

- Uživatelské rozhraní, které požadujete, nelze vytvořit přizpůsobením vzhledu a chování stávajících implementací WPF.

- Požadované chování není podporováno (nebo není podporováno) stávajícími implementacemi WPF.

  V tuto chvíli ale můžete využít jeden ze tří modelů WPF pro vytvoření nového ovládacího prvku. Každý model cílí na konkrétní scénář a vyžaduje, aby váš vlastní ovládací prvek byl odvozen z konkrétní základní třídy WPF. Tady jsou uvedené tři modely:

- **Model uživatelského ovládacího prvku**. Vlastní ovládací prvek je odvozen z <xref:System.Windows.Controls.UserControl> a skládá se z jednoho nebo více dalších ovládacích prvků.

- **Model ovládacího prvku**. Vlastní ovládací prvek je odvozen z <xref:System.Windows.Controls.Control> a slouží k sestavování implementací, které oddělují své chování od jejich vzhledu pomocí šablon, podobně jako většina ovládacích prvků WPF. Odvození z <xref:System.Windows.Controls.Control> vám umožňuje větší volnost při vytváření vlastního uživatelského rozhraní než uživatelských ovládacích prvků, ale může to vyžadovat více úsilí.

- **Model elementu rozhraní**. Vlastní ovládací prvek je odvozen z <xref:System.Windows.FrameworkElement>, pokud je jeho vzhled definován pomocí vlastní logiky vykreslování (nikoli šablon).

  Následující příklad ukazuje vlastní číselnou kontrolu nahoru/dolů, která je odvozena od <xref:System.Windows.Controls.UserControl>.

  [!code-xml[IntroToWPFSnippets#UserControlMARKUP](../snippets/csharp/VS_Snippets_Wpf/IntroToWPFSnippets/CSharp/NumericUpDown.xaml#usercontrolmarkup)]

  [!code-csharp[IntroToWPFSnippets#UserControlCODEBEHIND1](../snippets/csharp/VS_Snippets_Wpf/IntroToWPFSnippets/CSharp/NumericUpDown.xaml.cs#usercontrolcodebehind1)]
  [!code-vb[IntroToWPFSnippets#UserControlCODEBEHIND1](../snippets/visualbasic/VS_Snippets_Wpf/IntroToWPFSnippets/VisualBasic/NumericUpDown.xaml.vb#usercontrolcodebehind1)]
  [!code-csharp[IntroToWPFSnippets#UserControlCODEBEHIND2](../snippets/csharp/VS_Snippets_Wpf/IntroToWPFSnippets/CSharp/NumericUpDown.xaml.cs#usercontrolcodebehind2)]
  [!code-vb[IntroToWPFSnippets#UserControlCODEBEHIND2](../snippets/visualbasic/VS_Snippets_Wpf/IntroToWPFSnippets/VisualBasic/NumericUpDown.xaml.vb#usercontrolcodebehind2)]

 Následující příklad ilustruje kód XAML, který je požadován pro zahrnutí uživatelského ovládacího prvku do <xref:System.Windows.Window>.

 [!code-xml[IntroToWPFSnippets#UserControlWindowMARKUP1](../snippets/csharp/VS_Snippets_Wpf/IntroToWPFSnippets/CSharp/UserControlWindow.xaml#usercontrolwindowmarkup1)]
[!code-xml[IntroToWPFSnippets#UserControlWindowMARKUP2](../snippets/csharp/VS_Snippets_Wpf/IntroToWPFSnippets/CSharp/UserControlWindow.xaml#usercontrolwindowmarkup2)]
[!code-xml[IntroToWPFSnippets#UserControlWindowMARKUP3](../snippets/csharp/VS_Snippets_Wpf/IntroToWPFSnippets/CSharp/UserControlWindow.xaml#usercontrolwindowmarkup3)]

 Následující obrázek znázorňuje ovládací prvek `NumericUpDown` hostovaný ve <xref:System.Windows.Window>.

 ![Vlastní UserControl](../designers/media/wpfintrofigure3.png "WPFIntroFigure3")

 Další informace o vlastních ovládacích prvcích najdete v tématu [Přehled vytváření ovládacích](https://msdn.microsoft.com/library/ms745025\(v=vs.100\).aspx)prvků.

## <a name="WPF_Best_Practices"></a>Osvědčené postupy pro WPF
 Stejně jako u jakékoli vývojové platformy je možné WPF použít různými způsoby, abyste dosáhli požadovaného výsledku. Jako způsob, jak zajistit, aby vaše aplikace WPF poskytovaly požadované uživatelské prostředí a splňovaly požadavky cílové skupiny obecně, existují Doporučené osvědčené postupy pro přístupnost, globalizaci a lokalizaci a výkon. Další informace najdete v následujících tématech:

- [Osvědčené postupy pro usnadnění](https://msdn.microsoft.com/library/aa350483\(v=vs.100\).aspx) Osvědčené postupy pro usnadnění

- [Přehled globalizace a lokalizace WPF](https://msdn.microsoft.com/library/ms788718\(v=vs.100\).aspx)

- [Optimalizace výkonu aplikace WPF](https://msdn.microsoft.com/library/aa970683\(v=vs.100\).aspx)

- [Windows Presentation Foundation zabezpečení](https://msdn.microsoft.com/library/aa970906\(v=vs.100\).aspx)

## <a name="Summary"></a>Shrnut
 WPF je komplexní prezentační technologie pro vytváření široké škály vizuálně působivých klientských aplikací. V tomto úvodu najdete klíčové funkce WPF.

 Dalším krokem je sestavování aplikací WPF!

 Když je sestavíte, můžete se vrátit k tomuto úvodu pro aktualizační program na klíčových funkcích a vyhledat odkazy na podrobnější pokrytí funkcí popsaných v tomto úvodu.

## <a name="see-also"></a>Viz také
 [Začínáme s WPF](../designers/getting-started-with-wpf.md) [Vytvářejte moderní desktopové aplikace pomocí Windows Presentation Foundation](../designers/create-modern-desktop-applications-with-windows-presentation-foundation.md) [Windows Presentation Foundation](https://msdn.microsoft.com/library/ms754130\(v=vs.100\).aspx)
