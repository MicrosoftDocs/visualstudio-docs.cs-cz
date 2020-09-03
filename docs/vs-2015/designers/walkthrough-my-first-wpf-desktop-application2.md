---
title: 'Návod: Moje první desktopová plocha WPF Application2 | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-designers
ms.topic: conceptual
ms.assetid: 3c460fa9-2ea1-413f-ae54-54a1f2a499d1
caps.latest.revision: 8
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: e800fe651d32435351b2338b4da2f9c55158b3a0
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "72663997"
---
# <a name="walkthrough-my-first-wpf-desktop-application"></a>Návod: Moje první desktopová aplikace WPF
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

a Name = "Úvod" ></a> Tento návod poskytuje Úvod do vývoje Windows Presentation Foundation (WPF). Vytvoříte základní aplikaci, která obsahuje prvky, které jsou společné pro většinu desktopových aplikací WPF: kód jazyka XAML, kód na pozadí, definice aplikací, ovládací prvky, rozložení, datové vazby a styly.

## <a name="creating-the-application-project"></a><a name="Create_The_Application_Code_Files"></a> Vytvoření projektu aplikace
 V této části vytvoříte aplikační infrastrukturu, která zahrnuje projekt a hlavní okno nebo formulář.

#### <a name="to-create-the-project"></a>Vytvoření projektu

1. Na panelu nabídek vyberte položku **soubor**, **Nový**, **projekt**.

2. V dialogovém okně **Nový projekt** rozbalte uzel **Visual C#** nebo **Visual Basic** a zvolte uzel **Windows** a potom rozbalte uzel **Windows** a zvolte **klasický desktopový** uzel.

3. V seznamu šablon vyberte šablonu **aplikace WPF** .

4. Do textového pole **název** zadejte `ExpenseIt` a pak klikněte na tlačítko **OK** .

     Projekt je vytvořen a jsou přidány soubory projektu do **Průzkumník řešení**a zobrazí se Návrhář pro výchozí okno aplikace s názvem **MainWindow. XAML** .

#### <a name="to-modify-the-main-window"></a>Úprava hlavního okna

1. V návrháři vyberte kartu **MainWindow. XAML** , pokud již není aktivní kartou návrháře.

2. Pokud používáte jazyk C#, Najděte řádek `<Window x:Class="ExpenseIt.MainWindow"` a nahraďte ho `<NavigationWindow x:Class="ExpenseIt.MainWindow"` .

     Pokud používáte Visual Basic, Najděte řádek `<Window x:Class=" MainWindow"` a nahraďte ho `<NavigationWindow x:Class="MainWindow"` .

     Všimněte si, že když změníte `<Window` značku na `<NavigationWindow` , technologie IntelliSense automaticky změní uzavírací značku na také `</NavigationWindow>` .

    > [!NOTE]
    > Pokud je po změně značky otevřené okno **Seznam chyb** , můžete si všimnout několika chyb. Nedělejte si starosti, změny provedené v následujících krocích provedete tak, jak jsou pryč.

3. Vyberte `<Grid>` značky a `</Grid>` a odstraňte je.

     **Objektu NavigationWindow** nemůže obsahovat jiné prvky uživatelského rozhraní, jako je například **Mřížka**.

4. V okně **vlastnosti** rozbalte uzel **společná** kategorie a zvolte vlastnost **název** a potom zadejte a stiskněte klávesu `ExpenseIt` **ENTER** .

     Všimněte si, že se element **title** v okně XAML změní tak, aby odpovídal nové hodnotě. Vlastnosti XAML lze upravit buď v okně XAML, nebo v okně **vlastnosti** , a změny budou synchronizovány.

5. V okně XAML nastavte hodnotu prvku **Height** na `375` a nastavte hodnotu vlastnosti **Width** na `500` .

     Tyto prvky odpovídají vlastnostem **Výška** a **Šířka** , které se nacházejí v kategorii **rozložení** v okně **vlastnosti** .

     Váš soubor **MainWindow. XAML** by teď měl vypadat jako v jazyce C#:

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

     Nebo podobně jako v Visual Basic:

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

