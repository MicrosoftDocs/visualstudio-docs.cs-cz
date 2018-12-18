---
title: 'Návod: Moje první WPF plochy Application2 | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3c460fa9-2ea1-413f-ae54-54a1f2a499d1
caps.latest.revision: 8
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 7d8af02051774b744f9229e15a6184603c4d9f6b
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49899276"
---
# <a name="walkthrough-my-first-wpf-desktop-application"></a>Návod: Moje první Desktopová aplikace WPF
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

name = "Úvod" ></a> Tento názorný postup obsahuje úvod do vývoje Windows Presentation Foundation (WPF). Vytvoříte základní aplikaci, která obsahuje elementy, které jsou společné pro většinu aplikací klasické pracovní plochy WPF: XAML značky, použití modelu code-behind, definice aplikací, ovládací prvky, rozložení, datové vazby a styly.  
  
##  <a name="Create_The_Application_Code_Files"></a> Vytvoření projektu aplikace  
 V této části vytvoříte aplikační infrastruktury, které obsahuje projekt a hlavního okna nebo formuláře.  
  
#### <a name="to-create-the-project"></a>Vytvoření projektu  
  
1.  V panelu nabídky zvolte **souboru**, **nový**, **projektu**.  
  
2.  V **nový projekt** dialogového okna, rozbalte buď **Visual C#** nebo **jazyka Visual Basic** uzlu a zvolte **Windows** uzel a potom rozbalte **Windows** uzlu a zvolte **klasický desktopový** uzlu.  
  
3.  V seznamu šablon vyberte **aplikace WPF** šablony.  
  
4.  V **název** textového pole zadejte `ExpenseIt`a klikněte na tlačítko **OK** tlačítko.  
  
     Vytvoření projektu a soubory projektu jsou přidány do **Průzkumníka řešení**a otevře se návrhář pro výchozí okno aplikace s názvem **souboru MainWindow.xaml** se zobrazí.  
  
#### <a name="to-modify-the-main-window"></a>Chcete-li změnit hlavní okno  
  
1.  V návrháři, zvolte **souboru MainWindow.xaml** kartu, pokud ještě není aktivní kartu návrháře.  
  
2.  Pokud používáte C#, vyhledejte řádek `<Window x:Class="ExpenseIt.MainWindow"` a nahraďte ho hodnotou `<NavigationWindow x:Class="ExpenseIt.MainWindow"`.  
  
     Pokud používáte jazyk Visual Basic, vyhledejte řádek `<Window x:Class=" MainWindow"` a nahraďte ho hodnotou `<NavigationWindow x:Class="MainWindow"`.  
  
     Všimněte si, že když změníte `<Window` značku na `<NavigationWindow`, technologie Intellisense automaticky změní uzavírací značku `</NavigationWindow>` také.  
  
    > [!NOTE]
    >  Po změně značky, pokud **seznam chyb** je otevřeno okno může dojít k několika chybám. Nedělejte si starosti, budou změny provedené v dalších několika krocích tyto go okamžitě.  
  
3.  Zvolte `<Grid>` a `</Grid>` značky a odstranit je.  
  
     A **objektu NavigationWindow** nemůže obsahovat další prvky uživatelského rozhraní, jako **mřížky**.  
  
4.  V **vlastnosti** okna, rozbalte **běžné** kategorie uzlu a zvolte **název** vlastnost a pak zadejte `ExpenseIt` a stiskněte klávesu **Enter**  klíč.  
  
     Všimněte si, že **Title** prvku v XAML okno změní tak, aby odpovídala nové hodnoty. Můžete upravit vlastnosti XAML v okně XAML nebo **vlastnosti** okno a změny se synchronizují.  
  
5.  V okně XAML, nastavte hodnotu **výška** elementu `375`a nastavte hodnotu **šířka** vlastnost `500`.  
  
     Tyto prvky odpovídají **výška** a **šířka** vlastnosti nalezené v **rozložení** kategorii **vlastnosti** okna.  
  
     Vaše **souboru MainWindow.xaml** soubor by teď měl vypadat takto v jazyce C#:  
  
    ```xaml  
    <NavigationWindow x:Class="ExpenseIt.MainWindow"  
            xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"  
            xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"  
            xmlns:d="http://schemas.microsoft.com/expression/blend/2008"  
            xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"  
            xmlns:local="clr-namespace:ExpenseIt"  
            mc:Ignorable="d"  
            Title="ExpenseIt" Height="375" Width="500">  
  
    </NavigationWindow>  
    ```  
  
     Nebo takto v jazyce Visual Basic:  
  
    ```xaml  
    <NavigationWindow x:Class="MainWindow"  
            xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"  
            xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"  
            xmlns:d="http://schemas.microsoft.com/expression/blend/2008"  
            xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"  
            xmlns:local="clr-namespace:ExpenseIt"  
            mc:Ignorable="d"  
            Title="ExpenseIt" Height="375" Width="500">  
  
    </NavigationWindow>  
    ```  
  
#### <a name="to-modify-the-code-behind-file-c"></a>Úprava souboru kódu na pozadí (C#)  
  
1.  V **Průzkumníku řešení**, rozbalte **souboru MainWindow.xaml** uzlu a otevřít **MainWindow.xaml.cs** souboru.  
  
2.  Vyhledejte řádek `public partial class MainWindow : Window` a nahraďte ho hodnotou `public partial class MainWindow : NavigationWindow`.  
  
     Tím se změní `MainWindow` třídy odvozovat z `NavigationWindow`. V jazyce Visual Basic tomu automaticky dojde při změně okna v XAML, takže nejsou nutné žádné změny kódu.  
  
##  <a name="add_files_to_the_application"></a> Přidávání souborů do aplikace  
 V této části přidáte dvě stránky a obrázku do aplikace.  
  
#### <a name="to-add-a-home-screen"></a>Chcete-li přidat domovské obrazovky  
  
