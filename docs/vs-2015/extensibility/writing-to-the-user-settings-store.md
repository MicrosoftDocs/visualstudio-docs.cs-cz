---
title: Zápis do Store nastavení uživatele | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: efd27f00-7fe5-45f8-9b97-371af732be97
caps.latest.revision: 4
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 70522d8a291cad559a042dab7f4eeb3c3c4684ac
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51779720"
---
# <a name="writing-to-the-user-settings-store"></a>Zápis do úložiště uživatelských nastavení
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Uživatelská nastavení jsou zapisovatelné nastavení, jako je v **Nástroje / možnosti** dialogového okna, okna vlastností a některých dalších dialogových oknech. Rozšíření sady Visual Studio může použít k ukládání malé množství dat. Tento návod ukazuje, jak přidat program Poznámkový blok se sadou Visual Studio jako externího nástroje ve čtení a zápisu do úložiště uživatelských nastavení.  
  
### <a name="backing-up-your-user-settings"></a>Zálohování nastavení uživatele  
  
1.  Musíte být schopni obnovit nastavení externí nástroje, aby mohli ladit a opakujte tento postup. Chcete-li to provést, musíte uložit původní nastavení tak, aby je mohli obnovit podle potřeby.  
  
2.  Otevřete Regedit.exe.  
  
3.  Přejděte na nástroje HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\14.0Exp\External\\.  
  
    > [!NOTE]
    >  Ujistěte se, že máte před sebou klíč, který obsahuje \14.0Exp\ a ne \14.0\\. Když spustíte experimentální instanci sady Visual Studio, uživatelská nastavení jsou v podregistru "14.0Exp".  
  
4.  Klikněte pravým tlačítkem na podklíč \External Tools\ a potom klikněte na tlačítko **exportovat**. Ujistěte se, že **Vybraná větev** zaškrtnuto.  
  
5.  Výsledný soubor externí Tools.reg uložte.  
  
6.  Později, pokud chcete obnovit nastavení externí nástroje, vyberte klíč registru HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\14.0Exp\External Tools\ a klikněte na tlačítko **odstranit** v místní nabídce.  
  
7.  Když **Potvrdit odstranění klíče** dialogové okno se zobrazí, klikněte na tlačítko **Ano**.  
  
8.  Klikněte pravým tlačítkem na externí Tools.reg soubor, který jste předtím uložili, klikněte na tlačítko **otevřít v programu**a potom klikněte na tlačítko **Editor registru**.  
  
## <a name="writing-to-the-user-settings-store"></a>Zápis do úložiště uživatelských nastavení  
  
1.  Vytvořte projekt VSIX s názvem UserSettingsStoreExtension a pak přidejte vlastní příkaz s názvem UserSettingsStoreCommand. Další informace o tom, jak vytvořit vlastní příkaz najdete v tématu [vytváření rozšíření pomocí příkazu nabídky](../extensibility/creating-an-extension-with-a-menu-command.md)  
  
2.  V souboru UserSettingsStoreCommand.cs, přidejte následující příkazy using:  
  
    ```csharp  
    using System.Collections.Generic;  
    using Microsoft.VisualStudio.Settings;  
    using Microsoft.VisualStudio.Shell.Settings;  
    ```  
  
3.  V MenuItemCallback odstraňte tělo metody a získat uživatelské nastavení uložená, následujícím způsobem:  
  
    ```csharp  
    private void MenuItemCallback(object sender, EventArgs e)  
    {  
        SettingsManager settingsManager = new ShellSettingsManager(ServiceProvider);  
        WritableSettingsStore userSettingsStore = settingsManager.GetWritableSettingsStore(SettingsScope.UserSettings);  
    }  
    ```  
  
4.  Teď zjistěte, zda poznámkového bloku již nastaven jako externího nástroje. Je nutné iterovat všechny externí nástroje pro zjištění nastavení ToolCmd "Poznámkový blok", následujícím způsobem:  
  
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
  
5.  Pokud program Poznámkový blok není nastavený jako externího nástroje, nastavte ho následujícím způsobem:  
  
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
  
6.  Testování kódu. Mějte na paměti, že ho Poznámkový blok přidá jako externího nástroje, takže se musí vrátit registru před jejím spuštěním podruhé.  
  
7.  Sestavte kód a spusťte ladění.  
  
8.  Na **nástroje** nabídky, klikněte na tlačítko **vyvolat UserSettingsStoreCommand**. Tato možnost přidá Poznámkový blok a **nástroje** nabídky.  
  
9. Teď byste měli vidět Poznámkový blok v nabídce Nástroje / možnosti nabídky a kliknutím na **Poznámkový blok** by měl vyvolat instance poznámkového bloku.

