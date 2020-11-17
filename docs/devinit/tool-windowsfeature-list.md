---
title: windowsfeature-list
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
ms.openlocfilehash: b521009affbc1db81676481e33640a69e619aaf3
ms.sourcegitcommit: 3d96f7a8c9affab40358c3e81e3472db31d841b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/17/2020
ms.locfileid: "94671710"
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
