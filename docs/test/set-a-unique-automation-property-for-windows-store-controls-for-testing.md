---
title: Nastavení jedinečné vlastnosti automatizace pro ovládací prvky UPW za účelem testování
ms.date: 05/31/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.topic: conceptual
ms.author: gewarren
manager: douge
ms.workload:
- uwp
author: gewarren
ms.openlocfilehash: 1cc8986c3101bb2048e0cd4ace739974031344ed
ms.sourcegitcommit: ae46be4a2b2b63da7e7049e9ed67cd80897c8102
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/05/2018
ms.locfileid: "52894778"
---
# <a name="set-a-unique-automation-property-for-uwp-controls-for-testing"></a>Nastavit jedinečnou vlastnost automatizace pro ovládacích prvků UPW pro účely testování

Pokud chcete spustit programové testy UI pro aplikace UWP založené na XAML, musí být každý ovládací prvek identifikován jedinečnou vlastnost automatizace. Můžete přiřadit jedinečné vlastnosti automatizace založená na typu ovládacího prvku XAML v aplikaci.

[!INCLUDE [coded-ui-test-deprecation](includes/coded-ui-test-deprecation.md)]

## <a name="static-xaml-definition"></a>Statické definice XAML

Chcete-li určit jedinečné vlastnosti automatizace pro ovládací prvek, který je definován v souboru XAML, můžete nastavit **AutomationProperties.AutomationId** nebo **AutomationProperties.Name** implicitně nebo explicitně, jak ukazují příklady, které následují. Některé z těchto hodnot nastavení poskytuje jedinečnou vlastnost automatizace, který slouží k identifikaci ovládacího prvku, když vytvoříte programové záznamu testu nebo akce uživatelského rozhraní ovládacího prvku.

### <a name="set-the-property-implicitly"></a>Nastavte vlastnost implicitně

Nastavte **AutomationProperties.AutomationId** k **ButtonX** pomocí **název** vlastnost v XAML pro ovládací prvek.

```xaml
<Button Name="ButtonX" Height="31" HorizontalAlignment="Left" Margin="23,26,0,0"  VerticalAlignment="Top" Width="140" Click="ButtonX_Click" />
```

Nastavte **AutomationProperties.Name** k **ButtonY** pomocí **obsahu** vlastnost v XAML pro ovládací prvek.

```xaml
<Button Content="ButtonY" Height="31" HorizontalAlignment="Left" Margin="23,76,0,0" VerticalAlignment="Top" Width="140" Click="ButtonY_Click" />
```

### <a name="set-the-property-explicitly"></a>Explicitně nastavit vlastnost

Nastavte **AutomationProperties.AutomationId** k **ButtonX** explicitně v XAML pro ovládací prvek.

```xaml
<Button AutomationProperties.AutomationId="ButtonX" Height="31" HorizontalAlignment="Left" Margin="23,26,0,0"  VerticalAlignment="Top" Width="140" Click="ButtonX_Click" />
```

Nastavte **AutomationProperties.Name** k **ButtonY** explicitně v XAML pro ovládací prvek.

```xaml
<Button AutomationProperties.Name="ButtonY" Height="31" HorizontalAlignment="Left" Margin="23,76,0,0" VerticalAlignment="Top" Width="140" Click="ButtonY_Click" />
```

## <a name="assign-unique-names"></a>Přiřazení jedinečných názvů

V programu Blend pro Visual Studio, můžete vybrat možnosti pro přiřazení jedinečných názvů interaktivní prvky jako tlačítka, seznamy, pole se seznamem a textová pole, které poskytuje jedinečné hodnoty pro ovládací prvky **AutomationProperties.Name**.

Chcete-li přiřadit jedinečné názvy pro existující ovládací prvky, vyberte **nástroje** > **pojmenovat interaktivní prvky**.

![Pojmenovat interaktivní prvky v programu Blend for Visual Studio](../test/media/cuit_windowsstoreproperty_blend_1.png)

Automaticky poskytnout jedinečné názvy pro nové ovládací prvky, které přidáte, vyberte **nástroje** > **možnosti** otevřít **možnosti** dialogového okna. Vyberte **návrháře XAML** a pak vyberte **automaticky pojmenovat interaktivní prvky při vytváření**. Vyberte **OK** zavřete dialogové okno.

## <a name="use-a-data-template"></a>Použití šablony dat

Můžete definovat jednoduchý šablony pomocí **ItemTemplate** k vázání hodnot v seznamu proměnných:

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

Můžete také použít šablony s **ItemContainerStyle** k vázání hodnot do proměnných:

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

U obou těchto příkladech, je nutné pak přepsat **ToString()** metoda **vlastnost ItemSource**, jak je znázorněno v následujícím příkladu kódu pomocí. Tento kód, zajišťuje, že **AutomationProperties.Name** hodnota je nastavena a je jedinečný, protože nelze nastavit jedinečnou vlastnost automatizace pro každou položku seznamu vázaných na data pomocí vazby. Jedinečná hodnota pro nastavení **automatizace Properties.Name** v tomto případě je dostačující.

> [!NOTE]
> Tento přístup vnitřní obsah položky seznamu, můžete také nastavit na řetězec ve třídě zaměstnance pomocí vazby. Jak je znázorněno v příkladu, ovládací prvek tlačítko každou položku seznamu je přiřazen jedinečný automatizace id, které je ID zaměstnance.

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

## <a name="use-a-control-template"></a>Použít šablonu ovládacího prvku

Šablony ovládacího prvku můžete použít tak, aby každý výskyt určitého typu získá jedinečnou vlastnost automatizace, když je definována v kódu. Vytvořit šablonu tak, aby **AutomationProperty** váže k jedinečné ID v instanci ovládacího prvku. Následující XAML ukazuje jeden ze způsobů vytvoření touto vazbou pomocí šablony ovládacího prvku:

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

Při definování dvě instance pomocí této šablony ovládacího prvku tlačítko ID služby automation je nastaven na jedinečný řetězec obsahu pro ovládací prvky v šabloně, jak je znázorněno v následující XAML:

```xaml
<Button Content="Button1" Style="{StaticResource MyButton}" Width="140"/>
<Button Content="Button2" Style="{StaticResource MyButton}" Width="140"/>
```

### <a name="dynamic-controls"></a>Dynamické ovládací prvky

Pokud máte ovládací prvky, které se vytvářejí dynamicky z vašeho kódu a nebyl vytvořen staticky nebo prostřednictvím šablon v souborech XAML, je nutné nastavit **obsahu** nebo **název** vlastnosti ovládacího prvku. Tato akce zajistí, že každý dynamický ovládací prvek má jedinečnou vlastnost automatizace. Například pokud máte zaškrtávací políčko, musí se zobrazí, když vyberete položku seznamu, můžete nastavit tyto vlastnosti, jak je znázorněno zde:

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

## <a name="see-also"></a>Viz také:

- [Testování aplikací pro UWP pomocí programových testů uživatelského rozhraní](../test/test-uwp-app-with-coded-ui-test.md)
