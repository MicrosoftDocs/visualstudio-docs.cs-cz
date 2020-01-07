---
title: Synchronizovat nastavení
ms.date: 12/10/2018
ms.topic: conceptual
ms.assetid: a3d2ea29-be5d-4012-9820-44b06adbb7dd
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 8f7183f20139df82d14f80ee4b57e28b4aed3a66
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/01/2020
ms.locfileid: "75566784"
---
# <a name="synchronize-visual-studio-settings-across-multiple-computers"></a>Synchronizace nastavení sady Visual Studio napříč více počítači

Když se přihlásíte do sady Visual Studio na více počítačích pomocí stejného účtu individuálního nastavení, můžete nastavení synchronizovat napříč počítači.

## <a name="synchronized-settings"></a>Synchronizovaná nastavení

Ve výchozím nastavení se synchronizují následující nastavení:

- Nastavení vývoje. Můžete vybrat kolekci nastavení při prvním otevření sady Visual Studio, ale výběr můžete kdykoli změnit. Další informace najdete v tématu [nastavení prostředí](../ide/environment-settings.md).

- Aliasy příkazu definované uživatelem. Další informace o tom, jak definovat aliasy příkazů, naleznete v tématu [Aliasy příkazů sady Visual Studio](../ide/reference/visual-studio-command-aliases.md).

- Uživatelsky definované rozložení oken v **okně** > **Spravovat stránku rozložení oken** .

- Na stránkách **možnosti** > **nástroje** jsou následující možnosti:

  - Nastavení malých a velkých písmen na panelu nabídek na stránce **prostředí** > **Obecné** možnosti.

  - Všechna nastavení na stránce **prostředí** > možnosti **písma a barvy** .

  - Všechny klávesové zkratky na stránce možnosti **prostředí** > **klávesnice** .

  - Všechna nastavení na kartách **prostředí** > a na stránce možnosti **systému Windows** .

  - Všechna nastavení na stránce možnosti **prostředí** > **po spuštění** .

  - Všechna nastavení na stránkách možností **textového editoru** , například [Předvolby stylu kódu](code-styles-and-code-cleanup.md).

  - Všechna nastavení na stránkách možností **Návrhář XAML** .

## <a name="turn-off-synchronized-settings-on-a-particular-computer"></a>Vypnutí synchronizovaných nastavení na konkrétním počítači

Synchronizovaná nastavení pro sadu Visual Studio jsou ve výchozím nastavení zapnutá. Synchronizovaná nastavení můžete na počítači vypnout tak, že na stránce **nástroje** > **možnosti** > **prostředí** > **účty** a v případě přihlášení k Visual Studiu zrušíte zaškrtnutí políčka **synchronizovat nastavení v rámci zařízení**.

Pokud se například rozhodnete, že nesynchronizujete nastavení sady Visual Studio v počítači "A", žádné změny nastavení provedené v počítači "A" se nezobrazí v počítači "B" nebo v počítači "C". Počítače "B" a "C" budou nadále synchronizovány navzájem, ale ne u počítače "A".

> [!NOTE]
> Pokud se rozhodnete nesynchronizovat nastavení tím, že zrušíte výběr možnosti na stránce **nástroje** > **Možnosti** >  > **účty** **prostředí** , ostatní verze nebo edice sady Visual Studio, které máte ve stejném počítači, nebudou ovlivněny. Tato Souběžná instalace sady Visual Studio bude pokračovat v synchronizaci jejich nastavení (Pokud nechcete zrušit možnost, že je to možné).

## <a name="synchronize-settings-across-visual-studio-family-products-and-editions"></a>Synchronizovat nastavení napříč produkty a edicemi řady Visual Studio

Nastavení se synchronizují napříč verzemi a edicemi sady Visual Studio nainstalovanou *vedle*sebe. Nastavení jsou také synchronizována v produktech řady Visual Studio, včetně Blend pro Visual Studio. Samostatný produkt Family však může mít vlastní nastavení, které není sdíleno se sadou Visual Studio. Například nastavení specifická pro Blend pro Visual Studio v počítači "A" nejsou sdílena se sadou Visual Studio na počítačích "A" nebo "B".

## <a name="side-by-side-synchronized-settings"></a>Nastavení vedle sebe synchronizovaného

::: moniker range="vs-2017"

Určitá nastavení, například rozložení okna nástroje, se nesdílí mezi různými souběžnými instalacemi sady Visual Studio. Soubor *CurrentSettings. vssettings* v *%UserProfile%\Documents\Visual Studio 2017 \ Settings* je ve složce určené pro instalaci, která je podobná *%localappdata%\microsoft\visualstudio\15.0_xxxxxxxx \settings*.

> [!NOTE]
> Chcete-li použít nové nastavení specifické pro instalaci, proveďte novou instalaci. Když upgradujete existující instalaci sady Visual Studio, použije se existující sdílené umístění.

Pokud aktuálně máte souběžné instalace sady Visual Studio a chcete použít nové umístění souboru nastavení specifického pro instalaci, postupujte následovně:

1. Upgradujte na Visual Studio 2017 verze 15,3 nebo novější.

2. Pomocí **Průvodce importem a exportem nastavení** můžete exportovat všechna stávající nastavení do umístění mimo složku *%localappdata%\microsoft\visualstudio\15.0_xxxxxxxx* .

3. Otevřete **Developer Command Prompt pro VS 2017** a spusťte `devenv /resetuserdata`.

1. Otevřete sadu Visual Studio a importujte uložená nastavení ze souboru exportovaných nastavení.

::: moniker-end

::: moniker range=">=vs-2019"

Určitá nastavení, například rozložení okna nástroje, se nesdílí mezi různými souběžnými instalacemi sady Visual Studio. Soubor *CurrentSettings. vssettings* v *%UserProfile%\Documents\Visual studiu 2019 \ Settings* je ve složce specifické pro instalaci, která je podobná *%localappdata%\microsoft\visualstudio\16.0_xxxxxxxx \settings*.

::: moniker-end

## <a name="reset-synchronized-settings"></a>Resetovat synchronizovaná nastavení

Pokud chcete resetovat všechna nastavení na jejich výchozí hodnoty, přihlaste se k aplikaci Visual Studio a potom vyberte **nástroje** > **Nastavení importu a exportu** a otevřete **Průvodce importem a exportem nastavení**. Vyberte **Obnovit všechna nastavení** a potom postupujte podle zbývajících kroků průvodce.

## <a name="see-also"></a>Viz také:

- [Přizpůsobení integrovaného vývojového prostředí](../ide/personalizing-the-visual-studio-ide.md)
- [Nastavení prostředí](../ide/environment-settings.md)
- [Dialogové okno Možnosti účtů > prostředí](reference/accounts-environment-options-dialog-box.md)
