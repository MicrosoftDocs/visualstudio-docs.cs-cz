---
title: Změna vzhledu příkazu | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- commands, changing appearance
- menu commands, changing appearance
- menus, changing command appearance
ms.assetid: da2474fa-f92d-4e9e-b8bf-67c61bf249c2
caps.latest.revision: 24
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 4741059410e052c571d77088b9cbe109fb651642
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "68184509"
---
# <a name="changing-the-appearance-of-a-command"></a>Změna vzhledu příkazu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Zpětnou vazbu můžete poskytnout uživateli změnou vzhledu příkazu. Například může být vhodné, aby příkaz vypadal jinak, pokud není k dispozici. Příkazy lze zpřístupnit nebo není k dispozici, skrýt nebo zobrazit, nebo je v nabídce zaškrtnout nebo zrušit jejich kontrolu.  
  
 Chcete-li změnit vzhled příkazu, proveďte jednu z následujících akcí:  
  
- Zadejte příslušné příznaky v definici příkazu v souboru tabulky příkazů.  
  
- Službu použijte <xref:Microsoft.VisualStudio.Shell.OleMenuCommandService> .  
  
- Implementujte <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> rozhraní a upravte nezpracované objekty příkazů.  
  
  Následující kroky ukazují, jak najít a aktualizovat vzhled příkazu pomocí spravovaného balíčku balíčku (MPF).  
  
### <a name="to-change-the-appearance-of-a-menu-command"></a>Změna vzhledu příkazu nabídky  
  
1. Podle pokynů v části [Změna textu příkazu nabídky](../extensibility/changing-the-text-of-a-menu-command.md) vytvořte položku nabídky s názvem `New Text` .  
  
2. Do souboru ChangeMenuText.cs přidejte následující příkaz using:  
  
    ```csharp  
    using System.Security.Permissions;  
    ```  
  
3. Do souboru ChangeMenuTextPackageGuids.cs přidejte následující řádek:  
  
    ```csharp  
    public const string guidChangeMenuTextPackageCmdSet= "00000000-0000-0000-0000-00000000";  // get the GUID from the .vsct file  
    ```  
  
4. V souboru ChangeMenuText.cs nahraďte kód v metodě ShowMessageBox následujícím způsobem:  
  
    ```csharp  
    private void ShowMessageBox(object sender, EventArgs e)  
    {  
        var command = sender as OleMenuCommand;  
        if (command.Text == "New Text")  
            ChangeMyCommand(command.CommandID.ID, false);}  
    }  
    ```  
  
5. Z objektu Získejte příkaz, který chcete aktualizovat, <xref:Microsoft.VisualStudio.Shell.OleMenuCommandService> a pak nastavte příslušné vlastnosti objektu Command. Například následující metoda provede zadaný příkaz z sady příkazů VSPackage, který je k dispozici nebo není k dispozici. Následující kód provede položku nabídky s názvem `New Text` není k dispozici po kliknutí.  
  
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
        return cmdUpdated;    }  
    }  
    ```  
  
6. Sestavte projekt a spusťte ladění. Měla by se zobrazit experimentální instance sady Visual Studio.  
  
7. V nabídce **nástroje** klikněte na příkaz **vyvolat ChangeMenuText** . V tomto okamžiku název příkazu **vyvolá ChangeMenuText**, takže obslužná rutina příkazu nevolá ChangeMyCommand ().  
  
8. V nabídce **nástroje** by se teď měl zobrazit **nový text**. Klikněte na **nový text**. Příkaz by měl být teď šedý.  
  
## <a name="see-also"></a>Viz také  
 [Příkazy, nabídky a panely nástrojů](../extensibility/internals/commands-menus-and-toolbars.md)   
 [Jak prvky VSPackage přidávají prvky uživatelského rozhraní](../extensibility/internals/how-vspackages-add-user-interface-elements.md)   
 [Rozšiřování nabídek a příkazů](../extensibility/extending-menus-and-commands.md)   
 [Soubory tabulek příkazů sady Visual Studio (.Vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
