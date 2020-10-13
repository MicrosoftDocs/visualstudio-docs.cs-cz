---
title: vcpkg-install
description: devinit Tool vcpkg – Install.
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
ms.openlocfilehash: 6744e8fb3b42f81f6d0814646cab1f2388ebe577
ms.sourcegitcommit: 3e05bd4bfac6f0b8b3534d8c013388f67e288651
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/12/2020
ms.locfileid: "91959757"
---
# <a name="vcpkg-install"></a>vcpkg-install

Tento `vcpkg-install` nástroj slouží k získání knihoven jazyka C/C++ (označovaných jako porty) pomocí [vcpkg](https://github.com/microsoft/vcpkg).

## <a name="usage"></a>Využití

Pokud `input` `additionalOptions` jsou vlastnosti i vynechány nebo jsou prázdné, nástroj bude postupovat podle [výchozího](#default-behavior) chování popsané níže.

| Název                                             | Typ   | Vyžadováno | Hodnota                                                                                   |
|--------------------------------------------------|--------|----------|-----------------------------------------------------------------------------------------|
| **vyjádření**                                     | řetězec | No       | Volitelná vlastnost komentářů Nepoužívá se.                                                   |
| [**vstup**](#input)                              | řetězec | Ano      | Balíčky, které se mají nainstalovat Podrobnosti najdete níže v části o [zadání](#input) .                       |
| [**additionalOptions**](#additional-options)     | řetězec | No       | Podrobnosti najdete níže v části [Další možnosti](#additional-options) .                        |

### <a name="input"></a>Vstup

`input`Vlastnost by měla být v rámci `name` `vcpkg` instalace nebo seznamu názvů oddělených mezerami pro instalaci více balíčků. Seznam dostupných portů najdete v [úložišti GitHub vcpkg](https://github.com/microsoft/vcpkg/tree/master/ports).

### <a name="additional-options"></a>Další možnosti

Další možnosti jsou předány přímo příkazu [vcpkg](/powershell/module/powershellget/install-module?view=powershell-7&preserve-view=true) a jsou popsány v [úložišti GitHub vcpkg](https://github.com/microsoft/vcpkg/blob/master/docs/examples/installing-and-using-packages.md).

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