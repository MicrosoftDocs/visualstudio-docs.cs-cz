---
title: windowsfeature-list
description: devinit – seznam nástrojů WindowsFeature
ms.date: 11/20/2020
ms.topic: reference
author: andysterland
ms.author: andster
manager: jmartens
ms.workload:
- multiple
monikerRange: '>= vs-2019'
ms.prod: visual-studio-windows
ms.technology: devinit
ms.openlocfilehash: 43370389aaffdb4395248fed6ec83de39f16c86d
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99874503"
---
# <a name="windowsfeature-list"></a>windowsfeature-list

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
Níže je uveden příklad, jak spustit `windowsfeature-list` pomocí `.devinit.json` .

#### <a name="devinitjson-that-will-list-the-state-of-all-windows-features"></a>.devinit.jsv seznamu se zobrazí stav všech funkcí Windows:
```json
{
    "$schema": "https://json.schemastore.org/devinit.schema-3.0.json",
    "run": [
        {
            "tool": "windowsfeature-list"
        }
    ]
}
```
