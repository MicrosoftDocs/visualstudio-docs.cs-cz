---
title: Změna vzhledu příkazu | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- commands, changing appearance
- menu commands, changing appearance
- menus, changing command appearance
ms.assetid: da2474fa-f92d-4e9e-b8bf-67c61bf249c2
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 61ba39bc8a312fb06499bed7ca94e33dc5e7153e
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49825983"
---
# <a name="change-the-appearance-of-a-command"></a>Změna vzhledu příkazu
Změnou vzhledu příkazu můžete poskytnou zpětnou vazbu uživatelů. Například můžete příkazu, který bude vypadat jinak, pokud není k dispozici. Můžete provést příkazy k dispozici nebo není k dispozici, skrýt nebo zobrazit, nebo zaškrtněte nebo zrušte jejich zaškrtnutí v nabídce.  
  
 Změna vzhledu příkazu, proveďte jednu z těchto akcí:  
  
- Zadejte odpovídající příznaky v definici příkaz v tabulce souboru příkazů.  
  
- Použití <xref:Microsoft.VisualStudio.Shell.OleMenuCommandService> služby.  
  
- Implementace <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> rozhraní a úpravám objektů nezpracované příkazu.  
  
  Následující kroky ukazují, jak najít a aktualizovat vzhledu příkazu pomocí Managed Package Framework (MPF).  
  
### <a name="to-change-the-appearance-of-a-menu-command"></a>Chcete-li změnit vzhled příkazu nabídky  
  
1.  Postupujte podle pokynů v [změní celý text příkazu nabídky](../extensibility/changing-the-text-of-a-menu-command.md) vytvořit položku nabídky s názvem `New Text`.  
  
2.  V *ChangeMenuText.cs* soubor, přidejte následující příkaz using:  
  
    ```csharp  
    using System.Security.Permissions;  
    ```  
  
3.  V *ChangeMenuTextPackageGuids.cs* přidejte následující řádek:  
  
    ```csharp  
    public const string guidChangeMenuTextPackageCmdSet= "00000000-0000-0000-0000-00000000";  // get the GUID from the .vsct file  
    ```  
  
4.  V *ChangeMenuText.cs* souboru, nahraďte kód v metodě ShowMessageBox následujícím kódem:  
  
    ```csharp  
    private void ShowMessageBox(object sender, EventArgs e)  
    {  
        var command = sender as OleMenuCommand;  
        if (command.Text == "New Text")  
            ChangeMyCommand(command.CommandID.ID, false);
    }  
    ```  
  
5.  Získat příkaz, který chcete aktualizovat z <xref:Microsoft.VisualStudio.Shell.OleMenuCommandService> objekt a potom nastavte příslušné vlastnosti v objektu command. Například následující metoda provede zadaný příkaz z příkazu VSPackage nastavení k dispozici nebo není k dispozici. Následující kód vytvoří položka nabídky s názvem `New Text` není k dispozici, až se kliklo.  
  
    ```csharp  
    public bool ChangeMyCommand(int cmdID, bool enableCmd)  
    {  
        bool cmdUpdated = false;  
        var mcs = this.ServiceProvider.GetService(typeof(IMenuCommandService))  
            as OleMenuCommandService;  
        var newCmdID = new CommandID(new Guid(ChangeMenuTextPackageGuids.guidChangeMenuTextPackageCmdSet), cmdID);  
        MenuCommand mc = mcs.FindCommand(newCmdID);  
        if (mc != null)  
        {  
            mc.Enabled = enableCmd;  
            cmdUpdated = true;  
        }  
        return cmdUpdated;
    }  
    ```  
  
6.  Sestavte projekt a spusťte ladění. Experimentální instanci sady Visual Studio by se zobrazit.  
  
7.  Na **nástroje** nabídky, klikněte na tlačítko **vyvolat ChangeMenuText** příkazu. V tomto okamžiku je název příkazu **vyvolat ChangeMenuText**, takže nemá volat obslužná rutina příkazu **ChangeMyCommand()**.  
  
8.  Na **nástroje** nabídky, měli byste vidět **nový Text**. Klikněte na tlačítko **nový Text**. Příkaz by měl nyní být zobrazena šedě.  
  
## <a name="see-also"></a>Viz také:  
 [Příkazy, nabídky a panely nástrojů](../extensibility/internals/commands-menus-and-toolbars.md)   
 [Jak balíčky VSPackages přidávají prvky uživatelského rozhraní](../extensibility/internals/how-vspackages-add-user-interface-elements.md)   
 [Rozšiřování nabídek a příkazů](../extensibility/extending-menus-and-commands.md)   
 [Visual Studio tabulky příkazů (. Soubory Vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
