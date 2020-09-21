---
title: dotnet – toolinstall
description: devinit nástroj dotnet – toolinstall.
ms.date: 08/28/2020
ms.topic: reference
author: andster
ms.author: andster
manager: jillfra
ms.workload:
- multiple
monikerRange: '>= vs-2019'
ms.prod: visual-studio-windows
ms.technology: devinit
ms.openlocfilehash: afc200bca49617dff40697210ac783d18ff5f532
ms.sourcegitcommit: 566144d59c376474c09bbb55164c01d70f4b621c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2020
ms.locfileid: "90810142"
---
# <a name="dotnet-toolinstall"></a>dotnet – toolinstall

Tento `dotnet-toolinstall` nástroj slouží k instalaci [nástrojů .NET Core](https://dotnet.microsoft.com/) pomocí `dotnet tool update` příkazu.

## <a name="usage"></a>Využití

Pokud `input` `additionalOptions` jsou vlastnosti i vynechány nebo jsou prázdné, nástroj bude postupovat podle [výchozího](#default-behavior) chování popsané níže.

| Název                                             | Typ   | Vyžadováno | Hodnota                                                                 |
|--------------------------------------------------|--------|----------|-----------------------------------------------------------------------|
| **vyjádření**                                     | řetězec | No       | Volitelná vlastnost komentářů Nepoužívá se.                                 |
| [**vstup**](#input)                              | řetězec | Yes      | Nástroj .NET Core, který se má nainstalovat Podrobnosti najdete níže v části o [zadání](#input) . |
| [**additionalOptions**](#additional-options)     | řetězec | No       | Podrobnosti najdete níže v části [Další možnosti](#additional-options) .      |

### <a name="input"></a>Vstup

Tato `input` vlastnost slouží k určení instalace nástroje .NET Core. V systému je k dispozici neoficiální seznam nástrojů [https://github.com/natemcmaster/dotnet-tools](https://github.com/natemcmaster/dotnet-tools) .

### <a name="additional-options"></a>Další možnosti

Další možnosti konfigurace mohou být předány jako hodnota `additionalOptions` . Tyto argumenty představují přímý průchod k argumentům použitým [`dotnet tool update`](https://docs.microsoft.com/dotnet/core/tools/global-tools#update-a-tool) příkazem. 

`dotnet tool update`Příkaz slouží k bezpečnému zpracování případu, kde je nástroj již nainstalován.

### <a name="default-behavior"></a>Výchozí chování

Výchozím chováním `dotnet-toolinstall` nástroje je chyba, jak `input` je požadováno.

## <a name="example-usage"></a>Příklad použití

```json
{
    "$schema": "https://json.schemastore.org/devinit.schema-2.0",
    "run": [
        {
            "comments": "Example that will install the dotnet-trace tool.",
            "tool": "dotnet-toolinstall",
            "input": "dotnet-trace"
        },
        {
            "comments": "Example that will install the dotnet-trace tool as a global tool.",
            "tool": "dotnet-toolinstall",
            "input": "dotnet-trace",
            "additionalOptions": "--global"
        }
    ]
}
```
