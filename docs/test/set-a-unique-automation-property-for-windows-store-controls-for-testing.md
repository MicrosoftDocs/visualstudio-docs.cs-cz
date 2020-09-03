---
title: Nastavení jedinečné vlastnosti automatizace pro ovládací prvky UPW za účelem testování
ms.date: 05/31/2018
ms.topic: how-to
ms.author: mikejo
manager: jillfra
ms.workload:
- uwp
author: mikejo5000
ms.openlocfilehash: 62409dc4aac8f640c7b58b112f7f86215ba2043b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "85286710"
---
# <a name="set-a-unique-automation-property-for-uwp-controls-for-testing"></a>Nastavení jedinečné vlastnosti automatizace pro ovládací prvky UWP pro testování

Chcete-li spustit programové testy uživatelského rozhraní pro aplikaci UWP založené na jazyce XAML, musí být každý ovládací prvek identifikován jedinečnou vlastností automatizace. Můžete přiřadit jedinečnou vlastnost Automation založenou na typu ovládacího prvku jazyka XAML v aplikaci.

[!INCLUDE [coded-ui-test-deprecation](includes/coded-ui-test-deprecation.md)]

## <a name="static-xaml-definition"></a>Statická definice XAML

Chcete-li zadat jedinečnou vlastnost automatizace pro ovládací prvek, který je definován v souboru XAML, můžete nastavit **Vlastnosti automatizace. AutomationId** nebo **AutomationProperties.Name** implicitně nebo explicitně, jak je znázorněno v následujících příkladech. Nastavení jedné z těchto hodnot poskytuje ovládacímu prvku jedinečnou vlastnost automatizace, která se dá použít k identifikaci ovládacího prvku při vytváření programového testu uživatelského rozhraní nebo záznamu akce.

### <a name="set-the-property-implicitly"></a>Nastavit vlastnost implicitně

Nastavte **Vlastnosti automatizace. AutomationId** na **ButtonX** pomocí vlastnosti **Name** v XAML ovládacího prvku.

```xaml
<Button Name="ButtonX" Height="31" HorizontalAlignment="Left" Margin="23,26,0,0"  VerticalAlignment="Top" Width="140" Click="ButtonX_Click" />
```

Nastavte **AutomationProperties.Name** na **tlačítko** pomocí vlastnosti **Content** v XAML ovládacího prvku.

```xaml
<Button Content="ButtonY" Height="31" HorizontalAlignment="Left" Margin="23,76,0,0" VerticalAlignment="Top" Width="140" Click="ButtonY_Click" />
```

### <a name="set-the-property-explicitly"></a>Nastavit vlastnost explicitně

Nastavte **Vlastnosti automatizace. AutomationId** na **ButtonX** explicitně v jazyce XAML pro ovládací prvek.

```xaml
<Button AutomationProperties.AutomationId="ButtonX" Height="31" HorizontalAlignment="Left" Margin="23,26,0,0"  VerticalAlignment="Top" Width="140" Click="ButtonX_Click" />
```

Nastavte **AutomationProperties.Name** na **tlačítko** explicitně v jazyce XAML ovládacího prvku.

```xaml
<Button AutomationProperties.Name="ButtonY" Height="31" HorizontalAlignment="Left" Margin="23,76,0,0" VerticalAlignment="Top" Width="140" Click="ButtonY_Click" />
```

## <a name="assign-unique-names"></a>Přiřadit jedinečné názvy

V Blend pro Visual Studio můžete vybrat možnost pro přiřazení jedinečných názvů k interaktivním prvkům, jako jsou tlačítka, seznamy, pole se seznamem a textová pole, která poskytují ovládací prvky jedinečné hodnoty pro **AutomationProperties.Name**.

Chcete-li přiřadit jedinečné názvy existujícím ovládacím prvkům, vyberte **nástroje**  >  **název interaktivní prvky**.

![Pojmenování interaktivních prvků v Blend pro Visual Studio](../test/media/cuit_windowsstoreproperty_blend_1.png)

Chcete-li automaticky zadat jedinečné názvy pro nové ovládací prvky, které **Tools**přidáte, vyberte možnost  >  **Možnosti** nástrojů a otevřete dialogové okno **Možnosti** . Vyberte **Návrhář XAML** a pak **při vytváření automaticky pojmenovat interaktivní prvky**. Kliknutím na **tlačítko OK** zavřete dialogové okno.

## <a name="use-a-data-template"></a>Použití šablony dat

Můžete definovat jednoduchou šablonu pomocí šablony **ItemTemplate** k navázání hodnot v poli se seznamem na proměnné:

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

K navázání hodnot na proměnné můžete použít také šablonu s **ItemContainerStyle** :

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

V obou těchto příkladech je nutné přepsat metodu **ToString ()** **vlastnost ItemSource**, jak je znázorněno v následujícím příkladu kódu. Tento kód zajistí, že hodnota **AutomationProperties.Name** je nastavena a je jedinečná, protože nemůžete nastavit jedinečnou vlastnost Automation pro každou položku seznamu vázaného na data pomocí vazby. V tomto případě je v tomto případě nastavovaná jedinečná hodnota pro **Properties.Name Automation** .

> [!NOTE]
> Pomocí tohoto přístupu může být vnitřní obsah položky seznamu také nastaven na řetězec ve třídě Employee prostřednictvím vazby. Jak je znázorněno v příkladu, je ovládacímu prvku tlačítko v každé položce seznamu přiřazeno jedinečné ID automatizace, což je ID zaměstnance.

```csharp
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

## <a name="use-a-control-template"></a>Použití šablony ovládacího prvku

Můžete použít šablonu ovládacího prvku, aby každá instance konkrétního typu získala jedinečnou vlastnost Automation, když je definována v kódu. Vytvořte šablonu, aby se **AutomationProperty** váže k jedinečnému ID v instanci ovládacího prvku. Následující kód XAML ukazuje jeden z přístupů k vytvoření této vazby pomocí šablony ovládacího prvku:

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

Pokud definujete dvě instance tlačítka pomocí této šablony ovládacích prvků, ID automatizace je nastaveno na jedinečný řetězec obsahu pro ovládací prvky v šabloně, jak je znázorněno v následujícím kódu XAML:

```xaml
<Button Content="Button1" Style="{StaticResource MyButton}" Width="140"/>
<Button Content="Button2" Style="{StaticResource MyButton}" Width="140"/>
```

### <a name="dynamic-controls"></a>Dynamické ovládací prvky

Pokud máte ovládací prvky, které jsou vytvářeny dynamicky z kódu a nejsou vytvořeny staticky nebo prostřednictvím šablon v souborech XAML, je nutné nastavit vlastnosti **obsahu** nebo **názvu** ovládacího prvku. Tato akce zajistí, že má každý dynamický ovládací prvek jedinečnou vlastnost Automation. Například pokud máte zaškrtávací políčko, které se musí zobrazit při výběru položky seznamu, můžete nastavit tyto vlastnosti, jak je znázorněno zde:

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

## <a name="see-also"></a>Viz také

- [Testování aplikací pro UWP pomocí programových testů uživatelského rozhraní](../test/test-uwp-app-with-coded-ui-test.md)
