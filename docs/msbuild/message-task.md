---
title: Zpráva úlohy | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
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
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: a0b61bf9def1ba37667302850527715eed1db4ff
ms.sourcegitcommit: 5b767247b3d819a99deb0dbce729a0562b9654ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/20/2018
ms.locfileid: "39178329"
---
# <a name="message-task"></a>úloha zprávy
Zaznamená zprávu během sestavení.  
  
## <a name="parameters"></a>Parametry  
 Následující tabulka popisuje parametry `Message` úloh.  
  
|Parametr|Popis|  
|---------------|-----------------|  
|`Importance`|Volitelné `String` parametru.<br /><br /> Určuje důležitost zprávy. Tento parametr může mít hodnotu `high`, `normal` nebo `low`. Výchozí hodnota je `normal`.|  
|`Text`|Volitelné `String` parametru.<br /><br /> Text chyby do protokolu.|  
  
## <a name="remarks"></a>Poznámky  
 `Message` Úloha umožňuje [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] projekty se mají problém zprávy protokolovacích nástrojů na jiné kroky v procesu sestavení.  
  
 Pokud `Condition` vyhodnotí jako parametr `true`, hodnota `Text` parametr se zaznamenají a sestavení budou i nadále spouštět. Pokud `Condition` neexistuje parametr, se do protokolu zapíše text zprávy. Další informace o protokolování naleznete v tématu [získat protokoly o sestavení](../msbuild/obtaining-build-logs-with-msbuild.md).  
  
 Ve výchozím nastavení je zpráva odeslána k protokolovací nástroj konzoly nástroje MSBuild. To se dá změnit tak, že nastavíte <xref:Microsoft.Build.Tasks.TaskExtension.Log%2A> parametru. Protokolovací nástroj interpretuje `Importance` parametru.  
  
 Kromě výše uvedených parametrů zdědí tento úkol parametry ze <xref:Microsoft.Build.Tasks.TaskExtension> třída, která sama dědí z <xref:Microsoft.Build.Utilities.Task> třídy. Seznam těchto dalších parametrů a jejich popisy najdete v tématu [taskextension – základní třída](../msbuild/taskextension-base-class.md).  
  
## <a name="example"></a>Příklad  
 Následující příklad kódu zprávy protokolu pro všechna registrovaná protokolovacích nástrojů.  
  
```xml  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    <Target Name="DisplayMessages">  
        <Message Text="Project File Name = $(MSBuildProjectFile)" />  
        <Message Text="Project Extension = $(MSBuildProjectExtension)" />  
    </Target>  
    ...  
</Project>  
```  
  
## <a name="see-also"></a>Viz také:  
 [Referenční dokumentace úlohy](../msbuild/msbuild-task-reference.md)   
 [Získání protokolů o sestavení](../msbuild/obtaining-build-logs-with-msbuild.md)