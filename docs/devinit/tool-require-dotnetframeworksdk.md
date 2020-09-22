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
ms.openlocfilehash: 4de8daf4b57d4775e4f1ede57392bb594bae53ea
ms.sourcegitcommit: 09d1f5cef5360cdc1cdfd4b22a1a426b38079618
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/22/2020
ms.locfileid: "91005108"
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

```json
{
    "$schema": "https://json.schemastore.org/devinit.schema-2.0",
    "run": [
        {
            "comments": "Example that will install a specific version of the .NET Framework SDK.",
            "tool": "require-dotnetframeworksdk",
            "input": "4.8.0"
        },
        {
            "comments": "Example that will install the latest version of the .NET Framework SDK.",
            "tool": "require-dotnetframeworksdk"
        }
    ]
}
```
