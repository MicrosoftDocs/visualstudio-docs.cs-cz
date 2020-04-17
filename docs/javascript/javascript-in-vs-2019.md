---
title: JavaScript a Script script ve Visual Studiu 2019
ms.date: 03/16/2020
ms.technology: vs-javascript
ms.topic: conceptual
dev_langs:
- JavaScript
- TypeScript
- DHTML
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: '>= vs-2019'
ms.openlocfilehash: 199a27dbfef2b7297563e87d973137e2acd9c745
ms.sourcegitcommit: eef26de3d7a5c971baedbecf3b4941fb683ddb2d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/17/2020
ms.locfileid: "81544286"
---
# <a name="javascript-and-typescript-in-visual-studio-2019"></a>JavaScript a Script script ve Visual Studiu 2019

## <a name="overview"></a>Přehled

Visual Studio 2019 poskytuje bohatou podporu pro vývoj JavaScriptu, a to jak pomocí JavaScriptu přímo, tak také pomocí [programovacího jazyka TypeScript](http://www.typescriptlang.org/), který byl vyvinut tak, aby poskytoval produktivnější a příjemnější vývojové prostředí JavaScriptu, zejména při vývoji projektů ve velkém měřítku. V sadě Visual Studio můžete psát javascriptový nebo typový kód pro mnoho typů aplikací a služeb.

## <a name="javascript-language-service"></a>Služba jazyka JavaScript

Prostředí JavaScriptu ve Visual Studiu 2019 je poháněno stejným motorem, který poskytuje podporu jazyka TypeScript. To vám dává lepší podporu funkcí, bohatost a integraci okamžitě out-of-the-box.

Možnost obnovení starší jazykové služby JavaScript již není k dispozici. Uživatelé mají nyní novou jazykovou službu JavaScript out-of-the-box. Nová jazyková služba je založena výhradně na službě jazyka TypeScript, která je poháněna statickou analýzou. To nám umožňuje poskytovat vám lepší nástroje, takže váš kód JavaScript může těžit z bohatšího technologie IntelliSense na základě definic typů. Nová služba je zjednodušená a spotřebovává méně paměti než starší služba, což vám poskytuje lepší výkon při škálování kódu. Také jsme zlepšili výkon jazykové služby pro zpracování větších projektů.

## <a name="typescript-support"></a>Podpora jazyka TypeScript

Visual Studio 2019 nabízí několik možností pro integraci kompilace TypeScriptu do vašeho projektu:

* [Balíček TypeScript NuGet](https://www.nuget.org/packages/Microsoft.TypeScript.MSBuild). Když je do projektu nainstalován balíček NuGet pro TypeScript 3.2 nebo vyšší, načte se odpovídající verze služby jazyka TypeScript v editoru.
* [Balíček TypeScript npm](https://www.npmjs.com/package/typescript). Pokud je do projektu nainstalován balíček npm pro typescript 2.1 nebo vyšší, načte se odpovídající verze služby jazyka TypeScript v editoru.
* Sada TypeScript SDK, která je ve výchozím nastavení k dispozici v instalačním programu sady Visual Studio, a samostatná sada SDK ke stažení z [webu VS Marketplace](https://marketplace.visualstudio.com/items?itemName=TypeScriptTeam.typescript-331-vs2017).

> [!TIP]
> Pro projekty vyvinuté v Sadě Visual Studio 2019 doporučujeme použít balíček TypeScript NuGet nebo TypeScript npm pro větší přenositelnost na různých platformách a prostředích.

Jedním z běžných použití pro balíček NuGet je kompilace TypeScript pomocí rozhraní PŘÍKAZOVÉHO PŘÍKAZU jádra .NET. Pokud ručně neupravíte soubor projektu pro import cílů sestavení z instalace sady TypeScript SDK, je balíček NuGet jediným `dotnet build` `dotnet publish`způsobem, jak povolit kompilaci jazyka TypeScript pomocí příkazů rozhraní .NET Core CLI, jako jsou příkazy a .

## <a name="remove-default-imports-aspnet-core-projects"></a>Odebrání výchozích importů (ASP.NET základní projekty)

Ve starších projektech, které používají [formát jiného než sdk](https://docs.microsoft.com/nuget/resources/check-project-format), bude pravděpodobně nutné odebrat některé prvky souboru projektu.

Pokud používáte balíček NuGet pro podporu MSBuild pro projekt, `Microsoft.TypeScript.Default.props` `Microsoft.TypeScript.targets`soubor projektu nesmí importovat nebo . Soubory získat importovány balíček NuGet, takže jejich zahrnutí samostatně může způsobit nežádoucí chování.

1. Klepněte pravým tlačítkem myši na projekt a zvolte **Uvolnit projekt**.

1. Klikněte pravým tlačítkem myši na projekt a zvolte **Upravit \< *název*\>souboru projektu**.

   Otevře se soubor projektu.

1. Odeberte `Microsoft.TypeScript.Default.props` odkazy `Microsoft.TypeScript.targets`na a .

   Importy odebrat vypadat podobně jako následující:

   ```xml
   <Import
      Project="$(MSBuildExtensionsPath32)\Microsoft\VisualStudio\v$(VisualStudioVersion)\TypeScript\Microsoft.TypeScript.Default.props"
      Condition="Exists('$(MSBuildExtensionsPath32)\Microsoft\VisualStudio\v$(VisualStudioVersion)\TypeScript\Microsoft.TypeScript.Default.props')" />

   <Import
      Project="$(MSBuildExtensionsPath32)\Microsoft\VisualStudio\v$(VisualStudioVersion)\TypeScript\Microsoft.TypeScript.targets"
      Condition="Exists('$(MSBuildExtensionsPath32)\Microsoft\VisualStudio\v$(VisualStudioVersion)\TypeScript\Microsoft.TypeScript.targets')" />
   ```

## <a name="projects"></a>Projekty

Javascriptové aplikace UPW se už v sadě Visual Studio 2019 nepodporují. Nelze vytvářet ani otevírat projekty JavaScript UPW (soubory s příponou *Jsproj*). Další informace naleznete v naší dokumentaci o [vytváření progresivních webových aplikací (PWA),](/microsoft-edge/progressive-web-apps/get-started) které dobře běží v systému Windows.
