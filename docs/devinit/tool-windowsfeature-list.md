---
title: windowsfeature-list
description: devinit – seznam nástrojů WindowsFeature
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
ms.openlocfilehash: 07b92e8783393fa19e5c09344a396a6c5c4fc011
ms.sourcegitcommit: 02f14db142dce68d084dcb0a19ca41a16f5bccff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2020
ms.locfileid: "95442124"
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
