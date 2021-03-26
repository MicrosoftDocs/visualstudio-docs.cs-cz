---
title: Změna vzhledu příkazu | Microsoft Docs
description: Naučte se, jak poskytnout zpětnou vazbu, která mění vzhled příkazu, jako je například zpřístupnění příkazů/nedostupné, skryté/zobrazené nebo zaškrtnuté nebo nezaškrtnuté.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- commands, changing appearance
- menu commands, changing appearance
- menus, changing command appearance
ms.assetid: da2474fa-f92d-4e9e-b8bf-67c61bf249c2
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 8b6911d865b253ff82ffcc6c4911e0989f109f28
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/25/2021
ms.locfileid: "105089820"
---
# <a name="change-the-appearance-of-a-command"></a>Změna vzhledu příkazu
Zpětnou vazbu můžete poskytnout uživateli změnou vzhledu příkazu. Například může být vhodné, aby příkaz vypadal jinak, pokud není k dispozici. Příkazy lze zpřístupnit nebo není k dispozici, skrýt nebo zobrazit, nebo je v nabídce zaškrtnout nebo zrušit jejich kontrolu.

Chcete-li změnit vzhled příkazu, proveďte jednu z následujících akcí:

- Zadejte příslušné příznaky v definici příkazu v souboru tabulky příkazů.

- Službu použijte <xref:Microsoft.VisualStudio.Shell.OleMenuCommandService> .

- Implementujte <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> rozhraní a upravte nezpracované objekty příkazů.

  Následující kroky ukazují, jak najít a aktualizovat vzhled příkazu pomocí spravovaného balíčku balíčku (MPF).

### <a name="to-change-the-appearance-of-a-menu-command"></a>Změna vzhledu příkazu nabídky

1. Podle pokynů v části [Změna textu příkazu nabídky](../extensibility/changing-the-text-of-a-menu-command.md) vytvořte položku nabídky s názvem `New Text` .

2. V souboru *ChangeMenuText. cs* přidejte následující příkaz using:

    ```csharp
    using System.Security.Permissions;
    ```

3. Do souboru *ChangeMenuTextPackageGuids. cs* přidejte následující řádek:

    ```csharp
    public const string guidChangeMenuTextPackageCmdSet= "00000000-0000-0000-0000-00000000";  // get the GUID from the .vsct file
    ```

4. V souboru *ChangeMenuText. cs* nahraďte kód v metodě ShowMessageBox následujícím způsobem:

    ```csharp
    private void Execute(object sender, EventArgs e)
    {
        ThreadHelper.ThrowIfNotOnUIThread();
        var command = sender as OleMenuCommand;
        if (command.Text == "New Text")
            ChangeMyCommand(command.CommandID.ID, false);
    }
    ```

5. Z objektu Získejte příkaz, který chcete aktualizovat, <xref:Microsoft.VisualStudio.Shell.OleMenuCommandService> a pak nastavte příslušné vlastnosti objektu Command. Například následující metoda provede zadaný příkaz z sady příkazů VSPackage, který je k dispozici nebo není k dispozici. Následující kód provede položku nabídky s názvem `New Text` není k dispozici po kliknutí.

    ```csharp
    public bool ChangeMyCommand(int cmdID, bool enableCmd)
    {
        bool cmdUpdated = false;
        var mcs = this.package.GetService<IMenuCommandService, OleMenuCommandService>();
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

6. Sestavte projekt a spusťte ladění. Měla by se zobrazit experimentální instance sady Visual Studio.

7. V nabídce **nástroje** klikněte na příkaz **vyvolat ChangeMenuText** . V tomto okamžiku název příkazu **vyvolá ChangeMenuText**, takže obslužná rutina příkazu nevolá **ChangeMyCommand ()**.

8. V nabídce **nástroje** by se teď měl zobrazit **nový text**. Klikněte na **nový text**. Příkaz by měl být teď šedý.

## <a name="see-also"></a>Viz také
- [Příkazy, nabídky a panely nástrojů](../extensibility/internals/commands-menus-and-toolbars.md)
- [Jak prvky VSPackage přidávají prvky uživatelského rozhraní](../extensibility/internals/how-vspackages-add-user-interface-elements.md)
- [Rozšiřování nabídek a příkazů](../extensibility/extending-menus-and-commands.md)
- [Příkazová tabulka sady Visual Studio (. Soubory vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
