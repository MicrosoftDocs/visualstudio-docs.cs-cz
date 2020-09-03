---
title: Nastavení jedinečné vlastnosti automatizace pro ovládací prvky Windows Storu pro testování | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-test
ms.topic: conceptual
ms.assetid: 9bdd74ff-2534-4fc7-a5c3-a77bf7843037
caps.latest.revision: 12
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: d4ccf10f3ce085aa8f0275c40644f1a109616daf
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "72672141"
---
# <a name="set-a-unique-automation-property-for-windows-store-controls-for-testing"></a>Nastavení jedinečné vlastnosti automatizace pro ovládací prvky pro Windows Store za účelem testování
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Chcete-li spustit programové testy uživatelského rozhraní pro aplikaci Windows Store založené na jazyce XAML, je nutné mít jedinečnou vlastnost automatizace, která identifikuje každý ovládací prvek.

 Můžete přiřadit jedinečnou vlastnost Automation založenou na typu ovládacího prvku jazyka XAML v aplikaci. Zde je postup přiřazení jedinečné vlastnosti automatizace v následujících situacích:

- [Statická definice jazyka XAML ovládacích prvků](#UniquePropertyWindowsStoreControlsStaticXAML)

- [Přiřazení jedinečných vlastností automatizace pomocí sady Visual Studio nebo Blend pro Visual Studio](#UniquePropertyWindowsStoreControlsExpressionBlend)

- [Použití DataTemplate](#UniquePropertyWindowsStoreControlsDataTemplate)

- [Použití šablony ovládacího prvku](#UniquePropertyWindowsStoreControlsControlTemplate)

- [Dynamické ovládací prvky](#UniquePropertyWindowsStoreControlsDynamicControls)

## <a name="use-methods-to-assign-a-unique-automation-property"></a>K přiřazení jedinečné vlastnosti automatizace použijte metody

### <a name="static-xaml-definition"></a><a name="UniquePropertyWindowsStoreControlsStaticXAML"></a> Statická definice XAML
 Chcete-li zadat jedinečnou vlastnost automatizace pro ovládací prvek, který je definován v souboru XAML, můžete nastavit vlastnosti automatizace. AutomationId nebo AutomationProperties.Name implicitně nebo explicitně, jak je znázorněno v následujících příkladech. Nastavení jedné z těchto hodnot poskytuje ovládacímu prvku jedinečnou vlastnost automatizace, která se dá použít k identifikaci ovládacího prvku při vytváření programového testu uživatelského rozhraní nebo záznamu akce.

 **Nastavit vlastnost implicitně**

 Nastavte vlastnosti automatizace. AutomationId na **ButtonX** pomocí vlastnosti Name v XAML ovládacího prvku.

```xaml
<Button Name="ButtonX" Height="31" HorizontalAlignment="Left" Margin="23,26,0,0"  VerticalAlignment="Top" Width="140" Click="ButtonX_Click" />

```

 Nastavte AutomationProperties.Name na **tlačítko** pomocí vlastnosti Content v XAML ovládacího prvku.

```xaml
<Button Content="ButtonY" Height="31" HorizontalAlignment="Left" Margin="23,76,0,0" VerticalAlignment="Top" Width="140" Click="ButtonY_Click" />

```

 **Nastavit vlastnost explicitně**

 Nastavte vlastnosti automatizace. AutomationId na **ButtonX** explicitně v jazyce XAML ovládacího prvku.

```xaml
<Button AutomationProperties.AutomationId=“ButtonX” Height="31" HorizontalAlignment="Left" Margin="23,26,0,0"  VerticalAlignment="Top" Width="140" Click="ButtonX_Click" />

```

 Nastavte AutomationProperties.Name na **tlačítko** explicitně v jazyce XAML ovládacího prvku.

```
<Button AutomationProperties.Name="ButtonY" Height="31" HorizontalAlignment="Left" Margin="23,76,0,0" VerticalAlignment="Top" Width="140" Click="ButtonY_Click" />
```

### <a name="assign-unique-automation-properties-using-visual-studio-or-blend-for-visual-studio"></a><a name="UniquePropertyWindowsStoreControlsExpressionBlend"></a> Přiřazení jedinečných vlastností automatizace pomocí sady Visual Studio nebo Blend pro Visual Studio
 Můžete použít aplikaci Visual Studio nebo Blend pro Visual Studio k přiřazení jedinečných názvů k interaktivním prvkům, jako jsou tlačítka, seznamy, pole se seznamem a textová pole. To dává ovládacímu prvku jedinečnou hodnotu pro AutomationProperties.Name.

 **Visual Studio:** V nabídce **nástroje** přejděte na **Možnosti** a pak zvolte **textový editor**, potom **XAML**a nakonec **jiné**.

 Vyberte **automaticky pojmenovat interaktivní prvky při vytváření** a pak zvolte **OK**.

 ![Různé možnosti XAML](../test/media/cuit-windowsstoreapp-b.png "CUIT_WindowsStoreApp_B")

 **Blend pro Visual Studio:** K tomu použijte jednu z následujících metod Blend pro Visual Studio.

> [!NOTE]
> Tuto metodu lze použít pouze pro ovládací prvky, které jsou vytvořeny staticky pomocí jazyka XAML.

 **Udělení jedinečného názvu existujícím ovládacím prvkům**

 V nabídce **nástroje** vyberte **název interaktivní prvky**, jak je znázorněno zde:

 ![V nabídce Nástroje vyberte název interaktivní prvky](../test/media/cuit-windowsstoreproperty-blend-1.png "CUIT_WindowsStoreProperty_Blend_1")

 **Automatické udělení jedinečného názvu ovládacím prvkům, které vytvoříte**

 V nabídce **nástroje** přejděte na **možnost možnosti**a pak zvolte možnost **projekt**. Vyberte možnost **automaticky pojmenovat interaktivní prvky při vytváření** a pak zvolte **OK**, jak je znázorněno zde:

 ![Nastavení projektu pro pojmenování interaktivních prvků](../test/media/cuit-windowsstoreproeprty-blend-2.png "CUIT_WindowsStoreProeprty_Blend_2")

### <a name="use-a-data-template"></a><a name="UniquePropertyWindowsStoreControlsDataTemplate"></a> Použití šablony dat
 Můžete definovat jednoduchou šablonu pomocí šablony ItemTemplate k navázání hodnot v poli se seznamem na proměnné pomocí následujícího XAML.

```xaml

<ListBox Name="listBox1" ItemsSource="{Binding Source={StaticResource employees}}">
   <ListBox.ItemTemplate>
      <DataTemplate>
         <StackPanel Orientation="Horizontal">
            <TextBlock Text="{Binding EmployeeName}" />
            <TextBlock Text="{Binding EmployeeID}" />
         </StackPanel>
      </DataTemplate>
   </ListBox.ItemTemplate>
</ListBox>
```

 Můžete také použít šablonu s ItemContainerStyle pro svázání hodnot s proměnnými pomocí následujícího XAML.

```xaml

      <ListBox Name="listBox1" ItemsSource="{Binding Source={StaticResource employees}}">
            <ListBox.ItemContainerStyle>
                <Style TargetType="ListBoxItem">
                    <Setter Property="Template">
                        <Setter.Value>
                            <ControlTemplate TargetType="ListBoxItem">
                                <Grid>
                                    <Button Content="{Binding EmployeeName}" AutomationProperties.AutomationId="{Binding EmployeeID}"/>
                                </Grid>
                            </ControlTemplate>
                        </Setter.Value>
                    </Setter>
                </Style>
            </ListBox.ItemContainerStyle>        
        </ListBox>

```

 V obou těchto příkladech je nutné přepsat metodu ToString () vlastnost ItemSource, jak je znázorněno v následujícím kódu. Tento kód zajistí, že hodnota AutomationProperties.Name je nastavena a je jedinečná, protože nemůžete nastavit jedinečnou vlastnost Automation pro každou položku seznamu vázaného na data pomocí vazby. V tomto případě je v tomto případě nastavovaná jedinečná hodnota pro Properties.Name Automation.

> [!NOTE]
> Pomocí tohoto přístupu může být vnitřní obsah položky seznamu také nastaven na řetězec ve třídě Employee prostřednictvím vazby. Jak je znázorněno v příkladu, je ovládacímu prvku tlačítko v každé položce seznamu přiřazeno jedinečné ID automatizace, které je ID zaměstnance.

```

Employee[] employees = new Employee[]
{
   new Employee("john", "4384"),
   new Employee("margaret", "7556"),
   new Employee("richard", "8688"),
   new Employee("george", "1293")
};

listBox1.ItemsSource = employees;

public override string ToString()
{
    return EmployeeName + EmployeeID; // Unique Identification to be set as the AutomationProperties.Name
}

```

### <a name="use-a-control-template"></a><a name="UniquePropertyWindowsStoreControlsControlTemplate"></a> Použití šablony ovládacího prvku
 Můžete použít šablonu ovládacího prvku, aby každá instance konkrétního typu získala jedinečnou vlastnost Automation, když je definována v kódu. Je nutné vytvořit šablonu, aby se AutomationProperty váže k jedinečnému ID v instanci ovládacího prvku. Následující kód XAML ukazuje jeden z přístupů k vytvoření této vazby pomocí šablony ovládacího prvku.

```xaml

<Style x:Key="MyButton" TargetType="Button">
<Setter Property="Template">
   <Setter.Value>
<ControlTemplate TargetType="Button">
   <Grid>
      <CheckBox HorizontalAlignment="Left" AutomationProperties.AutomationId="{TemplateBinding Content}"></CheckBox>
      <Button Width="90" HorizontalAlignment="Right" Content="{TemplateBinding Content}" AutomationProperties.AutomationId="{TemplateBinding Content}"></Button>
   </Grid>
</ControlTemplate>
   </Setter.Value>
</Setter>
</Style>

```

 Pokud definujete dvě instance tlačítka pomocí této šablony ovládacích prvků, ID automatizace je nastaveno na jedinečný řetězec obsahu pro ovládací prvky v šabloně, jak je znázorněno v následujícím kódu XAML.

```xaml

<Button Content=”Button1” Style="{StaticResource MyButton}" Width="140"/>
<Button Content=”Button2” Style="{StaticResource MyButton}" Width="140"/>
```

### <a name="dynamic-controls"></a><a name="UniquePropertyWindowsStoreControlsDynamicControls"></a> Dynamické ovládací prvky
 Pokud máte ovládací prvky, které jsou vytvářeny dynamicky z kódu a nejsou vytvořeny staticky nebo prostřednictvím šablon v souborech XAML, je nutné nastavit vlastnosti obsahu nebo názvu ovládacího prvku. Tím se zajistí, že každý dynamický ovládací prvek má jedinečnou vlastnost Automation. Například pokud máte zaškrtávací políčko, které se musí zobrazit při výběru položky seznamu, můžete nastavit tyto vlastnosti, jak je znázorněno zde:

```csharp

private void CreateCheckBox(string txt, StackPanel panel)
   {
      CheckBox cb = new CheckBox();
      cb.Content = txt; // Sets the AutomationProperties.Name
      cb.Height = 50;
      cb.Width = 100;
      cb.Name = "DynamicCheckBoxAid"+ txt; // Sets the AutomationProperties.AutomationId
      panel.Children.Add(cb);
    }

```
