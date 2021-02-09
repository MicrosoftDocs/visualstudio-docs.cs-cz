---
title: Konfigurační soubor devinit
description: Dokumentace pro .devinit.jssouboru manifestu pro devinit.
ms.date: 11/02/2020
ms.topic: reference
author: andysterland
ms.author: andster
manager: jmartens
ms.workload:
- multiple
monikerRange: '>= vs-2019'
ms.prod: visual-studio-windows
ms.technology: devinit
ms.openlocfilehash: 47859d00861c2361ed03931bf1417e22425d6e68
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99908122"
---
# <a name="devinit-configuration-file"></a>konfigurační soubor devinit

`.devinit.json`Soubor definuje závislosti v rámci systému, které vaše aplikace potřebuje ke spuštění a sestavení. Závislosti v rámci systému jsou například Node.js, SQL Server, IIS, RabbitMQ, Docker atd. Jedná se o řazení věcí, které byste normálně nainstalovali do pole pro vývoj, které není nainstalované konkrétním úložištěm. Nejedná se o místo pro definování závislostí specifických pro aplikaci, jako byste měli v rámci správce balíčků, jako je NuGet nebo NPM. Je však místo, kde můžete definovat, že potřebujete tyto správce balíčků.

## <a name="file-location"></a>Umístění souboru

`devinit init`Příkaz je ovládán prostřednictvím `.devinit.json` souboru. Ve výchozím nastavení `devinit` vyhledá soubor v následujících umístěních:

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

`.devinit.json`Soubor lze také zadat explicitně prostřednictvím `--file` / `-f` Možnosti.

### <a name="directories-and-relative-paths"></a>Adresáře a relativní cesty

Cesty jsou relativní vzhledem k umístění, kde je spuštěný devinit. Obvykle se jedná o aktuální pracovní adresář, ze kterého `devinit` byl proveden.

## <a name="file-format"></a>Formát souboru
V nástroji `.devinit.json` můžete zadat více než jeden nástroj, který se má spustit. V `run` části můžete umístit libovolný počet objektů. Příklad tohoto příkladu se zobrazuje v našem ukázkovém [.devinit.jsna](sample-all-tool.md) všech našich nástrojích.

```json
{
    "$schema": "https://json.schemastore.org/devinit.schema-3.0",
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
