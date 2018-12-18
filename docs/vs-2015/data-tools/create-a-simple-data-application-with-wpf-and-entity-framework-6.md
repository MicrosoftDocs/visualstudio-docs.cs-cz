---
title: Vytvoření jednoduché datové aplikace s použitím WPF a Entity Framework 6 | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 65929fab-5d78-4e04-af1e-cf4957f230f6
caps.latest.revision: 25
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: ac3db033b9e8055c28f29d54027df5fadf156742
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49922195"
---
# <a name="create-a-simple-data-application-with-wpf-and-entity-framework-6"></a>Vytvoření jednoduché datové aplikace s použitím WPF a Entity Framework 6
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Tento názorný ukazuje, jak vytvořit základní "formy nad daty" aplikace v sadě Visual Studio s SQL Server LocalDB, Northwind databáze, Entity Framework 6 a Windows Presentation Foundation. Ukazuje, jak provést základní datové vazby seznam podrobnosti zobrazení a také se vlastní "vazby Navigátor" pomocí tlačítka pro "Přesunout na další", "Přesunout na předchozí," "Přesunout na začátek," "přesunout na konec," "Aktualizace" a "Odstranit".  
  
 Tento článek se zaměřuje na pomocí nástrojů data v sadě Visual Studio a nebude pokoušet o vysvětlují základní technologie v libovolnou hloubku. Předpokládá, že máte základní znalosti s XAML, Entity Framework a SQL. Tento příklad také neukazuje architektury MVVM, což je standard pro aplikace WPF. Tento kód však můžete zkopírovat do MVVM aplikace s velmi několik změn.  
  
## <a name="install-and-connect-to-northwind"></a>Nainstalujte a připojte se k Northwind  
 Tento příklad používá SQL Server Express LocalDB a ukázkové databáze Northwind. Ji by měl fungovat s jinými produkty SQL database stejně, pokud zprostředkovatel dat ADO.NET pro tento produkt podporuje rozhraní Entity Framework.  
  
