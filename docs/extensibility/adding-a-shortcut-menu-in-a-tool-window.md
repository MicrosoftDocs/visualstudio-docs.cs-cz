---
title: Přidání místní nabídky v okně nástroje | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- context menus, adding to tool windows
- menus, context menus
- shortcut menus, adding to tool windows
- tool windows, adding context menus
ms.assetid: 50234537-9e95-4b7e-9cb7-e5cf26d6e9d2
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: a5567fd2fe72b8fcc102c8609ac0d155f78141a9
ms.sourcegitcommit: 8ee7efb70a1bfebcb6dd9855b926a4ff043ecf35
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/17/2018
ms.locfileid: "39078612"
---
# <a name="add-a-shortcut-menu-in-a-tool-window"></a>Přidat místní nabídku v panelu nástrojů
Tento názorný postup vloží nabídku v panelu nástrojů. Místní nabídka je nabídka, která se zobrazí, když uživatel klepne pravým tlačítkem na tlačítko, textového pole nebo pozadí okna. Příkazy v místní nabídce se chová stejně jako příkazy na jiné nabídky nebo panely nástrojů. Pro podporu místní nabídky, zadejte ho *.vsct* souborů a zobrazit je v reakci na klikněte pravým tlačítkem myši.  
  
 Panel nástrojů se skládá z uživatelský ovládací prvek WPF v, která dědí z třídy okna vlastního nástroje <xref:Microsoft.VisualStudio.Shell.ToolWindowPane>.  
  
 Tento návod ukazuje, jak vytvořit místní nabídce jako nabídky sady Visual Studio, deklarováním položek nabídky v *.vsct* souboru a pak pomocí Managed Package Framework pro implementaci ve třídě, která definuje panel nástrojů. Tento přístup umožňuje přístup k příkazy sady Visual Studio, prvky uživatelského rozhraní a model objektu automatizace.  
  
 Případně, pokud vaši nabídku nebudou přístup k funkcím sady Visual Studio, můžete použít <xref:System.Windows.FrameworkElement.ContextMenu%2A> vlastnost elementu XAML do uživatelského ovládacího prvku. Další informace najdete v tématu [ContextMenu](/dotnet/framework/wpf/controls/contextmenu).  
  
