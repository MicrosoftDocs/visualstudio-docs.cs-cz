---
title: Změna vzhledu příkazu | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- commands, changing appearance
- menu commands, changing appearance
- menus, changing command appearance
ms.assetid: da2474fa-f92d-4e9e-b8bf-67c61bf249c2
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 653f516dda89f4895b8d19d77f7f49bf9c6aa45b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739862"
---
# <a name="change-the-appearance-of-a-command"></a>Změna vzhledu příkazu
Zpětnou vazbu můžete uživateli poskytnout změnou vzhledu příkazu. Můžete například chtít, aby příkaz vypadal jinak, pokud není k dispozici. Příkazy můžete zpřístupnit nebo zpřístupnit, skrýt nebo zobrazit nebo je v nabídce zkontrolovat nebo zrušit jejich zaškrtnutí.

Chcete-li změnit vzhled příkazu, proveďte jednu z těchto akcí:

- Zadejte příslušné příznaky v definici příkazu v souboru tabulky příkazů.

- Použijte <xref:Microsoft.VisualStudio.Shell.OleMenuCommandService> službu.

- Implementujte <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> rozhraní a upravte nezpracovaná příkazová objekty.

  Následující kroky ukazují, jak najít a aktualizovat vzhled příkazu pomocí rozhraní MPF (Managed Package Framework).

### <a name="to-change-the-appearance-of-a-menu-command"></a>Změna vzhledu příkazu nabídky

1. Podle pokynů v části [Změna textu příkazu nabídky](../extensibility/changing-the-text-of-a-menu-command.md) `New Text`vytvořte položku nabídky s názvem .

2. Do *souboru ChangeMenuText.cs* přidejte následující příkaz using:

    ```csharp
    using System.Security.Permissions;
    ```

3. Do *souboru ChangeMenuTextPackageGuids.cs* přidejte následující řádek:

    ```csharp
    public const string guidChangeMenuTextPackageCmdSet= "00000000-0000-0000-0000-00000000";  // get the GUID from the .vsct file
    ```

4. V *souboru ChangeMenuText.cs* nahraďte kód v metodě ShowMessageBox následujícím:

    ```csharp
    private void ShowMessageBox(object sender, EventArgs e)
    {
        var command = sender as OleMenuCommand;
        if (command.Text == "New Text")
            ChangeMyCommand(command.CommandID.ID, false);
    }
    ```

5. Získejte příkaz, který chcete <xref:Microsoft.VisualStudio.Shell.OleMenuCommandService> aktualizovat z objektu, a nastavte příslušné vlastnosti objektu příkazu. Například následující metoda zpřístupňuje zadaný příkaz ze sady příkazů VSPackage nebo není k dispozici. Následující kód znepřístupní `New Text` položku nabídky po klepnutí na ni.

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

6. Sestavení projektu a začít ladění. Experimentální instance sady Visual Studio by se měla zobrazit.

7. V nabídce **Nástroje** klepněte na příkaz **Invoke ChangeMenuText** . V tomto okamžiku je název příkazu **Invoke ChangeMenuText**, takže obslužná rutina příkazu nevolá **ChangeMyCommand()**.

8. V nabídce **Nástroje** byste nyní měli vidět **Nový text**. Klepněte na **položku Nový text**. Příkaz by nyní měl být zašedlý.

## <a name="see-also"></a>Viz také
- [Příkazy, nabídky a panely nástrojů](../extensibility/internals/commands-menus-and-toolbars.md)
- [Jak VSPackages přidat prvky uživatelského rozhraní](../extensibility/internals/how-vspackages-add-user-interface-elements.md)
- [Rozšíření nabídek a příkazů](../extensibility/extending-menus-and-commands.md)
- [Visual Studio příkaz tabulky (. Vsct) Soubory](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
