---
title: Úloha WriteLinesToFile | Dokumenty společnosti Microsoft
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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "77630662"
---
# <a name="writelinestofile-task"></a>WriteLinesToFile – úloha

Zapíše cesty určených položek do zadaného textového souboru.

## <a name="task-parameters"></a>Parametry úlohy

 Následující tabulka popisuje parametry `WriteLinestoFile` úkolu.

|Parametr|Popis|
|---------------|-----------------|
|`File`|Požadovaný parametr <xref:Microsoft.Build.Framework.ITaskItem>.<br /><br /> Určuje soubor, do který má být položky zapsány.|
|`Lines`|Volitelný <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametr.<br /><br /> Určuje položky, které mají být zapsány do souboru.|
|`Overwrite`|Volitelný `Boolean` parametr.<br /><br /> Pokud `true`úkol přepíše existující obsah v souboru.|
|`Encoding`|Volitelný `String` parametr.<br /><br /> Vybere kódování znaků, například "Unicode".  Viz <xref:System.Text.Encoding>také .|
|`WriteOnlyWhenDifferent`|Volitelný `Boolean` parametr.<br /><br /> Pokud `true`, cílový soubor zadaný, pokud existuje, bude číst jako první porovnat s co by byl napsán úkol. Pokud je totožný, soubor není zapsán na disk a časové razítko bude zachováno.|

## <a name="remarks"></a>Poznámky

 Pokud `Overwrite` `true`je , vytvoří nový soubor, zapisuje obsah do souboru a zavře soubor. Pokud cílový soubor již existuje, je přepsán. Pokud `Overwrite` `false`je , připojí obsah k souboru, vytvoření cílového souboru, pokud ještě neexistuje.

 Kromě výše uvedených parametrů tato úloha dědí <xref:Microsoft.Build.Tasks.TaskExtension> parametry z třídy, <xref:Microsoft.Build.Utilities.Task> která sama dědí z třídy. Seznam těchto dalších parametrů a jejich popisy naleznete v tématu [TaskExtension base class](../msbuild/taskextension-base-class.md).

## <a name="example"></a>Příklad

 Následující příklad používá `WriteLinesToFile` úlohu k zápisu cest `MyItems` položek v kolekci položek `MyTextFile` do souboru určeného kolekcí položek.

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

V tomto příkladu používáme vlastnost s vloženými novými řádky k zápisu textového souboru s více řádky. Pokud má `Lines` položka v aplikaci vložené znaky nového řádku, budou nové řádky zahrnuty do výstupního souboru. Tímto způsobem můžete odkazovat na víceřádkové vlastnosti.

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
