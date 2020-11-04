---
title: Konfigurační soubor devinit
description: Dokumentace pro .devinit.jssouboru manifestu pro devinit.
ms.date: 11/02/2020
ms.topic: reference
author: andysterland
ms.author: andster
manager: jillfra
ms.workload:
- multiple
monikerRange: '>= vs-2019'
ms.prod: visual-studio-windows
ms.technology: devinit
ms.openlocfilehash: 29ea900b534bc03e47cfda49dba15af910189e48
ms.sourcegitcommit: e132a870ec198fdcec289227f1a0c1c48fef070c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/04/2020
ms.locfileid: "93344483"
---
# <a name="devinit-configuration-file"></a>konfigurační soubor devinit

## <a name="file-location"></a>Umístění souboru

`devinit.exe init`Příkaz je ovládán prostřednictvím _.devinit.jsv_ souboru. Ve výchozím nastavení `devinit.exe` vyhledá soubor v následujících umístěních:

* {Current-Directory} \\.devinit.jsna
* {Current-Directory} \\devinit.jsna
* {Current-Directory} \\ . devinit \\.devinit.js
* {Current-Directory} \\ . devinit \\devinit.js
* {Current-Directory} \\ devinit \\.devinit.js
* {Current-Directory} \\ devinit \\devinit.js
* {Current-Directory} \\ . devcontainer \\.devinit.js
* {Current-Directory} \\ . devcontainer \\devinit.js

> [!NOTE]
> Pokud je nalezeno více výchozích souborů, pak devinit použije soubor, který se zobrazí jako první v seznamu výše.

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
| **spouštěl**      | array  | Yes      | [Objekt RunTool](#run-tool-object) |

#### <a name="run-tool-object"></a>Spustit objekt nástroje

| Název                  | Typ   | Vyžadováno | Hodnota                                                                                                      |
|-----------------------|--------|----------|------------------------------------------------------------------------------------------------------------|
| **vyjádření**          | řetězec | No       | Komentáře pro položku Nástroje                                                                               |
| **štětec**              | řetězec | Yes      | Název nástroje. `devinit list`Seznam dostupných nástrojů najdete v příkazu.                            |
| **vstup**             | řetězec | No       | Vstup nástroje. Liší se podle nástroje. Například požadovaná verze, ID balíčku, název souboru nebo složka.|
| **additionalOptions** | řetězec | No       | Další argumenty příkazového řádku, které mají být předány nástroji.                                                |

## <a name="examples"></a>Příklady

Další příklady použití devinit naleznete v [části Samples](sample-readme.md).
