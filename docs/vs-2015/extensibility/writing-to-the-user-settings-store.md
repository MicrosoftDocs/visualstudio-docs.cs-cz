---
title: Zápis do úložiště uživatelských nastavení | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
ms.assetid: efd27f00-7fe5-45f8-9b97-371af732be97
caps.latest.revision: 4
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 764d9b81297c6bbefd1f5fdf7c77e4d514bb5045
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "64821295"
---
# <a name="writing-to-the-user-settings-store"></a>Zápis do úložiště uživatelských nastavení
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Uživatelská nastavení jsou zapisovatelná nastavení, podobně jako v dialogovém okně **Nástroje/možnosti** , vlastnosti okna a určitá další dialogová okna. Rozšíření sady Visual Studio je můžou použít k ukládání malých objemů dat. Tento návod ukazuje, jak přidat program Poznámkový blok do sady Visual Studio jako externí nástroj pomocí čtení a zápisu do úložiště uživatelských nastavení.  
  
### <a name="backing-up-your-user-settings"></a>Zálohování uživatelských nastavení  
  
1. Musíte být schopni obnovit nastavení externích nástrojů, aby bylo možné provést ladění a zopakovat postup. K tomu je nutné uložit původní nastavení, abyste je mohli obnovit podle potřeby.  
  
2. Otevřete Regedit.exe.  
  
3. Přejděte na HKEY_CURRENT_USER nástroje \Software\Microsoft\VisualStudio\14.0Exp\External \\ .  
  
    > [!NOTE]
    > Ujistěte se, že se díváte na klíč obsahující \14.0Exp\, ne \ 14,0 \\ . Při spuštění experimentální instance sady Visual Studio se uživatelská nastavení nacházejí v podregistru "14.0 EXP".  
  
4. Klikněte pravým tlačítkem na podklíč \External Tools \ a pak klikněte na **exportovat**. Ujistěte se, že je vybraná **Vybraná větev** .  
  
5. Uložte výsledný soubor. reg pro externí nástroje.  
  
6. Později, pokud chcete resetovat nastavení externích nástrojů, vyberte klíč registru HKEY_CURRENT_USER \Software\Microsoft\VisualStudio\14.0Exp\External Tools \ a v místní nabídce klikněte na **Odstranit** .  
  
7. Když se zobrazí dialogové okno **Potvrdit odstranění klíče** , klikněte na **Ano**.  
  
8. Klikněte pravým tlačítkem na soubor. reg, který jste předtím uložili, klikněte na **otevřít v programu**a pak klikněte na **Editor registru**.  
  
## <a name="writing-to-the-user-settings-store"></a>Zápis do úložiště uživatelských nastavení  
  
1. Vytvořte projekt VSIX s názvem UserSettingsStoreExtension a pak přidejte vlastní příkaz s názvem UserSettingsStoreCommand. Další informace o tom, jak vytvořit vlastní příkaz, najdete v tématu [Vytvoření rozšíření pomocí příkazu nabídky](../extensibility/creating-an-extension-with-a-menu-command.md) .  
  
2. V UserSettingsStoreCommand.cs přidejte následující příkazy using:  
  
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
