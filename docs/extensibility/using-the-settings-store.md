---
title: Pomocí nastavení Store | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- Settings Store, using
ms.assetid: 447ec08a-eca5-40b8-89b0-f98fdf3d39a4
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 72bfc23f585506d86a485d325611c9281f49a51d
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49949211"
---
# <a name="using-the-settings-store"></a>Použití úložiště nastavení
Existují dva typy nastavení úložišť:  
  
- Nastavení konfigurace, které je určené jen pro čtení nastavení sady Visual Studio a VSPackage. Visual Studio slučuje nastavení ze všech vygenerovaných souborů známých .pkgdef do tohoto úložiště.  
  
- Uživatelská nastavení, která jsou zapisovatelné nastavení, například ty, které se zobrazí na stránkách **možnosti** dialogové okno stránky vlastností a některých dalších dialogových oknech. Rozšíření sady Visual Studio může použít pro malá množství dat místního úložiště.  
  
  Tento návod ukazuje, jak přečíst data z úložiště nastavení konfigurace. Zobrazit [zápisu do Store nastavení uživatele](../extensibility/writing-to-the-user-settings-store.md) vysvětlení toho, jak zapsat do úložiště uživatelských nastavení.  
  
## <a name="creating-the-example-project"></a>Vytvořit příklad projektu  
 Tato část ukazuje, jak vytvořit jednoduché rozšíření projektu pomocí příkazu nabídky ukázku.  
  
1. Každé rozšíření sady Visual Studio spustí nasazení projektu VSIX, který bude obsahovat rozšíření prostředků. Vytvoření [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] VSIX projekt s názvem `SettingsStoreExtension`. Můžete najít šablonu projektu VSIX v **nový projekt** dialogového okna v části **Visual C# / rozšíření**.  
  
2. Nyní přidejte vlastní příkaz šablonu položky s názvem **SettingsStoreCommand**. V **přidat novou položku** dialogové okno, přejděte na **Visual C# / rozšíření** a vyberte **vlastního příkazu**. V **název** pole v dolní části okna, změňte název souboru příkazu **SettingsStoreCommand.cs**. Další informace o tom, jak vytvořit vlastní příkaz najdete v tématu [vytváření rozšíření pomocí příkazu nabídky](../extensibility/creating-an-extension-with-a-menu-command.md)  
  
## <a name="using-the-configuration-settings-store"></a>Pomocí Store nastavení konfigurace  
 Tato část ukazuje, jak detekovat a zobrazit nastavení konfigurace.  
  
1. V souboru SettingsStorageCommand.cs, přidejte následující příkazy using:  
  
   ```  
   using System.Collections.Generic;  
   using Microsoft.VisualStudio.Settings;  
   using Microsoft.VisualStudio.Shell.Settings;  
   using System.Windows.Forms;  
   ```  
  
2. V `MenuItemCallback`odeberte tělo metody a přidejte tyto řádky získat nastavení úložiště konfigurace:  
  
   ```  
   SettingsManager settingsManager = new ShellSettingsManager(ServiceProvider);  
   SettingsStore configurationSettingsStore = settingsManager.GetReadOnlySettingsStore(SettingsScope.Configuration);  
   ```  
  
    <xref:Microsoft.VisualStudio.Shell.Settings.ShellSettingsManager> Je spravované pomocná třída nad <xref:Microsoft.VisualStudio.Shell.Interop.IVsSettingsManager> služby.  
  
3. Teď zjistěte, zda jsou nainstalované nástroje Windows Phone. Kód by měl vypadat takto:  
  
   ```  
   private void MenuItemCallback(object sender, EventArgs e)  
   {  
       SettingsManager settingsManager = new ShellSettingsManager(ServiceProvider);  
       SettingsStore configurationSettingsStore = settingsManager.GetReadOnlySettingsStore(SettingsScope.Configuration);  
       bool arePhoneToolsInstalled = configurationSettingsStore.CollectionExists(@"InstalledProducts\Microsoft Windows Phone Developer Tools");  
       string message = "Microsoft Windows Phone Developer Tools: " + arePhoneToolsInstalled;  
       MessageBox.Show(message);  
   }  
   ```  
  
4. Testování kódu. Sestavte projekt a spusťte ladění.  
  
5. V experimentální instanci na **nástroje** nabídky, klikněte na tlačítko **vyvolat SettingsStoreCommand**.  
  
    Měla by se zobrazit zpráva s oznámením **vývojovými nástroji společnosti Microsoft Windows Phone:** následovaný **True** nebo **False**.  
  
   Visual Studio udržuje úložiště nastavení v registru systému.  
  
#### <a name="to-use-a-registry-editor-to-verify-configuration-settings"></a>Pomocí Editoru registru ověřte nastavení konfigurace  
  
1.  Otevřete Regedit.exe.  
  
2.  Přejděte do HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\14.0Exp_Config\InstalledProducts\\.  
  
    > [!NOTE]
    >  Ujistěte se, že máte před sebou klíč, který obsahuje \14.0Exp_Config\ a ne \14.0_Config\\. Když spustíte experimentální instanci sady Visual Studio, nastavení konfigurace jsou v podregistru "14.0Exp_Config".  
  
3.  Rozbalte uzel \Installed Products\. Pokud má zpráva v předchozích krocích **nástroje Microsoft Windows Phone Developer nainstalovaná: True**, \Installed Products\ by mělo obsahovat uzel Microsoft Windows Phone Developer Tools. Pokud má zpráva **nástroje Microsoft Windows Phone Developer nainstalovaná: False**, pak \Installed Products\ by neměla obsahovat uzel Microsoft Windows Phone Developer Tools.