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
ms.openlocfilehash: 115fda00f880e9c2fa1782735dd471fc3df68936
ms.sourcegitcommit: 09d1f5cef5360cdc1cdfd4b22a1a426b38079618
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/22/2020
ms.locfileid: "91005972"
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

### <a name="additional-options"></a>Další možnosti

Žádné

### <a name="default-behavior"></a>Výchozí chování

Výchozím chováním `windowsfeature-enable` nástroje je chyba, jak `input` je třeba.

## <a name="example-usage"></a>Příklad použití

```json
{
    "$schema": "https://json.schemastore.org/devinit.schema-2.0",
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
