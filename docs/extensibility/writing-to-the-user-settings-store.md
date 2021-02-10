---
title: Zápis do úložiště uživatelských nastavení | Microsoft Docs
description: Pomocí tohoto návodu se dozvíte, jak přidat do sady Visual Studio Poznámkový blok jako externí nástroj.
ms.custom: SEO-VS-2020
ms.date: 05/23/2019
ms.topic: how-to
ms.assetid: efd27f00-7fe5-45f8-9b97-371af732be97
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: f022023ec03ddb280424f3c47944c91e8fa696de
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99958385"
---
# <a name="writing-to-the-user-settings-store"></a>Zápis do úložiště uživatelských nastavení
Uživatelská nastavení jsou zapisovatelná nastavení, podobně jako v dialogovém okně **Nástroje/možnosti** , vlastnosti okna a určitá další dialogová okna. Rozšíření sady Visual Studio je můžou použít k ukládání malých objemů dat. Tento návod ukazuje, jak přidat program Poznámkový blok do sady Visual Studio jako externí nástroj pomocí čtení a zápisu do úložiště uživatelských nastavení.

## <a name="writing-to-the-user-settings-store"></a>Zápis do úložiště uživatelských nastavení

1. Vytvořte projekt VSIX s názvem UserSettingsStoreExtension a pak přidejte vlastní příkaz s názvem UserSettingsStoreCommand. Další informace o tom, jak vytvořit vlastní příkaz, najdete v tématu [Vytvoření rozšíření pomocí příkazu nabídky](../extensibility/creating-an-extension-with-a-menu-command.md) .

2. Do UserSettingsStoreCommand.cs přidejte následující direktivy using:

    ```csharp
    using System.Collections.Generic;
    using Microsoft.VisualStudio.Settings;
    using Microsoft.VisualStudio.Shell.Settings;
    ```

3. V MenuItemCallback odstraňte tělo metody a získejte úložiště uživatelských nastavení následujícím způsobem:

    ```csharp
    private void MenuItemCallback(object sender, EventArgs e)
    {
        SettingsManager settingsManager = new ShellSettingsManager(ServiceProvider);
        WritableSettingsStore userSettingsStore = settingsManager.GetWritableSettingsStore(SettingsScope.UserSettings);
    }
    ```

4. Nyní zjistíte, zda je Poznámkový blok již nastaven jako externí nástroj. Abyste zjistili, jestli je nastavení ToolCmd Poznámkový blok, musíte iterovat pomocí všech externích nástrojů, a to následujícím způsobem:

    ```csharp
    private void MenuItemCallback(object sender, EventArgs e)
    {
        SettingsManager settingsManager = new ShellSettingsManager(ServiceProvider);
        WritableSettingsStore userSettingsStore = settingsManager.GetWritableSettingsStore(SettingsScope.UserSettings);

        // Find out whether Notepad is already an External Tool.
        int toolCount = userSettingsStore.GetInt32("External Tools", "ToolNumKeys");
        bool hasNotepad = false;
        CompareInfo Compare = CultureInfo.InvariantCulture.CompareInfo;
        for (int i = 0; i < toolCount; i++)
        {
            if (Compare.IndexOf(userSettingsStore.GetString("External Tools", "ToolCmd" + i), "Notepad", CompareOptions.IgnoreCase) >= 0)
            {
                hasNotepad = true;
                break;
            }
        }
    }

    ```

5. Pokud nebyl program Poznámkový blok nastaven jako externí nástroj, nastavte ho následujícím způsobem:

    ```vb
    private void MenuItemCallback(object sender, EventArgs e)
    {
        SettingsManager settingsManager = new ShellSettingsManager(ServiceProvider);
        WritableSettingsStore userSettingsStore = settingsManager.GetWritableSettingsStore(SettingsScope.UserSettings);

        // Find out whether Notepad is already installed.
        int toolCount = userSettingsStore.GetInt32("External Tools", "ToolNumKeys");
        bool hasNotepad = false;
        CompareInfo Compare = CultureInfo.InvariantCulture.CompareInfo;
        for (int i = 0; i < toolCount; i++)
        {
            if (Compare.IndexOf(userSettingsStore.GetString("External Tools", "ToolCmd" + i), "Notepad", CompareOptions.IgnoreCase) >= 0)
            {
                hasNotepad = true;
                break;
            }
        }

        string message = (hasNotepad) ? "Notepad already installed" : "Installing Notepad";
         if (!hasNotepad)
        {
            userSettingsStore.SetString("External Tools", "ToolTitle" + toolCount, "&Notepad");
            userSettingsStore.SetString("External Tools", "ToolCmd" + toolCount, "C:\\Windows\\notepad.exe");
            userSettingsStore.SetString("External Tools", "ToolArg" + toolCount, "");
            userSettingsStore.SetString("External Tools", "ToolDir" + toolCount, "$(ProjectDir)");
            userSettingsStore.SetString("External Tools", "ToolSourceKey" + toolCount, "");
            userSettingsStore.SetUInt32("External Tools", "ToolOpt" + toolCount, 0x00000011);

            userSettingsStore.SetInt32("External Tools", "ToolNumKeys", toolCount + 1);
        }
    }
    ```

6. Otestujte kód. Mějte na paměti, že přidá do programu Poznámkový blok jako externí nástroj, takže před tím, než ho spustíte podruhé, je nutné registr vrátit zpátky.

7. Sestavte kód a spusťte ladění.

8. V nabídce **nástroje** klikněte na **vyvolat UserSettingsStoreCommand**. Tím se přidá Poznámkový blok do nabídky **nástroje** .

9. Nyní byste měli v nabídce Nástroje/možnosti Zobrazit Poznámkový blok a kliknout na Poznámkový **blok** , který by měl vyvolat instanci poznámkového bloku.
