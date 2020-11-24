---
title: dotnet-toolinstall
description: devinit nástroj dotnet – toolinstall.
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
ms.openlocfilehash: 343c66a0f1da955479993502cf5dcf967abe03b9
ms.sourcegitcommit: 02f14db142dce68d084dcb0a19ca41a16f5bccff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2020
ms.locfileid: "95440400"
---
# <a name="dotnet-toolinstall"></a>dotnet-toolinstall

Tento `dotnet-toolinstall` nástroj slouží k instalaci [nástrojů .NET Core](https://dotnet.microsoft.com/) pomocí `dotnet tool update` příkazu.

## <a name="usage"></a>Využití

Pokud `input` `additionalOptions` jsou vlastnosti i vynechány nebo jsou prázdné, nástroj bude postupovat podle [výchozího](#default-behavior) chování popsané níže.

| Název                                             | Typ   | Vyžadováno | Hodnota                                                                 |
|--------------------------------------------------|--------|----------|-----------------------------------------------------------------------|
| **vyjádření**                                     | řetězec | No       | Volitelná vlastnost komentářů Nepoužívá se.                                 |
| [**vstup**](#input)                              | řetězec | Ano      | Nástroj .NET Core, který se má nainstalovat Podrobnosti najdete níže v části o [zadání](#input) . |
| [**additionalOptions**](#additional-options)     | řetězec | No       | Podrobnosti najdete níže v části [Další možnosti](#additional-options) .      |

### <a name="input"></a>Vstup

Tato `input` vlastnost slouží k určení nástroje .NET Core pro instalaci. V systému je k dispozici neoficiální seznam nástrojů [https://github.com/natemcmaster/dotnet-tools](https://github.com/natemcmaster/dotnet-tools) .

### <a name="additional-options"></a>Další možnosti

Další možnosti konfigurace mohou být předány jako hodnota `additionalOptions` . Tyto argumenty představují přímý průchod k argumentům použitým [`dotnet tool update`](/dotnet/core/tools/global-tools#update-a-tool) příkazem.

`dotnet tool update`Příkaz slouží k bezpečnému zpracování případu, kde je nástroj již nainstalován.

### <a name="default-behavior"></a>Výchozí chování

Výchozím chováním `dotnet-toolinstall` nástroje je chyba, jak `input` je požadováno.

## <a name="example-usage"></a>Příklad použití
Níže jsou uvedeny příklady, jak spustit `dotnet-toolinstall` pomocí `.devinit.json` .

#### <a name="devinitjson-that-will-install-the-dotnet-trace-tool"></a>.devinit.js, na které se nainstaluje nástroj dotnet-Trace Tool:
```json
{
    "$schema": "https://json.schemastore.org/devinit.schema-3.0",
    "run": [
        {
            "tool": "dotnet-toolinstall",
            "input": "dotnet-trace"
        }
    ]
}
```

#### <a name="devinitjson-that-will-install-the-dotnet-trace-tool-as-a-global-tool"></a>.devinit.js, na které se nainstaluje nástroj dotnet-Trace Tool jako globální nástroj:
```json
{
    "$schema": "https://json.schemastore.org/devinit.schema-3.0",
    "run": [
        {
            "tool": "dotnet-toolinstall",
            "input": "dotnet-trace",
            "additionalOptions": "--global"
        }
    ]
}
```