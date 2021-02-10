---
title: Použití úložiště nastavení | Microsoft Docs
description: Naučte se číst data z úložiště nastavení konfigurace, která jsou jenom pro čtení a nastavení sady Visual Studio a VSPackage.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Settings Store, using
ms.assetid: 447ec08a-eca5-40b8-89b0-f98fdf3d39a4
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 752a912fd9a565e4b3e8dcb5c4c142e8f37dffc5
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99934035"
---
# <a name="using-the-settings-store"></a>Použití úložiště nastavení
Existují dva druhy úložišť nastavení:

- Nastavení konfigurace, která jsou jen pro čtení a nastavení sady Visual Studio a VSPackage. Visual Studio sloučí nastavení ze všech známých souborů. pkgdef do tohoto úložiště.

- Uživatelská nastavení, která jsou zapisovatelná nastavení, jako jsou například ta, která jsou zobrazena na stránkách v dialogovém okně **Možnosti** , stránky vlastností a určitá další dialogová okna. Rozšíření sady Visual Studio je můžou používat pro místní úložiště s malými objemy dat.

  Tento návod ukazuje, jak číst data z úložiště nastavení konfigurace. Vysvětlení, jak zapisovat do úložiště uživatelských nastavení, najdete v tématu [zápis do úložiště uživatelských nastavení](../extensibility/writing-to-the-user-settings-store.md) .

## <a name="creating-the-example-project"></a>Vytvoření ukázkového projektu
 V této části se dozvíte, jak vytvořit jednoduchý projekt rozšíření pomocí příkazu nabídky pro ukázku.

1. Každé rozšíření sady Visual Studio začíná projektem nasazení VSIX, který bude obsahovat prostředky rozšíření. Vytvořte [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] projekt VSIX s názvem `SettingsStoreExtension` . Šablonu projektu VSIX můžete najít v dialogovém okně **Nový projekt** v části **Visual C#/rozšiřitelnost**.

2. Nyní přidejte šablonu vlastní položky příkazu s názvem **SettingsStoreCommand**. V dialogovém okně **Přidat novou položku** přejít na **Visual C#/rozšiřitelnost** a vyberte **vlastní příkaz**. V poli **název** v dolní části okna změňte název souboru příkazů na **SettingsStoreCommand.cs**. Další informace o tom, jak vytvořit vlastní příkaz, najdete v tématu [Vytvoření rozšíření pomocí příkazu nabídky](../extensibility/creating-an-extension-with-a-menu-command.md) .

## <a name="using-the-configuration-settings-store"></a>Použití úložiště nastavení konfigurace
 V této části se dozvíte, jak zjistit a zobrazit nastavení konfigurace.

1. Do souboru SettingsStorageCommand.cs přidejte následující direktivy using:

   ```
   using System.Collections.Generic;
   using Microsoft.VisualStudio.Settings;
   using Microsoft.VisualStudio.Shell.Settings;
   using System.Windows.Forms;
   ```

2. V nástroji `MenuItemCallback` odeberte tělo metody a přidejte tyto řádky do úložiště nastavení konfigurace:

   ```
   SettingsManager settingsManager = new ShellSettingsManager(ServiceProvider);
   SettingsStore configurationSettingsStore = settingsManager.GetReadOnlySettingsStore(SettingsScope.Configuration);
   ```

    <xref:Microsoft.VisualStudio.Shell.Settings.ShellSettingsManager>Je spravovaná pomocná třída přes <xref:Microsoft.VisualStudio.Shell.Interop.IVsSettingsManager> službu.

3. Nyní zjistíte, jestli jsou nainstalované nástroje Windows Phone. Kód by měl vypadat takto:

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

4. Otestujte kód. Sestavte projekt a spusťte ladění.

5. V experimentální instanci v nabídce **nástroje** klikněte na **vyvolat SettingsStoreCommand**.

    Mělo by se zobrazit okno se zprávou, že **Microsoft Windows Phone vývojářské nástroje:**  následované hodnotou **true** nebo **false**.

   Visual Studio uchovává úložiště nastavení v registru systému.

#### <a name="to-use-a-registry-editor-to-verify-configuration-settings"></a>Použití Editoru registru k ověření nastavení konfigurace

1. Otevřete Regedit.exe.

2. Přejděte na HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\14.0Exp_Config\InstalledProducts\\ .

    > [!NOTE]
    > Ujistěte se, že se díváte na klíč, který obsahuje \ 14.0Exp_Config \ a ne \ 14.0_Config \\ . Při spuštění experimentální instance sady Visual Studio se konfigurační nastavení nachází v podregistru "14.0Exp_Config".

3. Rozbalte uzel \Installed Products \. Pokud je zpráva v předchozích krocích **Microsoft Windows Phone vývojářské nástroje nainstalovaná: true**, pak \Installed Products \ by měla obsahovat uzel Microsoft Windows Phone vývojářské nástroje. Pokud je zpráva **Microsoft Windows Phone vývojářské nástroje nainstalovaná: false**, pak \Installed Products \ nesmí obsahovat uzel Microsoft Windows Phone vývojářské nástroje.
