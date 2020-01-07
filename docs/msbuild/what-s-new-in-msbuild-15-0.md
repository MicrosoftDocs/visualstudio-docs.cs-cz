---
title: Co&#39;je nového v nástroji MSBuild 15 | Microsoft Docs
ms.date: 03/01/2017
ms.topic: conceptual
ms.assetid: 9976b6fd-d052-4017-b848-35b5bf4b2f66
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
monikerRange: '>=vs-2017'
ms.openlocfilehash: 49e248ee0e5537ae54957695ca698b041fc1ce8b
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/01/2020
ms.locfileid: "75567277"
---
# <a name="whats-new-in-msbuild-15"></a>Co je nového v nástroji MSBuild 15

Nástroj MSBuild je nyní k dispozici jako součást [.NET Core SDK](https://www.microsoft.com/net/download/core) a může sestavovat projekty .NET Core ve Windows, MacOS a Linux.

## <a name="changed-path"></a>Změněná cesta

 Nástroj MSBuild je nyní nainstalován do složky v každé verzi sady Visual Studio. Například *C:\Program Files (x86) \Microsoft Visual Studio\2017\Enterprise\MSBuild*. K vyhledání MSBuild: [vssetup. PowerShellu](https://github.com/Microsoft/vssetup.powershell)můžete použít taky následující modul PowerShellu.

 Nástroj MSBuild již není nainstalován v globální mezipaměti sestavení (GAC). K programovému odkazu na MSBuild použijte balíčky NuGet. Další informace najdete v tématu [aktualizace existující aplikace pro MSBuild 15,0](../msbuild/updating-an-existing-application.md).

## <a name="changed-properties"></a>Změněné vlastnosti

 Následující vlastnosti nástroje MSBuild byly aktualizovány z důvodu nového čísla verze.

- `MSBuildToolsVersion` pro tuto verzi nástrojů je 15,0. Verze sestavení je 15.1.0.0.

- `MSBuildToolsPath` již nepoužívá pevné umístění. Ve výchozím nastavení se nachází ve složce *MSBuild\15.0\Bin* relativně k umístění instalace sady Visual Studio, ale umístění instalace sady Visual Studio lze změnit během instalace.

- `ToolsVersion` hodnoty již nejsou v registru nastaveny.

- Vlastnosti `SDK35ToolsPath` a `SDK40ToolsPath` odkazují na sadu .NET Framework SDK, která je zabalena s touto verzí sady Visual Studio (například 10.0 A pro nástroje 4. X).

## <a name="updates"></a>Aktualizace
- [Prvek projektu](../msbuild/project-element-msbuild.md) má nový atribut `SDK`. Také atribut `Xmlns` je nyní volitelný. Další informace o atributu `SDK` naleznete v tématu [How to: use MSBuild Project SDK](../msbuild/how-to-use-project-sdk.md), [Packages, metabalíčky a](/dotnet/core/packages) Builds and dodaný [Formát csproj pro .NET Core](/dotnet/core/tools/csproj).
- [Element Item](../msbuild/item-element-msbuild.md) mimo cíle má nový atribut `Update`. Také omezení u atributu `Remove` bylo eliminováno.
- *Directory. Build. props* je uživatelsky definovaný soubor, který poskytuje přizpůsobení projektům v adresáři. Tento soubor je automaticky importován z *aplikace Microsoft. Common. props* , pokud vlastnost `ImportDirectoryBuildTargets` není nastavena na **hodnotu false**. *Directory. Build. targets* se importují pomocí *Microsoft. Common. targets*.
- Všechna metadata s názvem, která nejsou v konfliktu s aktuálním seznamem atributů, mohou být volitelně vyjádřena jako atribut. Další informace naleznete v tématu [element Item](../msbuild/item-element-msbuild.md).

## <a name="new-property-functions"></a>Nové funkce vlastností

- `EnsureTrailingSlash` přidá koncové lomítko k cestě, pokud ještě neexistuje.
- `NormalizePath` kombinuje prvky cesty a zajistí, že výstupní řetězec má pro aktuální operační systém správné znaky oddělovače adresáře.
- `NormalizeDirectory` kombinuje prvky cesty, zajišťuje koncové lomítko a zajistí, že výstupní řetězec má pro aktuální operační systém správné znaky oddělovače adresáře.
- `GetPathOfFileAbove` vrátí cestu k souboru bezprostředně před tímto souborem. Je funkčně odpovídá volání `<Import Project="$([MSBuild]::GetDirectoryNameOfFileAbove($(MSBuildThisFileDirectory), dir.props))\dir.props" />`

## <a name="see-also"></a>Viz také:
- [MSBuild](../msbuild/msbuild.md)
