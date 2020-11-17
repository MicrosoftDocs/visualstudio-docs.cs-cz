---
title: require-dotnetframeworksdk
description: devinit Tool vyžaduje – dotnetframeworksdk.
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
ms.openlocfilehash: a74f45d67c6f2a921d8c5a06bc60abf6f5c76cb9
ms.sourcegitcommit: 3d96f7a8c9affab40358c3e81e3472db31d841b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/17/2020
ms.locfileid: "94671792"
---
# <a name="require-dotnetframeworksdk"></a>require-dotnetframeworksdk

Tento `require-dotnetframeworksdk` nástroj slouží k instalaci [sady .NET Framework SDK](https://dotnet.microsoft.com/) prostřednictvím [poskytnutých instalačních programů](https://dotnet.microsoft.com/download/visual-studio-sdks).

## <a name="usage"></a>Využití

Pokud `input` `additionalOptions` jsou vlastnosti i vynechány nebo jsou prázdné, nástroj bude postupovat podle [výchozího](#default-behavior) chování popsané níže.

| Název                                             | Typ   | Vyžadováno  | Hodnota                                                                                    |
|--------------------------------------------------|--------|-----------|------------------------------------------------------------------------------------------|
| **vyjádření**                                     | řetězec | No        | Volitelná vlastnost komentářů Nepoužívá se.                                                    |
| [**vstup**](#input)                              | řetězec | No        | Verze sady .NET Framework SDK, která se má nainstalovat Podrobnosti najdete níže v části o [zadání](#input) . |
| [**additionalOptions**](#additional-options)     | řetězec | No        | Nepoužívá se. Podrobnosti najdete níže v části [Další možnosti](#additional-options) .               |

### <a name="input"></a>Vstup

Tato `input` vlastnost slouží k určení verze sady .NET Framework SDK, která se má nainstalovat. Seznam verzí najdete na [webu DotNET-Framework](https://dotnet.microsoft.com/download/visual-studio-sdks).

### <a name="additional-options"></a>Další možnosti

Nepoužívá se.

### <a name="default-behavior"></a>Výchozí chování

Výchozím chováním `require-dotnetframeworksdk` nástroje je instalace nejnovější verze. Podívejte se na [poskytnuté instalační programy](https://dotnet.microsoft.com/download/visual-studio-sdks) pro nejnovější verzi.

## <a name="example-usage"></a>Příklad použití
Níže jsou uvedeny příklady, jak spustit `require-dotnetframeworksdk` pomocí `.devinit.json` . 

#### <a name="devinitjson-that-will-install-the-latest-net-framework"></a>.devinit.js, které budou instalovat nejnovější .NET Framework:
```json
{
    "$schema": "https://json.schemastore.org/devinit.schema-3.0",
    "run": [
        {
            "tool": "require-dotnetframeworksdk"
        }
    ]
}
```

#### <a name="devinitjson-that-will-install-a-specific-version-of-the-net-framework"></a>.devinit.js, na které se nainstaluje konkrétní verze .NET Framework:
```json
{
    "$schema": "https://json.schemastore.org/devinit.schema-3.0",
    "run": [
        {
            "tool": "require-dotnetframeworksdk",
            "input": "4.8.0"
        }
    ]
}
```