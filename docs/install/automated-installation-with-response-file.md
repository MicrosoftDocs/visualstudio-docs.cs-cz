---
title: Automatizace instalace pomocí souboru odpovědí
description: Zjistěte, jak vytvořit soubor odpovědí JSON, který vám pomůže automatizovat instalaci sady Visual Studio.
ms.date: 03/30/2019
ms.custom: seodec18
ms.topic: conceptual
helpviewer_keywords:
- response file
- automate
- installation
- command-line
author: ornellaalt
ms.author: ornella
manager: jillfra
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: ecdda55bbe4e79af01f8fb9a9a2b77f775548b10
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "76115230"
---
# <a name="how-to-define-settings-in-a-response-file"></a>Jak definovat nastavení v souboru odpovědí

Správci, kteří nasazují Visual Studio můžete `--in` zadat soubor odpovědi pomocí parametru, jako v následujícím příkladu:

```cmd
vs_enterprise.exe --in customInstall.json
```

Soubory odpovědí jsou soubory [JSON,](http://json-schema.org/) jejichž obsah zrcadlí argumenty příkazového řádku.  Obecně platí, že pokud parametr příkazového řádku nepřebírá žádné argumenty (například `--quiet`, `--passive`, atd.), hodnota v souboru odpovědí by měla být true/false.  Pokud trvá argument `--installPath <dir>`(například), hodnota v souboru odpovědí by měla být řetězec.  Pokud trvá argument a může se objevit na příkazovém `--add <id>`řádku více než jednou (například ), mělo by to být pole řetězců.

Parametry, které jsou zadány na příkazovém řádku přepsat nastavení ze souboru odpovědí, `--add`s výjimkou, kdy parametry trvat více vstupů (například). Pokud máte více vstupů, vstupy zadané na příkazovém řádku jsou sloučeny s nastavením ze souboru odpovědí.

## <a name="setting-a-default-configuration-for-visual-studio"></a>Nastavení výchozí konfigurace pro visual studio

Pokud jste vytvořili mezipaměť `--layout`rozložení `response.json` sítě s rozhraním , vytvoří se v rozvržení počáteční soubor. Pokud vytvoříte částečné rozložení, tento soubor odpovědí obsahuje úlohy a jazyky, které byly zahrnuty v rozložení.  Spuštění majedla z tohoto rozložení automaticky používá tento soubor response.json, který vybere úlohy a součásti zahrnuté v rozvržení.  Uživatelé mohou před instalací sady Visual Studio stále vybrat nebo zrušit výběr všech úloh v uživatelském uživatelském nastavení.

Správci, kteří vytvoří rozložení, mohou `response.json` upravit soubor v rozložení a řídit tak výchozí nastavení, která jejich uživatelům zobrazí při instalaci sady Visual Studio z rozložení.  Pokud například správce požaduje, aby byly ve výchozím nastavení nainstalovány určité úlohy a součásti, může `response.json` soubor nakonfigurovat tak, aby je přidával.

Při spuštění nastavení sady Visual Studio ze složky rozložení _automaticky_ použije soubor odpovědí ve složce rozložení.  Tuto `--in` možnost nemusíte používat.

`response.json` Soubor vytvořený ve složce rozložení offline můžete aktualizovat a definovat tak výchozí nastavení pro uživatele, kteří instalují z tohoto rozložení.

> [!WARNING]
> Je důležité ponechat existující vlastnosti, které byly definovány při vytvoření rozložení.

Základní `response.json` soubor v rozložení by měl vypadat podobně jako v následujícím příkladu s tím rozdílem, že by zahrnoval hodnotu produktu a kanálu, který chcete nainstalovat:

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

::: moniker range="vs-2019"

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

Při vytváření nebo aktualizaci rozložení je také vytvořen soubor response.template.json.  Tento soubor obsahuje všechna pracovní vytížení, součásta a ID jazyka, které lze použít.  Tento soubor je k dispozici jako šablona pro to, co všechno by mohlo být zahrnuto do vlastní instalace.  Správci mohou tento soubor použít jako výchozí bod pro vlastní soubor odpovědí.  Stačí odebrat ID pro věci, které nechcete nainstalovat a uložit do vlastního souboru odpovědí.  Nepřizpůsobujte soubor response.template.json nebo budou změny při každé aktualizaci rozložení ztraceny.

## <a name="example-layout-response-file-content"></a>Příklad obsahu souboru odpovědí na rozložení

Následující příklad nainstaluje Visual Studio Enterprise se šesti běžnými úlohami a součástmi a s anglickým a francouzským jazykem ui. Tento příklad můžete použít jako šablonu; stačí změnit úlohy a součásti na ty, které chcete nainstalovat:

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

::: moniker range="vs-2019"

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
* [Poradce při potížích se sítí při instalaci nebo použití sady Visual Studio](troubleshooting-network-related-errors-in-visual-studio.md)