1.  V **Průzkumníka řešení**, otevřete místní nabídku **ExpenseIt –** uzlu a zvolte **přidat**, **stránky**.  
  
2.  V **přidat novou položku** dialogového okna, vyberte **název** textové pole a zadejte `ExpenseItHome`a klikněte na tlačítko **přidat** tlačítko.  
  
     Tato stránka je první okno, které se zobrazí při spuštění aplikace.  
  
3.  V návrháři, zvolte **ExpenseItHome.xaml** kartu, pokud ještě není aktivní kartu návrháře.  
  
4.  Zvolte `<Title>` prvku a změňte nadpis na **ExpenseIt – – Domů**.  
  
     Vaše **ExpenseItHome.xaml** soubor by teď měl vypadat takto v jazyce C#:  
  
    ```xaml  
    <Page x:Class="ExpenseIt.ExpenseItHome"  
          xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"  
          xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"  
          xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"   
          xmlns:d="http://schemas.microsoft.com/expression/blend/2008"   
          xmlns:local="clr-namespace:ExpenseIt"  
          mc:Ignorable="d"   
          d:DesignHeight="300" d:DesignWidth="300"  
          Title="ExpenseIt - Home">  
  
        <Grid>  
  
        </Grid>  
    </Page>  
    ```  
  
     Nebo takto v jazyce Visual Basic:  
  
    ```xaml  
    <Page x:Class="ExpenseItHome"  
          xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"  
          xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"  
          xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"   
          xmlns:d="http://schemas.microsoft.com/expression/blend/2008"   
          xmlns:local="clr-namespace:ExpenseIt"  
          mc:Ignorable="d"   
          d:DesignHeight="300" d:DesignWidth="300"  
          Title="ExpenseIt - Home">  
        <Grid>  
  
        </Grid>  
    </Page>  
    ```  
  
5.  V návrháři, zvolte **souboru MainWindow.xaml** kartu.  
  
6.  Vyhledejte řádek `Title="ExpenseIt" Height="375" Width="500">` prvek a přidat `Source="ExpenseItHome.xaml"` vlastnost.  
  
     Tím se nastaví **ExpenseItHome.xaml** bude první stránka otevře při spuštění aplikace. Vaše **souboru MainWindow.xaml** soubor by teď měl vypadat takto v jazyce C#:  
  
    ```xaml  
    <NavigationWindow x:Class="ExpenseIt.MainWindow"  
            xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"  
            xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"  
            xmlns:d="http://schemas.microsoft.com/expression/blend/2008"  
            xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"  
            xmlns:local="clr-namespace:ExpenseIt"  
            mc:Ignorable="d"  
            Title="ExpenseIt" Height="375" Width="500" Source="ExpenseItHome.xaml">  
  
    </NavigationWindow>  
    ```  
  
     Nebo takto v jazyce Visual Basic:  
  
    ```xaml  
    <NavigationWindow x:Class="MainWindow"  
            xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"  
            xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"  
            xmlns:d="http://schemas.microsoft.com/expression/blend/2008"  
            xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"  
            xmlns:local="clr-namespace:ExpenseIt"  
            mc:Ignorable="d"  
            Title="ExpenseIt" Height="375" Width="500" Source="ExpenseItHome.xaml">  
  
    </NavigationWindow>  
    ```  
  
     Jako s vlastnostmi, které jste nastavili dříve, mohli jste nastavili `Source` vlastnost **různé** kategorii **vlastnosti** okna.  
  
#### <a name="to-add-a-details-window"></a>Chcete-li přidat okno podrobností  
  
1.  V **Průzkumníka řešení**, otevřete místní nabídku **ExpenseIt –** uzlu a zvolte **přidat**, **stránky**.  
  
2.  V **přidat novou položku** dialogového okna, vyberte **název** textové pole a zadejte `ExpenseReportPage`a klikněte na tlačítko **přidat** tlačítko.  
  
     Toto okno se zobrazí jednotlivých vyúčtování.  
  
3.  V návrháři, zvolte **ExpenseReportPage.xaml** kartu, pokud ještě není aktivní kartu návrháře.  
  
4.  Zvolte `<Title>` prvku a změňte nadpis na **ExpenseIt – – zobrazení výdajů**.  
  
     Váš soubor ExpenseReportPage.xaml by měl nyní vypadat nějak takto v jazyce C#:  
  
    ```xaml  
    <Page x:Class="ExpenseIt.ExpenseReportPage"  
          xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"  
          xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"  
          xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"   
          xmlns:d="http://schemas.microsoft.com/expression/blend/2008"   
          xmlns:local="clr-namespace:ExpenseIt"  
          mc:Ignorable="d"   
          d:DesignHeight="300" d:DesignWidth="300"  
          Title="ExpenseIt - View Expense">  
  
        <Grid>  
  
        </Grid>  
    </Page>  
    ```  
  
     Nebo takto v jazyce Visual Basic:  
  
    ```xaml  
    <Page x:Class="ExpenseReportPage"  
          xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"  
          xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"  
          xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"   
          xmlns:d="http://schemas.microsoft.com/expression/blend/2008"   
          xmlns:local="clr-namespace:ExpenseIt"  
          mc:Ignorable="d"   
          d:DesignHeight="300" d:DesignWidth="300"  
          Title="ExpenseIt - View Expense">  
        <Grid>  
  
        </Grid>  
    </Page>  
    ```  
  
5.  V panelu nabídky zvolte **ladění**, **spustit ladění** (nebo stiskněte klávesu F5) spusťte aplikaci.  
  
     Následující obrázek znázorňuje aplikaci okno navigačních tlačítek.  
  
     ![Snímek obrazovky ukázkové ExpenseIt –](../designers/media/gettingstartedfigure1.png "GettingStartedFigure1")  
  
6.  Ukončete aplikaci chcete vrátit do režimu návrhu.  
  
