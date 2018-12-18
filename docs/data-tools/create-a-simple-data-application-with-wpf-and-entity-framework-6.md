---
title: Vytvoření jednoduché datové aplikace s použitím WPF a Entity Framework 6
ms.date: 08/22/2017
ms.topic: conceptual
dev_langs:
- CSharp
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 5993256b41a07c4861ef2def58dc14d7fd849313
ms.sourcegitcommit: 81e9d90843ead658bc73b30c869f25921d99e116
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/26/2018
ms.locfileid: "52305608"
---
# <a name="create-a-simple-data-application-with-wpf-and-entity-framework-6"></a>Vytvoření jednoduché datové aplikace s použitím WPF a Entity Framework 6

Tento návod ukazuje, jak vytvořit základní "formy nad daty" aplikace v sadě Visual Studio. Aplikace používá SQL Server LocalDB, Northwind databáze, Entity Framework 6 a Windows Presentation Foundation. Ukazuje, jak provést základní datové vazby seznam podrobnosti zobrazení a také obsahuje vlastní Navigátor vazby pomocí tlačítka pro **přesunout na další**, **přesunout na předchozí**, **přejděte od**, **Přesunout na konec**, **aktualizace** a **odstranit**.

Tento článek se zaměřuje na pomocí nástrojů data v sadě Visual Studio a nebude pokoušet o vysvětlují základní technologie v libovolnou hloubku. Předpokládá, že máte základní znalosti s XAML, Entity Framework a SQL. Tento příklad také neukazuje architektury Model-View-ViewModel (MVVM), což je standard pro aplikace WPF. Tento kód však můžete zkopírovat do MVVM aplikace s několik změn.

## <a name="install-and-connect-to-northwind"></a>Nainstalujte a připojte se k Northwind

Tento příklad používá SQL Server Express LocalDB a ukázkové databáze Northwind. Pokud zprostředkovatele dat ADO.NET pro tento produkt podporuje rozhraní Entity Framework, že by měl bude fungovat s produkty SQL database stejně.

