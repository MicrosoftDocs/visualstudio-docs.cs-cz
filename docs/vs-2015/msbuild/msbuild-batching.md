---
title: Dávkování nástroje MSBuild | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: reference
helpviewer_keywords:
- batching [MSBuild]
- MSBuild, batching
ms.assetid: d35c085b-27b8-49d7-b6f8-8f2f3a0eec38
caps.latest.revision: 12
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: d96330c01ab340d4db67694f358717a2dae0bce3
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "64799390"
---
# <a name="msbuild-batching"></a>Dávkování nástroje MSBuild
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

[!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] má možnost rozdělit seznamy položek do různých kategorií nebo dávky na základě metadat položky a spustit cíl nebo úlohu jednou pro každou dávku.  
  
## <a name="task-batching"></a>Dávkování úloh  
 Dávkování úloh umožňuje zjednodušit soubory projektu tím, že poskytuje způsob, jak rozdělit seznamy položek do různých dávek a předat každou z těchto dávek do úlohy samostatně. To znamená, že soubor projektu potřebuje mít úlohu a její atributy deklarované pouze jednou, i když je možné ji spustit několikrát.  
  
 [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)]Pomocí notace%(*ItemMetaDataName*) v jednom z atributů úlohy určíte, že chcete provést dávkování s úkolem. V následujícím příkladu je rozdělen `Example` seznam položek na dávky založené na `Color` hodnotě metadat položky a každý z těchto dávek se do úlohy předává `MyTask` samostatně.  
  
> [!NOTE]
> Pokud neodkazujte na seznam položek jinde v atributech úlohy nebo název metadat může být nejednoznačný, můžete použít zápis%(*ItemCollection. ItemMetaDataName*) a plně kvalifikovat hodnotu metadat položky, která se má použít pro dávkování.  
  
```  
<Project  
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  
    <ItemGroup>  
        <Example Include="Item1">  
            <Color>Blue</Color>  
        </Example>  
        <Example Include="Item2">  
            <Color>Red</Color>  
        </Example>  
    </ItemGroup>  
  
    <Target Name="RunMyTask">  
        <MyTask  
            Sources = "@(Example)"  
            Output = "%(Color)\MyFile.txt"/>  
    </Target>  
  
</Project>  
```  
  
 Konkrétnější příklady dávkování najdete [v tématu Metadata položek v dávkování úloh](../msbuild/item-metadata-in-task-batching.md).  
  
## <a name="target-batching"></a>Dávkování cíle  
 [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] kontroluje, zda jsou vstupy a výstupy cíle aktuální před spuštěním cíle. Pokud jsou vstupy i výstupy aktuální, přeskočí se cíl. Pokud úloha v cíli používá dávkování, [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] musí určit, jestli jsou vstupy a výstupy pro každou dávku položek aktuální. V opačném případě se cíl spustí pokaždé, když je dosaženo.  
  
 Následující příklad ukazuje `Target` element, který obsahuje `Outputs` atribut s notaci%(*ItemMetaDataName*). [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] rozdělí `Example` seznam položek na dávky založené na `Color` metadatech položky a analyzuje časová razítka výstupních souborů pro každou dávku. Pokud výstupy z dávky nejsou aktuální, je cíl spuštěn. V opačném případě se cíl přeskočí.  
  
```  
<Project  
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  
    <ItemGroup>  
        <Example Include="Item1">  
            <Color>Blue</Color>  
        </Example>  
        <Example Include="Item2">  
            <Color>Red</Color>  
        </Example>  
    </ItemGroup>  
  
    <Target Name="RunMyTask"  
        Inputs="@(Example)"  
        Outputs="%(Color)\MyFile.txt">  
        <MyTask  
            Sources = "@(Example)"  
            Output = "%(Color)\MyFile.txt"/>  
    </Target>  
  
</Project>  
```  
  
 Další příklad cílového dávkování najdete v tématu [Metadata položek v cílové dávce](../msbuild/item-metadata-in-target-batching.md).  
  
## <a name="property-functions-using-metadata"></a>Funkce vlastností pomocí metadat  
 Dávkování lze řídit funkcemi vlastností, které zahrnují metadata. Příklad:  
  
 `$([System.IO.Path]::Combine($(RootPath),%(Compile.Identity)))`  
  
 používá <xref:System.IO.Path.Combine%2A> ke kombinování cesty ke kořenové složce s cestou položky kompilace.  
  
 Funkce vlastností se nesmí vyskytovat v hodnotách metadat.  Příklad:  
  
 `%(Compile.FullPath.Substring(0,3))`  
  
 není povoleno.  
  
 Další informace o funkcích vlastností naleznete v tématu [funkce vlastností](../msbuild/property-functions.md).  
  
## <a name="see-also"></a>Viz také  
 [ItemMetadata – – element (MSBuild)](../msbuild/itemmetadata-element-msbuild.md)   
 [Koncepty nástroje MSBuild](../msbuild/msbuild-concepts.md)   
 [Referenční dokumentace nástroje MSBuild](../msbuild/msbuild-reference.md)   
 [Pokročilé koncepty](../msbuild/msbuild-advanced-concepts.md)
