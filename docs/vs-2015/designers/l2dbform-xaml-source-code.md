---
title: Zdrojový kód zdrojový kód L2DBForm. XAML | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-designers
ms.topic: conceptual
ms.assetid: 624e96d4-6d27-4195-8ac2-2f3835f6c57e
caps.latest.revision: 4
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: fc0ec53c35f87751efe78359f582e5f4297143c9
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72664267"
---
# <a name="l2dbformxaml-source-code"></a>Zdrojový kód L2DBForm.xaml
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Toto téma obsahuje a popisuje zdrojový soubor XAML pro [datovou vazbu WPF pomocí LINQ to XML příklad](../designers/wpf-data-binding-using-linq-to-xml-example.md)zdrojový kód L2DBForm. XAML.

## <a name="overall-ui-structure"></a>Celková struktura uživatelského rozhraní
 Jak je typický pro projekt WPF, tento soubor obsahuje jeden nadřazený prvek, <xref:System.Windows.Window> element XML přidružený k odvozené třídě `L2XDBFrom` v oboru názvů `LinqToXmlDataBinding`.

 Klientská oblast je obsažena v <xref:System.Windows.Controls.StackPanel>, kterému je přiděleno světlé modré pozadí. Tento panel obsahuje čtyři oddíly <xref:System.Windows.Controls.DockPanel> uživatelského rozhraní oddělené <xref:System.Windows.Controls.Separator> panely. Účel těchto oddílů je popsaný v části **poznámky** v [předchozím tématu](../designers/walkthrough-linqtoxmldatabinding-example.md).

 Každá část obsahuje popisek, který ho identifikuje. V prvních dvou oddílech je tento popisek otočen 90 stupňů pomocí <xref:System.Windows.FrameworkElement.LayoutTransform%2A>. Zbytek oddílu obsahuje prvky uživatelského rozhraní, které jsou vhodné pro účely tohoto oddílu: textové bloky, textová pole, tlačítka a tak dále. V některých případech je použita podřízená <xref:System.Windows.Controls.StackPanel> k zarovnání těchto podřízených ovládacích prvků.

## <a name="window-resource-section"></a>Oddíl prostředků okna
 Úvodní značka `<Window.Resources>` na řádku 9 označuje začátek oddílu prostředků okna. Končí uzavírací značkou na řádku 35.

 Značka `<ObjectDataProvider>`, která zahrnuje řádky 11 až 25, deklaruje <xref:System.Windows.Data.ObjectDataProvider> s názvem `LoadedBooks`, která jako zdroj používá <xref:System.Xml.Linq.XElement>. Tento <xref:System.Xml.Linq.XElement> je inicializován analýzou vloženého dokumentu XML (`CDATA` elementu). Všimněte si, že prázdné znaky jsou zachovány při deklaraci vloženého dokumentu XML a také při jeho analýze. To bylo provedeno, protože ovládací prvek <xref:System.Windows.Controls.TextBlock>, který slouží k zobrazení nezpracovaného kódu XML, nemá žádné speciální funkce formátování XML.

 Nakonec <xref:System.Windows.DataTemplate> s názvem `BookTemplate` je definována na řádcích 28 až 34. Tato šablona se použije k zobrazení položek v části uživatelské rozhraní **seznamu knih** . Pomocí datových vazeb a LINQ to XML dynamické vlastnosti k získání ID knihy a názvu knihy prostřednictvím následujících přiřazení:

```
Text="{Binding Path=Attribute[id].Value}"Text="{Binding Path=Value}"
```

## <a name="data-binding-code"></a>Kód datové vazby
 Kromě prvku <xref:System.Windows.DataTemplate> se datová vazba používá v několika dalších místech tohoto souboru.

 V úvodní značce `<StackPanel>` na řádku 38 je vlastnost <xref:System.Windows.FrameworkElement.DataContext%2A> tohoto panelu nastavena na `LoadedBooks` poskytovatel dat.

```
DataContext="{Binding Source={StaticResource LoadedBooks}}
```

 To umožňuje (na řádku 46) pro <xref:System.Windows.Controls.TextBlock> s názvem `tbRawXml` zobrazit nezpracovaný kód XML vazbou na vlastnost `Xml` tohoto poskytovatele dat:

```
Text="{Binding Path=Xml}"
```

 @No__t_0 v části uživatelské rozhraní **seznamu knih** na řádcích 58 až 62 nastaví šablonu pro své položky zobrazení na `BookTemplate` definované v části prostředků systému Windows:

