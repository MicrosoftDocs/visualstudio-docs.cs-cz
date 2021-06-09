---
title: Použití dat pro čas návrhu s Návrhář XAML v aplikaci Visual Studio
description: Naučte se používat data v jazyce XAML v době návrhu.
ms.date: 04/22/2021
ms.topic: overview
author: alihamie
ms.author: tglee
manager: jmartens
monikerRange: '>=vs-2019'
ms.openlocfilehash: 47bf978bc32c651cb90130ecc90517bfe1c29cdd
ms.sourcegitcommit: 01a411cd7ae3488b7b979a947bca92fd296a98e9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/09/2021
ms.locfileid: "111761105"
---
# <a name="use-design-time-data-with-the-xaml-designer-in-visual-studio"></a>Použití dat pro čas návrhu s Návrhář XAML v aplikaci Visual Studio

Některá rozložení je obtížné vizualizovat bez dat. V tomto dokumentu si ukážeme jeden ze způsobů, jak vývojáři pracující na desktopových projektech použít k napodobování dat v Návrháři XAML. Tento přístup se provádí pomocí existujícího oboru názvů "d:", který je ignorován. Pomocí tohoto přístupu můžete rychle přidat data o návrhu na stránky nebo ovládací prvky, aniž byste museli vytvořit úplný ViewModel, nebo stačí testovat, jak může změna vlastnosti ovlivnit vaši aplikaci, aniž byste se museli starat o to, aby tyto změny ovlivnily vaše sestavení vydaných verzí. Vše d: data jsou používána pouze Návrhář XAML a žádné neignorovatelné hodnoty oboru názvů jsou zkompilovány do aplikace.

> [!NOTE]
> Pokud používáte Xamarin. Forms, Prohlédněte si [data o době návrhu Xamarin. Forms.](/xamarin/xamarin-forms/xaml/xaml-previewer/design-time-data)

## <a name="design-time-data-basics"></a>Základy časových údajů návrhu

Data v době návrhu jsou vzorová data, která jste nastavili tak, aby byly vaše ovládací prvky v Návrhář XAML snadněji vizualizace. Chcete-li začít, přidejte následující řádky kódu do záhlaví dokumentu jazyka XAML, pokud ještě nejsou k dispozici:

```xml
xmlns:d="http://schemas.microsoft.com/expression/blend/2008"
xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"
mc:Ignorable="d"
```

Po přidání oborů názvů můžete umístit `d:` před libovolný atribut nebo ovládací prvek, který se zobrazí pouze v Návrhář XAML, ale ne za běhu.

Například můžete přidat text do TextBlock, který má obvykle data s ním spojená.

```xml
<TextBlock Text="{Binding Name}" d:Text="Name!" />
```

