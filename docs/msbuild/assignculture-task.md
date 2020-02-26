---
title: Úloha AssignCulture – | Microsoft Docs
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
ms.openlocfilehash: 393077d6391a5c1f5f4088773013538efbedc9f7
ms.sourcegitcommit: 2ae2436dc3484b9dfa10e0483afba1e5a02a52eb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/25/2020
ms.locfileid: "77578708"
---
# <a name="assignculture-task"></a>AssignCulture – úloha
Tato úloha přijímá seznam položek, které mohou obsahovat platný řetězec identifikátoru kultury rozhraní .NET jako součást názvu souboru a vytváří položky, které mají metadata s názvem `Culture` obsahující odpovídající identifikátor jazykové verze. Například název souboru *Form1.fr-fr. resx* má vloženou identifikátor jazykové verze "fr-FR", takže tato úloha vytvoří položku, která má stejný název souboru s metadaty `Culture` rovna `fr-fr`. Úloha také vytvoří seznam názvů souborů s jazykovou verzí odebraným z názvu souboru.

## <a name="task-parameters"></a>Parametry úlohy
Následující tabulka popisuje parametry úlohy `AssignCulture`.

|Parametr|Popis|
|---------------|-----------------|
|`AssignedFiles`|Volitelný <xref:Microsoft.Build.Framework.ITaskItem>parametr Output `[]`.<br /><br /> Obsahuje seznam položek přijatých v parametru `Files` s položkou `Culture` metadata přidané do každé položky.<br /><br /> Pokud příchozí položka z parametru `Files` již obsahuje položku `Culture` metadata, použije se původní položka metadat.<br /><br /> Tato úloha přiřadí položku metadat `Culture` pouze v případě, že název souboru obsahuje platný identifikátor jazykové verze. Identifikátor jazykové verze musí být mezi posledními dvěma tečkami v názvu souboru.|
|`AssignedFilesWithCulture`|Volitelný <xref:Microsoft.Build.Framework.ITaskItem>parametr Output `[]`.<br /><br /> Obsahuje podmnožinu položek z parametru `AssignedFiles`, který má položku `Culture` metadat.|
|`AssignedFilesWithNoCulture`|Volitelný <xref:Microsoft.Build.Framework.ITaskItem>parametr Output `[]`.<br /><br /> Obsahuje podmnožinu položek z parametru `AssignedFiles`, který nemá položku `Culture` metadata.|
|`CultureNeutralAssignedFiles`|Volitelný <xref:Microsoft.Build.Framework.ITaskItem>parametr Output `[]`.<br /><br /> Obsahuje stejný seznam položek, které jsou vytvořeny v parametru `AssignedFiles`, s výjimkou jazykové verze odebrané z názvu souboru.<br /><br /> Úloha odebere jazykovou verzi z názvu souboru pouze v případě, že se jedná o platný identifikátor jazykové verze.|
|`Files`|Požadovaný parametr <xref:Microsoft.Build.Framework.ITaskItem>`[]`.<br /><br /> Určuje seznam souborů s vloženou kulturou názvů, pro které má být přiřazena jazyková verze.|

## <a name="remarks"></a>Poznámky
Kromě výše uvedených parametrů Tato úloha dědí parametry z <xref:Microsoft.Build.Tasks.TaskExtension> třídy, které sama dědí z <xref:Microsoft.Build.Utilities.Task> třídy. Seznam těchto dalších parametrů a jejich popis naleznete v tématu [TaskExtension – Base Class](../msbuild/taskextension-base-class.md).

## <a name="example"></a>Příklad
 Následující příklad spustí úlohu `AssignCulture` s kolekcí `ResourceFiles` Item.

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

Následující tabulka popisuje hodnotu výstupních položek po provedení úkolu. Metadata položky se zobrazí v závorkách za položkou.

|Kolekce položek|Obsah|
|---------------------|--------------|
|`OutAssignedFiles`|*MyResource1. fr. resx* (Culture = "fr")<br /><br /> *MyResource2. xx. resx* (žádná další metadata)|
|`OutAssignedFilesWithCulture`|*MyResource1. fr. resx* (Culture = "fr")|
|`OutAssignedFilesWithNoCulture`|*MyResource2. xx. resx* (žádná další metadata)|
|`OutCultureNeutralAssignedFiles`|*MyResource1. resx* (Culture = "fr")<br /><br /> *MyResource2. xx. resx* (žádná další metadata)|

## <a name="see-also"></a>Viz také
- [Úlohy](../msbuild/msbuild-tasks.md)
- [Odkaz na úkol](../msbuild/msbuild-task-reference.md)