1.  Pokud nemáte SQL Server Express LocalDB, nainstalujte ji z [SQL Server Express stránku pro stažení](https://www.microsoft.com/sql-server/sql-server-editions-express), nebo prostřednictvím **instalační program sady Visual Studio**. V **instalační program sady Visual Studio**, jako součást můžete nainstalovat SQL Server Express LocalDB **vývoj desktopových aplikací .NET** úloh nebo jako jednotlivých komponent.

2.  Instalace ukázkové databáze Northwind pomocí následujících kroků:

    1. V sadě Visual Studio, otevřete **Průzkumník objektů systému SQL Server** okna. (**Průzkumník objektů systému SQL Server** je nainstalován jako součást **ukládání a zpracování dat** zatížení **instalační program sady Visual Studio**.) Rozbalte **systému SQL Server** uzlu. Klikněte pravým tlačítkem na instanci LocalDB a vyberte **nový dotaz**.

       Otevře se okno editor dotazů.

    2. Kopírovat [Northwind příkazů jazyka Transact-SQL skriptů](https://github.com/MicrosoftDocs/visualstudio-docs/blob/master/docs/data-tools/samples/northwind.sql?raw=true) do schránky. Tento skript T-SQL vytvoří databázi Northwind úplně od začátku a naplní daty.

    3. Vložte skript T-SQL do editoru dotazů a klikněte na tlačítko **Execute** tlačítko.

       Po chvilce dotaz doběhnutí a vytvořit databázi Northwind.

3.  [Přidat nové připojení](../data-tools/add-new-connections.md) pro databáze Northwind.

## <a name="configure-the-project"></a>Konfigurace projektu

1.  V sadě Visual Studio, zvolte **souboru** > **nový** > **projektu** a vytvořte nové C# aplikaci WPF.

2.  V dalším kroku přidejte balíček NuGet pro Entity Framework 6. V **Průzkumníka řešení**, vyberte uzel projektu. V hlavní nabídce zvolte **projektu** > **spravovat balíčky NuGet**.

     ![Spravovat balíčky NuGet položky nabídky](../data-tools/media/raddata_vs2015_manage_nuget_packages.png)

3.  V **Správce balíčků NuGet**, klikněte na **Procházet** odkaz. Entity Framework je pravděpodobně hlavní balíček v seznamu. Klikněte na tlačítko **nainstalovat** v pravém podokně a postupujte podle zobrazených výzev. V okně výstupu zjistíte, po dokončení instalace.

     ![Balíček NuGet Entity Framework](../data-tools/media/raddata_vs2015_nuget_ef.png)

4.  Teď můžete použít Visual Studio k vytvoření model založený na databázi Northwind.

## <a name="create-the-model"></a>Vytvoření modelu

1. Klikněte pravým tlačítkem na uzel projektu v **Průzkumníka řešení** a zvolte **přidat** > **nová položka**. V levém podokně v části C# uzlu, vyberte **Data** a v prostředním podokně vyberte **datový Model Entity ADO.NET**.

   ![Entity Framework Model novou položku projektu](../data-tools/media/raddata-ef-new-project-item.png)

2. Volání modelu `Northwind_model` a zvolte **OK**. **Průvodce datovým modelem Entity** otevře. Zvolte **EF designeru z databáze** a potom klikněte na tlačítko **Další**.

   ![EF Model z databáze](../data-tools/media/raddata-ef-model-from-database.png)

3. Na další obrazovce vyberte váš LocalDB Northwind připojení a na **Další**.

4. Na další stránce průvodce zvolte, které tabulky, uložené procedury a ostatních databázových objektů chcete zahrnout do modelu Entity Framework. Dbo uzlu ve stromovém zobrazení rozbalte a vyberte možnost **zákazníkům**, **objednávky**, a **OrderDetails**. Ponechte výchozí nastavení zaškrtnuté políčko a klikněte na tlačítko **Dokončit**.

    ![Zvolit databázové objekty pro model](../data-tools/media/raddata-choose-ef-objects.png)

5. Průvodce vygeneruje třídy C#, které představují model Entity Framework. Třídy jsou plain old C# třídy a jsou co jsme do uživatelského rozhraní WPF databind. *Edmx* soubor popisuje vztahy a další metadata, která přidružuje třídy objektů v databázi. *.Tt* soubory jsou šablony T4, které generují kód, který funguje na modelu a uložte změny do databáze. Zobrazí se všechny tyto soubory v **Průzkumníka řešení** pod uzlem Northwind_model:

      ![Soubory modelu EF Průzkumníka řešení](../data-tools/media/raddata-solution-explorer-ef-model-files.png)

    Na plochu návrháře pro *edmx* soubor můžete upravit některé vlastnosti a vztahy v modelu. Nebudeme použití návrháře v tomto názorném postupu.

6. *.Tt* soubory jsou obecné účely a je potřeba jeden z nich pro práci s datovou vazbou WPF, která vyžaduje ObservableCollections upravit. V **Průzkumníka řešení**, rozbalte uzel Northwind_model, dokud nenajdete *Northwind_model.tt*. (Ujistěte se, že nejste v *. Context.tt* souboru, který je přímo pod *edmx* souboru.)

   -   Nahraďte dva výskyty <xref:System.Collections.ICollection> s <xref:System.Collections.ObjectModel.ObservableCollection%601>.

   -   Nahraďte první výskyt <xref:System.Collections.Generic.HashSet%601> s <xref:System.Collections.ObjectModel.ObservableCollection%601> kolem řádku 51. Druhým výskytem HashSet nenahrazují.

   -   Nahradit jenom výskyt <xref:System.Collections.Generic> (kolem řádku 431) s <xref:System.Collections.ObjectModel>.

7. Stisknutím klávesy **Ctrl**+**Shift**+**B** k sestavení projektu. Po dokončení sestavení jsou viditelné v Průvodci zdroje dat třídy modelu.

Nyní jste připraveni k připojení tento model na stránku XAML tak, že můžete zobrazit, přejděte a upravit data.

## <a name="databind-the-model-to-the-xaml-page"></a>DataBind modelu, který má stránky XAML

Je možné psát vlastní kód vázání dat, ale je mnohem jednodušší nechte Visual Studio to pro vás udělal.

1.  V hlavní nabídce zvolte **projektu** > **přidat nový zdroj dat** zobrazíte **Průvodce konfigurací zdroje dat**. Zvolte **objekt** vzhledem k tomu, že jsou vazby modelu třídám, ne k databázi:

     ![Průvodce konfigurací zdroje dat se zdrojem objektu](../data-tools/media/raddata-data-source-configuration-wizard-with-object-source.png)

2.  Vyberte **zákazníka**. (Zdrojů pro objednávky jsou automaticky generovány z navigační vlastnost objednávky v zákazníka.)

     ![Přidání tříd entit jako zdroje dat](../data-tools/media/raddata-add-entity-classes-as-data-sources.png)

3.  Klikněte na tlačítko **Dokončit**.

4.  Přejděte do *souboru MainWindow.xaml* v zobrazení kódu. XAML uchováváme na jednoduché pro účely tohoto příkladu. Změna názvu hlavního okna MainWindow výstižněji a zvýšit jeho výšku a šířku na 600 × 800 teď. Můžete vždycky změnit ji později. Nyní přidejte definice těchto tří řádků do hlavní mřížky, jeden řádek pro navigačních tlačítek, jeden pro podrobnosti zákazníka a jeden pro tabulku, která zobrazuje jejich objednávky:

    ```xaml
    <Grid.RowDefinitions>
            <RowDefinition Height="auto"/>
            <RowDefinition Height="auto"/>
            <RowDefinition Height="*"/>
        </Grid.RowDefinitions>
    ```

5.  Nyní otevřete *souboru MainWindow.xaml* tak, aby prohlížíte v návrháři. To způsobí, že **zdroje dat** okna vedle nezobrazí jako možnost na okraji okna sady Visual Studio **nástrojů**. Klikněte na kartu pro otevření okna nebo jinak stisknutím klávesy **Shift**+**Alt**+**D** nebo zvolte **zobrazení**  >  **Jiných Windows** > **zdroje dat**. Budeme zobrazit každou vlastnost v třídě zákazníci vlastní jednotlivé textové pole. Nejprve, klikněte na šipku v **zákazníkům** – pole se seznamem a vyberte **podrobnosti**. Potom přetáhněte uzel na prostřední část návrhové ploše tak, aby návrháři ví, že chcete, aby přejděte v prostředním. Pokud někam ho nezaložili můžete později ručně v XAML řádku. Ve výchozím nastavení ovládací prvky jsou umístěny ve svislém směru v elementu mřížky, ale v tomto okamžiku je možné uspořádat je však chcete ve formuláři. Například může mít smysl umístit **název** textového pole v horní části výše adresu. Ukázková aplikace pro účely tohoto článku změní pořadí polí a uspořádá do dvou sloupců.

     ![Vazba zdroje dat zákazníků na jednotlivých ovládacích prvků](../data-tools/media/raddata-customers-data-source-binding-to-individual-controls.png)

     V zobrazení kódu nyní uvidíte novou `Grid` element na řádku 1 (střední řádek) nadřazené mřížky. Nadřazené mřížka obsahuje `DataContext` atribut, který odkazuje na kolekce CollectionViewSource, který je přidán do `Windows.Resources` elementu. Zadaný tento kontext dat při prvního textového pole váže k **adresu**, tento název se mapuje na `Address` vlastnost v aktuální `Customer` objektu do kolekce CollectionViewSource.

    ```xaml
    <Grid DataContext="{StaticResource customerViewSource}">
    ```

6.  Když zákazník není viditelná. v horní části okna, chcete zobrazit jeho objednávky v dolní části částečně. Zobrazit objednávky v ovládacím prvku zobrazení jedné mřížce. Pro datové vazby seznam podrobnosti fungovat podle očekávání je důležité vytvořit vazbu na vlastnost objednávky ve třídě zákazníkům, aby samostatný uzel objednávky. Přetáhněte vlastnost objednávek zákazníků třídy na dolní polovinu formuláře, tak, aby, návrhář vloží řádek 2:

     ![Přetáhněte třídy objednávky jako mřížku](../data-tools/media/raddata-drag-orders-classes-as-grid.png)

7.  Visual Studio vygenerovala všechny vazební kód, který se připojuje ovládacích prvků uživatelského rozhraní na události v modelu. Všechno, co musíte udělat, aby bylo možné zobrazit nějaká data, je napsat kód k vyplnění modelu. Nejprve přejděte do *MainWindow.xaml.cs* a přidejte datové členy třídy hlavního okna MainWindow pro datový kontext. Tento objekt, který byl vygenerován pro vás, funguje něco jako ovládací prvek, který sleduje změny a události v modelu. Budete také přidat logiku inicializace konstruktoru. Horní části třídy by měl vypadat nějak takto:

     [!code-csharp[MainWindow#1](../data-tools/codesnippet/CSharp/CreateWPFDataApp/MainWindow.xaml.cs#1)]

     Přidat `using` směrnice pro System.Data.Entity metodu načtení rozšíření převeďte do rozsahu:

     ```csharp
     using System.Data.Entity;
     ```

     Nyní, posuňte se dolů a najděte `Window_Loaded` obslužné rutiny události. Všimněte si, že sada Visual Studio přidala objekt kolekce CollectionViewSource. To představuje NorthwindEntities objekt, který jste vybrali při vytváření modelu. Teď přidejte kód, který `Window_Loaded` tak, aby celou metodu nyní vypadá takto:

     [!code-csharp[Window_Loaded#2](../data-tools/codesnippet/CSharp/CreateWPFDataApp/MainWindow.xaml.cs#2)]

8.  Stisknutím klávesy **F5**. Měli byste vidět podrobnosti prvního zákazníka, která byla načtena do kolekce CollectionViewSource. Také byste měli vidět jejich objednávky v datové mřížce. Formátování není skvělé, proto Pojďme to opravit. Můžete také vytvořit způsob, jak zobrazit další záznamy a provádět základní operace CRUD.

## <a name="adjust-the-page-design-and-add-grids-for-new-customers-and-orders"></a>Upravte návrh stránek a přidání mřížky pro noví zákazníci a objednávky

Výchozí uspořádání vytvořené pomocí sady Visual Studio není ideální pro vaše aplikace, takže budete provést nějaké změny ručně v XAML. Budete potřebovat některé "typy" (které jsou ve skutečnosti mřížky) a povolit uživateli přidání nového zákazníka nebo pořadí. Aby bylo možné přidat nové odběratele a objednávky, potřebujete samostatnou sadu textová pole, které nejsou vázán na data `CollectionViewSource`. Bude ovládací prvek mřížky, které uživateli se zobrazí v daném okamžiku tak, že nastavíte vlastnost Visible v metody obslužné rutiny. Nakonec přidejte tlačítko pro odstranění na každý řádek v tabulce objednávky a povolit uživateli odstranit jednotlivé objednávky.

Nejprve přidejte tyto styly `Windows.Resources` prvek *souboru MainWindow.xaml*:

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
<Grid>
     <Grid.RowDefinitions>
         <RowDefinition Height="auto"/>
         <RowDefinition Height="auto"/>
         <RowDefinition Height="*"/>
     </Grid.RowDefinitions>
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
         <TextBox x:Name="customerIDTextBox" Grid.Row="0" Style="{StaticResource CustTextBox}"
                  Text="{Binding CustomerID, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true}"/>
         <Label Content="Company Name:" Grid.Row="1" Style="{StaticResource Label}"/>
         <TextBox x:Name="companyNameTextBox" Grid.Row="1" Style="{StaticResource CustTextBox}"
                  Text="{Binding CompanyName, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true}"/>
         <Label Content="Contact Name:" Grid.Row="2" Style="{StaticResource Label}"/>
         <TextBox x:Name="contactNameTextBox" Grid.Row="2" Style="{StaticResource CustTextBox}"
                  Text="{Binding ContactName, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true}"/>
         <Label Content="Contact Title:" Grid.Row="3" Style="{StaticResource Label}"/>
         <TextBox x:Name="contactTitleTextBox" Grid.Row="3" Style="{StaticResource CustTextBox}"
                  Text="{Binding ContactTitle, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true}"/>
         <Label Content="Address:" Grid.Row="4" Style="{StaticResource Label}"/>
         <TextBox x:Name="addressTextBox" Grid.Row="4" Style="{StaticResource CustTextBox}"
                  Text="{Binding Address, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true}"/>
         <Label Content="City:" Grid.Column="1" Grid.Row="0" Style="{StaticResource Label}"/>
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
         <TextBox x:Name="add_customerIDTextBox" Grid.Row="0" Style="{StaticResource CustTextBox}"
                  Text="{Binding CustomerID, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true}"/>
         <Label Content="Company Name:" Grid.Row="1" Style="{StaticResource Label}"/>
         <TextBox x:Name="add_companyNameTextBox" Grid.Row="1" Style="{StaticResource CustTextBox}"
                  Text="{Binding CompanyName, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true }"/>
         <Label Content="Contact Name:" Grid.Row="2" Style="{StaticResource Label}"/>
         <TextBox x:Name="add_contactNameTextBox" Grid.Row="2" Style="{StaticResource CustTextBox}"
                  Text="{Binding ContactName, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true}"/>
         <Label Content="Contact Title:" Grid.Row="3" Style="{StaticResource Label}"/>
         <TextBox x:Name="add_contactTitleTextBox" Grid.Row="3" Style="{StaticResource CustTextBox}"
                  Text="{Binding ContactTitle, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true}"/>
         <Label Content="Address:" Grid.Row="4" Style="{StaticResource Label}"/>
         <TextBox x:Name="add_addressTextBox" Grid.Row="4" Style="{StaticResource CustTextBox}"
                  Text="{Binding Address, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true}"/>
         <Label Content="City:" Grid.Column="1" Grid.Row="0" Style="{StaticResource Label}"/>
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
                         <Button Content="Delete" Command="{StaticResource DeleteOrderCommand}" CommandParameter="{Binding}"/>
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

V aplikacích Windows Forms získejte objekt BindingNavigator pomocí tlačítek pro procházení řádků v databázi a provádění základních operací CRUD. WPF neposkytuje objektu BindingNavigator, ale je docela jednoduché, k jejímu vytvoření. Můžete to udělat pomocí tlačítek v objektu StackPanel vodorovné a přidružit tlačítek s příkazy, které jsou vázány na metody v kódu.

Existují fours části příkazu logiku: (1) příkazy, (2) vazby, (3) tlačítka a (4) obslužné rutiny příkazů v kódu.

### <a name="add-commands-bindings-and-buttons-in-xaml"></a>Přidání příkazů, vazby a tlačítka v XAML

1.  Nejprve přidejte příkazy v *souboru MainWindow.xaml* uvnitř souboru `Windows.Resources` element:

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

2.  Vazbou CommandBinding mapuje `RoutedUICommand` událostí na metodu v kódu. Přidejte tuto `CommandBindings` elementu po `Windows.Resources` uzavírací značku:

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

3.  Teď přidejte `StackPanel` s navigací, přidání, odstranění a aktualizace tlačítka. Nejprve přidejte tento styl `Windows.Resources`:

    ```xaml
    <Style x:Key="NavButton" TargetType="{x:Type Button}" BasedOn="{x:Null}">
        <Setter Property="FontSize" Value="24"/>
        <Setter Property="FontFamily" Value="Segoe UI Symbol"/>
        <Setter Property="Margin" Value="2,2,2,0"/>
        <Setter Property="Width" Value="40"/>
        <Setter Property="Height" Value="auto"/>
    </Style>
    ```

     Za druhé, vložte tento kód hned za `RowDefinitions` pro vnější `Grid` prvek směrem k horní části stránky XAML:

    ```xaml
    <StackPanel Orientation="Horizontal" Margin="2,2,2,0" Height="36" VerticalAlignment="Top" Background="Gainsboro" DataContext="{StaticResource customerViewSource}" d:LayoutOverrides="LeftMargin, RightMargin, TopMargin, BottomMargin">
        <Button Name="btnFirst" Content="|◄" Command="{StaticResource FirstCommand}" Style="{StaticResource NavButton}"/>
        <Button Name="btnPrev" Content="◄" Command="{StaticResource PreviousCommand}" Style="{StaticResource NavButton}"/>
        <Button Name="btnNext" Content="►" Command="{StaticResource NextCommand}" Style="{StaticResource NavButton}"/>
        <Button Name="btnLast" Content="►|" Command="{StaticResource LastCommand}" Style="{StaticResource NavButton}"/>
        <Button Name="btnDelete" Content="Delete Customer" Command="{StaticResource DeleteCustomerCommand}" FontSize="11" Width="120" Style="{StaticResource NavButton}"/>
        <Button Name="btnAdd" Content="New Customer" Command="{StaticResource AddCommand}" FontSize="11" Width="80" Style="{StaticResource NavButton}"/>
        <Button Content="New Order" Name="btnNewOrder" FontSize="11" Width="80" Style="{StaticResource NavButton}" Click="NewOrder_click"/>
        <Button Name="btnUpdate" Content="Commit" Command="{StaticResource UpdateCommand}" FontSize="11" Width="80" Style="{StaticResource NavButton}"/>
        <Button Content="Cancel" Name="btnCancel" Command="{StaticResource CancelCommand}" FontSize="11" Width="80" Style="{StaticResource NavButton}"/>
    </StackPanel>
    ```

### <a name="add-command-handlers-to-the-mainwindow-class"></a>Přidání obslužné rutiny příkazů do třídy hlavního okna MainWindow

Použití modelu code-behind je minimální s výjimkou metody přidat a odstranit. Navigace se provádí pomocí volání metody na vlastnost zobrazení kolekce CollectionViewSource. `DeleteOrderCommandHandler` Ukazuje, jak provádět kaskádové odstranění objednávku. Musíme nejprve odstranit Order_Details, které jsou k ní přidružena. `UpdateCommandHandler` Přidá nového zákazníka nebo pořadí do kolekce, jinak pouze změny provedené uživatelem v textových polích aktualizuje existujícího zákazníka nebo pořadí.

Přidejte tyto metody obslužné rutiny třídy hlavního okna MainWindow v *MainWindow.xaml.cs*. Pokud vaše kolekce CollectionViewSource pro tabulku zákazníků má jiný název, je potřeba upravit název v každém z těchto metod:

[!code-csharp[CommandHandlers#3](../data-tools/codesnippet/CSharp/CreateWPFDataApp/MainWindow.xaml.cs#3)]

## <a name="run-the-application"></a>Spuštění aplikace

Chcete-li spustit ladění, stiskněte **F5**. Měli byste vidět zákazníka a data o objednávkách v mřížce a navigačních tlačítek by měl fungovat podle očekávání. Klikněte na **potvrzení** po zadání data přidání nového zákazníka nebo pořadí modelu. Klikněte na **zrušit** pro zálohování bez uložení dat z nového zákazníka nebo nový formulář objednávky. Můžete provádět úpravy stávající zákazníci a objednávky přímo v textových polích a tyto změny se zapisují do modelu automaticky.

## <a name="see-also"></a>Viz také:

- [Visual Studio Data Tools for .NET](../data-tools/visual-studio-data-tools-for-dotnet.md)
- [Dokumentace Entity Framework](/ef/)