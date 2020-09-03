---
title: 'Návod: vytvoření desktopové aplikace WPF připojené k mobilní službě Azure | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-designers
ms.topic: conceptual
ms.assetid: 8d42620f-553b-4b04-a38b-f6b306d73a50
caps.latest.revision: 9
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 624fffb9c86a7ad874f27797dfd5251c8585870f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "72664030"
---
# <a name="walkthrough-create-a-wpf-desktop-application-connected-to-an-azure-mobile-service"></a>Návod: Vytvoření desktopové aplikace WPF připojené ke službě Azure Mobile
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Pomocí Windows Presentation Foundation (WPF) můžete rychle vytvořit moderní desktopovou aplikaci, která používá mobilní službu Azure k ukládání a poskytování dat.

## <a name="prerequisites"></a><a name="Requirements"></a> Požadovaný
 K dokončení tohoto Názorného postupu budete potřebovat následující:

- Visual Studio 2015 – jakákoli verze, která podporuje vývoj WPF.

- Aktivní účet Microsoft Azure.

  - [Zde](https://azure.microsoft.com/pricing/free-trial/)si můžete zaregistrovat bezplatný zkušební účet.

  - Můžete aktivovat [výhody pro předplatitele MSDN](https://azure.microsoft.com/pricing/member-offers/msdn-benefits-details/?WT.mc_id=A261C142F). Díky předplatnému MSDN každý měsíc získáváte kredity, které můžete použít pro placené služby Azure.

## <a name="create-a-project-and-add-references"></a>Vytvořit projekt a přidat odkazy
 Prvním krokem je vytvoření projektu WPF a přidání balíčku NuGet, který vám umožní připojit se k Azure Mobile Services.

#### <a name="to-create-the-project"></a>Vytvoření projektu

1. Na panelu nabídek vyberte položku **soubor**, **Nový**, **projekt**.

2. V dialogovém okně **Nový projekt** rozbalte uzel **Visual C#** nebo **Visual Basic** a zvolte uzel **Windows** a potom rozbalte uzel **Windows** a zvolte **klasický desktopový** uzel.

3. V seznamu šablon vyberte šablonu **aplikace WPF** .

4. Do textového pole **název** zadejte `WPFQuickStart` a pak klikněte na tlačítko **OK** .

     Projekt je vytvořen a jsou přidány soubory projektu do **Průzkumník řešení**a zobrazí se Návrhář pro výchozí okno aplikace s názvem **MainWindow. XAML** .

#### <a name="to-add-a-reference-to-the-windows-azure-mobile-services-sdk"></a>Přidání odkazu do sady Windows Azure Mobile Services SDK

1. V **Průzkumník řešení**otevřete místní nabídku uzlu **odkazy** a vyberte možnost **Spravovat balíčky NuGet**.

2. Ve **Správci balíčků NuGet**vyberte **vyhledávací** pole a zadejte `mobileservices` .

3. V levém podokně zvolte **windowsazure. MobileServices**a potom v pravém podokně klikněte na tlačítko **nainstalovat** .

    > [!NOTE]
    > Pokud se zobrazí dialogové okno **Náhled** , zkontrolujte navrhované změny a pak klikněte na tlačítko **OK** .

4. V dialogu **přijetí licence** si přečtěte licenční podmínky a pak je **přijměte kliknutím na tlačítko Souhlasím** .

     Nezbytné odkazy budou přidány do **Průzkumník řešení**.

    > [!NOTE]
    > Pokud s licenčními podmínkami nesouhlasíte, klikněte na tlačítko **odmítnout** . Nebudete moct dokončit zbytek tohoto návodu.

## <a name="create-the-user-interface"></a>Vytvoření uživatelského rozhraní
 Dalším krokem je vytvoření uživatelského rozhraní pro aplikaci. Nejprve vytvoříte opakovaně použitelný uživatelský ovládací prvek, který zobrazí standardní rozložení vedle sebe. Přidáte uživatelský ovládací prvek do okna hlavní aplikace a přidáte ovládací prvky pro zadávání a zobrazování dat a pak napíšete nějaký kód pro definování interakce s back-endu mobilní služby.

#### <a name="to-add-a-user-control"></a>Přidání uživatelského ovládacího prvku

1. V **Průzkumník řešení**otevřete místní nabídku uzlu **WPFQuickStart** a vyberte **Přidat**, **Nová složka**.

2. Pojmenujte složku `Common` .

3. Otevřete místní nabídku pro složku **Common** a vyberte možnost **Přidat**, **uživatelský ovládací prvek**.

4. V dialogovém okně **Přidat novou položku** zvolte pole název a zadejte a `QuickStartTask` pak klikněte na tlačítko **Přidat** .

     Uživatelský ovládací prvek se přidá do projektu a otevře se soubor **QuickStartTask. XAML** v návrháři.

5. V dolním podokně návrháře vyberte `<Grid>` `</Grid>` značky a a nahraďte je následujícím kódem XAML:

    ```xaml
    <Grid VerticalAlignment="Top">
            <StackPanel Orientation="Horizontal">
                <Border BorderThickness="0,0,1,0" BorderBrush="DarkGray" Margin="0,10" MinWidth="70">
                    <TextBlock Text="{Binding Number}" FontSize="45" Foreground="DarkGray" Margin="20,0"/>
                </Border>
                <StackPanel>
                    <TextBlock Text="{Binding Title}" Margin="10,10,0,0" FontSize="16" FontWeight="Bold" />
                    <TextBlock Text="{Binding Description}" Margin="10,0,0,0" TextWrapping="Wrap" MaxWidth="500" />
                </StackPanel>
            </StackPanel>
        </Grid>
    ```

     Tento kód XAML vytvoří opakovaně použitelné rozložení se zástupnými symboly pro pole číslo, název a popis. V době spuštění mohou být zástupné symboly nahrazeny textem, jak je znázorněno na následujícím obrázku.

     ![Uživatelský ovládací prvek QuickStartTask](../designers/media/wpfquickstart1.PNG "WPFQuickStart1")

6. V **Průzkumník řešení**rozbalte uzel **QuickStartTask. XAML** a otevřete soubor **QuickStartTask.XAML.cs** nebo **QuickStartTask. XAML. vb** .

7. V editoru kódu nahraďte `namespace WPFQuickStart.Common` obor názvů (C#) nebo `Public Class QuickStartTask` (VB) metodou následujícím kódem:

    ```csharp
    namespace WPFQuickStart.Common
    {
        /// <summary>
        /// Interaction logic for QuickStartTask.xaml
        /// </summary>
        public partial class QuickStartTask : UserControl
        {
            public QuickStartTask()
            {
                this.InitializeComponent();
                this.DataContext = this;
            }

            public int Number
            {
                get { return (int)GetValue(NumberProperty); }
                set { SetValue(NumberProperty, value); }
            }

            // Using a DependencyProperty as the backing store for Number.  This enables animation, styling, binding, etc...
            public static readonly DependencyProperty NumberProperty =
                DependencyProperty.Register("Number", typeof(int), typeof(QuickStartTask), new PropertyMetadata(0));

            public string Title
            {
                get { return (string)GetValue(TitleProperty); }
                set { SetValue(TitleProperty, value); }
            }

            // Using a DependencyProperty as the backing store for Title.  This enables animation, styling, binding, etc...
            public static readonly DependencyProperty TitleProperty =
                DependencyProperty.Register("Title", typeof(string), typeof(QuickStartTask), new PropertyMetadata(default(string)));

            public string Description
            {
                get { return (string)GetValue(DescriptionProperty); }
                set { SetValue(DescriptionProperty, value); }
            }

            // Using a DependencyProperty as the backing store for Description.  This enables animation, styling, binding, etc...
            public static readonly DependencyProperty DescriptionProperty =
                DependencyProperty.Register("Description", typeof(string), typeof(QuickStartTask), new PropertyMetadata(default(string)));
        }
    }
    ```

    ```vb
    Partial Public Class QuickStartTask
            Inherits UserControl

            Public Sub New()
                Me.InitializeComponent()
                Me.DataContext = Me
            End Sub

            Public Property Number() As Integer
                Get
                    Return CInt(Fix(GetValue(NumberProperty)))
                End Get
                Set(ByVal value As Integer)
                    SetValue(NumberProperty, value)
                End Set
            End Property

            ' Using a DependencyProperty as the backing store for Number.  This enables animation, styling, binding, etc...
            Public Shared ReadOnly NumberProperty As DependencyProperty = DependencyProperty.Register("Number", GetType(Integer), GetType(QuickStartTask), New PropertyMetadata(0))

            Public Property Title() As String
                Get
                    Return CStr(GetValue(TitleProperty))
                End Get
                Set(ByVal value As String)
                    SetValue(TitleProperty, value)
                End Set
            End Property

            ' Using a DependencyProperty as the backing store for Title.  This enables animation, styling, binding, etc...
            Public Shared ReadOnly TitleProperty As DependencyProperty = DependencyProperty.Register("Title", GetType(String), GetType(QuickStartTask), New PropertyMetadata(Nothing))

            Public Property Description() As String
                Get
                    Return CStr(GetValue(DescriptionProperty))
                End Get
                Set(ByVal value As String)
                    SetValue(DescriptionProperty, value)
                End Set
            End Property

            ' Using a DependencyProperty as the backing store for Description.  This enables animation, styling, binding, etc...
            Public Shared ReadOnly DescriptionProperty As DependencyProperty = DependencyProperty.Register("Description", GetType(String), GetType(QuickStartTask), New PropertyMetadata(Nothing))
        End Class
    ```

     Tento kód používá vlastnosti závislosti k nastavení hodnot pro pole číslo, název a popis v době běhu.

8. Na panelu nabídek vyberte **sestavení**, **sestavit WPFQuickStart** a sestavte uživatelský ovládací prvek.

#### <a name="to-create-and-modify-the-main-window"></a>Vytvoření a úprava hlavního okna

1. V **Průzkumník řešení**otevřete soubor **MainWindow. XAML** .

2. **Důležité**informace. Tento krok je jenom pro C#. Pokud používáte Visual Basic, přejděte k dalšímu kroku. V dolním podokně návrháře Najděte řádek `xmlns:local=”clr-namespace:WPFQuickStart”` a nahraďte ho následujícím kódem XAML:

    ```xaml
    xmlns:local=”clr-namespace:WPFQuickStart.Common”
    ```

3. V okně **vlastnosti** rozbalte uzel **společná** kategorie a zvolte vlastnost **název** a potom zadejte a stiskněte klávesu `WPF Todo List` **ENTER** .

     Všimněte si, že se element **title** v okně XAML změní tak, aby odpovídal nové hodnotě. Vlastnosti XAML lze upravit buď v okně XAML, nebo v okně **vlastnosti** , a změny budou synchronizovány.

4. V okně XAML nastavte hodnotu prvku **Height** na `768` a nastavte hodnotu vlastnosti **Width** na `1280` .

     Tyto prvky odpovídají vlastnostem **Výška** a **Šířka** , které se nacházejí v kategorii **rozložení** v okně **vlastnosti** .

5. Vyberte `<Grid>` značky a `</Grid>` a nahraďte je následujícím kódem XAML:

    ```xaml
    <Grid>

            <Grid Margin="50,50,10,10">
                <Grid.ColumnDefinitions>
                    <ColumnDefinition Width="*" />
                    <ColumnDefinition Width="*" />
                </Grid.ColumnDefinitions>
                <Grid.RowDefinitions>
                    <RowDefinition Height="Auto" />
                    <RowDefinition Height="*" />
                </Grid.RowDefinitions>

                <Grid Grid.Row="0" Grid.ColumnSpan="2" Margin="0,0,0,20">
                    <StackPanel>
                        <TextBlock Foreground="#0094ff" FontFamily="Segoe UI Light" Margin="0,0,0,6">MICROSOFT AZURE MOBILE SERVICES</TextBlock>
                        <TextBlock Foreground="Gray" FontFamily="Segoe UI Light" FontSize="45" ><Run Text="My Todo List"/></TextBlock>
                    </StackPanel>
                </Grid>

                <Grid Grid.Row="1">
                    <StackPanel>

                        <local:QuickStartTask Number="1" Title="Insert a TodoItem" Description="Enter some text below and click Save to insert a new todo item into the list." />

                        <StackPanel Orientation="Horizontal" Margin="72,0,0,0">
                            <TextBox x:Name="TodoInput" Margin="5" MinWidth="300"/>
                            <Button x:Name="ButtonSave" Click="ButtonSave_Click" Content="Save"/>
                        </StackPanel>

                    </StackPanel>
                </Grid>

                <Grid Grid.Row="1" Grid.Column="1">
                    <Grid.RowDefinitions>
                        <RowDefinition Height="Auto" />
                        <RowDefinition />
                    </Grid.RowDefinitions>
                    <StackPanel>
                        <local:QuickStartTask Number="2" Title="Query and Update Data" Description="Click the Refresh button to load the unfinished TodoItems from the Azure Mobile Service. Select the checkbox to mark a ToDo item as complete and update the list." />
                        <Button Margin="72,0,0,0" Name="ButtonRefresh" Click="ButtonRefresh_Click">Refresh</Button>
                    </StackPanel>

                    <ListView Name="ListItems" Margin="62,10,0,0" Grid.Row="1">
                        <ListView.ItemTemplate>
                            <DataTemplate>
                                <StackPanel Orientation="Horizontal">
                                    <CheckBox Name="CheckBoxComplete" IsChecked="{Binding Complete, Mode=TwoWay}" Checked="CheckBoxComplete_Checked" Content="{Binding Text}" Margin="10,5" VerticalAlignment="Center"/>
                                </StackPanel>
                            </DataTemplate>
                        </ListView.ItemTemplate>
                    </ListView>

                </Grid>

            </Grid>
        </Grid>
    ```

     Všimněte si, že se změny projeví v okně návrh. Znovu můžete také definovat uživatelské rozhraní přidáním ovládacích prvků z okna **panelu nástrojů** a nastavením vlastností v okně **vlastnosti** . Cokoli, co je možné provést v návrháři, lze provést v kódu XAML a naopak.

     V tomto okamžiku by měl návrh vypadat jako na následujícím obrázku.

     ![MainWindow v Návrháři](../designers/media/wpfquickstart2.PNG "WPFQuickStart2")

    > [!NOTE]
    > Po následujících několika postupech se mohou v **Seznam chyb** , pokud je otevřená, zobrazit chyby. Nedělejte si starosti; Tyto chyby budou po dokončení zbývajících postupů pryč.

6. V **Průzkumník řešení**rozbalte uzel **MainWindow. XAML** a otevřete soubor **MainWindow.XAML.cs** nebo **MainWindow. XAML. vb** .

7. V editoru kódu na začátek souboru přidejte následující `using` `Imports` direktivy nebo:

    ```csharp
    using Microsoft.WindowsAzure.MobileServices;
    using Newtonsoft.Json;
    ```

    ```vb
    Imports Microsoft.WindowsAzure.MobileServices
    Imports Newtonsoft.Json
    ```

8. Nahraďte celý kód v oboru názvů **WPFQuickStart** (C#) nebo třídy **MAINWINDOW** třídy (VB) následujícím kódem:

    ```csharp
    namespace WPFQuickStart
    {
        /// <summary>
        /// Interaction logic for MainWindow.xaml
        /// </summary>
        public class TodoItem
        {
            public string Id { get; set; }

            [JsonProperty(PropertyName = "text")]
            public string Text { get; set; }

            [JsonProperty(PropertyName = "complete")]
            public bool Complete { get; set; }
        }

        public partial class MainWindow : Window
        {
            private MobileServiceCollection<TodoItem, TodoItem> items;
            private IMobileServiceTable<TodoItem> todoTable = App.MobileService.GetTable<TodoItem>();

            public MainWindow()
            {
                InitializeComponent();
            }

            private async void InsertTodoItem(TodoItem todoItem)
            {
                // This code inserts a new TodoItem into the database. When the operation completes
                // and Mobile Services has assigned an Id, the item is added to the CollectionView
                await todoTable.InsertAsync(todoItem);
                items.Add(todoItem);
            }

            private async void RefreshTodoItems()
            {
                try
                {
                    // This code refreshes the entries in the list view by querying the TodoItem table.
                    // The query excludes completed TodoItems
                    items = await todoTable
                        .Where(todoItem => todoItem.Complete == false)
                        .ToCollectionAsync();
                    ListItems.ItemsSource = items;
                }
                catch (MobileServiceInvalidOperationException e)
                {
                    MessageBox.Show(e.Message, "Error loading items");
                }
            }

            private async void UpdateCheckedTodoItem(TodoItem item)
            {
                // This code takes a freshly completed TodoItem and updates the database. When the MobileService
                // responds, the item is removed from the list
                await todoTable.UpdateAsync(item);
                items.Remove(item);
            }

            private void ButtonRefresh_Click(object sender, RoutedEventArgs e)
            {
                RefreshTodoItems();
            }

            private void ButtonSave_Click(object sender, RoutedEventArgs e)
            {
                var todoItem = new TodoItem { Text = TodoInput.Text };
                InsertTodoItem(todoItem);
                TodoInput.Text = "";
            }

            private void CheckBoxComplete_Checked(object sender, RoutedEventArgs e)
            {
                CheckBox cb = (CheckBox)sender;
                TodoItem item = cb.DataContext as TodoItem;
                UpdateCheckedTodoItem(item);
            }

            protected override void OnActivated(EventArgs e)
            {
                RefreshTodoItems();
            }
        }

    }
    ```

    ```vb
    Public Class TodoItem
        Public Property Id() As String

        <JsonProperty(PropertyName:="text")>
        Public Property Text() As String

        <JsonProperty(PropertyName:="complete")>
        Public Property Complete() As Boolean
    End Class

    Partial Public Class MainWindow
        Inherits Window

        Private items As MobileServiceCollection(Of TodoItem, TodoItem)
        Private todoTable As IMobileServiceTable(Of TodoItem) = Application.MobileService.GetTable(Of TodoItem)()

        Public Sub New()
            InitializeComponent()
        End Sub

        Private Async Sub InsertTodoItem(ByVal todoItem As TodoItem)
            ' This code inserts a new TodoItem into the database. When the operation completes
            ' and Mobile Services has assigned an Id, the item is added to the CollectionView
            Await todoTable.InsertAsync(todoItem)
            items.Add(todoItem)
        End Sub

        Private Async Sub RefreshTodoItems()
            Dim exception As MobileServiceInvalidOperationException = Nothing
            Try
                ' This code refreshes the entries in the list view by querying the TodoItem table.
                ' The query excludes completed TodoItems
                items = Await todoTable.Where(Function(todoItem) todoItem.Complete = False).ToCollectionAsync()
            Catch e As MobileServiceInvalidOperationException
                exception = e
            End Try

            If exception IsNot Nothing Then
                MessageBox.Show(exception.Message, "Error loading items")
            Else
                ListItems.ItemsSource = items
            End If
        End Sub

        Private Async Sub UpdateCheckedTodoItem(ByVal item As TodoItem)
            ' This code takes a freshly completed TodoItem and updates the database. When the MobileService
            ' responds, the item is removed from the list
            Await todoTable.UpdateAsync(item)
            items.Remove(item)
        End Sub

        Private Sub ButtonRefresh_Click(ByVal sender As Object, ByVal e As RoutedEventArgs)
            RefreshTodoItems()
        End Sub

        Private Sub ButtonSave_Click(ByVal sender As Object, ByVal e As RoutedEventArgs)
            Dim todoItem = New TodoItem With {.Text = TodoInput.Text}
            InsertTodoItem(todoItem)
            TodoInput.Text = ""
        End Sub

        Private Sub CheckBoxComplete_Checked(ByVal sender As Object, ByVal e As RoutedEventArgs)
            Dim cb As CheckBox = DirectCast(sender, CheckBox)
            Dim item As TodoItem = TryCast(cb.DataContext, TodoItem)
            UpdateCheckedTodoItem(item)
        End Sub

        Protected Overrides Sub OnActivated(ByVal e As EventArgs)
            RefreshTodoItems()
        End Sub
    End Class
    ```

     Tento kód definuje interakci mezi uživatelským rozhraním a databází v mobilní službě pomocí asynchronních metod.

## <a name="create-the-azure-mobile-service"></a>Vytvoření mobilní služby Azure
 Posledním krokem je vytvoření mobilní služby v Microsoft Azure, přidání tabulky pro uložení dat a následného odkazování instance služby z vaší aplikace.

#### <a name="to-create-a-mobile-service"></a>Vytvoření mobilní služby

1. Otevřete webový prohlížeč a přihlaste se ke svému portál Microsoft Azure a pak zvolte kartu **Mobile Services** .

2. Klikněte na tlačítko **Nový** a v okně místní nabídky vyberte **COMPUTE**, **mobilní služba, vytvořit**.

3. V dialogovém okně **Nová mobilní služba** klikněte na textové pole **adresy URL** a zadejte `wpfquickstart01` .

    > [!NOTE]
    > Možná budete muset změnit číselnou část adresy URL. Microsoft Azure vyžaduje pro každou mobilní službu jedinečnou adresu URL.

     Tím se nastaví adresa URL služby na `https://wpfquickstart01.azure-mobile.net/` .

4. V seznamu **databáze** vyberte možnost databáze. Vzhledem k tomu, že se jedná o aplikaci, která pravděpodobně nezíská spoustu využití, možná budete chtít vybrat možnost **vytvořit bezplatnou databázi SQL 20MB** nebo zvolit bezplatnou databázi, která je už přidružená k vašemu předplatnému.

5. V seznamu **oblast** vyberte datové centrum, kam chcete mobilní službu nasadit, a pak klikněte na tlačítko **Další** (šipka doprava).

    > [!NOTE]
    > Pro tuto službu použijete výchozí nastavení **back-endu** **JavaScript**.

6. Pokud vytváříte novou databázi, na stránce **zadat nastavení databáze** vyberte v seznamu **Server** možnost **Nový server služby SQL Database**, zadejte své **přihlašovací jméno** a **heslo**SQL a pak klikněte na tlačítko **úplné** (zaškrtnutí).

7. Pokud jste zvolili existující databázi, zadejte na stránce **nastavení databáze** **přihlašovací heslo** a pak klikněte na tlačítko **úplné** (zaškrtnutí).

     Spustí se proces vytváření mobilní služby. Až se proces dokončí, stav se změní na **připravený** a můžete přejít k dalšímu kroku.

8. Na portálu vyberte nově vytvořenou mobilní službu a pak klikněte na tlačítko **spravovat klíče** .

9. V dialogovém okně **Správa přístupových klíčů** zkopírujte **klíč aplikace**.

     Použijete ho v dalším postupu.

#### <a name="to-create-a-table"></a>Vytvoření tabulky

1. V portál Microsoft Azure klikněte na šipku vpravo vedle názvu mobilní služby a v řádku nabídek zvolte **data**a pak zvolte odkaz **Přidat tabulku** .

2. V dialogovém okně **vytvořit novou tabulku** zadejte do TEXTOVÉHO pole **název tabulky** `TodoItem` a pak klikněte na tlačítko **úplné** (zaškrtnutí).

     Počkejte na vytvoření tabulky a potom přejděte k poslednímu postupu.

#### <a name="to-add-a-declaration-for-the-mobile-service"></a>Přidání deklarace pro mobilní službu

1. Vraťte se do sady Visual Studio. V **Průzkumník řešení**rozbalte uzel **App. XAML** (C#) nebo **Application. XAML** (Visual Basic) a otevřete soubor **App.XAML.cs** nebo **App. XAML. vb** .

2. V editoru kódu přidejte následující `using` direktivy nebo **importy** do horní části souboru:

    ```csharp
    using Microsoft.WindowsAzure.MobileServices;
    ```

    ```vb
    Imports Microsoft.WindowsAzure.MobileServices
    ```

3. Přidejte do třídy následující deklaraci, nahraďte *SERVICE_HERE* názvem adresy URL vaší služby a NAHRAĎte *klíčovou* zkratkou aplikace, kterou jste zkopírovali v předchozím postupu:

    ```csharp
    public static MobileServiceClient MobileService = new MobileServiceClient(
                 "https://YOUR-SERVICE-HERE.azure-mobile.net/",
                 "YOUR-KEY-HERE"
             );
    ```

    ```vb
    Public Shared MobileService As New MobileServiceClient("https://YOUR-SERVICE-HERE.azure-mobile.net/", "YOUR-KEY-HERE")
    ```

     Tento kód umožňuje aplikaci přístup k mobilní službě spuštěné v Microsoft Azure.

## <a name="test-the-application"></a>Testování aplikace
 To je to – vytvořili jste desktopovou aplikaci WPF, která přistupuje k mobilní službě Azure. Vše, co zbývá, je spuštění aplikace a její zobrazení v akci.

#### <a name="to-run-the-application"></a>Spuštění aplikace

1. Na panelu nabídek zvolte položku **ladit**, **Spustit ladění** (nebo stiskněte klávesu F5).

2. Do textového pole **Vložit TodoItem** zadejte `Do something` a pak klikněte na tlačítko **Uložit** .

3. Zadejte `Do something else` a pak znovu klikněte na tlačítko **Uložit** .

     Všimněte si, že dvě položky jsou přidány do seznamu **dotaz a aktualizace dat** , jak je znázorněno na následujícím obrázku.

     ![Položky ToDo se přidají do seznamu.](../designers/media/wpfquickstart3.PNG "WPFQuickStart3")

4. Zaškrtněte políčko pro položku **dělat něco jiného** v seznamu.

     Tím se zavolá metoda **UpdateCheckedTodoItem** a odebere se položka ze seznamu i databáze.

## <a name="next-steps"></a>Další kroky
 Dokončili jste poměrně zjednodušený příklad desktopové aplikace WPF s back-endu Azure. Skutečná aplikace je samozřejmě pravděpodobně mnohem složitější, ale platí stejné základní koncepty. Viz [WPF v .NET Framework](https://msdn.microsoft.com/library/ms754130\(v=vs.100\).aspx).

 Přidáním barev, tvarů, grafiky a dokonce animací můžete nastavit lepší přitažlivost uživatelského rozhraní. Viz [Návrh XAML v aplikaci Visual Studio a Blend pro Visual Studio](../designers/designing-xaml-in-visual-studio.md).

 Pomocí Azure Mobile Services se můžete připojit k existujícím databázím SQL nebo jiným zdrojům dat. Viz [dokumentace Mobile Services](https://azure.microsoft.com/services/app-service/mobile/).

## <a name="see-also"></a>Viz také
 [Návod: Moje první desktopová aplikace WPF](../designers/walkthrough-my-first-wpf-desktop-application2.md) [vytvoří moderní aplikace klasické pracovní plochy pomocí Windows Presentation Foundation](../designers/create-modern-desktop-applications-with-windows-presentation-foundation.md)
