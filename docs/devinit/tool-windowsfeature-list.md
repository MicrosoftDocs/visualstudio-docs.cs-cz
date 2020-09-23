---
title: WindowsFeature – seznam
description: devinit – seznam nástrojů WindowsFeature
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
ms.openlocfilehash: 6c4c20fb92e0d854eb7745a598efabd7ac426bfc
ms.sourcegitcommit: 417ea66a8b07ec102ece2fa00e07b88edc404c00
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/23/2020
ms.locfileid: "91127826"
---
# <a name="windowsfeature-list"></a>WindowsFeature – seznam

Tento `windowsfeature-list` nástroj slouží k vypsání stavu povolení a zakázání všech funkcí systému Windows.

| Název                                             | Typ   | Vyžadováno | Hodnota                                      |
|--------------------------------------------------|--------|----------|--------------------------------------------|
| **vyjádření**                                     | řetězec | No       | Volitelná vlastnost komentářů Nepoužívá se.      |
| [**vstup**](#input)                              | řetězec | No       | Nepoužívá se. Přeskočen.                         |
| [**additionalOptions**](#additional-options)     | řetězec | No       | Nepoužívá se. Přeskočen.                         |

### <a name="input"></a>Vstup

Nepoužívá se. Přeskočen.

#### <a name="additional-options"></a>Další možnosti

Nepoužívá se. Přeskočen.

### <a name="default-behavior"></a>Výchozí chování

Výchozím chováním tohoto `windowsfeature-list` nástroje je vypsat stav povolit/zakázat všechny funkce systému Windows.

## <a name="example-usage"></a>Příklad použití

```json
{
    "$schema": "./devinit.schema-2.0.json",
    "run": [
        {
            "comments": "Lists the state of all Windows features.",
            "tool": "windowsfeature-list"
        }
    ]
}
```
