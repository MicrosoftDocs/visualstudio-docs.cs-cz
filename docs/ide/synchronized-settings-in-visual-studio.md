---
title: Synchronizovat nastavení
description: Přečtěte si, jak synchronizovat nastavení Visual studia napříč několika počítači, a to přihlášením ke stejnému účtu přizpůsobení.
ms.custom: SEO-VS-2020
ms.date: 06/18/2020
ms.topic: conceptual
ms.assetid: a3d2ea29-be5d-4012-9820-44b06adbb7dd
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 5326264063d135582f2e9b8730ffcf16cba9e3d6
ms.sourcegitcommit: df6ba39a62eae387e29f89388be9e3ee5ceff69c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2020
ms.locfileid: "96479200"
---
# <a name="synchronize-visual-studio-settings-across-multiple-computers"></a>Synchronizace nastavení sady Visual Studio napříč více počítači

Když se přihlásíte do sady Visual Studio na více počítačích pomocí stejného účtu individuálního nastavení, můžete nastavení synchronizovat napříč počítači.

## <a name="synchronized-settings"></a>Synchronizovaná nastavení

Ve výchozím nastavení se synchronizují následující nastavení:

- Nastavení vývoje. Můžete vybrat kolekci nastavení při prvním otevření sady Visual Studio, ale výběr můžete kdykoli změnit. Další informace najdete v tématu [nastavení prostředí](../ide/environment-settings.md).

- Aliasy příkazů definované uživatelem Další informace o tom, jak definovat aliasy příkazů, naleznete v tématu [Aliasy příkazů sady Visual Studio](../ide/reference/visual-studio-command-aliases.md).

- Uživatelsky definované rozložení oken v **okně**  >  **Spravovat stránku rozložení oken** .

- Na **Tools**  >  stránkách **Možnosti** nástrojů se nacházejí tyto možnosti:

  - Motiv a nastavení velikosti písmen na panelu nabídek **Environment** na  >  stránce **Obecné** možnosti prostředí.

  - Všechna nastavení na **Environment**  >  stránce možnosti **písma a barvy** prostředí.

  - Všechny klávesové zkratky na **Environment**  >  stránce možností **klávesnice** prostředí.

  - Všechna nastavení na **Environment**  >  **kartách prostředí a** na stránce Možnosti systému Windows.

  - Všechna nastavení na **Environment**  >  stránce možnosti **spuštění** prostředí.

  - Všechna nastavení na stránkách možností **textového editoru** , například [Předvolby stylu kódu](code-styles-and-code-cleanup.md).

  - Všechna nastavení na stránkách možností **Návrhář XAML** .

## <a name="turn-off-synchronized-settings-on-a-particular-computer"></a>Vypnutí synchronizovaných nastavení na konkrétním počítači

Synchronizovaná nastavení pro Visual Studio jsou ve výchozím nastavení zapnutá. Synchronizovaná nastavení v počítači můžete vypnout tak, že na stránce **nástroje** zobrazíte  >  **Options**  >  **Environment**  >  **účty** prostředí možnosti a v **případě přihlášení do sady Visual Studio zrušíte zaškrtnutí možnosti Synchronizovat nastavení v rámci zařízení**.

Pokud se například rozhodnete, že nechcete synchronizovat nastavení v aplikaci Visual Studio v počítači "A", žádné změny nastavení provedené v počítači "A" se nezobrazí v počítači "B" nebo v počítači "C". Počítače "B" a "C" budou nadále synchronizovány navzájem, ale ne u počítače "A".

> [!NOTE]
> Pokud se rozhodnete nesynchronizovat nastavení tím, že zrušíte výběr možnosti na **Tools**  >  **Options**  >  **Environment**  >  stránce **účty** prostředí možnosti nástrojů, jiné verze nebo edice sady Visual Studio, které máte ve stejném počítači, nebudou ovlivněny. Tato Souběžná instalace sady Visual Studio bude pokračovat v synchronizaci jejich nastavení (Pokud nechcete zrušit možnost, že je to možné).

## <a name="synchronize-settings-across-visual-studio-ide-products-and-editions"></a>Synchronizace nastavení v rámci produktů a edicí IDE sady Visual Studio

Nastavení se synchronizují napříč verzemi a edicemi sady Visual Studio nainstalovanou *vedle* sebe. Nastavení jsou také synchronizovaná v rámci Visual Studio IDE Products, včetně Blend pro Visual Studio. Jednotlivý produkt IDE sady Visual Studio však může mít vlastní nastavení, které není sdíleno se sadou Visual Studio. Například nastavení specifická pro Blend pro Visual Studio v počítači "A" nejsou sdílena se sadou Visual Studio na počítačích "A" nebo "B".

## <a name="side-by-side-synchronized-settings"></a>Nastavení vedle sebe synchronizovaného

::: moniker range="vs-2017"

Určitá nastavení, například rozložení okna nástroje, se nesdílí mezi různými souběžnými instalacemi sady Visual Studio. Soubor *CurrentSettings. vssettings* v *%UserProfile%\Documents\Visual Studio 2017 \ Settings* je ve složce určené pro instalaci, která je podobná *%LocalAppData%\Microsoft\VisualStudio\ 15.0_xxxxxxxx \settings*.

> [!NOTE]
> Chcete-li použít nové nastavení specifické pro instalaci, proveďte novou instalaci. Když upgradujete existující instalaci sady Visual Studio, použije se existující sdílené umístění.

Pokud aktuálně máte souběžné instalace sady Visual Studio a chcete použít nové umístění souboru nastavení specifického pro instalaci, postupujte následovně:

1. Upgradujte na Visual Studio 2017 verze 15,3 nebo novější.

2. Pomocí **Průvodce importem a exportem nastavení** můžete exportovat všechna stávající nastavení do umístění mimo složku *%LocalAppData%\Microsoft\VisualStudio\ 15.0_xxxxxxxx* .

3. Otevřete **Developer Command Prompt pro VS 2017** a spusťte `devenv /resetuserdata` .

1. Otevřete sadu Visual Studio a importujte uložená nastavení ze souboru exportovaných nastavení.

::: moniker-end

::: moniker range=">=vs-2019"

Určitá nastavení, například rozložení okna nástroje, se nesdílí mezi různými souběžnými instalacemi sady Visual Studio. Soubor *CurrentSettings. vssettings* v *%UserProfile%\Documents\Visual studiu 2019 \ Settings* je ve složce specifické pro instalaci, která je podobná *%LocalAppData%\Microsoft\VisualStudio\ 16.0_xxxxxxxx \settings*.

::: moniker-end

## <a name="reset-synchronized-settings"></a>Resetovat synchronizovaná nastavení

Pokud chcete resetovat všechna nastavení na jejich výchozí hodnoty, přihlaste se k Visual Studiu a pak výběrem možnosti **nástroje**  >  **importovat a exportovat nastavení** otevřete **Průvodce importem a exportem nastavení**. Vyberte **Obnovit všechna nastavení** a potom postupujte podle zbývajících kroků průvodce.

## <a name="see-also"></a>Viz také

- [Přizpůsobení integrovaného vývojového prostředí](../ide/personalizing-the-visual-studio-ide.md)
- [Nastavení prostředí](../ide/environment-settings.md)
- [Dialogové okno Možnosti účtů > prostředí](reference/accounts-environment-options-dialog-box.md)
- [Souběžná instalace různých verzí sady Visual Studio](../install/install-visual-studio-versions-side-by-side.md)
