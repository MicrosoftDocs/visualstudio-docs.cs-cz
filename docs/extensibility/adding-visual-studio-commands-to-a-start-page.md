---
title: Přidání příkazů sady Visual Studio na úvodní stránku | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- start page commands
- vs:VSCommands
ms.assetid: a8e2765c-cfb5-47b5-a414-6e48b434e0c2
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
monikerRange: vs-2017
ms.openlocfilehash: 13dd40006039209b06cc6a71760fdbaa240db4fe
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80740110"
---
# <a name="add-visual-studio-commands-to-a-start-page"></a>Přidání příkazů sady Visual Studio na úvodní stránku

Když vytvoříte vlastní úvodní stránku, můžete do ní přidat příkazy sady Visual Studio. Tento dokument popisuje různé způsoby svázání příkazů sady Visual Studio s objekty XAML na úvodní stránce.

Další informace o příkazech v XAML naleznete v [tématu Commanding overview](/dotnet/framework/wpf/advanced/commanding-overview)

## <a name="add-commands-from-the-command-well"></a>Dobře přidávat příkazy z příkazu

Úvodní stránka vytvořená v části Vytvořit <xref:Microsoft.VisualStudio.PlatformUI?displayProperty=fullName> <xref:Microsoft.VisualStudio.Shell?displayProperty=fullName> vlastní [úvodní stránku](../extensibility/creating-a-custom-start-page.md) přidala a jmenné prostory takto.

```xml
xmlns:vs="clr-namespace:Microsoft.VisualStudio.PlatformUI;assembly=Microsoft.VisualStudio.Shell.14.0"
xmlns:vsfx="clr-namespace:Microsoft.VisualStudio.Shell;assembly=Microsoft.VisualStudio.Shell.14.0"
```

Přidejte další obor názvů pro Microsoft.VisualStudio.Shell ze sestavy *Microsoft.VisualStudio.Shell.Immutable.11.0.dll*. (Možná budete muset přidat odkaz na toto sestavení v projektu.)

```xml
xmlns:vscom="clr-namespace:Microsoft.VisualStudio.Shell;assembly=Microsoft.VisualStudio.Shell.Immutable.11.0"
```

`vscom:` Alias můžete použít k vytvoření svázání příkazů sady Visual Studio s <xref:System.Windows.Controls.Primitives.ButtonBase.Command%2A> ovládacími prvky XAML na stránce nastavením vlastnosti ovládacího prvku na `vscom:VSCommands.ExecuteCommand`. Potom můžete nastavit <xref:System.Windows.Controls.Primitives.ButtonBase.CommandParameter%2A> vlastnost na název příkazu, který má být proveden, jak je znázorněno v následujícím příkladu.

```xml
<Button Name="btnNewProj" Content="New Project"
    Command="{x:Static vscom:VSCommands.ExecuteCommand}"
    CommandParameter="File.NewProject" >
</Button>
```

> [!NOTE]
> Alias, `x:` který odkazuje na schéma XAML, je vyžadován na začátku všech příkazů.

 Hodnotu vlastnosti `Command` můžete nastavit na libovolný příkaz, ke kterému lze přistupovat z okna **Příkaz.** Seznam dostupných příkazů naleznete v tématu [Aliasy příkazů sady Visual Studio](../ide/reference/visual-studio-command-aliases.md).

 Pokud příkaz přidat vyžaduje další parametr, můžete jej přidat `CommandParameter` k hodnotě vlastnosti. Oddělte parametry od příkazů pomocí mezer, jak je znázorněno v následujícím příkladu.

```xml
<Button Content="Web Search"
        Command="{x:Static vscom:VSCommands.ExecuteCommand}"
        CommandParameter="View.WebBrowser www.bing.com" />
```

### <a name="call-extensions-from-the-command-well"></a>Rozšíření volání z příkazu dobře
 Příkazy z registrovaných balíčků VSPackages můžete volat pomocí stejné syntaxe, která se používá k volání jiných příkazů sady Visual Studio. Pokud například nainstalovaný balíček VSPackage přidá příkaz **Domovská stránka** do `CommandParameter` nabídky `View.HomePage` **Zobrazení,** můžete tento příkaz volat nastavením na .

> [!NOTE]
> Pokud zavoláte příkaz, který je přidružen k VSPackage, balíček musí být načten při vyvolání příkazu.

## <a name="add-commands-from-assemblies"></a>Přidání příkazů ze sestavení
 Chcete-li volat příkaz z sestavení nebo pro přístup ke kódu v balíčku VSPackage, který není přidružen k příkazu nabídky, musíte vytvořit alias pro sestavení a potom zavolat alias.

### <a name="to-call-a-command-from-an-assembly"></a>Volání příkazu ze sestavy

1. Ve vašem řešení přidejte odkaz na sestavení.

2. V horní části souboru *StartPage.xaml* přidejte direktivu oboru názvů pro sestavení, jak je znázorněno v následujícím příkladu.

    ```xml
    xmlns:vsc="clr-namespace:WebUserControl;assembly=WebUserControl"
    ```

3. Příkaz vyvolá nastavením `Command` vlastnosti objektu XAML, jak je znázorněno v následujícím příkladu.

     Xaml

    ```
    <vs:Button Text="Hide me" Command="{x:Static vsc:HideControl}" .../>
    ```

> [!NOTE]
> Sestavení je nutné zkopírovat a vložit do *.. \\{Instalační složka sady Visual Studio}\Common7\IDE\PrivateAssemblies, abyste se ujistili,\* že je načtena před voláním.

## <a name="add-commands-with-the-dte-object"></a>Přidání příkazů s objektem DTE
 K objektu DTE můžete přistupovat z úvodní stránky, a to jak ve značkách, tak v kódu.

 Ve značkách k němu můžete přistupovat pomocí syntaxe <xref:EnvDTE.DTE> [rozšíření vazby k](/dotnet/framework/wpf/advanced/binding-markup-extension) volání objektu. Tento přístup můžete použít k vytvoření vazby na jednoduché vlastnosti, jako jsou ty, které vracejí kolekce, ale nelze vytvořit vazbu na metody nebo služby. Následující příklad ukazuje <xref:System.Windows.Controls.TextBlock> ovládací prvek, <xref:EnvDTE._DTE.Name%2A> který se <xref:System.Windows.Controls.ListBox> váže na vlastnost a <xref:EnvDTE.Window.Caption%2A> ovládací prvek, který vytvoří <xref:EnvDTE._DTE.Windows%2A> enumerates vlastnosti kolekce, která je vrácena vlastnost.

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

 Příklad najdete [v tématu Návod: Uložení uživatelských nastavení na úvodní stránce](../extensibility/walkthrough-saving-user-settings-on-a-start-page.md).

## <a name="see-also"></a>Viz také

- [Přidání uživatelského ovládacího prvku na úvodní stránku](../extensibility/adding-user-control-to-the-start-page.md)
