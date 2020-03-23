---
title: 'Postup: Použití vyhrazených znaků XML v souborech projektu | Dokumenty společnosti Microsoft'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, using reserved XML characters
- MSBuild, reserved XML characters
ms.assetid: 1ae37275-96bf-4e6e-897b-6b048e5bbe93
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a041802af1c2fe8cfa195990e6eda3e9b49d773a
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "77633769"
---
# <a name="how-to-use-reserved-xml-characters-in-project-files"></a>Postup: Použití vyhrazených znaků XML v souborech projektu

Při vytváření souborů projektu může být nutné použít vyhrazené znaky XML, například v hodnotách vlastností nebo v hodnotách parametrů úkolu. Některé vyhrazené znaky však musí být nahrazeny pojmenovanou entitou, aby bylo možné analyzovat soubor projektu.

## <a name="use-reserved-characters"></a>Použití vyhrazených znaků

 Následující tabulka popisuje vyhrazené znaky XML, které musí být nahrazeny odpovídající pojmenovanou entitou, aby bylo možné analyzovat soubor projektu.

|Vyhrazený znak|Snázvem entita|
|------------------------|------------------|
|\<|&amp;To;|
|>|&amp;gt;|
|&|&amp;a)|
|"|&amp;quot;|
|'|&amp;apos;|

#### <a name="to-use-double-quotes-in-a-project-file"></a>Použití dvojitých uvozovek v souboru projektu

- Nahraďte dvojité uvozovky &amp;odpovídající pojmenovanou entitou, quot;. Chcete-li například umístit `EXEFile` dvojité uvozovky kolem seznamu položek, zadejte:

    ```xml
    <Message Text="The output file is &quot;@(EXEFile)&quot;."/>
    ```

## <a name="example"></a>Příklad

 V následujícím příkladu kódu se dvojité uvozovky používají ke zvýraznění názvu souboru ve zprávě, která je výstupem souboru projektu.

```xml
<Project DefaultTargets="Compile"
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003" >
    <!-- Set the application name as a property -->
    <PropertyGroup>
        <appname>"HelloWorldCS"</appname>
    </PropertyGroup>
    <!-- Specify the inputs -->
    <ItemGroup>
        <CSFile Include = "consolehwcs1.cs" />
    </ItemGroup>
    <Target Name = "Compile">
        <!-- Run the Visual C# compilation using input
        files of type CSFile -->
        <Csc Sources = "@(CSFile)">
            <!-- Set the OutputAssembly attribute of the CSC task
            to the name of the executable file that is created -->
            <Output
                TaskParameter = "OutputAssembly"
                ItemName = "EXEFile"/>
        </Csc>
        <!-- Log the file name of the output file -->
        <Message Text="The output file is &quot;@(EXEFile)&quot;."/>
    </Target>
</Project>
```

## <a name="see-also"></a>Viz také

- [Odkaz na sestavení msbuild](../msbuild/msbuild-reference.md)
- [Msbuild](../msbuild/msbuild.md)
