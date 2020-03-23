---
title: Odstranit úkol | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#Delete
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- Delete task [MSBuild]
- MSBuild, Delete task
ms.assetid: 916bb2e3-3017-4828-ae27-c0b5c99bbb48
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c9effb00c613c5a61a5a8d4d89cbbe5b785601d8
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "77634276"
---
# <a name="delete-task"></a>Delete – úloha

Odstraní zadané soubory.

## <a name="parameters"></a>Parametry

Následující tabulka popisuje parametry `Delete` úkolu.

|Parametr|Popis|
|---------------|-----------------|
|`DeletedFiles`|Volitelný <xref:Microsoft.Build.Framework.ITaskItem> `[]` výstupní parametr.<br /><br /> Určuje soubory, které byly úspěšně odstraněny.|
|`Files`|Požadovaný parametr <xref:Microsoft.Build.Framework.ITaskItem>`[]`.<br /><br /> Určuje soubory, které chcete odstranit.|
|`TreatErrorsAsWarnings`|Volitelný `Boolean` parametr<br /><br /> Pokud `true`jsou chyby zaznamenány jako upozornění. Výchozí hodnota je `false`.|

## <a name="remarks"></a>Poznámky

Kromě výše uvedených parametrů tato úloha dědí <xref:Microsoft.Build.Tasks.TaskExtension> parametry z třídy, <xref:Microsoft.Build.Utilities.Task> která sama dědí z třídy. Seznam těchto dalších parametrů a jejich popisy naleznete v tématu [TaskExtension base class](../msbuild/taskextension-base-class.md).

> [!WARNING]
> Buďte opatrní při použití zástupných znaků s úkolem. `Delete` Můžete snadno odstranit nesprávné soubory s `$(SomeProperty)\**\*.*` `$(SomeProperty)/**/*.*`výrazy jako nebo , zejména v případě, `Files` že vlastnost vyhodnotí na prázdný řetězec, v takovém případě parametr může vyhodnotit do kořenového adresáře jednotky a odstranit mnohem více, než jste chtěli odstranit.

## <a name="example"></a>Příklad

Následující příklad odstraní soubor *MyApp.pdb*.

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">

    <PropertyGroup>
        <AppName>MyApp</AppName>
    </PropertyGroup>

    <Target Name="DeleteFiles">
        <Delete Files="$(AppName).pdb" />
    </Target>
</Project>
```

## <a name="see-also"></a>Viz také

- [Úlohy](../msbuild/msbuild-tasks.md)
- [Odkaz na úkol](../msbuild/msbuild-task-reference.md)
