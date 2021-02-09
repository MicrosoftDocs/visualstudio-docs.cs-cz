---
title: 'Postupy: odkazování na sadu SDK projektu MSBuild | Microsoft Docs'
description: Naučte se používat sady SDK projektů MSBuild ke zjednodušení používání sad pro vývoj softwaru, které vyžadují Import vlastností a cílů.
ms.custom: SEO-VS-2020
ms.date: 01/25/2018
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, SDKs, SDK
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: e6303efce016a9e678e4c9e8aa62c91aa116e44f
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99914216"
---
# <a name="how-to-use-msbuild-project-sdks"></a>Postupy: použití sad SDK projektů MSBuild

MSBuild 15,0 představil koncept "projektové sady SDK", který zjednodušuje používání sad pro vývoj softwaru, které vyžadují Import vlastností a cílů.

```xml
<Project Sdk="Microsoft.NET.Sdk">
    <PropertyGroup>
        <TargetFramework>net46</TargetFramework>
    </PropertyGroup>
</Project>
```

Během hodnocení projektu nástroj MSBuild přidá implicitní importy v horní a dolní části souboru projektu:

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

- Použijte `Sdk` atribut pro `<Project/>` element:

    ```xml
    <Project Sdk="My.Custom.Sdk">
        ...
    </Project>
    ```

    Do horní a dolní části projektu se přidá implicitní import, jak je popsáno výše.
    
    Chcete-li zadat konkrétní verzi sady SDK, přidejte ji do `Sdk` atributu:

    ```xml
    <Project Sdk="My.Custom.Sdk/1.2.3">
        ...
    </Project>
    ```

- Použijte element nejvyšší úrovně `<Sdk/>` :

    ```xml
    <Project>
        <Sdk Name="My.Custom.Sdk" Version="1.2.3" />
        ...
    </Project>
   ```

   Do horní a dolní části projektu se přidá implicitní import, jak je popsáno výše.
   
   `Version`Atribut není povinný.

- Použijte `<Import/>` element kdekoli v projektu:

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

   Při použití `<Import/>` elementu můžete zadat `Version` také volitelný atribut. Můžete například zadat `<Import Project="Sdk.props" Sdk="My.Custom.Sdk" Version="1.2.3" />` .

## <a name="how-project-sdks-are-resolved"></a>Jak se řeší sady SDK projektu

Při vyhodnocování importu nástroj MSBuild dynamicky vyřeší cestu k projektové sadě SDK na základě názvu a verze, kterou jste zadali.  Nástroj MSBuild obsahuje také seznam registrovaných překladačů sady SDK, které jsou moduly plug-in, které na vašem počítači hledají sady SDK projektu. Mezi tyto moduly plug-in patří:

- Překladač založený na NuGetu, který se dotazuje na vaše nakonfigurované kanály balíčků pro balíčky NuGet, které odpovídají ID a verzi sady SDK, kterou jste určili.

   Tento překladač je aktivní pouze v případě, že jste zadali volitelnou verzi. Dá se použít pro libovolnou vlastní sadu SDK projektu.
   
- Překladač sady .NET SDK, který řeší sady MSBuild SDK, které jsou nainstalovány se sadou [.NET SDK](/dotnet/core/sdk/).

   Tento překladač vyhledá sady SDK projektu, například `Microsoft.NET.Sdk` a `Microsoft.NET.Sdk.Web` , které jsou součástí produktu.
   
- Výchozí překladač, který řeší sady SDK, které byly nainstalovány s nástrojem MSBuild.

Překladač SDK na základě NuGet podporuje určení verze v [global.js](/dotnet/core/tools/global-json) souboru, což vám umožní řídit verzi sady SDK projektu na jednom místě, a ne v jednotlivých projektech:

```json
{
    "msbuild-sdks": {
        "My.Custom.Sdk": "5.0.0",
        "My.Other.Sdk": "1.0.0-beta"
    }
}
```

Během sestavení lze použít pouze jednu verzi sady SDK projektu. Pokud odkazujete na dvě různé verze stejné projektové sady SDK, nástroj MSBuild vygeneruje upozornění. Doporučuje **se, abyste v** projektech neurčili verzi, pokud je v souboru *global.js* .

## <a name="see-also"></a>Viz také

- [Koncepty nástroje MSBuild](../msbuild/msbuild-concepts.md)
- [Přizpůsobení sestavení](../msbuild/customize-your-build.md)
- [Balíčky, metadata a rozhraní](/dotnet/core/packages)
- [Přidání do formátu csproj pro .NET Core](/dotnet/core/tools/csproj)
