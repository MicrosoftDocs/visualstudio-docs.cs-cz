---
title: Přidávání příkazů sady Visual Studio na úvodní stránku | Microsoft Docs
description: Přečtěte si o různých způsobech, jak navazovat příkazy sady Visual Studio na objekty XAML na vlastní úvodní stránce v aplikaci Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- start page commands
- vs:VSCommands
ms.assetid: a8e2765c-cfb5-47b5-a414-6e48b434e0c2
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
monikerRange: vs-2017
ms.openlocfilehash: 0bf0f9a3db21dd93b1a497731bca9142a4377acc
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/25/2021
ms.locfileid: "112901510"
---
# <a name="add-visual-studio-commands-to-a-start-page"></a>Přidání příkazů sady Visual Studio na úvodní stránku

Když vytvoříte vlastní úvodní stránku, můžete k ní přidat příkazy sady Visual Studio. Tento dokument popisuje různé způsoby, jak navazovat příkazy sady Visual Studio na objekty XAML na úvodní stránce.

Další informace o příkazech v XAML najdete v tématu [Přehled příkazů](/dotnet/framework/wpf/advanced/commanding-overview) .

## <a name="add-commands-from-the-command-well"></a>Přidat příkazy z příkazu Well

Úvodní stránka vytvořená v části [Vytvoření vlastní úvodní stránky](../extensibility/creating-a-custom-start-page.md) přidala <xref:Microsoft.VisualStudio.PlatformUI?displayProperty=fullName> <xref:Microsoft.VisualStudio.Shell?displayProperty=fullName> obory názvů a, jak je znázorněno níže.

```xml
xmlns:vs="clr-namespace:Microsoft.VisualStudio.PlatformUI;assembly=Microsoft.VisualStudio.Shell.14.0"
xmlns:vsfx="clr-namespace:Microsoft.VisualStudio.Shell;assembly=Microsoft.VisualStudio.Shell.14.0"
```

Přidejte další obor názvů pro Microsoft. VisualStudio. Shell ze *Microsoft.VisualStudio.Shell.Immutable.11.0.dll* sestavení. (V projektu možná budete muset přidat odkaz na toto sestavení.)

```xml
xmlns:vscom="clr-namespace:Microsoft.VisualStudio.Shell;assembly=Microsoft.VisualStudio.Shell.Immutable.11.0"
```

Můžete použít `vscom:` alias pro svázání příkazů sady Visual Studio s ovládacími prvky XAML na stránce nastavením <xref:System.Windows.Controls.Primitives.ButtonBase.Command%2A> vlastnosti ovládacího prvku na `vscom:VSCommands.ExecuteCommand` . Pak můžete nastavit <xref:System.Windows.Controls.Primitives.ButtonBase.CommandParameter%2A> vlastnost na název příkazu, který má být spuštěn, jak je znázorněno v následujícím příkladu.

```xml
<Button Name="btnNewProj" Content="New Project"
    Command="{x:Static vscom:VSCommands.ExecuteCommand}"
    CommandParameter="File.NewProject" >
</Button>
```

> [!NOTE]
> `x:`Alias, který odkazuje na schéma jazyka XAML, je vyžadován na začátku všech příkazů.

 Můžete nastavit hodnotu `Command` vlastnosti na libovolný příkaz, který je možné použít z **příkazového** okna. Seznam dostupných příkazů naleznete v tématu [Aliasy příkazů sady Visual Studio](../ide/reference/visual-studio-command-aliases.md).

 Pokud příkaz pro přidání vyžaduje další parametr, můžete jej přidat do hodnoty `CommandParameter` Vlastnosti. Oddělte parametry z příkazů pomocí mezer, jak je znázorněno v následujícím příkladu.

```xml
<Button Content="Web Search"
        Command="{x:Static vscom:VSCommands.ExecuteCommand}"
        CommandParameter="View.WebBrowser www.bing.com" />
```

### <a name="call-extensions-from-the-command-well"></a>Správné volání rozšíření z příkazu
 Můžete volat příkazy z registrovaných VSPackage pomocí stejné syntaxe, která se používá k volání jiných příkazů sady Visual Studio. Pokud například nainstalovaný VSPackage přidá do nabídky **zobrazení** **domovskou stránku** , můžete tento příkaz zavolat nastavením `CommandParameter` na `View.HomePage` .

> [!NOTE]
> Pokud zavoláte příkaz, který je spojen s rozhraním VSPackage, balíček musí být načten při vyvolání příkazu.

## <a name="add-commands-from-assemblies"></a>Přidat příkazy ze sestavení
 Chcete-li volat příkaz ze sestavení nebo získat přístup k kódu ve VSPackage, který není přidružen k příkazu nabídky, je nutné vytvořit alias pro sestavení a poté zavolat alias.

### <a name="to-call-a-command-from-an-assembly"></a>Volání příkazu ze sestavení

1. Ve vašem řešení přidejte odkaz na sestavení.

2. V horní části souboru *StartPage. XAML* přidejte direktivu Namespace pro sestavení, jak je znázorněno v následujícím příkladu.

    ```xml
    xmlns:vsc="clr-namespace:WebUserControl;assembly=WebUserControl"
    ```

3. Vyvolání příkazu nastavením `Command` vlastnosti objektu XAML, jak je znázorněno v následujícím příkladu.

     Formátu

    ```
    <vs:Button Text="Hide me" Command="{x:Static vsc:HideControl}" .../>
    ```

> [!NOTE]
> Je nutné zkopírovat sestavení a vložit jej do *.. \\ {Instalační složka sady Visual Studio} \Common7\IDE\PrivateAssemblies \* , abyste se ujistili, že je načtená před tím, než se zavolá.

## <a name="add-commands-with-the-dte-object"></a>Přidání příkazů s objektem DTE
 Na objekt DTE můžete přistupovat z úvodní stránky, v kódu i v kódu.

 V kódu můžete k němu přistupovat pomocí syntaxe [rozšíření značek vazby](/dotnet/framework/wpf/advanced/binding-markup-extension) pro volání <xref:EnvDTE.DTE> objektu. Tento přístup můžete použít k vytvoření vazby k jednoduchým vlastnostem, jako jsou ty, které vracejí kolekce, ale nemůžete vytvořit vazby na metody nebo služby. Následující příklad ukazuje <xref:System.Windows.Controls.TextBlock> ovládací prvek, který se váže k <xref:EnvDTE._DTE.Name%2A> vlastnosti, a <xref:System.Windows.Controls.ListBox> ovládací prvek, který vytvoří výčet <xref:EnvDTE.Window.Caption%2A> vlastností kolekce, které jsou vráceny <xref:EnvDTE._DTE.Windows%2A> vlastností.

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

 Příklad najdete v tématu [Návod: ukládání uživatelských nastavení na úvodní stránce](../extensibility/walkthrough-saving-user-settings-on-a-start-page.md).

## <a name="see-also"></a>Viz také

- [Přidání uživatelského ovládacího prvku na úvodní stránku](../extensibility/adding-user-control-to-the-start-page.md)
