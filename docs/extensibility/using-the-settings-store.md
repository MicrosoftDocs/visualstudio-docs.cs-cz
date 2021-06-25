---
title: Použití nastavení úložiště | Microsoft Docs
description: Zjistěte, jak číst data z úložiště nastavení konfigurace, které je jen pro čtení Visual Studio a VSPackage.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- Settings Store, using
ms.assetid: 447ec08a-eca5-40b8-89b0-f98fdf3d39a4
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 4d7fff5bc3eeeb3b4515e2e47027f5b88fb7807d
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/25/2021
ms.locfileid: "112898380"
---
# <a name="using-the-settings-store"></a>Použití úložiště nastavení
Existují dva druhy úložišť nastavení:

- Nastavení konfigurace, která jsou jen pro čtení Visual Studio a VSPackage. Visual Studio sloučí nastavení ze všech známých souborů .pkgdef do tohoto úložiště.

- Uživatelská nastavení, což jsou zapisovatelná nastavení, například  ta, která se zobrazují na stránkách v dialogovém okně Možnosti, na stránkách vlastností a určitých dalších dialogových oknech. Visual Studio rozšíření používejte pro místní úložiště malých objemů dat.

  Tento názorný postup ukazuje, jak číst data z úložiště nastavení konfigurace. Vysvětlení [zápisu](../extensibility/writing-to-the-user-settings-store.md) do úložiště uživatelských nastavení najdete v tématu Zápis do úložiště uživatelských nastavení.

## <a name="creating-the-example-project"></a>Vytvoření příkladu projektu
 Tato část ukazuje, jak vytvořit jednoduchý projekt rozšíření s příkazem nabídky pro ukázku.

1. Každé Visual Studio začíná projektem nasazení VSIX, který bude obsahovat prostředky rozšíření. Vytvořte projekt [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] VSIX s názvem `SettingsStoreExtension` . Šablonu projektu VSIX najdete v dialogovém **okně Nový projekt** v části Visual **C# / Rozšiřitelnost**.

2. Teď přidejte vlastní šablonu položky příkazu s názvem **SettingsStoreCommand**. V dialogovém **okně Přidat novou položku** přejděte na Visual **C# / Rozšiřitelnost** a vyberte **Vlastní příkaz**. V **poli Název** v dolní části okna změňte název souboru příkazu **na SettingsStoreCommand.cs**. Další informace o vytvoření vlastního příkazu najdete v tématu [Vytvoření rozšíření pomocí příkazu nabídky.](../extensibility/creating-an-extension-with-a-menu-command.md)

## <a name="using-the-configuration-settings-store"></a>Použití úložiště nastavení konfigurace
 Tato část ukazuje, jak zjistit a zobrazit nastavení konfigurace.

1. Do souboru SettingsStorageCommand.cs přidejte následující direktivy using:

   ```
   using System.Collections.Generic;
   using Microsoft.VisualStudio.Settings;
   using Microsoft.VisualStudio.Shell.Settings;
   using System.Windows.Forms;
   ```

2. V souboru odeberte tělo metody a přidejte `MenuItemCallback` tyto řádky pro získání úložiště nastavení konfigurace:

   ```
   SettingsManager settingsManager = new ShellSettingsManager(ServiceProvider);
   SettingsStore configurationSettingsStore = settingsManager.GetReadOnlySettingsStore(SettingsScope.Configuration);
   ```

    je <xref:Microsoft.VisualStudio.Shell.Settings.ShellSettingsManager> spravovaná pomocná třída <xref:Microsoft.VisualStudio.Shell.Interop.IVsSettingsManager> služby.

3. Teď zjistěte, jestli Windows Phone nástroje nainstalované. Kód by měl vypadat takhle:

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

5. V experimentální instanci v nabídce Nástroje **klikněte** na **Vyvolat nastaveníStoreCommand.**

    Mělo by se zobrazit okno se zprávou **Microsoft Windows Phone Vývojářské nástroje:**  a **true** nebo **false**.

   Visual Studio uchovává úložiště nastavení v systémovém registru.

#### <a name="to-use-a-registry-editor-to-verify-configuration-settings"></a>Ověření nastavení konfigurace pomocí editoru registru

1. Otevřete Regedit.exe.

2. Přejděte na HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\14.0Exp_Config\InstalledProducts\\ .

    > [!NOTE]
    > Ujistěte se, že se díváte na klíč, který obsahuje \14.0Exp_Config\, a ne \14.0_Config \\ . Když spustíte experimentální instanci Visual Studio, nastavení konfigurace se nachází v podregistru registru "14.0Exp_Config".

3. Rozbalte uzel \Installed Products\. Pokud je zpráva v předchozích krocích nastavená na **Microsoft Windows Phone Vývojářské nástroje Nainstalováno: True**, pak by složka \Installed Products\ měla obsahovat uzel Windows Phone Vývojářské nástroje Microsoftu. Pokud se zobrazí zpráva **Microsoft Windows Phone Vývojářské nástroje Nainstalováno: False**, pak by složka \Installed Products\ neměla obsahovat Windows Phone Vývojářské nástroje Microsoftu.
