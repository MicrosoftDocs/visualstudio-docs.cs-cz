---
title: Přidání příkazů sady Visual Studio na úvodní stránku | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- start page commands
- vs:VSCommands
ms.assetid: a8e2765c-cfb5-47b5-a414-6e48b434e0c2
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 22ae9ebb5e9acb3fa1787f2af3b0fbb159c1485d
ms.sourcegitcommit: 0e5289414d90a314ca0d560c0c3fe9c88cb2217c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/19/2018
ms.locfileid: "39153628"
---
# <a name="add-visual-studio-commands-to-a-start-page"></a>Přidání příkazů sady Visual Studio pro úvodní stránku
Když vytvoříte vlastní úvodní stránky, můžete přidat příkazy sady Visual Studio k němu. Tento dokument popisuje různé způsoby, jak svázat objekty XAML na úvodní stránce příkazy sady Visual Studio.  
  
 Další informace o příkazech v XAML najdete v tématu [Commanding přehled](/dotnet/framework/wpf/advanced/commanding-overview)  
  
## <a name="add-commands-from-the-command-well"></a>Přidání příkazů z příkazu dobře  
 Úvodní stránka vytvořené v [vytvořit vlastní úvodní stránky](../extensibility/creating-a-custom-start-page.md) přidán <xref:Microsoft.VisualStudio.PlatformUI?displayProperty=fullName> a <xref:Microsoft.VisualStudio.Shell?displayProperty=fullName> obory názvů, následujícím způsobem.  
  
```  
xmlns:vs="clr-namespace:Microsoft.VisualStudio.PlatformUI;assembly=Microsoft.VisualStudio.Shell.14.0"  
xmlns:vsfx="clr-namespace:Microsoft.VisualStudio.Shell;assembly=Microsoft.VisualStudio.Shell.14.0"  
```  
  
 Přidat jiný obor názvů pro Microsoft.VisualStudio.Shell ze sestavení *Microsoft.VisualStudio.Shell.Immutable.11.0.dll*. (Budete muset přidat odkaz na toto sestavení v projektu.)  
  
```xml  
xmlns:vscom="clr-namespace:Microsoft.VisualStudio.Shell;assembly=Microsoft.VisualStudio.Shell.Immutable.11.0"  
```  
  
 Můžete použít `vscom:` alias vytvoření vazby mezi příkazy sady Visual Studio XAML ovládací prvky na stránce nastavení <xref:System.Windows.Controls.Primitives.ButtonBase.Command%2A> vlastnost ovládacího prvku na `vscom:VSCommands.ExecuteCommand`. Pak můžete nastavit <xref:System.Windows.Controls.Primitives.ButtonBase.CommandParameter%2A> nastavte název příkazu ke spuštění, jak je znázorněno v následujícím příkladu.  
  
```xml  
<Button Name="btnNewProj" Content="New Project"   
    Command="{x:Static vscom:VSCommands.ExecuteCommand}"  
    CommandParameter="File.NewProject" >  
</Button>  
```  
  
> [!NOTE]
>  `x:` Alias, který odkazuje na schématu XAML, se vyžaduje na začátku všechny příkazy.  
  
 Můžete nastavit hodnotu `Command` vlastnost jakýkoli příkaz, který je přístupný z **příkaz** okna. Seznam dostupných příkazů najdete v tématu [aliasy příkazů sady Visual Studio](../ide/reference/visual-studio-command-aliases.md).  
  
 Pokud příkaz pro přidání vyžaduje další parametr, můžete ho přidat do hodnoty vlastnosti `CommandParameter` vlastnost. Oddělené parametry z příkazů pomocí mezer, jak je znázorněno v následujícím příkladu.  
  
```xml  
<Button Content="Web Search"   
        Command="{x:Static vscom:VSCommands.ExecuteCommand}"  
        CommandParameter="View.WebBrowser www.bing.com" />  
```  
  
### <a name="call-extensions-from-the-command-well"></a>Dobře volání rozšíření z příkazu  
 Příkazy můžete volat z registrovaných rozšíření VSPackages pomocí stejné syntaxe, která slouží k volání jiné příkazy sady Visual Studio. Například, pokud nainstalovaný balíček VSPackage správy kódu přidá **domovskou stránku** příkaz **zobrazení** nabídku, můžete volat příkaz tak, že nastavíte `CommandParameter` k `View.HomePage`.  
  
> [!NOTE]
>  Pokud zavoláte příkaz, který je přidružený k VSPackage, musí být balíček načíst při vyvolání příkazu.  
  
## <a name="add-commands-from-assemblies"></a>Přidání příkazů ze sestavení  
 Volání příkazu ze sestavení nebo na přístupový kód v sadě VSPackage, která nejsou spojena s příkaz nabídky, musíte vytvořit alias pro sestavení a poté zavolejte alias.  
  
### <a name="to-call-a-command-from-an-assembly"></a>Volání příkazu ze sestavení  
  
1.  Ve vašem řešení přidejte odkaz na sestavení.  
  
2.  V horní části *StartPage.xaml* souboru přidejte direktivu oboru názvů pro sestavení, jak je znázorněno v následujícím příkladu.  
  
    ```xml  
    xmlns:vsc="clr-namespace:WebUserControl;assembly=WebUserControl"  
    ```  
  
3.  Vyvolat příkaz tak, že nastavíte `Command` vlastnosti objektu XAML, jak je znázorněno v následujícím příkladu.  
  
     XAML  
  
    ```  
    <vs:Button Text="Hide me" Command="{x:Static vsc:HideControl}" .../>  
    ```  
  
> [!NOTE]
>  Musíte zkopírovat sestavení a vložte jej do *.. \\{Instalační složky sady visual Studio} \Common7\IDE\PrivateAssemblies\* k Ujistěte se, že je načteno předtím, než je volána.  
  
## <a name="add-commands-with-the-dte-object"></a>Přidání příkazů s objekt DTE  
 Objekt DTE můžete přistupovat z úvodní stránku značek a kódu.  
  
 V kódu, můžete k němu přístup s použitím [vazby – rozšíření značek](/dotnet/framework/wpf/advanced/binding-markup-extension) syntaxi pro volání <xref:EnvDTE.DTE> objektu. Tento přístup můžete použít k vytvoření vazby na jednoduché vlastnosti, jako jsou ty, které vracejí kolekce, ale nelze vytvořit vazbu s metod nebo služeb. Následující příklad ukazuje <xref:System.Windows.Controls.TextBlock> ovládací prvek, který se váže k <xref:EnvDTE._DTE.Name%2A> vlastnost a <xref:System.Windows.Controls.ListBox> ovládací prvek, který vytvoří výčet <xref:EnvDTE.Window.Caption%2A> vlastnosti kolekce, který je vrácen <xref:EnvDTE._DTE.Windows%2A> vlastnost.  
  
```xml  
<TextBlock Text="{Binding Path=DTE.Name}" FontSize="12" HorizontalAlignment="Center"/>  
<ListBox ItemsSource="{Binding Path=DTE.Windows}">  
    <ListBox.ItemTemplate>  
        <DataTemplate>  
            <TextBlock Text="{Binding Path=Caption}"/>  
        </DataTemplate>  
    </ListBox.ItemTemplate>  
</ListBox  
```  
  
 Příklad najdete v tématu [návod: ukládání uživatelských nastavení na úvodní stránce](../extensibility/walkthrough-saving-user-settings-on-a-start-page.md).  
  
## <a name="see-also"></a>Viz také:  
 [Přidání uživatelského ovládacího prvku na úvodní stránku](../extensibility/adding-user-control-to-the-start-page.md)