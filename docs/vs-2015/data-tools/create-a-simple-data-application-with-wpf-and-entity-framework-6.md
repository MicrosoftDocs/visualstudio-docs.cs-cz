---
title: Vytvoření jednoduché datové aplikace pomocí WPF a Entity Framework 6 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
ms.assetid: 65929fab-5d78-4e04-af1e-cf4957f230f6
caps.latest.revision: 25
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 403415eaf8a882efdd63fdb9a73b5489b91f2529
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "72651089"
---
# <a name="create-a-simple-data-application-with-wpf-and-entity-framework-6"></a>Vytvoření jednoduché datové aplikace pomocí WPF a Entity Framework 6
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Tento názorný ukazuje, jak vytvořit základní aplikaci "Forms over data" v aplikaci Visual Studio s SQL Server LocalDB, databází Northwind, Entity Framework 6 a Windows Presentation Foundation. Ukazuje, jak provést základní datovou vazbu pomocí zobrazení hlavní-podrobnosti a má také vlastní "navigátor vazeb" s tlačítky pro "přesunout další", "přesunout předchozí", "" přesunout na začátek, "" přesunout na konec, "aktualizovat" a "odstranit".

 Tento článek se zaměřuje na použití datových nástrojů v aplikaci Visual Studio a nepokouší se vysvětlovat základní technologie v jakékoli hloubce. Předpokládá, že máte základní znalosti v jazyce XAML, Entity Framework a SQL. Tento příklad také neukazuje architekturu MVVM, která je standardem pro aplikace WPF. Tento kód ale můžete zkopírovat do vlastní aplikace MVVM s velmi malým počtem úprav.

## <a name="install-and-connect-to-northwind"></a>Instalace a připojení k databázi Northwind
 V tomto příkladu se používá SQL Server Express LocalDB a ukázková databáze Northwind. Měl by spolupracovat s jinými produkty SQL Database stejně, i když poskytovatel dat ADO.NET pro daný produkt podporuje Entity Framework.

