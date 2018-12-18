---
title: Writelinestofile – úloha | Dokumentace Microsoftu
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
- http://schemas.microsoft.com/developer/msbuild/2003#WriteLinesToFile
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- WriteLinesToFile task [MSBuild]
- MSBuild, WriteLinesToFile task
ms.assetid: 9c8862ac-8da5-4437-9430-ecc30421f1c9
caps.latest.revision: 13
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 4af63679437e0b128472d084a55f1ef24a93bc4f
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/12/2018
ms.locfileid: "49301844"
---
# <a name="writelinestofile-task"></a>WriteLinesToFile – úloha
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Zapíše cest zadaných položek do zadaného textového souboru.  
  
## <a name="task-parameters"></a>Parametry úlohy  
 Následující tabulka popisuje parametry `WriteLinestoFile` úloh.  
  
|Parametr|Popis|  
|---------------|-----------------|  
|`File`|Vyžaduje <xref:Microsoft.Build.Framework.ITaskItem> parametru.<br /><br /> Určuje soubor pro zápis položky, které chcete.|  
|`Lines`|Volitelné <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametru.<br /><br /> Určuje položky, které chcete zapisovat do souboru.|  
|`Overwrite`|Volitelné `Boolean` parametru.<br /><br /> Pokud `true`, úloha přepíše veškerý existující obsah v souboru.|  
|`Encoding`|Volitelné `String` parametru.<br /><br /> Vybere kódování, například "Unicode" znaků.  Viz také <xref:System.Text.Encoding>.|  
  
## <a name="remarks"></a>Poznámky  
 Pokud `Overwrite` je `true`, vytvoří nový soubor, zapsat obsah do souboru a pak se soubor zavře. Pokud cílový soubor už existuje, je přepsán. Pokud `Overwrite` je `false`, připojí obsah do souboru, vytváření cílový soubor, pokud ještě neexistuje.  
  
 Kromě výše uvedených parametrů zdědí tento úkol parametry ze <xref:Microsoft.Build.Tasks.TaskExtension> třída, která sama dědí z <xref:Microsoft.Build.Utilities.Task> třídy. Seznam těchto dalších parametrů a jejich popisy najdete v tématu [taskextension – základní třída](../msbuild/taskextension-base-class.md).  
  
## <a name="example"></a>Příklad  
 V následujícím příkladu `WriteLinesToFile` úlohy pro zápis cesty položky v `MyItems` kolekci do souboru určeného položek `MyTextFile` kolekci položek.  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  
    <ItemGroup>  
        <MyTextFile Include="Items.txt"/>  
        <MyItems Include="*.cs"/>  
    </ItemGroup>  
  
    <Target Name="WriteToFile">  
        <WriteLinesToFile  
            File="@(MyTextFile)"  
            Lines="@(MyItems)"  
            Overwrite="true"  
            Encoding="Unicode"/>  
    </Target>  
  
</Project>  
```  
  
## <a name="see-also"></a>Viz také  
 [Úlohy](../msbuild/msbuild-tasks.md)   
 [Referenční dokumentace úlohy](../msbuild/msbuild-task-reference.md)



