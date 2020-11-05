---
title: dotnet-toolinstall
description: devinit nástroj dotnet – toolinstall.
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
ms.openlocfilehash: 464460d6a33c01e5c53b66e8a03de7aa7f844953
ms.sourcegitcommit: f4b49f1fc50ffcb39c6b87e2716b4dc7085c7fb5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/05/2020
ms.locfileid: "93399651"
---
# <a name="dotnet-toolinstall"></a>dotnet-toolinstall

Tento `dotnet-toolinstall` nástroj slouží k instalaci [nástrojů .NET Core](https://dotnet.microsoft.com/) pomocí `dotnet tool update` příkazu.

## <a name="usage"></a>Využití

Pokud `input` `additionalOptions` jsou vlastnosti i vynechány nebo jsou prázdné, nástroj bude postupovat podle [výchozího](#default-behavior) chování popsané níže.

| Název                                             | Typ   | Vyžadováno | Hodnota                                                                 |
|--------------------------------------------------|--------|----------|-----------------------------------------------------------------------|
| **vyjádření**                                     | řetězec | No       | Volitelná vlastnost komentářů Nepoužívá se.                                 |
| [**vstup**](#input)                              | řetězec | Yes      | Nástroj .NET Core, který se má nainstalovat Podrobnosti najdete níže v části o [zadání](#input) . |
| [**additionalOptions**](#additional-options)     | řetězec | No       | Podrobnosti najdete níže v části [Další možnosti](#additional-options) .      |

### <a name="input"></a>Vstup

Tato `input` vlastnost slouží k určení nástroje .NET Core pro instalaci. V systému je k dispozici neoficiální seznam nástrojů [https://github.com/natemcmaster/dotnet-tools](https://github.com/natemcmaster/dotnet-tools) .

### <a name="additional-options"></a>Další možnosti

Další možnosti konfigurace mohou být předány jako hodnota `additionalOptions` . Tyto argumenty představují přímý průchod k argumentům použitým [`dotnet tool update`](/dotnet/core/tools/global-tools#update-a-tool) příkazem. 

`dotnet tool update`Příkaz slouží k bezpečnému zpracování případu, kde je nástroj již nainstalován.

### <a name="default-behavior"></a>Výchozí chování

Výchozím chováním `dotnet-toolinstall` nástroje je chyba, jak `input` je požadováno.

## <a name="example-usage"></a>Příklad použití

```json
{
    "$schema": "https://json.schemastore.org/devinit.schema-3.0",
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