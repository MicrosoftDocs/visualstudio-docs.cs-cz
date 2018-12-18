---
title: 'Návod: Vytvoření aplikace WPF plochy připojené k mobilní službě Azure | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 8d42620f-553b-4b04-a38b-f6b306d73a50
caps.latest.revision: 9
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 9ab2c5bbea358c226407ba83e2a367195ecfef06
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/12/2018
ms.locfileid: "49270606"
---
# <a name="walkthrough-create-a-wpf-desktop-application-connected-to-an-azure-mobile-service"></a>Návod: Vytvoření aplikace WPF plochy připojené k mobilní službě Azure
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Windows Presentation Foundation (WPF) můžete rychle vytvářet moderní aplikace, která používá Azure Mobile Service k ukládání a poskytují data.  
  
##  <a name="Requirements"></a> Požadované součásti  
 Následující příkaz pro dokončení tohoto návodu budete potřebovat:  
  
-   Visual Studio 2015 – všechny verze, která podporuje vývoj WPF.  
  
-   Aktivní účet Microsoft Azure.  
  
    -   Si můžete zaregistrovat Bezplatný zkušební účet [tady](http://azure.microsoft.com/pricing/free-trial/).  
  
    -   Můžete si aktivovat [výhody pro předplatitele MSDN](https://azure.microsoft.com/pricing/member-offers/msdn-benefits-details/?WT.mc_id=A261C142F). Vaše předplatné MSDN vám dává kredity každý měsíc, můžete použít k placení za služby Azure.  
  
## <a name="create-a-project-and-add-references"></a>Vytvořte projekt a přidejte odkazy  
 Prvním krokem je vytvoření projektu WPF a přidání balíčku NuGet, který vám umožní připojit se k mobilním službám Azure.  
  
#### <a name="to-create-the-project"></a>Vytvoření projektu  
  
1.  V panelu nabídky zvolte **souboru**, **nový**, **projektu**.  
  
2.  V **nový projekt** dialogového okna, rozbalte buď **Visual C#** nebo **jazyka Visual Basic** uzlu a zvolte **Windows** uzel a potom rozbalte **Windows** uzlu a zvolte **klasický desktopový** uzlu.  
  
3.  V seznamu šablon vyberte **aplikace WPF** šablony.  
  
4.  V **název** textového pole zadejte `WPFQuickStart`a klikněte na tlačítko **OK** tlačítko.  
  
     Vytvoření projektu a soubory projektu jsou přidány do **Průzkumníka řešení**a otevře se návrhář pro výchozí okno aplikace s názvem **souboru MainWindow.xaml** se zobrazí.  
  
#### <a name="to-add-a-reference-to-the-windows-azure-mobile-services-sdk"></a>Chcete-li přidat odkaz na Windows Azure Mobile Services SDK  
  
1.  V **Průzkumníka řešení**, otevřete místní nabídku **odkazy** uzlu a zvolte **spravovat balíčky NuGet**.  
  
2.  V **Správce balíčků NuGet**, zvolte **hledání** pole a zadejte `mobileservices`.  
  
3.  V levém podokně vyberte **WindowsAzure.MobileServices**a poté v pravém podokně vyberte **nainstalovat** tlačítko.  
  
    > [!NOTE]
    >  Pokud **ve verzi Preview** se zobrazí dialogové okno, projděte si navrhované změny a klikněte na tlačítko **OK** tlačítko.  
  
4.  V **přijetí licence** dialogové okno, zkontrolujte licenční podmínky a přijměte je kliknutím **souhlasím** tlačítko.  
  
     Přidá potřebné odkazy do **Průzkumníka řešení**.  
  
    > [!NOTE]
    >  Pokud nesouhlasíte s licenčními podmínkami, zvolte **nesouhlasím** tlačítko. Nebudete moct dokončit zbytek návodu.  
  
## <a name="create-the-user-interface"></a>Vytvoření uživatelského rozhraní  
 Dalším krokem je vytvoření uživatelského rozhraní pro aplikaci. Nejdřív vytvoříte opakovaně použitelné uživatelský ovládací prvek, který zobrazí standardní vedle sebe dva podokno rozložení. Budete přidat uživatelský ovládací prvek do hlavního okna aplikace a přidat ovládací prvky k zadávání a zobrazování dat a napsání kódu pro definování interakci s back-end mobilní službě.  
  
#### <a name="to-add-a-user-control"></a>Chcete-li přidat uživatelský ovládací prvek  
  
1.  V **Průzkumníka řešení**, otevřete místní nabídku **WPFQuickStart** uzlu a zvolte **přidat**, **novou složku**.  
  
2.  Název složky `Common`.  
  
3.  Otevřete místní nabídku **běžné** složky a vyberte **přidat**, **uživatelský ovládací prvek**.  
  
4.  V **přidat novou položku** dialogového okna, vyberte název pole a zadejte `QuickStartTask`a klikněte na tlačítko **přidat** tlačítko.  
  
     Uživatelský ovládací prvek se přidá do projektu a **QuickStartTask.xaml** soubor se otevře v návrháři.  
  
5.  V dolním podokně návrháře, vyberte `<Grid>` a `</Grid>` značek a nahraďte následující kód XAML:  
  
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
  
     Tento kód XAML vytvoří opakovaně použitelné rozložení se zástupnými symboly pro číslo, název a popis pole. Jak je znázorněno na následujícím obrázku, lze v době běhu nahradit zástupné symboly textem.  
  
     ![Uživatelský ovládací prvek QuickStartTask](../designers/media/wpfquickstart1.PNG "WPFQuickStart1")  
  
6.  V **Průzkumníka řešení**, rozbalte **QuickStartTask.xaml** uzlu a otevřít **QuickStartTask.xaml.cs** nebo **QuickStartTask.xaml.vb**souboru.  
  
7.  V editoru kódu nahraďte `namespace WPFQuickStart.Common` obor názvů (C#) nebo `Public Class QuickStartTask` – metoda (VB) následujícím kódem:  
  
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
  
     Tento kód používá k nastavení hodnot pro pole číslo, název a popis v době běhu vlastnosti závislosti.  
  
8.  V panelu nabídky zvolte **sestavení**, **sestavení WPFQuickStart** k vytvoření uživatelského ovládacího prvku.  
  
#### <a name="to-create-and-modify-the-main-window"></a>K vytvoření a úprava hlavního okna  
  
1.  V **Průzkumníka řešení**, otevřete **souboru MainWindow.xaml** souboru.  
  
2.  **Důležité**. Tento krok je k dispozici pouze pro jazyk C#. Pokud používáte Visual Basic, přejděte k dalšímu kroku. V dolním podokně návrháře, vyhledejte řádek `xmlns:local=”clr-namespace:WPFQuickStart”` a nahraďte ho následujícím kódem XAML:  
  
    ```xaml  
    xmlns:local=”clr-namespace:WPFQuickStart.Common”  
    ```  
  
3.  V **vlastnosti** okna, rozbalte **běžné** kategorie uzlu a zvolte **název** vlastnost a pak zadejte `WPF Todo List` a stiskněte klávesu **Enter**  klíč.  
  
     Všimněte si, že **Title** prvku v XAML okno změní tak, aby odpovídala nové hodnoty. Můžete upravit vlastnosti XAML v okně XAML nebo **vlastnosti** okno a změny se synchronizují.  
  
4.  V okně XAML, nastavte hodnotu **výška** elementu `768`a nastavte hodnotu **šířka** vlastnost `1280`.  
  
     Tyto prvky odpovídají **výška** a **šířka** vlastnosti nalezené v **rozložení** kategorii **vlastnosti** okna.  
  
5.  Vyberte `<Grid>` a `</Grid>` značek a nahraďte následující kód XAML:  
  
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
  
     Všimněte si, že změny se projeví v okně návrhu. Ještě jednou, také může jste definovali uživatelského rozhraní přidáním ovládacích prvků z **nástrojů** okno a nastavení vlastností ve **vlastnosti** okna. Cokoli, co můžete udělat v Návrháři můžete udělat v kódu XAML a naopak.  
  
     V tomto okamžiku návrh by měl vypadat jako na následujícím obrázku.  
  
     ![Hlavní okno MainWindow v návrháři](../designers/media/wpfquickstart2.PNG "WPFQuickStart2")  
  
    > [!NOTE]
    >  Při dalším několik postupů můžou se zobrazovat chyby v **seznam chyb** Pokud je otevřený. Nedělejte si starosti; Tyto chyby zmizí po dokončení zbývajících postupy.  
  
6.  V **Průzkumníku řešení**, rozbalte **souboru MainWindow.xaml** uzlu a otevřít **MainWindow.xaml.cs** nebo **soubor MainWindow.xaml.vb** souboru.  
  
7.  V editoru kódu přidejte následující `using` nebo `Imports` direktivy do horní části souboru:  
  
    ```csharp  
    using Microsoft.WindowsAzure.MobileServices;  
    using Newtonsoft.Json;   
    ```  
  
    ```vb  
    Imports Microsoft.WindowsAzure.MobileServices  
    Imports Newtonsoft.Json  
    ```  
  
8.  Nahraďte kód v **WPFQuickStart** obor názvů (C#) nebo **třídy hlavního okna MainWindow** třídy (VB) následujícím kódem:  
  
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
  
     Tento kód definuje interakce mezi uživatelského rozhraní a databází v mobilní službě použití asynchronních metod.  
  
## <a name="create-the-azure-mobile-service"></a>Vytvoření mobilní služby Azure  
 Posledním krokem je vytvoření mobilní služby v Microsoft Azure, přidejte tabulku pro ukládání dat a pak odkazovat na instanci služby z vaší aplikace.  
  
#### <a name="to-create-a-mobile-service"></a>K vytvoření mobilní služby  
  
1.  Otevřete webový prohlížeč a přihlaste se k Microsoft Azure portal a klikněte na tlačítko **MOBILE SERVICES** kartu.  
  
2.  Zvolte **nový** a v zobrazeném dialogovém okně tlačítko **COMPUTE**, **mobilní službu, vytvořit**.  
  
3.  V **novou mobilní službu** dialogového okna, vyberte **URL** textového pole a zadejte `wpfquickstart01`.  
  
    > [!NOTE]
    >  Budete muset změnit číselnou část adresy URL. Microsoft Azure vyžaduje jedinečnou adresu URL pro každou mobilní službu.  
  
     Tím se nastaví adresu URL pro službu *https://wpfquickstart01.azure-mobile.net/*.  
  
4.  V **databáze** seznamu, vyberte volbu databáze. Protože jde aplikaci, která pravděpodobně nebude obohatit o spoustu využití, můžete chtít vybrat **vytvořit zdarma 20MB databází SQL database** možnost, nebo vyberte bezplatnou databázi již spojen s vaším předplatným.  
  
5.  V **oblasti** klikněte na položku datové centrum, ve které chcete nasadit na mobilní službu a klikněte na tlačítko **Další** tlačítko (šipka doprava).  
  
    > [!NOTE]
    >  Pro tuto službu budete používat výchozí **back-ENDU** nastavení **JavaScript**.  
  
6.  Pokud vytváříte novou databázi na **nastavení databáze** stránku, **SERVER** seznamu zvolte **nový SQL server database**, zadejte vaše **přihlášení k serveru SQL NÁZEV** a **heslo**a klikněte na tlačítko **Complete** (zaškrtnutí).  
  
7.  Pokud zvolíte existující databázi, na **nastavení databáze** zadejte vaše **PŘIHLAŠOVACÍ heslo** a klikněte na tlačítko **Complete** (zaškrtnutí).  
  
     Vytvoření mobilní služby bude proces. Po dokončení procesu se stav změní na **připravené** , a můžete přejít další krok.  
  
8.  Na portálu vyberte nově vytvořenou mobilní službu a pak klikněte **Správa KLÍČŮ** tlačítko.  
  
9. V **spravovat přístupové klíče** dialogové okno, kopie **klíč aplikace**.  
  
     Toto použijete v dalším postupu.  
  
#### <a name="to-create-a-table"></a>Pokud chcete vytvořit tabulku  
  
1.  Na portálu Microsoft Azure, klikněte na šipku doprava vedle názvu mobilní služby a na řádku nabídek, zvolte **DATA**a klikněte na tlačítko **tabulku A přidat** odkaz.  
  
2.  V **vytvořit novou tabulku** dialogového okna v **název tabulky** textového pole zadejte `TodoItem`a klikněte na tlačítko **Complete** (zaškrtnutí).  
  
     Počkejte tabulka, která má být vytvořen a poté přejít k posledním kroku.  
  
#### <a name="to-add-a-declaration-for-the-mobile-service"></a>Chcete-li přidat deklaraci mobilní služby  
  
1.  Vraťte se do sady Visual Studio. V **Průzkumníka řešení**, rozbalte **App.xaml** (C#) nebo **Application.xaml** uzlu (Visual Basic) a otevřete **App.xaml.cs** nebo  **App.XAML.vb** souboru.  
  
2.  V editoru kódu přidejte následující `using` nebo **importy** direktivy do horní části souboru:  
  
    ```csharp  
    using Microsoft.WindowsAzure.MobileServices;  
    ```  
  
    ```vb  
    Imports Microsoft.WindowsAzure.MobileServices  
    ```  
  
3.  Přidejte následující prohlášení do třídy, nahraďte *YOUR SERVICE_HERE* s názvem adresu URL pro vaši službu a nahrazení *YOUR-KEY-KORENOVA* s klíčem aplikace, který jste zkopírovali v předchozím Postup:  
  
    ```csharp  
    public static MobileServiceClient MobileService = new MobileServiceClient(  
                 "https://YOUR-SERVICE-HERE.azure-mobile.net/",  
                 "YOUR-KEY-HERE"  
             );  
    ```  
  
    ```vb  
    Public Shared MobileService As New MobileServiceClient("https://YOUR-SERVICE-HERE.azure-mobile.net/", "YOUR-KEY-HERE")  
    ```  
  
     Tento kód umožňuje aplikaci přístup k mobilní službě běžící v Microsoft Azure.  
  
## <a name="test-the-application"></a>Testování aplikace  
 To je vše – desktopová aplikace WPF, který přistupuje k mobilní službě Azure jste vytvořili. Nyní je vše, co zbývá ke spuštění aplikace a sledujte v akci.  
  
#### <a name="to-run-the-application"></a>Ke spuštění aplikace  
  
1.  V panelu nabídky zvolte **ladění**, **spustit ladění** (nebo stiskněte klávesu F5).  
  
2.  V **vložení úkolu** textového pole zadejte `Do something`a klikněte na tlačítko **Uložit** tlačítko.  
  
3.  Zadejte `Do something else`a klikněte na tlačítko **Uložit** tlačítko znovu.  
  
     Všimněte si, že jsou přidány dvě položky **dotazů a aktualizace dat** seznamu, jak je znázorněno na následujícím obrázku.  
  
     ![Položky seznamu úkolů jsou přidány do seznamu. ](../designers/media/wpfquickstart3.PNG "WPFQuickStart3")  
  
4.  Zaškrtněte políčko **dělat něco jiného** položky v seznamu.  
  
     Volá **UpdateCheckedTodoItem** metoda a odebere položku ze seznamu a databáze.  
  
## <a name="next-steps"></a>Další kroky  
 Dokončili jste poměrně zjednodušenou příklad desktopová aplikace WPF s back-endu Azure. Samozřejmě aplikace skutečný by mohla být mnohem složitější, ale stejnou základní koncepty platí. Zobrazit [WPF v rozhraní .NET Framework](https://msdn.microsoft.com/library/ms754130\(v=vs.100\).aspx).  
  
 Více přitažlivé uživatelské rozhraní můžete nastavit tak, že přidáte barvy, tvary, grafika a animace. Zobrazit [návrh XAML v sadě Visual Studio a nástroje Blend for Visual Studio](../designers/designing-xaml-in-visual-studio.md).  
  
 Můžete připojit k existující databáze SQL nebo jiných zdrojů dat pomocí Azure Mobile Services. Zobrazit [dokumentace k Mobile Services](http://azure.microsoft.com/services/app-service/mobile/).  
  
## <a name="see-also"></a>Viz také  
 [Návod: Moje první Desktopová aplikace WPF](../designers/walkthrough-my-first-wpf-desktop-application2.md)   
 [Vytvoření moderních desktopových aplikací pomocí Windows Presentation Foundation](../designers/create-modern-desktop-applications-with-windows-presentation-foundation.md)



