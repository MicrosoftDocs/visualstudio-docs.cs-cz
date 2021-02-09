---
title: Metadata položek v cílové dávce | Microsoft Docs
description: Naučte se, jak MSBuild používá metadata položek v cílové dávce k provedení analýzy závislostí na vstupech a výstupech cíle sestavení.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- batching [MSBuild]
- MSBuild, target batching
- target batching [MSBuild]
ms.assetid: f3cc4186-6a4c-4161-bbe5-1ec638b4925b
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 2d3389d24ded805c7b1f8bbb8d31daef0cbef1a5
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99913907"
---
# <a name="item-metadata-in-target-batching"></a>Metadata položek v dávkování cíle

Nástroj MSBuild má schopnost provádět analýzu závislostí na vstupech a výstupech cíle sestavení. Je-li zjištěno, že vstupy nebo výstupy cíle jsou aktuální, bude cíl vynechán a sestavení bude pokračovat. `Target` prvky pomocí `Inputs` atributů a `Outputs` určují položky, které se mají zkontrolovat během analýzy závislostí.

Pokud cíl obsahuje úkol, který používá dávkové položky jako vstupy nebo výstupy, `Target` element Target by měl použít dávkování ve svých `Inputs` atributech nebo, `Outputs` aby nástroj MSBuild mohl přeskočit dávky položek, které jsou již aktuální.

## <a name="batch-targets"></a>Cíle dávky

Následující příklad obsahuje seznam položek s názvem `Res` , který je rozdělen na dvě dávky na základě `Culture` metadat položky. Každá z těchto dávek je předána do `AL` úlohy, která vytvoří výstupní sestavení pro každou dávku. Pomocí dávkového zpracování u `Outputs` atributu `Target` elementu může MSBuild určit, zda je každá z jednotlivých dávek aktuální před spuštěním cíle. Bez použití cílového dávkování by úloha při každém spuštění cíle spouštěla obě dávky položek.

```xml
<Project
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003">

    <ItemGroup>
        <Res Include="Strings.fr.resources">
            <Culture>fr</Culture>
        </Res>
        <Res Include="Strings.jp.resources">
            <Culture>jp</Culture>
        </Res>
        <Res Include="Menus.fr.resources">
            <Culture>fr</Culture>
        </Res>
        <Res Include="Dialogs.fr.resources">
            <Culture>fr</Culture>
        </Res>
        <Res Include="Dialogs.jp.resources">
            <Culture>jp</Culture>
        </Res>
        <Res Include="Menus.jp.resources">
            <Culture>jp</Culture>
        </Res>
    </ItemGroup>

    <Target Name="Build"
        Inputs="@(Res)"
        Outputs="%(Culture)\MyApp.resources.dll">

        <AL Resources="@(Res)"
            TargetType="library"
            OutputAssembly="%(Culture)\MyApp.resources.dll">

    </Target>

</Project>
```

## <a name="see-also"></a>Viz také

- [Postupy: přírůstkové sestavení](../msbuild/how-to-build-incrementally.md)
- [Dávkování](../msbuild/msbuild-batching.md)
- [Target – element (MSBuild)](../msbuild/target-element-msbuild.md)
- [Metadata položek v dávkování úloh](../msbuild/item-metadata-in-task-batching.md)
