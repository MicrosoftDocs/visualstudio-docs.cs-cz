---
title: windowsfeature-disable
description: Nástroj devinit WindowsFeature – zakázat.
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
ms.openlocfilehash: e48ba0a288aec76588e3d984d4c1577e053e35ae
ms.sourcegitcommit: 02f14db142dce68d084dcb0a19ca41a16f5bccff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2020
ms.locfileid: "95442157"
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

Výchozím chováním `windowsfeature-disable` nástroje je chyba, jak `input` je požadováno.

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
