---
title: require-npm
description: devinit Tool vyžaduje – npm.
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
ms.openlocfilehash: ed87f58e3065da36f113355bde30e70caa87c992
ms.sourcegitcommit: 02f14db142dce68d084dcb0a19ca41a16f5bccff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2020
ms.locfileid: "95442103"
---
# <a name="require-npm"></a>require-npm

`require-npm`Nástroj se používá k instalaci [npm](https://www.npmjs.com/).

## <a name="usage"></a>Využití

Pokud `input` `additionalOptions` jsou vlastnosti i vynechány nebo jsou prázdné, nástroj bude postupovat podle [výchozího](#default-behavior) chování popsané níže.

| Název                                             | Typ   | Vyžadováno | Hodnota                                                                                       |
|--------------------------------------------------|--------|----------|---------------------------------------------------------------------------------------------|
| **vyjádření**                                     | řetězec | No       | Volitelná vlastnost komentářů Nepoužívá se.                                                       |
| [**vstup**](#input)                              | řetězec | Ano      | Určuje verzi NPM. Podrobnosti najdete níže v části o [zadání](#input) .                           |
| [**additionalOptions**](#additional-options)     | řetězec | No       | Nepoužívá se. Podrobnosti najdete níže v části [Další možnosti](#additional-options) .                  |

### <a name="input"></a>Vstup

`input`Vlastnost se používá k určení verze npm.

### <a name="additional-options"></a>Další možnosti

Nepoužívá se.

### <a name="default-behavior"></a>Výchozí chování

Výchozím chováním `require-nodejs` nástroje je instalace nejnovější LTS verze npm.

## <a name="example-usage"></a>Příklad použití
Níže jsou uvedeny příklady, jak spustit `require-npm` pomocí `.devinit.json` .

#### <a name="devinitjson-that-will-install-the-lts-of-npm"></a>.devinit.js, na které se bude instalovat LTS npm:
```json
{
    "$schema": "https://json.schemastore.org/devinit.schema-3.0",
    "run": [
        {
            "tool": "require-npm"
        }
    ]
}
```

#### <a name="devinitjson-that-will-install-a-specific-version-of-npm"></a>.devinit.js, na které se nainstaluje konkrétní verze npm:
```json
{
    "$schema": "https://json.schemastore.org/devinit.schema-3.0",
    "run": [
        {
            "tool": "require-npm",
            "input": "6.14.6"
        }
    ]
}
```