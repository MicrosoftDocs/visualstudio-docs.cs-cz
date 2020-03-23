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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "75566784"
---
# <a name="synchronize-visual-studio-settings-across-multiple-computers"></a>Synchronizace nastavení sady Visual Studio ve více počítačích

Když se k aplikaci Visual Studio přihlásíte ve více počítačích pomocí stejného účtu individuálního nastavení, může být nastavení synchronizováno mezi počítači.

## <a name="synchronized-settings"></a>Synchronizovaná nastavení

Ve výchozím nastavení jsou synchronizována následující nastavení:

- Nastavení vývoje. Při prvním spuštění sady Visual Studio vyberete kolekci nastavení, ale výběr můžete kdykoli změnit. Další informace naleznete v [tématu Nastavení prostředí](../ide/environment-settings.md).

- Uživatelem definované příkazové aliasy. Další informace o definování aliasů příkazů naleznete v tématu [Aliasy příkazů sady Visual Studio](../ide/reference/visual-studio-command-aliases.md).

- Uživatelem definovaná rozložení oken na stránce **Správa** > **rozložení oken.**

- Na stránkách**Možnosti** **nástroje** > jsou následující:

  - Nastavení velikosti motivu a panelu nabídek na stránce**Možnosti Obecné** **prostředí.** > 

  - Všechna nastavení na stránce**Volby písma a barvy** **prostředí.** > 

  - Všechny klávesové zkratky na stránce**Možnosti klávesnice** **prostředí.** > 

  - Všechna nastavení na stránce Karty **prostředí** > **a Možnosti systému Windows.**

  - Všechna nastavení na stránce možnosti**spuštění** **prostředí.** > 

  - Všechna nastavení na stránkách možností **textového editoru,** například [předvolby stylu kódu](code-styles-and-code-cleanup.md).

  - Všechna nastavení na stránkách možností **aplikace XAML.**

## <a name="turn-off-synchronized-settings-on-a-particular-computer"></a>Vypnutí synchronizovaných nastavení v určitém počítači

Synchronizovaná nastavení sady Visual Studio jsou ve výchozím nastavení zapnutá. Synchronizovaná nastavení v počítači můžete vypnout tak, že přejdete na stránku**Účty** **prostředí** >  **Nástroje** > **a** > po zrušení zaškrtnutí políčka Nastavení **synchronizace mezi zařízeními při přihlášení do sady Visual Studio**.

Pokud se například rozhodnete nesynchronizovat nastavení sady Visual Studio v počítači "A", nebudou v počítači "B" ani v počítači "C" zobrazeny žádné změny nastavení provedené v počítači "A". Počítače "B" a "C" budou pokračovat v synchronizaci mezi sebou, ale ne s počítačem "A".

> [!NOTE]
> Pokud se rozhodnete nesynchronizovat nastavení zrušením výběru možnosti na stránce**Účty** **prostředí** > **Možnosti** >  **nástroje,** > nebudou ovlivněny jiné verze nebo edice sady Visual Studio, které máte ve stejném počítači. Tyto souběžné instalace sady Visual Studio budou pokračovat v synchronizaci nastavení (pokud zde nezrušíte zaškrtnutí možnosti).

## <a name="synchronize-settings-across-visual-studio-family-products-and-editions"></a>Synchronizace nastavení v produktech a edicích sady Visual Studio

Nastavení jsou synchronizována mezi verzemi a edicemi sady Visual Studio *nainstalovanými vedle sebe*. Nastavení jsou také synchronizovány mezi produkty řady Visual Studio, včetně blendu pro Visual Studio. Produkt pro jednotlivé řady však může mít vlastní nastavení, která nejsou sdílena s visual studio. Například nastavení specifická pro blend pro Visual Studio v počítači "A" nejsou sdíleny s Visual Studio v počítačích "A" nebo "B".

## <a name="side-by-side-synchronized-settings"></a>Synchronizovaná nastavení vedle sebe

::: moniker range="vs-2017"

Některá nastavení, jako je rozložení okna nástroje nejsou sdíleny mezi různými souběžné instalace sady Visual Studio. Soubor *CurrentSettings.vssettings* v *%userprofile%\Documents\Visual Studio 2017\Settings* je ve složce specifické pro instalaci, která je podobná *%localappdata%\Microsoft\VisualStudio\15.0_xxxxxxxx\Settings*.

> [!NOTE]
> Chcete-li použít nové nastavení specifické pro instalaci, proveďte novou instalaci. Při upgradu existující instalace sady Visual Studio používá existující sdílené umístění.

Pokud máte aktuálně souběžné instalace sady Visual Studio a chcete použít nové umístění souboru nastavení specifické pro instalaci, postupujte takto:

1. Upgradujte na Visual Studio 2017 verze 15.3 nebo novější.

2. Pomocí **Průvodce importem a exportem nastavení** exportujte všechna existující nastavení do určitého umístění mimo složku *%localappdata%\Microsoft\VisualStudio\15.0_xxxxxxxx.*

3. Otevřete **příkazový řádek pro vývojáře pro VS 2017** a spusťte . `devenv /resetuserdata`

1. Otevřete Visual Studio a importujte uložená nastavení z exportovaného souboru nastavení.

::: moniker-end

::: moniker range=">=vs-2019"

Některá nastavení, jako je rozložení okna nástroje nejsou sdíleny mezi různými souběžné instalace sady Visual Studio. Soubor *CurrentSettings.vssettings* v *%userprofile%\Documents\Visual Studio 2019\Settings* je ve složce specifické pro instalaci, která je podobná *%localappdata%\Microsoft\VisualStudio\16.0_xxxxxxxx\Settings*.

::: moniker-end

## <a name="reset-synchronized-settings"></a>Obnovit synchronizované nastavení

Chcete-li obnovit výchozí nastavení všech nastavení, přihlaste se do sady Visual Studio a pak vyberte **Nástroje** > **Pro import a export nastavení** otevřete Průvodce **nastavením importu a exportu**. Vyberte **Obnovit všechna nastavení** a postupujte podle zbývajících kroků průvodce.

## <a name="see-also"></a>Viz také

- [Přizpůsobení prostředí IDE](../ide/personalizing-the-visual-studio-ide.md)
- [Nastavení prostředí](../ide/environment-settings.md)
- [Dialogové okno Možnosti > účtů prostředí](reference/accounts-environment-options-dialog-box.md)
