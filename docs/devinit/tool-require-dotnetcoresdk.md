---
title: require-dotnetcoresdk
description: devinit Tool vyžaduje – dotnetcoresdk.
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
ms.openlocfilehash: 5c5b68b663d6ee4cd0294aa77bd89c2e778f8d2b
ms.sourcegitcommit: f4b49f1fc50ffcb39c6b87e2716b4dc7085c7fb5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/05/2020
ms.locfileid: "93399604"
---
# <a name="require-dotnetcoresdk"></a>require-dotnetcoresdk

Tento `require-dotnetcoresdk` nástroj slouží k instalaci [.NET Core SDK](https://dotnet.microsoft.com/) a sdíleného modulu runtime prostřednictvím skriptu [dotnet-Install](/dotnet/core/tools/dotnet-install-script) .

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

Další možnosti konfigurace mohou být předány jako hodnota `additionalOptions` . Tyto argumenty představují přímý průchod k argumentům použitým v příkazu [dotnet-Install](/dotnet/core/tools/dotnet-install-script) Script. Další informace o dostupných parametrech naleznete v [dokumentaci](/dotnet/core/tools/dotnet-install-script) k příkazu [dotnet-Install](/dotnet/core/tools/dotnet-install-script) Script. Při použití nástroje `additionalOptions` se ujistěte, že používáte názvy a formát argumentů PowerShellu.

> [!NOTE]
> Jakákoli další hodnota argumentu obsahujícího mezera musí zahrnovat další dvojici řídicích uvozovek (pomocí zpětného lomítka). Příklad můžete zobrazit v [příkladu](#example-usage) použití pomocí `-InstallDir` .

### <a name="default-behavior"></a>Výchozí chování

Výchozím chováním `require-dotnetcoresdk` nástroje je instalace verze .NET Core SDK uvedená v `global.json` souboru [(dokumentace)](/dotnet/core/tools/global-json?tabs=netcore3x) v aktuálním pracovním adresáři. Pokud `global.json` se nenajde žádný soubor, `require-dotnetcoresdk` nainstaluje nejnovější aktuální verzi .NET Core SDK a sdíleného modulu runtime.

## <a name="example-usage"></a>Příklad použití

```json
{
    "$schema": "https://json.schemastore.org/devinit.schema-3.0",
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
            "additionalOptions": "-InstallDir \"C:\\Program Files\\dotnet\""
        }
    ]
}
```