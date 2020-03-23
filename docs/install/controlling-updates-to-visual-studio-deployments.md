---
title: Řízení aktualizací nasazení
description: Přečtěte si, jak změnit místo, kde Visual Studio hledá aktualizaci při instalaci ze sítě.
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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "76115312"
---
# <a name="control-updates-to-network-based-visual-studio-deployments"></a>Řízení aktualizací nasazení sady Visual Studio v síti

Podnikoví správci často vytvářejí rozložení a hostují ho ve sdílené síťové složce, aby je nasadili svým koncovým uživatelům.

## <a name="controlling-where-visual-studio-looks-for-updates"></a>Řízení, kde Visual Studio hledá aktualizace

Ve výchozím nastavení visual studio pokračuje v hledání aktualizací online i v případě, že instalace byla nasazena ze sdílené síťové složky. Pokud je k dispozici aktualizace, uživatel ji může nainstalovat. Veškerý aktualizovaný obsah, který nebyl nalezen v rozložení offline, se stáhne z webu.

Pokud chcete přímou kontrolu nad tím, kde Visual Studio hledá aktualizace, můžete upravit umístění, kde vypadá. Můžete také řídit verzi, na kterou jsou uživatelé aktualizováni. Postup je následující:

1. Vytvoření offline rozložení:

   ```cmd
   vs_enterprise.exe --layout C:\vsoffline --lang en-US
   ```

2. Zkopírujte ji do sdílené složky, kde ji chcete hostovat:

   ```cmd
   xcopy /e C:\vsoffline \\server\share\VS
   ```

3. Upravte soubor response.json v rozložení `channelUri` a změňte hodnotu tak, aby ukazovala na kopii kanáluManifest.json, který řídí správce.

   Ujistěte se, že uniknout zpětná lomítka v hodnotě, jako v následujícím příkladu:

   ```json
   "channelUri":"\\\\server\\share\\VS\\ChannelManifest.json"
   ```

   Koncoví uživatelé teď můžou spustit instalační program z této sdílené složky a nainstalovat visual studio.

   ```cmd
   \\server\share\VS\vs_enterprise.exe
   ```

Pokud správce rozlehlé sítě určí, že je čas, aby se uživatelé aktualizovali na novější verzi sady Visual Studio, mohou [aktualizovat umístění rozložení](update-a-network-installation-of-visual-studio.md) takto, aby zahrnovalo aktualizované soubory.

1. Použijte příkaz, který je podobný následujícímu příkazu:

   ```cmd
   vs_enterprise.exe --layout \\server\share\VS --lang en-US
   ```

2. Ujistěte se, že soubor response.json v aktualizovaném rozložení stále obsahuje vaše vlastní nastavení, konkrétně změny channelUri, takto:

   ```json
   "channelUri":"\\\\server\\share\\VS\\ChannelManifest.json"
   ```

   Existující sady Visual Studio, které se `\\server\share\VS\ChannelManifest.json`instalují z tohoto rozložení, vyhledá v aplikaci aktualizace. Pokud je kanálManifest.json novější než to, co uživatel nainstaloval, Visual Studio upozorní uživatele, že je k dispozici aktualizace.

   Nové instalace automaticky nainstalují aktualizovanou verzi sady Visual Studio přímo z rozložení.

## <a name="controlling-notifications-in-the-visual-studio-ide"></a>Řízení oznámení v ide sady Visual Studio

::: moniker range="vs-2017"

Jak je popsáno výše, sada Visual Studio zkontroluje umístění, ze kterého byla nainstalována, například sdílenou síťovou složku nebo internet, a zjistí, zda jsou k dispozici nějaké aktualizace. Pokud je k dispozici aktualizace, Visual Studio upozorní uživatele s příznakem oznámení v pravém horním rohu okna.

   ![Příznak oznámení pro aktualizace](media/notification-flag.png)

::: moniker-end

::: moniker range="vs-2019"

Jak je popsáno výše, sada Visual Studio zkontroluje umístění, ze kterého byla nainstalována, například sdílenou síťovou složku nebo internet, a zjistí, zda jsou k dispozici nějaké aktualizace. Pokud je k dispozici aktualizace, Visual Studio upozorní uživatele s ikonou oznámení v pravém dolním rohu okna.

   ![Ikona oznámení v ide sady Visual Studio](media/vs-2019/notification-bar.png "Ikona oznámení v ide sady Visual Studio")

::: moniker-end

Oznámení můžete zakázat, pokud nechcete, aby koncoví uživatelé byli upozorňováni na aktualizace. (Můžete například zakázat oznámení, pokud doručujete aktualizace prostřednictvím centrálního mechanismu distribuce softwaru.)

::: moniker range="vs-2017"

Vzhledem k tomu, že Visual Studio 2017 [ukládá položky registru v soukromém registru](tools-for-managing-visual-studio-instances.md#editing-the-registry-for-a-visual-studio-instance), nelze přímo upravit registr typickým způsobem. Visual Studio však `vsregedit.exe` obsahuje nástroj, který můžete použít ke změně nastavení sady Visual Studio. Oznámení můžete vypnout pomocí následujícího příkazu:

```cmd
vsregedit.exe set "C:\Program Files (x86)\Microsoft Visual Studio\2017\Enterprise" HKCU ExtensionManager AutomaticallyCheckForUpdates2Override dword 0
```

::: moniker-end

::: moniker range="vs-2019"

Vzhledem k tomu, že Visual Studio 2019 [ukládá položky registru do soukromého registru](tools-for-managing-visual-studio-instances.md#editing-the-registry-for-a-visual-studio-instance), nemůžete přímo upravit registr typickým způsobem. Visual Studio však `vsregedit.exe` obsahuje nástroj, který můžete použít ke změně nastavení sady Visual Studio. Oznámení můžete vypnout pomocí následujícího příkazu:

```cmd
vsregedit.exe set "C:\Program Files (x86)\Microsoft Visual Studio\2019\Enterprise" HKCU ExtensionManager AutomaticallyCheckForUpdates2Override dword 0
```

::: moniker-end

(Ujistěte se, že nahradit adresář, aby odpovídaly nainstalované instance, kterou chcete upravit.)

> [!TIP]
> Pomocí [programu vswhere.exe](tools-for-managing-visual-studio-instances.md#detecting-existing-visual-studio-instances) vyhledejte konkrétní instanci sady Visual Studio na klientské pracovní stanici.

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Viz také

* [Instalace sady Visual Studio](install-visual-studio.md)
* [Průvodce správcem sady Visual Studio](visual-studio-administrator-guide.md)
* [Instalace sady Visual Studio pomocí parametrů příkazového řádku](use-command-line-parameters-to-install-visual-studio.md)
* [Nástroje pro správu instancí sady Visual Studio](tools-for-managing-visual-studio-instances.md)
* [Životní cyklus produktu Visual Studio a servis](/visualstudio/releases/2019/servicing/)
