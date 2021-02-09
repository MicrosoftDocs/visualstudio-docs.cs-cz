---
title: Úloha zprávy | Microsoft Docs
description: Přečtěte si o parametrech a nastaveních pro úlohu zprávy nástroje MSBuild, která protokoluje zprávy během sestavení.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: eb2a1837210a5f36577d3bf677a4152033914f49
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99918246"
---
# <a name="message-task"></a>úloha zprávy

Zaprotokoluje zprávu během sestavení.

## <a name="parameters"></a>Parametry

 Následující tabulka popisuje parametry `Message` úkolu.

|Parametr|Popis|
|---------------|-----------------|
|`Importance`|Volitelný `String` parametr.<br /><br /> Určuje důležitost zprávy. Tento parametr může mít hodnotu `high` `normal` nebo `low` . Výchozí hodnota je `normal`.|
|`Text`|Volitelný `String` parametr.<br /><br /> Chybový text, který se má protokolovat|

## <a name="remarks"></a>Poznámky

 `Message`Úloha umožňuje projektům nástroje MSBuild vystavovat zprávy do protokolovacích nástrojů v různých krocích procesu sestavení.

 Pokud se `Condition` parametr vyhodnotí jako `true` , hodnota `Text` parametru se zaprotokoluje a sestavení bude i nadále spuštěno. Pokud `Condition` parametr neexistuje, text zprávy se zaznamená do protokolu. Další informace o protokolování naleznete v tématu [získání protokolů sestavení](../msbuild/obtaining-build-logs-with-msbuild.md).

 Ve výchozím nastavení je zpráva odeslána všem registrovaným protokolovacím nástrojům. Protokolovací nástroj interpretuje `Importance` parametr. Zpráva nastavená na je obvykle `high` odeslána, když je podrobnost protokolovacího nástroje nastavena na <xref:Microsoft.Build.Framework.LoggerVerbosity> .`Minimal` nebo vyšší. Zpráva nastavená na `low` je odeslána, když je podrobnost protokolovacího nástroje nastavena na <xref:Microsoft.Build.Framework.LoggerVerbosity> . `Detailed` .

 Kromě výše uvedených parametrů Tato úloha dědí parametry z <xref:Microsoft.Build.Tasks.TaskExtension> třídy, která sama dědí z <xref:Microsoft.Build.Utilities.Task> třídy. Seznam těchto dalších parametrů a jejich popis naleznete v tématu [TaskExtension – Base Class](../msbuild/taskextension-base-class.md).

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

## <a name="see-also"></a>Viz také

- [Referenční dokumentace úlohy](../msbuild/msbuild-task-reference.md)
- [Získat protokoly sestavení](../msbuild/obtaining-build-logs-with-msbuild.md)
