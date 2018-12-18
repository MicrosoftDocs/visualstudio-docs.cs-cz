---
title: Metadata položek v dávkování úloh | Dokumentace Microsoftu
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
- task batching [MSBuild]
- MSBuild, task batching
ms.assetid: 31e480f8-fe4d-4633-8c54-8ec498e2306d
caps.latest.revision: 16
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c117f6864aadd7c981aa2b89302c06ccfd6c9768
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49923781"
---
# <a name="item-metadata-in-task-batching"></a>Metadata položek v dávkování úloh
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
[!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] má schopnost rozdělení seznamů položek do různých kategorií nebo dávek, na základě položky metadat a spuštění úlohy jednou s jednotlivých dávek. Může být matoucí pochopit přesně položky, které jsou předávány pomocí které služby batch. Toto téma popisuje následující běžné scénáře, které se týkají dávkování.  
  
- Dělení seznam položek do dávek  
  
- Dělení několik seznamů položek do dávek  
  
- Dávkování jedna položka v čase  
  
- Filtrování seznamů položek  
  
  Další informace o dávkové zpracování s [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)], naleznete v tématu [dávkování](../msbuild/msbuild-batching.md).  
  
## <a name="dividing-an-item-list-into-batches"></a>Dělení seznam položek do dávek  
 Dávkování umožňuje rozdělit seznam položek na jiné listy na základě položky metadat a předejte jednotlivých dávek úkol samostatně. To je užitečné pro vytváření satelitních sestavení.  
  
 Následující příklad ukazuje, jak rozdělit seznam položek do dávek na základě metadat položky. `ExampColl` Seznam položek je rozdělen na tři dávek na základě `Number` metadata položky. Přítomnost `%(ExampColl.Number)`v `Text` atribut informuje [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] , že má být provedena dávkování. `ExampColl` Seznam položek je rozdělen na tři dávek na základě `Number` metadata a každá dávka je předán samostatně do úkolu.  
  
```  
<Project  
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  
    <ItemGroup>  
        <ExampColl Include="Item1">  
            <Number>1</Number>  
        </ExampColl>  
        <ExampColl Include="Item2">  
            <Number>2</Number>  
        </ExampColl>  
        <ExampColl Include="Item3">  
            <Number>3</Number>  
        </ExampColl>  
        <ExampColl Include="Item4">  
            <Number>1</Number>  
        </ExampColl>  
        <ExampColl Include="Item5">  
            <Number>2</Number>  
        </ExampColl>  
        <ExampColl Include="Item6">  
            <Number>3</Number>  
        </ExampColl>  
    </ItemGroup>  
  
    <Target Name="ShowMessage">  
        <Message  
            Text = "Number: %(ExampColl.Number) -- Items in ExampColl: @(ExampColl)"/>  
    </Target>  
  
</Project>  
```  
  
 [Úloha zprávy](../msbuild/message-task.md) úloh zobrazí následující informace:  
  
 `Number: 1 -- Items in ExampColl: Item1;Item4`  
  
 `Number: 2 -- Items in ExampColl: Item2;Item5`  
  
 `Number: 3 -- Items in ExampColl: Item3;Item6`  
  
## <a name="dividing-several-item-lists-into-batches"></a>Dělení několik položek obsahuje do dávek  
 [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] více položek seznamů lze rozdělit do dávek na základě stejné metadat. To umožňuje snadno k rozdělení seznamů různých položek do dávek pro tvorbu více sestavení. Například můžete mít seznam položek souborů .cs rozdělit do batch aplikace a batch sestavení a souborů prostředků, které jsou rozdělené do batch aplikace a batch sestavení seznam položek. Můžete pak použít dávkové zpracování předat tyto seznamy položek do jednoho úkolu a vytvářejte aplikace a sestavení.  
  
> [!NOTE]
>  Pokud seznam položek předávaný do úlohy neobsahuje žádné položky odkazované metadaty, každá položka v seznamu položek je předán do každé dávky.  
  
 Následující příklad ukazuje, jak rozdělit do dávek na základě metadat položky seznamu více položek. `ExampColl` a `ExampColl2` každý seznamy položek jsou rozdělené do tří dávek na základě `Number` metadata položky. Přítomnost `%(Number)`v `Text` atribut informuje [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] , že má být provedena dávkování. `ExampColl` a `ExampColl2` seznamy položek jsou rozdělené do tří dávek na základě `Number` metadata a každá dávka je předán samostatně do úkolu.  
  
