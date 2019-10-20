---
title: Použití úložiště nastavení | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Settings Store, using
ms.assetid: 447ec08a-eca5-40b8-89b0-f98fdf3d39a4
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f9c42835e720fd3c33e53d862192e3e2863a4423
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72632601"
---
# <a name="using-the-settings-store"></a>Použití úložiště nastavení
Existují dva druhy úložišť nastavení:

- Nastavení konfigurace, která jsou jen pro čtení a nastavení sady Visual Studio a VSPackage. Visual Studio sloučí nastavení ze všech známých souborů. pkgdef do tohoto úložiště.

- Uživatelská nastavení, která jsou zapisovatelná nastavení, jako jsou například ta, která jsou zobrazena na stránkách v dialogovém okně **Možnosti** , stránky vlastností a určitá další dialogová okna. Rozšíření sady Visual Studio je můžou používat pro místní úložiště s malými objemy dat.

  Tento návod ukazuje, jak číst data z úložiště nastavení konfigurace. Vysvětlení, jak zapisovat do úložiště uživatelských nastavení, najdete v tématu [zápis do úložiště uživatelských nastavení](../extensibility/writing-to-the-user-settings-store.md) .

## <a name="creating-the-example-project"></a>Vytvoření ukázkového projektu
 V této části se dozvíte, jak vytvořit jednoduchý projekt rozšíření pomocí příkazu nabídky pro ukázku.

1. Každé rozšíření sady Visual Studio začíná projektem nasazení VSIX, který bude obsahovat prostředky rozšíření. Vytvořte [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] projekt VSIX s názvem `SettingsStoreExtension`. Šablonu projektu VSIX můžete najít v dialogovém okně **Nový projekt** v části **vizuální C# nebo rozšiřitelnost**.

2. Nyní přidejte šablonu vlastní položky příkazu s názvem **SettingsStoreCommand**. V dialogovém okně **Přidat novou položku** přejdete na **možnost C# Visual nebo rozšiřitelnost** a vyberte možnost **vlastní příkaz**. V poli **název** v dolní části okna změňte název souboru příkazů na **SettingsStoreCommand.cs**. Další informace o tom, jak vytvořit vlastní příkaz, najdete v tématu [Vytvoření rozšíření pomocí příkazu nabídky](../extensibility/creating-an-extension-with-a-menu-command.md) .

## <a name="using-the-configuration-settings-store"></a>Použití úložiště nastavení konfigurace
 V této části se dozvíte, jak zjistit a zobrazit nastavení konfigurace.

1. Do souboru SettingsStorageCommand.cs přidejte následující direktivy using:

   ```
   using System.Collections.Generic;
   using Microsoft.VisualStudio.Settings;
   using Microsoft.VisualStudio.Shell.Settings;
   using System.Windows.Forms;
   ```

2. V `MenuItemCallback` odeberte text metody a přidejte tyto řádky do úložiště nastavení konfigurace:

   ```
   SettingsManager settingsManager = new ShellSettingsManager(ServiceProvider);
   SettingsStore configurationSettingsStore = settingsManager.GetReadOnlySettingsStore(SettingsScope.Configuration);
   ```

    @No__t_0 je spravovaná pomocná třída prostřednictvím služby <xref:Microsoft.VisualStudio.Shell.Interop.IVsSettingsManager>.

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

    Mělo by se zobrazit okno se zprávou, že **Microsoft Windows Phone vývojářské nástroje:** následované hodnotou **true** nebo **false**.

   Visual Studio uchovává úložiště nastavení v registru systému.

#### <a name="to-use-a-registry-editor-to-verify-configuration-settings"></a>Použití Editoru registru k ověření nastavení konfigurace

1. Otevřete regedit. exe.

2. Přejděte na HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\14.0Exp_Config\InstalledProducts \\.

    > [!NOTE]
    > Ujistěte se, že se díváte na klíč, který obsahuje \14.0Exp_Config\ a ne \14.0_Config \\. Při spuštění experimentální instance sady Visual Studio se konfigurační nastavení nachází v podregistru "14.0 Exp_Config".

3. Rozbalte uzel \Installed Products \. Pokud je zpráva v předchozích krocích **Microsoft Windows Phone vývojářské nástroje nainstalovaná: true**, pak \Installed Products \ by měla obsahovat uzel Microsoft Windows Phone vývojářské nástroje. Pokud je zpráva **Microsoft Windows Phone vývojářské nástroje nainstalovaná: false**, pak \Installed Products \ nesmí obsahovat uzel Microsoft Windows Phone vývojářské nástroje.
