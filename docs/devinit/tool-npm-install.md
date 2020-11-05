---
title: npm-install
description: devinit Tool npm – Install.
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
ms.openlocfilehash: 432c2a6c532e95e7d0e3e4cb22c87930031f5907
ms.sourcegitcommit: f4b49f1fc50ffcb39c6b87e2716b4dc7085c7fb5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/05/2020
ms.locfileid: "93400293"
---
# <a name="npm-install"></a>npm-install

`npm-install`Nástroj lze použít k instalaci balíčků [npm](https://www.npmjs.com/) .

## <a name="usage"></a>Využití

Pokud `input` `additionalOptions` jsou vlastnosti i vynechány nebo jsou prázdné, nástroj neprovede žádnou akci.

| Název                                             | Typ   | Vyžadováno | Hodnota                                                                                                          |
|--------------------------------------------------|--------|----------|----------------------------------------------------------------------------------------------------------------|
| **vyjádření**                                     | řetězec | No       | Volitelná vlastnost komentářů Nepoužívá se.                                                                          |
| [**vstup**](#input)                              | řetězec | Yes      | Balíček, který se má nainstalovat Podrobnosti najdete níže v části o [zadání](#input) .                                                 |
| [**additionalOptions**](#additional-options)     | řetězec | No       | Další možnosti, které se mají předat nástroji Podrobnosti najdete níže v části [Další možnosti](#additional-options) .       |

### <a name="input"></a>Vstup

Tato `input` vlastnost slouží k zadání názvu balíčku, který se má nainstalovat (například ' Mongo ').

### <a name="additional-options"></a>Další možnosti

Další možnosti konfigurace mohou být předány jako hodnota `additionalOptions` . Tyto argumenty představují přímý průchod na argumenty používané [npm Install](https://docs.npmjs.com/cli/install).

## <a name="example-usage"></a>Příklad použití

```json
{
    "$schema": "https://json.schemastore.org/devinit.schema-3.0",
    "run": [
        {
            "comments": "Example that will install the mongo NPM package (https://www.npmjs.com/package/mongo).",
            "tool": "npm-install",
            "input": "mongo",
        }
    ]
}
```
