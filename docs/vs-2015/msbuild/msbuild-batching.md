---
title: Dávkování nástroje MSBuild | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- batching [MSBuild]
- MSBuild, batching
ms.assetid: d35c085b-27b8-49d7-b6f8-8f2f3a0eec38
caps.latest.revision: 12
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 24baafbaf213e90999a5e4e0eea030f2ef608501
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/12/2018
ms.locfileid: "49304169"
---
# <a name="msbuild-batching"></a>Dávkování nástroje MSBuild
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
[!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] má schopnost rozdělení seznamů položek do různých kategorií nebo dávek, na základě položky metadat a spustit cíl nebo úloha jednou s jednotlivých dávek.  
  
## <a name="task-batching"></a>Dávkování úloh  
 Dávkování úloh můžete zjednodušit tím, že poskytuje způsob, jak rozdělení seznamů položek na jiné listy a každá z těchto dávky samostatně předat do úlohy soubory projektu. To znamená, že soubor projektu pouze musí mít úkolu a její atributy deklarované jednou, i když můžete spustit několikrát.  
  
 Určete, jestli má [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] provádět dávkové zpracování s úlohami pomocí %(*ItemMetaDataName*) zápis v jednom z atributů úlohy. V následujícím příkladu se rozdělí `Example` na základě seznamu položek do dávek `Color` hodnotu položky metadat a předá do dávek `MyTask` úloh samostatně.  
  
> [!NOTE]
>  Pokud Neodkazovat seznam položek jinde v atributech úloh nebo může být nejednoznačný název metadat, můžete použít %(*ItemCollection.ItemMetaDataName*) zápis k plnému určení hodnotu položky metadat pro dávkové zpracování.  
  
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
  
 Dávkování konkrétnější příklady najdete v tématu [Metadata položek v dávkování úloh](../msbuild/item-metadata-in-task-batching.md).  
  
## <a name="target-batching"></a>Dávkování cíle  
 [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] kontroluje, pokud vstupy a výstupy cíle jsou aktuální předtím, než spustí cíl. Pokud se vstupy a výstupy jsou aktuální, je cíl vynechán. Pokud úkol uvnitř cíl využívá, dávkové zpracování, [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] potřebuje k určení, zda je aktuální vstupy a výstupy pro jednotlivé skupiny položek. V opačném případě je cíl proveden pokaždé, když je spuštění.  
  
 Následující příklad ukazuje `Target` element, který obsahuje `Outputs` atributem %(*ItemMetaDataName*) notaci. [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] Rozdělí `Example` na základě seznamu položek do dávek `Color` položky metadat a analyzovat časová razítka výstupních souborů pro jednotlivé dávky. Pokud výstupy z dávky nejsou aktuální, je spustit cíl. V opačném případě je cíl vynechán.  
  
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
  
 Další příklad dávkování cíle, naleznete v tématu [Metadata položek v dávkování cíle](../msbuild/item-metadata-in-target-batching.md).  
  
## <a name="property-functions-using-metadata"></a>Funkce vlastností pomocí metadat  
 Dávkování lze ovládat funkce vlastností, které zahrnují metadata. Například  
  
 `$([System.IO.Path]::Combine($(RootPath),%(Compile.Identity)))`  
  
 používá <xref:System.IO.Path.Combine%2A> zkombinovat cesta ke kořenové složce položky cestu kompilace.  
  
 Funkce vlastností se nemusí zobrazit v rámci hodnoty metadat.  Například  
  
 `%(Compile.FullPath.Substring(0,3))`  
  
 není povoleno.  
  
 Další informace o funkcích vlastnost, naleznete v tématu [funkce vlastností](../msbuild/property-functions.md).  
  
## <a name="see-also"></a>Viz také  
 [Itemmetadata – Element (MSBuild)](../msbuild/itemmetadata-element-msbuild.md)   
 [Koncepty nástroje MSBuild](../msbuild/msbuild-concepts.md)   
 [Referenční dokumentace nástroje MSBuild](../msbuild/msbuild-reference.md)   
 [Rozšířené koncepty](../msbuild/msbuild-advanced-concepts.md)



