---
title: Odkazování na název nebo umístění souboru projektu
description: Naučte se používat rezervované vlastnosti MSBuild k odkazování na název nebo umístění souboru projektu bez nutnosti vytvářet vlastní vlastnosti.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- locations, referencing
- locations
- MSBuildProjectName property
- MSBuild, referencing the project file
- names, referencing
- reserved properties
- project files, referencing
ms.assetid: c8fcc594-5d37-4e2e-b070-4d9c012043b5
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: c6527a4f54abf147d54e73c8f887b57b70ff4243
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99914184"
---
# <a name="how-to-reference-the-name-or-location-of-the-project-file"></a>Postupy: odkazování na název nebo umístění souboru projektu

Můžete použít název nebo umístění projektu v samotném souboru projektu, aniž by bylo nutné vytvořit vlastní vlastnost. Nástroj MSBuild poskytuje vyhrazené vlastnosti, které odkazují na název souboru projektu a další vlastnosti, které se vztahují k projektu. Další informace o vyhrazených vlastnostech naleznete v tématu [vyhrazené a dobře známé vlastnosti nástroje MSBuild](../msbuild/msbuild-reserved-and-well-known-properties.md).

## <a name="use-the-project-properties"></a>Použití vlastností projektu

 Nástroj MSBuild poskytuje některé vyhrazené vlastnosti, které lze použít v souborech projektu bez jejich definování pokaždé. Například vyhrazená vlastnost `MSBuildProjectName` poskytuje odkaz na název souboru projektu. Vyhrazená vlastnost `MSBuildProjectDirectory` poskytuje odkaz na umístění souboru projektu.

#### <a name="to-use-the-project-properties"></a>Použití vlastností projektu

- Odkazujte na vlastnost v souboru projektu pomocí notace $ (), stejně jako u libovolné vlastnosti. Příklad:

  ```xml
  <CSC Sources = "@(CSFile)"
      OutputAssembly = "$(MSBuildProjectName).exe"/>
  </CSC>
  ```

  Výhodou použití rezervované vlastnosti je, že všechny změny názvu souboru projektu jsou začleněny automaticky. Při příštím sestavení projektu bude mít výstupní soubor nový název, který nevyžaduje žádnou další akci.

  Další informace o použití speciálních znaků v odkazech na soubor nebo projekt naleznete v tématu [speciální znaky nástroje MSBuild](../msbuild/msbuild-special-characters.md).

> [!NOTE]
> Rezervované vlastnosti nelze předefinovat v souboru projektu.

## <a name="example-1"></a>Příklad 1

 Následující příklad souboru projektu odkazuje na název projektu jako vyhrazená vlastnost k určení názvu výstupu.

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003"
    DefaultTargets = "Compile">

    <!-- Specify the inputs -->
    <ItemGroup>
        <CSFile Include = "consolehwcs1.cs"/>
     </ItemGroup>
    <Target Name = "Compile">
        <!-- Run the Visual C# compilation using
        input files of type CSFile -->
        <CSC Sources = "@(CSFile)"
            OutputAssembly = "$(MSBuildProjectName).exe" >
            <!-- Set the OutputAssembly attribute of the CSC task
            to the name of the project -->
            <Output
                TaskParameter = "OutputAssembly"
                ItemName = "EXEFile" />
        </CSC>
        <!-- Log the file name of the output file -->
        <Message Text="The output file is @(EXEFile)"/>
    </Target>
</Project>
```

## <a name="example-2"></a>Příklad 2

 Následující příklad souboru projektu používá `MSBuildProjectDirectory` vyhrazenou vlastnost k vytvoření úplné cesty k souboru v umístění souboru projektu.

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">

    <!-- Build the path to a file in the root of the project -->
    <PropertyGroup>
        <NewFilePath>$([System.IO.Path]::Combine($(MSBuildProjectDirectory), `BuildInfo.txt`))</NewFilePath>
    </PropertyGroup>
</Project>
```

V příkladu se používá syntaxe [funkce Property](property-functions.md) pro volání statické metody .NET Framework <xref:System.IO.Path.Combine*?displayProperty=fullName> .

## <a name="see-also"></a>Viz také

- [MSBuild](../msbuild/msbuild.md)
- [Vyhrazené a známé vlastnosti nástroje MSBuild](../msbuild/msbuild-reserved-and-well-known-properties.md)
