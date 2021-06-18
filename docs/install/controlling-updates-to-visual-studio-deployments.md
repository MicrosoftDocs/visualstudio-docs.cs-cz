---
title: Řízení aktualizací pro nasazení
description: Naučte se, jak změnit, kde aplikace Visual Studio při instalaci ze sítě vyhledává aktualizaci.
ms.date: 04/06/2021
ms.custom: seodec18
ms.topic: conceptual
helpviewer_keywords:
- '{{PLACEHOLDER}}'
- '{{PLACEHOLDER}}'
ms.assetid: 35C7AB05-07D5-4B38-BCAC-AB88444E7368
author: j-martens
ms.author: jmartens
manager: jmartens
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: f15281db55381dadbfd3370eb10a04feeab9c3a5
ms.sourcegitcommit: 5fb4a67a8208707e79dc09601e8db70b16ba7192
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/17/2021
ms.locfileid: "112307567"
---
# <a name="control-updates-to-network-based-visual-studio-deployments"></a>Řízení aktualizací pro nasazení sady Visual Studio založené na síti

Podnikoví správci často vytvářejí rozložení a hostují ho v síťové sdílené složce, aby je mohli nasadit koncovým uživatelům. Tato stránka popisuje, jak správně nakonfigurovat možnosti rozložení sítě.

## <a name="controlling-where-visual-studio-looks-for-updates"></a>Řízení, kde aplikace Visual Studio hledá aktualizace

**Scénář 1: klient byl původně nainstalován z rozložení, ale je nakonfigurován pro příjem aktualizací z umístění rozložení sítě nebo z webu.**

Ve výchozím nastavení Visual Studio nadále hledá aktualizace online i v případě, že byla instalace původně nasazena ze sdílené síťové složky. Pokud je na webu k dispozici aktualizace, může ji uživatel nainstalovat. I když se mezipaměť rozložení sítě nejdřív kontroluje u všech aktualizovaných produktových bitů, pokud tam tam nenajdete, Visual Studio bude hledat a stahovat aktualizované produktové bity z webu.

**Scénář 2: klient byl původně nainstalován a měl by přijímat pouze aktualizace z rozložení sítě.**

Chcete-li určit, kde má klient sady Visual Studio vyhledat aktualizace, například pokud klientský počítač nemá přístup k Internetu, a chcete zajistit, aby byl a vždy nainstalován z rozložení, můžete nakonfigurovat umístění, kde instalační program klienta vyhledá aktualizované verze produktu. Před tím, než klient provede počáteční instalaci z rozložení, je vhodné se ujistit, že toto nastavení je správně nakonfigurované.

1. Vytvořit offline rozložení:

   ```shell
   vs_enterprise.exe --layout C:\vsoffline --lang en-US
   ```

2. Zkopírujte ho do sdílené složky, kam ho chcete hostovat:

   ```shell
   xcopy /e C:\vsoffline \\server\share\VS
   ```

3. Upravte `response.json` soubor v rozložení a změňte `channelUri` hodnotu tak, aby odkazovala na kopii channelManifest.jsv tom, že ovládací prvky správce.

   Nezapomeňte zadat zpětná lomítka v hodnotě, jak je uvedeno v následujícím příkladu:

   ```json
   "channelUri":"\\\\server\\share\\VS\\ChannelManifest.json"
   ```

   Nyní mohou koncoví uživatelé spustit instalaci z této sdílené složky pro instalaci sady Visual Studio.

   ```shell
   \\server\share\VS\vs_enterprise.exe
   ```

Když správce podniku zjistí, že je doba, kterou si uživatelé chtějí aktualizovat na novější verzi sady Visual Studio, může [aktualizovat umístění rozložení](update-a-network-installation-of-visual-studio.md) , aby zahrnovalo aktualizované soubory, a to následujícím způsobem.

1. Použijte příkaz, který se podobá následujícímu příkazu:

   ```shell
   vs_enterprise.exe --layout \\server\share\VS --lang en-US
   ```

2. Ujistěte se, že `response.json` soubor v aktualizovaném rozložení stále obsahuje vaše vlastní nastavení, konkrétně úpravy parametr channeluri, a to následujícím způsobem:

   ```json
   "channelUri":"\\\\server\\share\\VS\\ChannelManifest.json"
   ```

Stávající instalace sady Visual Studio z tohoto rozložení hledají aktualizace na `\\server\share\VS\ChannelManifest.json` . Pokud je channelManifest.jsje novější než uživatel, který je nainstaloval, Visual Studio uživatele upozorní, že je k dispozici aktualizace.

Jakákoli aktualizace instalace iniciovaná z klienta automaticky nainstaluje aktualizovanou verzi sady Visual Studio přímo z rozložení.

**Scénář 3: klient původně nainstaloval z webu, ale měl by teď přijímat jenom aktualizace z rozložení sítě.**

