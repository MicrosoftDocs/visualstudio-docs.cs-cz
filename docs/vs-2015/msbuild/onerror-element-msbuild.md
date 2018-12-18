---
title: Onerror – Element (MSBuild) | Dokumentace Microsoftu
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
manager: ghogen
ms.openlocfilehash: 10f89d21441418ae0b5c267c0fea7e8451115afe
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/12/2018
ms.locfileid: "49228706"
---
# <a name="onerror-element-msbuild"></a>OnError – element (MSBuild)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Způsobí, že jeden nebo více cílů ke spuštění, pokud `ContinueOnError` atribut je `false` neúspěšné úlohy.  
  
 \<Project>  
 \<Cíl >  
 \<Onerror – >  
  
## <a name="syntax"></a>Syntaxe  
  
```  
<OnError ExecuteTargets="TargetName"  
    Condition="'String A'=='String B'" />  
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
  
|Atribut|Popis|  
|---------------|-----------------|  
|`Condition`|Nepovinný atribut.<br /><br /> Podmínku, která má být vyhodnocen. Další informace najdete v tématu [podmínky](../msbuild/msbuild-conditions.md).|  
|`ExecuteTargets`|Požadovaný atribut.<br /><br /> Cílů ke spuštění neúspěšné úlohy. Několik cílů oddělte středníky. Několik cílů jsou spuštěny v uvedeném pořadí.|  
  
### <a name="child-elements"></a>Podřízené elementy  
 Žádné  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[Cíl](../msbuild/target-element-msbuild.md)|Prvek kontejneru pro [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] úlohy.|  
  
## <a name="remarks"></a>Poznámky  
 [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] Spustí `OnError` element, pokud jeden z `Target` elementu úlohy nezdaří a zobrazí se `ContinueOnError` atribut nastaven na `ErrorAndStop` (nebo `false`). Pokud úloha selže, cíle zadané v `ExecuteTargets` atribut je proveden. Pokud existuje více než jeden `OnError` element v cíli, `OnError` prvky jsou spouštěny postupně, pokud se úloha nezdaří.  
  
 Informace o tom, `ContinueOnError` atributu naleznete v tématu [Task – Element (MSBuild)](../msbuild/task-element-msbuild.md). Informace o cílech naleznete v tématu [cíle](../msbuild/msbuild-targets.md).  
  
## <a name="example"></a>Příklad  
 Následující kód se provádí `TaskOne` a `TaskTwo` úlohy. Pokud `TaskOne` selže, [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] vyhodnotí `OnError` elementu a spustí `OtherTarget` cíl.  
  
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
 [Cíle](../msbuild/msbuild-targets.md)



