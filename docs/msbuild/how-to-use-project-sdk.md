---
title: 'Postupy: odkazování na sadu SDK projektu MSBuild | Microsoft Docs'
ms.date: 01/25/2018
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, SDKs, SDK
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 0be8f9ed17bf4474307a639bb75f409da2ff1638
ms.sourcegitcommit: 257fc60eb01fefafa9185fca28727ded81b8bca9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/25/2019
ms.locfileid: "72911297"
---
# <a name="how-to-use-msbuild-project-sdks"></a>Postupy: použití sad SDK projektů MSBuild

[!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] 15,0 představil koncept "projektové sady SDK", který zjednodušuje používání sad pro vývoj softwaru, které vyžadují Import vlastností a cílů.

```xml
<Project Sdk="Microsoft.NET.Sdk">
    <PropertyGroup>
        <TargetFramework>net46</TargetFramework>
    </PropertyGroup>
</Project>
```

Během hodnocení projektu [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] přidá implicitní importy v horní a dolní části projektu:

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

## <a name="reference-a-project-sdk"></a>Odkaz na sadu SDK projektu

 Existují tři způsoby, jak odkazovat na sadu SDK projektu:

1. Použijte atribut `Sdk` u elementu `<Project/>`:

    ```xml
    <Project Sdk="My.Custom.Sdk">
        ...
    </Project>
    ```

    Do horní a dolní části projektu se přidá implicitní import, jak je popsáno výše.
    
    K určení konkrétní verze sady SDK ji můžete připojit k atributu `Sdk`:

    ```xml
    <Project Sdk="My.Custom.Sdk/1.2.3">
        ...
    </Project>
    ```

    > [!NOTE]
    > Toto je momentálně jediný podporovaný způsob, jak odkazovat na sadu SDK projektu v Visual Studio pro Mac.

2. Použijte `<Sdk/>` element nejvyšší úrovně:

    ```xml
    <Project>
        <Sdk Name="My.Custom.Sdk" Version="1.2.3" />
        ...
    </Project>
   ```

   Do horní a dolní části projektu se přidá implicitní import, jak je popsáno výše.  Atribut `Version` není povinný.

3. Použijte `<Import/>` element kdekoli v projektu:

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

   Explicitní zahrnutí importů do projektu vám umožní plnou kontrolu nad objednávkou.

   Při použití prvku `<Import/>` můžete zadat také volitelný atribut `Version`.  Můžete například zadat `<Import Project="Sdk.props" Sdk="My.Custom.Sdk" Version="1.2.3" />`.

## <a name="how-project-sdks-are-resolved"></a>Jak se řeší sady SDK projektu

Při vyhodnocování importu [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] dynamicky vyřeší cestu k projektové sadě SDK na základě názvu a verze, kterou jste zadali.  [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] taky obsahuje seznam registrovaných překladačů SDK, které jsou moduly plug-in, které na vašem počítači hledají sady Project SDK.  Mezi tyto moduly plug-in patří:

1. Překladač založený na NuGetu, který se dotazuje na vaše nakonfigurované kanály balíčků pro balíčky NuGet, které odpovídají ID a verzi sady SDK, kterou jste určili.<br/>
   Tento překladač je aktivní pouze v případě, že jste zadali volitelnou verzi a je možné ji použít pro vlastní projektové sady SDK.
2. Překladač rozhraní .NET CLI, který řeší sady SDK, které jsou nainstalovány s rozhraním .NET CLI.<br/>
   Tento překladač vyhledá sady SDK projektu, například `Microsoft.NET.Sdk` a `Microsoft.NET.Sdk.Web`, které jsou součástí produktu.
3. Výchozí překladač, který řeší sady SDK, které byly nainstalovány s nástrojem MSBuild.

Překladač SDK na základě NuGet podporuje určení verze v [globálním formátu. JSON](/dotnet/core/tools/global-json) , který umožňuje řídit verzi SDK projektu na jednom místě, a ne v jednotlivých projektech:

```json
{
    "msbuild-sdks": {
        "My.Custom.Sdk": "5.0.0",
        "My.Other.Sdk": "1.0.0-beta"
    }
}
```

Během sestavení lze použít pouze jednu verzi sady SDK projektu.  Pokud odkazujete na dvě různé verze stejné projektové sady SDK, nástroj MSBuild vygeneruje upozornění.  Pokud je ve vašem *globálním formátu. JSON*zadaná verze, **doporučuje se v projektech nespecifikovat** verze.

## <a name="see-also"></a>Viz také:

- [Koncepty nástroje MSBuild](../msbuild/msbuild-concepts.md)
- [Přizpůsobení sestavení](../msbuild/customize-your-build.md)
- [Balíčky, metadata a rozhraní](/dotnet/core/packages)
- [Přidání do formátu csproj pro .NET Core](/dotnet/core/tools/csproj)
