---
title: Writelinestofile – úloha | Dokumentace Microsoftu
ms.custom: ''
ms.date: 09/20/2018
ms.technology: msbuild
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
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 909c35ca889295385cae98d51a81b22b4f7eb5d8
ms.sourcegitcommit: 95aedf723c6be5272c3c5a2911cb2bdec50e2148
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/26/2018
ms.locfileid: "47228835"
---
# <a name="writelinestofile-task"></a>WriteLinesToFile – úloha
Zapíše cest zadaných položek do zadaného textového souboru.  
  
## <a name="task-parameters"></a>Parametry úlohy  
 Následující tabulka popisuje parametry `WriteLinestoFile` úloh.  
  
|Parametr|Popis|  
|---------------|-----------------|  
|`File`|Vyžaduje <xref:Microsoft.Build.Framework.ITaskItem> parametru.<br /><br /> Určuje soubor pro zápis položky, které chcete.|  
|`Lines`|Volitelné <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametru.<br /><br /> Určuje položky, které chcete zapisovat do souboru.|  
|`Overwrite`|Volitelné `Boolean` parametru.<br /><br /> Pokud `true`, úloha přepíše veškerý existující obsah v souboru.|  
|`Encoding`|Volitelné `String` parametru.<br /><br /> Vybere kódování, například "Unicode" znaků.  Viz také <xref:System.Text.Encoding>.|  
|`WriteOnlyWhenDifferent`|Volitelné `Boolean` parametru.<br /><br /> Pokud `true`, cílový soubor, který je zadán, pokud existuje, bude číst nejprve k porovnání, co by vytvořilo úlohu. Pokud shodné, soubor není zapsán na disk a časové razítko zůstane zachovaná.|  

## <a name="remarks"></a>Poznámky  
 Pokud `Overwrite` je `true`, vytvoří nový soubor, zapsat obsah do souboru a pak se soubor zavře. Pokud cílový soubor už existuje, je přepsán. Pokud `Overwrite` je `false`, připojí obsah do souboru, vytváření cílový soubor, pokud ještě neexistuje.  
  
 Kromě výše uvedených parametrů zdědí tento úkol parametry ze <xref:Microsoft.Build.Tasks.TaskExtension> třída, která sama dědí z <xref:Microsoft.Build.Utilities.Task> třídy. Seznam těchto dalších parametrů a jejich popisy najdete v tématu [taskextension – základní třída](../msbuild/taskextension-base-class.md).  
  
## <a name="example"></a>Příklad  
 V následujícím příkladu `WriteLinesToFile` úlohy pro zápis cesty položky v `MyItems` kolekci do souboru určeného položek `MyTextFile` kolekci položek.  
  
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

V tomto příkladu používáme vlastnost s vložený tabulátorů pro zápis do textového souboru s více řádky. Pokud položka v `Lines` obsahuje vložené znaky nového řádku, nové řádky se zahrnou do výstupního souboru. Tímto způsobem můžete odkazovat na více řádků vlastnosti.

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
  
## <a name="see-also"></a>Viz také:  
 [Úlohy](../msbuild/msbuild-tasks.md)   
 [Referenční dokumentace úlohy](../msbuild/msbuild-task-reference.md)
