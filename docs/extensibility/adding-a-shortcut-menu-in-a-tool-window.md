---
title: Přidání místní nabídky v okně nástroje | Microsoft Docs
description: Naučte se, jak přidat místní nabídku do panelu nástrojů v aplikaci Visual Studio, který se zobrazí po kliknutí pravým tlačítkem na tlačítko, textové pole nebo pozadí okna.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
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
ms.openlocfilehash: 2e14d948bf5d4b637002ca1f2ec8be37b64dc22b
ms.sourcegitcommit: d6207a3a590c9ea84e3b25981d39933ad5f19ea3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/24/2020
ms.locfileid: "95597870"
---
# <a name="add-a-shortcut-menu-in-a-tool-window"></a>Přidání místní nabídky v okně nástroje
Tento návod vloží místní nabídku do okna nástroje. Místní nabídka je nabídka, která se zobrazí, když uživatel klikne pravým tlačítkem myši na tlačítko, textové pole nebo okno na pozadí. Příkazy v místní nabídce se chovají stejně jako příkazy v jiných nabídkách nebo panelech nástrojů. Chcete-li podporovat místní nabídku, zadejte ji v souboru *. vsct* a zobrazte ji v reakci na tlačítko myši pravým tlačítkem myši.

Okno nástroje se skládá z uživatelského ovládacího prvku WPF ve vlastní třídě panelu nástrojů, která dědí z <xref:Microsoft.VisualStudio.Shell.ToolWindowPane> .

Tento návod ukazuje, jak vytvořit místní nabídku jako nabídku aplikace Visual Studio deklarací položek nabídky v souboru *. vsct* a poté pomocí spravovaného rozhraní balíčku pro implementaci ve třídě, která definuje okno nástroje. Tento přístup usnadňuje přístup k příkazům sady Visual Studio, k prvkům uživatelského rozhraní a objektovému modelu automatizace.

Případně, pokud vaše místní nabídka nebude přistupovat k funkcím sady Visual Studio, můžete použít <xref:System.Windows.FrameworkElement.ContextMenu%2A> vlastnost prvku XAML v uživatelském ovládacím prvku. Další informace najdete [v tématu](/dotnet/framework/wpf/controls/contextmenu)věnovaném dopři.

