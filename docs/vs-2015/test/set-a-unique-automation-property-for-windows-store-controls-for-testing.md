---
title: Nastavení jedinečné vlastnosti automatizace pro ovládací prvky Windows Store pro testování | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 9bdd74ff-2534-4fc7-a5c3-a77bf7843037
caps.latest.revision: 12
ms.author: gewarren
manager: douge
ms.openlocfilehash: 25890adaf22d1855426813c35e69766bba02a1c8
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49833925"
---
# <a name="set-a-unique-automation-property-for-windows-store-controls-for-testing"></a>Nastavení jedinečné vlastnosti automatizace pro ovládací prvky pro Windows Store za účelem testování
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Pokud chcete spustit programové testy UI pro aplikace Windows Store založených na XAML, musí mít jedinečnou vlastnost automatizace, který identifikuje každý ovládací prvek.  
  
 Můžete přiřadit jedinečné vlastnosti automatizace založená na typu ovládacího prvku XAML v aplikaci. Tady je postup pro přiřazení této jedinečné vlastnosti automatizace v následujících situacích:  
  
-   [Statické definice XAML ovládacích prvků](#UniquePropertyWindowsStoreControlsStaticXAML)  
  
-   [Přiřazení vlastností jedinečný automatizace pomocí sady Visual Studio nebo programu Blend pro Visual Studio](#UniquePropertyWindowsStoreControlsExpressionBlend)  
  
-   [Použít šablonu DataTemplate](#UniquePropertyWindowsStoreControlsDataTemplate)  
  
-   [Použít šablonu ovládacího prvku](#UniquePropertyWindowsStoreControlsControlTemplate)  
  
-   [Dynamické ovládací prvky](#UniquePropertyWindowsStoreControlsDynamicControls)  
  
## <a name="use-methods-to-assign-a-unique-automation-property"></a>Použijte metody přiřazení jedinečné vlastnosti automatizace  
  
###  <a name="UniquePropertyWindowsStoreControlsStaticXAML"></a> Statické definice XAML  
 Chcete-li určit jedinečné vlastnosti automatizace pro ovládací prvek, který je definován v souboru XAML, můžete nastavit AutomationProperties.AutomationId nebo AutomationProperties.Name implicitně nebo explicitně, jak je znázorněno v následujícím příkladu. Některé z těchto hodnot nastavení poskytuje jedinečnou vlastnost automatizace, který slouží k identifikaci ovládacího prvku, když vytvoříte programové záznamu testu nebo akce uživatelského rozhraní ovládacího prvku.  
  
 **Nastavte vlastnost implicitně**  
  
 Nastavte AutomationProperties.AutomationId na **ButtonX** použijete vlastnost Name ve XAML pro ovládací prvek.  
  
```xaml  
<Button Name="ButtonX" Height="31" HorizontalAlignment="Left" Margin="23,26,0,0"  VerticalAlignment="Top" Width="140" Click="ButtonX_Click" />  
  
```  
  
 Nastavte AutomationProperties.Name na **ButtonY** pomocí vlastnost obsahu v XAML pro ovládací prvek.  
  
```xaml  
<Button Content="ButtonY" Height="31" HorizontalAlignment="Left" Margin="23,76,0,0" VerticalAlignment="Top" Width="140" Click="ButtonY_Click" />  
  
```  
  
 **Explicitně nastavit vlastnost**  
  
 Nastavte AutomationProperties.AutomationId na **ButtonX** explicitně v XAML pro ovládací prvek.  
  
```xaml  
<Button AutomationProperties.AutomationId=“ButtonX” Height="31" HorizontalAlignment="Left" Margin="23,26,0,0"  VerticalAlignment="Top" Width="140" Click="ButtonX_Click" />  
  
```  
  
 Nastavte AutomationProperties.Name na **ButtonY** explicitně v XAML pro ovládací prvek.  
  
```  
<Button AutomationProperties.Name="ButtonY" Height="31" HorizontalAlignment="Left" Margin="23,76,0,0" VerticalAlignment="Top" Width="140" Click="ButtonY_Click" />  
```  
  
###  <a name="UniquePropertyWindowsStoreControlsExpressionBlend"></a> Přiřazení vlastností jedinečný automatizace pomocí sady Visual Studio nebo programu Blend pro Visual Studio  
 Visual Studio nebo nástroje Blend for Visual Studio můžete použít pro přiřazení jedinečných názvů interaktivní prvky, jako jsou tlačítka, seznamy, pole se seznamem a textová pole. Díky tomu ovládacího prvku jedinečnou hodnotu pro AutomationProperties.Name.  
  
 **Visual Studio:** na **nástroje** nabídky, přejděte k **možnosti** a klikněte na tlačítko **textový Editor**, pak **XAML**a nakonec **Různé**.  
  
 Vyberte **automaticky pojmenovat interaktivní prvky při vytváření** a klikněte na tlačítko **OK**.  
  
 ![XAML různé možnosti](../test/media/cuit-windowsstoreapp-b.png "CUIT_WindowsStoreApp_B")  
  
 **Blend for Visual Studio:** použijte jednu z následujících metod k tomu blendu for Visual Studio.  
  
> [!NOTE]
>  Tuto metodu můžete použít pouze pro ovládací prvky, které jsou vytvořeny staticky pomocí XAML.  
  
 **Chcete-li zadejte jedinečný název pro existující ovládací prvky**  
  
 Na **nástroje** nabídce zvolte **pojmenovat interaktivní prvky**, jak je znázorněno zde:  
  
 ![V nabídce Nástroje zvolte pojmenovat interaktivní prvky](../test/media/cuit-windowsstoreproperty-blend-1.png "CUIT_WindowsStoreProperty_Blend_1")  
  
 **Automaticky přidělit ovládací prvky, které můžete vytvořit jedinečný název**  
  
 Na **nástroje** nabídky, přejděte k **možnosti**a klikněte na tlačítko **projektu**. Vyberte **automaticky pojmenovat interaktivní prvky při vytváření** a klikněte na tlačítko **OK**, jak je znázorněno zde:  
  
 ![Sada projekt tak, aby pojmenovat interaktivní prvky](../test/media/cuit-windowsstoreproeprty-blend-2.png "CUIT_WindowsStoreProeprty_Blend_2")  
  
###  <a name="UniquePropertyWindowsStoreControlsDataTemplate"></a> Použití šablony dat  
 Můžete definovat jednoduchá šablona ItemTemplate pomocí k vázání hodnot v seznamu do proměnných pomocí následující XAML.  
  
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
  
 Můžete také použít šablonu s ItemContainerStyle k vázání hodnot do proměnných pomocí následující XAML.  
  
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
  
 U obou těchto příkladech musí pak přepsat metodu ToString() vlastnost ItemSource, jak je znázorněno, pomocí následujícího kódu. Tento kód zajišťuje, že hodnota AutomationProperties.Name nastavena a je jedinečný, protože nelze nastavit jedinečnou vlastnost automatizace pro každou položku seznamu vázaného data pomocí vazby. Nastavení jedinečnou hodnotu pro automatizaci Properties.Name stačí v tomto případě.  
  
> [!NOTE]
>  Tento přístup vnitřní obsah položky seznamu, můžete také nastavit na řetězec ve třídě zaměstnance pomocí vazby. Jak je znázorněno v příkladu, ovládací prvek tlačítko každou položku seznamu je přiřazen jedinečný automatizace id, které je ID zaměstnance.  
  
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
  
###  <a name="UniquePropertyWindowsStoreControlsControlTemplate"></a> Použít šablonu ovládacího prvku  
 Šablony ovládacího prvku můžete použít tak, aby každý výskyt určitého typu získá jedinečnou vlastnost automatizace, když je definována v kódu. Musíte vytvořit šablonu tak, aby AutomationProperty váže k jedinečné ID v instanci ovládacího prvku. Následující XAML ukazuje jeden ze způsobů vytvoření touto vazbou pomocí šablony ovládacího prvku.  
  
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
  
 Při definování dvě instance pomocí této šablony ovládacího prvku tlačítko id automatizace je nastavena na jedinečný řetězec obsahu pro ovládací prvky v šabloně, jak je znázorněno v následující XAML.  
  
```xaml  
  
<Button Content=”Button1” Style="{StaticResource MyButton}" Width="140"/>  
<Button Content=”Button2” Style="{StaticResource MyButton}" Width="140"/>  
```  
  
###  <a name="UniquePropertyWindowsStoreControlsDynamicControls"></a> Dynamické ovládací prvky  
 Pokud máte ovládací prvky, které se vytvářejí dynamicky z vašeho kódu a nebyl vytvořen staticky nebo prostřednictvím šablon v souborech XAML, musíte nastavit vlastnosti obsahu nebo název ovládacího prvku. Tím je zajištěno, že každý dynamický ovládací prvek má jedinečnou vlastnost automatizace. Například pokud máte zaškrtávací políčko, musí se zobrazí, když vyberete položku seznamu, můžete nastavit tyto vlastnosti, jak je znázorněno zde:  
  
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




