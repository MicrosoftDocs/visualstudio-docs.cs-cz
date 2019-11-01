---
title: Automatizace instalace pomocí souboru odpovědí
description: Naučte se vytvořit soubor odezvy JSON, který vám pomůže automatizovat instalaci sady Visual Studio.
ms.date: 03/30/2019
ms.custom: seodec18
ms.topic: conceptual
helpviewer_keywords:
- response file
- automate
- installation
- command-line
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: d26211f566bb8f683f3b38deade4f13defe9cb01
ms.sourcegitcommit: 40bd5b27f247a07c2e2514acb293b23d6ce03c29
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2019
ms.locfileid: "73189501"
---
# <a name="how-to-define-settings-in-a-response-file"></a>Definování nastavení v souboru odpovědí

Správci, kteří nasazují Visual Studio, mohou určit soubor odpovědí pomocí parametru `--in`, jak je uvedeno v následujícím příkladu:

```cmd
vs_enterprise.exe --in customInstall.json
```

Soubory odpovědí jsou soubory [JSON](http://json-schema.org/) , jejichž obsah zrcadlí argumenty příkazového řádku.  Obecně platí, že pokud parametr příkazového řádku nepřijímá žádné argumenty (například `--quiet`, `--passive`atd.), musí mít hodnota v souboru odpovědí hodnotu true nebo false.  Pokud převezme argument (například `--installPath <dir>`), musí být hodnota v souboru odpovědí řetězec.  Pokud převezme argument a může se zobrazit na příkazovém řádku více než jednou (například `--add <id>`), mělo by to být pole řetězců.

Parametry, které jsou zadány v nastavení přepisu příkazového řádku ze souboru odpovědí, s výjimkou případů, kdy parametry přebírají více vstupů (například `--add`). Pokud máte více vstupů, jsou vstupy zadané v příkazovém řádku sloučeny s nastavením ze souboru odpovědí.

## <a name="setting-a-default-configuration-for-visual-studio"></a>Nastavení výchozí konfigurace pro Visual Studio

Pokud jste vytvořili mezipaměť rozložení sítě s `--layout`, vytvoří se v rozložení počáteční soubor `response.json`. Pokud vytvoříte částečné rozložení, bude tento soubor odpovědí obsahovat úlohy a jazyky, které byly zahrnuty v rozložení.  Při spuštění instalačního programu z tohoto rozložení se automaticky použije tento soubor Response. JSON, který vybere úlohy a součásti zahrnuté v rozložení.  Uživatelé si stále můžou vybrat libovolné úlohy v uživatelském rozhraní instalace před instalací sady Visual Studio.

Správci, kteří vytvářejí rozložení, mohou upravit soubor `response.json` v rozložení, aby bylo možné řídit výchozí nastavení, která se uživatelům zobrazí při instalaci sady Visual Studio z rozložení.  Pokud například chce správce, aby ve výchozím nastavení nastavil konkrétní úlohy a komponenty, může nakonfigurovat `response.json` soubor, aby je přidal.

Když je instalační program sady Visual Studio spuštěn ze složky rozložení, _automaticky_ používá soubor odpovědí ve složce rozložení.  Nemusíte používat možnost `--in`.

Soubor `response.json`, který je vytvořený ve složce offline rozložení, můžete aktualizovat a definovat výchozí nastavení pro uživatele, kteří z tohoto rozložení nainstalují.

> [!WARNING]
> Je důležité, abyste nechali existující vlastnosti, které byly definovány při vytváření rozložení.

Základní `response.json` soubor v rozložení by měl vypadat podobně jako v následujícím příkladu, s tím rozdílem, že by obsahoval hodnotu pro produkt a kanál, který chcete nainstalovat:

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

Při vytváření nebo aktualizaci rozložení se vytvoří také soubor Response. template. JSON.  Tento soubor obsahuje všechna ID úloh, komponent a jazyků, které lze použít.  Tento soubor je k dispozici jako šablona pro to, co by bylo možné zahrnout do vlastní instalace.  Správci můžou tento soubor použít jako výchozí bod pro vlastní soubor odpovědí.  Stačí odebrat ID pro věci, které nechcete instalovat, a uložit je do vlastního souboru odpovědí.  Neupravujte soubor Response. template. JSON, jinak se provedené změny ztratí při aktualizaci rozložení.

## <a name="example-layout-response-file-content"></a>Příklad obsahu souboru odpovědi na rozložení

Následující příklad instaluje Visual Studio Enterprise se šesti běžnými úlohami a komponentami a zároveň s jazyky anglické a francouzského uživatelského rozhraní. Tento příklad můžete použít jako šablonu. Stačí změnit úlohy a komponenty na ty, které chcete nainstalovat:

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

## <a name="see-also"></a>Viz také:

* [ID úloh a komponent sady Visual Studio](workload-and-component-ids.md)
* [Řešení chyb souvisejících se sítí při instalaci nebo používání sady Visual Studio](troubleshooting-network-related-errors-in-visual-studio.md)
