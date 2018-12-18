---
title: Zdrojový kód L2DBForm.XAML | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-csharp
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 624e96d4-6d27-4195-8ac2-2f3835f6c57e
caps.latest.revision: 4
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 291f7ece2c53d168125da32a11e50ca42e19f3fb
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/12/2018
ms.locfileid: "49207685"
---
# <a name="l2dbformxaml-source-code"></a>Zdrojový kód L2DBForm.XAML
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Toto téma obsahuje a popisuje zdrojového souboru XAML [WPF datové vazby pomocí LINQ to XML příklad](../designers/wpf-data-binding-using-linq-to-xml-example.md), L2DBForm.xaml.  
  
## <a name="overall-ui-structure"></a>Celková struktura uživatelského rozhraní  
 Je typické pro projekt WPF, tento soubor obsahuje jeden nadřazený prvek, <xref:System.Windows.Window> – element XML přidružené k odvozené třídě `L2XDBFrom` v `LinqToXmlDataBinding` oboru názvů.  
  
 Je součástí klientské oblasti <xref:System.Windows.Controls.StackPanel> světle modrý na pozadí, který je uveden. Tento panel obsahuje čtyři <xref:System.Windows.Controls.DockPanel> oddělené části uživatelského rozhraní <xref:System.Windows.Controls.Separator> pruhy. Účelem těchto částí je popsána v **poznámky** v [předchozí téma](../designers/walkthrough-linqtoxmldatabinding-example.md).  
  
 Každý oddíl obsahuje popisek, který ji identifikuje. V prvních dvou částech se tento popisek se otočenou o 90 stupňů prostřednictvím <xref:System.Windows.FrameworkElement.LayoutTransform%2A>. Zbývající část obsahuje prvky uživatelského rozhraní, které jsou vhodné pro účely tohoto oddílu: bloky textu, textová pole, tlačítka a tak dále. Někdy podřízený <xref:System.Windows.Controls.StackPanel> použité pro zarovnání tyto podřízené ovládací prvky.  
  
## <a name="window-resource-section"></a>Části okna prostředku  
 Otevírání `<Window.Resources>` značky řádku 9 označuje začátek části okna prostředku. Končí na řádku 35 uzavírací značku.  
  
 `<ObjectDataProvider>` Značky, který zahrnuje řádky 11 až 25, deklaruje <xref:System.Windows.Data.ObjectDataProvider>s názvem `LoadedBooks`, který používá <xref:System.Xml.Linq.XElement> jako zdroj. To <xref:System.Xml.Linq.XElement> je inicializován pomocí analýzy vložený dokument XML ( `CDATA` element). Všimněte si, že se, že mezery, se zachová, i když deklarace vložený dokument XML a i když je analyzován. To bylo provedeno vzhledem k tomu, <xref:System.Windows.Controls.TextBlock> ovládací prvek, který se používá k zobrazení nezpracovaném kódu XML, nemá žádný speciální XML možnosti formátování.  
  
 A konečně <xref:System.Windows.DataTemplate> s názvem `BookTemplate` je definován na řádcích 28 až 34. Tato šablona se používá k zobrazení položek v **Book List** části uživatelského rozhraní. Využívá datová vazba a LINQ na dynamické vlastnosti XML k načtení knihy ID a název knihy prostřednictvím následujících přiřazení:  
  
```  
Text="{Binding Path=Attribute[id].Value}"Text="{Binding Path=Value}"  
```  
  
## <a name="data-binding-code"></a>Data vazební kód  
 Kromě <xref:System.Windows.DataTemplate> použit element, datové vazby v řadě dalších míst v tomto souboru.  
  
 Při otevírání `<StackPanel>` označení řádku 38 <xref:System.Windows.FrameworkElement.DataContext%2A> tohoto panelu je nastavena na `LoadedBooks` poskytovatele dat služeb.  
  
```  
DataContext="{Binding Source={StaticResource LoadedBooks}}  
```  
  
 Díky tomu (na řádku 46) pro <xref:System.Windows.Controls.TextBlock> s názvem `tbRawXml` zobrazíte nezpracovaná XML vazbou na tento zprostředkovatel dat `Xml` vlastnost:  
  
```  
Text="{Binding Path=Xml}"   
```  
  
 <xref:System.Windows.Controls.ListBox> v **Book List** části uživatelského rozhraní na řádcích 58 prostřednictvím 62, nastaví šablonu pro zobrazení položek `BookTemplate` definovaná v části okna prostředku:  
  
```  
ItemTemplate ="{StaticResource BookTemplate}"   
```  
  
 Potom na řádcích 59 prostřednictvím 62, skutečné hodnoty knih, které jsou vázány na toto pole se seznamem:  
  
```  
<ListBox.ItemsSource>  
    <Binding Path="Elements[{http://www.mybooks.com}book]"/>  
</ListBox.ItemsSource>  
```  
  
 Třetí část uživatelského rozhraní **upravit vybrané knihy**, nejdřív vytvoří vazbu <xref:System.Windows.FrameworkElement.DataContext%2A> nadřazené <xref:System.Windows.Controls.StackPanel> aktuálně vybranou položku v z **Book List** části uživatelského rozhraní (řádek 82):  
  
```  
DataContext="{Binding ElementName=lbBooks, Path=SelectedItem}"  
```  
  
 Poté použije obousměrný datové vazby, tak, aby aktuální hodnoty knihy elementy se zobrazí a aktualizuje z tato dvě textová pole v tomto panelu. Vazba dat na dynamické vlastnosti je podobný, který používá v `BookTemplate` data šablony:  
  
```  
Text="{Binding Path=Attribute[id].Value}"...Text="{Binding Path=Value}"  
```  
  
 V poslední části uživatelského rozhraní, **přidat nová kniha**, nepoužívá datové vazby v jeho kód XAML; místo toho takového kódu najdete v jeho zpracování kódu v souboru L2DBForm.xaml.cs událostí.  
  
## <a name="example"></a>Příklad  
  
### <a name="description"></a>Popis  
  
> [!NOTE]
>  Doporučujeme, zkopírujte následující kód níže do editoru kódu, jako je C# editoru zdrojového kódu v sadě Visual Studio, aby čísla řádků bude jednodušší sledovat.  
  
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
 Zdrojový kód jazyka C# pro obslužné rutiny událostí, které jsou spojené s prvky uživatelského rozhraní WPF, naleznete v tématu [zdrojový kód L2DBForm.xaml.cs](../designers/l2dbform-xaml-cs-source-code.md).  
  
## <a name="see-also"></a>Viz také  
 [Návod: Příklad LinqToXmlDataBinding](../designers/walkthrough-linqtoxmldatabinding-example.md)   
 [Zdrojový kód L2DBForm.xaml.cs](../designers/l2dbform-xaml-cs-source-code.md)



