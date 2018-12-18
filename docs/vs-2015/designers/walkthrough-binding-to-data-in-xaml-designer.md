---
title: 'Návod: Vazba s daty v Návrháři XAML | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- VS.XamlDesigner.DataBinding
ms.assetid: 1a99aeae-c3ef-407d-ba79-b8055489a43d
caps.latest.revision: 22
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 597145da912c8d80508b67f4ff47c901f5ccac1d
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/12/2018
ms.locfileid: "49298763"
---
# <a name="walkthrough-binding-to-data-in-xaml-designer"></a>Návod: Vazba s daty v Návrháři XAML
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

V Návrháři XAML můžete nastavit vlastnosti datové vazby pomocí návrhové ploše nebo v okně Vlastnosti. V příkladu v tomto návodu ukazuje, jak k vytvoření vazby dat k ovládacímu prvku. Konkrétně návodu ukazuje, jak vytvořit jednoduchou nákupního košíku třídu, která má [DependencyProperty](http://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.dependencyproperty.aspx) s názvem `ItemCount`a pak vytvoříte vazbu `ItemCount` vlastnost **Text** vlastnost nástroje [TextBlock](http://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.textblock.aspx) ovládacího prvku.  
  
### <a name="to-create-a-class-to-use-as-a-data-source"></a>Pro vytvoření třídy, který se použije jako zdroj dat  
  
1.  Na **souboru** nabídce zvolte **nový**, **projektu**.  
  
2.  V **nový projekt** dialogového okna zvolte buď **Visual C#** nebo **jazyka Visual Basic** uzlu, rozbalte **Windows Desktop** uzel a pak Zvolte **aplikace WPF** šablony.  
  
3.  Pojmenujte projekt **BindingTest**a klikněte na tlačítko **OK** tlačítko.  
  
4.  Otevřete soubor MainWindow.xaml.cs (nebo soubor MainWindow.xaml.vb) a přidejte následující kód. V jazyce C#, přidejte kód `BindingTest` obor názvů (před posledním pravou závorku v souboru). V jazyce Visual Basic přidejte novou třídu.  
  
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
  
     Tento kód nastaví hodnotu 0 jako počet položek výchozí pomocí [třída PropertyMetadata](http://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.propertymetadata.aspx) objektu.  
  
5.  Na **souboru** nabídce zvolte **sestavení**, **sestavit řešení**.  
  
### <a name="to-bind-the-itemcount-property-to-a-textblock-control"></a>Vlastnost ItemCount vázat na ovládací prvek TextBlock  
  
1.  V Průzkumníku řešení otevřete místní nabídku souboru mainwindow.XAML a zvolte **Návrhář zobrazení**.  
  
2.  Na panelu nástrojů zvolte [mřížky](http://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.grid.aspx) ovládací prvek a přidat do formuláře.  
  
3.  S `Grid` vybrán, v okně Vlastnosti zvolte **nový** vedle **DataContext** vlastnost.  
  
4.  V **vybrat objekt** dialogové okno pole, ujistěte se, že **ukázat všechna sestavení** zrušeno zaškrtnutí políčka, zvolte **ShoppingCart** pod **BindingTest** obor názvů a klikněte na tlačítko **OK** tlačítko.  
  
     Je vidět na následujícím obrázku **vybrat objekt** dialogové okno s **ShoppingCart** vybrané.  
  
     ![Dialogové okno Vybrat objekt](../designers/media/blendselectobject.PNG "BlendSelectObject")  
  
5.  V **nástrojů**, zvolte `TextBlock` ovládací prvek pro přidání do formuláře.  
  
6.  S `TextBlock` ovládací prvek vybrán, v okně Vlastnosti zvolte značku vlastnost napravo od **Text** vlastnost a klikněte na tlačítko **vytvořit datovou vazbu**. (Značka vlastnosti vypadá jako malé pole.)  
  
7.  V datech vytvořit vazby v dialogovém okně **cesta** zvolte **ItemCount: (int32)** vlastnosti a klikněte na tlačítko **OK** tlačítko.  
  
     Je vidět na následujícím obrázku **vytvořit datovou vazbu** dialogové okno s **ItemCount** vybrané vlastnosti.  
  
     ![Datové vazby dialogové okno vytvořit](../designers/media/xaml-create-data-binding.png "xaml_create_data_binding")  
  
8.  Stisknutím klávesy F5 spusťte aplikaci.  
  
     `TextBlock` Ovládací prvek zobrazovat výchozí hodnotu 0 jako text.  
  
## <a name="see-also"></a>Viz také  
 [Vytvoření uživatelského rozhraní pomocí návrháře XAML](../designers/creating-a-ui-by-using-xaml-designer-in-visual-studio.md)   
 [NIB: Převaděč hodnoty dialogové okno Přidat](http://msdn.microsoft.com/en-us/c5f3d110-a541-4b55-8bca-928f77778af8)



