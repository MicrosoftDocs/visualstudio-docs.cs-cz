---
title: Error – element (MSBuild) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: conceptual
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#OnError
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- OnError Element [MSBuild]
- <OnError Element [MSBuild]
ms.assetid: 765767d3-ecb7-4cd9-ba1e-d9468964dddc
caps.latest.revision: 17
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 46f6907bea5954cffae92b41398717a8247350e0
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "68195664"
---
# <a name="onerror-element-msbuild"></a>OnError – element (MSBuild)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Způsobí provedení jednoho nebo více cílů, pokud `ContinueOnError` je atribut `false` pro neúspěšnou úlohu.  
  
 \<Project>  
 \<Target>  
 \<OnError>  
  
## <a name="syntax"></a>Syntax  
  
```  
<OnError ExecuteTargets="TargetName"  
    Condition="'String A'=='String B'" />  
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
  
|Atribut|Popis|  
|---------------|-----------------|  
|`Condition`|Nepovinný atribut.<br /><br /> Podmínka, která má být vyhodnocena. Další informace najdete v tématu [podmínky](../msbuild/msbuild-conditions.md).|  
|`ExecuteTargets`|Požadovaný atribut.<br /><br /> Cíle, které se mají provést, pokud se úloha nezdařila Více cílů oddělte středníkem. V zadaném pořadí je spuštěno více cílů.|  
  
### <a name="child-elements"></a>Podřízené elementy  
 Žádné  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Element|Popis|  
|-------------|-----------------|  
|[Cílové](../msbuild/target-element-msbuild.md)|Prvek kontejneru pro [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] úlohy.|  
  
## <a name="remarks"></a>Poznámky  
 [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] spustí prvek, je `OnError` -li jeden z `Target` úkolů elementu neúspěšný s `ContinueOnError` atributem nastaveným na `ErrorAndStop` (nebo `false` ). Pokud se úloha nezdařila, cíle zadané v `ExecuteTargets` atributu se spustí. Pokud je v cíli více než jeden `OnError` prvek, `OnError` prvky jsou spouštěny postupně, pokud se úloha nezdařila.  
  
 Informace o atributu naleznete `ContinueOnError` v tématu [element Task (MSBuild)](../msbuild/task-element-msbuild.md). Informace o cílech najdete v tématu [cíle](../msbuild/msbuild-targets.md).  
  
## <a name="example"></a>Příklad  
 Následující kód provede `TaskOne` `TaskTwo` úlohy a. Pokud `TaskOne` dojde k chybě, [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] vyhodnotí `OnError` prvek a provede `OtherTarget` cíl.  
  
```  
<Target Name="ThisTarget">  
    <TaskOne ContinueOnError="ErrorAndStop">  
    </TaskOne>  
    <TaskTwo>  
    </TaskTwo>  
    <OnError ExecuteTargets="OtherTarget" />  
</Target>  
```  
  
## <a name="see-also"></a>Viz také  
 [Referenční dokumentace schématu souboru projektu](../msbuild/msbuild-project-file-schema-reference.md)   
 [Targets](../msbuild/msbuild-targets.md)