##  <a name="Add_Layout"></a> Vytvoření uživatelského rozhraní  
 Rozložení poskytuje seřazený umožňuje umístit prvky a také spravuje velikost a umístění těchto prvků při změně velikosti formuláře. V této části vytvoříte Jednosloupcové tabulky se třemi řádky. Budete přidání ovládacích prvků do dvou stránkách, přidání kódu a nakonec definujte opakovaně použitelné styly pro ovládací prvky.  
  
#### <a name="to-create-the-layout"></a>Chcete-li vytvořit rozložení  
  
1.  Otevřít **ExpenseItHome.xaml** a zvolte `<Grid>` elementu.  
  
2.  V **vlastnosti** okna, rozbalte **rozložení** kategorie uzlu a nastavte **okraj** hodnoty `10`, `10`, `0`a `10`, která odpovídá levé, pravé, horní a dolní okraj.  
  
     Element `Margin="10,0,10,10"` se přidá do `<Grid>` prvek XAML. Zase může zadáte tyto hodnoty přímo v kódu XAML v místo **vlastnosti** okno s stejný výsledek.  
  
3.  Přidejte následující kód XAML, který `Grid` prvku k vytvoření definice řádků a sloupců:  
  
    ```xaml  
    <Grid.ColumnDefinitions>  
        <ColumnDefinition />  
    </Grid.ColumnDefinitions>  
    <Grid.RowDefinitions>  
        <RowDefinition Height="Auto"/>  
        <RowDefinition />  
        <RowDefinition Height="Auto"/>  
    </Grid.RowDefinitions>  
    ```  
  
#### <a name="to-add-controls"></a>Chcete-li přidat ovládací prvky  
  
1.  Otevřít **ExpenseItHome.xaml**.  
  
2.  Přidejte následující kód XAML přímo nad `</Grid>` značku k vytvoření `Border`, `ListBox` a `Button` ovládací prvky.  
  
    ```xaml  
    <!-- People list -->  
      <Border Grid.Column="0" Grid.Row="0" Height="35" Padding="5" Background="#4E87D4">  
          <Label VerticalAlignment="Center" Foreground="White">Names</Label>  
      </Border>  
      <ListBox Name="peopleListBox" Grid.Column="0" Grid.Row="1">  
          <ListBoxItem>Mike</ListBoxItem>  
          <ListBoxItem>Lisa</ListBoxItem>  
          <ListBoxItem>John</ListBoxItem>  
          <ListBoxItem>Mary</ListBoxItem>  
      </ListBox>  
  
      <!-- View report button -->  
      <Button Grid.Column="0" Grid.Row="2" Margin="0,10,0,0" Width="125"  
    Height="25" HorizontalAlignment="Right">View</Button>  
  
    ```  
  
     Všimněte si, že ovládací prvky se zobrazí v okně návrhu. Může také vytvoříte ovládací prvky z jejich přetažením **nástrojů** okna do okna návrhu a nastavování jejich vlastností **vlastnosti** okna.  
  
3.  Sestavte a spusťte aplikaci. Následující obrázek znázorňuje vzhledu za běhu ovládací prvky, které jsou vytvořeny pomocí XAML v tomto postupu.  
  
     ![Snímek obrazovky ukázkové ExpenseIt –](../designers/media/gettingstartedfigure2.png "GettingStartedFigure2")  
  
4.  Ukončete aplikaci chcete vrátit do režimu návrhu.  
  
#### <a name="to-add-a-background-image"></a>Přidání obrázku na pozadí  
  
1.  Zvolte následující obrázek a uložte ho jako `watermark.png`.  
  
     ![Obrázek vodoznaku návodu](../designers/media/wpf-watermark.png "WPF_watermark")  
  
    > [!NOTE]
    >  Případně můžete vytvořit vlastní image a uložte ho jako `watermark.png`.  
  
2.  V **Průzkumníka řešení**, otevřete místní nabídku **ExpenseIt –** uzlu a zvolte **přidat**, **existující položku**.  
  
3.  V **přidat existující položku** dialogového okna, vyhledejte **watermark.png** image, kterou jste právě přidali, vyberte jej a klikněte na tlačítko **přidat** tlačítko.  
  
    > [!NOTE]
    >  Budete muset Rozbalit **typy souborů** seznam a zvolte **soubory bitových kopií**.  
  
4.  Otevřít **ExpenseItHome.xaml** a přidejte následující kód XAML přímo nad `</Grid>` značku na vytvoření bitové kopie na pozadí:  
  
    ```xaml  
    <Grid.Background>  
        <ImageBrush ImageSource="watermark.png"/>  
    </Grid.Background>  
  
    ```  
  
#### <a name="to-add-a-title"></a>Přidání názvu  
  
1.  Otevřít **ExpenseItHome.xaml**.  
  
2.  Vyhledejte řádek `<Grid.ColumnDefinitions>` a přidejte následující právě pod ní:  
  
    ```xaml  
    <ColumnDefinition Width="230" />  
  
    ```  
  
     Tím se vytvoří další sloupec nalevo od ostatních sloupců s pevnou šířkou 230 pixelů.  
  
3.  Vyhledejte řádek `<Grid.RowDefinitions>` a přidejte následující právě pod ní:  
  
    ```xaml  
    <RowDefinition />  
  
    ```  
  
     To přidá řádek do horní části mřížky.  
  
4.  Přesuňte ovládací prvky na druhý sloupec tak, že nastavíte `Grid.Column` hodnotu 1. Každý ovládací prvek dolů na řádku zvýšením každý `Grid.Row` hodnotu o 1.  
  
    1.  Vyhledejte řádek `<Border Grid.Column="0" Grid.Row="0" Height="35" Padding="5" Background="#4E87D4">`. Změnit `Grid.Column="0"` k `Grid.Column="1"` a změňte `Grid.Row="0"` k `Grid.Row="1"`.  
  
    2.  Vyhledejte řádek `<ListBox Name="peopleListBox" Grid.Column="0" Grid.Row="1"`. Změnit `Grid.Column="0"` k `Grid.Column="1"` a změňte `Grid.Row="1"` k `Grid.Row="2"`.  
  
    3.  Vyhledejte řádek `<Button Grid.Column="0" Grid.Row="2" Margin="0,10,0,0" Width="125"`. Změnit `Grid.Column="0"` k `Grid.Column="1"` a změňte `Grid.Row="2"` k `Grid.Row="3"`.  
  
