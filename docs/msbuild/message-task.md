---
title: Úloha zprávy | Microsoft Docs
ms.date: 11/04/2016
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
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c5a2e2a1adb810a8468d318298747eec226846df
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/01/2020
ms.locfileid: "75592175"
---
# <a name="message-task"></a>úloha zprávy
Zaprotokoluje zprávu během sestavení.

## <a name="parameters"></a>Parametry
 Následující tabulka popisuje parametry úlohy `Message`.

|Parametr|Popis|
|---------------|-----------------|
|`Importance`|Volitelný parametr `String`.<br /><br /> Určuje důležitost zprávy. Tento parametr může mít hodnotu `high`, `normal` nebo `low`. Výchozí hodnota je `normal`.|
|`Text`|Volitelný parametr `String`.<br /><br /> Chybový text, který se má protokolovat|

## <a name="remarks"></a>Poznámky
 Úloha `Message` umožňuje projektům [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] vydávat zprávy protokolovacím nástrojům v různých krocích procesu sestavení.

 Pokud je parametr `Condition` vyhodnocen jako `true`, bude hodnota parametru `Text` zaznamenána a sestavení bude nadále spuštěno. Pokud parametr `Condition` neexistuje, text zprávy se zaznamená do protokolu. Další informace o protokolování naleznete v tématu [získání protokolů sestavení](../msbuild/obtaining-build-logs-with-msbuild.md).

 Ve výchozím nastavení se zpráva pošle do protokolovacího nástroje konzoly MSBuild. To lze změnit nastavením parametru <xref:Microsoft.Build.Tasks.TaskExtension.Log%2A>. Protokolovací nástroj interpretuje parametr `Importance`. Zpráva nastavená na `high` se obvykle pošle, když je podrobnost protokolovacího nástroje nastavená na <xref:Microsoft.Build.Framework.LoggerVerbosity>`Minimal` nebo vyšší. Když je podrobnost protokolovacího nástroje nastavená na <xref:Microsoft.Build.Framework.LoggerVerbosity>`Detailed`, pošle se zpráva nastavená na `low`.

 Kromě výše uvedených parametrů Tato úloha dědí parametry z <xref:Microsoft.Build.Tasks.TaskExtension> třídy, které sama dědí z <xref:Microsoft.Build.Utilities.Task> třídy. Seznam těchto dalších parametrů a jejich popis naleznete v tématu [TaskExtension – Base Class](../msbuild/taskextension-base-class.md).

## <a name="example"></a>Příklad
 Následující příklad kódu protokoluje zprávy do všech registrovaných protokolovacích nástrojů.

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
- [Odkaz na úkol](../msbuild/msbuild-task-reference.md)
- [Získat protokoly sestavení](../msbuild/obtaining-build-logs-with-msbuild.md)
