---
title: Filtry řešení v nástroji MSBuild
description: Vysvětluje filtry řešení a ukazuje, jak vytvořit soubor filtru řešení pomocí nástroje MSBuild.
ms.date: 07/28/2020
ms.topic: reference
helpviewer_keywords:
- MSBuild, solution filters
- solution filters [MSBuild]
author: ghogen
ms.author: ghogen
manager: jillfra
monikerRange: '>= vs-2019'
ms.openlocfilehash: 998103828d20827e8a1d99e0cc34d7f9beb6bd7c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "87401028"
---
# <a name="solution-filters-in-msbuild"></a>Filtry řešení v nástroji MSBuild

Soubory filtru řešení jsou soubory JSON s příponou *. slnf* , které označují, které projekty se mají sestavit nebo načíst ze všech projektů v řešení. Počínaje nástrojem MSBuild 16,7 můžete vyvolat MSBuild v souboru filtru řešení pro sestavení řešení s povoleným filtrováním. 

> [!NOTE]
> Soubor filtru řešení snižuje sadu projektů, které budou načteny nebo sestaveny, a zjednodušuje formát. Soubor řešení je stále požadován.

## <a name="build-a-solution-filter-from-the-command-line"></a>Sestavení filtru řešení z příkazového řádku

Sestavení souboru filtru řešení z příkazového řádku používá naprosto stejnou syntaxi jako sestavení souboru řešení. Místo řešení pro sestavení s povoleným filtrováním zadejte soubor filtru řešení, a to následujícím způsobem:

```console
msbuild [options] solutionFilterFile.slnf
```

Přepínače a další vlastnosti můžete také připojit jako normální. Viz [Reference k příkazovému řádku MSBuild](msbuild-command-line-reference.md). Tento příkaz vytvoří filtrované projekty a všechny projekty, na kterých jsou závislé. Nástroj MSBuild automaticky sleduje závislosti při sestavování filtru řešení z příkazového řádku. Sestaví projekt, pokud je zadán ve filtru nebo odkazováno sestaveným projektem.

## <a name="solution-filter-files"></a>Soubory filtru řešení

Pomocí sady Visual Studio můžete pracovat se soubory filtru řešení. Otevřením filtru řešení v aplikaci Visual Studio se zobrazí Nenačtené projekty a také načtené projekty a získáte možnost načítat další projekty pro jejich výběr pro sestavení. Můžete načíst všechny projekty, na které se na sestavení závisí i počáteční projekty, ale to není vyžadováno. Viz [filtrovaná řešení](../ide/filtered-solutions.md).

Filtr řešení nemusí být ve stejné složce jako řešení. Cesta k souboru řešení je relativní vzhledem k umístění souboru filtru řešení, ale cesty ke každému projektu jsou relativní vzhledem k samotnému souboru řešení a měly by odpovídat cestám projektu v souboru řešení. Následující příklad demonstruje použití relativních cest:

```json
{
  "solution": {
    "path": "..\\..\\Documents\\GitHub\\msbuild\\MSBuild.sln",
    "projects": [
      "src\\Build.OM.UnitTests\\Microsoft.Build.Engine.OM.UnitTests.csproj"
    ]
  }
}
```

Zpětná lomítka v cestách musí být dvojitá, protože jsou řídicí.

## <a name="example"></a>Příklad

Tady je příklad filtrovaného řešení v aplikaci Visual Studio:

![Snímek obrazovky s filtrovaným řešením v aplikaci Visual Studio](media/solution-with-filter.png)

V tomto řešení se ClassLibrary1 používá v projektu i v ProjectB, takže ClassLibrary1 je uveden jako odkaz na projekt.

Zde je soubor filtru řešení, který aplikace Visual Studio vygeneruje:

```json
{
  "solution": {
    "path": "MyApplication.sln",
    "projects": [
      "MyApplication\\MyApplication.csproj",
      "ProjectA\\ProjectA.csproj"
    ]
  }
}
```

V tomto příkladu, když sestavíte s povoleným filtrováním (pomocí příkazu `MSBuild [options] MyFilter.slnf` ), MSBuild sestaví MyApplication a Projecta, protože jsou výslovně uvedeny v souboru filtru řešení. V rámci sestavování projektu MSBuild sestavení MSBuild sestaví ClassLibrary1, protože na něm závisí Projecta.  ProjectB není sestaven. (Tato diskuze předpokládá čistý Build. Pokud byly projekty sestaveny dříve, použijí se obvyklá pravidla pro přeskočení projektů, které jsou již aktuální.)

## <a name="see-also"></a>Viz také

- [Filtrovaná řešení](../ide/filtered-solutions.md)
- [Reference k příkazovému řádku nástroje MSBuild](msbuild-command-line-reference.md)
