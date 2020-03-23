---
title: Úloha třídění souborů | Dokumenty společnosti Microsoft
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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "77634185"
---
# <a name="fileclassifier-task"></a>Úloha třídy souborů

Úloha <xref:Microsoft.Build.Tasks.Windows.FileClassifier> klasifikuje sadu zdrojových prostředků jako ty, které budou vloženy do sestavení. Pokud prostředek není lokalizovatelný, je vložen do sestavení hlavní aplikace; v opačném případě je vložen do satelitního sestavení.

## <a name="task-parameters"></a>Parametry úlohy

|Parametr|Popis|
|---------------|-----------------|
|`CLREmbeddedResource`|Nepoužívá se.|
|`CLRResourceFiles`|Nepoužívá se.|
|`CLRSatelliteEmbeddedResource`|Nepoužívá se.|
|`Culture`|Volitelný **parametr String.**<br /><br /> Určuje jazykovou verzi sestavení. Tato hodnota může být **null,** pokud sestavení je non-lokalizovatelné. Pokud **null**, výchozí hodnota je malá hodnota, která **CultureInfo.InvariantCulture** vrátí.|
|`MainEmbeddedFiles`|Volitelný výstupní parametr **ITaskItem[].**<br /><br /> Určuje nelokalizovatelné prostředky, které jsou vloženy do hlavního sestavení.|
|`OutputType`|Povinný **parametr String.**<br /><br /> Určuje typ souboru, do který chcete vložit zadané zdrojové soubory. Platné hodnoty jsou **exe**, **winexe**nebo **knihovna**.|
|`SatelliteEmbeddedFiles`|Volitelný výstupní parametr **ITaskItem[].**<br /><br /> Určuje lokalizovatelné soubory, které jsou vloženy do satelitního sestavení pro jazykovou verzi určenou parametrem **Culture.**|
|`SourceFiles`|Povinný parametr **ITaskItem[].**<br /><br /> Určuje seznam souborů, které chcete klasifikovat.|

## <a name="remarks"></a>Poznámky

Pokud není nastaven parametr **Culture,** všechny prostředky, které jsou určeny pomocí **SourceFiles** parametr jsou non-lokalizovatelné; v opačném případě jsou lokalizovatelné, pokud nejsou spojeny s **lokalizovatelný** atribut, který je nastaven na **false**.

## <a name="example"></a>Příklad

Následující příklad klasifikuje jeden zdrojový soubor jako prostředek a potom jej vloží do satelitního sestavení pro francouzsko-kanadskou (fr-CA) jazykovou verzi.

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

- [WPF MSBuild odkaz](../msbuild/wpf-msbuild-reference.md)
- [Odkaz na úkol](../msbuild/wpf-msbuild-task-reference.md)
- [Odkaz na sestavení msbuild](../msbuild/msbuild-reference.md)
- [Odkaz na úkol](../msbuild/msbuild-task-reference.md)
- [Vytvoření aplikace WPF (WPF)](/dotnet/framework/wpf/app-development/building-a-wpf-application-wpf)
