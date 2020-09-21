---
title: vyžadovat – dotnetcoresdk
description: devinit Tool vyžaduje – dotnetcoresdk.
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
ms.openlocfilehash: cf68889b9dbac39031a4a79fbe799dc02fc8e419
ms.sourcegitcommit: 566144d59c376474c09bbb55164c01d70f4b621c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2020
ms.locfileid: "90809691"
---
# <a name="require-dotnetcoresdk"></a>vyžadovat – dotnetcoresdk

Tento `require-dotnetcoresdk` nástroj slouží k instalaci [.NET Core SDK](https://dotnet.microsoft.com/) a sdíleného modulu runtime prostřednictvím skriptu [dotnet-Install](https://docs.microsoft.com/dotnet/core/tools/dotnet-install-script) .

## <a name="usage"></a>Využití

Pokud `input` `additionalOptions` jsou vlastnosti i vynechány nebo jsou prázdné, nástroj bude postupovat podle [výchozího](#default-behavior) chování popsané níže.

| Název                                             | Typ   | Vyžadováno | Hodnota                                                                               |
|--------------------------------------------------|--------|----------|-------------------------------------------------------------------------------------|
| **vyjádření**                                     | řetězec | No       | Volitelná vlastnost komentářů Nepoužívá se.                                               |
| [**vstup**](#input)                              | řetězec | No       | Verze .NET Core SDK, která se má nainstalovat Podrobnosti najdete níže v části o [zadání](#input) . |
| [**additionalOptions**](#additional-options)     | řetězec | No       | Podrobnosti najdete níže v části [Další možnosti](#additional-options) .                    |

### <a name="input"></a>Vstup

Tato `input` vlastnost slouží k určení verze .NET Core SDK k instalaci. Seznam verzí najdete v [lokalitě dotnet-Core](https://dotnet.microsoft.com/download/dotnet-core).

### <a name="additional-options"></a>Další možnosti

Další možnosti konfigurace mohou být předány jako hodnota `additionalOptions` . Tyto argumenty představují přímý průchod k argumentům použitým v příkazu [dotnet-Install](https://docs.microsoft.com/dotnet/core/tools/dotnet-install-script) Script. Další informace o dostupných parametrech naleznete v [dokumentaci](https://docs.microsoft.com/dotnet/core/tools/dotnet-install-script) k příkazu [dotnet-Install](https://docs.microsoft.com/dotnet/core/tools/dotnet-install-script) Script. Při použití nástroje `additionalOptions` se ujistěte, že používáte názvy a formát argumentů PowerShellu.

Poznámka: jakákoli další hodnota argumentu obsahujícího mezera musí zahrnovat další dvojici řídicích uvozovek (pomocí zpětného lomítka). Příklad můžete zobrazit v [příkladu](#example-usage) použití pomocí `-InstallDir` .

### <a name="default-behavior"></a>Výchozí chování

Výchozím chováním `require-dotnetcoresdk` nástroje je instalace verze .NET Core SDK uvedená v `global.json` souboru [(dokumentace)](https://docs.microsoft.com/dotnet/core/tools/global-json?tabs=netcore3x) v aktuálním pracovním adresáři. Pokud `global.json` se nenajde žádný soubor, `require-dotnetcoresdk` nainstaluje nejnovější aktuální verzi .NET Core SDK a sdíleného modulu runtime.

## <a name="example-usage"></a>Příklad použití

```json
{
    "$schema": "https://json.schemastore.org/devinit.schema-2.0",
    "run": [
        {
            "comments": "Example that will trigger the Default behavior of installing latest or, if present, the SDK version from a global.json file.",
            "tool": "require-dotnetcoresdk"
        },
        {
            "comments": "Example that will install a specific version.",
            "tool": "require-dotnetcoresdk",
            "input": "3.0.0"
        },
        {
            "comments": "Example that will install a specific version and the aspnetcore runtime.",
            "tool": "require-dotnetcoresdk",
            "input": "3.0.0",
            "additionalOptions": "-Runtime aspnetcore"
        },
        {
            "comments": "Example that will install in a specific directory.",
            "tool": "require-dotnetcoresdk",
            "additionalOptions": "-InstallDir \"C:\Program Files\dotnet\""
        }
    ]
}
```
