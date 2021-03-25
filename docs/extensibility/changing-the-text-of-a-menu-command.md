---
title: Změna textu příkazu nabídky | Microsoft Docs
description: Podívejte se, jak změnit textový popisek příkazu nabídky pomocí služby IMenuCommandService, a to tak, že zkontrolujete tento příklad kódu.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- menus, changing text
- text, menus
- commands, changing text
ms.assetid: 5cb676a0-c6e2-47e5-bd2b-133dc8842e46
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 47389352e0491c20b7eb6409c36091179bf967d1
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/25/2021
ms.locfileid: "105068060"
---
# <a name="change-the-text-of-a-menu-command"></a>Změna textu příkazu nabídky
Následující kroky ukazují, jak změnit textový popisek příkazu nabídky pomocí <xref:System.ComponentModel.Design.IMenuCommandService> služby.

## <a name="changing-a-menu-command-label-with-the-imenucommandservice"></a>Změna popisku příkazu nabídky pomocí IMenuCommandService

1. Vytvořte projekt VSIX s názvem `MenuText` s příkazem nabídky s názvem **ChangeMenuText**. Další informace najdete v tématu [Vytvoření rozšíření pomocí příkazu nabídky](../extensibility/creating-an-extension-with-a-menu-command.md).

2. V souboru *. vsct* přidejte `TextChanges` příznak do příkazu nabídky, jak je znázorněno v následujícím příkladu.

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

3. V souboru *ChangeMenuText. cs* vytvořte obslužnou rutinu události, která bude volána před zobrazením příkazu nabídky.

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

    Můžete také aktualizovat stav příkazu nabídky v této metodě změnou <xref:System.ComponentModel.Design.MenuCommand.Visible%2A> <xref:System.ComponentModel.Design.MenuCommand.Checked%2A> vlastností, a <xref:System.ComponentModel.Design.MenuCommand.Enabled%2A> v <xref:Microsoft.VisualStudio.Shell.OleMenuCommand> objektu.

4. V konstruktoru ChangeMenuText nahraďte původní inicializaci příkazu a kód umístění kódem, který vytvoří <xref:Microsoft.VisualStudio.Shell.OleMenuCommand> (spíše než a `MenuCommand` ), který představuje příkaz nabídky, přidá <xref:Microsoft.VisualStudio.Shell.OleMenuCommand.BeforeQueryStatus> obslužnou rutinu události a poskytne příkaz nabídky službě příkazu nabídky.

    Tady je to, co by mělo vypadat takto:

    ```csharp
    private ChangeMenuText(AsyncPackage package, OleMenuCommandService commandService)
    {
        this.package = package ?? throw new ArgumentNullException(nameof(package));
        commandService = commandService ?? throw new ArgumentNullException(nameof(commandService));
        
        var menuCommandID = new CommandID(CommandSet, CommandId);
        var menuItem = new OleMenuCommand(this.Excute, menuCommandID);
        menuItem.BeforeQueryStatus += new EventHandler(OnBeforeQueryStatus);
        commandService.AddCommand(menuItem);
    }
    ```

5. Sestavte projekt a spusťte ladění. Zobrazí se experimentální instance aplikace Visual Studio.

6. V nabídce **nástroje** byste měli vidět příkaz s názvem **Invoke ChangeMenuText**.

7. Klikněte na příkaz. Mělo by se zobrazit okno se zprávou oznamující, že byl zavolán tento **MenuItemCallback** . Po zavření okna se zprávou byste měli vidět, že název příkazu v nabídce nástroje je teď **nový text**.
