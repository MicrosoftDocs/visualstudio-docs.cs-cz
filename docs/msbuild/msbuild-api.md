---
title: Rozhraní API pro MSBuild | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e87ee95c4027d0513c78d3ce0386cf31d47baf94
ms.sourcegitcommit: e38419bb842d587fd9e37c24b6cf3fc5c2e74817
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/09/2020
ms.locfileid: "91862689"
---
# <a name="use-the-msbuild-api"></a>Použití rozhraní API pro MSBuild

Nástroj MSBuild poskytuje veřejnou plochu rozhraní API, aby mohl program provádět sestavení a kontrolovat projekty. Poslední verze rozhraní API nástroje MSBuild najdete v následujících balíčcích NuGet:

| Název balíčku | Popis |
| ------------ | ----------- |
| [Microsoft. Build](https://www.nuget.org/packages/Microsoft.Build) | Obsahuje sestavení Microsoft. Build, které slouží k vytváření, úpravám a vyhodnocení projektů MSBuild.|
| [Microsoft. Build. Framework](https://www.nuget.org/packages/Microsoft.Build.Framework)| Obsahuje společné sestavení rozhraní MSBuild používané jinými sestaveními nástroje MSBuild. |
| [Microsoft. Build. Runtime](https://www.nuget.org/packages/Microsoft.Build.Runtime) | Doručí úplnou spustitelnou kopii nástroje MSBuild. Odkazujte na tento balíček pouze v případě, že vaše aplikace potřebuje načíst projekty nebo spustit sestavení v procesu bez nutnosti instalace nástroje MSBuild. Úspěšné vyhodnocení projektů pomocí tohoto balíčku vyžaduje agregaci dalších komponent (jako jsou kompilátory) do adresáře aplikace. |
| [Microsoft. Build. Tasks. Core](https://www.nuget.org/packages/Microsoft.Build.Tasks.Core) | Obsahuje sestavení Microsoft. Build. Tasks, které implementuje běžně používané úlohy nástroje MSBuild. |
| [Microsoft. Build. Utilities. Core](https://www.nuget.org/packages/Microsoft.Build.Utilities.Core) | Obsahuje sestavení Microsoft. Build. Utilities, které se používá k implementaci vlastních úloh MSBuild. |

Kromě toho NuGet hostuje také starší sestavení, [Microsoft. Build. Engine](https://www.nuget.org/packages/Microsoft.Build.Engine), který je zastaralý.

Existuje několik různých verzí rozhraní API nástroje MSBuild a pro verze 15 a 16 existují dvě různé formy sestavení v balíčcích NuGet, jeden kompilovaný s .NET Framework a další kompilováno s rozhraním .NET Core, které je podmnožinou .NET Frameworkho rozhraní API.  Verze nástroje MSBuild pro .NET Core se používá při vyvolání `dotnet` příkazu a při použití nástroje MSBuild v systémech Mac a Linux.

Dokumentaci k rozhraní MSBuild API najdete v [prohlížeči rozhraní .NET API](/dotnet/api), nebo procházením oborů názvů v následujícím seznamu.

::: moniker range="vs-2017"
| Obor názvů | Platí pro | Popis |
|-----------| -----------| ----------- |
| [Microsoft. Build. konstrukcí](/dotnet/api/Microsoft.Build.Construction?view=msbuild-15&preserve-view=true) | Vše |  Obsahuje typy, které model objektu MSBuild používá pro konstrukci kořenů projektu s vyhodnocenými hodnotami. Každý kořen projektu odpovídá souboru projektu nebo cíle. |
| [Microsoft. Build. definition](/dotnet/api/Microsoft.Build.Definition?view=msbuild-15&preserve-view=true) | Vše | Obsahuje `ProjectOptions` třídu, která podporuje vytváření projektu. |
| [Microsoft. Build. Evaluation](/dotnet/api/Microsoft.Build.Evaluation?view=msbuild-15&preserve-view=true) | Vše | Obsahuje typy, které model objektu MSBuild používá pro vyhodnocení projektů. Každý projekt je přidružen k jedné nebo více kořenům projektu. |
| [Microsoft. Build. Evaluation. Context](/dotnet/api/Microsoft.Build.Evaluation.Context?view=msbuild-15&preserve-view=true) | Vše | Obsahuje `EvaluationContext` třídu, která se používá k uložení stavu vyhodnocení napříč voláními. |
| [Microsoft. Build. Exceptions](/dotnet/api/Microsoft.Build.Exceptions?view=msbuild-15&preserve-view=true) | Vše | Obsahuje typy výjimek, které mohou být vyvolány během procesu sestavení. |
| [Microsoft.Build.Execution](/dotnet/api/Microsoft.Build.Execution?view=msbuild-15&preserve-view=true) | Vše | Obsahuje typy, které objektový model MSBuild používá k sestavení projektů. |
| [Microsoft. Build. Framework](/dotnet/api/Microsoft.Build.Framework?view=msbuild-15&preserve-view=true) | Vše | Obsahuje typy, které definují, jak úlohy a protokolovací nástroje komunikují s modulem MSBuild.|
| [Microsoft. Build. Framework. Profiler](/dotnet/api/Microsoft.Build.Framework.Profiler?view=msbuild-15&preserve-view=true) | Vše | Obsahuje typy, které podporují profilování výkonu. |
| [Microsoft. Build. Framework. XamlTypes](/dotnet/api/Microsoft.Build.Framework.XamlTypes?view=msbuild-15&preserve-view=true) | Pouze .NET Framework | Obsahuje třídy používané pro reprezentaci typů XAML, které jsou analyzovány ze souborů, pravidel a dalších zdrojů. |
| [Microsoft. Build. expanze](/dotnet/api/Microsoft.Build.Globbing?view=msbuild-15&preserve-view=true) | Vše | Obsahuje třídy, které podporují zpracování zástupných znaků. |
| [Microsoft. Build. expanze. rozšíření](/dotnet/api/Microsoft.Build.Globbing.Extensions?view=msbuild-15&preserve-view=true) | Vše | Obsahuje typy, které podporují rozšíření pro zpracování zástupných znaků. |
| [Microsoft. Build. Graph](/dotnet/api/Microsoft.Build.Graph?view=msbuild-15&preserve-view=true) | Vše | Obsahuje typy, které podporují `-graph` přepínač MSBuild. |
| [Microsoft. Build. Logging](/dotnet/api/Microsoft.Build.Logging?view=msbuild-15&preserve-view=true) | Vše | Obsahuje typy používané pro protokolování průběhu sestavení. |
| [Microsoft. Build. ObjectModelRemoting](/dotnet/api/Microsoft.Build.ObjectModelRemoting?view=msbuild-15&preserve-view=true) | Vše | Obsahuje typy, které podporují vzdálenou komunikaci v nástroji MSBuild. |
| [Microsoft. Build. Tasks](/dotnet/api/Microsoft.Build.Tasks?view=msbuild-15&preserve-view=true) | Vše | Obsahuje implementaci všech úkolů dodávaných s nástrojem MSBuild. |
| [Microsoft. Build. Tasks. Deployment. zaváděcí nástroj](/dotnet/api/Microsoft.Build.Tasks.Deployment.Bootstrapper?view=msbuild-15&preserve-view=true) | Pouze .NET Framework | Obsahuje třídy používané interně nástrojem MSBuild. |
| [Microsoft. Build. Tasks. Deployment. ManifestUtilities](/dotnet/api/Microsoft.Build.Tasks.Deployment.ManifestUtilities?view=msbuild-15&preserve-view=true) | Pouze .NET Framework | Obsahuje třídy, které používá nástroj MSBuild.|
| [Microsoft. Build. Tasks. hosting](/dotnet/api/Microsoft.Build.Tasks.Hosting?view=msbuild-15&preserve-view=true) | Vše | Obsahuje třídy používané interně nástrojem MSBuild. |
| [Microsoft. Build. Tasks. XAML](/dotnet/api/Microsoft.Build.Tasks.Xaml?view=msbuild-15&preserve-view=true) | Pouze .NET Framework | Obsahuje třídy související s úlohami sestavení XAML. |
| [Microsoft. Build. Utilities](/dotnet/api/Microsoft.Build.Utilities?view=msbuild-15&preserve-view=true) | Vše | Obsahuje pomocné třídy, které lze použít k vytvoření vlastních protokolovacích nástrojů a úloh nástroje MSBuild.|
:::moniker-end
:::moniker range=">=vs-2019"
| Obor názvů | Platí pro | Popis |
|-----------| -----------| ----------- |
| [Microsoft. Build. konstrukcí](/dotnet/api/Microsoft.Build.Construction?view=msbuild-16&preserve-view=true) | Vše |  Obsahuje typy, které model objektu MSBuild používá pro konstrukci kořenů projektu s vyhodnocenými hodnotami. Každý kořen projektu odpovídá souboru projektu nebo cíle. |
| [Microsoft. Build. definition](/dotnet/api/Microsoft.Build.Definition?view=msbuild-16&preserve-view=true) | Vše | Obsahuje `ProjectOptions` třídu, která podporuje vytváření projektu. |
| [Microsoft. Build. Evaluation](/dotnet/api/Microsoft.Build.Evaluation?view=msbuild-16&preserve-view=true) | Vše | Obsahuje typy, které model objektu MSBuild používá pro vyhodnocení projektů. Každý projekt je přidružen k jedné nebo více kořenům projektu. |
| [Microsoft. Build. Evaluation. Context](/dotnet/api/Microsoft.Build.Evaluation.Context?view=msbuild-16&preserve-view=true) | Vše | Obsahuje `EvaluationContext` třídu, která se používá k uložení stavu vyhodnocení napříč voláními. |
| [Microsoft. Build. Exceptions](/dotnet/api/Microsoft.Build.Exceptions?view=msbuild-16&preserve-view=true) | Vše | Obsahuje typy výjimek, které mohou být vyvolány během procesu sestavení. |
| [Microsoft.Build.Execution](/dotnet/api/Microsoft.Build.Execution?view=msbuild-16&preserve-view=true) | Vše | Obsahuje typy, které objektový model MSBuild používá k sestavení projektů. |
| [Microsoft. Build. Framework](/dotnet/api/Microsoft.Build.Framework?view=msbuild-16&preserve-view=true) | Vše | Obsahuje typy, které definují, jak úlohy a protokolovací nástroje komunikují s modulem MSBuild.|
| [Microsoft. Build. Framework. Profiler](/dotnet/api/Microsoft.Build.Framework.Profiler?view=msbuild-16&preserve-view=true) | Vše | Obsahuje typy, které podporují profilování výkonu. |
| [Microsoft. Build. Framework. XamlTypes](/dotnet/api/Microsoft.Build.Framework.XamlTypes?view=msbuild-16&preserve-view=true) | Pouze .NET Framework | Obsahuje třídy používané pro reprezentaci typů XAML, které jsou analyzovány ze souborů, pravidel a dalších zdrojů. |
| [Microsoft. Build. expanze](/dotnet/api/Microsoft.Build.Globbing?view=msbuild-16&preserve-view=true) | Vše | Obsahuje třídy, které podporují zpracování zástupných znaků. |
| [Microsoft. Build. expanze. rozšíření](/dotnet/api/Microsoft.Build.Globbing.Extensions?view=msbuild-16&preserve-view=true) | Vše | Obsahuje typy, které podporují rozšíření pro zpracování zástupných znaků. |
| [Microsoft. Build. Graph](/dotnet/api/Microsoft.Build.Graph?view=msbuild-16&preserve-view=true) | Vše | Obsahuje typy, které podporují `-graph` přepínač MSBuild. |
| [Microsoft. Build. Logging](/dotnet/api/Microsoft.Build.Logging?view=msbuild-16&preserve-view=true) | Vše | Obsahuje typy používané pro protokolování průběhu sestavení. |
| [Microsoft. Build. ObjectModelRemoting](/dotnet/api/Microsoft.Build.ObjectModelRemoting?view=msbuild-16&preserve-view=true) | Vše | Obsahuje typy, které podporují vzdálenou komunikaci v nástroji MSBuild. |
| [Microsoft. Build. Tasks](/dotnet/api/Microsoft.Build.Tasks?view=msbuild-16&preserve-view=true) | Vše | Obsahuje implementaci všech úkolů dodávaných s nástrojem MSBuild. |
| [Microsoft. Build. Tasks. Deployment. zaváděcí nástroj](/dotnet/api/Microsoft.Build.Tasks.Deployment.Bootstrapper?view=msbuild-16&preserve-view=true) | Pouze .NET Framework | Obsahuje třídy používané interně nástrojem MSBuild. |
| [Microsoft. Build. Tasks. Deployment. ManifestUtilities](/dotnet/api/Microsoft.Build.Tasks.Deployment.ManifestUtilities?view=msbuild-16&preserve-view=true) | Pouze .NET Framework | Obsahuje třídy, které používá nástroj MSBuild.|
| [Microsoft. Build. Tasks. hosting](/dotnet/api/Microsoft.Build.Tasks.Hosting?view=msbuild-16&preserve-view=true) | Vše | Obsahuje třídy používané interně nástrojem MSBuild. |
| [Microsoft. Build. Tasks. XAML](/dotnet/api/Microsoft.Build.Tasks.Xaml?view=msbuild-16&preserve-view=true) | Pouze .NET Framework | Obsahuje třídy související s úlohami sestavení XAML. |
| [Microsoft. Build. Utilities](/dotnet/api/Microsoft.Build.Utilities?view=msbuild-16&preserve-view=true) | Vše | Obsahuje pomocné třídy, které lze použít k vytvoření vlastních protokolovacích nástrojů a úloh nástroje MSBuild.|
:::moniker-end

V předchozí tabulce znamená, že všechny ve sloupci platí pro jsou typy v oboru názvů dostupné jak v .NET Framework, tak i ve verzích .NET Core rozhraní API pro MSBuild.
