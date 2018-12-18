---
title: Přidání příkazů sady Visual Studio na úvodní stránku | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- start page commands
- vs:VSCommands
ms.assetid: a8e2765c-cfb5-47b5-a414-6e48b434e0c2
caps.latest.revision: 21
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 6a5a0e205d04fb219d000dd87e97735cdfd26162
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51748763"
---
# <a name="adding-visual-studio-commands-to-a-start-page"></a>Přidání příkazů sady Visual Studio na úvodní stránku
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Když vytvoříte vlastní úvodní stránku, můžete přidat příkazy sady Visual Studio k němu. Tento dokument popisuje různé způsoby, jak svázat objekty XAML na úvodní stránce příkazy sady Visual Studio.  
  
 Další informace o příkazech v XAML najdete v tématu [přehled příkazů](http://msdn.microsoft.com/library/bc208dfe-367d-426a-99de-52b7e7511e81)  
  
## <a name="adding-commands-from-the-command-well"></a>Přidání příkazů z příkazu dobře  
 Na úvodní stránce vytvořené v [vytvoření vlastní úvodní stránku](../extensibility/creating-a-custom-start-page.md) přidán <xref:Microsoft.VisualStudio.PlatformUI?displayProperty=fullName> a <xref:Microsoft.VisualStudio.Shell?displayProperty=fullName> obory názvů, následujícím způsobem.  
  
```  
xmlns:vs="clr-namespace:Microsoft.VisualStudio.PlatformUI;assembly=Microsoft.VisualStudio.Shell.14.0"  
xmlns:vsfx="clr-namespace:Microsoft.VisualStudio.Shell;assembly=Microsoft.VisualStudio.Shell.14.0"  
```  
  
 Přidáte jiný obor názvů pro Microsoft.VisualStudio.Shell ze sestavení Microsoft.VisualStudio.Shell.Immutable.11.0.dll. (Budete muset přidat odkaz na toto sestavení v projektu.)  
  
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
  
 Můžete nastavit hodnotu `Command` vlastnost jakýkoli příkaz, který je přístupný z **příkaz** okna. Seznam dostupných příkazů najdete v tématu [aliasy příkazů aplikace Visual Studio](../ide/reference/visual-studio-command-aliases.md).  
  
 Pokud příkaz pro přidání vyžaduje další parametr, můžete ho přidat do hodnoty vlastnosti `CommandParameter` vlastnost. Oddělené parametry z příkazů pomocí mezer, jak je znázorněno v následujícím příkladu.  
  
```xml  
<Button Content="Web Search"   
        Command="{x:Static vscom:VSCommands.ExecuteCommand}"  
        CommandParameter="View.WebBrowser www.bing.com" />  
```  
  
### <a name="calling-extensions-from-the-command-well"></a>Dobře volání rozšíření z příkazu  
 Příkazy můžete volat z registrovaných rozšíření VSPackages pomocí stejné syntaxe, která slouží k volání jiné příkazy sady Visual Studio. Například, pokud nainstalovaný balíček VSPackage správy kódu přidá **domovskou stránku** příkaz **zobrazení** nabídku, můžete volat příkaz tak, že nastavíte `CommandParameter` k `View.HomePage`.  
  
> [!NOTE]
>  Pokud zavoláte příkaz, který je přidružený k VSPackage, musí být balíček načíst při vyvolání příkazu.  
  
## <a name="adding-commands-from-assemblies"></a>Přidání příkazů ze sestavení  
 Volání příkazu ze sestavení nebo na přístupový kód v sadě VSPackage, která nejsou spojena s příkaz nabídky, musíte vytvořit alias pro sestavení a poté zavolejte alias.  
  
#### <a name="to-call-a-command-from-an-assembly"></a>Volání příkazu ze sestavení  
  
1.  Ve vašem řešení přidejte odkaz na sestavení.  
  
2.  V horní části souboru StartPage.xaml přidejte direktivu oboru názvů pro sestavení, jak je znázorněno v následujícím příkladu.  
  
    ```xml  
    xmlns:vsc="clr-namespace:WebUserControl;assembly=WebUserControl"  
    ```  
  
3.  Vyvolat příkaz tak, že nastavíte `Command` vlastnosti objektu XAML, jak je znázorněno v následujícím příkladu.  
  
     XAML  
  
    ```  
    <vs:Button Text="Hide me" Command="{x:Static vsc:HideControl}" .../>  
    ```  
  
> [!NOTE]
>  Musíte zkopírovat sestavení a vložte jej do... \\ *Instalační složky sady visual Studio*\Common7\IDE\PrivateAssemblies\ Ujistěte se, že je načteno předtím, než je volána.  
  
## <a name="adding-commands-with-the-dte-object"></a>Přidání komentářů k objektu DTE  
 Objekt DTE můžete přistupovat z úvodní stránku značek a kódu.  
  
 V kódu, můžete k němu přístup s použitím [vazby – rozšíření značek](http://msdn.microsoft.com/library/83d6e2a4-1b0c-4fc8-bd96-b5e98800ab63) syntaxi pro volání <xref:EnvDTE.DTE> objektu. Tento přístup můžete použít k vytvoření vazby na jednoduché vlastnosti, jako jsou ty, které vracejí kolekce, ale nelze vytvořit vazbu s metod nebo služeb. Následující příklad ukazuje <xref:System.Windows.Controls.TextBlock> ovládací prvek, který se váže k <xref:EnvDTE._DTE.Name%2A> vlastnost a <xref:System.Windows.Controls.ListBox> ovládací prvek, který vytvoří výčet <xref:EnvDTE.Window.Caption%2A> vlastnosti kolekce, který je vrácen <xref:EnvDTE._DTE.Windows%2A> vlastnost.  
  
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
  
 Příklad najdete v tématu [návod: ukládání uživatelská nastavení na úvodní stránce](../extensibility/walkthrough-saving-user-settings-on-a-start-page.md).  
  
## <a name="see-also"></a>Viz také  
 [Přidání uživatelského ovládacího prvku na úvodní stránku](../extensibility/adding-user-control-to-the-start-page.md)

