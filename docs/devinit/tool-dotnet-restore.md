---
title: dotnet-restore
description: devinit nástroj dotnet – obnovení
ms.date: 08/28/2020
ms.topic: reference
author: andysterland
ms.author: andster
manager: jillfra
ms.workload:
- multiple
monikerRange: '>= vs-2019'
ms.prod: visual-studio-windows
ms.technology: devinit
ms.openlocfilehash: 2febd8a62e041384c8acf5b7b0b5e1c974597c0a
ms.sourcegitcommit: e38419bb842d587fd9e37c24b6cf3fc5c2e74817
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/09/2020
ms.locfileid: "91862253"
---
# <a name="dotnet-restore"></a>dotnet-restore

`dotnet-restore`Nástroj obnoví závislosti a nástroje specifické pro projekt, které jsou zadány v souboru projektu. Přečtěte [si další informace o dotnet Restore.](/dotnet/core/tools/dotnet-restore)

## <a name="usage"></a>Využití

Pokud `input` `additionalOptions` jsou vlastnosti i vynechány nebo jsou prázdné, nástroj bude postupovat podle [výchozího](#default-behavior) chování popsané níže.

| Název                                             | Typ   | Vyžadováno | Hodnota                                                                                |
|--------------------------------------------------|--------|----------|--------------------------------------------------------------------------------------|
| **vyjádření**                                     | řetězec | No       | Volitelná vlastnost komentářů Nepoužívá se.                                                |
| [**vstup**](#input)                              | řetězec | No       | Cesta k souboru projektu nebo řešení, který má být obnoven. Podrobnosti najdete níže v části o [zadání](#input) . |
| [**additionalOptions**](#additional-options)     | řetězec | No       | Podrobnosti najdete níže v části [Další možnosti](#additional-options) .                     |

### <a name="input"></a>Vstup

Cesta k souboru projektu nebo řešení, který má být obnoven.

### <a name="additional-options"></a>Další možnosti

Další možnosti jsou předány jako dotnet restore příkazu.

### <a name="default-behavior"></a>Výchozí chování

Výchozím chováním `dotnet-restore` nástroje je spuštění příkazu ' dotnet Restore ' v aktuálním adresáři.

## <a name="example-usage"></a>Příklad použití

```json
{
    "$schema": "https://json.schemastore.org/devinit.schema-2.0",
    "comments": "A sample dot-devinit file that builds the 'kitchen sink'",
    "run": [
        {
            "tool": "dotnet-restore",
            "comments": "Restores the dependencies and tools of a project using dotnet core.",
            "input": "C:\\app1\\app1.csproj"
        }
    ]
}
```