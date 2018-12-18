---
title: Zápis do úložiště uživatelských nastavení | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
ms.assetid: efd27f00-7fe5-45f8-9b97-371af732be97
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 0e205fa8850bdd5ee664f66c6d6bb7bf86195bfd
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/16/2018
ms.locfileid: "31145409"
---
# <a name="writing-to-the-user-settings-store"></a>Zápis do úložiště uživatelských nastavení
Uživatelská nastavení jsou zapisovatelné nastavení, jako jsou v **Nástroje / možnosti** dialogové okno Vlastnosti windows a určitých dialogových oken. Rozšíření pro Visual Studio může použít k uložení malé množství dat. Tento návod ukazuje, jak přidat Poznámkový blok pro Visual Studio jako externího nástroje, čtení a zápis do úložiště uživatelských nastavení.  
  
### <a name="backing-up-your-user-settings"></a>Zálohování nastavení pro vaše uživatele  
  
1.  Musíte být schopni obnovit nastavení externích nástrojů, aby mohli ladění a opakujte postup. Chcete-li to provést, je nutné uložit původní nastavení tak, aby je mohli obnovit podle potřeby.  
  
2.  Otevřete Regedit.exe.  
  
3.  Přejděte do nástroje HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\14.0Exp\External\\.  
  
    > [!NOTE]
    >  Ujistěte se, že hledáte na klíč, který obsahuje \14.0Exp\ a není \14.0\\. Když spustíte experimentální instanci sady Visual Studio, jsou uživatelská nastavení v podregistru "14.0Exp".  
  
4.  Klikněte pravým tlačítkem na podklíč \External Tools\ a pak klikněte na **exportovat**. Ujistěte se, že **vybrané větve** je vybrána.  
  
5.  Uložte soubor výsledné externí Tools.reg.  
  
6.  Později, pokud chcete obnovit nastavení externích nástrojích, vyberte klíč registru HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\14.0Exp\External Tools\ a klikněte na **odstranit** v místní nabídce.  
  
7.  Když **Potvrdit odstranění klíče** se zobrazí dialogové okno, klikněte na tlačítko **Ano**.  
  
8.  Pravým tlačítkem na externí Tools.reg soubor, který jste předtím uložili, klikněte na tlačítko **Otevřít protokolem**a potom klikněte na **Editor registru**.  
  
## <a name="writing-to-the-user-settings-store"></a>Zápis do úložiště uživatelských nastavení  
  
1.  Vytvoření projektu VSIX s názvem UserSettingsStoreExtension a poté přidejte vlastní příkaz s názvem UserSettingsStoreCommand. Další informace o tom, jak vytvořit vlastní příkaz najdete v tématu [vytvoření rozšíření pomocí příkazu nabídky](../extensibility/creating-an-extension-with-a-menu-command.md)  
  
2.  V UserSettingsStoreCommand.cs, přidejte následující příkazy:  
  
    ```csharp  
    using System.Collections.Generic;  
    using Microsoft.VisualStudio.Settings;  
    using Microsoft.VisualStudio.Shell.Settings;  
    ```  
  
3.  V MenuItemCallback odstraňte text metody a získat uživatele, kterého nastavení uložit, následujícím způsobem:  
  
    ```csharp  
    private void MenuItemCallback(object sender, EventArgs e)  
    {  
        SettingsManager settingsManager = new ShellSettingsManager(ServiceProvider);  
        WritableSettingsStore userSettingsStore = settingsManager.GetWritableSettingsStore(SettingsScope.UserSettings);  
    }  
    ```  
  
4.  Nyní zjistěte, jestli Poznámkový blok je již nastavena jako externího nástroje. Je třeba k iteraci v rámci všech externí nástroje k určení, zda nastavení ToolCmd "Poznámkový blok", následujícím způsobem:  
  
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
  
5.  Pokud poznámkový blok nebyl nastaven jako externího nástroje, nastavte ho následujícím způsobem:  
  
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
  
6.  Testování kódu. Mějte na paměti, že ho Poznámkový blok přidá jako externího nástroje, takže se musí vrátit registru před spuštěním ještě jednou.  
  
7.  Sestavte kód a spusťte ladění.  
  
8.  Na **nástroje** nabídky, klikněte na tlačítko **vyvolání UserSettingsStoreCommand**. Bude přidáno Poznámkový blok k **nástroje** nabídky.  
  
9. Teď byste měli vidět Poznámkový blok v nabídce Nástroje / možnosti nabídky a kliknutím na **Poznámkový blok** by měl zprovoznit instanci programu Poznámkový blok.