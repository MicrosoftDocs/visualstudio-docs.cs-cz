---
title: Úloha WriteLinesToFile – | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: reference
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
manager: jillfra
ms.openlocfilehash: f530648c7dd772fb60148f4d755d4a4ffb420cbb
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "62419956"
---
# <a name="writelinestofile-task"></a>WriteLinesToFile – úloha
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Zapíše cesty zadaných položek do zadaného textového souboru.  
  
## <a name="task-parameters"></a>Parametry úlohy  
 Následující tabulka popisuje parametry `WriteLinestoFile` úkolu.  
  
|Parametr|Popis|  
|---------------|-----------------|  
|`File`|Požadovaný parametr <xref:Microsoft.Build.Framework.ITaskItem>.<br /><br /> Určuje soubor, do kterého budou zapsány položky.|  
|`Lines`|Volitelný <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametr.<br /><br /> Určuje položky, které mají být zapsány do souboru.|  
|`Overwrite`|Volitelný `Boolean` parametr.<br /><br /> Pokud `true` úloha přepíše veškerý existující obsah v souboru.|  
|`Encoding`|Volitelný `String` parametr.<br /><br /> Vybere kódování znaků, například "Unicode".  Viz také <xref:System.Text.Encoding> .|  
  
## <a name="remarks"></a>Poznámky  
 Pokud `Overwrite` je `true` , vytvoří nový soubor, zapíše do souboru obsah a pak soubor zavře. Pokud cílový soubor již existuje, bude přepsán. Pokud `Overwrite` je `false` , připojí obsah k souboru a vytvoří cílový soubor, pokud ještě neexistuje.  
  
 Kromě výše uvedených parametrů Tato úloha dědí parametry z <xref:Microsoft.Build.Tasks.TaskExtension> třídy, která sama dědí z <xref:Microsoft.Build.Utilities.Task> třídy. Seznam těchto dalších parametrů a jejich popis naleznete v tématu [TaskExtension – Base Class](../msbuild/taskextension-base-class.md).  
  
## <a name="example"></a>Příklad  
 Následující příklad používá `WriteLinesToFile` úlohu k zápisu cest k položkám v `MyItems` kolekci položek do souboru určeného `MyTextFile` kolekcí položek.  
  
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
 [Provádění](../msbuild/msbuild-tasks.md)   
 [Odkaz na úkol](../msbuild/msbuild-task-reference.md)
