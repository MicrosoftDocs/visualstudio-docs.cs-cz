---
title: Konfigurační soubor devinit
description: Dokumentace pro .devinit.jssouboru manifestu pro devinit.
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
ms.openlocfilehash: 5ba7299f90ce5f3f253a7210456053faa6bd22c0
ms.sourcegitcommit: 062615c058d2ff44751e8d0c704ccfa3c5543469
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/22/2020
ms.locfileid: "90852200"
---
# <a name="devinit-configuration-file"></a>konfigurační soubor devinit

## <a name="file-location"></a>Umístění souboru

`devinit.exe init`Příkaz je ovládán prostřednictvím _.devinit.jsv_ souboru. Ve výchozím nastavení `devinit.exe` vyhledá soubor v následujících umístěních:

- _{Current-Directory}\\_
- _{Current-Directory} \\ . devinit\\_
- _{Current-Directory} \\ . devcontainer\\_

Rozhraní _._ v názvech adresářů a souborů lze tento název vynechat.

_.devinit.jsv_ souboru lze také zadat explicitně prostřednictvím `--file` / `-f` Možnosti.

### <a name="directories-and-relative-paths"></a>Adresáře a relativní cesty

Cesty jsou relativní vzhledem k umístění, kde je spuštěný devinit. Obvykle se jedná o aktuální pracovní adresář, ze kterého `devinit` byl proveden.

## <a name="file-format"></a>Formát souboru

```json
{
    "$schema": "https://json.schemastore.org/devinit.schema-2.0",
    "comments": "string",
    "run": [
        {
            "comments": "string",
            "tool": "string",
            "input": "string|null|undefined",
            "additionalOptions": "string|null|undefined"
        }
    ]
}
```

### <a name="property-values"></a>Hodnoty vlastností

| Název         | Typ   | Vyžadováno | Hodnota                              |
|--------------|--------|----------|------------------------------------|
| **vyjádření** | řetězec | No       | Komentáře k souboru             |
| **spouštěl**      | array  | Ano      | [Objekt RunTool](#run-tool-object) |

#### <a name="run-tool-object"></a>Spustit objekt nástroje

| Název                  | Typ   | Vyžadováno | Hodnota                                                                                                      |
|-----------------------|--------|----------|------------------------------------------------------------------------------------------------------------|
| **vyjádření**          | řetězec | No       | Komentáře pro položku Nástroje                                                                               |
| **štětec**              | řetězec | Ano      | Název nástroje. `devinit list`Seznam dostupných nástrojů najdete v příkazu.                            |
| **vstup**             | řetězec | No       | Vstup nástroje. Liší se podle nástroje. Například požadovaná verze, ID balíčku, název souboru nebo složka.|
| **additionalOptions** | řetězec | No       | Další argumenty příkazového řádku, které mají být předány nástroji.                                                |

## <a name="examples"></a>Příklady

Další příklady použití devinit naleznete v [části Samples](sample-readme.md).