## <a name="prerequisites"></a>Předpoklady
Od sady Visual Studio 2015 nenainstalujete sadu Visual Studio SDK z webu Stažení softwaru. V instalačním programu sady Visual Studio je zahrnutý jako volitelná funkce. Sadu VS SDK můžete také nainstalovat později. Další informace najdete v tématu [instalace sady Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="create-the-tool-window-shortcut-menu-package"></a>Vytvoření balíčku místní nabídky okna nástrojů

1. Vytvořte projekt VSIX s názvem `TWShortcutMenu` a přidejte do něj šablonu okna nástrojů **ShortcutMenu** s názvem Outlook. Další informace o vytváření panelu nástrojů naleznete v tématu [Vytvoření rozšíření s oknem nástrojů](../extensibility/creating-an-extension-with-a-tool-window.md).

## <a name="specifying-the-shortcut-menu"></a>Zadání místní nabídky
Místní nabídka, například ta, která je znázorněna v tomto návodu, umožňuje uživateli vybrat ze seznamu barev, který se používá k vyplnění pozadí okna nástroje.

1. V *ShortcutMenuPackage. vsct* vyhledejte v elementu GuidSymbol s názvem guidShortcutMenuPackageCmdSet a deklarujte místní nabídku, skupinu místních nabídek a možnosti nabídky. Element GuidSymbol by teď měl vypadat takto:

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

2. Těsně před elementem tlačítka vytvořte element Menus a pak definujte místní nabídku.

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

    Místní nabídka nemá nadřazený prvek, protože není součástí nabídky nebo panelu nástrojů.

3. Vytvořte prvek skupiny pomocí prvku skupiny, který obsahuje položky místní nabídky a přidružte skupinu k místní nabídce.

    ```xml
    <Groups>
        <Group guid="guidShortcutMenuPackageCmdSet" id="ColorGroup">
            <Parent guid="guidShortcutMenuPackageCmdSet" id="ColorMenu"/>
        </Group>
    </Groups>
    ```

4. V prvku tlačítka definujte jednotlivé příkazy, které se zobrazí v místní nabídce. Element Buttons by měl vypadat takto:

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

5. Do *ShortcutMenuCommand.cs* přidejte definice pro identifikátor GUID sady příkazů, místní nabídku a položky nabídky.

    ```csharp
    public const string guidShortcutMenuPackageCmdSet = "00000000-0000-0000-0000-00000000"; // your GUID will differ
    public const int ColorMenu = 0x1000;
    public const int cmdidRed = 0x102;
    public const int cmdidYellow = 0x103;
    public const int cmdidBlue = 0x104;
    ```

    Jedná se o stejné identifikátory příkazů, které jsou definovány v části symboly souboru *ShortcutMenuPackage. vsct* . Kontextová skupina zde není obsažena, protože je požadována pouze v souboru *. vsct* .

## <a name="implementing-the-shortcut-menu"></a>Implementace místní nabídky
 Tato část implementuje místní nabídku a její příkazy.

1. V *ShortcutMenu.cs* může okno nástroje získat službu příkazu nabídky, ale ovládací prvek, který obsahuje, nemůže. Následující kroky ukazují, jak nastavit, aby byla služba příkazu nabídky k dispozici pro uživatelský ovládací prvek.

2. Do *ShortcutMenu.cs* přidejte následující direktivy using:

    ```csharp
    using Microsoft.VisualStudio.Shell;
    using System.ComponentModel.Design;
    ```

3. Přepište metodu Initialize () panelu nástrojů k získání služby příkazu nabídky a přidání ovládacího prvku, předání služby příkazu nabídky do konstruktoru:

    ```csharp
    protected override void Initialize()
    {
        var commandService = (OleMenuCommandService)GetService(typeof(IMenuCommandService));
        Content = new ShortcutMenuControl(commandService);
    }
    ```

4. V konstruktoru okna nástroje místní nabídka odeberte řádek, který přidá ovládací prvek. Konstruktor by teď měl vypadat takto:

    ```csharp
    public ShortcutMenu() : base(null)
    {
        this.Caption = "ShortcutMenu";
        this.BitmapResourceID = 301;
        this.BitmapIndex = 1;
    }
    ```

5. V *ShortcutMenuControl.XAML.cs* přidejte soukromé pole pro příkazovou službu nabídky a změňte konstruktor ovládacího prvku tak, aby probral službu příkazu nabídky. Pak použijte příkazová služba nabídky k přidání příkazů kontextové nabídky. Konstruktor ShortcutMenuControl by teď měl vypadat jako v následujícím kódu. Obslužná rutina příkazu bude definována později.

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

6. V souboru *ShortcutMenuControl. XAML* přidejte <xref:System.Windows.UIElement.MouseRightButtonDown> událost do elementu nejvyšší úrovně <xref:System.Windows.Controls.UserControl> . Soubor XAML by teď měl vypadat takto:

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

7. V *ShortcutMenuControl.XAML.cs* přidejte zástupnou proceduru pro obslužnou rutinu události.

    ```csharp
    private void MyToolWindow_MouseRightButtonDown(object sender, MouseButtonEventArgs e)
    {
    . . .
    }
    ```

8. Do stejného souboru přidejte následující direktivy using:

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

    Tím se vytvoří <xref:System.ComponentModel.Design.CommandID> objekt pro místní nabídku, určíte umístění kliknutí myší a otevře se místní nabídka v tomto umístění pomocí <xref:Microsoft.VisualStudio.Shell.OleMenuCommandService.ShowContextMenu%2A> metody.

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

    V tomto případě pouze jedna metoda zpracovává události pro všechny položky nabídky, a to tak, že identifikuje <xref:System.ComponentModel.Design.CommandID> a nastaví barvu pozadí odpovídajícím způsobem. Pokud položky nabídky obsahovaly nesouvisející příkazy, měli byste pro každý příkaz vytvořit samostatnou obslužnou rutinu události.

## <a name="test-the-tool-window-features"></a>Testování funkcí okna nástrojů

1. Sestavte projekt a spusťte ladění. Objeví se experimentální instance.

2. V experimentální instanci klikněte na **Zobrazit/další okna** a potom klikněte na **místní nabídka**. V takovém případě by se měl zobrazit okno nástroje.

3. Klikněte pravým tlačítkem myši na tělo okna nástroje. Měla by se zobrazit místní nabídka, která má seznam barev.

4. V místní nabídce klikněte na barvu. Barva pozadí okna nástroje by měla být změněna na vybranou barvu.

## <a name="see-also"></a>Viz také
- [Příkazy, nabídky a panely nástrojů](../extensibility/internals/commands-menus-and-toolbars.md)
- [Používání a poskytování služeb](../extensibility/using-and-providing-services.md)
