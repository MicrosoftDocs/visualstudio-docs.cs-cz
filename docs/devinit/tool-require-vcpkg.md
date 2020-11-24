---
title: require-vcpkg
description: devinit Tool vyžaduje – vcpkg.
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
ms.openlocfilehash: 7fabd803645e9e79e273683c364ca427793c0aff
ms.sourcegitcommit: 02f14db142dce68d084dcb0a19ca41a16f5bccff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2020
ms.locfileid: "95442289"
---
# <a name="require-vcpkg"></a>require-vcpkg

`require-vcpkg`Nástroj se používá k instalaci [vcpkg](https://github.com/microsoft/vcpkg).

## <a name="usage"></a>Využití

Pokud `input` `additionalOptions` jsou vlastnosti i vynechány nebo jsou prázdné, nástroj bude postupovat podle [výchozího](#default-behavior) chování popsané níže.

| Název                                             | Typ   | Vyžadováno | Hodnota                                                                      |
|--------------------------------------------------|--------|----------|----------------------------------------------------------------------------|
| **vyjádření**                                     | řetězec | No       | Volitelná vlastnost komentářů Nepoužívá se.                                      |
| [**vstup**](#input)                              | řetězec | No       | Nepoužívá se. Podrobnosti najdete níže v části o [zadání](#input) .                           |
| [**additionalOptions**](#additional-options)     | řetězec | No       | Nepoužívá se. Podrobnosti najdete níže v části [Další možnosti](#additional-options) . |

### <a name="input"></a>Vstup

Nepoužívá se.

### <a name="additional-options"></a>Další možnosti

Nepoužívá se.

### <a name="default-behavior"></a>Výchozí chování

Výchozím chováním `require-vcpkg` nástroje je instalace vcpkg a jeho přidání do `PATH` .

## <a name="example-usage"></a>Příklad použití
Níže je uveden příklad, jak spustit `require-vcpkg` pomocí `.devinit.json` .

#### <a name="devinitjson-that-will-install-vcpkg"></a>.devinit.js, které budou instalovat vcpkg:
```json
{
    "$schema": "https://json.schemastore.org/devinit.schema-3.0",
    "run": [
        {
            "tool": "require-vcpkg"
        }
    ]
}
```