1. V **Průzkumník řešení**rozbalte uzel **MainWindow. XAML** a otevřete soubor **MainWindow.XAML.cs** .

2. Najděte řádek `public partial class MainWindow : Window` a nahraďte ho `public partial class MainWindow : NavigationWindow` .

     Tím se změní `MainWindow` třída, ze které se má odvozovat `NavigationWindow` . V Visual Basic k tomu dochází automaticky při změně okna v jazyce XAML, takže není nutné dělat žádné změny kódu.

## <a name="adding-files-to-the-application"></a><a name="add_files_to_the_application"></a> Přidávání souborů do aplikace
 V této části přidáte do aplikace dvě stránky a image.

#### <a name="to-add-a-home-screen"></a>Přidání domovské obrazovky

1. V **Průzkumník řešení**otevřete místní nabídku uzlu **ExpenseIt** a vyberte možnost **Přidat**, **Stránka**.

2. V dialogovém okně **Přidat novou položku** zvolte textové pole **název** a zadejte a `ExpenseItHome` pak klikněte na tlačítko **Přidat** .

     Tato stránka je prvním oknem, které se zobrazí při spuštění aplikace.

3. V návrháři vyberte kartu **ExpenseItHome. XAML** , pokud již není aktivní kartou návrháře.

4. Vyberte `<Title>` element a změňte název na **ExpenseIt – Home**.

     Váš soubor **ExpenseItHome. XAML** by teď měl vypadat jako v jazyce C#:

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

     Nebo podobně jako v Visual Basic:

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

5. V návrháři klikněte na kartu **MainWindow. XAML** .

6. Najděte element line `Title="ExpenseIt" Height="375" Width="500">` a přidejte `Source="ExpenseItHome.xaml"` vlastnost.

     Tato sada **ExpenseItHome. XAML** nastaví jako první stránku otevřenou při spuštění aplikace. Váš soubor **MainWindow. XAML** by teď měl vypadat jako v jazyce C#:

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

     Nebo podobně jako v Visual Basic:

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

     Stejně jako u vlastností, které jste nastavili dříve, mohli byste nastavit `Source` vlastnost v kategorii **různé** v okně **vlastnosti** .

#### <a name="to-add-a-details-window"></a>Přidání okna podrobností

1. V **Průzkumník řešení**otevřete místní nabídku uzlu **ExpenseIt** a vyberte možnost **Přidat**, **Stránka**.

2. V dialogovém okně **Přidat novou položku** zvolte textové pole **název** a zadejte a `ExpenseReportPage` pak klikněte na tlačítko **Přidat** .

     V tomto okně se zobrazí jednotlivá Sestava výdajů.

3. V návrháři vyberte kartu **ExpenseReportPage. XAML** , pokud již není aktivní kartou návrháře.

4. Vyberte `<Title>` element a změňte nadpis na **ExpenseIt – zobrazit náklady**.

     Váš soubor ExpenseReportPage. XAML by teď měl vypadat jako v jazyce C#:

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

     Nebo podobně jako v Visual Basic:

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

5. Na panelu nabídek zvolte položku **ladit**, **Spustit ladění** (nebo stiskněte klávesu F5) a spusťte aplikaci.

     Na následujícím obrázku je znázorněna aplikace s tlačítky pro navigační okno.

     ![Snímek obrazovky Ukázka ExpenseIt](../designers/media/gettingstartedfigure1.png "GettingStartedFigure1")

6. Ukončete aplikaci a vraťte se do režimu návrhu.

## <a name="creating-the-user-interface"></a><a name="Add_Layout"></a> Vytvoření uživatelského rozhraní
 Rozložení poskytuje uspořádaný způsob, jak umístit prvky a také spravuje velikost a polohu těchto prvků při změně velikosti formuláře. V této části vytvoříte mřížku s jedním sloupcem se třemi řádky. Přidáte ovládací prvky na dvě stránky, přidáte nějaký kód a nakonec definujete opakovaně použitelné styly pro ovládací prvky.

