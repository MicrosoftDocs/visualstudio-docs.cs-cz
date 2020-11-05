---
title: windowsfeature-enable
description: Nástroj devinit WindowsFeature – povolit.
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
ms.openlocfilehash: 6e3d2fdaf6be019cae504d4f71258d410d232ff5
ms.sourcegitcommit: f4b49f1fc50ffcb39c6b87e2716b4dc7085c7fb5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/05/2020
ms.locfileid: "93400203"
---
# <a name="windowsfeature-enable"></a>windowsfeature-enable

`windowsfeature-enable`Nástroj slouží k povolení funkcí systému Windows.

## <a name="usage"></a>Využití

| Název                                             | Typ   | Vyžadováno | Hodnota                                                                    |
|--------------------------------------------------|--------|----------|--------------------------------------------------------------------------|
| **vyjádření**                                     | řetězec | No       | Volitelná vlastnost komentářů Nepoužívá se.                                    |
| [**vstup**](#input)                              | řetězec | Yes      | Funkce Windows, která se má nainstalovat Podrobnosti najdete níže v části o [zadání](#input) .   |
| [**additionalOptions**](#additional-options)     | řetězec | No       | Podrobnosti najdete níže v části [Další možnosti](#additional-options) .         |

### <a name="input"></a>Vstup

`input`Vlastnost by měla být `name` `windows feature` pro instalaci. Seznam dostupných funkcí můžete najít spuštěním `Get-WindowsFeature` PowerShellu PowerShellu.

### <a name="additional-options"></a>Additional-Options

Žádné

### <a name="default-behavior"></a>Výchozí chování

Výchozím chováním `windowsfeature-enable` nástroje je chyba, jak `input` je třeba.

## <a name="example-usage"></a>Příklad použití

```json
{
    "$schema": "https://json.schemastore.org/devinit.schema-3.0",
    "run": [
        {
            "comments": "Installs IIS.",
            "tool": "windowsfeature-enable",
            "input": "web-server",
        },
        {
            "comments": "Installs the .NET Framework 3.5.",
            "tool": "windowsfeature-enable",
            "input": "net-framework-features"
        },
        {
            "comments": "Installs the .NET Framework 4.5.",
            "tool": "windowsfeature-enable",
            "input": "net-framework-45-features"
        },
        {
            "comments": "Installs Windows Subsystem for Linux 2.0.",
            "tool": "windowsfeature-enable",
            "input": "Microsoft-Windows-Subsystem-Linux"
        }
    ]
}
```
