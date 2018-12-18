---
title: 'Postupy: odkaz sadu SDK projektu MSBuild | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 01/25/2018
ms.technology: msbuild
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, SDKs, SDK
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: abc61f0e07ed1e22d0ec3b2c8fb15d66c9eea3cd
ms.sourcegitcommit: d462dd10746624ad139f1db04edd501e7737d51e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/29/2018
ms.locfileid: "50220441"
---
# <a name="how-to-use-msbuild-project-sdks"></a>Postupy: projektu MSBuild pomocí sady SDK

[!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] 15.0 představil nový koncept "Projekt SDK", což zjednodušuje pomocí sad SDK, které vyžadují vlastností a cílů, které se mají naimportovat.

```xml
<Project Sdk="Microsoft.NET.Sdk">
    <PropertyGroup>
        <TargetFramework>net46</TargetFramework>
    </PropertyGroup>
</Project>
```

Během vyhodnocování projektu [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] přidává implicitní importy v horní a dolní části vašeho projektu:

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

## <a name="reference-a-project-sdk"></a>Odkazovat na sadu SDK projektu

 Existují tři způsoby, jak odkazovat na sadu SDK projektu:

1. Použití `Sdk` atribut na `<Project/>` element:

    ```xml
    <Project Sdk="My.Custom.Sdk">
        ...
    </Project>
    ```

    Implicitní import se přidá do horní a dolní část projektu, jak je popsáno výše.  Formát `Sdk` atribut je `Name[/Version]` kde verze je nepovinná.  Například můžete zadat `My.Custom.Sdk/1.2.3`.

    > [!NOTE]
    > Toto je momentálně jediný podporovaný způsob, jak odkazovat na projekt SDK v sadě Visual Studio pro Mac.

2. Použít na nejvyšší úrovni `<Sdk/>` element:

    ```xml
    <Project>
        <Sdk Name="My.Custom.Sdk" Version="1.2.3" />
        ...
    </Project>
   ```

   Implicitní import se přidá do horní a dolní část projektu, jak je popsáno výše.  `Version` Atribut se nevyžaduje.

3. Použití `<Import/>` element kdekoli ve vašem projektu:

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

   Explicitně zahrnutí importů do projektu umožňuje plnou kontrolu nad pořadí.

   Při použití `<Import/>` element, můžete zadat volitelný `Version` atributem také.  Například můžete zadat `<Import Project="Sdk.props" Sdk="My.Custom.Sdk" Version="1.2.3" />`.

## <a name="how-project-sdks-are-resolved"></a>Způsob řešení projekt sady SDK

Při vyhodnocování importu [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] dynamicky přeloží cestu k projektu sadu SDK na základě názvu a verze, které jste zadali.  [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] obsahuje také seznam registrovaných překladačů sady SDK, které jsou moduly plug-in, které se najít projekt sady SDK na svém počítači.  Tyto moduly plug-in patří:

1. Překladač založená na Nugetu, který se dotazuje nakonfigurované balíček informační kanály pro balíčky NuGet, které odpovídají ID a verzi sady SDK, které jste zadali.<br/>
   Tento překladač je aktivní, pouze pokud jste zadali volitelné verze a můžou používat pro všechny vlastní sadu SDK projektu.  
2. Překladač .NET CLI, který se přeloží sad SDK, které se instalují s .NET CLI.<br/>
   Tento překladač vyhledá sady SDK projektu jako `Microsoft.NET.Sdk` a `Microsoft.NET.Sdk.Web` které jsou součástí produktu.
3. Výchozí překladač, který se přeloží sad SDK, které byly nainstalovány s nástrojem MSBuild.

Překladač založená na Nugetu SDK podporuje určení verze ve vaší [global.json](https://docs.microsoft.com/dotnet/core/tools/global-json) , který umožňuje řízení verze sady SDK projektu na jednom místě, nikoli v každý projekt:

```json
{
    "msbuild-sdks": {
        "My.Custom.Sdk": "5.0.0",
        "My.Other.Sdk": "1.0.0-beta"
    }
}
```

Během sestavení lze použít pouze jednu verzi každého projektu sady SDK.  Pokud odkazujete na dvě různé verze stejného projektu sadu SDK, nástroj MSBuild vygeneruje upozornění.  Doporučuje se **není** určit verzi ve vašich projektech, pokud je zadán s verzí v vaše *global.json*.  

## <a name="see-also"></a>Viz také:

 [Koncepty nástroje MSBuild](../msbuild/msbuild-concepts.md)   
 [Přizpůsobení sestavení](../msbuild/customize-your-build.md)   
 [Balíčky, metadata a architektur](/dotnet/core/packages)   
 [Dodatky k formátu csproj pro .NET Core](/dotnet/core/tools/csproj)
