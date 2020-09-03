---
title: Úloha zprávy | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#Message
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, Message task
- Message task [MSBuild]
ms.assetid: 2293309d-42b6-46dc-9684-8c146f66bc28
caps.latest.revision: 27
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 48e867cd0993106247f7105c1102f4e1407a4fed
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "68190905"
---
# <a name="message-task"></a>Úlohy zpráv
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Zaprotokoluje zprávu během sestavení.  
  
## <a name="parameters"></a>Parametry  
 Tabulka tato popisuje parametry `Message` úkolu.  
  
|Parametr|Popis|  
|---------------|-----------------|  
|`Importance`|Volitelný `String` parametr.<br /><br /> Určuje důležitost zprávy. Tento parametr může mít hodnotu `high` `normal` nebo `low` . Výchozí hodnota je `normal`.|  
|`Text`|Volitelný `String` parametr.<br /><br /> Chybový text, který se má protokolovat|  
  
## <a name="remarks"></a>Poznámky  
 `Message`Úloha umožňuje [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] projektům vystavovat zprávy do protokolovacích nástrojů v různých krocích procesu sestavení.  
  
 Pokud se `Condition` parametr vyhodnotí jako `true` , hodnota `Text` parametru se zaprotokoluje a sestavení bude i nadále spuštěno. Pokud `Condition` parametr neexistuje, text zprávy se zaznamená do protokolu. Další informace o protokolování naleznete v tématu [získání protokolů sestavení](../msbuild/obtaining-build-logs-with-msbuild.md).  
  
 Ve výchozím nastavení se zpráva pošle do protokolovacího nástroje konzoly MSBuild. To lze změnit nastavením <xref:Microsoft.Build.Tasks.TaskExtension.Log%2A> parametru. Protokolovací nástroj interpretuje `Importance` parametr.  
  
 Kromě výše uvedených parametrů Tato úloha dědí parametry z <xref:Microsoft.Build.Tasks.TaskExtension> třídy, která sama dědí z <xref:Microsoft.Build.Utilities.Task> třídy. Seznam těchto dalších parametrů a jejich popis naleznete v tématu [TaskExtension – Base Class](../msbuild/taskextension-base-class.md).  
  
## <a name="example"></a>Příklad  
 Následující příklad kódu protokoluje zprávy do všech registrovaných protokolovacích nástrojů.  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    <Target Name="DisplayMessages">  
        <Message Text="Project File Name = $(MSBuildProjectFile)" />  
        <Message Text="Project Extension = $(MSBuildProjectExtension)" />  
    </Target>  
    ...  
</Project>  
```  
  
## <a name="see-also"></a>Viz také  
 [Odkaz na úkol](../msbuild/msbuild-task-reference.md)   
 [Získávání protokolů o sestavení](../msbuild/obtaining-build-logs-with-msbuild.md)
