---
title: Zápis do úložiště uživatelských nastavení | Dokumenty společnosti Microsoft
ms.date: 05/23/2019
ms.topic: conceptual
ms.assetid: efd27f00-7fe5-45f8-9b97-371af732be97
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 2bed721cc084042c3ebe57639af28b7e9f13d206
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80740359"
---
# <a name="writing-to-the-user-settings-store"></a>Zápis do úložiště uživatelských nastavení
Uživatelská nastavení jsou zapisovatelná nastavení, jako jsou nastavení v dialogovém **okně Nástroje / Možnosti,** okna vlastností a některá další dialogová okna. Rozšíření sady Visual Studio je mohou používat k ukládání malých objemů dat. Tento návod ukazuje, jak přidat poznámkový blok do sady Visual Studio jako externí nástroj čtením a zápisem do úložiště uživatelských nastavení.

## <a name="writing-to-the-user-settings-store"></a>Zápis do úložiště uživatelských nastavení

1. Vytvořte projekt VSIX s názvem UserSettingsStoreExtension a přidejte vlastní příkaz s názvem UserSettingsStoreCommand. Další informace o vytvoření vlastního příkazu naleznete v [tématu Vytvoření rozšíření pomocí příkazu nabídky](../extensibility/creating-an-extension-with-a-menu-command.md)

2. V UserSettingsStoreCommand.cs přidejte následující pomocí direktiv:

    ```csharp
    using System.Collections.Generic;
    using Microsoft.VisualStudio.Settings;
    using Microsoft.VisualStudio.Shell.Settings;
    ```

3. V MenuItemCallback, odstraňte tělo metody a získejte úložiště uživatelských nastavení, a to následovně:

    ```csharp
    private void MenuItemCallback(object sender, EventArgs e)
    {
        SettingsManager settingsManager = new ShellSettingsManager(ServiceProvider);
        WritableSettingsStore userSettingsStore = settingsManager.GetWritableSettingsStore(SettingsScope.UserSettings);
    }
    ```

4. Nyní zjistěte, zda je poznámkový blok již nastaven jako externí nástroj. Chcete-li zjistit, zda je nastavení ToolCmd "Poznámkový blok", je třeba iterate přes všechny externí nástroje, abyste zjistili, zda je nastavení ToolCmd "Poznámkový blok", a to následovně:

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

5. Pokud poznámkový blok nebyl nastaven jako externí nástroj, nastavte jej takto:

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

6. Otestujte kód. Nezapomeňte, že přidává poznámkový blok jako externí nástroj, takže je nutné vrátit zpět registr před spuštěním podruhé.

7. Sestavte kód a začněte ladit.

8. V nabídce **Nástroje** klepněte na tlačítko **Vyvolat příkaz UserSettingsStoreCommand**. Tím přidáte poznámkový blok do nabídky **Nástroje.**

9. Nyní byste měli vidět Poznámkový blok v nabídce Nástroje / Možnosti a kliknutím na **Poznámkový blok** byste měli vyvolat instanci poznámkového bloku.
