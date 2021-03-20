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
ms.openlocfilehash: 3225e67db734e02abce96820d44ca1515ddc348f
ms.sourcegitcommit: 3fc099cdc484344c781f597581f299729c6bfb10
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/19/2021
ms.locfileid: "104672629"
---
# <a name="windowsfeature-list"></a>windowsfeature-list

> [!IMPORTANT]
> Od 12. dubna 2021 se už nebudete moct připojit k GitHub Codespaces ze sady Visual Studio 2019 a uzavírá se tato privátní verze Preview. Zaměřujeme se na vývoj prostředí pro vnitřní smyčku s využitím cloudu a řešení VDI optimalizovaná pro širokou škálu úloh sady Visual Studio. Jako součást tohoto `devinit` a přidružených nástrojů již nebudou k dispozici. Doporučujeme, abyste se účastnili našeho fóra komunity vývojářů pro Visual Studio, kde najdete informace o budoucích náhledech a informacích o plánech.

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