#### <a name="to-create-the-layout"></a>Vytvoření rozložení

1. Otevřete **ExpenseItHome. XAML** a vyberte `<Grid>` element.

2. V okně **vlastnosti** rozbalte uzel kategorie **rozložení** a nastavte hodnoty **okrajů** na `10` , `10` , `0` a `10` , které odpovídají levému, pravému a hornímu a dolnímu okraji.

     Prvek `Margin="10,0,10,10"` je přidán do `<Grid>` prvku v jazyce XAML. Později jste mohli tyto hodnoty zadat přímo v kódu XAML místo v okně **vlastnosti** se stejným výsledkem.

3. Přidejte následující kód XAML k `Grid` elementu pro vytvoření definice řádků a sloupců:

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

#### <a name="to-add-controls"></a>Přidání ovládacích prvků

1. Otevřete **ExpenseItHome. XAML**.

2. `</Grid>`Chcete-li vytvořit `Border` `ListBox` ovládací prvky, přidejte následující kód XAML hned nad značku `Button` .

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

     Všimněte si, že ovládací prvky se zobrazí v okně návrh. Můžete také vytvořit ovládací prvky jejich přetažením z okna **panelu nástrojů** do okna návrh a nastavit jejich vlastnosti v okně **vlastnosti** .

3. Sestavte a spusťte aplikaci. Následující ilustrace znázorňuje dobu běhu ovládacích prvků, které jsou vytvořeny pomocí jazyka XAML v tomto postupu.

     ![Snímek obrazovky Ukázka ExpenseIt](../designers/media/gettingstartedfigure2.png "GettingStartedFigure2")

4. Ukončete aplikaci a vraťte se do režimu návrhu.

#### <a name="to-add-a-background-image"></a>Přidání obrázku na pozadí

1. Vyberte následující obrázek a uložte ho jako `watermark.png` .

     ![Obrázek vodoznaku pro návod](../designers/media/wpf-watermark.png "WPF_watermark")

    > [!NOTE]
    > Případně můžete vytvořit vlastní image a uložit ji jako `watermark.png` .

2. V **Průzkumník řešení**otevřete místní nabídku uzlu **ExpenseIt** a vyberte **Přidat**, **existující položka**.

3. V dialogovém okně **Přidat existující položku** vyhledejte **watermark.png** obrázek, který jste právě přidali, zvolte ho a pak klikněte na tlačítko **Přidat** .

    > [!NOTE]
    > Možná budete muset rozbalit seznam **typy souborů** a zvolit **soubory imagí**.

4. Otevřete soubor **ExpenseItHome. XAML** a přidejte následující kód XAML hned nad `</Grid>` značku a vytvořte tak obrázek pozadí:

    ```xaml
    <Grid.Background>
        <ImageBrush ImageSource="watermark.png"/>
    </Grid.Background>

    ```

#### <a name="to-add-a-title"></a>Přidání názvu

1. Otevřete **ExpenseItHome. XAML**.

2. Najděte řádek `<Grid.ColumnDefinitions>` a přidejte ho hned pod tímto textem:

    ```xaml
    <ColumnDefinition Width="230" />

    ```

     Tím se vytvoří další sloupec nalevo od ostatních sloupců s pevnou šířkou 230 pixelů.

3. Najděte řádek `<Grid.RowDefinitions>` a přidejte ho hned pod tímto textem:

    ```xaml
    <RowDefinition />

    ```

     Tím se přidá řádek do horní části mřížky.

