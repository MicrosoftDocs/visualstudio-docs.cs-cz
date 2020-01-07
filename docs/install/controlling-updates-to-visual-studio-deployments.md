---
title: Řízení aktualizací nasazení
description: Zjistěte, jak změnit, kam sady Visual Studio vyhledá aktualizace při instalaci ze sítě.
ms.date: 03/30/2019
ms.custom: seodec18
ms.topic: conceptual
helpviewer_keywords:
- '{{PLACEHOLDER}}'
- '{{PLACEHOLDER}}'
ms.assetid: 35C7AB05-07D5-4B38-BCAC-AB88444E7368
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: 2cdf4d4e6fb90b18c8141d1d176629539a0a4f8b
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/01/2020
ms.locfileid: "75570580"
---
# <a name="control-updates-to-network-based-visual-studio-deployments"></a>Řízení aktualizací nasazení sady Visual Studio založené na síti

Tito správci často vytvořit rozložení a hostujte ho do souboru sdílené síťové složky pro nasazení pro své koncové uživatele.

## <a name="controlling-where-visual-studio-looks-for-updates"></a>Řízení, ve kterém aplikace Visual Studio vyhledá aktualizace

Ve výchozím nastavení Visual Studio nadále hledat online aktualizace, i v případě, že byla nasazena instalace ze sdílené síťové složky. Pokud je k dispozici aktualizace, uživatel může nainstalovat ji. Aktualizovaný obsah, který nebyl nalezen v offline rozložení je stáhnout z webu.

Pokud chcete přímou kontrolu nad kde sady Visual Studio vyhledá aktualizace, můžete upravit místo, kde bude vypadat. Můžete také řídit verze, kterou vaši uživatelé jsou aktualizovány. Chcete-li to provést, postupujte takto:

1. Vytvořte offline rozložení:

   ```cmd
   vs_enterprise.exe --layout C:\vsoffline --lang en-US
   ```

2. Zkopírujte ho do sdílené složky, ve kterém chcete hostovat ho:

   ```cmd
   xcopy /e C:\vsoffline \\server\share\VS
   ```

3. Upravte soubor response.json v rozložení a změna `channelUri` hodnotu tak, aby odkazoval na kopii channelManifest.json, které řídí správce.

   Ujistěte se, že řídicí zpětná lomítka v hodnotě, jako v následujícím příkladu:

   ```json
   "channelUri":"\\\\server\\share\\VS\\ChannelManifest.json"
   ```

   Koncoví uživatelé teď spustit instalaci z této sdílené složce instalace sady Visual Studio.

   ```cmd
   \\server\share\VS\vs_enterprise.exe
   ```

Když správce podnikové sítě zjistí, je čas pro jejich uživatelům aktualizovat na novější verzi sady Visual Studio, mohou [aktualizovat umístění rozložení](update-a-network-installation-of-visual-studio.md) začlenit aktualizované soubory, následujícím způsobem.

1. Použijte příkaz, který se podobá následující příkaz:

   ```cmd
   vs_enterprise.exe --layout \\server\share\VS --lang en-US
   ```

2. Ujistěte se, soubor response.json v aktualizované rozložení stále obsahuje úpravy, konkrétně změny parametr channelUri následujícím způsobem:

   ```json
   "channelUri":"\\\\server\\share\\VS\\ChannelManifest.json"
   ```

   Existující sady Visual Studio a instaluje se z rozložení vyhledání aktualizací na `\\server\share\VS\ChannelManifest.json`. Pokud channelManifest.json je novější než co uživatel nainstaloval, Visual Studio upozorní uživatele, že je k dispozici aktualizace.

   Nové instalace automaticky nainstalují aktualizovaná verze sady Visual Studio přímo z rozložení.

## <a name="controlling-notifications-in-the-visual-studio-ide"></a>Řízení oznámení v integrovaném vývojovém prostředí sady Visual Studio

::: moniker range="vs-2017"

Jak je popsáno výše, zkontroluje sada Visual Studio umístění, ze kterého jeho instalaci, jako je například sdílené síťové složky nebo na internet, pokud chcete zobrazit, zda jsou k dispozici žádné aktualizace. Pokud je aktualizace dostupná, Visual Studio upozorní uživatele s příznaku oznámení v pravém horním rohu okna.

   ![Příznak oznámení pro aktualizace](media/notification-flag.png)

::: moniker-end

::: moniker range="vs-2019"

Jak je popsáno výše, zkontroluje sada Visual Studio umístění, ze kterého jeho instalaci, jako je například sdílené síťové složky nebo na internet, pokud chcete zobrazit, zda jsou k dispozici žádné aktualizace. Když je k dispozici aktualizace, Visual Studio upozorní uživatele pomocí ikony oznámení v pravém dolním rohu okna.

   ![Ikona oznámení v integrovaném vývojovém prostředí sady Visual Studio](media/vs-2019/notification-bar.png "Ikona oznámení v integrovaném vývojovém prostředí sady Visual Studio")

::: moniker-end

Oznámení můžete zakázat, pokud nechcete koncovým uživatelům oznámeno aktualizací. (Například můžete chtít zakázat oznámení, pokud k doručování aktualizací mechanismem distribuce softwaru centrální.)

::: moniker range="vs-2017"

Protože Visual Studio 2017 [ukládá položky registru v privátním registru](tools-for-managing-visual-studio-instances.md#editing-the-registry-for-a-visual-studio-instance), které nelze přímo upravovat položky registru obvyklým způsobem. Však zahrnuje Visual Studio `vsregedit.exe` nástroj, který vám umožní změnit nastavení sady Visual Studio. Můžete ji vypnout oznámení pomocí následujícího příkazu:

```cmd
vsregedit.exe set "C:\Program Files (x86)\Microsoft Visual Studio\2017\Enterprise" HKCU ExtensionManager AutomaticallyCheckForUpdates2Override dword 0
```

::: moniker-end

::: moniker range="vs-2019"

Vzhledem k tomu, že Visual Studio 2019 [ukládá položky registru do privátního registru](tools-for-managing-visual-studio-instances.md#editing-the-registry-for-a-visual-studio-instance), nemůžete v obvyklých případech přímo upravovat registr. Však zahrnuje Visual Studio `vsregedit.exe` nástroj, který vám umožní změnit nastavení sady Visual Studio. Můžete ji vypnout oznámení pomocí následujícího příkazu:

```cmd
vsregedit.exe set "C:\Program Files (x86)\Microsoft Visual Studio\2019\Enterprise" HKCU ExtensionManager AutomaticallyCheckForUpdates2Override dword 0
```

::: moniker-end

(Nezapomeňte nahradit adresáře tak, aby odpovídaly nainstalované instanci, kterou chcete upravit.)

> [!TIP]
> Použití [vswhere.exe](tools-for-managing-visual-studio-instances.md#detecting-existing-visual-studio-instances) najít konkrétní instanci sady Visual Studio na klientské pracovní stanice.

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Viz také:

* [Instalace sady Visual Studio](install-visual-studio.md)
* [Příručka pro správce aplikace Visual Studio](visual-studio-administrator-guide.md)
* [Instalace sady Visual Studio s použitím parametrů příkazového řádku](use-command-line-parameters-to-install-visual-studio.md)
* [Nástroje pro správu instancí sady Visual Studio](tools-for-managing-visual-studio-instances.md)
* [Životní cyklus produktu Visual Studio a údržba](/visualstudio/releases/2019/servicing/)