## <a name="prerequisites"></a>Požadavky  
 Spouští se v sadě Visual Studio 2015, nenainstalujete sadu Visual Studio SDK ze služby Stažení softwaru. Je zahrnut jako volitelná funkce v instalačním programu sady Visual Studio. VS SDK můžete také nainstalovat později. Další informace najdete v tématu [instalace sady Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="create-the-tool-window-shortcut-menu-package"></a>Vytvořit balíček nástroje okno místní nabídky  
  
1.  Vytvořte projekt VSIX s názvem `TWShortcutMenu` a přidejte šablonu okno nástroje s názvem **místní nabídka** k němu. Další informace o vytvoření panelu nástrojů najdete v tématu [vytváření rozšíření pomocí panelu nástrojů](../extensibility/creating-an-extension-with-a-tool-window.md).  
  
## <a name="specifying-the-shortcut-menu"></a>Určení nabídku  
 Místní nabídky, jako je uvedena v tomto návodu umožňuje uživateli vybrat ze seznamu barev, které jsou použity k vyplnění pozadí panelu nástrojů.  
  
1.  V *ShortcutMenuPackage.vsct*, vyhledejte v guidsymbol – element s názvem guidShortcutMenuPackageCmdSet a deklarujte místní nabídku, skupina místní nabídky a možnosti nabídky. Guidsymbol – element by teď měl vypadat takto:  
  
    ```xml  
    <GuidSymbol name="guidShortcutMenuPackageCmdSet" value="{00000000-0000-0000-0000-0000}"> // your GUID here  
        <IDSymbol name="ShortcutMenuCommandId" value="0x0100" />  
        <IDSymbol name="ColorMenu" value="0x1000"/>  
        <IDSymbol name="ColorGroup" value="0x1100"/>  
        <IDSymbol name="cmdidRed" value="0x102"/>  
        <IDSymbol name="cmdidYellow" value="0x103"/>  
        <IDSymbol name="cmdidBlue" value="0x104"/>  
    </GuidSymbol>  
    ```  
  
2.  Bezprostředně před prvek tlačítka vytvořit prvek nabídky a potom v něm definovat nabídku.  
  
    ```vb  
    <Menus>  
      <Menu guid="guidShortcutMenuPackageCmdSet" id="ColorMenu" type="Context">  
        <Strings>  
          <ButtonText>Color change</ButtonText>  
          <CommandName>ColorChange</CommandName>  
        </Strings>  
      </Menu>  
    </Menus>  
    ```  
  
     Místní nabídka nemá nadřazenou položku, protože není součástí nabídky nebo panelu nástrojů.  
  
3.  Vytvořte prvek skupiny s do skupinového elementu, který obsahuje položky místní nabídky a přidružte skupinu nabídku.  
  
    ```xml  
    <Groups>  
        <Group guid="guidShortcutMenuPackageCmdSet" id="ColorGroup">  
            <Parent guid="guidShortcutMenuPackageCmdSet" id="ColorMenu"/>  
        </Group>  
    </Groups>  
    ```  
  
4.  V elementu tlačítka definujte příkazy, které se zobrazí v místní nabídce. Tlačítka element by měl vypadat nějak takto:  
  
    ```xml  
    <Buttons>  
        <Button guid="guidShortcutMenuPackageCmdSet" id="ShortcutMenuCommandId" priority="0x0100" type="Button">  
            <Parent guid="guidSHLMainMenu" id="IDG_VS_WNDO_OTRWNDWS1"/>  
            <Icon guid="guidImages" id="bmpPic1" />  
            <Strings>  
                <ButtonText>ShortcutMenu</ButtonText>  
            </Strings>  
        </Button>  
  
        <Button guid="guidShortcutMenuPackageCmdSet" id="cmdidRed" priority="1" type="Button">  
            <Parent guid="guidShortcutMenuPackageCmdSet" id="ColorGroup" />  
            <Strings>  
                <ButtonText>Red</ButtonText>  
            </Strings>  
        </Button>  
  
        <Button guid="guidShortcutMenuPackageCmdSet" id="cmdidYellow" priority="3" type="Button">  
            <Parent guid="guidShortcutMenuPackageCmdSet" id="ColorGroup" />  
            <Strings>  
                <ButtonText>Yellow</ButtonText>  
            </Strings>  
        </Button>  
  
        <Button guid="guidShortcutMenuPackageCmdSet" id="cmdidBlue" priority="5" type="Button">  
            <Parent guid="guidShortcutMenuPackageCmdSet" id="ColorGroup" />  
            <Strings>  
                <ButtonText>Blue</ButtonText>  
            </Strings>  
        </Button>  
    </Buttons>  
    ```  
  
5.  V *ShortcutMenuCommand.cs*, přidejte definice příkazu nastavený identifikátor GUID, nabídku a položky nabídky.  
  
    ```csharp  
    public const string guidShortcutMenuPackageCmdSet = "00000000-0000-0000-0000-00000000"; // your GUID will differ  
    public const int ColorMenu = 0x1000;  
    public const int cmdidRed = 0x102;  
    public const int cmdidYellow = 0x103;  
    public const int cmdidBlue = 0x104;  
    ```  
  
     Jedná se stejným ID příkazů, které jsou definovány v sekci symboly *ShortcutMenuPackage.vsct* souboru. Skupinu kontextu zde není obsažena vzhledem k tomu, že se vyžaduje jenom v *.vsct* souboru.  
  
## <a name="implementing-the-shortcut-menu"></a>Implementace nabídku  
 Tato část implementuje místní nabídku a její příkazy.  
  
1.  V *ShortcutMenu.cs*, panel nástrojů můžete získat službu příkazu nabídky, ale nikoli ovládací prvek obsahuje. Následující kroky ukazují, jak chcete zpřístupnit službu příkazu nabídky do uživatelského ovládacího prvku.  
  
2.  V *ShortcutMenu.cs*, přidejte následující příkazy using:  
  
    ```csharp  
    using Microsoft.VisualStudio.Shell;  
    using System.ComponentModel.Design;  
    ```  
  
3.  Přepište metodu Initialize() panel nástrojů a získat službu příkazu nabídky a přidejte ovládací prvek, předá službu příkazu nabídky do konstruktoru:  
  
    ```csharp  
    protected override void Initialize()  
    {  
        var commandService = (OleMenuCommandService)GetService(typeof(IMenuCommandService));  
        Content = new ShortcutMenuControl(commandService);  
    }  
    ```  
  
4.  V konstruktoru místní nabídka okna nástroje odeberte řádek, který přidá ovládací prvek. Konstruktor by teď měl vypadat takto:  
  
    ```csharp  
    public ShortcutMenu() : base(null)  
    {  
        this.Caption = "ShortcutMenu";  
        this.BitmapResourceID = 301;  
        this.BitmapIndex = 1;  
    }  
    ```  
  
5.  V *ShortcutMenuControl.xaml.cs*, přidat soukromé pole pro službu příkazu nabídky a změnit konstruktoru ovládacího prvku abyste mohli službu příkazu nabídky. Pak použijte službu příkazu nabídky přidat příkazy místní nabídky. Konstruktor ShortcutMenuControl by teď měl vypadat jako v následujícím kódu. Obslužná rutina příkazu bude definici později.  
  
    ```csharp  
    public ShortcutMenuControl(OleMenuCommandService service)  
    {  
        this.InitializeComponent();  
        commandService = service;  
  
        if (null !=commandService)  
        {  
            // Create an alias for the command set guid.  
            Guid guid = new Guid(ShortcutMenuCommand.guidShortcutMenuPackageCmdSet);  
  
            // Create the command IDs.   
            var red = new CommandID(guid, ShortcutMenuCommand.cmdidRed);  
            var yellow = new CommandID(guid, ShortcutMenuCommand.cmdidYellow);  
            var blue = new CommandID(guid, ShortcutMenuCommand.cmdidBlue);  
  
            // Add a command for each command ID.  
            commandService.AddCommand(new MenuCommand(ChangeColor, red));  
            commandService.AddCommand(new MenuCommand(ChangeColor, yellow));  
            commandService.AddCommand(new MenuCommand(ChangeColor, blue));  
        }  
    }  
    ```  
  
6.  V *ShortcutMenuControl.xaml*, přidejte <xref:System.Windows.UIElement.MouseRightButtonDown> událostí na nejvyšší úrovni <xref:System.Windows.Controls.UserControl> elementu. Soubor XAML by měl nyní vypadat nějak takto:  
  
    ```vb  
    <UserControl x:Class="TWShortcutMenu.ShortcutMenuControl"  
        xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"  
        xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"  
        xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"  
        xmlns:d="http://schemas.microsoft.com/expression/blend/2008"  
            Background="{DynamicResource VsBrush.Window}"  
            Foreground="{DynamicResource VsBrush.WindowText}"  
            mc:Ignorable="d"  
            d:DesignHeight="300" d:DesignWidth="300"  
            Name="MyToolWindow"  
            MouseRightButtonDown="MyToolWindow_MouseRightButtonDown">  
        <Grid>  
            <StackPanel Orientation="Vertical">  
                <TextBlock Margin="10" HorizontalAlignment="Center">ShortcutMenu</TextBlock>  
            </StackPanel>  
        </Grid>  
    </UserControl>  
    ```  
  
7.  V *ShortcutMenuControl.xaml.cs*, přidejte zástupnou proceduru pro obslužnou rutinu události.  
  
    ```csharp  
    private void MyToolWindow_MouseRightButtonDown(object sender, MouseButtonEventArgs e)  
    {  
    . . .  
    }  
    ```  
  
8.  Přidejte následující příkazy using do stejného souboru:  
  
    ```csharp  
    using Microsoft.VisualStudio.Shell;  
    using System.ComponentModel.Design;  
    using System;  
    using System.Windows.Input;  
    using System.Windows.Media;  
    ```  
  
9. Implementace `MyToolWindowMouseRightButtonDown` událostí následujícím způsobem.  
  
    ```csharp  
    private void MyToolWindow_MouseRightButtonDown(object sender, MouseButtonEventArgs e)  
    {  
        if (null != commandService)  
        {  
            CommandID menuID = new CommandID(  
                new Guid(ShortcutMenuCommand.guidShortcutMenuPackageCmdSet),  
                ShortcutMenuCommand.ColorMenu);  
            Point p = this.PointToScreen(e.GetPosition(this));  
            commandService.ShowContextMenu(menuID, (int)p.X, (int)p.Y);  
        }  
    }  
    ```  
  
     Tím se vytvoří <xref:System.ComponentModel.Design.CommandID> objekt pro nabídku, polohu kliknutí myší a otevře místní nabídku v dané oblasti s použitím <xref:Microsoft.VisualStudio.Shell.OleMenuCommandService.ShowContextMenu%2A> metody.  
  
10. Implementace obslužné rutiny příkazu.  
  
    ```csharp  
    private void ChangeColor(object sender, EventArgs e)  
    {  
        var mc = sender as MenuCommand;  
  
        switch (mc.CommandID.ID)  
        {  
            case ShortcutMenuCommand.cmdidRed:  
                MyToolWindow.Background = Brushes.Red;  
                break;  
            case ShortcutMenuCommand.cmdidYellow:  
                MyToolWindow.Background = Brushes.Yellow;  
                break;  
            case ShortcutMenuCommand.cmdidBlue:  
                MyToolWindow.Background = Brushes.Blue;  
                break;  
        }  
    }  
    ```  
  
     V takovém případě právě jedna metoda zpracovává události pro všechny položky nabídky určením <xref:System.ComponentModel.Design.CommandID> a odpovídajícím způsobem nastavení barvy pozadí. Pokud položek nabídky původně obsahovala nesouvisejících příkazy, by jste vytvořili obslužnou rutinu události samostatné pro každý příkaz.  
  
## <a name="test-the-tool-window-features"></a>Testování funkcí okno nástroje  
  
1.  Sestavte projekt a spusťte ladění. Zobrazí se experimentální instance.  
  
2.  V experimentální instanci aplikace, klikněte na tlačítko **zobrazení / ostatní Windows**a potom klikněte na tlačítko **místní nabídka**. Tím by se zobrazit okno nástroje.  
  
3.  Klikněte pravým tlačítkem myši v těle panel nástrojů. Místní nabídky, který má seznam barev má být zobrazena.  
  
4.  Klepněte na požadovanou barvu v místní nabídce. Na vybraném barevném změňte barvu pozadí okna nástrojů.  
  
## <a name="see-also"></a>Viz také:  
 [Příkazy, nabídky a panely nástrojů](../extensibility/internals/commands-menus-and-toolbars.md)   
 [Používání a poskytování služeb](../extensibility/using-and-providing-services.md)