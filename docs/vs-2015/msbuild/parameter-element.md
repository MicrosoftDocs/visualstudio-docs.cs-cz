---
title: Parameter – Element | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- Parameter element [MSBuild]
- <Parameter> element [MSBuild]
ms.assetid: b273afff-b500-4e97-8cfd-31f39fa64a51
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 632973aab0447ffcd8d2bff5e752683223ea3838
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49844481"
---
# <a name="parameter-element"></a>Parameter – element
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Obsahuje informace o určitý parametr u úkolu, který je generován `UsingTask``TaskFactory`.  Název elementu je název parametru.  Další informace najdete v části [usingtask – Element (MSBuild)](../msbuild/usingtask-element-msbuild.md).  
  
 \<Project>  
 \<Usingtask – >  
 \<Parametergroup – >  
 \<Parametr >  
  
## <a name="syntax"></a>Syntaxe  
  
```  
<ParameterGroup ParameterType="SystemType"  
    Output="true/false"  
    Required="true/false" />  
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
  
|Atribut|Popis|  
|---------------|-----------------|  
|`ParameterType`|Nepovinný atribut.<br /><br /> .NET typ parametru, například "System.String".|  
|`Output`|Volitelný logický atribut.<br /><br /> Pokud `true`, tento parametr je výstupní parametr pro úlohu. Výchozí hodnota je `false`.|  
|`Required`|Volitelný logický atribut.<br /><br /> Pokud `true`, tento parametr je povinný parametr pro úlohu. Výchozí hodnota je `false`.|  
  
### <a name="child-elements"></a>Podřízené elementy  
 Žádné  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[ParameterGroup](../msbuild/parametergroup-element.md)|Obsahuje volitelný seznam parametrů, které bude k dispozici na na úkol, který je generován `UsingTask``TaskFactory`.|  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje způsob použití `Parameter` elementu.  
  
```  
<UsingTask TaskName="MyTask" AssemblyName="My.Assembly" TaskFactory="MyTaskFactory">  
       <ParameterGroup>  
              <Parameter1 ParameterType="System.String" Required="False" Output="False"/>  
              <Parameter2 ParameterType="System.Int" Required="True" Output="False"/>  
             ...  
</ParameterGroup>  
       <TaskBody Evaluate="true">  
      ... Task factory-specific data ...  
       </TaskBody>  
</UsingTask>  
```  
  
## <a name="see-also"></a>Viz také  
 [Úlohy](../msbuild/msbuild-tasks.md)   
 [Referenční dokumentace úlohy](../msbuild/msbuild-task-reference.md)   
 [Referenční dokumentace schématu souboru projektu](../msbuild/msbuild-project-file-schema-reference.md)



