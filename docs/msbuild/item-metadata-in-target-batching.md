---
title: Metadata položky v cílovém dávkování | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- batching [MSBuild]
- MSBuild, target batching
- target batching [MSBuild]
ms.assetid: f3cc4186-6a4c-4161-bbe5-1ec638b4925b
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 83a5d0c9dec280633d0a39573581c083e6ddd4d8
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "77633665"
---
# <a name="item-metadata-in-target-batching"></a>Metadata položky v cílovém dávkování

MSBuild má schopnost provádět analýzu závislostí na vstupy a výstupy cíle sestavení. Pokud je zjištěno, že vstupy nebo výstupy cíle jsou aktuální, cíl bude přeskočen a sestavení bude pokračovat. `Target`elementy `Inputs` používají `Outputs` atributy a k určení položek, které mají být kontrolovány během analýzy závislostí.

Pokud cíl obsahuje úkol, který používá dávkové položky `Target` jako vstupy nebo výstupy, `Inputs` `Outputs` prvek cíle by měl použít dávkování v jeho nebo atributy povolit MSBuild přeskočit dávky položek, které jsou již aktuální.

## <a name="batch-targets"></a>Dávkové cíle

Následující příklad obsahuje seznam `Res` položek s názvem, který je `Culture` rozdělen do dvou dávek na základě metadat položky. Každá z těchto dávek je `AL` předána do úlohy, která vytvoří výstupní sestavení pro každou dávku. Pomocí dávkování na `Outputs` atribut `Target` prvku MSBuild můžete určit, pokud každý z jednotlivých dávek je aktuální před spuštěním cíle. Bez použití cílové dávkování, obě dávky položek by být spuštěna úlohou při každém provedení cíle.

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

- [Postup: Sestavení postupně](../msbuild/how-to-build-incrementally.md)
- [Dávkování](../msbuild/msbuild-batching.md)
- [Cílový prvek (MSBuild)](../msbuild/target-element-msbuild.md)
- [Metadata položky v dávkování úloh](../msbuild/item-metadata-in-task-batching.md)
