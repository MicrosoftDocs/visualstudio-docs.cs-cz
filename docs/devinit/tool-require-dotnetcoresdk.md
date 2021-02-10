---
title: require-dotnetcoresdk
description: devinit Tool vyžaduje – dotnetcoresdk.
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
ms.openlocfilehash: 8f96566242e940f5a36f3d6ab62cd8e08ec9b7ac
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99934340"
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
Níže jsou uvedeny příklady, jak spustit `require-dotnetcoresdk` pomocí `.devinit.json` .

#### <a name="devinitjson-that-will-install-the-latest-version-of-net-core"></a>.devinit.js, které budou instalovat nejnovější verzi rozhraní .NET Core:
```json
{
    "$schema": "https://json.schemastore.org/devinit.schema-3.0",
    "run": [
        {
            "tool": "require-dotnetcoresdk"
        }
    ]
}
```

#### <a name="devinitjson-that-will-install-a-specific-version-of-net-core"></a>.devinit.js, který nainstaluje konkrétní verzi .NET Core:
```json
{
    "$schema": "https://json.schemastore.org/devinit.schema-3.0",
    "run": [
        {
            "tool": "require-dotnetcoresdk",
            "input": "3.0.0"
        }
    ]
}
```

#### <a name="devinitjson-that-will-install-a-specific-version-of-net-core-and-aspnet-core"></a>.devinit.js, na které se nainstaluje konkrétní verze .NET Core a ASP.NET Core:
```json
{
    "$schema": "https://json.schemastore.org/devinit.schema-3.0",
    "run": [
        {
            "tool": "require-dotnetcoresdk",
            "input": "3.0.0",
            "additionalOptions": "-Runtime aspnetcore"
        }
    ]
}
```

#### <a name="devinitjson-that-will-install-net-core-in-a-specific-directory"></a>.devinit.js, který nainstaluje .NET Core do konkrétního adresáře:
```json
{
    "$schema": "https://json.schemastore.org/devinit.schema-3.0",
    "run": [
        {
            "tool": "require-dotnetcoresdk",
            "additionalOptions": "-InstallDir \"C:\\Program Files\\dotnet\""
        }
    ]
}
```