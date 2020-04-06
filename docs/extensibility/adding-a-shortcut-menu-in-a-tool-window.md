---
title: Přidání místní nabídky do okna nástroje | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- context menus, adding to tool windows
- menus, context menus
- shortcut menus, adding to tool windows
- tool windows, adding context menus
ms.assetid: 50234537-9e95-4b7e-9cb7-e5cf26d6e9d2
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 0f5b5b79721aa910c46e2580228d3f3a7836f70d
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80740291"
---
# <a name="add-a-shortcut-menu-in-a-tool-window"></a>Přidání místní nabídky do okna nástroje
Tento návod umístí místní nabídku do okna nástroje. Místní nabídka je nabídka, která se zobrazí, když uživatel klepne pravým tlačítkem myši na tlačítko, textové pole nebo pozadí okna. Příkazy v místní nabídce se chovají stejně jako příkazy v jiných nabídkách nebo panelech nástrojů. Chcete-li místní nabídku podporovat, zadejte ji do souboru *.vsct* a zobrazte ji v reakci na klepnutí pravým tlačítkem myši.

Okno nástroje se skládá z uživatelského ovládacího prvku WPF <xref:Microsoft.VisualStudio.Shell.ToolWindowPane>ve vlastní třídě okna nástroje, která dědí z .

Tento návod ukazuje, jak vytvořit místní nabídku jako nabídku sady Visual Studio deklarováním položek nabídky v souboru *.vsct* a potom pomocí rozhraní Managed Package Framework k jejich implementaci do třídy, která definuje okno nástroje. Tento přístup usnadňuje přístup k příkazům sady Visual Studio, prvkům uživatelského rozhraní a objektovému modelu Automation.

Případně pokud místní nabídka nebude mít přístup k funkcím <xref:System.Windows.FrameworkElement.ContextMenu%2A> sady Visual Studio, můžete použít vlastnost prvku XAML v uživatelském ovládacím prvku. Další informace naleznete v tématu [ContextMenu](/dotnet/framework/wpf/controls/contextmenu).

