---
title: choco-upgrade
description: devinit Tool Choco – upgrade.
ms.date: 11/20/2020
ms.topic: reference
author: andysterland
ms.author: andster
manager: jillfra
ms.workload:
- multiple
monikerRange: '>= vs-2019'
ms.prod: visual-studio-windows
ms.technology: devinit
ms.openlocfilehash: 27a29584a4cf3cd688abe36f625c2e68967c39c0
ms.sourcegitcommit: 02f14db142dce68d084dcb0a19ca41a16f5bccff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2020
ms.locfileid: "95440487"
---
# <a name="choco-upgrade"></a>choco-upgrade

`choco-upgrade`Nástroj lze použít k instalaci a aktualizaci [čokoládových](https://chocolatey.org/docs/commandsupgrade) balíčků.

## <a name="usage"></a>Využití

Pokud `input` `additionalOptions` jsou vlastnosti i vynechány nebo jsou prázdné, nástroj neprovede žádnou akci.

| Název                                             | Typ   | Vyžadováno  | Hodnota                                                                                                          |
|--------------------------------------------------|--------|-----------|----------------------------------------------------------------------------------------------------------------|
| **vyjádření**                                     | řetězec | No        | Volitelná vlastnost komentářů Nepoužívá se.                                                                          |
| [**vstup**](#input)                              | řetězec | Ano       | Balíček, který se má upgradovat Podrobnosti najdete níže v části o [zadání](#input) .                                                 |
| [**additionalOptions**](#additional-options)     | řetězec | No        | Další možnosti, které se mají předat nástroji Podrobnosti najdete níže v části [Další možnosti](#additional-options) .       |

### <a name="input"></a>Vstup

Tato `input` vlastnost slouží k zadání názvu balíčku, který se má upgradovat (například "MongoDB"), nebo cesty ke konfiguračnímu souboru následujících formátů _packages.config_, _. nuspec_ a _. nupkg_. Hodnota `input` bude připojena k `choco upgrade` příkazu (například `choco upgrade mongodb` ) spolu s případnými argumenty, které jsou specifické v nástroji [`additionalOptions`](#additional-options) a integrovanými `choco` možnostmi (definované [níže](#built-in-options)). Balíčky najdete v [galerii balíčků pro čokolády](https://chocolatey.org/packages). Při použití konfiguračního souboru můžete předat cestu k tomuto souboru ve `input` vlastnosti, například: `"input":"packages.config"` .

### <a name="additional-options"></a>Další možnosti

Další možnosti konfigurace mohou být předány jako hodnota `additionalOptions` . Tyto argumenty jsou přímo Passthrough na argumenty používané [`choco upgrade`](https://chocolatey.org/docs/commands-upgrade) a jsou definovány v dokumentaci k čokoládě.

### <a name="built-in-options"></a>Předdefinované možnosti

`choco-upgrade`Nástroj nastaví řadu `choco` argumentů příkazového řádku, aby bylo zajištěno, že `choco` může běžet bez periferních zařízení. Níže jsou uvedené argumenty a dokumentace k nim najdete v [dokumentaci k čokoládě](https://chocolatey.org/docs/).

| Název                  | Popis                                                                                        |
|-----------------------|----------------------------------------------------------------------------------------------------|
| **--Ano**             | Potvrdit všechny výzvy – vybere kladnou odpověď místo výzvy. Implikuje `--accept-license` . |
| **--No-Progress**     | Nezobrazovat průběh – procento průběhu nebude zobrazeno.                                         |
| **--Skip-PowerShell** | Přeskočit PowerShell – chocolateyInstall.ps1 nebude spuštěná.                                              |

### <a name="default-behavior"></a>Výchozí chování

Výchozím chováním `choco-upgrade` nástroje je chyba, protože `input` vlastnost je povinná.

## <a name="example-usage"></a>Příklad použití
Níže jsou uvedeny příklady, jak spustit `choco-upgrade` pomocí `.devinit.json` .

#### <a name="devinitjson-that-will-update-packages-listed-in-packagesconfig"></a>.devinit.js, které budou aktualizovat balíčky uvedené v packages.config:
```json
{
    "$schema": "https://json.schemastore.org/devinit.schema-3.0",
    "run": [
        {
            "tool": "choco-upgrade",
            "input": "packages.config",
        }
    ]
}
```

#### <a name="devinitjson-that-will-upgrade-mongodb"></a>.devinit.js, které budou upgradovat MongoDB:
```json
{
    "$schema": "https://json.schemastore.org/devinit.schema-3.0",
    "run": [
        {
            "tool": "choco-upgrade",
            "input": "mongodb"
        }
    ]
}
```

#### <a name="devinitjson-that-will-upgrade-to-a-specific-version-of-mongodb"></a>.devinit.js, které budou upgradovány na konkrétní verzi MongoDB:
```json
{
    "$schema": "https://json.schemastore.org/devinit.schema-3.0",
    "run": [
        {
            "tool": "choco-upgrade",
            "input": "mongodb",
            "additionalOptions": "--version 4.2.7"
        }
    ]
}
```