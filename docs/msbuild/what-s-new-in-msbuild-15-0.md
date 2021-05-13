---
title: Co je nového v nástroji MSBuild 15 | Microsoft Docs
description: Viz změněné, aktualizované a nové funkce nástroje MSBuild 15, které jsou dostupné pro .NET Core SDK a pro sestavování projektů .NET Core ve Windows, macOS a Linuxu.
ms.custom: SEO-VS-2020
ms.date: 03/01/2017
ms.topic: conceptual
ms.assetid: 9976b6fd-d052-4017-b848-35b5bf4b2f66
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
monikerRange: '>=vs-2017'
ms.openlocfilehash: e0fe78e781af4f2fafa52a230036bc20b657fd8e
ms.sourcegitcommit: 9cb0097c33755a3e5cbadde3b0a6e9e76cee727d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/13/2021
ms.locfileid: "109848263"
---
# <a name="whats-new-in-msbuild-15"></a>Co je nového v nástroji MSBuild 15

Nástroj MSBuild je teď k dispozici jako součást [.NET Core SDK](https://www.microsoft.com/net/download/core) a může sestavovat projekty .NET Core ve Windows, macOS a Linuxu.

## <a name="changed-path"></a>Změněná cesta

 Nástroj MSBuild je teď nainstalovaný ve složce v každé verzi nástroje Visual Studio. Například *C:\Program Files (x86)\Microsoft Visual Studio\2017\Enterprise\MSBuild*. K vyhledání nástroje MSBuild můžete použít také následující modul PowerShellu: [vssetup.powershell](https://github.com/Microsoft/vssetup.powershell).

 Nástroj MSBuild už není nainstalován v globální mezipaměti sestavení (GAC). Pokud chcete na MSBuild odkazovat programově, použijte balíčky NuGet. Další informace najdete v tématu [Aktualizace existující aplikace pro MSBuild 15.0.](../msbuild/updating-an-existing-application.md)

## <a name="changed-properties"></a>Změněné vlastnosti

 Kvůli novému číslu verze byly aktualizovány následující vlastnosti nástroje MSBuild.

- `MSBuildToolsVersion` pro tuto verzi nástrojů je 15.0. Verze sestavení je 15.1.0.0.

- `MSBuildToolsPath` už nemá pevné umístění. Ve výchozím nastavení se nachází ve složce *MSBuild\15.0\Bin* vzhledem k umístění instalace Visual Studio, ale umístění instalace Visual Studio lze změnit v době instalace.

- `ToolsVersion` Hodnoty se už v registru nastavovat nebudou.

- Vlastnosti a odkazovat na sadu .NET Framework SDK, která je součástí této verze `SDK35ToolsPath` `SDK40ToolsPath` Visual Studio (například 10.0A pro nástroje 4.X).

## <a name="updates"></a>Aktualizace

- [Projekt element](../msbuild/project-element-msbuild.md) má nový `SDK` atribut. `Xmlns`Atribut je teď také volitelný. Další informace o `SDK` atributu naleznete v tématu [How to: use MSBuild Project SDK](../msbuild/how-to-use-project-sdk.md), [Packages, metabalíčky a Frameworks](/dotnet/core/packages) and doplňující [Formát csproj pro .NET Core](/dotnet/core/tools/csproj).
- [Element Item](../msbuild/item-element-msbuild.md) mimo cíl má nový `Update` atribut. Také omezení u `Remove` atributu bylo eliminováno.
- *Directory. Build. props* je uživatelsky definovaný soubor, který poskytuje přizpůsobení projektům v adresáři. Tento soubor je automaticky importován z *aplikace Microsoft. Common. props* , pokud vlastnost `ImportDirectoryBuildTargets` není nastavena na **hodnotu false**. *Directory. Build. targets* se importují pomocí *Microsoft. Common. targets*.
- Všechna metadata s názvem, která nejsou v konfliktu s aktuálním seznamem atributů, mohou být volitelně vyjádřena jako atribut. Další informace naleznete v tématu [element Item](../msbuild/item-element-msbuild.md).

## <a name="new-property-functions"></a>Nové funkce vlastností

- `EnsureTrailingSlash` Přidá koncové lomítko k cestě, pokud ještě neexistuje.
- `NormalizePath` kombinuje prvky cesty a zajistí, že výstupní řetězec má pro aktuální operační systém správné znaky oddělovače adresáře.
- `NormalizeDirectory` kombinuje prvky cesty, zajišťuje koncové lomítko a zajistí, že výstupní řetězec má pro aktuální operační systém správné znaky oddělovače adresáře.
- `GetPathOfFileAbove` Vrátí cestu k souboru, který bezprostředně předchází této složce. Je funkčně ekvivalentní volání `<Import Project="$([MSBuild]::GetDirectoryNameOfFileAbove($(MSBuildThisFileDirectory), dir.props))\dir.props" />`

## <a name="see-also"></a>Viz také

- [MSBuild](../msbuild/msbuild.md)
