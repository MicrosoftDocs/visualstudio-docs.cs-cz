---
title: Co&#39;nového v MSBuild 15 | Dokumentace Microsoftu
ms.custom: ''
ms.date: 03/01/2017
ms.technology: msbuild
ms.topic: conceptual
ms.assetid: 9976b6fd-d052-4017-b848-35b5bf4b2f66
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 2333f45cca5510a4ba3bb0f54abf45a569454cf8
ms.sourcegitcommit: 25fc9605ba673afb51a24ce587cf4304b06aa577
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/24/2018
ms.locfileid: "47028959"
---
# <a name="whats-new-in-msbuild-15"></a>Co je nového v MSBuild 15

Nástroj MSBuild je nyní k dispozici jako součást [.NET Core SDK](https://www.microsoft.com/net/download/core) a můžete vytvářet projekty .NET Core ve Windows, macOS a Linuxu.

## <a name="changed-path"></a>Změněné cesta

 Nástroj MSBuild je nyní nainstalován do složky pod jednotlivými verzemi sady Visual Studio. Například *C:\Program Files (x86) \Microsoft Visual Studio\2017\Enterprise\MSBuild*. Následující modul Powershellu můžete použít také k vyhledání nástroje MSBuild: [vssetup.powershell](https://github.com/Microsoft/vssetup.powershell).

 MSBuild je již nainstalována v globální mezipaměti sestavení. K odkazování MSBuild prostřednictvím kódu programu, používaly balíčky NuGet.

## <a name="changed-properties"></a>Změněné vlastnosti

 Byly aktualizovány následující vlastnosti nástroje MSBuild kvůli nové číslo verze.

- `MSBuildToolsVersion` pro tuto verzi sady nástrojů je 15.0. Verze sestavení je 15.1.0.0.

- `MSBuildToolsPath` už má pevné umístění. Ve výchozím nastavení se nachází v *MSBuild\15.0\Bin* složce relativní k umístění instalace sady Visual Studio, ale umístění instalace sady Visual Studio lze změnit v době instalace.

- `ToolsVersion` hodnoty jsou už nastavené v registru.

- `SDK35ToolsPath` a `SDK40ToolsPath` vlastnosti odkazovat na rozhraní .NET Framework SDK je zabalený s touto verzí sady Visual Studio (například 10.0A pro nástroje 4.X).

## <a name="updates"></a>Aktualizace
- [Project – element](../msbuild/project-element-msbuild.md) má přidánu novou `SDK` atribut. Také `Xmlns` atribut je volitelný. Další informace o `SDK` atributu naleznete v tématu [jak: projektu MSBuild pomocí sady SDK](../msbuild/how-to-use-project-sdk.md), [balíčky, metabalíčky a architektury](/dotnet/core/packages) a [doplňky csproj formát pro .NET Základní](/dotnet/core/tools/csproj).
- [Item – element](../msbuild/item-element-msbuild.md) mimo cíle obsahuje novou `Update` atribut. Navíc omezení `Remove` atribut se odstranilo.
- *Directory.Build.props* je uživatelem definovaného souboru, který obsahuje vlastní nastavení pro projekty v adresáři. Tento soubor je automaticky importován z *Microsoft.Common.props* není-li vlastnost `ImportDirectoryBuildTargets` je nastavena na **false**. *Directory.Build.targets* importovaných pomocí *cílů Microsoft.Common.targets*.
- Veškerá metadata s názvem, který není v konfliktu s aktuální seznam atributů může být volitelně vyjádřený jako atribut. Další informace najdete v tématu [Item – element](../msbuild/item-element-msbuild.md).

## <a name="new-property-functions"></a>Nové funkce vlastností

- `EnsureTrailingSlash` Pokud již neexistuje, přidá cestu koncové lomítko.
- `NormalizePath` kombinuje prvky cesty a zajistí, že výstupní řetězec obsahuje znaky oddělovače správný adresář pro aktuální operační systém.
- `NormalizeDirectory` kombinuje prvků cesty, zajišťuje koncové lomítko a zajistí, že výstupní řetězec obsahuje znaky oddělovače správný adresář pro aktuální operační systém.
- `GetPathOfFileAbove` vrátí cestu k souboru, všechny předcházející. Je funkčně odpovídá volání `<Import Project="$([MSBuild]::GetDirectoryNameOfFileAbove($(MSBuildThisFileDirectory), dir.props))\dir.props" />`

## <a name="see-also"></a>Viz také:
[MSBuild](../msbuild/msbuild.md)
