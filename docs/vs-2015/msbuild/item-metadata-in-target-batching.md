---
title: Metadata položek v cílové dávce | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: conceptual
helpviewer_keywords:
- batching [MSBuild]
- MSBuild, target batching
- target batching [MSBuild]
ms.assetid: f3cc4186-6a4c-4161-bbe5-1ec638b4925b
caps.latest.revision: 9
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 9dd6c297e00a305fbd1b13cf0fe0bd4a4f151f6b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "68192874"
---
# <a name="item-metadata-in-target-batching"></a>Metadata položek v dávkování cíle
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

[!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] má schopnost provádět analýzu závislostí na vstupech a výstupech cíle sestavení. Je-li zjištěno, že vstupy nebo výstupy cíle jsou aktuální, bude cíl vynechán a sestavení bude PROCEDE. `Target` prvky pomocí `Inputs` atributů a `Outputs` určují položky, které se mají zkontrolovat během analýzy závislostí.  
  
 Pokud cíl obsahuje úkol, který používá dávkové položky jako vstupy nebo výstupy, `Target` element Target by měl použít dávkování ve svých `Inputs` atributech nebo, `Outputs` aby bylo možné [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] Přeskočit dávky položek, které jsou již aktuální.  
  
## <a name="batching-targets"></a>Cíle dávkování  
 Následující příklad obsahuje seznam položek s názvem `Res` , který je rozdělen na dvě dávky na základě `Culture` metadat položky. Každá z těchto dávek je předána do `AL` úlohy, která vytvoří výstupní sestavení pro každou dávku. Pomocí dávkového zpracování u `Outputs` atributu `Target` elementu [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] může určit, zda je každá z jednotlivých dávek aktuální před spuštěním cíle. Bez použití cílového dávkování by úloha při každém spuštění cíle spouštěla obě dávky položek.  
  
```  
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
  
## <a name="see-also"></a>Viz také  
 [Postupy: přírůstkové sestavení](../msbuild/how-to-build-incrementally.md)   
 [Dávkování](../msbuild/msbuild-batching.md)   
 [Target – element (MSBuild)](../msbuild/target-element-msbuild.md)   
 [Metadata položek v dávkování úloh](../msbuild/item-metadata-in-task-batching.md)