5.  Těsně před `<Border` prvek přidejte následující kód XAML pro zobrazení názvu:  
  
    ```xaml  
    <Label Grid.Column="1" VerticalAlignment="Center" FontFamily="Trebuchet MS"   
            FontWeight="Bold" FontSize="18" Foreground="#0066cc">  
        View Expense Report  
    </Label>  
  
    ```  
  
     Obsah **ExpenseItHome.xaml** by teď měl vypadat takto v jazyce C#:  
  
    ```xaml  
    <Page x:Class="ExpenseIt.ExpenseItHome"  
          xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"  
          xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"  
          xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"   
          xmlns:d="http://schemas.microsoft.com/expression/blend/2008"   
          xmlns:local="clr-namespace:ExpenseIt"  
          mc:Ignorable="d"   
          d:DesignHeight="300" d:DesignWidth="300"  
          Title="ExpenseIt - Home">  
        <Grid Margin="10,0,10,10">  
            <Grid.ColumnDefinitions>  
                <ColumnDefinition Width="230" />  
                <ColumnDefinition />  
            </Grid.ColumnDefinitions>  
            <Grid.RowDefinitions>  
                <RowDefinition />  
                <RowDefinition Height="Auto"/>  
                <RowDefinition />  
                <RowDefinition Height="Auto"/>  
            </Grid.RowDefinitions>  
            <Border Grid.Column="1" Grid.Row="1" Height="35" Padding="5" Background="#4E87D4">  
                <Label VerticalAlignment="Center" Foreground="White">Names</Label>  
            </Border>  
            <!-- People list -->  
            <Label Grid.Column="1" VerticalAlignment="Center" FontFamily="Trebuchet MS"   
            FontWeight="Bold" FontSize="18" Foreground="#0066cc">  
                View Expense Report  
            </Label>  
            <ListBox Name="peopleListBox" Grid.Column="1" Grid.Row="2">  
                <ListBoxItem>Mike</ListBoxItem>  
                <ListBoxItem>Lisa</ListBoxItem>  
                <ListBoxItem>John</ListBoxItem>  
                <ListBoxItem>Mary</ListBoxItem>  
            </ListBox>  
  
            <!-- View report button -->  
            <Button Grid.Column="1" Grid.Row="3" Margin="0,10,0,0" Width="125"  
    Height="25" HorizontalAlignment="Right">View</Button>  
            <Grid.Background>  
                <ImageBrush ImageSource="watermark.png"/>  
            </Grid.Background>  
        </Grid>  
    </Page>  
    ```  
  
     Nebo takto v jazyce Visual Basic:  
  
    ```xaml  
    <Page x:Class="ExpenseItHome"  
          xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"  
          xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"  
          xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"   
          xmlns:d="http://schemas.microsoft.com/expression/blend/2008"   
          xmlns:local="clr-namespace:ExpenseIt"  
          mc:Ignorable="d"   
          d:DesignHeight="300" d:DesignWidth="300"  
          Title="ExpenseIt - Home" >  
        <Grid Margin="10,0,10,10">  
            <Grid.ColumnDefinitions>  
                <ColumnDefinition Width="230" />  
                <ColumnDefinition />  
            </Grid.ColumnDefinitions>  
            <Grid.RowDefinitions>  
                <RowDefinition />  
                <RowDefinition Height="Auto"/>  
                <RowDefinition />  
                <RowDefinition Height="Auto"/>  
            </Grid.RowDefinitions>  
            <Border Grid.Column="1" Grid.Row="1" Height="35" Padding="5" Background="#4E87D4">  
                <Label VerticalAlignment="Center" Foreground="White">Names</Label>  
            </Border>  
            <!-- People list -->  
            <Label Grid.Column="1" VerticalAlignment="Center" FontFamily="Trebuchet MS"   
            FontWeight="Bold" FontSize="18" Foreground="#0066cc">  
                View Expense Report  
            </Label>  
            <ListBox Name="peopleListBox" Grid.Column="1" Grid.Row="2">  
                <ListBoxItem>Mike</ListBoxItem>  
                <ListBoxItem>Lisa</ListBoxItem>  
                <ListBoxItem>John</ListBoxItem>  
                <ListBoxItem>Mary</ListBoxItem>  
            </ListBox>  
  
            <!-- View report button -->  
            <Button Grid.Column="1" Grid.Row="3" Margin="0,10,0,0" Width="125"  
    Height="25" HorizontalAlignment="Right">View</Button>  
            <Grid.Background>  
                <ImageBrush ImageSource="watermark.png"/>  
            </Grid.Background>  
        </Grid>  
    </Page>  
    ```  
  
6.  Pokud sestavíte a spustíte aplikaci v tomto okamžiku by měl vypadat jako na následujícím obrázku:  
  
     ![Snímek obrazovky ukázkové ExpenseIt –](../designers/media/gettingstartedfigure3.png "GettingStartedFigure3")  
  
#### <a name="to-add-code-to-the-button"></a>Přidání kódu k tlačítku  
  
1.  Otevřít **ExpenseItHome.xaml**.  
  
2.  Zvolili `<Button` elementu a přidejte následující kód XAML ihned po **HorizontalAlignment = "Vpravo"** element: `Click="Button_Click"`.  
  
     Tento postup přidá obslužnou rutinu události pro tlačítka `Click` událostí. **< Tlačítko** element kódu by teď měl vypadat takto:  
  
    ```  
    <!-- View report button -->  
      <Button Grid.Column="1" Grid.Row="3" Margin="0,10,0,0" Width="125"  
    Height="25" HorizontalAlignment="Right" Click="Button_Click">View</Button>  
    ```  
  
