---
title: Choco – upgrade
description: devinit Tool Choco – upgrade.
ms.date: 08/28/2020
ms.topic: reference
author: andster
ms.author: andster
manager: jillfra
ms.workload:
- multiple
monikerRange: '>= vs-2019'
ms.prod: visual-studio-windows
ms.technology: devinit
ms.openlocfilehash: 7b7c2d3dd005c54edb882e059679d45e77e539be
ms.sourcegitcommit: 566144d59c376474c09bbb55164c01d70f4b621c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2020
ms.locfileid: "90810156"
---
# <a name="choco-upgrade"></a>Choco – upgrade

`choco-upgrade`Nástroj lze použít k instalaci a aktualizaci [čokoládových](https://chocolatey.org/docs/commandsupgrade) balíčků.

## <a name="usage"></a>Využití

Pokud `input` `additionalOptions` jsou vlastnosti i vynechány nebo jsou prázdné, nástroj neprovede žádnou akci.

| Název                                             | Typ   | Vyžadováno | Hodnota                                                                                                          |
|--------------------------------------------------|--------|----------|----------------------------------------------------------------------------------------------------------------|
| **vyjádření**                                     | řetězec | No       | Volitelná vlastnost komentářů Nepoužívá se.                                                                          |
| [**vstup**](#input)                              | řetězec | No       | Balíček, který se má upgradovat Podrobnosti najdete níže v části o [zadání](#input) .                                                 |
| [**additionalOptions**](#additional-options)     | řetězec | No       | Další možnosti, které se mají předat nástroji Podrobnosti najdete níže v části [Další možnosti](#additional-options) .       |

### <a name="input"></a>Vstup

Tato `input` vlastnost slouží k zadání názvu balíčku, který se má upgradovat (například "MongoDB"), nebo cesty ke konfiguračnímu souboru následujících formátů _packages.config_, _. nuspec_a _. nupkg_. Hodnota `input` bude připojena k `choco upgrade` příkazu (například `choco upgrade mongodb` ) spolu s případnými argumenty, které jsou specifické v nástroji [`additionalOptions`](#additional-options) a integrovanými `choco` možnostmi (definované [níže](#built-in-options)). Balíčky najdete v [galerii balíčků pro čokolády](https://chocolatey.org/packages). Při použití konfiguračního souboru můžete předat cestu k tomuto souboru ve `input` vlastnosti, například: `"input":"packages.config"` .

### <a name="additional-options"></a>Další možnosti

Další možnosti konfigurace mohou být předány jako hodnota `additionalOptions` . Tyto argumenty jsou přímo Passthrough na argumenty používané [`choco upgrade`](https://chocolatey.org/docs/commands-upgrade) a jsou definovány v dokumentaci k čokoládě.

## <a name="built-in-options"></a>Předdefinované možnosti

`choco-upgrade`Nástroj nastaví řadu `choco` argumentů příkazového řádku, aby bylo zajištěno, že `choco` může běžet bez periferních zařízení. Níže jsou uvedené argumenty a dokumentace k nim najdete v [dokumentaci k čokoládě](https://chocolatey.org/docs/).

| Název                  | Popis                                                                                        |
|-----------------------|----------------------------------------------------------------------------------------------------|
| **--Ano**             | Potvrdit všechny výzvy – vybere kladnou odpověď místo výzvy. Implikuje `--accept-license` . |
| **--No-Progress**     | Nezobrazovat průběh – procento průběhu nebude zobrazeno.                                         |
| **--Skip-PowerShell** | Přeskočit PowerShell – chocolateyInstall.ps1 nebude spuštěná.                                              |

## <a name="example-usage"></a>Příklad použití

```json
{
    "$schema": "https://json.schemastore.org/devinit.schema-2.0",
    "run": [
        {
            "comments": "Example that will trigger the Default behavior of upgrading packages listed in a packages.config file.",
            "tool": "choco-upgrade",
            "input": "packages.config",
        },
        {
            "comments": "Example that will upgrade the package 'mongodb'.",
            "tool": "choco-upgrade",
            "input": "mongodb"
        },
        {
            "comments": "Example that will upgrade the '4.2.7' version of 'mongodb'.",
            "tool": "choco-upgrade",
            "input": "mongodb",
            "additionalOptions": "--version 4.2.7"
        }
    ]
}
```