```
ItemTemplate ="{StaticResource BookTemplate}"
```

 Pak na řádcích 59 až 62 jsou skutečné hodnoty knih vázány na tento seznam:

```
<ListBox.ItemsSource>
    <Binding Path="Elements[{http://www.mybooks.com}book]"/>
</ListBox.ItemsSource>
```

 Třetí oddíl uživatelského rozhraní, **Upravit vybranou knihu**, nejprve váže <xref:System.Windows.FrameworkElement.DataContext%2A> nadřazených <xref:System.Windows.Controls.StackPanel> k aktuálně vybrané položce v části uživatelského rozhraní **seznamu knih** (řádek 82):

```
DataContext="{Binding ElementName=lbBooks, Path=SelectedItem}"
```

 Potom používá obousměrnou datovou vazbu, aby se aktuální hodnoty prvků knihy zobrazovaly a aktualizovaly z obou textových polí na tomto panelu. Datová vazba na dynamické vlastnosti je podobná použití v šabloně `BookTemplate` dat:

```
Text="{Binding Path=Attribute[id].Value}"...Text="{Binding Path=Value}"
```

 Poslední oddíl uživatelského rozhraní, **Přidat novou knihu**, nepoužívá datovou vazbu ve svém kódu XAML; místo toho lze takový kód najít v kódu zpracování události v souboru L2DBForm.xaml.cs.

## <a name="example"></a>Příklad

### <a name="description"></a>Popis

> [!NOTE]
> Doporučujeme zkopírovat následující kód níže do editoru kódu, jako je C# například editor zdrojového kódu v aplikaci Visual Studio, aby bylo číslování řádků snazší sledovat.

### <a name="code"></a>Kód

