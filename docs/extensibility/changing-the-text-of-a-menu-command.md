---
title: Změna textu příkazu nabídky | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- menus, changing text
- text, menus
- commands, changing text
ms.assetid: 5cb676a0-c6e2-47e5-bd2b-133dc8842e46
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ff6af7bdd64342e86201af79dbe5c7968b247d6b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739844"
---
# <a name="change-the-text-of-a-menu-command"></a>Změna textu příkazu nabídky
Následující kroky ukazují, jak změnit textový popisek příkazu nabídky pomocí služby. <xref:System.ComponentModel.Design.IMenuCommandService>

## <a name="changing-a-menu-command-label-with-the-imenucommandservice"></a>Změna popisku příkazu nabídky pomocí služby IMenuCommandService

1. Vytvořte projekt VSIX s názvem `MenuText` příkazu nabídky s názvem **ChangeMenuText**. Další informace naleznete [v tématu Vytvoření rozšíření pomocí příkazu nabídky](../extensibility/creating-an-extension-with-a-menu-command.md).

2. V souboru *.vsct* `TextChanges` přidejte příznak do příkazu nabídky, jak je znázorněno v následujícím příkladu.

    ```xml
    <Button guid="guidChangeMenuTextPackageCmdSet" id="ChangeMenuTextId" priority="0x0100" type="Button">
        <Parent guid="guidChangeMenuTextPackageCmdSet" id="MyMenuGroup" />
        <Icon guid="guidImages" id="bmpPic1" />
        <CommandFlag>TextChanges</CommandFlag>
        <Strings>
            <ButtonText>Invoke ChangeMenuText</ButtonText>
        </Strings>
    </Button>
    ```

3. V *souboru ChangeMenuText.cs* vytvořte obslužnou rutinu události, která bude volána před zobrazením příkazu nabídky.

    ```csharp
    private void OnBeforeQueryStatus(object sender, EventArgs e)
    {
        var myCommand = sender as OleMenuCommand;
        if (null != myCommand)
        {
            myCommand.Text = "New Text";
        }
    }
    ```

    Můžete také aktualizovat stav příkazu nabídky v této <xref:System.ComponentModel.Design.MenuCommand.Visible%2A> <xref:System.ComponentModel.Design.MenuCommand.Checked%2A>metodě <xref:System.ComponentModel.Design.MenuCommand.Enabled%2A> změnou <xref:Microsoft.VisualStudio.Shell.OleMenuCommand> vlastností , a objektu.

4. V konstruktoru ChangeMenuText nahraďte původní inicializaci příkazu a kód umístění kódem, který vytvoří <xref:Microsoft.VisualStudio.Shell.OleMenuCommand> (spíše než `MenuCommand`a ), který představuje příkaz nabídky, přidá obslužnou rutinu <xref:Microsoft.VisualStudio.Shell.OleMenuCommand.BeforeQueryStatus> události a dá příkaz nabídky do služby příkazu nabídky.

    Zde je to, co by mělo vypadat:

    ```csharp
    private ChangeMenuText(Package package)
    {
        if (package == null)
        {
            throw new ArgumentNullException(nameof(package));
        }

        this.package = package;

        OleMenuCommandService commandService = this.ServiceProvider.GetService(typeof(IMenuCommandService)) as OleMenuCommandService;
        if (commandService != null)
        {
            CommandID menuCommandID = new CommandID(MenuGroup, CommandId);
            EventHandler eventHandler = this.ShowMessageBox;
            OleMenuCommand menuItem = new OleMenuCommand(ShowMessageBox, menuCommandID);
            menuItem.BeforeQueryStatus +=
                new EventHandler(OnBeforeQueryStatus);
            commandService.AddCommand(menuItem);
        }
    }
    ```

5. Sestavení projektu a začít ladění. Zobrazí se experimentální instance sady Visual Studio.

6. V nabídce **Tools** by se měl zobrazit příkaz s názvem **Invoke ChangeMenuText**.

7. Klepněte na příkaz. Měli byste vidět okno se zprávou oznamující, že **MenuItemCallback** byla volána. Když zavřete okno se zprávou, měli byste vidět, že název příkazu v nabídce Nástroje je nyní **Nový text**.
