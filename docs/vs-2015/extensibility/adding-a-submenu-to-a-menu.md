---
title: Přidání podnabídky do nabídky | Dokumentace Microsoftu
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
- context menus
- submenus, cascading
- cascading submenus
- menus, creating cascading submenus
ms.assetid: 692600cb-d052-40e2-bdae-4354ae7c6c84
caps.latest.revision: 44
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 14ad9d2daf603dd2ca80a784251f19503fee1cba
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51738317"
---
# <a name="adding-a-submenu-to-a-menu"></a>Přidání podnabídky do nabídky
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Tento návod vychází ukázku v [přidání nabídky do řádku nabídek sady Visual Studio](../extensibility/adding-a-menu-to-the-visual-studio-menu-bar.md) zobrazením přidání podnabídky do **TestMenu** nabídky.  
  
 Podnabídky je sekundární nabídka, která se zobrazí v jiné nabídky. Podnabídky lze identifikovat podle šipku, která odpovídá jeho názvu. Kliknutím na název způsobí, že podnabídku a jeho příkazy, který se má zobrazit.  
  
 Tento návod vytvoří podnabídky do nabídky na řádku nabídek sady Visual Studio a vloží nový příkaz v podnabídce. Průvodce také implementuje nový příkaz.  
  
## <a name="prerequisites"></a>Požadavky  
 Spouští se v sadě Visual Studio 2015, nenainstalujete sadu Visual Studio SDK ze služby Stažení softwaru. Je zahrnut jako volitelná funkce v instalačním programu sady Visual Studio. VS SDK můžete také nainstalovat později. Další informace najdete v tématu [instalace sady Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="adding-a-submenu-to-a-menu"></a>Přidání podnabídky do nabídky  
  
1.  Postupujte podle kroků v [přidání nabídky do řádku nabídek sady Visual Studio](../extensibility/adding-a-menu-to-the-visual-studio-menu-bar.md) vytvoření položky projektu a nabídky. Kroky v tomto názorném postupu se předpokládá, že je název projektu VSIX `TopLevelMenu`.  
  
2.  Open TestCommandPackage.vsct. V `<Symbols>` části, přidejte `<IDSymbol>` – element pro podnabídky, jednu pro skupinu podnabídku a jednu pro příkaz, vše v `<GuidSymbol>` uzel s názvem "guidTopLevelMenuCmdSet." Toto je stejný uzel, který obsahuje `<IDSymbol>` – element pro nabídek nejvyšší úrovně.  
  
    ```xml  
    <IDSymbol name="SubMenu" value="0x1100"/>  
    <IDSymbol name="SubMenuGroup" value="0x1150"/>  
    <IDSymbol name="cmdidTestSubCommand" value="0x0105"/>  
    ```  
  
3.  Přidání podnabídky nově vytvořený `<Menus>` oddílu.  
  
    ```xml  
    <Menu guid="guidTestCommandPackageCmdSet" id="SubMenu" priority="0x0100" type="Menu">  
        <Parent guid="guidTestCommandPackageCmdSet" id="MyMenuGroup"/>  
        <Strings>  
            <ButtonText>Sub Menu</ButtonText>  
            <CommandName>Sub Menu</CommandName>  
        </Strings>  
    </Menu>  
    ```  
  
     Určuje pár GUID a ID nadřazené skupiny nabídek, který byl vygenerován v [přidání nabídky do řádku nabídek sady Visual Studio](../extensibility/adding-a-menu-to-the-visual-studio-menu-bar.md), a je podřízeným prvkem nabídek nejvyšší úrovně.  
  
4.  Přidání skupiny nabídek definovaný v kroku 2 `<Groups>` části a udělat podřízeným podnabídky.  
  
    ```xml  
    <Group guid="guidTestCommandPackageCmdSet" id="SubMenuGroup" priority="0x0000">  
        <Parent guid="guidTestCommandPackageCmdSet" id="SubMenu"/>  
    </Group>  
    ```  
  
5.  Přidat nový `<Button>` elementu `<Buttons>` oddíl pro definování příkazu, který jste vytvořili v kroku 2 jako položka v podnabídce.  
  
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
  
6.  Sestavte řešení a spusťte ladění. Měli byste vidět experimentální instanci aplikace.  
  
7.  Klikněte na tlačítko **TestMenu** zobrazíte nové podnabídky s názvem **podnabídka**. Klikněte na tlačítko **podnabídka** otevřete podnabídku a zobrazte nový příkaz **Test dílčí příkaz**. Všimněte si, že kliknete na **Test dílčí příkaz** nemá žádný účinek.  
  
## <a name="adding-a-command"></a>Přidání příkazu  
  
1.  Otevřete TestCommand.cs a přidejte následující ID příkazu za stávající ID příkazu.  
  
    ```csharp  
    public const int cmdidTestSubCmd = 0x105;  
    ```  
  
2.  Přidáte dílčí příkaz. Přejděte na příkaz konstruktor. Přidejte následující řádky bezprostředně po volání `AddCommand` metody.  
  
    ```csharp  
    CommandID subCommandID = new CommandID(CommandSet, (int)TestCommandPackageGuids.cmdidTestSubCmd);  
    MenuCommand subItem = new MenuCommand(  
        new EventHandler(SubItemCallback), subCommandID);  
    commandService.AddCommand(subItem);  
  
    ```  
  
     `SubItemCallback` Obslužná rutina příkazu bude obsahovat definici později. Konstruktor by teď měl vypadat takto:  
  
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
  
3.  Přidáte SubItemCallback(). Toto je metoda, která je volána, když dojde ke kliknutí na nový příkaz v podnabídce.  
  
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
  
4.  Sestavte projekt a spusťte ladění. Experimentální instanci aplikace by se zobrazit.  
  
5.  Na **TestMenu** nabídky, klikněte na tlačítko **podnabídka** a potom klikněte na tlačítko **Test dílčí příkaz**. Okno se zprávou by měla objevit a zobrazit text "Test příkaz uvnitř TestCommand.SubItemCallback()".  
  
## <a name="see-also"></a>Viz také  
 [Přidání nabídky do řádku nabídek sady Visual Studio](../extensibility/adding-a-menu-to-the-visual-studio-menu-bar.md)   
 [Příkazy, nabídky a panely nástrojů](../extensibility/internals/commands-menus-and-toolbars.md)

