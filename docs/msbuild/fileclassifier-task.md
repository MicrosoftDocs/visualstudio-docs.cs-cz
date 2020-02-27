---
title: Úloha klasifikátoru Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- classifying a resource set to embed in an assembly [WPF MSBuild]
- non-localizable resources [WPF MSBuild], classifying to embed in an assembly
- FileClassifier task [WPF MSBuild]
ms.assetid: 14e03310-fcc0-4bb2-a84d-cda12be66367
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 46ed1b1f94cd2ef23ff0704912cb2a2194ba7dab
ms.sourcegitcommit: 96737c54162f5fd5c97adef9b2d86ccc660b2135
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/26/2020
ms.locfileid: "77634185"
---
# <a name="fileclassifier-task"></a>Úloha klasifikátoru

<xref:Microsoft.Build.Tasks.Windows.FileClassifier> úloha klasifikuje sadu zdrojových prostředků jako ty, které budou vloženy do sestavení. Pokud prostředek nelze lokalizovat, je vložen do hlavního sestavení aplikace; v opačném případě je vložen do satelitního sestavení.

## <a name="task-parameters"></a>Parametry úlohy

|Parametr|Popis|
|---------------|-----------------|
|`CLREmbeddedResource`|Nepoužívá se.|
|`CLRResourceFiles`|Nepoužívá se.|
|`CLRSatelliteEmbeddedResource`|Nepoužívá se.|
|`Culture`|Volitelný **řetězcový** parametr.<br /><br /> Určuje jazykovou verzi pro sestavení. Tato hodnota může být **null** , pokud sestavení není lokalizovatelné. Pokud je **null**, výchozí hodnota je malá hodnota, kterou vrací **CultureInfo. InvariantCulture** .|
|`MainEmbeddedFiles`|Volitelný výstupní parametr **ITaskItem []** .<br /><br /> Určuje nelokalizovatelné prostředky, které jsou vloženy do hlavního sestavení.|
|`OutputType`|Povinný parametr **řetězce**<br /><br /> Určuje typ souboru, do kterého se mají vložit zadané zdrojové soubory. Platné hodnoty jsou **exe**, **winexe**nebo **Library**.|
|`SatelliteEmbeddedFiles`|Volitelný výstupní parametr **ITaskItem []** .<br /><br /> Určuje lokalizovatelné soubory, které jsou vloženy do satelitního sestavení pro jazykovou verzi určenou parametrem **jazykové verze** .|
|`SourceFiles`|Povinný parametr **ITaskItem []** .<br /><br /> Určuje seznam souborů, které mají být klasifikovány.|

## <a name="remarks"></a>Poznámky

Pokud parametr **jazykové verze** není nastaven, všechny prostředky, které jsou zadány pomocí parametru **SourceFiles** , jsou nelokalizovatelné; v opačném případě jsou lokalizovatelné, pokud nejsou přidruženy k **lokalizovatelnýmu** atributu, který je nastaven na **hodnotu false**.

## <a name="example"></a>Příklad

Následující příklad klasifikuje jeden zdrojový soubor jako prostředek a pak jej vloží do satelitního sestavení pro jazykovou verzi, která je ve francouzštině kanadská (fr-CA).

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
  <UsingTask
    TaskName="Microsoft.Build.Tasks.Windows.FileClassifier"
    AssemblyFile="C:\Program Files\Reference Assemblies\Microsoft\Framework\v3.0\PresentationBuildTasks.dll" />
  <ItemGroup>
    <Resource Include="Resource1.bmp" />
  </ItemGroup>
  <Target Name="FileClassifierTask">
    <FileClassifier
      SourceFiles="Resource1.bmp"
      Culture="fr-CA"
      OutputType="exe" />
  </Target>
</Project>
```

## <a name="see-also"></a>Viz také

- [Referenční dokumentace WPF MSBuild](../msbuild/wpf-msbuild-reference.md)
- [Odkaz na úkol](../msbuild/wpf-msbuild-task-reference.md)
- [Referenční dokumentace nástroje MSBuild](../msbuild/msbuild-reference.md)
- [Odkaz na úkol](../msbuild/msbuild-task-reference.md)
- [Sestavení aplikace WPF (WPF)](/dotnet/framework/wpf/app-development/building-a-wpf-application-wpf)