1. Pokud jste to ještě neudělali, nainstalujte SQL Server 2014 LocalDB Express 32 ze [stránky pro stažení edice SQL Server](https://www.microsoft.com/sql-server/sql-server-editions-express).

2. Ukázkovou databázi Northwind nainstalujete podle pokynů uvedených tady: [instalace SQL Server ukázkových databází](../data-tools/install-sql-server-sample-databases.md).

3. [Přidejte nová připojení](../data-tools/add-new-connections.md) pro Northwind.

## <a name="configure-the-project"></a>Konfigurace projektu

1. V aplikaci Visual Studio zvolte **soubor &#124; nový projekt** a pak vytvořte novou aplikaci C# WPF.

2. V dalším kroku přidáme balíček NuGet pro Entity Framework 6. V Průzkumník řešení vyberte uzel projektu. V hlavní nabídce vyberte **projekt &#124; spravovat balíčky NuGet...**

     ![Položka nabídky spravovat balíčky NuGet](../data-tools/media/raddata-vs2015-manage-nuget-packages.png "raddata_vs2015_manage_nuget_packages")

3. Ve Správci balíčků NuGet klikněte na odkaz **Procházet** . Entity Framework je pravděpodobně horním balíčkem v seznamu. V pravém podokně klikněte na **instalovat** a postupujte podle pokynů. V okně výstup se dozvíte, že se instalace dokončila.

     ![Entity Framework balíček NuGet](../data-tools/media/raddata-vs2015-nuget-ef.png "raddata_vs2015_Nuget_EF")

4. Nyní můžeme použít Visual Studio k vytvoření modelu založeného na databázi Northwind.

## <a name="create-the-model"></a>Vytvoření modelu

1. V Průzkumník řešení klikněte pravým tlačítkem na uzel projektu a vyberte **přidat &#124; nová položka**. V levém podokně pod uzlem C# vyberte **data** a v prostředním podokně vyberte **ADO.NET model EDM (Entity Data Model)**.

    ![Entity Framework model nové položky projektu](../data-tools/media/raddata-ef-new-project-item.png "raddata EF nová položka projektu")

2. Zavolejte model `Northwind_model` a klikněte na tlačítko OK. Tím se zobrazí **průvodce model EDM (Entity Data Model)**. Zvolte **Návrhář EF z databáze** a pak klikněte na **Další**.

    ![Model EF z databáze](../data-tools/media/raddata-ef-model-from-database.png "Model raddata EF z databáze")

3. Na další obrazovce vyberte připojení Northwind LocalDB a klikněte na **Další**.

4. Na další stránce průvodce se volí tabulky, uložené procedury a další databázové objekty, které se mají zahrnout do modelu Entity Framework. Rozbalte uzel dbo ve stromovém zobrazení a vyberte podrobnosti o zákaznících, objednávkách a objednávkách. Ponechte zaškrtnuté výchozí hodnoty a klikněte na **Dokončit**.

    ![Výběr databázových objektů pro model](../data-tools/media/raddata-choose-ef-objects.png "raddata zvolit objekty EF")

5. Průvodce generuje třídy jazyka C#, které reprezentují Entity Framework model. Jedná se o prosté staré třídy jazyka C# a ty, které provedeme do uživatelského rozhraní WPF. Soubor. edmx popisuje vztahy a další metadata, která přidružuje třídy k objektům v databázi.  Soubory. TT jsou šablony T4, které generují kód, který bude pracovat s modelem a ukládají změny do databáze. Všechny tyto soubory můžete zobrazit v Průzkumník řešení pod uzlem Northwind_model:

    ![Průzkumník řešení soubory modelu EF](../data-tools/media/raddata-solution-explorer-ef-model-files.png "soubory modelů raddata Průzkumník řešení EF")

    Plocha návrháře pro soubor. edmx umožňuje upravit některé vlastnosti a relace v modelu. V tomto návodu nebudeme používat návrháře.

6. Soubory. TT jsou obecné účely a musíme pro práci s datovou vazbou WPF, která vyžaduje ObservableCollections, selepšit jednu z nich.  V Průzkumník řešení rozbalte uzel Northwind_model, dokud nenajdete Northwind_model. tt. (Ujistěte se, že **nejste v části** *. Context. tt soubor, který je přímo pod souborem. edmx).

   - Nahraďte dva výskyty <xref:System.Collections.ICollection> řetězcem <xref:System.Collections.ObjectModel.ObservableCollection%601> .

   - Nahraďte první výskyt <xref:System.Collections.Generic.HashSet%601> <xref:System.Collections.ObjectModel.ObservableCollection%601> kolem řádku 51. Nenahrazovat druhý výskyt HashSet –

   - Nahradí jediný výskyt <xref:System.Collections.Generic> (kolem řádku 334) s <xref:System.Collections.ObjectModel> .

7. Stisknutím **kombinace kláves CTRL + SHIFT + B** Sestavte projekt. Po dokončení sestavení jsou třídy modelu viditelné v průvodci zdroji dat.

   Nyní jsme připraveni připojit tento model na stránku XAML, aby bylo možné zobrazit, navigovat a upravovat data.

## <a name="databind-the-model-to-the-xaml-page"></a>Vázání modelu na stránku XAML
 Je možné napsat vlastní kód datové vazby, ale je mnohem jednodušší, aby to Visual Studio prodali za vás.

1. V hlavní nabídce vyberte možnost **projekt &#124; přidat nový zdroj dat** a zobrazte tak **Průvodce konfigurací zdroje dat**. Vyberte **objekt** , protože jsme navázáni na třídy modelů, nikoli na databázi:

     ![Průvodce konfigurací zdroje dat se zdrojem objektů](../data-tools/media/raddata-data-source-configuration-wizard-with-object-source.png "Průvodce konfigurací zdroje dat raddata se zdrojem objektů")

2. Vyberte zákazníka.  (Zdroje pro objednávky budou automaticky vygenerovány z vlastnosti navigace objednávky u zákazníka.)

     ![Přidání tříd entit jako zdrojů dat](../data-tools/media/raddata-add-entity-classes-as-data-sources.png "raddata přidat třídy entit jako zdroje dat")

3. Klikněte na **Dokončit**.

4. V zobrazení kód přejděte na MainWindow. XAML. Pro účely tohoto příkladu budeme uchovávat XAML velmi jednoduché. Změňte název MainWindow na výstižnější a zvyšte jeho výšku a šířku na 600 x 800. Kdykoli ho můžete později změnit. Teď přidejte tyto tři definice řádků do hlavní mřížky, jeden řádek pro navigační tlačítka, jednu pro podrobnosti o zákazníkovi, jednu pro mřížku, která zobrazuje jejich objednávky:

    ```xaml
    <Grid.RowDefinitions>
               <RowDefinition Height="auto"/>
               <RowDefinition Height="auto"/>
               <RowDefinition Height="*"/>
           </Grid.RowDefinitions>
    ```

5. Nyní otevřete MainWindow. XAML, abyste ho zobrazili v návrháři. To způsobí, že se okno zdroje dat zobrazí jako možnost v okraji okna sady Visual Studio vedle možnosti sada nástrojů. Kliknutím na kartu otevřete okno nebo jinak stiskněte klávesy **SHIFT + ALT + D** nebo zvolte možnost **Zobrazit &#124; jiné zdroje dat &#124; Windows**. Všechny vlastnosti ve třídě Customers (zákazníci) se zobrazí v samostatném textovém poli. Nejprve klikněte na šipku v poli se seznamem Customers (zákazníci) a vyberte **Podrobnosti**. Pak přetáhněte uzel do střední části návrhové plochy, aby Návrhář věděl, že má přejít na prostřední řádek.  Pokud k tomu dojde, můžete řádek zadat později v jazyce XAML. Ve výchozím nastavení jsou ovládací prvky umístěny svisle v prvku mřížky, ale v tomto okamžiku je můžete uspořádat tak, jak chcete, například na formuláři.  Může být například vhodné umístit textové pole název nahoře nad adresu. Ukázková aplikace pro tento článek mění pořadí polí a mění jejich uspořádání do dvou sloupců.

     ![Vazba zdroje dat zákazníků na jednotlivé ovládací prvky](../data-tools/media/raddata-customers-data-source-binding-to-individual-controls.png "vazba zdroje dat zákazníků raddata na jednotlivé ovládací prvky")

     V zobrazení kódu teď můžete zobrazit nový `Grid` prvek v řádku 1 (prostřední řádek) nadřazené mřížky. Nadřazená mřížka má `DataContext` atribut, který odkazuje na CollectionViewSource, který byl přidán do `Windows.Resources` elementu. Vzhledem k tomuto kontextu dat, když je první textové pole například svázána s názvem "adresa", je mapován na `Address` vlastnost v aktuálním `Customer` objektu v CollectionViewSource.

    ```xaml
    <Grid DataContext="{StaticResource customerViewSource}">
    ```

6. Když se zákazník zobrazí v horní polovině okna, chceme zobrazit jeho objednávky v dolní polovině. Objednávky zobrazíme v jednom ovládacím prvku zobrazení mřížky. Pro datovou vazbu hlavní-podrobnosti, která bude fungovat podle očekávání, je důležité vytvořit vazbu na vlastnost Orders ve třídě Customers, nikoli na uzel samostatné objednávky. Věnujte pozornost následující ilustraci. Přetáhněte vlastnost Orders třídy Customers na spodní polovinu formuláře, aby ho Návrhář na řádku 2 vloží:

     ![Přetahovat třídy Orders jako Grid](../data-tools/media/raddata-drag-orders-classes-as-grid.png "raddata přetahovat třídy Orders jako Grid")

7. Aplikace Visual Studio vygenerovala veškerý kód vazby, který spojuje ovládací prvky uživatelského rozhraní s událostmi v modelu. Vše, co potřebujeme, aby se zobrazila nějaká data, je napsat nějaký kód pro naplnění modelu. Nejdřív Pojďme přejít na MainWindow.xaml.cs a přidat datový člen do třídy MainWindow pro kontext dat. Tento objekt, který byl vygenerován pro nás, funguje podobně jako ovládací prvek, který sleduje změny a události v modelu. V tomto příkladu přidáme dva členy, které později použijeme k přidání nového zákazníka nebo nového řádu. Přidáme také logiku inicializace konstruktoru. Horní část naší třídy by měla vypadat takto:

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

     Přidejte `using` direktivu pro System. data. entity, která načte metodu rozšíření Load do oboru:

    ```csharp
    using System.Data.Entity;
    ```

     Nyní přejděte dolů a najděte obslužnou rutinu události Window_Loaded. Všimněte si, že Visual Studio přidalo pro nás objekt CollectionViewSource. To představuje objekt NorthwindEntities, který jsme vybrali při vytváření modelu. Přidejte kód pro Window_loaded tak, aby celá metoda teď vypadala takto:

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

8. Stiskněte klávesu **F5**. Měli byste vidět podrobnosti o prvním zákazníkovi, který se načetl do CollectionViewSource, a jejich objednávky v datové mřížce. Formátování není Skvělé, takže pojďme opravit. a sekotcím pro zobrazení ostatních záznamů a proveďte základní operace CRUD.

## <a name="adjust-the-page-design-and-add-grids-for-new-customers-and-orders"></a>Upravte návrh stránky a přidejte mřížku pro nové zákazníky a objednávky.
 Výchozí uspořádání vytvořené aplikací Visual Studio není ideální pro naši aplikaci, takže v XAML provedeme změny ručně. Také budete potřebovat některé "formy" (které jsou ve skutečnosti Gridy), aby uživatel mohl přidat nového zákazníka nebo nové pořadí.    Aby bylo možné přidat nového zákazníka a objednávku, potřebujeme samostatnou sadu textových polí, která nejsou vázaná na data na `CollectionViewSource` . Nastavením vlastnosti Visible v metodách obslužné rutiny určujeme, která mřížka se uživateli v daném čase uvidí.

 Nakonec přidáme na každý řádek v mřížce objednávky tlačítko Odstranit, aby uživatel mohl odstranit individuální objednávku.

 Nejdřív přidejte tyto styly do Windows. Resources:

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

 Potom nahraďte celou vnější mřížku tímto kódem:

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

## <a name="add-buttons-to-navigate-add-update-and-delete"></a>Přidání tlačítek pro navigaci, přidávání, aktualizaci a odstraňování
 V model Windows Formsch aplikacích získáte objekt BindingNavigator s tlačítky pro procházení řádků v databázi a provádění základních operací CRUD. WPF neposkytuje objekt BindingNavigator, ale je dostatečně snadné ho vytvořit. Provedeme to pomocí tlačítek uvnitř horizontálního StackPanelu v dolním řádku mřížky stránky a přiřadíme tlačítka k příkazům, které jsou svázané s metodami v kódu na pozadí.

 Příkazová logika obsahuje čtyři části: (1) příkazy, (2) vazby, (3) tlačítka a (4) obslužné rutiny příkazu v kódu na pozadí.

#### <a name="add-commands-bindings-and-buttons-in-xaml"></a>Přidání příkazů, vazeb a tlačítek v jazyce XAML

1. Nejprve přidáme příkazy do našeho souboru MainWindow. XAML v rámci elementu Windows. Resources:

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

2. CommandBinding mapuje událost RoutedUICommand na metodu v kódu na pozadí. Přidejte tento element CommandBindings za uzavírací značku Windows. Resources:

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

3. Nyní přidáme StackPanel pomocí tlačítek navigace, přidat, odstranit a aktualizovat. Nejprve tento styl přidejte do Windows. Resources:

    ```xaml
    <Style x:Key="NavButton" TargetType="{x:Type Button}" BasedOn="{x:Null}">
        <Setter Property="FontSize" Value="24"/>
        <Setter Property="FontFamily" Value="Segoe UI Symbol"/>
        <Setter Property="Margin" Value="2,2,2,0"/>
        <Setter Property="Width" Value="40"/>
        <Setter Property="Height" Value="auto"/>
    </Style>
    ```

     Nyní vložte tento kód hned za RowDefinitions pro vnější mřížku do horní části stránky XAML:

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

#### <a name="add-command-handlers-to-the-mainwindow-class"></a>Přidání obslužných rutin příkazů do třídy MainWindow

1. Kód na pozadí je minimální s výjimkou metod Add a DELETE. Všimněte si, že navigace je prováděna voláním metod ve vlastnosti zobrazení CollectionViewSource. DeleteOrderCommandHandler ukazuje, jak provést kaskádové odstranění na základě objednávky. Musíme nejdřív odstranit Order_Details, které jsou k němu přidružené. UpdateCommandHandler přidá do kolekce nového zákazníka nebo jinak pouze aktualizuje existující objekt o jakékoli změny provedené uživatelem v textových polích.

2. Přidejte tyto obslužné rutiny do třídy MainWindow v MainWindow.xaml.cs, pokud CollectionViewSource pro tabulku Customers má jiný název, budete muset upravit název v každé z těchto metod:

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

3. Stiskněte klávesu **F5**. Měla by se zobrazit vaše data a navigační tlačítka by měla fungovat podle očekávání. Po zadání dat klikněte na potvrdit a přidejte nového zákazníka nebo objednávku do modelu.  Klikněte na Zrušit pro zálohování nového zákazníka nebo nového formuláře objednávky bez uložení. Můžete provádět úpravy stávajících zákazníků a objednávek přímo v textových polích a tyto změny budou zapsány do modelu automaticky.

## <a name="see-also"></a>Viz také
 [Dokumentace k sadě](https://msdn.microsoft.com/data/ee712907.aspx) [Visual Studio data tools for .NET](../data-tools/visual-studio-data-tools-for-dotnet.md) Entity Framework
