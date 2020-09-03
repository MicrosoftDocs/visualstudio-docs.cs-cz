---
title: Přidání podnabídky do nabídky | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- context menus
- submenus, cascading
- cascading submenus
- menus, creating cascading submenus
ms.assetid: 692600cb-d052-40e2-bdae-4354ae7c6c84
caps.latest.revision: 44
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: f458d46395c3a902e62ba5dd4ac7d624c326700c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "68184892"
---
# <a name="adding-a-submenu-to-a-menu"></a>Přidání podnabídky do nabídky
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Tento návod sestaví na ukázce v tématu [Přidání nabídky do řádku nabídek sady Visual Studio](../extensibility/adding-a-menu-to-the-visual-studio-menu-bar.md) tím, že ukazuje, jak přidat podnabídku do nabídky **TestMenu** .  
  
 Podnabídka je sekundární nabídka, která se zobrazí v jiné nabídce. Podnabídku lze identifikovat pomocí šipky, která následuje po jejím názvu. Kliknutí na název způsobí, že se podnabídka a její příkazy zobrazí.  
  
 Tento návod vytvoří podnabídku v nabídce na řádku nabídek aplikace Visual Studio a vloží nový příkaz do podnabídky. Tento návod také implementuje nový příkaz.  
  
## <a name="prerequisites"></a>Předpoklady  
 Od sady Visual Studio 2015 nenainstalujete sadu Visual Studio SDK z webu Stažení softwaru. V instalačním programu sady Visual Studio je zahrnutý jako volitelná funkce. Sadu VS SDK můžete také nainstalovat později. Další informace najdete v tématu [instalace sady Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="adding-a-submenu-to-a-menu"></a>Přidání podnabídky do nabídky  
  
1. Podle postupu v části [Přidání nabídky do řádku nabídek sady Visual Studio](../extensibility/adding-a-menu-to-the-visual-studio-menu-bar.md) vytvořte projekt a položku nabídky. Postup v tomto návodu předpokládá, že název projektu VSIX je `TopLevelMenu` .  
  
2. Otevřete TestCommandPackage. vsct. V `<Symbols>` části přidejte `<IDSymbol>` element pro podnabídku, jednu pro skupinu podnabídky a jednu pro příkaz, vše v `<GuidSymbol>` uzlu s názvem "guidTopLevelMenuCmdSet". Toto je stejný uzel, který obsahuje `<IDSymbol>` element pro nabídku nejvyšší úrovně.  
  
    ```xml  
    <IDSymbol name="SubMenu" value="0x1100"/>  
    <IDSymbol name="SubMenuGroup" value="0x1150"/>  
    <IDSymbol name="cmdidTestSubCommand" value="0x0105"/>  
    ```  
  
3. Přidejte do oddílu nově vytvořenou podnabídku `<Menus>` .  
  
    ```xml  
    <Menu guid="guidTestCommandPackageCmdSet" id="SubMenu" priority="0x0100" type="Menu">  
        <Parent guid="guidTestCommandPackageCmdSet" id="MyMenuGroup"/>  
        <Strings>  
            <ButtonText>Sub Menu</ButtonText>  
            <CommandName>Sub Menu</CommandName>  
        </Strings>  
    </Menu>  
    ```  
  
     Dvojice identifikátoru GUID/ID nadřazené položky určuje skupinu nabídek, která byla vygenerována při [přidávání nabídky do řádku nabídek sady Visual Studio](../extensibility/adding-a-menu-to-the-visual-studio-menu-bar.md)a je podřízenou položkou nabídky nejvyšší úrovně.  
  
4. Přidejte skupinu nabídek definovanou v kroku 2 do `<Groups>` oddílu a nastavte ji jako podřízenou položku podnabídky.  
  
    ```xml  
    <Group guid="guidTestCommandPackageCmdSet" id="SubMenuGroup" priority="0x0000">  
        <Parent guid="guidTestCommandPackageCmdSet" id="SubMenu"/>  
    </Group>  
    ```  
  
5. Přidejte nový `<Button>` prvek do `<Buttons>` oddílu k definování příkazu vytvořeného v kroku 2 jako položku v podnabídce.  
  
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
  
6. Sestavte řešení a spusťte ladění. Měla by se zobrazit experimentální instance.  
  
7. Kliknutím na **TestMenu** zobrazíte novou **podnabídku s názvem sub menu**. Kliknutím na **podnabídku** otevřete podnabídku a zobrazí se nový příkaz **test sub Command**. Všimněte si, že kliknutím na **příkaz Test sub Command** neprovedete žádnou akci.  
  
## <a name="adding-a-command"></a>Přidání příkazu  
  
1. Otevřete TestCommand.cs a přidejte následující ID příkazu za existující ID příkazu.  
  
    ```csharp  
    public const int cmdidTestSubCmd = 0x105;  
    ```  
  
2. Přidejte dílčí příkaz. Najděte konstruktor příkazu. Přidejte následující řádky hned za volání `AddCommand` metody.  
  
    ```csharp  
    CommandID subCommandID = new CommandID(CommandSet, (int)TestCommandPackageGuids.cmdidTestSubCmd);  
    MenuCommand subItem = new MenuCommand(  
        new EventHandler(SubItemCallback), subCommandID);  
    commandService.AddCommand(subItem);  
  
    ```  
  
     `SubItemCallback`Obslužná rutina příkazu bude definována později. Konstruktor by teď měl vypadat takto:  
  
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
                    MenuCommand subItem = new MenuCommand(  
                        new EventHandler(SubItemCallback), subCommandID);  
                    commandService.AddCommand(subItem);  
                }  
    ```  
  
3. Přidejte SubItemCallback (). Toto je metoda, která je volána při kliknutí na nový příkaz v podnabídce.  
  
    ```csharp  
    private void SubItemCallback(object sender, EventArgs e)  
    {  
        IVsUIShell uiShell = (IVsUIShell)this.ServiceProvider.GetService(  
            typeof(SVsUIShell));  
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
  
4. Sestavte projekt a spusťte ladění. Měla by se zobrazit experimentální instance.  
  
5. V nabídce **TestMenu** klikněte na **podnabídku** a potom klikněte na příkaz **test sub Command**. Zobrazí se okno se zprávou a zobrazí se text, "testovací příkaz uvnitř TestCommand. SubItemCallback ()".  
  
## <a name="see-also"></a>Viz také  
 [Přidání nabídky do řádku nabídek sady Visual Studio](../extensibility/adding-a-menu-to-the-visual-studio-menu-bar.md)   
 [Příkazy, nabídky a panely nástrojů](../extensibility/internals/commands-menus-and-toolbars.md)