1.  Pokud jste tak dosud neučinili, nainstalujte SQL Server 2014 LocalDB Express 32 bit z [stránce pro stažení SQL serveru edice](https://www.microsoft.com/en-us/server-cloud/Products/sql-server-editions/sql-server-express.aspx).  
  
2.  Instalace ukázkové databáze Northwind podle pokynů uvedených zde: [instalace SQL serveru, ukázkové databáze](../data-tools/install-sql-server-sample-databases.md).  
  
3.  [Přidat nové připojení](../data-tools/add-new-connections.md) pro databáze Northwind.  
  
## <a name="configure-the-project"></a>Konfigurace projektu  
  
1.  V sadě Visual Studio, zvolte **souboru &#124; nový projekt** a vytvořte novou aplikaci WPF C#.  
  
2.  Vedle přidáme balíček NuGet Entity Framework 6. V Průzkumníku řešení vyberte uzel projektu. V hlavní nabídce zvolte **projektu &#124; spravovat balíčky NuGet...**  
  
     ![Spravovat balíčky NuGet v nabídce](../data-tools/media/raddata-vs2015-manage-nuget-packages.png "raddata_vs2015_manage_nuget_packages")  
  
3.  Ve správci balíčků NuGet, klikněte na **Procházet** odkaz. Entity Framework je pravděpodobně hlavní balíček v seznamu. Klikněte na tlačítko **nainstalovat** v pravém podokně a postupujte podle zobrazených výzev. V okně výstupu vám sdělí, po dokončení instalace.  
  
     ![Entity Framework NuGet Package](../data-tools/media/raddata-vs2015-nuget-ef.png "raddata_vs2015_Nuget_EF")  
  
4.  Teď můžeme použít Visual Studio k vytvoření model založený na databázi Northwind.  
  
## <a name="create-the-model"></a>Vytvoření modelu  
  
1. Klikněte pravým tlačítkem na uzel projektu v Průzkumníku řešení a zvolte **přidat &#124; nová položka**. V levém podokně pod uzlem jazyka C# vyberte **Data** a v prostředním podokně vyberte **datový Model Entity ADO.NET**.  
  
    ![Entity Framework Model novou položku projektu](../data-tools/media/raddata-ef-new-project-item.png "raddata EF novou položku projektu")  
  
2. Volání modelu `Northwind_model` a na tlačítko OK. Tím se zobrazí **Průvodce datovým modelem Entity**. Zvolte **EF designeru z databáze** a potom klikněte na tlačítko **Další**.  
  
    ![EF Model z databáze](../data-tools/media/raddata-ef-model-from-database.png "raddata modelu EF z databáze")  
  
3. Na další obrazovce vyberte váš LocalDB Northwind připojení a na **Další**.  
  
4. Na další stránce průvodce zvolíme, které tabulky, uložené procedury a ostatních databázových objektů chcete zahrnout do modelu Entity Framework. Rozbalte uzel dbo ve stromovém zobrazení a zvolte zákazníky, objednávky a podrobnostmi o objednávce. Ponechte zaškrtnuté políčko výchozí hodnoty a klikněte na **Dokončit**.  
  
    ![Zvolit databázové objekty modelu](../data-tools/media/raddata-choose-ef-objects.png "raddata zvolte EF objekty")  
  
5. Průvodce vygeneruje třídy C#, které představují model Entity Framework. Jedná se o prostý staré třídy jazyka C# a jsou co jsme se databind do uživatelského rozhraní WPF. Soubor .edmx popisuje vztahy a další metadata, která přidružuje třídy objektů v databázi.  Soubory .tt jsou šablony T4, které generují kód, které budou fungovat na modelu a uložte změny do databáze. Zobrazí se všechny tyto soubory v Průzkumníku řešení pod uzlem Northwind_model:  
  
    ![Soubory modelu EF v Průzkumníku řešení](../data-tools/media/raddata-solution-explorer-ef-model-files.png "raddata soubory modelu EF Průzkumníka řešení")  
  
    Na plochu návrháře pro soubor .edmx umožňuje změnit některé vlastnosti a vztahy v modelu. Nebudeme použití návrháře v tomto názorném postupu.  
  
6. Soubory .tt jsou pro obecné účely a My potřebujeme jeden z nich pro práci s datovou vazbou WPF, která vyžaduje ObservableCollections upravit.  V Průzkumníku řešení rozbalte uzel Northwind_model, dokud nenajdete Northwind_model.tt. (Ujistěte se, že jste **není** v *. Kontext .tt soubor, který je přímo pod soubor .edmx).  
  
   -   Nahraďte dva výskyty <xref:System.Collections.ICollection> s <xref:System.Collections.ObjectModel.ObservableCollection%601>.  
  
   -   Nahraďte první výskyt <xref:System.Collections.Generic.HashSet%601> s <xref:System.Collections.ObjectModel.ObservableCollection%601> kolem řádku 51. Druhým výskytem HashSet nenahrazují  
  
   -   Nahradit jenom výskyt <xref:System.Collections.Generic> (kolem řádku 334) s <xref:System.Collections.ObjectModel>.  
  
7. Stisknutím klávesy **Ctrl + Shift + B** k sestavení projektu. Po dokončení sestavení jsou viditelné v Průvodci zdroje dat třídy modelu.  
  
   Nyní jsme připraveni k připojení tento model na stránku XAML, jsme mohli zobrazit, přejděte a upravit data.  
  
## <a name="databind-the-model-to-the-xaml-page"></a>DataBind modelu, který má stránky XAML  
 Je možné psát vlastní kód vázání dat, ale je mnohem jednodušší nechte Visual Studio to pro vás udělal.  
  
1.  V hlavní nabídce zvolte **projektu &#124; přidat nový zdroj dat** zobrazíte **Průvodce konfigurací zdroje dat**. Zvolte **objekt** vzhledem k tomu, že jsme připojujete tříd modelu, není pro databázi:  
  
     ![Průvodce konfigurací zdroje dat se zdrojem objekt](../data-tools/media/raddata-data-source-configuration-wizard-with-object-source.png "raddata Průvodce konfigurací zdroje dat se zdrojem objektu")  
  
2.  Vyberte zákazníka.  (Zdrojů pro objednávky budou automaticky generovány z navigační vlastnost objednávky v zákazníka.)  
  
     ![Přidání tříd entit jako zdroje dat](../data-tools/media/raddata-add-entity-classes-as-data-sources.png "raddata Add entity třídy jako zdroje dat")  
  
3.  Klikněte na tlačítko **dokončit**  
  
4.  Přejděte na soubor MainWindow.xaml v zobrazení kódu. Budeme udržovat XAML pro účely tohoto příkladu velmi jednoduché. Změna názvu hlavního okna MainWindow výstižněji a zvýšit jeho výšku a šířku na 600 × 800 teď. Můžete vždycky změnit ji později. Nyní přidejte tyto definice tří řádků do hlavní mřížky, jeden řádek pro navigační tlačítka, jeden pro podrobnosti zákazníka, jeden pro tabulky, který ukazuje jeho objednávky:  
  
    ```xaml  
    <Grid.RowDefinitions>  
               <RowDefinition Height="auto"/>  
               <RowDefinition Height="auto"/>  
               <RowDefinition Height="*"/>  
           </Grid.RowDefinitions>  
    ```  
  
5.  Nyní otevřete soubor MainWindow.xaml, tak, aby se vám zobrazuje v návrháři. To způsobí, že v okně zdroje dat se zobrazí jako možnost okraji okna sady Visual Studio vedle panelu nástrojů. Klikněte na kartu pro otevření okna nebo jinak stisknutím klávesy **Shift + Alt + D** nebo zvolte **zobrazení &#124; ostatní Windows &#124; zdroje dat**. Budeme zobrazit každou vlastnost v třídě zákazníci vlastní jednotlivé textové pole. Nejprve klikněte na šipku v poli se seznamem zákazníci a zvolte **podrobnosti**. Přetáhněte uzel na prostřední části návrhové plochy, tak, aby návrháři ví, že chcete, aby přejděte v prostředním.  Pokud někam ho nezaložili můžete později ručně v XAML řádku. Ve výchozím nastavení ovládací prvky jsou umístěny ve svislém směru v elementu mřížky, ale v tomto okamžiku je možné uspořádat je však chcete ve formuláři.  Například může mít smysl vložit do textového pole název v horní části výše adresu. Ukázková aplikace pro účely tohoto článku změní pořadí polí a uspořádá do dvou sloupců.  
  
     ![Vazba zdroje dat zákazníků na jednotlivých ovládacích prvků](../data-tools/media/raddata-customers-data-source-binding-to-individual-controls.png "raddata zákazníkům datové zdroje vazby pro jednotlivé ovládací prvky")  
  
     V zobrazení kódu nyní uvidíte novou `Grid` element na řádku 1 (střední řádek) nadřazené mřížky. Nadřazené mřížka obsahuje `DataContext` atribut, který odkazuje na kolekce CollectionViewSource, který byl přidán do `Windows.Resources` elementu. Zadaný datový kontext, při prvním textové pole, například vytvoří vazbu k "Řešení" Tento název se mapuje na `Address` vlastnost v aktuální `Customer` objektu do kolekce CollectionViewSource.  
  
    ```xaml  
    <Grid DataContext="{StaticResource customerViewSource}">  
    ```  
  
6.  Když zákazník není viditelná. v horní části okna, chceme zobrazit jeho objednávky v dolní části částečně. Ukážeme objednávky v ovládacím prvku zobrazení jedné mřížce. Pro datové vazby seznam podrobnosti fungovat podle očekávání je důležité, že můžeme vytvořit vazbu na objednávky vlastnost ve třídě zákazníkům, aby samostatný uzel objednávky. Věnujte pozornost tomu na následujícím obrázku. Přetáhněte vlastnost objednávek zákazníků třídy na dolní polovinu formuláře, tak, aby, návrhář vloží řádek 2:  
  
     ![Přetáhněte třídy objednávky jako mřížku](../data-tools/media/raddata-drag-orders-classes-as-grid.png "raddata objednávky přetáhněte třídy jako mřížku")  
  
7.  Visual Studio vygenerovala všechny vazební kód, který se připojuje ovládacích prvků uživatelského rozhraní na události v modelu. Všechno, co musíme udělat, aby bylo možné zobrazit nějaká data, je napsat kód k vyplnění modelu. První můžeme přejít na MainWindow.xaml.cs a přidejte datové členy třídy hlavního okna MainWindow pro datový kontext. Tento objekt, který byl vygenerován pro nás, funguje něco jako ovládací prvek, který sleduje změny a události v modelu. I když jsme tady, přidáme dva členy, které přidáte do nového zákazníka nebo nová objednávka použijeme později. Přidáme také logiku inicializace konstruktoru. Horní část naší třídy by měl vypadat nějak takto:  
  
    ```csharp  
    public partial class MainWindow : Window  
       {  
           public Customer newCustomer { get; set; }  
           public Order newOrder { get; set; }  
  
           NorthwindEntities context = new NorthwindEntities();  
           CollectionViewSource custViewSource;  
           CollectionViewSource ordViewSource;  
  
           public MainWindow()  
           {  
               InitializeComponent();  
               newCustomer = new Customer();  
               newOrder = new Order();  
               custViewSource = ((CollectionViewSource)  
                   (FindResource("customerViewSource")));  
               ordViewSource = ((CollectionViewSource)  
                   (FindResource("customerOrdersViewSource")));  
               DataContext = this;  
           }  
    ```  
  
     Přidat `using` směrnice pro System.Data.Entity metodu načtení rozšíření převeďte do rozsahu:  
  
    ```csharp  
    using System.Data.Entity;  
    ```  
  
     Teď přejděte dolů a najít Window_Loaded obslužné rutiny události. Všimněte si, že sada Visual Studio přidala pro nás objekt kolekce CollectionViewSource. Reprezentuje NorthwindEntities objekt, který jsme vybrali, když jsme vytvořili model. Teď přidejte kód do Window_loaded tak, aby celou metodu nyní vypadá takto:  
  
    ```csharp  
    private void Window_Loaded(object sender, RoutedEventArgs e)  
        {  
            // Load is an extension method on IQueryable,    
            // defined in the System.Data.Entity namespace.   
            // This method enumerates the results of the query,    
            // similar to ToList but without creating a list.   
            // When used with Linq to Entities this method    
            // creates entity objects and adds them to the context.   
            context.Customers.Load();  
  
            // After the data is loaded call the DbSet<T>.Local property    
            // to use the DbSet<T> as a binding source.   
            custViewSource.Source = context.Customers.Local;  
        }  
    ```  
  
8.  Stisknutím klávesy **F5**. Měli byste vidět podrobnosti prvního zákazníka, která byla načtena do kolekce CollectionViewSource a jejich objednávky v datové mřížce. Formátování není skvělé, proto Pojďme to opravit. vytvořit způsob, jak zobrazit další záznamy a provádět základní operace CRUD.  
  
## <a name="adjust-the-page-design-and-add-grids-for-new-customers-and-orders"></a>Upravte návrh stránek a přidání mřížky pro noví zákazníci a objednávky  
 Výchozí uspořádání vytvořené pomocí sady Visual Studio není ideální pro naši aplikaci, proto jsme provede některé změny ručně v XAML. Budeme také muset některé "typy" (které jsou ve skutečnosti mřížky) umožňují uživatelům přidání nového zákazníka nebo nové pořadí.    Aby bylo možné přidat nové odběratele a objednávky, potřebujeme samostatnou sadu textová pole, které nejsou vázán na data `CollectionViewSource`. Jsme bude ovládací prvek mřížky, které uživateli se zobrazí v daném okamžiku tak, že nastavíte vlastnost Visible v metody obslužné rutiny.  
  
 Nakonec přidáme tlačítko pro odstranění na každý řádek v tabulce objednávky a povolit tak uživateli odstranit jednotlivé objednávky.  
  
 Nejprve přidejte tyto styly Windows.Resources:  
  
```xaml  
<Style x:Key="Label" TargetType="{x:Type Label}" BasedOn="{x:Null}">  
    <Setter Property="HorizontalAlignment" Value="Left"/>  
    <Setter Property="VerticalAlignment" Value="Center"/>  
    <Setter Property="Margin" Value="3"/>  
    <Setter Property="Height" Value="23"/>  
</Style>  
<Style x:Key="CustTextBox" TargetType="{x:Type TextBox}" BasedOn="{x:Null}">  
    <Setter Property="HorizontalAlignment" Value="Right"/>  
    <Setter Property="VerticalAlignment" Value="Center"/>  
    <Setter Property="Margin" Value="3"/>  
    <Setter Property="Height" Value="26"/>  
    <Setter Property="Width" Value="120"/>  
</Style>  
```  
  
 Vnější mřížky v dalším kroku nahraďte tento kód:  
  
```xaml  
<Grid >  
     <Grid.RowDefinitions>  
         <RowDefinition Height="auto"/>  
         <RowDefinition Height="auto"/>  
         <RowDefinition Height="*"/>  
     </Grid.RowDefinitions>  
     <StackPanel  Orientation="Horizontal" Margin="2,2,2,0" Height="36" VerticalAlignment="Top" Background="Gainsboro" DataContext="{StaticResource customerViewSource}" d:LayoutOverrides="LeftMargin, RightMargin, TopMargin, BottomMargin">  
         <Button Name="btnFirst" Content="|◄" Command="{StaticResource FirstCommand}" Style="{StaticResource NavButton}"  />  
         <Button Name="btnPrev"  Content="◄" Command="{StaticResource PreviousCommand}" Style="{StaticResource NavButton}"/>  
         <Button Name="btnNext"  Content="►" Command="{StaticResource NextCommand}"     Style="{StaticResource NavButton}"/>  
         <Button Name="btnLast"  Content="►|" Command="{StaticResource LastCommand}" Style="{StaticResource NavButton}"/>  
         <Button Name="btnDelete" Content="Delete Customer" Command="{StaticResource DeleteCustomerCommand}" FontSize="11" Width="120" Style="{StaticResource NavButton}"/>  
         <Button  Name="btnAdd"   Content="New Customer"  Command="{StaticResource AddCommand}" FontSize="11" Width="80" Style="{StaticResource NavButton}"/>  
         <Button Content="New Order" Name="btnNewOrder" FontSize="11" Width="80" Style="{StaticResource NavButton}" Click="NewOrder_click"/>  
         <Button Name="btnUpdate" Content="Commit" Command="{StaticResource UpdateCommand}" FontSize="11" Width="80" Style="{StaticResource NavButton}"/>  
         <Button Content="Cancel" Name="btnCancel"  Command="{StaticResource CancelCommand}" FontSize="11" Width="80" Style="{StaticResource NavButton}"/>  
     </StackPanel>  
     <Grid x:Name="existingCustomerGrid" Grid.Row="1" HorizontalAlignment="Left" Margin="5" Visibility="Visible" VerticalAlignment="Top" Background="AntiqueWhite" DataContext="{StaticResource customerViewSource}">  
         <Grid.ColumnDefinitions>  
             <ColumnDefinition Width="Auto" MinWidth="233"/>  
             <ColumnDefinition Width="Auto" MinWidth="397"/>  
         </Grid.ColumnDefinitions>  
         <Grid.RowDefinitions>  
             <RowDefinition Height="Auto"/>  
             <RowDefinition Height="Auto"/>  
             <RowDefinition Height="Auto"/>  
             <RowDefinition Height="Auto"/>  
             <RowDefinition Height="Auto"/>  
             <RowDefinition Height="Auto"/>  
         </Grid.RowDefinitions>  
         <Label Content="Customer ID:" Grid.Row="0" Style="{StaticResource Label}"/>  
         <TextBox x:Name="customerIDTextBox"  Grid.Row="0" Style="{StaticResource CustTextBox}"   
                  Text="{Binding CustomerID, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true}"/>  
         <Label Content="Company Name:"  Grid.Row="1" Style="{StaticResource Label}"/>  
         <TextBox x:Name="companyNameTextBox"  Grid.Row="1" Style="{StaticResource CustTextBox}"   
                  Text="{Binding CompanyName, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true}"/>  
         <Label Content="Contact Name:"  Grid.Row="2" Style="{StaticResource Label}"/>  
         <TextBox x:Name="contactNameTextBox" Grid.Row="2" Style="{StaticResource CustTextBox}"   
                  Text="{Binding ContactName, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true}"/>  
         <Label Content="Contact Title:"  Grid.Row="3" Style="{StaticResource Label}"/>  
         <TextBox x:Name="contactTitleTextBox" Grid.Row="3" Style="{StaticResource CustTextBox}"   
                  Text="{Binding ContactTitle, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true}"/>  
         <Label Content="Address:" Grid.Row="4" Style="{StaticResource Label}"/>  
         <TextBox x:Name="addressTextBox" Grid.Row="4" Style="{StaticResource CustTextBox}"   
                  Text="{Binding Address, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true}"/>  
         <Label Content="City:" Grid.Column="1" Grid.Row="0"  Style="{StaticResource Label}"/>  
         <TextBox x:Name="cityTextBox" Grid.Column="1" Grid.Row="0" Style="{StaticResource CustTextBox}"   
                  Text="{Binding City, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true}"/>  
         <Label Content="Country:" Grid.Column="1" Grid.Row="1" Style="{StaticResource Label}"/>  
         <TextBox x:Name="countryTextBox" Grid.Column="1" Grid.Row="1" Style="{StaticResource CustTextBox}"   
                  Text="{Binding Country, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true}"/>  
         <Label Content="Fax:" Grid.Column="1" Grid.Row="2" Style="{StaticResource Label}"/>  
         <TextBox x:Name="faxTextBox" Grid.Column="1" Grid.Row="2" Style="{StaticResource CustTextBox}"   
                  Text="{Binding Fax, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true}"/>  
         <Label Content="Phone:" Grid.Column="1" Grid.Row="3" Style="{StaticResource Label}"/>  
         <TextBox x:Name="phoneTextBox" Grid.Column="1" Grid.Row="3" Style="{StaticResource CustTextBox}"   
                  Text="{Binding Phone, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true}"/>  
         <Label Content="Postal Code:" Grid.Column="1" Grid.Row="4" VerticalAlignment="Center" Style="{StaticResource Label}"/>  
         <TextBox x:Name="postalCodeTextBox" Grid.Column="1" Grid.Row="4" Style="{StaticResource CustTextBox}"   
                  Text="{Binding PostalCode, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true}"/>  
         <Label Content="Region:" Grid.Column="1" Grid.Row="5" Style="{StaticResource Label}"/>  
         <TextBox x:Name="regionTextBox" Grid.Column="1" Grid.Row="5" Style="{StaticResource CustTextBox}"   
                  Text="{Binding Region, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true}"/>  
     </Grid>  
     <Grid x:Name="newCustomerGrid" Grid.Row="1" HorizontalAlignment="Left" VerticalAlignment="Top" Margin="5" DataContext="{Binding RelativeSource={RelativeSource FindAncestor, AncestorType={x:Type Window}}, Path=newCustomer, UpdateSourceTrigger=Explicit}" Visibility="Collapsed" Background="CornflowerBlue">  
         <Grid.ColumnDefinitions>  
             <ColumnDefinition Width="Auto" MinWidth="233"/>  
             <ColumnDefinition Width="Auto" MinWidth="397"/>  
         </Grid.ColumnDefinitions>  
         <Grid.RowDefinitions>  
             <RowDefinition Height="Auto"/>  
             <RowDefinition Height="Auto"/>  
             <RowDefinition Height="Auto"/>  
             <RowDefinition Height="Auto"/>  
             <RowDefinition Height="Auto"/>  
             <RowDefinition Height="Auto"/>  
         </Grid.RowDefinitions>  
         <Label Content="Customer ID:" Grid.Row="0" Style="{StaticResource Label}"/>  
         <TextBox x:Name="add_customerIDTextBox"  Grid.Row="0"  Style="{StaticResource CustTextBox}"   
                  Text="{Binding CustomerID, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true}"/>  
         <Label Content="Company Name:"  Grid.Row="1" Style="{StaticResource Label}"/>  
         <TextBox x:Name="add_companyNameTextBox"  Grid.Row="1" Style="{StaticResource CustTextBox}"   
                  Text="{Binding CompanyName, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true }"/>  
         <Label Content="Contact Name:"  Grid.Row="2" Style="{StaticResource Label}"/>  
         <TextBox x:Name="add_contactNameTextBox" Grid.Row="2" Style="{StaticResource CustTextBox}"   
                  Text="{Binding ContactName, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true}"/>  
         <Label Content="Contact Title:"  Grid.Row="3" Style="{StaticResource Label}"/>  
         <TextBox x:Name="add_contactTitleTextBox" Grid.Row="3" Style="{StaticResource CustTextBox}"   
                  Text="{Binding ContactTitle, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true}"/>  
         <Label Content="Address:" Grid.Row="4" Style="{StaticResource Label}"/>  
         <TextBox x:Name="add_addressTextBox" Grid.Row="4" Style="{StaticResource CustTextBox}"   
                  Text="{Binding Address, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true}"/>  
         <Label Content="City:" Grid.Column="1" Grid.Row="0"  Style="{StaticResource Label}"/>  
         <TextBox x:Name="add_cityTextBox" Grid.Column="1" Grid.Row="0" Style="{StaticResource CustTextBox}"   
                  Text="{Binding City, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true}"/>  
         <Label Content="Country:" Grid.Column="1" Grid.Row="1" Style="{StaticResource Label}"/>  
         <TextBox x:Name="add_countryTextBox" Grid.Column="1" Grid.Row="1" Style="{StaticResource CustTextBox}"   
                  Text="{Binding Country, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true}"/>  
         <Label Content="Fax:" Grid.Column="1" Grid.Row="2" Style="{StaticResource Label}"/>  
         <TextBox x:Name="add_faxTextBox" Grid.Column="1" Grid.Row="2" Style="{StaticResource CustTextBox}"   
                  Text="{Binding Fax, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true}"/>  
         <Label Content="Phone:" Grid.Column="1" Grid.Row="3" Style="{StaticResource Label}"/>  
         <TextBox x:Name="add_phoneTextBox" Grid.Column="1" Grid.Row="3" Style="{StaticResource CustTextBox}"   
                  Text="{Binding Phone, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true}"/>  
         <Label Content="Postal Code:" Grid.Column="1" Grid.Row="4" VerticalAlignment="Center" Style="{StaticResource Label}"/>  
         <TextBox x:Name="add_postalCodeTextBox" Grid.Column="1" Grid.Row="4" Style="{StaticResource CustTextBox}"   
                  Text="{Binding PostalCode, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true}"/>  
         <Label Content="Region:" Grid.Column="1" Grid.Row="5" Style="{StaticResource Label}"/>  
         <TextBox x:Name="add_regionTextBox" Grid.Column="1" Grid.Row="5" Style="{StaticResource CustTextBox}"   
                  Text="{Binding Region, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true}"/>  
     </Grid>  
     <Grid x:Name="newOrderGrid" Grid.Row="1" HorizontalAlignment="Left" VerticalAlignment="Top" Margin="5" DataContext="{Binding Path=newOrder, Mode=TwoWay}" Visibility="Collapsed" Background="LightGreen">  
         <Grid.ColumnDefinitions>  
             <ColumnDefinition Width="Auto" MinWidth="233"/>  
             <ColumnDefinition Width="Auto" MinWidth="397"/>  
         </Grid.ColumnDefinitions>  
         <Grid.RowDefinitions>  
             <RowDefinition Height="Auto"/>  
             <RowDefinition Height="Auto"/>  
             <RowDefinition Height="Auto"/>  
             <RowDefinition Height="Auto"/>  
             <RowDefinition Height="Auto"/>  
             <RowDefinition Height="Auto"/>  
             <RowDefinition Height="Auto"/>  
         </Grid.RowDefinitions>  
         <Label Content="New Order Form" FontWeight="Bold"/>  
         <Label Content="Employee ID:"  Grid.Row="1" Style="{StaticResource Label}"/>  
         <TextBox x:Name="add_employeeIDTextBox" Grid.Row="1" Style="{StaticResource CustTextBox}"   
                  Text="{Binding EmployeeID, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true}"/>  
         <Label Content="Order Date:"  Grid.Row="2" Style="{StaticResource Label}"/>  
         <DatePicker x:Name="add_orderDatePicker" Grid.Row="2"  HorizontalAlignment="Right" Width="120"  
                 SelectedDate="{Binding OrderDate, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true, UpdateSourceTrigger=PropertyChanged}"/>  
         <Label Content="Required Date:" Grid.Row="3" Style="{StaticResource Label}"/>  
         <DatePicker x:Name="add_requiredDatePicker" Grid.Row="3" HorizontalAlignment="Right" Width="120"  
                  SelectedDate="{Binding RequiredDate, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true, UpdateSourceTrigger=PropertyChanged}"/>  
         <Label Content="Shipped Date:"  Grid.Row="4"  Style="{StaticResource Label}"/>  
         <DatePicker x:Name="add_shippedDatePicker"  Grid.Row="4"  HorizontalAlignment="Right" Width="120"  
                 SelectedDate="{Binding ShippedDate, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true, UpdateSourceTrigger=PropertyChanged}"/>  
         <Label Content="Ship Via:"  Grid.Row="5" Style="{StaticResource Label}"/>  
         <TextBox x:Name="add_ShipViaTextBox"  Grid.Row="5" Style="{StaticResource CustTextBox}"   
                  Text="{Binding ShipVia, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true}"/>  
         <Label Content="Freight"  Grid.Row="6" Style="{StaticResource Label}"/>  
         <TextBox x:Name="add_freightTextBox" Grid.Row="6" Style="{StaticResource CustTextBox}"   
                  Text="{Binding Freight, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true}"/>  
     </Grid>  
     <DataGrid x:Name="ordersDataGrid" SelectionUnit="Cell" SelectionMode="Single" AutoGenerateColumns="False" CanUserAddRows="false" IsEnabled="True" EnableRowVirtualization="True" Width="auto" ItemsSource="{Binding Source={StaticResource customerOrdersViewSource}}" Margin="10,10,10,10" Grid.Row="2" RowDetailsVisibilityMode="VisibleWhenSelected">  
         <DataGrid.Columns>  
             <DataGridTemplateColumn>  
                 <DataGridTemplateColumn.CellTemplate>  
                     <DataTemplate>  
                         <Button Content="Delete"  Command="{StaticResource DeleteOrderCommand}" CommandParameter="{Binding}"/>  
                     </DataTemplate>  
                 </DataGridTemplateColumn.CellTemplate>  
             </DataGridTemplateColumn>  
             <DataGridTextColumn x:Name="customerIDColumn" Binding="{Binding CustomerID}" Header="Customer ID" Width="SizeToHeader"/>  
             <DataGridTextColumn x:Name="employeeIDColumn" Binding="{Binding EmployeeID}" Header="Employee ID" Width="SizeToHeader"/>  
             <DataGridTextColumn x:Name="freightColumn" Binding="{Binding Freight}" Header="Freight" Width="SizeToHeader"/>  
             <DataGridTemplateColumn x:Name="orderDateColumn" Header="Order Date" Width="SizeToHeader">  
                 <DataGridTemplateColumn.CellTemplate>  
                     <DataTemplate>  
                         <DatePicker SelectedDate="{Binding OrderDate, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true, UpdateSourceTrigger=PropertyChanged}"/>  
                     </DataTemplate>  
                 </DataGridTemplateColumn.CellTemplate>  
             </DataGridTemplateColumn>  
             <DataGridTextColumn x:Name="orderIDColumn" Binding="{Binding OrderID}" Header="Order ID" Width="SizeToHeader"/>  
             <DataGridTemplateColumn x:Name="requiredDateColumn" Header="Required Date" Width="SizeToHeader">  
                 <DataGridTemplateColumn.CellTemplate>  
                     <DataTemplate>  
                         <DatePicker SelectedDate="{Binding RequiredDate, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true, UpdateSourceTrigger=PropertyChanged}"/>  
                     </DataTemplate>  
                 </DataGridTemplateColumn.CellTemplate>  
             </DataGridTemplateColumn>  
             <DataGridTextColumn x:Name="shipAddressColumn" Binding="{Binding ShipAddress}" Header="Ship Address" Width="SizeToHeader"/>  
             <DataGridTextColumn x:Name="shipCityColumn" Binding="{Binding ShipCity}" Header="Ship City" Width="SizeToHeader"/>  
             <DataGridTextColumn x:Name="shipCountryColumn" Binding="{Binding ShipCountry}" Header="Ship Country" Width="SizeToHeader"/>  
             <DataGridTextColumn x:Name="shipNameColumn" Binding="{Binding ShipName}" Header="Ship Name" Width="SizeToHeader"/>  
             <DataGridTemplateColumn x:Name="shippedDateColumn" Header="Shipped Date" Width="SizeToHeader">  
                 <DataGridTemplateColumn.CellTemplate>  
                     <DataTemplate>  
                         <DatePicker SelectedDate="{Binding ShippedDate, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true, UpdateSourceTrigger=PropertyChanged}"/>  
                     </DataTemplate>  
                 </DataGridTemplateColumn.CellTemplate>  
             </DataGridTemplateColumn>  
             <DataGridTextColumn x:Name="shipPostalCodeColumn" Binding="{Binding ShipPostalCode}" Header="Ship Postal Code" Width="SizeToHeader"/>  
             <DataGridTextColumn x:Name="shipRegionColumn" Binding="{Binding ShipRegion}" Header="Ship Region" Width="SizeToHeader"/>  
             <DataGridTextColumn x:Name="shipViaColumn" Binding="{Binding ShipVia}" Header="Ship Via" Width="SizeToHeader"/>  
         </DataGrid.Columns>  
     </DataGrid>  
 </Grid>  
```  
  
## <a name="add-buttons-to-navigate-add-update-and-delete"></a>Přidat tlačítka Procházet, přidávat, aktualizovat a odstraňovat  
 V aplikacích Windows Forms získejte objekt BindingNavigator pomocí tlačítek pro procházení řádků v databázi a provádění základních operací CRUD. WPF neposkytuje objektu BindingNavigator, ale jsou to docela jednoduché, aby. Můžeme to udělat pomocí tlačítek uvnitř vodorovné StackPanel v dolním řádku stránku mřížky a přidružené příkazy, které jsou vázány na metody v kódu budete k tlačítka.  
  
 Existují fours části příkazu logiku: (1) příkazy, (2) vazby, (3) tlačítka a (4) obslužné rutiny příkazů v kódu.  
  
#### <a name="add-commands-bindings-and-buttons-in-xaml"></a>Přidání příkazů, vazby a tlačítka v XAML  
  
1.  Nejprve přidáme příkazy v souboru MainWindow.XAML uvnitř elementu Windows.Resources:  
  
    ```xaml  
  
     <RoutedUICommand x:Key="FirstCommand" Text="First"/>  
    <RoutedUICommand x:Key="LastCommand" Text="Last"/>  
    <RoutedUICommand x:Key="NextCommand" Text="Next"/>  
    <RoutedUICommand x:Key="PreviousCommand" Text="Previous"/>  
    <RoutedUICommand x:Key="DeleteCustomerCommand" Text="Delete Customer"/>  
    <RoutedUICommand x:Key="DeleteOrderCommand" Text="Delete Order"/>  
    <RoutedUICommand x:Key="UpdateCommand" Text="Update"/>  
    <RoutedUICommand x:Key="AddCommand" Text="Add"/>  
    <RoutedUICommand x:Key="CancelCommand" Text="Cancel"/>  
    ```  
  
2.  Vazbou CommandBinding mapuje RoutedUICommand událostí na metodu v kódu. Přidejte tento element CommandBindings po Windows.Resources uzavírací značku:  
  
    ```xaml  
  
        <Window.CommandBindings>  
        <CommandBinding Command="{StaticResource FirstCommand}" Executed="FirstCommandHandler"/>  
        <CommandBinding Command="{StaticResource LastCommand}" Executed="LastCommandHandler"/>  
        <CommandBinding Command="{StaticResource NextCommand}" Executed="NextCommandHandler"/>  
        <CommandBinding Command="{StaticResource PreviousCommand}" Executed="PreviousCommandHandler"/>  
        <CommandBinding Command="{StaticResource DeleteCustomerCommand}" Executed="DeleteCustomerCommandHandler"/>  
        <CommandBinding Command="{StaticResource DeleteOrderCommand}" Executed="DeleteOrderCommandHandler"/>  
        <CommandBinding Command="{StaticResource UpdateCommand}" Executed="UpdateCommandHandler"/>  
        <CommandBinding Command="{StaticResource AddCommand}" Executed="AddCommandHandler"/>  
        <CommandBinding Command="{StaticResource CancelCommand}" Executed="CancelCommandHandler"/>  
    </Window.CommandBindings>  
    ```  
  
3.  Nyní Pojďme přidat StackPanel s navigaci, přidání, odstranění a aktualizace tlačítka. Nejprve přidejte tento styl Windows.Resources:  
  
    ```xaml  
    <Style x:Key="NavButton" TargetType="{x:Type Button}" BasedOn="{x:Null}">  
        <Setter Property="FontSize" Value="24"/>  
        <Setter Property="FontFamily" Value="Segoe UI Symbol"/>  
        <Setter Property="Margin" Value="2,2,2,0"/>  
        <Setter Property="Width" Value="40"/>  
        <Setter Property="Height" Value="auto"/>  
    </Style>  
    ```  
  
     Nyní vložte tento kód bezprostředně po RowDefinitions pro vnější element mřížky směrem k horní části stránky XAML:  
  
    ```xaml  
    <StackPanel  Orientation="Horizontal" Margin="2,2,2,0" Height="36" VerticalAlignment="Top" Background="Gainsboro" DataContext="{StaticResource customerViewSource}" d:LayoutOverrides="LeftMargin, RightMargin, TopMargin, BottomMargin">  
        <Button Name="btnFirst" Content="|◄" Command="{StaticResource FirstCommand}" Style="{StaticResource NavButton}"  />  
        <Button Name="btnPrev"  Content="◄" Command="{StaticResource PreviousCommand}" Style="{StaticResource NavButton}"/>  
        <Button Name="btnNext"  Content="►" Command="{StaticResource NextCommand}"     Style="{StaticResource NavButton}"/>  
        <Button Name="btnLast"  Content="►|" Command="{StaticResource LastCommand}" Style="{StaticResource NavButton}"/>  
        <Button Name="btnDelete" Content="Delete Customer" Command="{StaticResource DeleteCustomerCommand}" FontSize="11" Width="120" Style="{StaticResource NavButton}"/>  
        <Button  Name="btnAdd"   Content="New Customer"  Command="{StaticResource AddCommand}" FontSize="11" Width="80" Style="{StaticResource NavButton}"/>  
        <Button Content="New Order" Name="btnNewOrder" FontSize="11" Width="80" Style="{StaticResource NavButton}" Click="NewOrder_click"/>  
        <Button Name="btnUpdate" Content="Commit" Command="{StaticResource UpdateCommand}" FontSize="11" Width="80" Style="{StaticResource NavButton}"/>  
        <Button Content="Cancel" Name="btnCancel"  Command="{StaticResource CancelCommand}" FontSize="11" Width="80" Style="{StaticResource NavButton}"/>  
    </StackPanel>  
    ```  
  
#### <a name="add-command-handlers-to-the-mainwindow-class"></a>Přidání obslužné rutiny příkazů do třídy hlavního okna MainWindow  
  
1.  Použití modelu code-behind je minimální s výjimkou metody přidat a odstranit. Všimněte si, že se provádí navigaci voláním metody, vlastnosti zobrazení kolekce CollectionViewSource. DeleteOrderCommandHandler ukazuje, jak provádět kaskádové odstranění objednávku. Musíme nejprve odstranit Order_Details, které jsou k ní přidružena. UpdateCommandHandler přidá nového zákazníka ke kolekci, jinak právě aktualizuje existující objekt cokoli, co změny provedené v textových polích.  
  
2.  Přidejte do třídy hlavního okna MainWindow v MainWindow.xaml.cs tyto metody obslužné rutiny, pokud vaše kolekce CollectionViewSource pro tabulku zákazníků má jiný název, pak budete muset upravit název v každém z těchto metod:  
  
    ```csharp  
       private void LastCommandHandler(object sender, ExecutedRoutedEventArgs e)  
    {  
        custViewSource.View.MoveCurrentToLast();  
    }  
  
    private void PreviousCommandHandler(object sender, ExecutedRoutedEventArgs e)  
    {  
        custViewSource.View.MoveCurrentToPrevious();  
    }  
  
    private void NextCommandHandler(object sender, ExecutedRoutedEventArgs e)  
    {  
        custViewSource.View.MoveCurrentToNext();  
    }  
  
    private void FirstCommandHandler(object sender, ExecutedRoutedEventArgs e)  
    {  
        custViewSource.View.MoveCurrentToFirst();  
    }  
  
    private void DeleteCustomerCommandHandler(object sender, ExecutedRoutedEventArgs e)  
    {  
        // If existing window is visible, then delete the customer and all their orders.  
        // In a real application, you should add warnings and allow a user to cancel the operation.  
        var cur = custViewSource.View.CurrentItem as Customer;  
  
        var cust = (from c in context.Customers  
                    where c.CustomerID == cur.CustomerID  
                    select c).FirstOrDefault();  
  
        if (cust != null)  
        {  
            foreach (var ord in cust.Orders.ToList())  
            {  
                Delete_Order(ord);  
            }  
            context.Customers.Remove(cust);  
        }  
        context.SaveChanges();  
        custViewSource.View.Refresh();  
    }  
  
    // Commit changes from the new customer form, the new order form,  
    // or edits made to the existing customer form.  
    private void UpdateCommandHandler(object sender, ExecutedRoutedEventArgs e)  
    {  
        if (newCustomerGrid.IsVisible)  
        {  
            // Create a new object because the old one  
            // is being tracked by EF now.  
            newCustomer = new Customer();   
            newCustomer.Address = add_addressTextBox.Text;  
            newCustomer.City = add_cityTextBox.Text;  
            newCustomer.CompanyName = add_companyNameTextBox.Text;  
            newCustomer.ContactName = add_contactNameTextBox.Text;  
            newCustomer.ContactTitle = add_contactTitleTextBox.Text;  
            newCustomer.Country = add_countryTextBox.Text;  
            newCustomer.CustomerID = add_customerIDTextBox.Text;  
            newCustomer.Fax = add_faxTextBox.Text;  
            newCustomer.Phone = add_phoneTextBox.Text;  
            newCustomer.PostalCode = add_postalCodeTextBox.Text;  
            newCustomer.Region = add_regionTextBox.Text;  
  
            // Perform very basic validation  
            if (newCustomer.CustomerID.Length == 5)  
            {  
                // Insert the new customer at correct position:  
                int len = context.Customers.Local.Count();  
                int pos = len;  
                for (int i = 0; i < len; ++i)  
                {  
                    if (String.CompareOrdinal(newCustomer.CustomerID, context.Customers.Local[i].CustomerID) < 0)  
                    {  
                        pos = i;  
                        break;  
                    }  
                }  
                context.Customers.Local.Insert(pos, newCustomer);  
                custViewSource.View.Refresh();  
                custViewSource.View.MoveCurrentTo(newCustomer);  
            }  
            else  
            {  
                MessageBox.Show("CustomerID must have 5 characters.");  
            }  
  
            newCustomerGrid.Visibility = Visibility.Collapsed;  
            existingCustomerGrid.Visibility = Visibility.Visible;  
        }  
        else if (newOrderGrid.IsVisible)  
        {  
            // Order ID is auto-generated so we don't set it here.  
            // For CustomerID, address, etc we use the values from current customer.  
            // User can modify these in the datagrid after the order is entered.  
  
            newOrder.OrderDate = add_orderDatePicker.SelectedDate;  
            newOrder.RequiredDate = add_requiredDatePicker.SelectedDate;  
            newOrder.ShippedDate = add_shippedDatePicker.SelectedDate;  
            try  
            {  
                // Exercise for the reader if you are using Northwind:  
                // Add the Northwind Shippers table to the model.  
                // Acceptable ShipperID values are 1, 2, or 3.  
                if (add_ShipViaTextBox.Text == "1" || add_ShipViaTextBox.Text == "2"  
                    || add_ShipViaTextBox.Text == "3")  
                {  
                    newOrder.ShipVia = Convert.ToInt32(add_ShipViaTextBox.Text);  
                }  
                else  
                {  
                    MessageBox.Show("Shipper ID must be 1, 2, or 3 in Northwind.");  
                    return;  
                }  
            }  
            catch  
            {  
                MessageBox.Show("Ship Via must be convertible to int");  
                return;  
            }  
            try  
            {  
                newOrder.Freight = Convert.ToDecimal(add_freightTextBox.Text);  
            }  
            catch  
            {  
                MessageBox.Show("Freight must be convertible to decimal.");  
                return;  
            }  
  
            // Add the order into the EF model  
            context.Orders.Add(newOrder);  
            ordViewSource.View.Refresh();  
        }  
  
        // Save the changes, either for a new customer, a new order  
        // or an edit in an existing customer or order  
        context.SaveChanges();  
    }  
  
    // Sets up the form so that user can enter data. Data is later  
    // saved when user clicks Commit.  
    private void AddCommandHandler(object sender, ExecutedRoutedEventArgs e)  
    {  
        existingCustomerGrid.Visibility = Visibility.Collapsed;  
        newOrderGrid.Visibility = Visibility.Collapsed;  
        newCustomerGrid.Visibility = Visibility.Visible;  
  
        // Clear all the text boxes before adding a new customer.  
        foreach (var child in newCustomerGrid.Children)  
        {  
            var tb = child as TextBox;  
            if (tb != null)  
            {  
                tb.Text = "";  
            }  
        }  
    }  
  
    private void NewOrder_click(object sender, RoutedEventArgs e)  
    {  
        var cust = custViewSource.View.CurrentItem as Customer;  
        if (cust == null)  
        {  
            MessageBox.Show("No customer selected.");  
            return;  
        }  
  
        newOrder.CustomerID = cust.CustomerID;  
  
        // Get address and other mostly constant fields from   
        // an existing order, if one exists  
        var coll = custViewSource.Source as IEnumerable<Customer>;  
        var lastOrder = (from c in coll  
                         from ord in c.Orders  
                         select ord).LastOrDefault();  
        if (lastOrder != null)  
        {  
            newOrder.ShipAddress = lastOrder.ShipAddress;  
            newOrder.ShipCity = lastOrder.ShipCity;  
            newOrder.ShipCountry = lastOrder.ShipCountry;  
            newOrder.ShipName = lastOrder.ShipName;  
            newOrder.ShipPostalCode = lastOrder.ShipPostalCode;  
            newOrder.ShipRegion = lastOrder.ShipRegion;  
        }  
  
        existingCustomerGrid.Visibility = Visibility.Collapsed;  
        newCustomerGrid.Visibility = Visibility.Collapsed;  
        newOrderGrid.UpdateLayout();  
        newOrderGrid.Visibility = Visibility.Visible;  
    }  
  
    // Cancels any input into the new customer form  
    private void CancelCommandHandler(object sender, ExecutedRoutedEventArgs e)  
    {  
        add_addressTextBox.Text = "";  
        add_cityTextBox.Text = "";  
        add_companyNameTextBox.Text = "";  
        add_contactNameTextBox.Text = "";  
        add_contactTitleTextBox.Text = "";  
        add_countryTextBox.Text = "";  
        add_customerIDTextBox.Text = "";  
        add_faxTextBox.Text = "";  
        add_phoneTextBox.Text = "";  
        add_postalCodeTextBox.Text = "";  
        add_regionTextBox.Text = "";  
  
        existingCustomerGrid.Visibility = Visibility.Visible;  
        newCustomerGrid.Visibility = Visibility.Collapsed;  
        newOrderGrid.Visibility = Visibility.Collapsed;  
    }  
  
    private void Delete_Order(Order order)  
    {  
        // Find the order in the EF model.  
        var ord = (from o in context.Orders.Local  
                   where o.OrderID == order.OrderID  
                   select o).FirstOrDefault();  
  
        // Delete all the order_details that have  
        // this Order as a foreign key  
        foreach (var detail in ord.Order_Details.ToList())  
        {  
            context.Order_Details.Remove(detail);  
        }  
  
        // Now it's safe to delete the order.  
        context.Orders.Remove(ord);  
        context.SaveChanges();  
  
        // Update the data grid.  
        ordViewSource.View.Refresh();  
    }  
  
    private void DeleteOrderCommandHandler(object sender, ExecutedRoutedEventArgs e)  
    {  
        // Get the Order in the row in which the Delete button was clicked.  
        Order obj = e.Parameter as Order;  
        Delete_Order(obj);  
    }  
    ```  
  
3.  Stisknutím klávesy **F5**. Měli byste vidět vaše data a navigačních tlačítek by měl fungovat podle očekávání. Klikněte na "Potvrzení" Přidání nového zákazníka nebo pořadí modelu po zadání data.  Klepněte na tlačítko "Storno" pro zálohování mimo nový zákazník nebo nová objednávka formulář bez uložení. Můžete provádět úpravy stávající zákazníci a objednávky přímo v textových polích a tyto změny se zapíšou do modelu automaticky.  
  
## <a name="see-also"></a>Viz také  
 [Visual Studio data tools pro .NET](../data-tools/visual-studio-data-tools-for-dotnet.md) [dokumentace Entity Framework](https://msdn.microsoft.com/data/ee712907.aspx)