## <a name="prerequisites"></a>Požadavky
Počínaje Visual Studio 2015 neinstalujete sady Visual Studio SDK ze služby stažení. Je součástí volitelné funkce v nastavení sady Visual Studio. VS SDK můžete také nainstalovat později. Další informace naleznete [v tématu Instalace sady Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="create-the-tool-window-shortcut-menu-package"></a>Vytvoření balíčku nabídky zástupce okna nástroje

1. Vytvořte projekt VSIX s názvem `TWShortcutMenu` a přidejte do něj šablonu okna nástroje s názvem **ShortcutMenu.** Další informace o vytvoření okna nástroje naleznete v [tématu Vytvoření rozšíření s oknem nástroje](../extensibility/creating-an-extension-with-a-tool-window.md).

## <a name="specifying-the-shortcut-menu"></a>Určení místní nabídky
Místní nabídka, například nabídka zobrazená v tomto návodu, umožňuje uživateli vybrat ze seznamu barev, které se používají k vyplnění pozadí okna nástroje.

1. V *souboru ShortcutMenuPackage.vsct*vyhledejte v elementu GuidSymbol s názvem guidShortcutMenuPackageCmdSet a deklarujte místní nabídku, skupinu místních nabídek a možnosti nabídky. Prvek GuidSymbol by nyní měl vypadat takto:

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

2. Těsně před buttons element, vytvořte menu element a pak definovat místní nabídku v něm.

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

3. Vytvořte prvek Skupiny s prvkem Skupiny, který obsahuje položky místní nabídky, a přidružte skupinu k místní nabídce.

    ```xml
    <Groups>
        <Group guid="guidShortcutMenuPackageCmdSet" id="ColorGroup">
            <Parent guid="guidShortcutMenuPackageCmdSet" id="ColorMenu"/>
        </Group>
    </Groups>
    ```

4. V elementu Buttons definujte jednotlivé příkazy, které se zobrazí v místní nabídce. Prvek Buttons by měl vypadat takto:

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

5. V *ShortcutMenuCommand.cs*přidejte definice identifikátoru GUID sady příkazů, místní nabídky a položek nabídky.

    ```csharp
    public const string guidShortcutMenuPackageCmdSet = "00000000-0000-0000-0000-00000000"; // your GUID will differ
    public const int ColorMenu = 0x1000;
    public const int cmdidRed = 0x102;
    public const int cmdidYellow = 0x103;
    public const int cmdidBlue = 0x104;
    ```

    Jedná se o stejná ID příkazů, která jsou definována v části Symboly souboru *ShortcutMenuPackage.vsct.* Skupina kontextu zde není zahrnuta, protože je vyžadována pouze v souboru *.vsct.*

## <a name="implementing-the-shortcut-menu"></a>Implementace místní nabídky
 Tato část implementuje místní nabídku a její příkazy.

1. V *ShortcutMenu.cs*může okno nástroje získat službu příkazu nabídky, ale ovládací prvek, který obsahuje, nemůže. Následující kroky ukazují, jak zpřístupnit službu příkazu nabídky uživatelskému ovládacímu prvku.

2. V *ShortcutMenu.cs*přidejte následující příkazy:

    ```csharp
    using Microsoft.VisualStudio.Shell;
    using System.ComponentModel.Design;
    ```

3. Přepsat metodu Initialize() okna nástroje, chcete-li získat službu příkazu nabídky a přidat ovládací prvek a předat příkazovou službu nabídky konstruktoru:

    ```csharp
    protected override void Initialize()
    {
        var commandService = (OleMenuCommandService)GetService(typeof(IMenuCommandService));
        Content = new ShortcutMenuControl(commandService);
    }
    ```

4. V konstruktoru okna nástroje Zkratkamenu odeberte čáru, která přidává ovládací prvek. Konstruktor by nyní měl vypadat takto:

    ```csharp
    public ShortcutMenu() : base(null)
    {
        this.Caption = "ShortcutMenu";
        this.BitmapResourceID = 301;
        this.BitmapIndex = 1;
    }
    ```

5. V *ShortcutMenuControl.xaml.cs*přidejte soukromé pole pro službu příkazu nabídky a změňte konstruktor ovládacího prvku tak, aby převzal službu příkazu nabídky. Potom pomocí služby příkazů nabídky přidejte příkazy místní nabídky. Konstruktor ShortcutMenuControl by nyní měl vypadat jako následující kód. Obslužná rutina příkazu bude definována později.

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

6. V *souboru ShortcutMenuControl.xaml*přidejte <xref:System.Windows.UIElement.MouseRightButtonDown> <xref:System.Windows.Controls.UserControl> událost do prvku nejvyšší úrovně. Soubor XAML by nyní měl vypadat takto:

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

7. V *ShortcutMenuControl.xaml.cs*přidejte zástupný kód pro obslužnou rutinu události.

    ```csharp
    private void MyToolWindow_MouseRightButtonDown(object sender, MouseButtonEventArgs e)
    {
    . . .
    }
    ```

8. Do stejného souboru přidejte následující direktivy pomocí:

    ```csharp
    using Microsoft.VisualStudio.Shell;
    using System.ComponentModel.Design;
    using System;
    using System.Windows.Input;
    using System.Windows.Media;
    ```

9. Implementujte `MyToolWindowMouseRightButtonDown` událost následujícím způsobem.

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

    Tím se <xref:System.ComponentModel.Design.CommandID> vytvoří objekt pro místní nabídku, identifikuje umístění klepnutí myší a pomocí <xref:Microsoft.VisualStudio.Shell.OleMenuCommandService.ShowContextMenu%2A> metody otevře místní nabídku v tomto umístění.

10. Implementujte obslužnou rutinu příkazu.

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

    V tomto případě pouze jedna metoda zpracovává události pro všechny <xref:System.ComponentModel.Design.CommandID> položky nabídky identifikací a nastavením barvy pozadí odpovídajícím způsobem. Pokud by položky nabídky obsahovaly nesouvisející příkazy, vytvořili byste pro každý příkaz samostatnou obslužnou rutinu události.

## <a name="test-the-tool-window-features"></a>Testování funkcí okna nástroje

1. Sestavení projektu a začít ladění. Zobrazí se experimentální instance.

2. V experimentální instanci klepněte na položku **Zobrazit / Ostatní windows**a potom klepněte na příkaz **ShortcutMenu**. To by mělo zobrazit okno nástroje.

3. Klepněte pravým tlačítkem myši do těla okna nástroje. Měla by být zobrazena místní nabídka se seznamem barev.

4. Klepněte na barvu v místní nabídce. Barva pozadí okna nástroje by měla být změněna na vybranou barvu.

## <a name="see-also"></a>Viz také
- [Příkazy, nabídky a panely nástrojů](../extensibility/internals/commands-menus-and-toolbars.md)
- [Využívání a poskytování služeb](../extensibility/using-and-providing-services.md)