[![Data v době návrhu s textem v TextBlock](media\xaml-design-time-textblock.png "Data v době návrhu s popisem")](media\xaml-design-time-textblock.png#lightbox)

V tomto příkladu, bez `d:Text` , Návrhář XAML by pro objekt TextBlock nic nezobrazovalo. Místo toho zobrazuje "název!" kde TextBlock bude mít za běhu skutečná data.

Můžete použít `d:` s atributy pro kterýkoli ovládací prvek prostředí pro UWP nebo WPF .NET Core, jako jsou barvy, velikosti písem a mezery. Můžete ho dokonce přidat do samotného ovládacího prvku.

```xml
<d:Button Content="Design Time Button" />
```

[![Data v době návrhu s ovládacím prvkem tlačítko](media\xaml-design-time-button.png "Data v době návrhu s ovládacím prvkem tlačítko")](media\xaml-design-time-button.png#lightbox)

V tomto příkladu se tlačítko zobrazí pouze v době návrhu. Tuto metodu použijte, chcete-li umístit zástupný symbol do vlastního ovládacího prvku nebo vyzkoušet jiné ovládací prvky. Všechny `d:` atributy a ovládací prvky budou během běhu ignorovány.

## <a name="preview-images-at-design-time"></a>Náhled obrázků v době návrhu

Můžete nastavit zdroj v době návrhu pro obrázky, které jsou vázány na stránku nebo dynamicky načteny. Přidejte do projektu obrázek, který chcete zobrazit v Návrhář XAML. Tento obrázek pak můžete zobrazit v Návrhář XAML v době návrhu:

```xml
<Image Source={Binding ProfilePicture} d:Source="DesignTimePicture.jpg" />
```

> [!NOTE]
> Obrázek v tomto příkladu musí existovat v řešení.

## <a name="design-time-data-for-listviews"></a>Data v době návrhu pro zobrazení ListView

Zobrazení ListView představují oblíbený způsob, jak zobrazit data v desktopové aplikaci. Je ale obtížné je vizualizovat bez jakýchkoli dat. Pomocí této funkce můžete vytvořit vložené datové vlastnost ItemSource nebo položky v době návrhu. Návrhář XAML zobrazuje, co je v tomto poli v zobrazení ListView v době návrhu.

### <a name="wpf-net-core-example"></a>Příklad WPF .NET Core
Chcete-li použít typ String (System: String), ujistěte se, že jste zahrnuli `xmlns:system="clr-namespace:System;assembly=mscorlib` do HLAVIČKY XAML.

```xml
<StackPanel>
    <ListView ItemsSource="{Binding Items}">
        <d:ListView.ItemsSource>
            <x:Array Type="{x:Type system:String}">
                <system:String>Item One</system:String>
                <system:String>Item Two</system:String>
                <system:String>Item Three</system:String>
            </x:Array>
        </d:ListView.ItemsSource>
    <ListView.ItemTemplate>
        <DataTemplate>
            <TextBlock Text="{Binding ItemName}" d:Text="{Binding .}" />
        </DataTemplate>
    </ListView.ItemTemplate>
   </ListView>
</StackPanel>
```

[![Data v době návrhu s ListView](media\xaml-design-time-listview-strings.png "Data v době návrhu s ListView")](media\xaml-design-time-listview-strings.png#lightbox)

Tento předchozí příklad ukazuje prvek ListView se třemi TextBlocksy v Návrhář XAML.

Můžete také vytvořit pole datových objektů. Veřejné vlastnosti `City` datového objektu lze například sestavit jako data v době návrhu.

```csharp
namespace Cities.Models
{
    public class City
    {
        public string Name { get; set; }
        public string Country { get; set; }
    }
}
```

Chcete-li použít třídu v jazyce XAML, je nutné importovat obor názvů do kořenového uzlu.

```xaml
xmlns:models="clr-namespace:Cities.Models"
```

```xml
<StackPanel>
    <ListView ItemsSource="{Binding Items}">
        <d:ListView.ItemsSource>
            <x:Array Type="{x:Type models:City}">
                <models:City Name="Seattle" Country="United States"/>
                <models:City Name="London" Country="United Kingdom"/>
                <models:City Name="Panama City" Country="Panama"/>
            </x:Array>
        </d:ListView.ItemsSource>
        <ListView.ItemTemplate>
            <DataTemplate>
                 <StackPanel Orientation="Horizontal" >
                    <TextBlock Text="{Binding Name}" Margin="0,0,5,0" />
                    <TextBlock Text="{Binding Country}" />
                 </StackPanel>
            </DataTemplate>
        </ListView.ItemTemplate>
    </ListView>
</StackPanel>
```

[![Skutečný model v datech při návrhu s ListView](media\xaml-design-time-listview-models.png "Skutečná data při návrhu modelu pomocí zobrazení ListView")](media\xaml-design-time-listview-models.png#lightbox)

Výhodou je, že můžete navazovat ovládací prvky na statickou verzi vašeho modelu.

### <a name="uwp-example"></a>Příklad UWP

x:Array se nepodporuje v UWP. Proto můžeme použít `<d:ListView.Items>` místo toho. Chcete-li použít typ String (System: String), ujistěte se, že jste zahrnuli `http://schemas.microsoft.com/winfx/2009/xaml` do HLAVIČKY XAML.

```xml
    <StackPanel>
        <ListView>
            <d:ListView.Items>
                <system:String>Item One</system:String>
                <system:String>Item Two</system:String>
                <system:String>Item Three</system:String>
            </d:ListView.Items>
        </ListView>
    </StackPanel>
```

## <a name="use-design-time-data-with-custom-types-and-properties"></a>Použití dat při návrhu s vlastními typy a vlastnostmi

Tato funkce ve výchozím nastavení funguje pouze s ovládacími prvky a vlastnostmi platformy. V této části provedeme kroky potřebné k tomu, abyste mohli používat vlastní ovládací prvky jako ovládací prvky pro dobu návrhu, pro zákazníky, kteří používají Visual Studio 2019 verze [16,8](/visualstudio/releases/2019/release-notes/) nebo novější, dostupné možnosti. Tuto možnost můžete povolit třemi požadavky:

- Vlastní obor názvů xmlns

    ```xml
    xmlns:myControls="http://MyCustomControls"
    ```

- Verze vašeho oboru názvů v době návrhu. To je možné dosáhnout pouhým připojením/design na konci.

     ```xml
    xmlns:myDesignTimeControls="http://MyCustomControls/design"
    ```

- Přidání předpony při návrhu do MC: ignorovat

    ```xml
    xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"
    mc:Ignorable="d myDesignTimeControls"
    ```

Po provedení všech těchto kroků můžete pomocí své `myDesignTimeControls` předpony vytvořit ovládací prvky pro dobu návrhu.

```xml
<myDesignTimeControls:MyButton>I am a design time Button</myDesignTimeControls:MyButton>
```

### <a name="creating-a-custom-xmlns-namespace"></a>Vytvoření vlastního oboru názvů xmlns

Chcete-li vytvořit vlastní obor názvů xmlns v prostředí WPF .NET Core, je nutné namapovat vlastní obor názvů XML na obor názvů CLR, ve kterém jsou ovládací prvky umístěny. To lze provést přidáním `XmlnsDefinition` atributu na úrovni sestavení v `AssemblyInfo.cs` souboru. Soubor se nachází v kořenové hierarchii vašeho projektu.

   ```C#
[assembly: XmlnsDefinition("http://MyCustomControls", "MyViews.MyButtons")]
   ```

## <a name="troubleshooting"></a>Řešení potíží

Pokud se setkáte s problémem, který není uvedený v této části, informujte nás pomocí nástroje [nahlásit problém](../ide/how-to-report-a-problem-with-visual-studio.md) .

### <a name="requirements"></a>Požadavky

- Data při návrhu vyžadují Visual Studio 2019 verze [16,7](/visualstudio/releases/2019/release-notes-v16.7) nebo novější.

- Podporuje desktopové projekty Windows, které cílí na Windows Presentation Foundation (WPF) pro .NET Core a UWP. Tato funkce je také k dispozici pro .NET Framework v [kanálu verze Preview](/visualstudio/releases/2019/release-notes-preview). Pokud ho chcete povolit, v nabídce **nástroje**  >  **Možnosti**  >  **prostředí**  >  **verze Preview** vyberte **Nový Návrhář XAML WPF pro .NET Framework** a restartujte Visual Studio.

- Počínaje sadou Visual Studio 2019 verze 16,7 Tato funkce funguje se všemi integrovanými ovládacími prvky z rozhraní WPF a UWP. Podpora pro ovládací prvky třetích stran je teď dostupná ve [verzi 16,8](/visualstudio/releases/2019/release-notes/).

### <a name="the-xaml-designer-stopped-working"></a>Návrhář XAML přestal fungovat.

Zkuste soubor XAML zavřít a znovu otevřít a vyčistěte a znovu sestavte projekt.

## <a name="see-also"></a>Viz také

- [Data při návrhu pomocí náhledu Xamarin. Forms](/xamarin/xamarin-forms/xaml/xaml-Designer/design-time-data/)
- [XAML v aplikacích WPF](/dotnet/framework/wpf/advanced/xaml-in-wpf)
- [XAML v aplikacích pro UWP](/windows/uwp/xaml-platform/xaml-overview)
- [XAML v aplikacích Xamarin. Forms](/xamarin/xamarin-forms/xaml/)