V některých případech klientský počítač již mohl nainstalovat aplikaci Visual Studio z webu, ale nyní chce, aby všechny budoucí aktualizace pocházely ze spravovaného rozložení. Jediným podporovaným způsobem, jak to provést, je vytvořit rozložení sítě s požadovanou verzí produktu a pak na klientském počítači spustit zaváděcí nástroj _z umístění rozložení_ (např. `\\server\share\vs_enterprise.exe` ). V ideálním případě by k původní instalaci klienta došlo pomocí zaváděcího nástroje z rozložení sítě s správně nakonfigurovaným parametr channeluri, ale při spuštění aktualizovaného zaváděcího nástroje z umístění rozložení sítě bude také fungovat. Jedna z těchto akcí by mohla být vložena na klientském počítači, připojení s tímto umístěním rozložení. Jediným aspektem, který má tento scénář fungovat správně, je, že "parametr channeluri" v `response.json` souboru rozložení musí být stejný jako parametr channeluri, který byl nastaven na počítači klienta, když se nastala původní instalace. Nejpravděpodobnější, že tato hodnota byla původně nastavena na [kanál](https://aka.ms/vs/16/release/channel)pro internetovou verzi.

## <a name="controlling-notifications-in-the-visual-studio-ide"></a>Řízení oznámení v integrovaném vývojovém prostředí sady Visual Studio

::: moniker range="vs-2017"

Jak bylo popsáno výše, Visual Studio kontroluje umístění, ze kterého byl nainstalován, například sdílenou síťovou složku nebo Internet, a zjišťuje, zda jsou k dispozici nějaké aktualizace. Když je k dispozici aktualizace, Visual Studio upozorní uživatele pomocí příznaku oznámení v pravém horním rohu okna.

   ![Příznak oznámení pro aktualizace](media/notification-flag.png)

::: moniker-end

::: moniker range=">=vs-2019&quot;

Jak bylo popsáno výše, Visual Studio kontroluje umístění, ze kterého byl nainstalován, například sdílenou síťovou složku nebo Internet, a zjišťuje, zda jsou k dispozici nějaké aktualizace. Když je k dispozici aktualizace, Visual Studio upozorní uživatele pomocí ikony oznámení v pravém dolním rohu okna.

   ![Ikona oznámení v integrovaném vývojovém prostředí sady Visual Studio](media/vs-2019/notification-bar.png &quot;Ikona oznámení v integrovaném vývojovém prostředí sady Visual Studio")

::: moniker-end

Oznámení můžete zakázat, pokud nechcete, aby koncoví uživatelé byli upozorňováni na aktualizace. Oznámení můžete například zakázat při doručování aktualizací prostřednictvím centrálního mechanismu distribuce softwaru.)

::: moniker range="vs-2017"

Vzhledem k tomu, že Visual Studio 2017 [ukládá položky registru do privátního registru](tools-for-managing-visual-studio-instances.md#editing-the-registry-for-a-visual-studio-instance), nemůžete v obvyklých případech přímo upravovat registr. Visual Studio ale obsahuje `vsregedit.exe` nástroj, který můžete použít ke změně nastavení sady Visual Studio. Oznámení můžete vypnout pomocí následujícího příkazu:

```shell
vsregedit.exe set "C:\Program Files (x86)\Microsoft Visual Studio\2017\Enterprise" HKCU ExtensionManager AutomaticallyCheckForUpdates2Override dword 0
```

::: moniker-end

::: moniker range="vs-2019"

Vzhledem k tomu, že Visual Studio 2019 [ukládá položky registru do privátního registru](tools-for-managing-visual-studio-instances.md#editing-the-registry-for-a-visual-studio-instance), nemůžete v obvyklých případech přímo upravovat registr. Visual Studio ale obsahuje `vsregedit.exe` nástroj, který můžete použít ke změně nastavení sady Visual Studio. Oznámení můžete vypnout pomocí následujícího příkazu:

```shell
vsregedit.exe set "C:\Program Files (x86)\Microsoft Visual Studio\2019\Enterprise" HKCU ExtensionManager AutomaticallyCheckForUpdates2Override dword 0
```

::: moniker-end

::: moniker range=">=vs-2022"

Vzhledem k tomu, že Visual Studio 2022 [ukládá položky registru do privátního registru](tools-for-managing-visual-studio-instances.md#editing-the-registry-for-a-visual-studio-instance), nemůžete v obvyklých případech přímo upravovat registr. Visual Studio ale obsahuje `vsregedit.exe` nástroj, který můžete použít ke změně nastavení sady Visual Studio. Oznámení můžete vypnout pomocí následujícího příkazu:

```shell
vsregedit.exe set "C:\Program Files\Microsoft Visual Studio\2022\Enterprise" HKCU ExtensionManager AutomaticallyCheckForUpdates2Override dword 0
```

::: moniker-end

(Nezapomeňte nahradit adresář tak, aby odpovídal nainstalované instanci, kterou chcete upravit.)

> [!TIP]
> K vyhledání konkrétní instance aplikace Visual Studio na pracovní stanici klienta použijte [vswhere.exe](tools-for-managing-visual-studio-instances.md#detecting-existing-visual-studio-instances) .

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Viz také

* [Příručka správce sady Visual Studio](visual-studio-administrator-guide.md)
* [Povolení aktualizací správců](enabling-administrator-updates.md)
* [Použití aktualizací správců](applying-administrator-updates.md)
* [Instalace sady Visual Studio s použitím parametrů příkazového řádku](use-command-line-parameters-to-install-visual-studio.md)
* [Nástroje pro správu instancí sady Visual Studio](tools-for-managing-visual-studio-instances.md)
* [Životní cyklus produktu Visual Studio a údržba](/visualstudio/releases/2019/servicing/)
