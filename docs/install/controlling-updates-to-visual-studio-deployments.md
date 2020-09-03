---
title: Řízení aktualizací pro nasazení
description: Naučte se, jak změnit, kde aplikace Visual Studio při instalaci ze sítě vyhledává aktualizaci.
ms.date: 03/30/2019
ms.custom: seodec18
ms.topic: conceptual
helpviewer_keywords:
- '{{PLACEHOLDER}}'
- '{{PLACEHOLDER}}'
ms.assetid: 35C7AB05-07D5-4B38-BCAC-AB88444E7368
author: ornellaalt
ms.author: ornella
manager: jillfra
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: 8743f042c7c33da34895f93e5df3990f6e0b2ed2
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "76115312"
---
# <a name="control-updates-to-network-based-visual-studio-deployments"></a>Řízení aktualizací pro nasazení sady Visual Studio založené na síti

Podnikoví správci často vytvářejí rozložení a hostují ho v síťové sdílené složce, aby je mohli nasadit koncovým uživatelům.

## <a name="controlling-where-visual-studio-looks-for-updates"></a>Řízení, kde aplikace Visual Studio hledá aktualizace

Ve výchozím nastavení Visual Studio nadále hledá aktualizace online i v případě, že byla instalace nasazena ze sdílené síťové složky. Pokud je aktualizace k dispozici, uživatel ji může nainstalovat. Aktualizovaný obsah, který se nenajde v offline rozložení, se stáhne z webu.

Pokud chcete přímou kontrolu nad tím, kde aplikace Visual Studio hledá aktualizace, můžete změnit umístění, kde vypadá. Můžete také řídit verzi, na kterou se budou uživatelé aktualizovat. Postup je následující:

1. Vytvořit offline rozložení:

   ```cmd
   vs_enterprise.exe --layout C:\vsoffline --lang en-US
   ```

2. Zkopírujte ho do sdílené složky, kam ho chcete hostovat:

   ```cmd
   xcopy /e C:\vsoffline \\server\share\VS
   ```

3. Upravte response.jsv souboru v rozložení a změňte `channelUri` hodnotu tak, aby odkazovala na kopii channelManifest.jsna ovládacím prvku správce.

   Nezapomeňte zadat zpětná lomítka v hodnotě, jak je uvedeno v následujícím příkladu:

   ```json
   "channelUri":"\\\\server\\share\\VS\\ChannelManifest.json"
   ```

   Nyní mohou koncoví uživatelé spustit instalaci z této sdílené složky pro instalaci sady Visual Studio.

   ```cmd
   \\server\share\VS\vs_enterprise.exe
   ```

Když správce podniku zjistí, že je doba, kterou si uživatelé chtějí aktualizovat na novější verzi sady Visual Studio, může [aktualizovat umístění rozložení](update-a-network-installation-of-visual-studio.md) , aby zahrnovalo aktualizované soubory, a to následujícím způsobem.

1. Použijte příkaz, který se podobá následujícímu příkazu:

   ```cmd
   vs_enterprise.exe --layout \\server\share\VS --lang en-US
   ```

2. Ujistěte se, že response.jsv souboru v aktualizovaném rozložení stále obsahuje vaše vlastní nastavení, konkrétně úpravy parametr channeluri, a to takto:

   ```json
   "channelUri":"\\\\server\\share\\VS\\ChannelManifest.json"
   ```

   Stávající instalace sady Visual Studio z tohoto rozložení hledají aktualizace na `\\server\share\VS\ChannelManifest.json` . Pokud je channelManifest.jsje novější než uživatel, který je nainstaloval, Visual Studio uživatele upozorní, že je k dispozici aktualizace.

   Nová instalace automaticky nainstaluje aktualizovanou verzi sady Visual Studio přímo z rozložení.

## <a name="controlling-notifications-in-the-visual-studio-ide"></a>Řízení oznámení v integrovaném vývojovém prostředí sady Visual Studio

::: moniker range="vs-2017"

Jak bylo popsáno výše, Visual Studio kontroluje umístění, ze kterého byl nainstalován, například sdílenou síťovou složku nebo Internet, a zjišťuje, zda jsou k dispozici nějaké aktualizace. Když je k dispozici aktualizace, Visual Studio upozorní uživatele pomocí příznaku oznámení v pravém horním rohu okna.

   ![Příznak oznámení pro aktualizace](media/notification-flag.png)

::: moniker-end

::: moniker range="vs-2019"

Jak bylo popsáno výše, Visual Studio kontroluje umístění, ze kterého byl nainstalován, například sdílenou síťovou složku nebo Internet, a zjišťuje, zda jsou k dispozici nějaké aktualizace. Když je k dispozici aktualizace, Visual Studio upozorní uživatele pomocí ikony oznámení v pravém dolním rohu okna.

   ![Ikona oznámení v integrovaném vývojovém prostředí sady Visual Studio](media/vs-2019/notification-bar.png "Ikona oznámení v integrovaném vývojovém prostředí sady Visual Studio")

::: moniker-end

Oznámení můžete zakázat, pokud nechcete, aby koncoví uživatelé byli upozorňováni na aktualizace. Oznámení můžete například zakázat při doručování aktualizací prostřednictvím centrálního mechanismu distribuce softwaru.)

::: moniker range="vs-2017"

Vzhledem k tomu, že Visual Studio 2017 [ukládá položky registru do privátního registru](tools-for-managing-visual-studio-instances.md#editing-the-registry-for-a-visual-studio-instance), nemůžete v obvyklých případech přímo upravovat registr. Visual Studio ale obsahuje `vsregedit.exe` nástroj, který můžete použít ke změně nastavení sady Visual Studio. Oznámení můžete vypnout pomocí následujícího příkazu:

```cmd
vsregedit.exe set "C:\Program Files (x86)\Microsoft Visual Studio\2017\Enterprise" HKCU ExtensionManager AutomaticallyCheckForUpdates2Override dword 0
```

::: moniker-end

::: moniker range="vs-2019"

Vzhledem k tomu, že Visual Studio 2019 [ukládá položky registru do privátního registru](tools-for-managing-visual-studio-instances.md#editing-the-registry-for-a-visual-studio-instance), nemůžete v obvyklých případech přímo upravovat registr. Visual Studio ale obsahuje `vsregedit.exe` nástroj, který můžete použít ke změně nastavení sady Visual Studio. Oznámení můžete vypnout pomocí následujícího příkazu:

```cmd
vsregedit.exe set "C:\Program Files (x86)\Microsoft Visual Studio\2019\Enterprise" HKCU ExtensionManager AutomaticallyCheckForUpdates2Override dword 0
```

::: moniker-end

(Nezapomeňte nahradit adresář tak, aby odpovídal nainstalované instanci, kterou chcete upravit.)

> [!TIP]
> K vyhledání konkrétní instance aplikace Visual Studio na pracovní stanici klienta použijte [vswhere.exe](tools-for-managing-visual-studio-instances.md#detecting-existing-visual-studio-instances) .

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Viz také

* [Instalace sady Visual Studio](install-visual-studio.md)
* [Příručka správce sady Visual Studio](visual-studio-administrator-guide.md)
* [Instalace sady Visual Studio s použitím parametrů příkazového řádku](use-command-line-parameters-to-install-visual-studio.md)
* [Nástroje pro správu instancí sady Visual Studio](tools-for-managing-visual-studio-instances.md)
* [Životní cyklus produktu Visual Studio a údržba](/visualstudio/releases/2019/servicing/)
