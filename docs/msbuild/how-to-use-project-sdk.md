---
title: 'Postup: Odkaz na sadu MSBuild Project SDK | Dokumenty společnosti Microsoft'
ms.date: 01/25/2018
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, SDKs, SDK
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 74ccc29417cdee7a9f93c39509c0f7d06a5c72ff
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "76826468"
---
# <a name="how-to-use-msbuild-project-sdks"></a>Postup: Použití sad SDK projektu MSBuild

MSBuild 15.0 představil koncept "projektu SDK", který zjednodušuje používání sad pro vývoj softwaru, které vyžadují vlastnosti a cíle, které mají být importovány.

```xml
<Project Sdk="Microsoft.NET.Sdk">
    <PropertyGroup>
        <TargetFramework>net46</TargetFramework>
    </PropertyGroup>
</Project>
```

Během hodnocení projektu MSBuild přidá implicitní importy v horní a dolní části souboru projektu:

```xml
<Project>
    <!-- Implicit top import -->
    <Import Project="Sdk.props" Sdk="Microsoft.NET.Sdk" />

    <PropertyGroup>
        <TargetFramework>net46</TargetFramework>
    </PropertyGroup>

    <!-- Implicit bottom import -->
    <Import Project="Sdk.targets" Sdk="Microsoft.NET.Sdk" />
</Project>
```

## <a name="reference-a-project-sdk"></a>Odkaz na projekt SDK

Existují tři způsoby, jak odkazovat na projekt SDK:

- Použijte `Sdk` atribut na `<Project/>` prvek:

    ```xml
    <Project Sdk="My.Custom.Sdk">
        ...
    </Project>
    ```

    Implicitní import je přidán do horní a dolní části projektu, jak bylo popsáno dříve.
    
    Chcete-li určit konkrétní verzi sady SDK, `Sdk` přidejte ji k atributu:

    ```xml
    <Project Sdk="My.Custom.Sdk/1.2.3">
        ...
    </Project>
    ```

    > [!NOTE]
    > Toto je v současné době jediný podporovaný způsob, jak odkazovat na projekt SDK v Sadě Visual Studio pro Mac.

- Použijte prvek nejvyšší `<Sdk/>` úrovně:

    ```xml
    <Project>
        <Sdk Name="My.Custom.Sdk" Version="1.2.3" />
        ...
    </Project>
   ```

   Implicitní import je přidán do horní a dolní části projektu, jak bylo popsáno dříve.
   
   Atribut `Version` není povinný.

- Použijte `<Import/>` prvek kdekoli v projektu:

    ```xml
    <Project>
        <PropertyGroup>
            <MyProperty>Value</MyProperty>
        </PropertyGroup>
        <Import Project="Sdk.props" Sdk="My.Custom.Sdk" />
        ...
        <Import Project="Sdk.targets" Sdk="My.Custom.Sdk" />
    </Project>
   ```

   Explicitní zahrnutí importů v projektu umožňuje plnou kontrolu nad objednávkou.

   Při použití `<Import/>` prvku můžete také `Version` zadat volitelný atribut. Můžete například zadat `<Import Project="Sdk.props" Sdk="My.Custom.Sdk" Version="1.2.3" />`.

## <a name="how-project-sdks-are-resolved"></a>Jak jsou sady SDK projektu vyřešeny

Při vyhodnocování importu MSBuild dynamicky řeší cestu k projektu SDK na základě zadaného názvu a verze.  MSBuild má také seznam registrovaných překladačů sady SDK, což jsou moduly plug-in, které vyhledávají sady SDK projektu v počítači. Tyto moduly plug-in zahrnují:

- Překládání založené na NuGet, který dotazuje nakonfigurované kanály balíčků pro balíčky NuGet, které odpovídají ID a verzi sady SDK, kterou jste zadali.

   Tento překladač je aktivní pouze v případě, že jste zadali volitelnou verzi. Lze jej použít pro libovolný vlastní projekt SDK.
   
- Překládání rozhraní .NET CLI, který řeší sady SDK nainstalované pomocí [rozhraní .NET CLI](/dotnet/core/tools/).

   Tento překladač vyhledá sady SDK projektu, jako `Microsoft.NET.Sdk` je například a `Microsoft.NET.Sdk.Web` které jsou součástí produktu.
   
- Výchozí překladač, který řeší sady SDK, které byly nainstalovány pomocí sady MSBuild.

Překládání sady SDK založené na NuGet podporuje určení verze v souboru [global.json,](/dotnet/core/tools/global-json) který umožňuje řídit verzi sady SDK projektu na jednom místě, nikoli v každém jednotlivém projektu:

```json
{
    "msbuild-sdks": {
        "My.Custom.Sdk": "5.0.0",
        "My.Other.Sdk": "1.0.0-beta"
    }
}
```

Během sestavení lze použít pouze jednu verzi každé sady SDK projektu. Pokud odkazujete na dvě různé verze stejnésady SDK projektu, msbuild vydává upozornění. Pokud je v souboru *global.json* zadána verze v projektech, doporučujeme **nezadávat** verzi v projektech.

## <a name="see-also"></a>Viz také

- [Koncepty MSBuild](../msbuild/msbuild-concepts.md)
- [Přizpůsobení sestavení](../msbuild/customize-your-build.md)
- [Balíčky, metadata a architektury](/dotnet/core/packages)
- [Dodatky k formátu csproj pro .NET Core](/dotnet/core/tools/csproj)
