---
title: Nastavení jedinečné vlastnosti automatizace pro ovládací prvky UPW za účelem testování
ms.date: 05/31/2018
ms.topic: conceptual
ms.author: mikejo
manager: jillfra
ms.workload:
- uwp
author: mikejo5000
ms.openlocfilehash: 51e16dcaa48a08ae97bc80be1d33163c6f3af875
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "75590446"
---
# <a name="set-a-unique-automation-property-for-uwp-controls-for-testing"></a>Nastavení jedinečné vlastnosti automatizace pro ovládací prvky UPW pro testování

Pokud chcete spustit programové testy uživatelského rozhraní pro aplikaci UPW založenou na XAML, musí být každý ovládací prvek identifikován jedinečnou vlastností automatizace. Můžete přiřadit jedinečnou vlastnost automatizace na základě typu ovládacího prvku XAML ve vaší aplikaci.

[!INCLUDE [coded-ui-test-deprecation](includes/coded-ui-test-deprecation.md)]

## <a name="static-xaml-definition"></a>Statická definice XAML

Chcete-li určit jedinečnou vlastnost automatizace pro ovládací prvek, který je definován v souboru XAML, můžete nastavit **AutomationProperties.AutomationId** nebo **AutomationProperties.Name** implicitně nebo explicitně, jak je znázorněno v následujících příkladech. Nastavení jedné z těchto hodnot poskytuje ovládacímu prvku jedinečnou vlastnost automatizace, kterou lze použít k identifikaci ovládacího prvku při vytváření kódovaného testu uživatelského rozhraní nebo záznamu akce.

### <a name="set-the-property-implicitly"></a>Implicitně nastavit vlastnost

Nastavte **AutomationProperties.AutomationId** na **ButtonX** pomocí **Name** vlastnost v XAML pro ovládací prvek.

```xaml
<Button Name="ButtonX" Height="31" HorizontalAlignment="Left" Margin="23,26,0,0"  VerticalAlignment="Top" Width="140" Click="ButtonX_Click" />
```

Nastavte **AutomationProperties.Name** **ButtonY** pomocí **Content** vlastnost v XAML pro ovládací prvek.

```xaml
<Button Content="ButtonY" Height="31" HorizontalAlignment="Left" Margin="23,76,0,0" VerticalAlignment="Top" Width="140" Click="ButtonY_Click" />
```

### <a name="set-the-property-explicitly"></a>Explicitně nastavit vlastnost

Nastavte **AutomationProperties.AutomationId** na **ButtonX** explicitně v XAML pro ovládací prvek.

```xaml
<Button AutomationProperties.AutomationId="ButtonX" Height="31" HorizontalAlignment="Left" Margin="23,26,0,0"  VerticalAlignment="Top" Width="140" Click="ButtonX_Click" />
```

Nastavte **AutomationProperties.Name** **ButtonY** explicitně v XAML pro ovládací prvek.

```xaml
<Button AutomationProperties.Name="ButtonY" Height="31" HorizontalAlignment="Left" Margin="23,76,0,0" VerticalAlignment="Top" Width="140" Click="ButtonY_Click" />
```

## <a name="assign-unique-names"></a>Přiřazení jedinečných názvů

V části Prolnutí pro visual studio můžete vybrat možnost přiřazení jedinečných názvů interaktivním prvkům, jako jsou tlačítka, seznamy, pole se seznamem a textová pole, která poskytuje ovládacím prvkům jedinečné hodnoty pro **AutomationProperties.Name**.

Chcete-li existujícím ovládacím prvkům přiřadit jedinečné názvy, vyberte **možnost Nástroje** > **pojmenovat interaktivní prvky**.

![Pojmenování interaktivních prvků v prolnutí pro visual studio](../test/media/cuit_windowsstoreproperty_blend_1.png)

Chcete-li automaticky přidat jedinečné názvy novým ovládacím prvkům, které přidáte, vyberte**Možnosti** **nástrojů** > a otevřete dialogové okno **Možnosti.** Vyberte **Návrhář XAML** a při vytváření vyberte **Automaticky pojmenovat interaktivní prvky**. Chcete-li dialogové okno zavřít, vyberte **OK.**

## <a name="use-a-data-template"></a>Použití šablony dat

Můžete definovat jednoduchou šablonu pomocí **itemtemplate** pro vazbu hodnot v seznamu s proměnnými:

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

Můžete také použít šablonu s **ItemContainerStyle** svázat hodnoty s proměnnými:

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

Pro oba tyto příklady je pak nutné přepsat **ToString()** metoda **ItemSource**, jak je znázorněno pomocí příkladu kódu, který následuje. Tento kód zajišťuje, že **hodnota AutomationProperties.Name** je nastavena a je jedinečná, protože nelze nastavit jedinečnou vlastnost automatizace pro každou položku seznamu vázanou na data pomocí vazby. Nastavení jedinečné hodnoty pro **Properties.Name automatizace** je v tomto případě dostačující.

> [!NOTE]
> Pomocí tohoto přístupu vnitřní obsah položky seznamu lze také nastavit na řetězec ve třídě Employee prostřednictvím vazby. Jak je znázorněno v příkladu, ovládací prvek tlačítka uvnitř každé položky seznamu je přiřazen o jedinečný id automatizace, což je ID zaměstnance.

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

Můžete použít šablonu ovládacího prvku tak, aby každá instance určitého typu získá jedinečnou vlastnost automatizace, když je definována v kódu. Vytvořte šablonu tak, aby **AutomationProperty** váže na jedinečné ID v instanci ovládacího prvku. Následující XAML ukazuje jeden přístup k vytvoření této vazby s šablonou ovládacího prvku:

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

Když definujete dvě instance tlačítka pomocí této šablony ovládacího prvku, ID automatizace je nastavena na jedinečný řetězec obsahu pro ovládací prvky v šabloně, jak je znázorněno v následujícím XAML:

```xaml
<Button Content="Button1" Style="{StaticResource MyButton}" Width="140"/>
<Button Content="Button2" Style="{StaticResource MyButton}" Width="140"/>
```

### <a name="dynamic-controls"></a>Dynamické ovládací prvky

Pokud máte ovládací prvky, které jsou vytvořeny dynamicky z vašeho kódu a nejsou vytvořeny staticky nebo prostřednictvím šablon v souborech XAML, musíte nastavit **content** nebo **name** vlastnosti ovládacího prvku. Tato akce zajišťuje, že každý dynamický ovládací prvek má jedinečnou vlastnost automatizace. Pokud máte například zaškrtávací políčko, které musí být zobrazeno při výběru položky seznamu, můžete nastavit tyto vlastnosti, jak je znázorněno zde:

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

- [Testování aplikací UPW pomocí kódovaných testů ui](../test/test-uwp-app-with-coded-ui-test.md)