4. Přesuňte ovládací prvky do druhého sloupce nastavením `Grid.Column` hodnoty na 1. Každý ovládací prvek se posune o jeden řádek dolů tím, že se každá `Grid.Row` hodnota zvýší o 1.

    1. Najděte řádek `<Border Grid.Column="0" Grid.Row="0" Height="35" Padding="5" Background="#4E87D4">` . Změňte `Grid.Column="0"` na `Grid.Column="1"` `Grid.Row="0"` `Grid.Row="1"` .

    2. Najděte řádek `<ListBox Name="peopleListBox" Grid.Column="0" Grid.Row="1"` . Změňte `Grid.Column="0"` na `Grid.Column="1"` `Grid.Row="1"` `Grid.Row="2"` .

    3. Najděte řádek `<Button Grid.Column="0" Grid.Row="2" Margin="0,10,0,0" Width="125"` . Změňte `Grid.Column="0"` na `Grid.Column="1"` `Grid.Row="2"` `Grid.Row="3"` .

5. Těsně před `<Border` prvkem přidejte následující kód XAML pro zobrazení názvu:

    ```xaml
    <Label Grid.Column="1" VerticalAlignment="Center" FontFamily="Trebuchet MS"
            FontWeight="Bold" FontSize="18" Foreground="#0066cc">
        View Expense Report
    </Label>

    ```

     Obsah souboru **ExpenseItHome. XAML** by teď měl vypadat jako v jazyce C#:

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

     Nebo podobně jako v Visual Basic:

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

6. Pokud v tomto okamžiku sestavíte a spustíte aplikaci, měla by vypadat jako na následujícím obrázku:

     ![Snímek obrazovky Ukázka ExpenseIt](../designers/media/gettingstartedfigure3.png "GettingStartedFigure3")

#### <a name="to-add-code-to-the-button"></a>Přidání kódu k tlačítku

1. Otevřete **ExpenseItHome. XAML**.

2. Zvolte `<Button` prvek a přidejte následující kód XAML hned za element **HorizontalAlignment = "Right"** : `Click="Button_Click"` .

     Tím se přidá obslužná rutina události pro `Click` Událost tlačítka. Kód prvku ** tlačítka<** by teď měl vypadat takto:

    ```
    <!-- View report button -->
      <Button Grid.Column="1" Grid.Row="3" Margin="0,10,0,0" Width="125"
    Height="25" HorizontalAlignment="Right" Click="Button_Click">View</Button>
    ```

3. Otevřete soubor **ExpenseItHome.XAML.cs** nebo **ExpenseItHome. XAML** .

4. Do třídy přidejte následující kód `ExpenseItHome` :

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

     Tato obslužná rutina události otevře stránku sestavy výdajů při kliknutí na tlačítko.

#### <a name="to-create-the-ui-for-the-report-page"></a>Vytvoření uživatelského rozhraní stránky sestavy

1. Otevřete **ExpenseReportPage. XAML**.

     Na této stránce se zobrazí sestava výdajů pro osobu, která je vybrána na domovské stránce.

2. Do značek a přidejte následující kód XAML `<Grid>` `</Grid>` :

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

     Toto uživatelské rozhraní se podobá uživatelskému rozhraní vytvořenému pro domovskou stránku, ale data sestavy se zobrazí v ovládacím prvku **DataGrid** .

3. Sestavte a spusťte aplikaci.

4. Klikněte na tlačítko **Zobrazit** .

     Zobrazí se stránka Sestava výdajů.

     Na následujícím obrázku vidíte stránku sestavy výdajů. Všimněte si, že je povoleno tlačítko zpět navigace.

     ![Snímek obrazovky Ukázka ExpenseIt](../designers/media/gettingstartedfigure4.png "GettingStartedFigure4")

#### <a name="to-style-controls"></a>Do ovládacích prvků stylu

