---
title: Co&#39;s Novinka v MSBuild 15 | Dokumenty společnosti Microsoft
ms.date: 03/01/2017
ms.topic: conceptual
ms.assetid: 9976b6fd-d052-4017-b848-35b5bf4b2f66
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
monikerRange: '>=vs-2017'
ms.openlocfilehash: 2503040e074a62422d4c7c904f5ad3a2bd84d6c1
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "77631026"
---
# <a name="whats-new-in-msbuild-15"></a>Co je nového v MSBuild 15

MSBuild je teď k dispozici jako součást [sady .NET Core SDK](https://www.microsoft.com/net/download/core) a může vytvářet projekty .NET Core ve Windows, macOS a Linuxu.

## <a name="changed-path"></a>Změněná cesta

 MSBuild je nyní nainstalován ve složce pod každou verzí sady Visual Studio. Například *C:\Program Files (x86)\Microsoft Visual Studio\2017\Enterprise\MSBuild*. K vyhledání msbuildu: [vssetup.powershellu](https://github.com/Microsoft/vssetup.powershell)můžete použít také následující modul prostředí PowerShell.

 MSBuild se již neinstaluje v globální mezipaměti sestavení. Chcete-li odkazovat na MSBuild programově, použijte balíčky NuGet. Další informace naleznete [v tématu Aktualizace existující aplikace pro msbuild 15.0](../msbuild/updating-an-existing-application.md).

## <a name="changed-properties"></a>Změněné vlastnosti

 Následující vlastnosti MSBuild byly aktualizovány z důvodu nového čísla verze.

- `MSBuildToolsVersion`pro tuto verzi nástrojů je 15.0. Verze sestavení je 15.1.0.0.

- `MSBuildToolsPath`již nemá pevné umístění. Ve výchozím nastavení je umístěn ve složce *MSBuild\15.0\Bin* vzhledem k umístění instalace sady Visual Studio, ale umístění instalace sady Visual Studio lze změnit v době instalace.

- `ToolsVersion`hodnoty již nejsou v registru nastaveny.

- `SDK35ToolsPath` Vlastnosti `SDK40ToolsPath` a odkazují na sdk rozhraní .NET Framework, která je zabalena s touto verzí sady Visual Studio (například 10.0A pro nástroje 4.X).

## <a name="updates"></a>Aktualizace

- [Prvek projektu](../msbuild/project-element-msbuild.md) má `SDK` nový atribut. Také `Xmlns` atribut je nyní volitelné. Další informace o `SDK` atributu naleznete v [tématu How to: Use MSBuild project SDKs](../msbuild/how-to-use-project-sdk.md), [Packages, metapackages and frameworks and Additions](/dotnet/core/packages) [to the csproj format for .NET Core](/dotnet/core/tools/csproj).
- [Prvek položky](../msbuild/item-element-msbuild.md) mimo `Update` cíle má nový atribut. Omezení atributu `Remove` bylo také eliminováno.
- *Directory.Build.props* je uživatelem definovaný soubor, který poskytuje vlastní nastavení projektů mj. Tento soubor je automaticky importován z *souboru Microsoft.Common.props,* pokud není vlastnost `ImportDirectoryBuildTargets` nastavena na **hodnotu false**. *Directory.Build.targets* je importován souborem *Microsoft.Common.targets*.
- Všechna metadata s názvem, který není v konfliktu s aktuálním seznamem atributů, mohou být volitelně vyjádřena jako atribut. Další informace naleznete v tématu [Item element](../msbuild/item-element-msbuild.md).

## <a name="new-property-functions"></a>Nové funkce vlastností

- `EnsureTrailingSlash`přidá do cesty koncové lomítko, pokud ještě neexistuje.
- `NormalizePath`kombinuje prvky cesty a zajišťuje, že výstupní řetězec má správné znaky oddělovače adresářů pro aktuální operační systém.
- `NormalizeDirectory`kombinuje prvky cesty, zajišťuje koncové lomítko a zajišťuje, že výstupní řetězec má správné znaky oddělovače adresářů pro aktuální operační systém.
- `GetPathOfFileAbove`vrátí cestu k souboru bezprostředně předcházejícímu tomuto souboru. Je funkčně ekvivalentní volání`<Import Project="$([MSBuild]::GetDirectoryNameOfFileAbove($(MSBuildThisFileDirectory), dir.props))\dir.props" />`

## <a name="see-also"></a>Viz také

- [Msbuild](../msbuild/msbuild.md)
