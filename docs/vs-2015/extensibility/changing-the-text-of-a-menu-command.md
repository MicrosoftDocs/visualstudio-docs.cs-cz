---
title: Změna textu příkazu nabídky | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- menus, changing text
- text, menus
- commands, changing text
ms.assetid: 5cb676a0-c6e2-47e5-bd2b-133dc8842e46
caps.latest.revision: 26
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: d8fd3fc01a5dd3e10e633b876b719695d6b26c18
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "68184495"
---
# <a name="changing-the-text-of-a-menu-command"></a>Změna textu příkazu nabídky
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Následující kroky ukazují, jak změnit textový popisek příkazu nabídky pomocí <xref:System.ComponentModel.Design.IMenuCommandService> služby.  
  
## <a name="changing-a-menu-command-label-with-the-imenucommandservice"></a>Změna popisku příkazu nabídky pomocí IMenuCommandService  
  
1. Vytvořte projekt VSIX s názvem `MenuText` s příkazem nabídky s názvem **ChangeMenuText**. Další informace najdete v tématu [Vytvoření rozšíření pomocí příkazu nabídky](../extensibility/creating-an-extension-with-a-menu-command.md).  
  
2. V souboru. vstc přidejte `TextChanges` příznak do příkazu nabídky, jak je znázorněno v následujícím příkladu.  
  
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
  
3. V souboru ChangeMenuText.cs vytvořte obslužnou rutinu události, která bude volána před zobrazením příkazu nabídky.  
  
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
  
5. Sestavte projekt a spusťte ladění. Zobrazí se experimentální instance aplikace Visual Studio.  
  
6. V nabídce **nástroje** byste měli vidět příkaz s názvem **Invoke ChangeMenuText**.  
  
7. Klikněte na příkaz. Mělo by se zobrazit okno se zprávou oznamující, že byl zavolán tento MenuItemCallback. Po zavření okna se zprávou byste měli vidět, že název příkazu v nabídce nástroje je teď **nový text**.
