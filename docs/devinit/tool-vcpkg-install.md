---
title: vcpkg-install
description: devinit Tool vcpkg – Install.
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
ms.openlocfilehash: 5247bdd262a7c5ec2c3c7e3b77ab21f2777524d1
ms.sourcegitcommit: 02f14db142dce68d084dcb0a19ca41a16f5bccff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2020
ms.locfileid: "95442164"
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

Výchozím chováním `vcpkg-install` nástroje je chyba, jak `input` je požadováno.

## <a name="example-usage"></a>Příklad použití
Níže jsou uvedeny příklady, jak spustit `vcpkg-install` pomocí `.devinit.json` .

#### <a name="devinitjson-that-will-install-the-sdl2-port"></a>.devinit.js, na které se nainstaluje port sdl2:
```json
{
    "$schema": "https://json.schemastore.org/devinit.schema-3.0",
    "run": [
        {
            "tool": "vcpkg-install",
            "input": "sdl2",
        }
    ]
}
```

#### <a name="devinitjson-that-will-install-multiple-ports"></a>.devinit.js, na které se nainstaluje víc portů:
```json
{
    "$schema": "https://json.schemastore.org/devinit.schema-3.0",
    "run": [

        {
            "tool": "vcpkg-install",
            "input": "sdl2 sqlite3"
        }
    ]
}
```