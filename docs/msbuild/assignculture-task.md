---
title: Úkol AssignCulture | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#AssignCulture
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, AssignCulture task
- AssignCulture task [MSBuild]
ms.assetid: 8f8314cc-82a6-4f16-a62d-b9f0d1d5e274
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: aa9f7bb47efefa3f7a1d4cf52cbfa5891602956f
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "77634562"
---
# <a name="assignculture-task"></a>AssignCulture – úloha

Tato úloha přijímá seznam položek, které mohou obsahovat platný řetězec identifikátoru jazykové verze .NET jako `Culture` součást názvu souboru, a vytvoří položky, které mají metadata s názvem obsahující odpovídající identifikátor jazykové verze. Například název souboru *Form1.fr-fr.resx* má vložený identifikátor jazykové verze "fr-fr", takže tato úloha vytvoří `Culture` položku, která má stejný název souboru s metadaty rovnými `fr-fr`. Úloha také vytvoří seznam názvů souborů s jazykovou verzí odebránou z názvu souboru.

## <a name="task-parameters"></a>Parametry úlohy

Následující tabulka popisuje parametry `AssignCulture` úkolu.

|Parametr|Popis|
|---------------|-----------------|
|`AssignedFiles`|Volitelný <xref:Microsoft.Build.Framework.ITaskItem> `[]` výstupní parametr.<br /><br /> Obsahuje seznam položek přijatých `Files` v parametru s přidanou položkou `Culture` metadat ke každé položce.<br /><br /> Pokud příchozí položka z `Files` parametru `Culture` již obsahuje položku metadat, použije se původní položka metadat.<br /><br /> Úkol přiřadí položku metadat pouze v `Culture` případě, že název souboru obsahuje platný identifikátor jazykové verze. Identifikátor jazykové verze musí být mezi posledními dvěma tečkami v názvu souboru.|
|`AssignedFilesWithCulture`|Volitelný <xref:Microsoft.Build.Framework.ITaskItem> `[]` výstupní parametr.<br /><br /> Obsahuje podmnožinu položek `AssignedFiles` z parametru, které mají položku `Culture` metadat.|
|`AssignedFilesWithNoCulture`|Volitelný <xref:Microsoft.Build.Framework.ITaskItem> `[]` výstupní parametr.<br /><br /> Obsahuje podmnožinu položek `AssignedFiles` z parametru, `Culture` které nemají položku metadat.|
|`CultureNeutralAssignedFiles`|Volitelný <xref:Microsoft.Build.Framework.ITaskItem> `[]` výstupní parametr.<br /><br /> Obsahuje stejný seznam položek, které `AssignedFiles` jsou vytvořeny v parametru, s výjimkou jazykové verze odebrány z názvu souboru.<br /><br /> Úloha odebere jazykovou verzi z názvu souboru pouze v případě, že se jedná o platný identifikátor jazykové verze.|
|`Files`|Požadovaný parametr <xref:Microsoft.Build.Framework.ITaskItem>`[]`.<br /><br /> Určuje seznam souborů s vloženými názvy jazykové verze, ke kterým má být jazyková verze přiřazena.|

## <a name="remarks"></a>Poznámky

Kromě výše uvedených parametrů tato úloha dědí <xref:Microsoft.Build.Tasks.TaskExtension> parametry z třídy, <xref:Microsoft.Build.Utilities.Task> která sama dědí z třídy. Seznam těchto dalších parametrů a jejich popisy naleznete v tématu [TaskExtension base class](../msbuild/taskextension-base-class.md).

## <a name="example"></a>Příklad

 Následující příklad provede `AssignCulture` úlohu `ResourceFiles` s kolekcí položek.

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
    <ItemGroup>
        <ResourceFiles Include="MyResource1.fr.resx"/>
        <ResourceFiles Include="MyResource2.XX.resx"/>
    </ItemGroup>

    <Target Name="Culture">
        <AssignCulture
            Files="@(ResourceFiles)"
            <Output TaskParameter="AssignedFiles"
                ItemName="OutAssignedFiles"/>
            <Output TaskParameter="AssignedFilesWithCulture"
                ItemName="OutAssignedFilesWithCulture"/>
            <Output TaskParameter="AssignedFilesWithNoCulture"
                ItemName="OutAssignedFilesWithNoCulture"/>
            <Output TaskParameter="CultureNeutralAssignedFiles"
                ItemName="OutCultureNeutralAssignedFiles"/>
        </AssignCulture>
    </Target>
</Project>
```

Následující tabulka popisuje hodnotu výstupních položek po provedení úlohy. Metadata položky jsou zobrazena v závorce za položkou.

|Kolekce položek|Obsah|
|---------------------|--------------|
|`OutAssignedFiles`|*MyResource1.fr.resx* (Kultura="fr")<br /><br /> *MyResource2.XX.resx* (žádná další metadata)|
|`OutAssignedFilesWithCulture`|*MyResource1.fr.resx* (Kultura="fr")|
|`OutAssignedFilesWithNoCulture`|*MyResource2.XX.resx* (žádná další metadata)|
|`OutCultureNeutralAssignedFiles`|*MyResource1.resx* (Kultura="fr")<br /><br /> *MyResource2.XX.resx* (žádná další metadata)|

## <a name="see-also"></a>Viz také

- [Úlohy](../msbuild/msbuild-tasks.md)
- [Odkaz na úkol](../msbuild/msbuild-task-reference.md)