3.  Otevřít **ExpenseItHome.xaml.cs** nebo **ExpenseItHome.xaml.vb** souboru.  
  
4.  Přidejte následující kód, který `ExpenseItHome` třídy:  
  
    ```csharp  
    private void Button_Click(object sender, RoutedEventArgs e)  
    {  
        // View Expense Report  
        ExpenseReportPage expenseReportPage = new ExpenseReportPage();  
        this.NavigationService.Navigate(expenseReportPage);  
  
    }  
    ```  
  
    ```vb  
    Private Sub Button_Click(ByVal sender As Object, ByVal e As RoutedEventArgs)  
        ' View Expense Report  
        Dim expenseReportPage As New ExpenseReportPage()  
    Me.NavigationService.Navigate(expenseReportPage)  
    End Sub  
    ```  
  
     Tato obslužná rutina události se otevře na stránce sestavy výdajů po kliknutí na tlačítko.  
  
#### <a name="to-create-the-ui-for-the-report-page"></a>Chcete-li vytvořit uživatelské rozhraní pro stránky sestavy  
  
1.  Otevřít **ExpenseReportPage.xaml**.  
  
     Na této stránce se zobrazí vyúčtování pro osobu, která je vybrané na domovské stránce.  
  
2.  Přidejte následující kód XAML mezi `<Grid>` a `</Grid>` značky:  
  
    ```xaml  
    <Grid.Background>  
        <ImageBrush ImageSource="watermark.png" />  
    </Grid.Background>  
    <Grid.ColumnDefinitions>  
        <ColumnDefinition Width="230" />  
        <ColumnDefinition />  
    </Grid.ColumnDefinitions>  
    <Grid.RowDefinitions>  
        <RowDefinition Height="Auto" />  
        <RowDefinition />  
    </Grid.RowDefinitions>  
  
    <Label Grid.Column="1" VerticalAlignment="Center" FontFamily="Trebuchet MS"   
    FontWeight="Bold" FontSize="18" Foreground="#0066cc">  
        Expense Report For:  
    </Label>  
    <Grid Margin="10" Grid.Column="1" Grid.Row="1">  
  
        <Grid.ColumnDefinitions>  
            <ColumnDefinition />  
            <ColumnDefinition />  
        </Grid.ColumnDefinitions>  
        <Grid.RowDefinitions>  
            <RowDefinition Height="Auto" />  
            <RowDefinition Height="Auto" />  
            <RowDefinition />  
        </Grid.RowDefinitions>  
  
        <!-- Name -->  
        <StackPanel Grid.Column="0" Grid.ColumnSpan="2" Grid.Row="0" Orientation="Horizontal">  
            <Label Margin="0,0,0,5" FontWeight="Bold">Name:</Label>  
            <Label Margin="0,0,0,5" FontWeight="Bold"></Label>  
        </StackPanel>  
  
        <!-- Department -->  
        <StackPanel Grid.Column="0" Grid.ColumnSpan="2" Grid.Row="1" Orientation="Horizontal">  
            <Label Margin="0,0,0,5" FontWeight="Bold">Department:</Label>  
            <Label Margin="0,0,0,5" FontWeight="Bold"></Label>  
        </StackPanel>  
  
        <Grid Grid.Column="0" Grid.ColumnSpan="2" Grid.Row="2" VerticalAlignment="Top"   
              HorizontalAlignment="Left">  
            <!-- Expense type and Amount table -->  
            <DataGrid  AutoGenerateColumns="False" RowHeaderWidth="0" >  
                <DataGrid.ColumnHeaderStyle>  
                    <Style TargetType="{x:Type DataGridColumnHeader}">  
                        <Setter Property="Height" Value="35" />  
                        <Setter Property="Padding" Value="5" />  
                        <Setter Property="Background" Value="#4E87D4" />  
                        <Setter Property="Foreground" Value="White" />  
                    </Style>  
                </DataGrid.ColumnHeaderStyle>  
                <DataGrid.Columns>  
                    <DataGridTextColumn Header="ExpenseType" />  
                    <DataGridTextColumn Header="Amount"  />  
                </DataGrid.Columns>  
            </DataGrid>  
        </Grid>  
    </Grid>  
    ```  
  
     Toto uživatelské rozhraní se podobá v uživatelském rozhraní vytvořené pro domovskou stránku, ale data sestavy se zobrazí v **DataGrid** ovládacího prvku.  
  
3.  Sestavte a spusťte aplikaci.  
  
4.  Zvolte **zobrazení** tlačítko.  
  
     Zobrazí se stránka sestavy výdajů.  
  
     Následující obrázek znázorňuje stránky sestavy výdajů. Všimněte si, že je povoleno tlačítko zpětné navigace.  
  
     ![Snímek obrazovky ukázkové ExpenseIt –](../designers/media/gettingstartedfigure4.png "GettingStartedFigure4")  
  
#### <a name="to-style-controls"></a>Pro ovládací prvky stylu  
  
