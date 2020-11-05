---
title: require-nodejs
description: devinit Tool vyžaduje – NodeJS.
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
ms.openlocfilehash: 6ba6b5a53c6b6f1c67c957c55a612cbe461b108c
ms.sourcegitcommit: f4b49f1fc50ffcb39c6b87e2716b4dc7085c7fb5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/05/2020
ms.locfileid: "93400265"
---
# <a name="require-nodejs"></a>require-nodejs

`require-nodejs`Nástroj se používá k instalaci [Node.js](https://nodejs.org/) přes MSI distribuovanou Node.js organizace.

## <a name="usage"></a>Využití

Pokud `input` `additionalOptions` jsou vlastnosti i vynechány nebo jsou prázdné, nástroj bude postupovat podle [výchozího](#default-behavior) chování popsané níže.

| Název                                             | Typ   | Vyžadováno | Hodnota                                                                     |
|--------------------------------------------------|--------|----------|---------------------------------------------------------------------------|
| **vyjádření**                                     | řetězec | No       | Volitelná vlastnost komentářů Nepoužívá se.                                     |
| [**vstup**](#input)                              | řetězec | No       | Verze Node.JS, která se má nainstalovat Podrobnosti najdete níže v části o [zadání](#input) . |
| [**additionalOptions**](#additional-options)     | řetězec | No       | Podrobnosti najdete níže v části [Další možnosti](#additional-options) .          |

### <a name="input"></a>Vstup

Tato `input` vlastnost slouží k určení verze Node.js. Seznam verzí najdete na [ stránce pro staženíNode.js](https://nodejs.org/en/download/). V případě, že dojde k vynechání některého z úplných verzí, je vyžadována hodnota hlavní_verze. podverze. cesta (například 14.4.0). instalace se nezdaří.

### <a name="additional-options"></a>Další možnosti

Další možnosti konfigurace mohou být předány jako hodnota `additionalOptions` . Tyto argumenty jsou přímým průchodem instalačního programu MSI pro Node.js.  

### <a name="default-behavior"></a>Výchozí chování

Výchozím chováním `require-nodejs` nástroje je nainstalovat nejnovější verzi LTS uzlu, jak je podrobně popsáno na [webu](https://nodejs.org/en/download/)Node.JS.

## <a name="example-usage"></a>Příklad použití

```json
{
    "$schema": "https://json.schemastore.org/devinit.schema-3.0",
    "run": [
        {
            "comments": "Example that will trigger the Default behavior of installing latest LTS of Node.JS.",
            "tool": "require-nodejs"
        },
        {
            "comments": "Example that will install a specific version.",
            "tool": "require-nodejs",
            "input": "14.4.0"
        }
    ]
}
```
