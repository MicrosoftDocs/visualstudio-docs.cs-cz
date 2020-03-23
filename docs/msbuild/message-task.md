---
title: Úkol zprávy | Dokumenty společnosti Microsoft
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
ms.openlocfilehash: 264ff3a5e64b756020648e888f7817e12702659f
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "78865359"
---
# <a name="message-task"></a>úloha zprávy

Zaznamená zprávu během sestavení.

## <a name="parameters"></a>Parametry

 Následující tabulka popisuje parametry `Message` úkolu.

|Parametr|Popis|
|---------------|-----------------|
|`Importance`|Volitelný `String` parametr.<br /><br /> Určuje důležitost zprávy. Tento parametr může mít `high` `normal` hodnotu , nebo `low`. Výchozí hodnota je `normal`.|
|`Text`|Volitelný `String` parametr.<br /><br /> Text chyby protokolu.|

## <a name="remarks"></a>Poznámky

 Úkol `Message` umožňuje MSBuild projekty vydávat zprávy úhozy kláves v různých krocích v procesu sestavení.

 Pokud `Condition` parametr vyhodnotí na `true`, `Text` hodnota parametru bude zaznamenána a sestavení bude pokračovat v provádění. Pokud `Condition` parametr neexistuje, je zaznamenán text zprávy. Další informace o protokolování naleznete v [tématu Získání protokolů sestavení](../msbuild/obtaining-build-logs-with-msbuild.md).

 Ve výchozím nastavení je zpráva odeslána všem registrovaným úhozům. Protokolovací protokol `Importance` interpretuje parametr. Obvykle je zpráva nastavena na `high` je odeslána, když <xref:Microsoft.Build.Framework.LoggerVerbosity>je nastavena podrobnost protokolování na .`Minimal` nebo vyšší. Zpráva nastavena `low` na je odeslána, když <xref:Microsoft.Build.Framework.LoggerVerbosity>je nastavena verbosita protokolování na . `Detailed`.

 Kromě výše uvedených parametrů tato úloha dědí <xref:Microsoft.Build.Tasks.TaskExtension> parametry z třídy, <xref:Microsoft.Build.Utilities.Task> která sama dědí z třídy. Seznam těchto dalších parametrů a jejich popisy naleznete v tématu [TaskExtension base class](../msbuild/taskextension-base-class.md).

## <a name="example"></a>Příklad

 Následující příklad kódu protokoluje zprávy všem registrovaným úhozům.

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

- [Odkaz na úkol](../msbuild/msbuild-task-reference.md)
- [Získat protokoly sestavení](../msbuild/obtaining-build-logs-with-msbuild.md)
