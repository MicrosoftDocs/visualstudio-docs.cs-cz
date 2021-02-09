---
title: nuget-restore
description: devinit Tool NuGet – obnovení
ms.date: 11/20/2020
ms.topic: reference
author: andysterland
ms.author: andster
manager: jmartens
ms.workload:
- multiple
monikerRange: '>= vs-2019'
ms.prod: visual-studio-windows
ms.technology: devinit
ms.openlocfilehash: f805b5c1c7b3b994c984dfdb6ce937f8cd51edf1
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99848230"
---
# <a name="nuget-restore"></a>nuget-restore

`nuget-restore`Nástroj obnoví závislosti a nástroje specifické pro projekt, které jsou zadány v souboru projektu. Přečtěte si další informace [o obnovení NuGet](/nuget/reference/cli-reference/cli-ref-restore).

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

Další možnosti jsou předány jako – do příkazu NuGet Restore.

### <a name="default-behavior"></a>Výchozí chování

Výchozím chováním `nuget-restore` nástroje je spustit `NuGet restore` v aktuálním adresáři.

## <a name="example-usage"></a>Příklad použití
Níže je uveden příklad, jak spustit `nuget-restore` pomocí `.devinit.json` .

#### <a name="devinitjson-that-will-restore-dependencies-and-tools-of-a-project"></a>.devinit.js, která obnoví závislosti a nástroje projektu:
```json
{
    "$schema": "https://json.schemastore.org/devinit.schema-3.0",
    "run": [
        {
            "tool": "nuget-restore",
            "input": "C:\\nuget\\Nuget.config"
        }
    ]
}
```