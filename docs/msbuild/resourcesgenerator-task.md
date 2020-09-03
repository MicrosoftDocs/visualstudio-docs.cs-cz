---
title: Úloha ResourcesGenerator – | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- embedding resources into a .resources file [WPF MSBuild]
- ResourcesGenerator task [WPF MSBuild]
- ResourcesGenerator task [WPF MSBuild], parameters
ms.assetid: e782bbac-9ee6-472b-8171-3ee008c77b4e
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 2b5aba45292aaa55a719eb19d6f0f6f115e8b477
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "77632508"
---
# <a name="resourcesgenerator-task"></a>ResourcesGenerator – úloha

<xref:Microsoft.Build.Tasks.Windows.ResourcesGenerator>Úkol vloží jeden nebo více prostředků (*. jpg*, *. ico*, *. bmp*, XAML v binárním formátu a jiné typy rozšíření) do souboru *. Resources* .

## <a name="task-parameters"></a>Parametry úlohy

|Parametr|Popis|
|---------------|-----------------|
|`OutputPath`|Povinný parametr **řetězce**<br /><br /> Určuje cestu k výstupnímu adresáři. Pokud cesta není absolutní cesta, je považována za cestu, která je relativní vzhledem ke kořenovému adresáři projektu.|
|`OutputResourcesFile`|Byl požadován výstupní parametr **ITaskItem []** .<br /><br /> Určuje cestu a název vygenerovaného souboru *. Resources* . Pokud cesta není absolutní cesta, soubor *. Resources* je vygenerován relativně ke kořenovému adresáři projektu.|
|`ResourcesFiles`|Povinný parametr **ITaskItem []** .<br /><br /> Určuje jeden nebo více prostředků, které mají být vloženy do vygenerovaného souboru *. Resources* .|

## <a name="example"></a>Příklad

 Následující příklad vygeneruje soubor *. Resources* s jedním prostředkem *. bmp* . Prostředek *. bmp* je vygenerován do adresáře, který je relativní vzhledem ke kořenovému adresáři projektu.

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
  <UsingTask
    TaskName="Microsoft.Build.Tasks.Windows.ResourcesGenerator"
    AssemblyFile="C:\Program Files\Reference Assemblies\Microsoft\Framework\v3.0\PresentationBuildTasks.dll" />
  <Target Name="ResourcesGeneratorTask">
    <ResourcesGenerator
      ResourceFiles="Resource1.bmp"
      OutputPath="myresources"
      OutputResourcesFile="myresources\my.resources" />
  </Target>
</Project>
```

## <a name="see-also"></a>Viz také

- [Referenční dokumentace WPF MSBuild](../msbuild/wpf-msbuild-reference.md)
- [Referenční dokumentace úlohy](../msbuild/wpf-msbuild-task-reference.md)
- [Referenční dokumentace nástroje MSBuild](../msbuild/msbuild-reference.md)
- [Referenční dokumentace úlohy](../msbuild/msbuild-task-reference.md)
- [Sestavení aplikace WPF (WPF)](/dotnet/framework/wpf/app-development/building-a-wpf-application-wpf)