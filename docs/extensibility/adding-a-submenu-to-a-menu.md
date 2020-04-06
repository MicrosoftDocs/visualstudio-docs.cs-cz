---
title: Přidání podnabídky do nabídky | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- context menus
- submenus, cascading
- cascading submenus
- menus, creating cascading submenus
ms.assetid: 692600cb-d052-40e2-bdae-4354ae7c6c84
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 59c9364d03aab135f7c9b4bf91df21b949e78ee4
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80740268"
---
# <a name="add-a-submenu-to-a-menu"></a>Přidání podnabídky do nabídky
Tento návod vychází z ukázky v [přidat nabídku do panelu nabídek Sady Visual Studio](../extensibility/adding-a-menu-to-the-visual-studio-menu-bar.md) tím, že ukazuje, jak přidat podnabídku do nabídky **TestMenu.**

 Podnabídka je sekundární nabídka, která se zobrazí v jiné nabídce. Podnabídku lze identifikovat šipkou, která následuje za jejím názvem. Klepnutí na název způsobí zobrazení podnabídky a jejích příkazů.

 Tento návod vytvoří podnabídku v nabídce na panelu nabídek sady Visual Studio a umístí nový příkaz do podnabídky. Návod také implementuje nový příkaz.

## <a name="prerequisites"></a>Požadavky
 Počínaje Visual Studio 2015 neinstalujete sady Visual Studio SDK ze služby stažení. Je součástí volitelné funkce v nastavení sady Visual Studio. VS SDK můžete také nainstalovat později. Další informace naleznete [v tématu Instalace sady Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="add-a-submenu-to-a-menu"></a>Přidání podnabídky do nabídky

1. Podle pokynů v [části Přidání nabídky na panel nabídek sady Visual Studio](../extensibility/adding-a-menu-to-the-visual-studio-menu-bar.md) vytvořte položku projektu a nabídky. Kroky v tomto návodu předpokládají, že název `TopLevelMenu`projektu VSIX je .

2. Otevřete *soubor TestCommandPackage.vsct*. V `<Symbols>` části přidejte `<IDSymbol>` prvek pro podnabídku, jeden pro skupinu podnabídky a `<GuidSymbol>` jeden pro příkaz, všechny v uzlu s názvem "guidTopLevelMenuCmdSet." Jedná se o stejný uzel, který obsahuje `<IDSymbol>` prvek pro nabídku nejvyšší úrovně.

    ```xml
    <IDSymbol name="SubMenu" value="0x1100"/>
    <IDSymbol name="SubMenuGroup" value="0x1150"/>
    <IDSymbol name="cmdidTestSubCommand" value="0x0105"/>
    ```

3. Přidejte nově vytvořenou `<Menus>` podnabídku do oddílu.

    ```xml
    <Menu guid="guidTestCommandPackageCmdSet" id="SubMenu" priority="0x0100" type="Menu">
        <Parent guid="guidTestCommandPackageCmdSet" id="MyMenuGroup"/>
        <Strings>
            <ButtonText>Sub Menu</ButtonText>
            <CommandName>Sub Menu</CommandName>
        </Strings>
    </Menu>
    ```

     Dvojice GUID/ID nadřazené určuje skupinu nabídek, která byla vygenerována v [nabídce Přidat nabídku na panel nabídek sady Visual Studio](../extensibility/adding-a-menu-to-the-visual-studio-menu-bar.md), a je podřízenou položkou nabídky nejvyšší úrovně.

4. Přidejte skupinu nabídek definovanou `<Groups>` v kroku 2 do oddílu a udělejte z ní podřízenou položku podnabídky.

    ```xml
    <Group guid="guidTestCommandPackageCmdSet" id="SubMenuGroup" priority="0x0000">
        <Parent guid="guidTestCommandPackageCmdSet" id="SubMenu"/>
    </Group>
    ```

5. Přidejte `<Button>` do oddílu nový prvek a `<Buttons>` definujte příkaz vytvořený v kroku 2 jako položku v podnabídce.

    ```xml
    <Button guid="guidTestCommandPackageCmdSet" id="cmdidTestSubCommand" priority="0x0000" type="Button">
        <Parent guid="guidTestCommandPackageCmdSet" id="SubMenuGroup" />
        <Icon guid="guidImages" id="bmpPic2" />
        <Strings>
           <CommandName>cmdidTestSubCommand</CommandName>
           <ButtonText>Test Sub Command</ButtonText>
        </Strings>
    </Button>
    ```

6. Sestavte řešení a začněte ladit. Měli byste vidět experimentální instanci.

7. Klepnutím na tlačítko **TestMenu** zobrazíte novou podnabídku s názvem **Podnabídka**. Klepnutím na **podnabídku** otevřete podnabídku a zobrazí se nový příkaz **Testovat dílčí příkaz**. Všimněte si, že klepnutím na **tlačítko Test Sub Command** neprovede tenicál.

## <a name="add-a-command"></a>Přidání příkazu

1. Otevřete *TestCommand.cs* a za existující ID příkazu přidejte následující ID příkazu.

    ```csharp
    public const int cmdidTestSubCmd = 0x0105;
    ```

2. Přidejte dílčí příkaz. Najděte konstruktor příkazů. Přidejte následující řádky těsně za `AddCommand` volání metody.

    ```csharp
    CommandID subCommandID = new CommandID(CommandSet, cmdidTestSubCmd);
    MenuCommand subItem = new MenuCommand(new EventHandler(SubItemCallback), subCommandID);
    commandService.AddCommand(subItem);
    ```

    Obslužná rutina `SubItemCallback` příkazu bude definována později. Konstruktor by nyní měl vypadat takto:

    ```csharp
    private TestCommand(Package package)
    {
        if (package == null)
        {
            throw new ArgumentNullException("package");
        }

        this.package = package;

        OleMenuCommandService commandService = this.ServiceProvider.GetService(typeof(IMenuCommandService)) as OleMenuCommandService;
        if (commandService != null)
        {
            var menuCommandID = new CommandID(CommandSet, CommandId);
            var menuItem = new MenuCommand(this.MenuItemCallback, menuCommandID);
            commandService.AddCommand(menuItem);

            CommandID subCommandID = new CommandID(CommandSet, cmdidTestSubCmd);
            MenuCommand subItem = new MenuCommand(new EventHandler(SubItemCallback), subCommandID);
            commandService.AddCommand(subItem);
        }
    }
    ```

3. Přidat `SubItemCallback()`. Toto je metoda, která je volána po klepnutí na nový příkaz v podnabídce.

    ```csharp
    private void SubItemCallback(object sender, EventArgs e)
    {
        IVsUIShell uiShell = (IVsUIShell)this.ServiceProvider.GetServiceAsync(typeof(SVsUIShell));
        Guid clsid = Guid.Empty;
        int result;
        uiShell.ShowMessageBox(
            0,
            ref clsid,
            "TestCommand",
            string.Format(CultureInfo.CurrentCulture,
            "Inside TestCommand.SubItemCallback()",
            this.ToString()),
            string.Empty,
            0,
            OLEMSGBUTTON.OLEMSGBUTTON_OK,
            OLEMSGDEFBUTTON.OLEMSGDEFBUTTON_FIRST,
            OLEMSGICON.OLEMSGICON_INFO,
            0,
            out result);
    }
    ```

4. Sestavení projektu a začít ladění. Experimentální instance by se měla zobrazit.

5. V nabídce **TestMenu** klepněte na **položku Dílčí nabídka** a potom klepněte na příkaz **Testovat dílčí položky**. Mělo by se zobrazit okno se zprávou a zobrazit text "Test Command Inside TestCommand.SubItemCallback()".

## <a name="see-also"></a>Viz také

- [Přidání nabídky do panelu nabídek sady Visual Studio](../extensibility/adding-a-menu-to-the-visual-studio-menu-bar.md)
- [Příkazy, nabídky a panely nástrojů](../extensibility/internals/commands-menus-and-toolbars.md)
