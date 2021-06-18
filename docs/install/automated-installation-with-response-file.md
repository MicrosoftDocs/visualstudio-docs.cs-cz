---
title: Automatizace instalace pomocí souboru odpovědí
description: Zjistěte, jak vytvořit soubor odpovědí JSON, který vám pomůže automatizovat instalaci Visual Studio json.
ms.date: 03/30/2019
ms.custom: seodec18
ms.topic: conceptual
helpviewer_keywords:
- response file
- automate
- installation
- command-line
author: j-martens
ms.author: jmartens
manager: jmartens
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: fe1d1a3c5ec13995cb69fff6ba6ec74c7a6c90d9
ms.sourcegitcommit: 5fb4a67a8208707e79dc09601e8db70b16ba7192
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/17/2021
ms.locfileid: "112307716"
---
# <a name="automate-installs-by-using-settings-in-a-response-file"></a>Automatizace instalací pomocí nastavení v souboru odpovědí

Správci, kteří Visual Studio, mohou zadat soubor odpovědi pomocí `--in` parametru jako v následujícím příkladu:

```shell
vs_enterprise.exe --in customInstall.json
```

Soubory odpovědí jsou [soubory JSON,](http://json-schema.org/) jejichž obsah zrcadlí argumenty příkazového řádku.  Obecně platí, že pokud parametr příkazového řádku nemá žádné argumenty (například , atd.), hodnota v souboru odpovědí by měla `--quiet` `--passive` být true/false.  Pokud přebírá argument (například ), hodnota v souboru odpovědi `--installPath <dir>` by měla být řetězec.  Pokud přebírá argument a může se zobrazit na příkazovém řádku více než jednou (například ), mělo by `--add <id>` to být pole řetězců.

Parametry zadané na příkazovém řádku přepíší nastavení ze souboru odpovědí, s výjimkou případů, kdy parametry přechytá více vstupů (například `--add` ). Pokud máte více vstupů, vstupy zadané na příkazovém řádku se sloučí s nastavením ze souboru odpovědí.

## <a name="setting-a-default-configuration-for-visual-studio"></a>Nastavení výchozí konfigurace pro Visual Studio

Pokud jste vytvořili mezipaměť rozložení sítě pomocí , vytvoří se v `--layout` `response.json` rozložení počáteční soubor. Pokud vytvoříte částečné rozložení, bude tento soubor odpovědi obsahovat úlohy a jazyky, které byly zahrnuty v rozložení.  Při spuštění instalačního programu z tohoto rozložení se response.jsna soubor, který vybere úlohy a komponenty zahrnuté v rozložení.  Uživatelé mohou stále vybrat nebo zrušit výběr jakýchkoli úloh v uživatelském rozhraní instalace před instalací Visual Studio.

Správci, kteří vytvářejí rozložení, můžou upravit soubor v rozložení tak, aby mohli řídit výchozí nastavení, která se uživatelům zobrazí při `response.json` instalaci Visual Studio z rozložení.  Pokud například chce správce ve výchozím nastavení nainstalovat konkrétní úlohy a komponenty, může soubor nakonfigurovat tak, aby je `response.json` přidá.

Když Visual Studio instalační program spustí ze složky  rozložení, automaticky použije soubor odpovědi ve složce rozložení.  Tuto možnost nemusíte `--in` používat.

Můžete aktualizovat soubor vytvořený ve složce rozložení offline a definovat výchozí nastavení pro uživatele, `response.json` kteří instalují z tohoto rozložení.

> [!WARNING]
> Je velmi důležité ponechat existující vlastnosti, které byly definovány při vytvoření rozložení.

Základní soubor v rozložení by měl vypadat podobně jako v následujícím příkladu s tím rozdílem, že by zahrnoval hodnotu produktu a kanálu, `response.json` který chcete nainstalovat:

::: moniker range="vs-2017"

```json
{
  "installChannelUri": ".\\ChannelManifest.json",
  "channelUri": "https://aka.ms/vs/15/release/channel",
  "installCatalogUri": ".\\Catalog.json",
  "channelId": "VisualStudio.15.Release",
  "productId": "Microsoft.VisualStudio.Product.Enterprise"
}
```

::: moniker-end

::: moniker range=">=vs-2019"

```json
{
  "installChannelUri": ".\\ChannelManifest.json",
  "channelUri": "https://aka.ms/vs/16/release/channel",
  "installCatalogUri": ".\\Catalog.json",
  "channelId": "VisualStudio.16.Release",
  "productId": "Microsoft.VisualStudio.Product.Enterprise"
}
```

::: moniker-end

Když vytvoříte nebo aktualizujete rozložení, vytvoří se response.template.jsna souboru.  Tento soubor obsahuje všechna ID úloh, komponent a jazyků, které je možné použít.  Tento soubor je k dispozici jako šablona pro to, co všechno může být součástí vlastní instalace.  Správci mohou tento soubor použít jako výchozí bod pro vlastní soubor odpovědí.  Stačí odebrat ID věcí, které nechcete instalovat, a uložit je do vlastního souboru odpovědí.  Nepřiznáte si response.template.jssouboru, jinak se změny ztratí při každé aktualizaci rozložení.

## <a name="example-layout-response-file-content"></a>Příklad obsahu souboru odpovědí rozložení

Následující příklad nainstaluje Visual Studio Enterprise se šesti běžnými úlohami a komponentami a s anglickým i anglickým uživatelským rozhraním. Tento příklad můžete použít jako šablonu. stačí změnit úlohy a komponenty na ty, které chcete nainstalovat:

::: moniker range="vs-2017"

```json
{
  "installChannelUri": ".\\ChannelManifest.json",
  "channelUri": "https://aka.ms/vs/15/release/channel",
  "installCatalogUri": ".\\Catalog.json",
  "channelId": "VisualStudio.15.Release",
  "productId": "Microsoft.VisualStudio.Product.Enterprise",

  "installPath": "C:\\VS2017",
  "quiet": false,
  "passive": false,
  "includeRecommended": true,
  "norestart": false,

  "addProductLang": [
    "en-US",
    "fr-FR"
    ],

    "add": [
        "Microsoft.VisualStudio.Workload.ManagedDesktop",
        "Microsoft.VisualStudio.Workload.Data",
        "Microsoft.VisualStudio.Workload.NativeDesktop",
        "Microsoft.VisualStudio.Workload.NetWeb",
        "Microsoft.VisualStudio.Workload.Office",
        "Microsoft.VisualStudio.Workload.Universal",
        "Component.GitHub.VisualStudio"
    ]
}
```

::: moniker-end

::: moniker range=">=vs-2019"

```json
{
  "installChannelUri": ".\\ChannelManifest.json",
  "channelUri": "https://aka.ms/vs/16/release/channel",
  "installCatalogUri": ".\\Catalog.json",
  "channelId": "VisualStudio.16.Release",
  "productId": "Microsoft.VisualStudio.Product.Enterprise",

  "installPath": "C:\\VS2019",
  "quiet": false,
  "passive": false,
  "includeRecommended": true,
  "norestart": false,

  "addProductLang": [
    "en-US",
    "fr-FR"
    ],

    "add": [
        "Microsoft.VisualStudio.Workload.ManagedDesktop",
        "Microsoft.VisualStudio.Workload.Data",
        "Microsoft.VisualStudio.Workload.NativeDesktop",
        "Microsoft.VisualStudio.Workload.NetWeb",
        "Microsoft.VisualStudio.Workload.Office",
        "Microsoft.VisualStudio.Workload.Universal",
        "Component.GitHub.VisualStudio"
    ]
}
```

::: moniker-end

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Viz také

* [ID úloh a komponent sady Visual Studio](workload-and-component-ids.md)
* [Řešení chyb souvisejících se sítí při instalaci nebo používání Visual Studio](troubleshooting-network-related-errors-in-visual-studio.md)
