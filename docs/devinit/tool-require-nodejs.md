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
ms.openlocfilehash: 3da6bd121aff31c680bea2c4655ee2250f5edb05
ms.sourcegitcommit: 3d96f7a8c9affab40358c3e81e3472db31d841b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/17/2020
ms.locfileid: "94671785"
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
Níže jsou uvedeny příklady, jak spustit `require-nodejs` pomocí `.devinit.json` . 

#### <a name="devinitjson-that-will-install-the-lts-of-nodejs"></a>.devinit.js, na které se bude instalovat LTS Node.js:
```json
{
    "$schema": "https://json.schemastore.org/devinit.schema-3.0",
    "run": [
        {
            "tool": "require-nodejs"
        }
    ]
}
```

#### <a name="devinitjson-that-will-install-a-specific-version-of-nodejs"></a>.devinit.js, na které se nainstaluje konkrétní verze Node.js:
```json
{
    "$schema": "https://json.schemastore.org/devinit.schema-3.0",
    "run": [
        {
            "tool": "require-nodejs",
            "input": "14.4.0"
        }
    ]
}
```
