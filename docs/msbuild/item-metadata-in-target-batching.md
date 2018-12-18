---
title: Metadata položek v dávkování cíle | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology: msbuild
ms.topic: conceptual
helpviewer_keywords:
- batching [MSBuild]
- MSBuild, target batching
- target batching [MSBuild]
ms.assetid: f3cc4186-6a4c-4161-bbe5-1ec638b4925b
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 486169788ad4533f5d45bf48c979ce3d0f5f7920
ms.sourcegitcommit: 8ee7efb70a1bfebcb6dd9855b926a4ff043ecf35
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/17/2018
ms.locfileid: "39081056"
---
# <a name="item-metadata-in-target-batching"></a>Metadata položek v dávkování cíle
[!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] má schopnost provádět analýzu závislostí na vstupy a výstupy cíle sestavení. Pokud je zjištěno, že vstupy nebo výstupy cíle jsou aktuální, cíl se přeskočí a bude pokračovat sestavení. `Target` použití elementů `Inputs` a `Outputs` atributů zadejte položky, které chcete zkontrolovat během analýzu závislostí.  
  
 Pokud cíl obsahuje úlohu, která využívá jako vstupy nebo výstupy, dávková položka `Target` element cíle by měl použití dávkování v jeho `Inputs` nebo `Outputs` atributy se mají povolit [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] přeskočit dávky položek, které jsou již aktuální.  
  
## <a name="batch-targets"></a>Cíle služby batch  
 Následující příklad obsahuje seznam položek s názvem `Res` , který je rozdělen do dvou dávek na základě `Culture` metadata položky. Každá z těchto dávky je předán `AL` úkol, který vytvoří výstup sestavení u každé dávky. S použitím dávkování na `Outputs` atribut `Target` elementu [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] můžete zjistit, jestli každý jednotlivých dávek aktuální před spuštěním cílové. Bez použití dávkování cíle, obě dávky položek by spustit úlohy pokaždé, když byl cíl spuštěn.  
  
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
            OutputAssembly="%(Culture)\MyApp.resources.dll"  
  
    </Target>  
  
</Project>  
```  
  
## <a name="see-also"></a>Viz také:  
 [Postupy: přírůstkové sestavování](../msbuild/how-to-build-incrementally.md)   
 [Dávkové zpracování](../msbuild/msbuild-batching.md)   
 [Target – element (MSBuild)](../msbuild/target-element-msbuild.md)   
 [Metadata položek v dávkování úloh](../msbuild/item-metadata-in-task-batching.md)