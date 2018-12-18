---
title: Vytvořit vazbu s daty v Návrháři XAML
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-designers
ms.topic: conceptual
f1_keywords:
- VS.XamlDesigner.DataBinding
dev_langs:
- CSharp
- VB
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- uwp
ms.openlocfilehash: f1effd15666839b6e48bcebf46120585c4cfc36c
ms.sourcegitcommit: 1ab675a872848c81a44d6b4bd3a49958fe673c56
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/10/2018
ms.locfileid: "44282882"
---
# <a name="walkthrough-bind-to-data-in-xaml-designer"></a>Návod: Vazba s daty v Návrháři XAML

V Návrháři XAML můžete nastavit vlastnosti datové vazby pomocí návrhové ploše nebo v okně Vlastnosti. V příkladu v tomto návodu ukazuje, jak k vytvoření vazby dat k ovládacímu prvku. Konkrétně návodu ukazuje, jak vytvořit jednoduchou nákupního košíku třídu, která má [DependencyProperty](/uwp/api/Windows.UI.Xaml.DependencyProperty) s názvem `ItemCount`a pak vytvoříte vazbu `ItemCount` vlastnost **Text** vlastnost nástroje [TextBlock](/uwp/api/Windows.UI.Xaml.Controls.TextBlock) ovládacího prvku.

## <a name="to-create-a-class-to-use-as-a-data-source"></a>Pro vytvoření třídy, který se použije jako zdroj dat

1. Na **souboru** nabídce zvolte **nový** > **projektu**.

1. V **nový projekt** dialogového okna zvolte buď **Visual C#** nebo **jazyka Visual Basic** uzlu, rozbalte **Windows Desktop** uzel a pak Zvolte **aplikace WPF** šablony.

1. Pojmenujte projekt **BindingTest**a klikněte na tlačítko **OK** tlačítko.

1. Otevřít **MainWindow.xaml.cs** (nebo **soubor MainWindow.xaml.vb**) a přidejte následující kód. V jazyce C#, přidejte kód `BindingTest` obor názvů (před posledním pravou závorku v souboru). V jazyce Visual Basic přidejte novou třídu.

   ```csharp
   public class ShoppingCart : DependencyObject
   {
       public int ItemCount
       {
           get { return (int)GetValue(ItemCountProperty); }
           set { SetValue(ItemCountProperty, value); }
       }

       public static readonly DependencyProperty ItemCountProperty =
            DependencyProperty.Register("ItemCount", typeof(int),
            typeof(ShoppingCart), new PropertyMetadata(0));
   }
   ```

   ```vb
   Public Class ShoppingCart
       Inherits DependencyObject

       Public Shared ReadOnly ItemCountProperty As DependencyProperty = DependencyProperty.Register(
            "ItemCount", GetType(Integer), GetType(ShoppingCart), New PropertyMetadata(0))
       Public Property ItemCount As Integer
           Get
               ItemCount = CType(GetValue(ItemCountProperty), Integer)
           End Get
           Set(value As Integer)
               SetValue(ItemCountProperty, value)
           End Set
       End Property
   End Class
   ```

   Tento kód nastaví hodnotu 0 jako počet položek výchozí pomocí [třída PropertyMetadata](/uwp/api/Windows.UI.Xaml.PropertyMetadata) objektu.

1. Na **souboru** nabídce zvolte **sestavení** > **sestavit řešení**.

## <a name="to-bind-the-itemcount-property-to-a-textblock-control"></a>Vlastnost ItemCount vázat na ovládací prvek TextBlock

1. V Průzkumníku řešení otevřete místní nabídku pro **souboru MainWindow.xaml** a zvolte **Návrhář zobrazení**.

1. Na panelu nástrojů zvolte [mřížky](/uwp/api/Windows.UI.Xaml.Controls.Grid) ovládací prvek a přidat do formuláře.

1. S `Grid` vybrán, v okně Vlastnosti zvolte **nový** vedle **DataContext** vlastnost.

1. V **vybrat objekt** dialogové okno pole, ujistěte se, že **ukázat všechna sestavení** zrušeno zaškrtnutí políčka, zvolte **ShoppingCart** pod **BindingTest** obor názvů a klikněte na tlačítko **OK** tlačítko.

     Je vidět na následujícím obrázku **vybrat objekt** dialogové okno s **ShoppingCart** vybrané.

     ![Dialogové okno Vybrat objekt](../designers/media/blendselectobject.png)

1. V **nástrojů**, zvolte `TextBlock` ovládací prvek pro přidání do formuláře.

1. S `TextBlock` ovládací prvek vybrán, v okně Vlastnosti zvolte značku vlastnost napravo od **Text** vlastnost a klikněte na tlačítko **vytvořit datovou vazbu**. (Značka vlastnosti vypadá jako malé pole.)

1. V datech vytvořit vazby v dialogovém okně **cesta** zvolte **ItemCount: (int32)** vlastnosti a klikněte na tlačítko **OK** tlačítko.

     Je vidět na následujícím obrázku **vytvořit datovou vazbu** dialogové okno s **ItemCount** vybrané vlastnosti.

     ![Vytvoření datové vazby dialogového okna](../designers/media/xaml_create_data_binding.png)

1. Stisknutím klávesy **F5** ke spuštění aplikace.

     `TextBlock` Ovládací prvek zobrazovat výchozí hodnotu 0 jako text.

## <a name="see-also"></a>Viz také:

- [Vytvoření uživatelského rozhraní pomocí Návrháře XAML](../designers/creating-a-ui-by-using-xaml-designer-in-visual-studio.md)
- [Přidat převaděč hodnot – dialogové okno](https://msdn.microsoft.com/library/c5f3d110-a541-4b55-8bca-928f77778af8)