```  
<Project  
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  
    <ItemGroup>  
  
        <ExampColl Include="Item1">  
            <Number>1</Number>  
        </ExampColl>  
        <ExampColl Include="Item2">  
            <Number>2</Number>  
        </ExampColl>  
        <ExampColl Include="Item3">  
            <Number>3</Number>  
        </ExampColl>  
  
        <ExampColl2 Include="Item4">  
            <Number>1</Number>  
        </ExampColl2>  
        <ExampColl2 Include="Item5">  
            <Number>2</Number>  
        </ExampColl2>  
        <ExampColl2 Include="Item6">  
            <Number>3</Number>  
        </ExampColl2>  
  
    </ItemGroup>  
  
    <Target Name="ShowMessage">  
        <Message  
            Text = "Number: %(Number) -- Items in ExampColl: @(ExampColl) ExampColl2: @(ExampColl2)"/>  
    </Target>  
  
</Project>  
```  
  
 [Úloha zprávy](../msbuild/message-task.md) úloh zobrazí následující informace:  
  
 `Number: 1 -- Items in ExampColl: Item1 ExampColl2: Item4`  
  
 `Number: 2 -- Items in ExampColl: Item2 ExampColl2: Item5`  
  
 `Number: 3 -- Items in ExampColl: Item3 ExampColl2: Item6`  
  
## <a name="batching-one-item-at-a-time"></a>Dávkování jedna položka v čase  
 Dávkování lze provést také u známá metadata položky, která je přiřazená každé položce při vytvoření. To zaručuje, že každá položka v kolekci mají některá metadata pro dávkové zpracování. `Identity` Hodnota metadat je jedinečný pro každé položky a je užitečné pro rozdělení každá položka v seznamu položek do samostatné dávky. Úplný seznam známá metadata položky, naleznete v tématu [Metadata známé položky](../msbuild/msbuild-well-known-item-metadata.md).  
  
 Následující příklad ukazuje, jak batch každou položku v seznamu položek jeden po druhém. Protože `Identity` hodnota metadat každá položka je jedinečný, `ExampColl` seznam položek je rozdělen do šesti dávek, každá dávka obsahující jednu položku seznamu položek. Přítomnost `%(Identity)`v `Text` atribut informuje [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] , že má být provedena dávkování.  
  
```  
<Project  
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  
    <ItemGroup>  
  
        <ExampColl Include="Item1"/>  
        <ExampColl Include="Item2"/>  
        <ExampColl Include="Item3"/>  
        <ExampColl Include="Item4"/>  
        <ExampColl Include="Item5"/>  
        <ExampColl Include="Item6"/>  
  
    </ItemGroup>  
  
    <Target Name="ShowMessage">  
        <Message  
            Text = "Identity: "%(Identity)" -- Items in ExampColl: @(ExampColl)"/>  
    </Target>  
  
</Project>  
```  
  
 [Úloha zprávy](../msbuild/message-task.md) úloh zobrazí následující informace:  
  
```  
Identity: "Item1" -- Items in ExampColl: Item1  
Identity: "Item2" -- Items in ExampColl: Item2  
Identity: "Item3" -- Items in ExampColl: Item3  
Identity: "Item4" -- Items in ExampColl: Item4  
Identity: "Item5" -- Items in ExampColl: Item5  
Identity: "Item6" -- Items in ExampColl: Item6  
```  
  
## <a name="filtering-item-lists"></a>Obsahuje seznam filtrování položek  
 Dávkování lze použít k filtrování některých položek ze seznamu položek před předáním k úkolu. Například filtrování `Extension` hodnota metadata známé položky umožňuje spouštět úlohy na pouze soubory s konkrétní příponou.  
  
 Následující příklad ukazuje, jak rozdělit seznam položek do dávek na základě položky metadat a vyfiltrujte těchto dávky, pokud jsou předány do úlohy. `ExampColl` Seznam položek je rozdělen na tři dávek na základě `Number` metadata položky. `Condition` Určuje atribut úkolu, který pouze s dávek `Number` položky metadat hodnotu `2` se předají do úlohy  
  
```  
<Project  
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  
    <ItemGroup>  
  
        <ExampColl Include="Item1">  
            <Number>1</Number>  
        </ExampColl>  
        <ExampColl Include="Item2">  
            <Number>2</Number>  
        </ExampColl>  
        <ExampColl Include="Item3">  
            <Number>3</Number>  
        </ExampColl>  
        <ExampColl Include="Item4">  
            <Number>1</Number>  
        </ExampColl>  
        <ExampColl Include="Item5">  
            <Number>2</Number>  
        </ExampColl>  
        <ExampColl Include="Item6">  
            <Number>3</Number>  
        </ExampColl>  
  
    </ItemGroup>  
  
    <Target Name="Exec">  
        <Message  
            Text = "Items in ExampColl: @(ExampColl)"  
            Condition="'%(Number)'=='2'"/>  
    </Target>  
  
</Project>  
```  
  
 [Úloha zprávy](../msbuild/message-task.md) úloh zobrazí následující informace:  
  
```  
Items in ExampColl: Item2;Item5  
```  
  
## <a name="see-also"></a>Viz také  
 [Metadata známé položky](../msbuild/msbuild-well-known-item-metadata.md)   
 [Item – Element (MSBuild)](../msbuild/item-element-msbuild.md)   
 [Itemmetadata – Element (MSBuild)](../msbuild/itemmetadata-element-msbuild.md)   
 [Dávkové zpracování](../msbuild/msbuild-batching.md)   
 [Koncepty nástroje MSBuild](../msbuild/msbuild-concepts.md)   
 [Referenční dokumentace nástroje MSBuild](../msbuild/msbuild-reference.md)



