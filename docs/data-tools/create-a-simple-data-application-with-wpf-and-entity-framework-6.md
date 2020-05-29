---
title: Jednoduchá datová aplikace s WPF a Entity Framework 6
ms.date: 08/22/2017
ms.topic: conceptual
dev_langs:
- CSharp
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 735a4cc533312bcfa3823410780b09caa4f53fde
ms.sourcegitcommit: d20ce855461c240ac5eee0fcfe373f166b4a04a9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/29/2020
ms.locfileid: "84173938"
---
# <a name="create-a-simple-data-application-with-wpf-and-entity-framework-6"></a>Vytvoření jednoduché datové aplikace pomocí WPF a Entity Framework 6

Tento návod ukazuje, jak vytvořit základní aplikaci "Forms over data" v aplikaci Visual Studio. Aplikace používá SQL Server LocalDB, databázi Northwind Entity Framework 6 a Windows Presentation Foundation. Ukazuje, jak provést základní datovou vazbu pomocí zobrazení hlavní-podrobnosti a má také vlastní navigátor vazby s tlačítky pro přesunutí na **Další**, **přesunout předchozí**, **přesunout na začátek**, **přesunout na konec**, **aktualizovat** a **Odstranit**.

Tento článek se zaměřuje na použití datových nástrojů v aplikaci Visual Studio a nepokouší se vysvětlovat základní technologie v jakékoli hloubce. Předpokládá, že máte základní znalosti v jazyce XAML, Entity Framework a SQL. Tento příklad také neukazuje architekturu Model-View-ViewModel (MVVM), která je standardem pro aplikace WPF. Tento kód však můžete zkopírovat do vlastní aplikace MVVM s malým počtem úprav.

## <a name="install-and-connect-to-northwind"></a>Instalace a připojení k databázi Northwind

V tomto příkladu se používá SQL Server Express LocalDB a ukázková databáze Northwind. Pokud poskytovatel dat ADO.NET pro daný produkt podporuje Entity Framework, měla by fungovat i s jinými produkty SQL Database.