```xml
<Window x:Class="LinqToXmlDataBinding.L2XDBForm"
    xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
    xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
    xmlns:system="clr-namespace:System;assembly=mscorlib"
    xmlns:xlinq="clr-namespace:System.Xml.Linq;assembly=System.Xml.Linq"
    xmlns:local="clr-namespace:LinqToXmlDataBinding"
    Title="WPF Data Binding using LINQ-to-XML" Height="665" Width="500" ResizeMode="NoResize">

    <Window.Resources>
        <!-- Books provider and inline data -->
        <ObjectDataProvider x:Key="LoadedBooks" ObjectType="{x:Type xlinq:XElement}" MethodName="Parse">
            <ObjectDataProvider.MethodParameters>
                <system:String xml:space="preserve">
<![CDATA[
<books xmlns="http://www.mybooks.com">
  <book id="0">book zero</book>
  <book id="1">book one</book>
  <book id="2">book two</book>
  <book id="3">book three</book>
</books>
]]>
                </system:String>
                <xlinq:LoadOptions>PreserveWhitespace</xlinq:LoadOptions>
            </ObjectDataProvider.MethodParameters>
        </ObjectDataProvider>

        <!-- Template for use in Books List listbox. -->
        <DataTemplate x:Key="BookTemplate">
            <StackPanel Orientation="Horizontal">
                <TextBlock Margin="3" Text="{Binding Path=Attribute[id].Value}"/>
                <TextBlock Margin="3" Text="-"/>
                <TextBlock Margin="3" Text="{Binding Path=Value}"/>
            </StackPanel>
        </DataTemplate>
    </Window.Resources>

    <!-- Main visual content container -->
    <StackPanel Background="lightblue" DataContext="{Binding Source={StaticResource LoadedBooks}}">
        <!-- Raw XML display section -->
        <DockPanel Margin="5">
            <Label  Background="Gray" FontSize="12" BorderBrush="Black" BorderThickness="1" FontWeight="Bold">XML
            <Label.LayoutTransform>
                <RotateTransform Angle="90"/>
            </Label.LayoutTransform>
            </Label>
            <TextBlock Name="tbRawXml" Height="200" Background="LightGray" Text="{Binding Path=Xml}" TextTrimming="CharacterEllipsis" />
        </DockPanel>

        <Separator Height="4" Margin="5" />

        <!-- List box to display all books section -->
        <DockPanel Margin="5">
            <Label  Background="Gray" FontSize="12" BorderBrush="Black" BorderThickness="1" FontWeight="Bold">Book List
                <Label.LayoutTransform>
                    <RotateTransform Angle="90"/>
                </Label.LayoutTransform>
            </Label>
            <ListBox Name="lbBooks" Height="200" Width="415" ItemTemplate ="{StaticResource BookTemplate}">
                <ListBox.ItemsSource>
                    <Binding Path="Elements[{http://www.mybooks.com}book]"/>
                </ListBox.ItemsSource>
            </ListBox>
            <Button Margin="5" DockPanel.Dock="Right" Height="30" Width ="130" Content="Remove Selected Book" Click="OnRemoveBook">
            <Button.LayoutTransform>
                <RotateTransform Angle="90"/>
            </Button.LayoutTransform>
            </Button>
        </DockPanel>

        <Separator Height="4" Margin="5" />

        <!-- Edit current selection section -->
        <DockPanel Margin="5">
            <TextBlock Margin="5" Height="30" Width="65" DockPanel.Dock="Right" Background="LightGray" TextWrapping="Wrap" TextAlignment="Center">
                    Changes are live!
                <TextBlock.LayoutTransform>
                    <RotateTransform Angle="90"/>
                </TextBlock.LayoutTransform>
            </TextBlock>
            <StackPanel>
                <Label Width="450" Background="Gray" FontSize="12" BorderBrush="Black" BorderThickness="1" HorizontalAlignment="Left" FontWeight="Bold">Edit Selected Book</Label>
                <StackPanel Margin="1" DataContext="{Binding ElementName=lbBooks, Path=SelectedItem}">
                    <StackPanel Orientation="Horizontal">
                        <Label Width="40">ID:</Label>
                        <TextBox Name="editAttributeTextBox" Width="410" Text="{Binding Path=Attribute[id].Value}">
                            <TextBox.ToolTip>
                                <TextBlock FontWeight="Bold" TextAlignment="Center">
                                    <Label>Edit the selected book ID and see it changed.</Label>
                                </TextBlock>
                            </TextBox.ToolTip>
                        </TextBox>
                    </StackPanel>
                    <StackPanel Orientation="Horizontal">
                        <Label Width="40">Value:</Label>
                        <TextBox Name="editValueTextBox" Width="410" Text="{Binding Path=Value}" Height="25">
                            <TextBox.ToolTip>
                                <TextBlock FontWeight="Bold" TextAlignment="Center">
                                    <Label>Edit the selected book Value and see it changed.</Label>
                                </TextBlock>
                            </TextBox.ToolTip>
                        </TextBox>
                    </StackPanel>
                </StackPanel>
            </StackPanel>
        </DockPanel>

        <Separator Height="4" Margin="5" />

        <!-- Add new book section -->
        <DockPanel Margin="5">
            <Button Margin="5" Height="30" DockPanel.Dock="Right" Click ="OnAddBook">Add Book
                <Button.LayoutTransform>
                    <RotateTransform Angle="90"/>
                </Button.LayoutTransform>
            </Button>
            <StackPanel>
                <Label Width="450" Background="Gray" FontSize="12" BorderBrush="Black" BorderThickness="1" HorizontalAlignment="Left" FontWeight="Bold">Add New Book</Label>
                <StackPanel Margin="1">
                    <StackPanel Orientation="Horizontal">
                        <Label Width="40">ID:</Label>
                        <TextBox Name="tbAddID" Width="410">
                            <TextBox.ToolTip>
                                <TextBlock FontWeight="Bold" TextAlignment="Center">
                                    <Label>Enter a book ID and Value pair, then click Add Book.</Label>
                                </TextBlock>
                            </TextBox.ToolTip>
                        </TextBox>
                    </StackPanel>
                    <StackPanel Orientation="Horizontal">
                        <Label Width="40">Value:</Label>
                        <TextBox Name="tbAddValue" Width="410" Height="25">
                            <TextBox.ToolTip>
                                <TextBlock FontWeight="UltraBold" TextAlignment="Center">
                                    <Label>Enter a book ID and Value pair, then click Add Book.</Label>
                                </TextBlock>
                            </TextBox.ToolTip>
                        </TextBox>
                    </StackPanel>
                </StackPanel>
            </StackPanel>
        </DockPanel>
    </StackPanel>
</Window>

```

### <a name="comments"></a>Komentáře
 C# Zdrojový kód obslužných rutin událostí přidružených k PRVKŮM uživatelského rozhraní WPF naleznete v tématu [L2DBForm.XAML.cs Source Code](../designers/l2dbform-xaml-cs-source-code.md).

## <a name="see-also"></a>Viz také
 [Návod: příkladu LinqToXmlDataBinding příklad](../designers/walkthrough-linqtoxmldatabinding-example.md) [L2DBForm.XAML.cs zdrojového kódu](../designers/l2dbform-xaml-cs-source-code.md)
