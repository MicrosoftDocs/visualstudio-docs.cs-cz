---
title: 'Postup: Odkaz na název nebo umístění souboru projektu | Dokumenty společnosti Microsoft'
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 2b54a63b135f844ff20b45ffac430662c4df1f19
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "77633834"
---
# <a name="how-to-reference-the-name-or-location-of-the-project-file"></a>Postup: Odkaz na název nebo umístění souboru projektu

Název nebo umístění projektu můžete použít v samotném souboru projektu, aniž byste museli vytvářet vlastní vlastnost. MSBuild poskytuje vyhrazené vlastnosti, které odkazují na název souboru projektu a další vlastnosti související s projektem. Další informace o rezervovaných vlastnostech naleznete v [tématu MSBuild reserved and well-known properties](../msbuild/msbuild-reserved-and-well-known-properties.md).

## <a name="use-the-project-properties"></a>Použití vlastností projektu

 MSBuild poskytuje některé vyhrazené vlastnosti, které můžete použít v souborech projektu bez jejich definování pokaždé. Například rezervovaná `MSBuildProjectName` vlastnost poskytuje odkaz na název souboru projektu. Rezervovaná `MSBuildProjectDirectory` vlastnost poskytuje odkaz na umístění souboru projektu.

#### <a name="to-use-the-project-properties"></a>Použití vlastností projektu

- Odkaz na vlastnost v souboru projektu s $() zápis, stejně jako u jakékoli vlastnosti. Například:

  ```xml
  <CSC Sources = "@(CSFile)"
      OutputAssembly = "$(MSBuildProjectName).exe"/>
  </CSC>
  ```

  Výhodou použití vyhrazené vlastnosti je, že všechny změny názvu souboru projektu jsou začleněny automaticky. Při příštím sestavení projektu bude mít výstupní soubor nový název bez nutnosti další akce z vaší strany.

  Další informace o použití speciálních znaků v odkazech na soubory nebo projekty naleznete v tématu [MSBuild special characters](../msbuild/msbuild-special-characters.md).

> [!NOTE]
> Rezervované vlastnosti nelze v souboru projektu znovu definovat.

## <a name="example"></a>Příklad

 Následující příklad souboru projektu odkazuje na název projektu jako rezervovanou vlastnost, která určuje název výstupu.

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

## <a name="example"></a>Příklad

 Následující ukázkový soubor `MSBuildProjectDirectory` projektu používá rezervovanou vlastnost k vytvoření úplné cesty k souboru v umístění souboru projektu.

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">

    <!-- Build the path to a file in the root of the project -->
    <PropertyGroup>
        <NewFilePath>$([System.IO.Path]::Combine($(MSBuildProjectDirectory), `BuildInfo.txt`))</NewFilePath>
    </PropertyGroup>
</Project>
```

Příklad používá syntaxi [funkce Vlastnost](property-functions.md) k volání <xref:System.IO.Path.Combine*?displayProperty=fullName>statické metody rozhraní .NET Framework .

## <a name="see-also"></a>Viz také

- [Msbuild](../msbuild/msbuild.md)
- [Vyhrazené a dobře známé vlastnosti msbuild](../msbuild/msbuild-reserved-and-well-known-properties.md)
