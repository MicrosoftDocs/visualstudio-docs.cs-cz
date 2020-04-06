---
title: Použití úložiště nastavení | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Settings Store, using
ms.assetid: 447ec08a-eca5-40b8-89b0-f98fdf3d39a4
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: b3bbc09586f883e067e32f525a0331c1a9e253f5
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80698519"
---
# <a name="using-the-settings-store"></a>Použití úložiště nastavení
Existují dva druhy úložišť nastavení:

- Nastavení konfigurace, která jsou jen pro čtení Visual Studio a VSPackage nastavení. Visual Studio sloučí nastavení ze všech známých souborů .pkgdef do tohoto úložiště.

- Uživatelská nastavení, která jsou zapisovatelná, například ta, která jsou zobrazena na stránkách dialogového okna **Možnosti,** stránkách vlastností a některých dalších dialogových oknech. Rozšíření sady Visual Studio je mohou používat pro místní úložiště malých objemů dat.

  Tento návod ukazuje, jak číst data z úložiště nastavení konfigurace. Vysvětlení, jak psát do úložiště uživatelských nastavení, naleznete v tématu [Zápis do úložiště uživatelských](../extensibility/writing-to-the-user-settings-store.md) nastavení.

## <a name="creating-the-example-project"></a>Vytvoření ukázkového projektu
 Tato část ukazuje, jak vytvořit jednoduchý projekt rozšíření s příkazem nabídky pro demonstraci.

1. Každé rozšíření sady Visual Studio začíná projektem nasazení VSIX, který bude obsahovat prostředky rozšíření. Vytvořte [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] projekt VSIX s názvem `SettingsStoreExtension`. Šablonu projektu VSIX najdete v dialogovém okně **Nový projekt** v části **Vizuální C# / Rozšiřitelnost**.

2. Nyní přidejte vlastní šablonu položky příkazu s názvem **SettingsStoreCommand**. V dialogovém okně **Přidat novou položku** přejděte na **Visual C# / Rozšiřitelnost** a vyberte **vlastní příkaz**. V poli **Název** v dolní části okna změňte název příkazového souboru na **SettingsStoreCommand.cs**. Další informace o vytvoření vlastního příkazu naleznete v [tématu Vytvoření rozšíření pomocí příkazu nabídky](../extensibility/creating-an-extension-with-a-menu-command.md)

## <a name="using-the-configuration-settings-store"></a>Použití úložiště nastavení konfigurace
 Tato část ukazuje, jak rozpoznat a zobrazit nastavení konfigurace.

1. Do souboru SettingsStorageCommand.cs přidejte následující příkazy pomocí direktiv:

   ```
   using System.Collections.Generic;
   using Microsoft.VisualStudio.Settings;
   using Microsoft.VisualStudio.Shell.Settings;
   using System.Windows.Forms;
   ```

2. V `MenuItemCallback`, odeberte tělo metody a přidejte tyto řádky získat úložiště nastavení konfigurace:

   ```
   SettingsManager settingsManager = new ShellSettingsManager(ServiceProvider);
   SettingsStore configurationSettingsStore = settingsManager.GetReadOnlySettingsStore(SettingsScope.Configuration);
   ```

    Je <xref:Microsoft.VisualStudio.Shell.Settings.ShellSettingsManager> spravované pomocné třídy <xref:Microsoft.VisualStudio.Shell.Interop.IVsSettingsManager> přes službu.

3. Teď zjistěte, jestli jsou nainstalované nástroje Windows Phone. Kód by měl vypadat takto:

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

4. Otestujte kód. Sestavení projektu a začít ladění.

5. V experimentální instanci klepněte v nabídce **Nástroje** na **příkaz Invoke SettingsStoreCommand**.

    Mělo by se zobrazit okno se zprávou, že **nástroje pro vývojáře microsoft windows phone:** následované **hodnotou True** nebo **False**.

   Visual Studio udržuje úložiště nastavení v systémovém registru.

#### <a name="to-use-a-registry-editor-to-verify-configuration-settings"></a>Použití editoru registru k ověření nastavení konfigurace

1. Otevřete soubor Regedit.exe.

2. Přejděte na HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\14.0Exp_Config\InstalledProducts\\.

    > [!NOTE]
    > Ujistěte se, že hledáte klíč, který obsahuje \14.0Exp_Config\\\a ne \14.0_Config . Při spuštění experimentální instance sady Visual Studio jsou nastavení konfigurace v podregistru registru "14.0Exp_Config".

3. Rozbalte uzel \Installed Products\. Pokud je zpráva v předchozích krocích **nainstalována nástroje pro vývojáře systému Microsoft Windows Phone: True**, měl by \Installed Products\ obsahovat uzel Nástroje pro vývojáře systému Microsoft Windows Phone. Pokud je zpráva **nainstalována nástroje pro vývojáře systému Microsoft Windows Phone: False**, neměla by \Installed Products\ obsahovat uzel Nástroje pro vývojáře systému Microsoft Windows Phone.
