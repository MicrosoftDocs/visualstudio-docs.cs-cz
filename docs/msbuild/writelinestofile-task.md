---
title: Úloha WriteLinesToFile – | Microsoft Docs
ms.date: 09/20/2018
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#WriteLinesToFile
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- WriteLinesToFile task [MSBuild]
- MSBuild, WriteLinesToFile task
ms.assetid: 9c8862ac-8da5-4437-9430-ecc30421f1c9
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b78ac2347a5143aeb532a4bcc294551430584b4a
ms.sourcegitcommit: 96737c54162f5fd5c97adef9b2d86ccc660b2135
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/26/2020
ms.locfileid: "77630662"
---
# <a name="writelinestofile-task"></a>WriteLinesToFile – úloha

Zapíše cesty zadaných položek do zadaného textového souboru.

## <a name="task-parameters"></a>Parametry úlohy

 Následující tabulka popisuje parametry úlohy `WriteLinestoFile`.

|Parametr|Popis|
|---------------|-----------------|
|`File`|Vyžaduje se <xref:Microsoft.Build.Framework.ITaskItem> parametr.<br /><br /> Určuje soubor, do kterého budou zapsány položky.|
|`Lines`|Volitelný <xref:Microsoft.Build.Framework.ITaskItem>`[]` parametr.<br /><br /> Určuje položky, které mají být zapsány do souboru.|
|`Overwrite`|Volitelný parametr `Boolean`.<br /><br /> Pokud `true`, úloha přepíše veškerý existující obsah v souboru.|
|`Encoding`|Volitelný parametr `String`.<br /><br /> Vybere kódování znaků, například "Unicode".  Viz také <xref:System.Text.Encoding>.|
|`WriteOnlyWhenDifferent`|Volitelný parametr `Boolean`.<br /><br /> Pokud `true`, je zadaný cílový soubor, pokud existuje, přečte se nejprve a porovná se s tím, co by byl úkol napsán. Pokud je to identické, soubor se nezapisuje na disk a časové razítko se zachová.|

## <a name="remarks"></a>Poznámky

 Pokud je `Overwrite` `true`, vytvoří nový soubor, zapíše obsah do souboru a potom soubor zavře. Pokud cílový soubor již existuje, bude přepsán. Pokud je `Overwrite` `false`, připojí obsah k souboru a vytvoří cílový soubor, pokud ještě neexistuje.

 Kromě výše uvedených parametrů Tato úloha dědí parametry z <xref:Microsoft.Build.Tasks.TaskExtension> třídy, které sama dědí z <xref:Microsoft.Build.Utilities.Task> třídy. Seznam těchto dalších parametrů a jejich popis naleznete v tématu [TaskExtension – Base Class](../msbuild/taskextension-base-class.md).

## <a name="example"></a>Příklad

 Následující příklad používá úlohu `WriteLinesToFile` k zápisu cest k položkám v kolekci `MyItems` položky do souboru určeného `MyTextFile` kolekcí položek.

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">

    <ItemGroup>
        <MyTextFile Include="Items.txt"/>
        <MyItems Include="*.cs"/>
    </ItemGroup>

    <Target Name="WriteToFile">
        <WriteLinesToFile
            File="@(MyTextFile)"
            Lines="@(MyItems)"
            Overwrite="true"
            Encoding="Unicode"/>
    </Target>

</Project>
```

V tomto příkladu používáme vlastnost s vloženým newlines k zápisu textového souboru s více řádky. Pokud položka v `Lines` obsahovala vložené znaky nového řádku, budou nové řádky zahrnuty do výstupního souboru. Tímto způsobem můžete odkazovat na víceřádkové vlastnosti.

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <OutputType>Exe</OutputType>
    <TargetFramework>netcoreapp2.1</TargetFramework>
  </PropertyGroup>

  <Target Name="WriteLaunchers" AfterTargets="CopyFilesToOutputDirectory">
      <PropertyGroup>
        <LauncherCmd>
@ECHO OFF
dotnet %~dp0$(AssemblyName).dll %*
        </LauncherCmd>
      </PropertyGroup>

      <WriteLinesToFile
        File="$(OutputPath)$(AssemblyName).cmd"
        Overwrite="true"
        Lines="$(LauncherCmd)" />
  </Target>
</Project>
```

## <a name="see-also"></a>Viz také

- [Úlohy](../msbuild/msbuild-tasks.md)
- [Odkaz na úkol](../msbuild/msbuild-task-reference.md)
