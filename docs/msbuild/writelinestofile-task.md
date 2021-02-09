---
title: Úloha WriteLinesToFile – | Microsoft Docs
description: Naučte se, jak MSBuild používá úlohu WriteLinesToFile – k zápisu cest k zadaným položkám do zadaného textového souboru.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 1f4e2f98f25c43fbd467218ed8777ad5f4a2ecb9
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99887949"
---
# <a name="writelinestofile-task"></a>WriteLinesToFile – úloha

Zapíše cesty zadaných položek do zadaného textového souboru.

## <a name="task-parameters"></a>Parametry úlohy

 Následující tabulka popisuje parametry `WriteLinestoFile` úkolu.

|Parametr|Popis|
|---------------|-----------------|
|`File`|Požadovaný parametr <xref:Microsoft.Build.Framework.ITaskItem>.<br /><br /> Určuje soubor, do kterého budou zapsány položky.|
|`Lines`|Volitelný <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametr.<br /><br /> Určuje položky, které mají být zapsány do souboru. Výchozí hodnota je prázdný seznam.|
|`Overwrite`|Volitelný `Boolean` parametr.<br /><br /> Pokud `true` úloha přepíše veškerý existující obsah v souboru. Výchozí je `false`.|
|`Encoding`|Volitelný `String` parametr.<br /><br /> Vybere kódování znaků, například "Unicode". Výchozí hodnota je UTF-8.  Viz také <xref:System.Text.Encoding> .|
|`WriteOnlyWhenDifferent`|Volitelný `Boolean` parametr.<br /><br /> Pokud je `true` zadaný cílový soubor, pokud existuje, přečte se nejprve a porovná se s tím, co by byl úkol napsán. Pokud je to identické, soubor se nezapisuje na disk a časové razítko se zachová. Výchozí je `false`.|

## <a name="remarks"></a>Poznámky

 Pokud `Overwrite` je `true` , vytvoří nový soubor, zapíše do souboru obsah a pak soubor zavře. Pokud cílový soubor již existuje, bude přepsán. Pokud `Overwrite` je `false` , připojí obsah k souboru a vytvoří cílový soubor, pokud ještě neexistuje.

 Kromě výše uvedených parametrů Tato úloha dědí parametry z <xref:Microsoft.Build.Tasks.TaskExtension> třídy, která sama dědí z <xref:Microsoft.Build.Utilities.Task> třídy. Seznam těchto dalších parametrů a jejich popis naleznete v tématu [TaskExtension – Base Class](../msbuild/taskextension-base-class.md).

## <a name="example"></a>Příklad

 Následující příklad používá `WriteLinesToFile` úlohu k zápisu cest k položkám v `MyItems` kolekci položek do souboru určeného `MyTextFile` kolekcí položek.

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

V tomto příkladu používáme vlastnost s vloženým newlines k zápisu textového souboru s více řádky. Pokud položka `Lines` obsahuje vložené znaky nového řádku, budou nové řádky zahrnuty do výstupního souboru. Tímto způsobem můžete odkazovat na víceřádkové vlastnosti.

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
- [Referenční dokumentace úlohy](../msbuild/msbuild-task-reference.md)
