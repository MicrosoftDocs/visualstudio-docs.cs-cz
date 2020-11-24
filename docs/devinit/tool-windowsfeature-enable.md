---
title: windowsfeature-enable
description: Nástroj devinit WindowsFeature – povolit.
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
ms.openlocfilehash: 57c122f9ff86994d6ed262fa41834a01be5fa949
ms.sourcegitcommit: 02f14db142dce68d084dcb0a19ca41a16f5bccff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2020
ms.locfileid: "95442117"
---
# <a name="windowsfeature-enable"></a>windowsfeature-enable

`windowsfeature-enable`Nástroj slouží k povolení funkcí systému Windows.

## <a name="usage"></a>Využití

| Název                                             | Typ   | Vyžadováno | Hodnota                                                                    |
|--------------------------------------------------|--------|----------|--------------------------------------------------------------------------|
| **vyjádření**                                     | řetězec | No       | Volitelná vlastnost komentářů Nepoužívá se.                                    |
| [**vstup**](#input)                              | řetězec | Ano      | Funkce Windows, která se má nainstalovat Podrobnosti najdete níže v části o [zadání](#input) .   |
| [**additionalOptions**](#additional-options)     | řetězec | No       | Podrobnosti najdete níže v části [Další možnosti](#additional-options) .         |

### <a name="input"></a>Vstup

`input`Vlastnost by měla být `name` `windows feature` pro instalaci. Seznam dostupných funkcí můžete najít spuštěním `Get-WindowsFeature` PowerShellu PowerShellu.

### <a name="additional-options"></a>Additional-Options

Žádné

### <a name="default-behavior"></a>Výchozí chování

Výchozím chováním `windowsfeature-enable` nástroje je chyba, jak `input` je požadováno.

## <a name="example-usage"></a>Příklad použití
Níže jsou uvedeny příklady, jak spustit `windowsfeature-enable` pomocí `.devinit.json` .

#### <a name="devinitjson-that-will-install-iis"></a>.devinit.js, které budou instalovat službu IIS:
```json
{
    "$schema": "https://json.schemastore.org/devinit.schema-3.0",
    "run": [
        {
            "tool": "windowsfeature-enable",
            "input": "web-server",
        }
    ]
}
```

#### <a name="devinitjson-that-will-install-the-net-framework"></a>.devinit.js, na které se nainstaluje .NET Framework:
```json
{
    "$schema": "https://json.schemastore.org/devinit.schema-3.0",
    "run": [
        {
            "tool": "windowsfeature-enable",
            "input": "net-framework-features"
        }
    ]
}
```

#### <a name="devinitjson-that-will-install-the-net-framework-45"></a>.devinit.js, na které se nainstaluje .NET Framework 4,5:
```json
{
    "$schema": "https://json.schemastore.org/devinit.schema-3.0",
    "run": [
        {
            "tool": "windowsfeature-enable",
            "input": "net-framework-45-features"
        }
    ]
}
```

#### <a name="devinitjson-that-will-install-the-windows-subsystem-for-linux-20"></a>.devinit.js, na které se nainstaluje podsystém Windows pro Linux 2,0:
```json
{
    "$schema": "https://json.schemastore.org/devinit.schema-3.0",
    "run": [
        {
            "tool": "windowsfeature-enable",
            "input": "Microsoft-Windows-Subsystem-Linux"
        }
    ]
}
```