1. Pokud nemáte SQL Server Express LocalDB, nainstalujte ji buď ze [stránky pro stažení SQL Server Express](https://www.microsoft.com/sql-server/sql-server-editions-express), nebo prostřednictvím **instalační program pro Visual Studio**. V **instalační program pro Visual Studio**můžete nainstalovat SQL Server Express LocalDB jako součást úlohy **vývoj desktopových** aplikací pro .NET nebo jako jednotlivé komponenty.

2. Nainstalujte ukázkovou databázi Northwind pomocí následujících kroků:

    1. V aplikaci Visual Studio otevřete okno **Průzkumník objektů systému SQL Server** . (**Průzkumník objektů systému SQL Server** je nainstalován v rámci úlohy **úložiště dat a zpracování** v **instalační program pro Visual Studio**.) Rozbalte uzel **SQL Server** . Klikněte pravým tlačítkem na instanci LocalDB a vyberte **Nový dotaz**.

       Otevře se okno editoru dotazů.

    2. Zkopírujte [skript Transact-SQL Northwind](https://github.com/MicrosoftDocs/visualstudio-docs/blob/master/docs/data-tools/samples/northwind.sql?raw=true) do schránky. Tento skript T-SQL vytvoří databázi Northwind od začátku a naplní ji daty.

    3. Vložte skript T-SQL do editoru dotazů a pak klikněte na tlačítko **Spustit** .

       Po krátké době se dotaz dokončí a vytvoří se databáze Northwind.

3. [Přidejte nová připojení](../data-tools/add-new-connections.md) pro Northwind.

## <a name="configure-the-project"></a>Konfigurace projektu

1. V aplikaci Visual Studio vytvořte nový projekt **aplikace WPF** pro C#.

2. Přidejte balíček NuGet pro Entity Framework 6. V **Průzkumník řešení**vyberte uzel projektu. V hlavní nabídce vyberte **projekt**  >  **Spravovat balíčky NuGet**.

     ![Položka nabídky spravovat balíčky NuGet](../data-tools/media/raddata_vs2015_manage_nuget_packages.png)

3. Ve **Správci balíčků NuGet**klikněte na odkaz **Procházet** . Entity Framework je pravděpodobně horním balíčkem v seznamu. V pravém podokně klikněte na **instalovat** a postupujte podle pokynů. V okně výstup se zobrazí informace o dokončení instalace.

     ![Entity Framework balíček NuGet](../data-tools/media/raddata_vs2015_nuget_ef.png)

4. Nyní můžete pomocí sady Visual Studio vytvořit model založený na databázi Northwind.

## <a name="create-the-model"></a>Vytvoření modelu

1. V **Průzkumník řešení** klikněte pravým tlačítkem myši na uzel projektu a vyberte možnost **Přidat**  >  **novou položku**. V levém podokně v uzlu C# vyberte **data** a v prostředním podokně vyberte **ADO.NET model EDM (Entity Data Model)**.

   ![Nová položka modelu Entity Framework](../data-tools/media/raddata-ef-new-project-item.png)

2. Zavolejte model `Northwind_model` a klikněte na **tlačítko OK**. Otevře se **průvodce model EDM (Entity Data Model)** . Zvolte **Návrhář EF z databáze** a pak klikněte na **Další**.

   ![Model EF z databáze](../data-tools/media/raddata-ef-model-from-database.png)

3. Na další obrazovce zadejte nebo zvolte připojení Northwind LocalDB (například (LocalDB) \MSSQLLocalDB), zadejte databázi Northwind a klikněte na **Další**.

4. Na další stránce průvodce vyberte, které tabulky, uložené procedury a další databázové objekty se mají zahrnout do modelu Entity Framework. Rozbalte uzel dbo ve stromovém zobrazení a vyberte podrobnosti o **zákaznících**, **objednávkách**a **objednávkách**. Ponechte vybrané výchozí hodnoty a klikněte na **Dokončit**.

    ![Výběr databázových objektů pro model](../data-tools/media/raddata-choose-ef-objects.png)

5. Průvodce generuje třídy jazyka C#, které reprezentují Entity Framework model. Třídy jsou prosté staré třídy C# a jsou to, co provádíme v uživatelském rozhraní WPF. Soubor *. edmx* popisuje vztahy a další metadata, která přidružuje třídy k objektům v databázi. Soubory *. TT* jsou šablony T4, které generují kód, který pracuje na modelu a ukládá změny do databáze. Všechny tyto soubory můžete zobrazit v **Průzkumník řešení** pod uzlem Northwind_model:

      ![Průzkumník řešení soubory modelu EF](../data-tools/media/raddata-solution-explorer-ef-model-files.png)

    Plocha návrháře pro soubor *. edmx* umožňuje upravit některé vlastnosti a relace v modelu. V tomto návodu nebudeme používat návrháře.

6. Soubory *. TT* jsou pro obecné účely a Vy musíte pro práci s datovou vazbou WPF, která vyžaduje ObservableCollections, selepšit jednu z nich. V **Průzkumník řešení**rozbalte uzel Northwind_model, dokud nenajdete *Northwind_model. TT*. (Ujistěte se, že nejste v *. Soubor Context.tt* , který je přímo pod souborem *. edmx* .)

   - Nahraďte dva výskyty <xref:System.Collections.ICollection> řetězcem <xref:System.Collections.ObjectModel.ObservableCollection%601> .

   - Nahraďte první výskyt <xref:System.Collections.Generic.HashSet%601> <xref:System.Collections.ObjectModel.ObservableCollection%601> kolem řádku 51. Neměňte druhý výskyt HashSet –.

   - Nahradí jediný výskyt <xref:System.Collections.Generic> (kolem řádku 431) s <xref:System.Collections.ObjectModel> .

7. Stisknutím **kombinace kláves CTRL** + **+ SHIFT** + **B** Sestavte projekt. Po dokončení sestavení jsou třídy modelu viditelné v průvodci zdroji dat.

Nyní jste připraveni připojit tento model na stránku XAML, abyste mohli zobrazit, navigovat a upravovat data.

## <a name="databind-the-model-to-the-xaml-page"></a>Vázání modelu na stránku XAML

Je možné napsat vlastní kód datové vazby, ale je mnohem jednodušší, aby to Visual Studio prodali za vás.

1. V hlavní nabídce vyberte možnost **projekt**  >  **Přidat nový zdroj dat** a zobrazte tak **Průvodce konfigurací zdroje dat**. Vyberte **objekt** , protože vytváříte vazbu na třídy modelů, nikoli na databázi:

     ![Průvodce konfigurací zdroje dat se zdrojem objektů](../data-tools/media/raddata-data-source-configuration-wizard-with-object-source.png)

2. Rozbalte uzel pro svůj projekt a vyberte možnost **Zákazník**. (Zdroje pro objednávky se automaticky generují z vlastnosti navigace objednávky u zákazníka.)

     ![Přidání tříd entit jako zdrojů dat](../data-tools/media/raddata-add-entity-classes-as-data-sources.png)

3. Klikněte na **Finish** (Dokončit).

4. V zobrazení kód přejděte na *MainWindow. XAML* . Pro účely tohoto příkladu udržujeme kódování XAML jednoduché. Změňte název MainWindow na výstižnější a zvyšte jeho výšku a šířku na 600 x 800. Kdykoli ho můžete později změnit. Nyní přidejte tyto tři definice řádků do hlavní mřížky, jeden řádek pro navigační tlačítka, jednu pro podrobnosti o zákazníkovi a jednu pro mřížku, která zobrazuje jejich objednávky:

    ```xaml
        <Grid.RowDefinitions>
            <RowDefinition Height="auto"/>
            <RowDefinition Height="auto"/>
            <RowDefinition Height="*"/>
        </Grid.RowDefinitions>
    ```

5. Nyní otevřete *MainWindow. XAML* , abyste si ho prohlíželi v návrháři. To způsobí, že se okno **zdroje dat** zobrazí jako možnost v okraji okna aplikace Visual Studio vedle panelu **nástrojů**. Kliknutím na kartu otevřete okno, nebo stiskněte klávesu **SHIFT** + **ALT +** + **D** nebo zvolte možnost **Zobrazit**  >  **ostatní**  >  **zdroje dat**Windows. Všechny vlastnosti ve třídě Customers (zákazníci) se zobrazí v samostatném textovém poli. Nejdřív klikněte na šipku v poli se seznamem **Customers (zákazníci** ) a vyberte **Podrobnosti**. Pak přetáhněte uzel do střední části návrhové plochy, aby Návrhář věděl, že má přejít na prostřední řádek. Pokud k tomu dojde, můžete řádek zadat později v jazyce XAML. Ve výchozím nastavení jsou ovládací prvky umístěny vertikálně v prvku mřížky, ale v tomto okamžiku je můžete uspořádat tak, jak chcete, například na formuláři. Může být například vhodné umístit textové pole **název** nahoře nad adresu. Ukázková aplikace pro tento článek mění pořadí polí a mění jejich uspořádání do dvou sloupců.

     ![Vazba zdroje dat zákazníků na jednotlivé ovládací prvky](../data-tools/media/raddata-customers-data-source-binding-to-individual-controls.png)

     V zobrazení kódu teď můžete zobrazit nový `Grid` prvek v řádku 1 (prostřední řádek) nadřazené mřížky. Nadřazená mřížka má `DataContext` atribut, který odkazuje na CollectionViewSource, který byl přidán do `Windows.Resources` elementu. Vzhledem k tomuto kontextu dat, když se první textové pole váže na **adresu**, je tento název namapován na `Address` vlastnost v aktuálním `Customer` objektu v CollectionViewSource.

    ```xaml
    <Grid DataContext="{StaticResource customerViewSource}">
    ```

6. Když se zákazník zobrazí v horní polovině okna, budete chtít zobrazit jeho objednávky v dolní polovině. Objednávky zobrazíte v jednom ovládacím prvku zobrazení mřížky. Pro datovou vazbu hlavní-podrobnosti, která bude fungovat podle očekávání, je důležité vytvořit vazbu na vlastnost Orders ve třídě Customers, nikoli na uzel samostatné objednávky. Přetáhněte vlastnost Orders třídy Customers na spodní polovinu formuláře, aby ho Návrhář na řádku 2 vloží:

     ![Přetahovat třídy Orders jako Grid](../data-tools/media/raddata-drag-orders-classes-as-grid.png)

7. Aplikace Visual Studio vygenerovala veškerý kód vazby, který spojuje ovládací prvky uživatelského rozhraní s událostmi v modelu. K tomu, abyste mohli zobrazit nějaká data, je třeba napsat nějaký kód pro naplnění modelu. Nejprve přejděte na *MainWindow.XAML.cs* a přidejte datový člen do třídy MainWindow pro datový kontext. Tento objekt, který byl vygenerován pro vás, funguje podobně jako ovládací prvek, který sleduje změny a události v modelu. Přidáte také CollectionViewSource datové členy pro zákazníky a objednávky a logiku inicializace přidruženého konstruktoru. Horní část třídy by měla vypadat takto:

     [!code-csharp[MainWindow#1](../data-tools/codesnippet/CSharp/CreateWPFDataApp/MainWindow.xaml.cs#1)]

     Přidejte `using` direktivu pro System. data. entity, která načte metodu rozšíření Load do oboru:

     ```csharp
     using System.Data.Entity;
     ```

     Teď se posuňte dolů a najděte `Window_Loaded` obslužnou rutinu události. Všimněte si, že Visual Studio přidalo objekt CollectionViewSource. To představuje objekt NorthwindEntities, který jste vybrali při vytváření modelu. Přidali jste už, takže ho tady nebudete potřebovat. Pojďme kód nahradit `Window_Loaded` , aby metoda teď vypadala takto:

     [!code-csharp[Window_Loaded#2](../data-tools/codesnippet/CSharp/CreateWPFDataApp/MainWindow.xaml.cs#2)]

8. Stiskněte klávesu **F5**. Měli byste vidět podrobnosti o prvním zákazníkovi, který se načetl do CollectionViewSource. Měli byste také vidět jejich objednávky v datové mřížce. Formátování není Skvělé, takže pojďme opravit. Můžete také vytvořit způsob zobrazení dalších záznamů a provést základní operace CRUD.

## <a name="adjust-the-page-design-and-add-grids-for-new-customers-and-orders"></a>Upravte návrh stránky a přidejte mřížku pro nové zákazníky a objednávky.

Výchozí uspořádání vytvořené aplikací Visual Studio není ideální pro vaši aplikaci, proto poskytneme sem konečný kód XAML, který bude zkopírován do kódu. K tomu, aby uživatel mohl přidat nového zákazníka nebo objednávku, potřebujete také některé "formy" (které jsou ve skutečnosti Gridy). Aby bylo možné přidat nového zákazníka a objednávku, potřebujete samostatnou sadu textových polí, která nejsou vázaná na data na `CollectionViewSource` . Nastavením vlastnosti Visible v metodách obslužné rutiny určíte, která mřížka se uživateli v daném čase uvidí. Nakonec přidáte tlačítko Odstranit do každého řádku v mřížce objednávky, aby uživatel mohl odstranit individuální objednávku.

Nejprve přidejte tyto styly do `Windows.Resources` prvku v souboru *MainWindow. XAML*:

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
         <Label Content="Contact title:" Grid.Row="3" Style="{StaticResource Label}"/>
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
         <Label Content="Contact title:" Grid.Row="3" Style="{StaticResource Label}"/>
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

## <a name="add-buttons-to-navigate-add-update-and-delete"></a>Přidání tlačítek pro navigaci, přidávání, aktualizaci a odstraňování

V model Windows Formsch aplikacích získáte objekt BindingNavigator s tlačítky pro procházení řádků v databázi a provádění základních operací CRUD. WPF neposkytuje objekt BindingNavigator, ale je dostatečně snadné ho vytvořit. Uděláte to s tlačítky uvnitř horizontálního StackPanel a přidružíte tlačítka k příkazům, které jsou vázány na metody v kódu na pozadí.

Příkazová logika obsahuje čtyři části: (1) příkazy, (2) vazby, (3) tlačítka a (4) obslužné rutiny příkazu v kódu na pozadí.

### <a name="add-commands-bindings-and-buttons-in-xaml"></a>Přidání příkazů, vazeb a tlačítek v jazyce XAML

1. Nejprve přidejte do souboru *MainWindow. XAML* příkazy v rámci `Windows.Resources` elementu:

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

2. CommandBinding mapuje `RoutedUICommand` událost na metodu v kódu na pozadí. Přidejte tento `CommandBindings` prvek za `Windows.Resources` uzavírací značku:

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

3. Nyní přidejte `StackPanel` tlačítka s tlačítky navigace, přidat, odstranit a aktualizovat. Nejprve přidejte tento styl do `Windows.Resources` :

    ```xaml
    <Style x:Key="NavButton" TargetType="{x:Type Button}" BasedOn="{x:Null}">
        <Setter Property="FontSize" Value="24"/>
        <Setter Property="FontFamily" Value="Segoe UI Symbol"/>
        <Setter Property="Margin" Value="2,2,2,0"/>
        <Setter Property="Width" Value="40"/>
        <Setter Property="Height" Value="auto"/>
    </Style>
    ```

     Za druhé vložte tento kód hned za `RowDefinitions` vnější `Grid` prvek směrem k hornímu okraji stránky XAML:

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

### <a name="add-command-handlers-to-the-mainwindow-class"></a>Přidání obslužných rutin příkazů do třídy MainWindow

Kód na pozadí je minimální s výjimkou metod Add a DELETE. Navigace je prováděna voláním metod ve vlastnosti zobrazení CollectionViewSource. `DeleteOrderCommandHandler`Ukazuje, jak provést kaskádovou odstranění na základě objednávky. Musíme nejdřív odstranit Order_Details, které jsou k němu přidružené. `UpdateCommandHandler`Přidá do kolekce nového zákazníka nebo objednávku nebo jinak pouze aktualizuje stávajícího zákazníka nebo objednávky změnami, které uživatel provedl v textových polích.

Přidejte tyto metody obslužné rutiny do třídy MainWindow v *MainWindow.XAML.cs*. Pokud má CollectionViewSource pro tabulku Customers jiný název, je nutné upravit název v každé z těchto metod:

[!code-csharp[CommandHandlers#3](../data-tools/codesnippet/CSharp/CreateWPFDataApp/MainWindow.xaml.cs#3)]

## <a name="run-the-application"></a>Spuštění aplikace

Ladění spustíte stisknutím klávesy **F5**. Měli byste vidět, že se data o zákaznících a objednávkách v mřížce naplní, a navigační tlačítka by měla fungovat podle očekávání. Po zadání dat klikněte na **Potvrdit** a přidejte nového zákazníka nebo objednávku do modelu. Klikněte na tlačítko **Zrušit** pro zálohování nového zákazníka nebo nového formuláře objednávky bez uložení dat. Můžete provádět úpravy stávajících zákazníků a objednávek přímo v textových polích a tyto změny se zapisují do modelu automaticky.

## <a name="see-also"></a>Viz také

- [Visual Studio Data Tools for .NET](../data-tools/visual-studio-data-tools-for-dotnet.md)
- [Dokumentace k Entity Framework](/ef/)
