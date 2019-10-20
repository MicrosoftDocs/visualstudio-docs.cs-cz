---
title: 'Návod: vytvoření vazby na data v Návrhář XAML | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-designers
ms.topic: conceptual
f1_keywords:
- VS.XamlDesigner.DataBinding
ms.assetid: 1a99aeae-c3ef-407d-ba79-b8055489a43d
caps.latest.revision: 22
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 38434d89544ed290f9adfd077593d7de9bdc1231
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72664019"
---
# <a name="walkthrough-binding-to-data-in-xaml-designer"></a>Návod: vytvoření vazby na data v Návrhář XAML
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

V Návrhář XAML můžete nastavit vlastnosti datové vazby pomocí návrhové plochy a okno Vlastnosti. Příklad v tomto návodu ukazuje, jak vytvořit vazby dat k ovládacímu prvku. Konkrétně tento návod ukazuje, jak vytvořit jednoduchou třídu nákupního košíku, která má [DependencyProperty](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.dependencyproperty.aspx) s názvem `ItemCount`, a potom navážete vlastnost `ItemCount` na vlastnost **text** ovládacího prvku [TextBlock](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.textblock.aspx) .

### <a name="to-create-a-class-to-use-as-a-data-source"></a>Vytvoření třídy, která bude použita jako zdroj dat

1. V nabídce **soubor** klikněte na příkaz **Nový**, **projekt**.

2. V dialogovém **okně Nový projekt** zvolte buď uzel  **C# vizuál** , nebo **Visual Basic** , rozbalte uzel **Windows Desktop** a pak zvolte šablonu **aplikace WPF** .

3. Pojmenujte projekt **BindingTest**a pak klikněte na tlačítko **OK** .

4. Otevřete soubor MainWindow.xaml.cs (nebo MainWindow. vb) a přidejte následující kód. V C#přidejte kód do oboru názvů `BindingTest` (před poslední pravou závorku v souboru). V Visual Basic stačí přidat novou třídu.

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

     Tento kód nastaví hodnotu 0 jako výchozí počet položek pomocí objektu [hodnotu PropertyMetadata](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.propertymetadata.aspx) .

5. V nabídce **soubor** klikněte na příkaz **sestavit**, **Sestavit řešení**.

### <a name="to-bind-the-itemcount-property-to-a-textblock-control"></a>Svázání vlastnosti vlastnost ItemCount s ovládacím prvkem TextBlock

1. V Průzkumník řešení otevřete místní nabídku pro MainWindow. XAML a klikněte na tlačítko **Návrhář zobrazení**.

2. V sadě nástrojů vyberte ovládací prvek [mřížky](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.grid.aspx) a přidejte jej do formuláře.

3. Když je vybrána možnost `Grid`, klikněte v okno Vlastnosti na tlačítko **Nový** vedle vlastnosti **DataContext** .

4. V dialogovém okně **Vybrat objekt** se ujistěte, že je zaškrtnuto políčko **Zobrazit všechna sestavení** , zvolte **ShoppingCart** pod oborem názvů **BindingTest** a pak klikněte na tlačítko **OK** .

     Na následujícím obrázku je znázorněno dialogové okno **Vybrat objekt** s vybraným **ShoppingCart** .

     ![Dialogové okno vybrat objekt](../designers/media/blendselectobject.PNG "BlendSelectObject")

5. V sadě **nástrojů**vyberte ovládací prvek `TextBlock`, který chcete přidat do formuláře.

6. Když je vybrán ovládací prvek `TextBlock`, vyberte v okno Vlastnosti značku vlastnosti napravo od vlastnosti **text** a pak zvolte **vytvořit datovou vazbu**. (Značka vlastnosti vypadá jako malá box.)

7. V dialogovém okně vytvořit datovou vazbu vyberte v poli **cesta** vlastnost **vlastnost ItemCount: (Int32)** a pak klikněte na tlačítko **OK** .

     Na následujícím obrázku je znázorněno dialogové okno **vytvořit datovou vazbu** s vybranou vlastností **vlastnost ItemCount** .

     ![Dialog vytvořit datovou vazbu – dialogové okno](../designers/media/xaml-create-data-binding.png "xaml_create_data_binding")

8. Stisknutím klávesy F5 spusťte aplikaci.

     V ovládacím prvku `TextBlock` by se měla zobrazit výchozí hodnota 0 jako text.

## <a name="see-also"></a>Viz také
 [Vytvoření uživatelského rozhraní pomocí Návrhář XAML](../designers/creating-a-ui-by-using-xaml-designer-in-visual-studio.md) [NIB: přidat hodnotový konvertor – dialogové okno](https://msdn.microsoft.com/c5f3d110-a541-4b55-8bca-928f77778af8)