1.  Otevřít **App.xaml** souboru (C#) nebo **Application.xaml** souboru (Visual Basic).  
  
2.  Přidejte následující XAML mezi `<Application.Resources>` a `</Application.Resources>` značky:  
  
    ```xaml  
    <!-- Header text style -->  
    <Style x:Key="headerTextStyle">  
        <Setter Property="Label.VerticalAlignment" Value="Center"></Setter>  
        <Setter Property="Label.FontFamily" Value="Trebuchet MS"></Setter>  
        <Setter Property="Label.FontWeight" Value="Bold"></Setter>  
        <Setter Property="Label.FontSize" Value="18"></Setter>  
        <Setter Property="Label.Foreground" Value="#0066cc"></Setter>  
    </Style>  
  
    <!-- Label style -->  
    <Style x:Key="labelStyle" TargetType="{x:Type Label}">  
        <Setter Property="VerticalAlignment" Value="Top" />  
        <Setter Property="HorizontalAlignment" Value="Left" />  
        <Setter Property="FontWeight" Value="Bold" />  
        <Setter Property="Margin" Value="0,0,0,5" />  
    </Style>  
  
    <!-- DataGrid header style -->  
    <Style x:Key="columnHeaderStyle" TargetType="{x:Type DataGridColumnHeader}">  
        <Setter Property="Height" Value="35" />  
        <Setter Property="Padding" Value="5" />  
        <Setter Property="Background" Value="#4E87D4" />  
        <Setter Property="Foreground" Value="White" />  
    </Style>  
  
    <!-- List header style -->  
    <Style x:Key="listHeaderStyle" TargetType="{x:Type Border}">  
        <Setter Property="Height" Value="35" />  
        <Setter Property="Padding" Value="5" />  
        <Setter Property="Background" Value="#4E87D4" />  
    </Style>  
  
    <!-- List header text style -->  
    <Style x:Key="listHeaderTextStyle" TargetType="{x:Type Label}">  
        <Setter Property="Foreground" Value="White" />  
        <Setter Property="VerticalAlignment" Value="Center" />  
        <Setter Property="HorizontalAlignment" Value="Left" />  
    </Style>  
  
    <!-- Button style -->  
    <Style x:Key="buttonStyle" TargetType="{x:Type Button}">  
        <Setter Property="Width" Value="125" />  
        <Setter Property="Height" Value="25" />  
        <Setter Property="Margin" Value="0,10,0,0" />  
        <Setter Property="HorizontalAlignment" Value="Right" />  
    </Style>  
    ```  
  
     Tento XAML přidá následující styly:  
  
    -   `headerTextStyle`: K formátování se název stránky `Label`.  
  
    -   `labelStyle`: K formátování `Label` ovládacích prvků.  
  
    -   `columnHeaderStyle`: K formátování `DataGridColumnHeader`.  
  
    -   `listHeaderStyle`: K formátování záhlaví seznamu `Border` ovládacích prvků.  
  
    -   `listHeaderTextStyle`: K formátování záhlaví seznamu **popisek**.  
  
    -   `buttonStyle`: K formátování `Button` na **ExpenseItHome.xaml** pppage.  
  
3.  Otevřít **ExpenseItHome.xaml** a nahradit všechno mezi `<Grid>` a `</Grid>` prvky s následující XAML  
  
    ```xaml  
    <Grid.ColumnDefinitions>  
                <ColumnDefinition Width="230" />  
                <ColumnDefinition />  
            </Grid.ColumnDefinitions>  
  
            <Grid.RowDefinitions>  
                <RowDefinition/>  
                <RowDefinition Height="Auto"/>  
                <RowDefinition />  
                <RowDefinition Height="Auto"/>  
            </Grid.RowDefinitions>  
            <Label Grid.Column="1" Style="{StaticResource headerTextStyle}" >  
                View Expense Report  
            </Label>  
            <!-- People list -->  
                  <Border Grid.Column="1" Grid.Row="1" Style="{StaticResource listHeaderStyle}">  
                <Label Style="{StaticResource listHeaderTextStyle}">Names</Label>  
            </Border>  
            <ListBox Name="peopleListBox" Grid.Column="1" Grid.Row="2">  
                <ListBoxItem>Mike</ListBoxItem>  
                <ListBoxItem>Lisa</ListBoxItem>  
                <ListBoxItem>John</ListBoxItem>  
                <ListBoxItem>Mary</ListBoxItem>  
            </ListBox>  
  
            <!-- View report button -->  
            <Button Grid.Column="1" Grid.Row="3" Click="Button_Click" Style="{StaticResource buttonStyle}">View</Button>  
            <Grid.Background>  
                <ImageBrush ImageSource="watermark.png"  />  
            </Grid.Background>  
    ```  
  
     Vlastnosti, jako `VerticalAlignment` a `FontFamily` , které definují vzhled každého ovládacího prvku odebrán a nahrazen o aplikování stylů.  
  
4.  Otevřít **ExpenseReportPage.xaml** a nahradit všechno mezi `<Grid>` a finální `</Grid>` prvky s následující XAML  
  
    ```xaml  
    <Grid.Background>  
        <ImageBrush ImageSource="watermark.png" />  
    </Grid.Background>  
    <Grid.ColumnDefinitions>  
        <ColumnDefinition Width="230" />  
        <ColumnDefinition />  
    </Grid.ColumnDefinitions>  
    <Grid.RowDefinitions>  
        <RowDefinition Height="Auto" />  
        <RowDefinition />  
    </Grid.RowDefinitions>  
    <Label Grid.Column="1" Style="{StaticResource headerTextStyle}">  
        Expense Report For:  
    </Label>  
    <Grid Margin="10" Grid.Column="1" Grid.Row="1">  
        <Grid.ColumnDefinitions>  
            <ColumnDefinition />  
            <ColumnDefinition />  
        </Grid.ColumnDefinitions>  
        <Grid.RowDefinitions>  
            <RowDefinition Height="Auto" />  
            <RowDefinition Height="Auto" />  
            <RowDefinition />  
        </Grid.RowDefinitions>  
  
        <!-- Name -->  
        <StackPanel Grid.Column="0" Grid.ColumnSpan="2" Grid.Row="0" Orientation="Horizontal">  
            <Label Style="{StaticResource labelStyle}">Name:</Label>  
            <Label Style="{StaticResource labelStyle}"></Label>  
        </StackPanel>  
  
        <!-- Department -->  
        <StackPanel Grid.Column="0" Grid.ColumnSpan="2" Grid.Row="1"   
    Orientation="Horizontal">  
            <Label Style="{StaticResource labelStyle}">Department:</Label>  
            <Label Style="{StaticResource labelStyle}"></Label>  
        </StackPanel>  
  
        <Grid Grid.Column="0" Grid.ColumnSpan="2" Grid.Row="2" VerticalAlignment="Top"   
              HorizontalAlignment="Left">  
            <!-- Expense type and Amount table -->  
            <DataGrid ColumnHeaderStyle="{StaticResource columnHeaderStyle}"   
                      AutoGenerateColumns="False" RowHeaderWidth="0" >  
                <DataGrid.Columns>  
                    <DataGridTextColumn Header="ExpenseType" />  
                    <DataGridTextColumn Header="Amount"  />  
                </DataGrid.Columns>  
            </DataGrid>  
        </Grid>  
    </Grid>  
  
    ```  
  
     Tento postup přidá stylů `<Label>` a `<Border>` elementy.  
  
## <a name="connecting-to-data"></a>Připojení k datům  
 V této části vytvoříte zprostředkovatele dat a datové šablony a pak se připojte ovládacích prvků pro zobrazení dat.  
  
#### <a name="to-bind-data-to-a-control"></a>Vazba dat k ovládacímu prvku  
  
1.  Otevřít **ExpenseItHome.xaml** a zvolte `<Grid>` prvek...  
  
2.  Přidejte následující kód XAML:  
  
    ```xaml  
  
    <Grid.Resources>  
    <!-- Expense Report Data -->  
    <XmlDataProvider x:Key="ExpenseDataSource" XPath="Expenses">  
        <x:XData>  
            <Expenses xmlns="">  
                <Person Name="Mike" Department="Legal">  
                    <Expense ExpenseType="Lunch" ExpenseAmount="50" />  
                    <Expense ExpenseType="Transportation" ExpenseAmount="50" />  
                </Person>  
                <Person Name="Lisa" Department="Marketing">  
                    <Expense ExpenseType="Document printing"  
          ExpenseAmount="50"/>  
                    <Expense ExpenseType="Gift" ExpenseAmount="125" />  
                </Person>  
                <Person Name="John" Department="Engineering">  
                    <Expense ExpenseType="Magazine subscription"   
         ExpenseAmount="50"/>  
                    <Expense ExpenseType="New machine" ExpenseAmount="600" />  
                    <Expense ExpenseType="Software" ExpenseAmount="500" />  
                </Person>  
                <Person Name="Mary" Department="Finance">  
                    <Expense ExpenseType="Dinner" ExpenseAmount="100" />  
                </Person>  
            </Expenses>  
        </x:XData>  
    </XmlDataProvider>  
    </Grid.Resources>  
    ```  
  
     Tento kód vytvoří `XmlDataProvider` třídu, která obsahuje data pro každou osobu. Obvykle to budou načteny jako soubor, ale pro zjednodušení je přidat data vložené.  
  
3.  Uvnitř `<Grid.Resources>` prvku, přidejte následující kód XAML:  
  
    ```xaml  
    <!-- Name item template -->  
    <DataTemplate x:Key="nameItemTemplate">  
        <Label Content="{Binding XPath=@Name}"/>  
    </DataTemplate>  
    ```  
  
     Tím se přidá `Data Template` určující způsob zobrazení dat v **ListBox**.  
  
4.  Nahraďte existující `<ListBox>` element s následující XAML.  
  
    ```xaml  
    <ListBox Name="peopleListBox" Grid.Column="1" Grid.Row="2"   
             ItemsSource="{Binding Source={StaticResource ExpenseDataSource}, XPath=Person}"  
             ItemTemplate="{StaticResource nameItemTemplate}">  
    </ListBox>  
    ```  
  
     Tento kód vytvoří vazbu `ItemsSource` vlastnost `ListBox` ke zdroji dat a použije šablona dat jako `ItemTemplate`.  
  
#### <a name="to-connect-data-to-controls"></a>K připojení dat k ovládacím prvkům  
  
1.  Otevřít **ExpenseReportPage.xaml.vb** nebo **ExpenseReportPage.xaml.cs**.  
  
2.  V jazyce C#, přidejte následující konstruktor k **ExpenseReportPage** třídy nebo v jazyce Visual Basic nahraďte existující třídy následujícím kódem:  
  
    ```csharp  
    // Custom constructor to pass expense report data  
        public ExpenseReportPage(object data):this()  
        {  
            // Bind to expense report data.  
            this.DataContext = data;  
        }  
    ```  
  
    ```vb  
    Partial Public Class ExpenseReportPage  
    Inherits Page  
    Public Sub New()  
    InitializeComponent()  
    End Sub  
  
    ' Custom constructor to pass expense report data  
    Public Sub New(ByVal data As Object)  
    Me.New()  
    ' Bind to expense report data.  
    Me.DataContext = data  
    End Sub  
  
    End Class  
    ```  
  
     Tento konstruktor je jako parametr používá datový objekt. Datový objekt v tomto případě bude obsahovat název vybraného uživatele.  
  
3.  Otevřít **ExpenseItHome.xaml.vb** nebo **ExpenseItHome.xaml.cs**.  
  
4.  Nahradit `Click` kód obslužné rutiny událostí následujícím kódem:  
  
    ```csharp  
    private void Button_Click(object sender, RoutedEventArgs e)  
    {  
        // View Expense Report  
        ExpenseReportPage expenseReportPage = new ExpenseReportPage(this.peopleListBox.SelectedItem);  
        this.NavigationService.Navigate(expenseReportPage);  
  
    }  
    ```  
  
    ```vb  
    Private Sub Button_Click(ByVal sender As Object, ByVal e As RoutedEventArgs)  
        ' View Expense Report  
        Dim expenseReportPage As New ExpenseReportPage(Me.peopleListBox.SelectedItem)  
        Me.NavigationService.Navigate(expenseReportPage)  
    End Sub  
    ```  
  
     Tento kód volá nový konstruktor.  
  
#### <a name="to-update-the-ui-with-data-templates"></a>Aktualizace uživatelského rozhraní pomocí šablony  
  
1.  Otevřít **ExpenseReportPage.xaml**.  
  
2.  Nahraďte kód XAML **název** a **oddělení** `<StackPanel` prvky s následující:  
  
    ```xaml  
    <!-- Name -->  
    <StackPanel Grid.Column="0" Grid.ColumnSpan="2" Grid.Row="0" Orientation="Horizontal">  
        <Label Style="{StaticResource labelStyle}">Name:</Label>  
        <Label Style="{StaticResource labelStyle}" Content="{Binding XPath=@Name}"></Label>  
    </StackPanel>  
  
    <!-- Department -->  
    <StackPanel Grid.Column="0" Grid.ColumnSpan="2" Grid.Row="1" Orientation="Horizontal">  
        <Label Style="{StaticResource labelStyle}">Department:</Label>  
        <Label Style="{StaticResource labelStyle}" Content="{Binding XPath=@Department}"></Label>  
    </StackPanel>  
  
    ```  
  
     Tím je vytvořena vazba **popisek** ovládacích prvků pro vlastnosti zdroje dat vhodné.  
  
3.  Přidejte následující kód XAML `<Grid>` element:  
  
    ```xaml  
    <!--Templates to display expense report data-->  
    <Grid.Resources>  
        <!-- Reason item template -->  
        <DataTemplate x:Key="typeItemTemplate">  
            <Label Content="{Binding XPath=@ExpenseType}"/>  
        </DataTemplate>  
        <!-- Amount item template -->  
        <DataTemplate x:Key="amountItemTemplate">  
            <Label Content="{Binding XPath=@ExpenseAmount}"/>  
        </DataTemplate>  
    </Grid.Resources>  
  
    ```  
  
     Definuje způsob zobrazení dat sestavy výdajů.  
  
4.  Nahradit `<DataGrid>` element následujícím kódem:  
  
    ```xaml  
    <!-- Expense type and Amount table -->  
    <DataGrid ItemsSource="{Binding XPath=Expense}" ColumnHeaderStyle="{StaticResource columnHeaderStyle}" AutoGenerateColumns="False" RowHeaderWidth="0" >  
  
        <DataGrid.Columns>  
            <DataGridTextColumn Header="ExpenseType" Binding="{Binding XPath=@ExpenseType}"  />  
            <DataGridTextColumn Header="Amount" Binding="{Binding XPath=@ExpenseAmount}" />  
        </DataGrid.Columns>  
  
    </DataGrid>  
    ```  
  
     Tím se přidá **vlastnost ItemSource** a definuje vazbu pro výdajové položky.  
  
5.  Sestavte a spusťte aplikaci.  
  
6.  Vyberte osobu a klikněte na tlačítko **zobrazení** tlačítko.  
  
     Následující obrázek znázorňuje obě stránky ExpenseIt – aplikace s ovládacími prvky, rozložení, styly, vazby dat a použitých šablon data.  
  
     ![Snímky obrazovky ukázkové ExpenseIt –](../designers/media/gettingstartedfigure5.png "GettingStartedFigure5")  
  
##  <a name="Best_Practices"></a> Osvědčené postupy  
 Tento příklad ukazuje základy WPF a v důsledku toho nedodržuje osvědčené postupy při vývoji aplikace. Pro komplexní pokrytí WPF a .NET Framework aplikace osvědčené postupy pro vývoj naleznete v následujících tématech podle potřeby:  
  
-   Usnadnění – [usnadnění – doporučené postupy](https://msdn.microsoft.com/library/aa350483\(v=vs.100\).aspx)  
  
-   Zabezpečení – [zabezpečení Windows Presentation Foundation](https://msdn.microsoft.com/library/aa970906\(v=vs.100\).aspx)  
  
-   Lokalizace - [přehled WPF globalizace a lokalizace](https://msdn.microsoft.com/library/ms788718\(v=vs.100\).aspx)  
  
-   Výkon - [optimalizace výkonu aplikace WPF](https://msdn.microsoft.com/library/aa970683\(v=vs.100\).aspx)  
  
##  <a name="Whats_Next"></a> Co se chystá  
 Teď máte řadu technik k dispozici pro vytváření aplikací pro stolní počítače s použitím WPF. Nyní byste měli mít základní znalosti o stavební kameny nástroje aplikace WPF vázané na data. V tomto tématu nejsou v žádném smyslu vyčerpávající, ale snad také Teď máte představu o některé z možností, které můžete narazit na vlastní nad rámec techniky v tomto tématu.  
  
 Další informace o WPF architekturu a programovací modely naleznete v následujících tématech:  
  
- [Architektura WPF](https://msdn.microsoft.com/library/ms750441\(v=vs.100\).aspx)  
  
- [Přehled XAML](https://msdn.microsoft.com/library/ms752059\(v=vs.100\).aspx)  
  
- [Přehled vlastností závislosti](https://msdn.microsoft.com/library/ms752914\(v=vs.100\).aspx)  
  
- [Systém rozložení](https://msdn.microsoft.com/library/ms745058\(v=vs.100\).aspx)  
  
- [Styly a šablony](https://msdn.microsoft.com/library/bb613570\(v=vs.100\).aspx)  
  
  Další informace o vytváření aplikací naleznete v následujících tématech:  
  
- [Přehled vývoje databázových aplikací](https://msdn.microsoft.com/library/bb613549\(v=vs.100\).aspx)  
  
- [Přehled ovládacích prvků](https://msdn.microsoft.com/library/bb613551\(v=vs.100\).aspx)  
  
- [Přehled datových vazeb](https://msdn.microsoft.com/library/ms752347\(v=vs.100\).aspx)  
  
- [Přehled média, animace a grafiky WPF](https://msdn.microsoft.com/library/ms742562\(v=vs.100\).aspx)  
  
- [Dokumenty v platformě WPF](https://msdn.microsoft.com/library/ms748388\(v=vs.100\).aspx)  
  
## <a name="see-also"></a>Viz také  
 [Návod: Vytvoření aplikace WPF plochy připojené k mobilní službě Azure](../designers/walkthrough-create-a-wpf-desktop-application-connected-to-an-azure-mobile-service.md)   
 [Vytvoření moderních desktopových aplikací pomocí Windows Presentation Foundation](../designers/create-modern-desktop-applications-with-windows-presentation-foundation.md)