1. Otevřete soubor **App. XAML** (C#) nebo **Application. XAML** (Visual Basic).

2. Přidejte následující kód XAML mezi `<Application.Resources>` značky a `</Application.Resources>` :

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

     Tento kód XAML přidá následující styly:

    - `headerTextStyle`: Pro naformátování nadpisu stránky `Label` .

    - `labelStyle`: Pro formátování `Label` ovládacích prvků.

    - `columnHeaderStyle`: K naformátování `DataGridColumnHeader` .

    - `listHeaderStyle`: Pro formátování `Border` ovládacích prvků záhlaví seznamu.

    - `listHeaderTextStyle`: Pro formátování **popisku**záhlaví seznamu.

    - `buttonStyle`: Pro naformátování souboru `Button` **ExpenseItHome. XAML** pppage.

3. Otevřete **ExpenseItHome. XAML** a nahraďte vše mezi `<Grid>` `</Grid>` elementy a následujícím XAML.

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

     Vlastnosti, jako `VerticalAlignment` jsou a definující `FontFamily` vzhled jednotlivých ovládacích prvků, jsou odebrány a nahrazeny použitím stylů.

4. Otevřete **ExpenseReportPage. XAML** a nahraďte vše mezi `<Grid>` koncovými `</Grid>` elementy a následujícím XAML.

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

     Tím se přidají styly `<Label>` do `<Border>` prvků a.

## <a name="connecting-to-data"></a>Připojení k datům
 V této části vytvoříte poskytovatele dat a šablonu dat a potom propojíte ovládací prvky, abyste zobrazili data.

#### <a name="to-bind-data-to-a-control"></a>Vytvoření vazby dat k ovládacímu prvku

1. Otevřete **ExpenseItHome. XAML** a vyberte `<Grid>` element..

2. Přidejte následující kód XAML:

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

     Tento kód vytvoří `XmlDataProvider` třídu, která obsahuje data pro každou osobu. Obvykle by se to načetlo jako soubor, ale pro zjednodušení se data přidávají jako vložené.

3. Uvnitř `<Grid.Resources>` elementu přidejte následující kód XAML:

    ```xaml
    <!-- Name item template -->
    <DataTemplate x:Key="nameItemTemplate">
        <Label Content="{Binding XPath=@Name}"/>
    </DataTemplate>
    ```

     Tím přidáte, `Data Template` který definuje, jak se mají zobrazovat data v **seznamu**.

4. Nahraďte existující `<ListBox>` prvek následujícím XAML.

    ```xaml
    <ListBox Name="peopleListBox" Grid.Column="1" Grid.Row="2"
             ItemsSource="{Binding Source={StaticResource ExpenseDataSource}, XPath=Person}"
             ItemTemplate="{StaticResource nameItemTemplate}">
    </ListBox>
    ```

     Tento kód váže `ItemsSource` vlastnost `ListBox` na zdroj dat a použije šablonu dat jako `ItemTemplate` .

#### <a name="to-connect-data-to-controls"></a>Připojení dat k ovládacím prvkům

1. Otevřete **ExpenseReportPage. XAML. vb** nebo **ExpenseReportPage.XAML.cs**.

2. V jazyce C# přidejte následující konstruktor do třídy **ExpenseReportPage** nebo v Visual Basic nahraďte existující třídu následujícím způsobem:

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

     Tento konstruktor přebírá datový objekt jako parametr. V takovém případě datový objekt bude obsahovat název vybrané osoby.

3. Otevřete **ExpenseItHome. XAML. vb** nebo **ExpenseItHome.XAML.cs**.

4. `Click`Kód obslužné rutiny události nahraďte následujícím kódem:

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

#### <a name="to-update-the-ui-with-data-templates"></a>Aktualizace uživatelského rozhraní pomocí šablon dat

1. Otevřete **ExpenseReportPage. XAML**.

2. Kód XAML pro prvky **název** a **oddělení** nahraďte `<StackPanel` následujícím kódem:

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

     Tato vlastnost váže ovládací prvky **Label** na příslušné vlastnosti zdroje dat.

3. Do elementu přidejte následující kód XAML `<Grid>` :

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

     To definuje, jak zobrazit data sestavy výdajů.

4. Nahraďte `<DataGrid>` prvek následujícím:

    ```xaml
    <!-- Expense type and Amount table -->
    <DataGrid ItemsSource="{Binding XPath=Expense}" ColumnHeaderStyle="{StaticResource columnHeaderStyle}" AutoGenerateColumns="False" RowHeaderWidth="0" >

        <DataGrid.Columns>
            <DataGridTextColumn Header="ExpenseType" Binding="{Binding XPath=@ExpenseType}"  />
            <DataGridTextColumn Header="Amount" Binding="{Binding XPath=@ExpenseAmount}" />
        </DataGrid.Columns>

    </DataGrid>
    ```

     Tím přidáte **vlastnost ItemSource** a definujete vazby pro položky výdajů.

5. Sestavte a spusťte aplikaci.

6. Zvolte osobu a pak klikněte na tlačítko **Zobrazit** .

     Následující ilustrace znázorňuje obě stránky aplikace ExpenseIt s ovládacími prvky, rozložením, styly, datovými vazbami a použitými šablonami dat.

     ![Snímky obrazovky ukázek ExpenseIt](../designers/media/gettingstartedfigure5.png "GettingStartedFigure5")

## <a name="best-practices"></a><a name="Best_Practices"></a> Osvědčené postupy
 Tato ukázka demonstruje základy WPF a v důsledku toho nedodržuje Doporučené postupy pro vývoj aplikací. Pro zajištění komplexního pokrytí osvědčených postupů pro vývoj aplikací WPF a .NET Framework můžete podle potřeby zobrazit následující témata:

- Usnadnění – [osvědčené postupy usnadnění](https://msdn.microsoft.com/library/aa350483\(v=vs.100\).aspx)

- Zabezpečení- [Windows Presentation Foundation zabezpečení](https://msdn.microsoft.com/library/aa970906\(v=vs.100\).aspx)

- Lokalizace – [Přehled globalizace a lokalizace WPF](https://msdn.microsoft.com/library/ms788718\(v=vs.100\).aspx)

- Výkon – [optimalizace výkonu aplikace WPF](https://msdn.microsoft.com/library/aa970683\(v=vs.100\).aspx)

## <a name="whats-next"></a><a name="Whats_Next"></a> Co dál
 Pro vytvoření desktopové aplikace pomocí WPF máte k dispozici řadu technik. Nyní byste měli mít základní znalosti o stavebních blocích aplikace WPF vázané na data. Toto téma není nijak vyčerpávající, ale snad nyní máte představu o některých možnostech, které byste mohli zjistit, a to nad rámec postupů v tomto tématu.

 Další informace o architektuře a programovacích modelech WPF naleznete v následujících tématech:

- [Architektura WPF](https://msdn.microsoft.com/library/ms750441\(v=vs.100\).aspx)

- [Přehled XAML](https://msdn.microsoft.com/library/ms752059\(v=vs.100\).aspx)

- [Přehled vlastností závislosti](https://msdn.microsoft.com/library/ms752914\(v=vs.100\).aspx)

- [Systém rozložení](https://msdn.microsoft.com/library/ms745058\(v=vs.100\).aspx)

- [– styly a šablony](https://msdn.microsoft.com/library/bb613570\(v=vs.100\).aspx)

  Další informace o vytváření aplikací naleznete v následujících tématech:

- [Přehled vývoje aplikací](https://msdn.microsoft.com/library/bb613549\(v=vs.100\).aspx)

- [Přehled ovládacích prvků](https://msdn.microsoft.com/library/bb613551\(v=vs.100\).aspx)

- [Přehled datových vazeb](https://msdn.microsoft.com/library/ms752347\(v=vs.100\).aspx)

- [Přehled grafiky, animace a multimédií pro WPF](https://msdn.microsoft.com/library/ms742562\(v=vs.100\).aspx)

- [Dokumenty v platformě WPF](https://msdn.microsoft.com/library/ms748388\(v=vs.100\).aspx)

## <a name="see-also"></a>Viz také
 [Návod: vytvoření desktopové aplikace WPF připojené k mobilní službě Azure](../designers/walkthrough-create-a-wpf-desktop-application-connected-to-an-azure-mobile-service.md) [Vytvoření moderních aplikací klasické pracovní plochy pomocí Windows Presentation Foundation](../designers/create-modern-desktop-applications-with-windows-presentation-foundation.md)
