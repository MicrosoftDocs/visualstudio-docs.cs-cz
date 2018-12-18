---
title: Output – Element (MSBuild) | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#Output
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- <Output> Element [MSBuild]
- Output Element [MSBuild]
ms.assetid: 34bc7cd1-efd3-4b57-b691-4584eeb6a0e9
caps.latest.revision: 17
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 8e3927a368c7b1b33b85a2067ea158edf80b72e8
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/12/2018
ms.locfileid: "49256683"
---
# <a name="output-element-msbuild"></a>Output – element (MSBuild)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Úložiště úlohy výstupní hodnoty v položek a vlastností.  
  
 \<Project>  
 \<Cíl >  
 \<Úloha >  
 \<Výstup >  
  
## <a name="syntax"></a>Syntaxe  
  
```  
<Output TaskParameter="Parameter"  
    PropertyName="PropertyName"   
    Condition = "'String A' == 'String B'" />  
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
  
|Atribut|Popis|  
|---------------|-----------------|  
|`TaskParameter`|Požadovaný atribut.<br /><br /> Název úkolu výstupní parametr.|  
|`PropertyName`|Buď `PropertyName` nebo `ItemName` atribut je vyžadován.<br /><br /> Vlastnost, která obdrží úkol výstupní hodnota parametru. Váš projekt pak může odkazovat vlastnost s `$(` *PropertyName* `)` syntaxe. Název této vlastnosti může být buď nový název vlastnosti nebo název, který je již definován v projektu.<br /><br /> Tento atribut nedá použít, pokud `ItemName` se také používá.|  
|`ItemName`|Buď `PropertyName` nebo `ItemName` atribut je vyžadován.<br /><br /> Hodnota parametru výstupní položku, která obdrží úkol. Váš projekt pak může odkazovat položka `@(` *ItemName* `)` syntaxe. Název položky může být buď název nové položky nebo název, který je již definován v projektu.<br /><br /> Tento atribut nedá použít, pokud `PropertyName` se také používá.|  
|`Condition`|Nepovinný atribut.<br /><br /> Podmínku, která má být vyhodnocen. Další informace najdete v tématu [podmínky](../msbuild/msbuild-conditions.md).|  
  
### <a name="child-elements"></a>Podřízené elementy  
 Žádné  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[Úloha](../msbuild/task-element-msbuild.md)|Vytvoří a spustí instanci [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] úloh.|  
  
## <a name="example"></a>Příklad  
 Následující příklad kódu ukazuje `Csc` úloh se spouští uvnitř `Target` elementu. Mimo rozsah v tomto příkladu jsou deklarovány položek a vlastností předat parametry úlohy. Hodnota z výstupního parametru `OutputAssembly` je uložen v `FinalAssemblyName` položky a hodnotu z výstupního parametru `BuildSucceeded` je uložen v `BuildWorked` vlastnost. Další informace najdete v tématu [úlohy](../msbuild/msbuild-tasks.md).  
  
```  
<Target Name="Compile" DependsOnTargets="Resources">  
    <Csc  Sources="@(CSFile)"  
            TargetType="library"  
            Resources="@(CompiledResources)"  
            EmitDebugInformation="$(includeDebugInformation)"  
            References="@(Reference)"  
            DebugType="$(debuggingType)"  
            OutputAssembly="$(builtdir)\$(MSBuildProjectName).dll" >  
        <Output TaskParameter="OutputAssembly"  
                  ItemName="FinalAssemblyName" />  
        <Output TaskParameter="BuildSucceeded"  
                  PropertyName="BuildWorked" />  
    </Csc>  
</Target>  
```  
  
## <a name="see-also"></a>Viz také  
 [Referenční dokumentace schématu souboru projektu](../msbuild/msbuild-project-file-schema-reference.md)   
 [Úlohy](../msbuild/msbuild-tasks.md)



