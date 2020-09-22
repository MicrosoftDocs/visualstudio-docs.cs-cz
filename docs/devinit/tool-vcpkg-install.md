---
title: vcpkg – instalace
description: devinit Tool vcpkg – Install.
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
ms.openlocfilehash: 2e6dcad778e89b112a8c851f2f27ac46330466af
ms.sourcegitcommit: 566144d59c376474c09bbb55164c01d70f4b621c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2020
ms.locfileid: "90810412"
---
# <a name="vcpkg-install"></a>vcpkg – instalace

Tento `vcpkg-install` nástroj slouží k získání knihoven jazyka C/C++ (označovaných jako porty) pomocí [vcpkg](https://github.com/microsoft/vcpkg).

## <a name="usage"></a>Využití

Pokud `input` `additionalOptions` jsou vlastnosti i vynechány nebo jsou prázdné, nástroj bude postupovat podle [výchozího](#default-behavior) chování popsané níže.

| Název                                             | Typ   | Vyžadováno | Hodnota                                                                                   |
|--------------------------------------------------|--------|----------|-----------------------------------------------------------------------------------------|
| **vyjádření**                                     | řetězec | No       | Volitelná vlastnost komentářů Nepoužívá se.                                                   |
| [**vstup**](#input)                              | řetězec | Yes      | Balíčky, které se mají nainstalovat Podrobnosti najdete níže v části o [zadání](#input) .                       |
| [**additionalOptions**](#additional-options)     | řetězec | No       | Podrobnosti najdete níže v části [Další možnosti](#additional-options) .                        |

### <a name="input"></a>Vstup

`input`Vlastnost by měla být v rámci `name` `vcpkg` instalace nebo seznamu názvů oddělených mezerami pro instalaci více balíčků. Seznam dostupných portů najdete v [úložišti GitHub vcpkg](https://github.com/microsoft/vcpkg/tree/master/ports).

### <a name="additional-options"></a>Další možnosti

Další možnosti jsou předány přímo příkazu [vcpkg](https://docs.microsoft.com/powershell/module/powershellget/install-module?view=powershell-7&preserve-view=true) a jsou popsány v [úložišti GitHub vcpkg](https://github.com/microsoft/vcpkg/blob/master/docs/examples/installing-and-using-packages.md).

### <a name="default-behavior"></a>Výchozí chování

Výchozím chováním `vcpkg-install` nástroje je chyba, jak `input` je třeba.

## <a name="example-usage"></a>Příklad použití

```json
{
    "$schema": "https://json.schemastore.org/devinit.schema-2.0",
    "run": [
        {
            "comments": "Installs the sdl2 port.",
            "tool": "vcpkg-install",
            "input": "sdl2",
        },
        {
            "comments": "Installs the sdl2 and sqlite3 ports.",
            "tool": "vcpkg-install",
            "input": "sdl2 sqlite3"
        }
    ]
}
```
