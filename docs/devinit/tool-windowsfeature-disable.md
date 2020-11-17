---
title: windowsfeature-disable
description: Nástroj devinit WindowsFeature – zakázat.
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
ms.openlocfilehash: 1f06f89a61b77bd4c323303ca796252d4874b3cc
ms.sourcegitcommit: 3d96f7a8c9affab40358c3e81e3472db31d841b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/17/2020
ms.locfileid: "94671730"
---
# <a name="windowsfeature-disable"></a>windowsfeature-disable

Tento `windowsfeature-disable` nástroj slouží k získání funkcí systému Windows.

## <a name="usage"></a>Využití

| Název                                             | Typ   | Vyžadováno | Hodnota                                                                  |
|--------------------------------------------------|--------|----------|------------------------------------------------------------------------|
| **vyjádření**                                     | řetězec | No       | Volitelná vlastnost komentářů Nepoužívá se.                                  |
| [**vstup**](#input)                              | řetězec | Ano      | Funkce Windows, která se má nainstalovat Podrobnosti najdete níže v části o [zadání](#input) . |
| [**additionalOptions**](#additional-options)     | řetězec | No       | Podrobnosti najdete níže v části [Další možnosti](#additional-options) .       |

### <a name="input"></a>Vstup

`input`Vlastnost by měla být `name` typu, který `windows feature` chcete zakázat.

### <a name="additional-options"></a>Additional-Options

Žádné

### <a name="default-behavior"></a>Výchozí chování

Výchozím chováním `windowsfeature-disable` nástroje je chyba, jak `input` je třeba.

## <a name="example-usage"></a>Příklad použití
Níže je uveden příklad, jak spustit `windowsfeature-disable` pomocí `.devinit.json` . 

#### <a name="devinitjson-that-will-disable-a-specified-feature"></a>.devinit.js, která zakáže zadanou funkci:
```json
{
    "$schema": "https://json.schemastore.org/devinit.schema-3.0",
    "run": [
        {
            "tool": "require-windowsfeature",
            "input": "web-server",
        }
    ]
}
```
