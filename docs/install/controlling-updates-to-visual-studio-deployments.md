---
title: Řízení aktualizací nasazení
description: Zjistěte, jak Visual Studio, kde se při instalaci ze sítě hledá aktualizace.
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
ms.openlocfilehash: 3504e866a7f89de8fa38f92a8bfea501ddd952c9
ms.sourcegitcommit: cc66c898ce82f9f1159bd505647f315792cac9fc
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/10/2021
ms.locfileid: "109666793"
---
# <a name="control-updates-to-network-based-visual-studio-deployments"></a>Řízení aktualizací nasazení síťových Visual Studio nasazení

Podniková správci často vytvářejí rozložení a hostují ho ve sdílené síťové sdílené složky, aby je nasadili koncovým uživatelům. Tato stránka popisuje, jak správně nakonfigurovat možnosti rozložení sítě. 

## <a name="controlling-where-visual-studio-looks-for-updates"></a>Řízení, kde Visual Studio hledá aktualizace

**Scénář 1: Klient původně nainstalovaný z rozložení, ale je nakonfigurovaný pro příjem aktualizací z umístění rozložení sítě nebo webu.**

Ve výchozím nastavení Visual Studio nadále hledat aktualizace online, i když byla instalace původně nasazena ze sdílené síťové složky. Pokud je aktualizace dostupná na webu, může ji uživatel nainstalovat. I když se mezipaměť rozložení sítě nejprve prověří z pohledu aktualizovaných bitů produktu, pokud se tam nenachytá, nástroj Visual Studio bude hledat a stahovat aktualizované bity produktu z webu.

**Scénář 2: Klient byl původně nainstalován a měl by přijímat aktualizace pouze z rozložení sítě.**

Pokud chcete řídit, kde klient Visual Studio hledá aktualizace, například pokud váš klientský počítač nemá přístup k internetu a chcete zajistit, aby se z rozložení instaluje jenom a vždy, můžete nakonfigurovat umístění, kde instalační program klienta hledá aktualizované bity produktu. Před počáteční instalací klienta z rozložení je nejlepší zajistit, aby bylo toto nastavení správně nakonfigurované. 

1. Vytvořte offline rozložení:

   ```cmd
   vs_enterprise.exe --layout C:\vsoffline --lang en-US
   ```

2. Zkopírujte ho do sdílené složky, kde ji chcete hostovat:

   ```cmd
   xcopy /e C:\vsoffline \\server\share\VS
   ```

3. Upravte soubor v rozložení a změňte hodnotu tak, aby odkazovat na kopii souboru `response.json` `channelUri` channelManifest.js, kterou řídí správce.

   Nezapomeňte v hodnotě vracet zpětná lomítka jako v následujícím příkladu:

   ```json
   "channelUri":"\\\\server\\share\\VS\\ChannelManifest.json"
   ```

   Koncoví uživatelé teď mohou spustit instalaci z této sdílené složky a Visual Studio.

   ```cmd
   \\server\share\VS\vs_enterprise.exe
   ```

Když správce podniku zjistí, že je doba, kterou si uživatelé chtějí aktualizovat na novější verzi sady Visual Studio, může [aktualizovat umístění rozložení](update-a-network-installation-of-visual-studio.md) , aby zahrnovalo aktualizované soubory, a to následujícím způsobem.

1. Použijte příkaz, který se podobá následujícímu příkazu:

   ```cmd
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

Jak je popsáno výše, Visual Studio zkontroluje umístění, ze kterého byla nainstalována, například sdílená síťová sdílená síť nebo internet, a zjistí, jestli jsou dostupné nějaké aktualizace. Když je k dispozici aktualizace, Visual Studio uživateli upozorní příznakem oznámení v pravém horním rohu okna.

   ![Příznak oznámení pro aktualizace](media/notification-flag.png)

::: moniker-end

::: moniker range="vs-2019&quot;

Jak je popsáno výše, Visual Studio zkontroluje umístění, ze kterého byla nainstalována, například sdílená síťová sdílená síť nebo internet, a zjistí, jestli jsou dostupné nějaké aktualizace. Když je k dispozici aktualizace, Visual Studio uživateli upozorní ikonou oznámení v pravém dolním rohu okna.

   ![Ikona oznámení v integrovaném vývojovém Visual Studio ideu](media/vs-2019/notification-bar.png &quot;Ikona oznámení v integrovaném vývojovém prostředí sady Visual Studio")

::: moniker-end

Pokud nechcete, aby koncoví uživatelé dostávat oznámení o aktualizacích, můžete oznámení zakázat. (Například můžete chtít oznámení zakázat, pokud doručíte aktualizace prostřednictvím centrálního mechanismu distribuce softwaru.)

::: moniker range="vs-2017"

Protože Visual Studio 2017 [](tools-for-managing-visual-studio-instances.md#editing-the-registry-for-a-visual-studio-instance)ukládá položky registru v privátním registru , nemůžete registr běžným způsobem přímo upravovat. Tento Visual Studio ale obsahuje `vsregedit.exe` nástroj, který můžete použít ke změně Visual Studio nastavení. Oznámení můžete vypnout pomocí následujícího příkazu:

```cmd
vsregedit.exe set "C:\Program Files (x86)\Microsoft Visual Studio\2017\Enterprise" HKCU ExtensionManager AutomaticallyCheckForUpdates2Override dword 0
```

::: moniker-end

::: moniker range="vs-2019"

Protože Visual Studio 2019 [](tools-for-managing-visual-studio-instances.md#editing-the-registry-for-a-visual-studio-instance)ukládá položky registru v privátním registru , nemůžete registr běžným způsobem přímo upravovat. Tento Visual Studio ale obsahuje `vsregedit.exe` nástroj, který můžete použít ke změně Visual Studio nastavení. Oznámení můžete vypnout pomocí následujícího příkazu:

```cmd
vsregedit.exe set "C:\Program Files (x86)\Microsoft Visual Studio\2019\Enterprise" HKCU ExtensionManager AutomaticallyCheckForUpdates2Override dword 0
```

::: moniker-end

(Nezapomeňte nahradit adresář tak, aby odpovídal nainstalované instanci, kterou chcete upravit.)

> [!TIP]
> Pomocí [vswhere.exe](tools-for-managing-visual-studio-instances.md#detecting-existing-visual-studio-instances) můžete najít konkrétní instanci Visual Studio na klientské pracovní stanici.

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Viz také

* [Příručka správce sady Visual Studio](visual-studio-administrator-guide.md)
* [Povolení aktualizací pro správce](enabling-administrator-updates.md)
* [Instalace aktualizací správce](applying-administrator-updates.md)
* [Instalace sady Visual Studio s použitím parametrů příkazového řádku](use-command-line-parameters-to-install-visual-studio.md)
* [Nástroje pro správu Visual Studio instancí](tools-for-managing-visual-studio-instances.md)
* [Visual Studio životního cyklu a údržby produktů](/visualstudio/releases/2019/servicing/)
