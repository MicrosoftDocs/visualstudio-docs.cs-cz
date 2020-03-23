---
title: ResourcesGenerator Úkol | Dokumenty společnosti Microsoft
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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "77632508"
---
# <a name="resourcesgenerator-task"></a>Úkol ResourcesGenerator

Úloha <xref:Microsoft.Build.Tasks.Windows.ResourcesGenerator> vloží jeden nebo více prostředků (*.jpg*, *.ico*, *.bmp*, XAML v binárním formátu a další typy rozšíření) do souboru *.resources.*

## <a name="task-parameters"></a>Parametry úlohy

|Parametr|Popis|
|---------------|-----------------|
|`OutputPath`|Povinný **parametr String.**<br /><br /> Určuje cestu k výstupnímu adresáři. Pokud cesta není absolutní cesta, je považována za cestu, která je relativní k adresáři kořenového projektu.|
|`OutputResourcesFile`|Povinný výstupní parametr **ITaskItem[].**<br /><br /> Určuje cestu a název generovaného souboru *.resources.* Pokud cesta není absolutní cesta, soubor *.resources* je generován vzhledem ke kořenovému adresáři projektu.|
|`ResourcesFiles`|Povinný parametr **ITaskItem[].**<br /><br /> Určuje jeden nebo více prostředků, které mají být vygenerovány do generovaného souboru *.resources.*|

## <a name="example"></a>Příklad

 Následující příklad generuje soubor *.resources* s jedním zdrojem *BMP.* Zdroj *BMP* je generován do adresáře, který je relativní vzhledem k kořenovému adresáři projektu.

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

- [WPF MSBuild odkaz](../msbuild/wpf-msbuild-reference.md)
- [Odkaz na úkol](../msbuild/wpf-msbuild-task-reference.md)
- [Odkaz na sestavení msbuild](../msbuild/msbuild-reference.md)
- [Odkaz na úkol](../msbuild/msbuild-task-reference.md)
- [Vytvoření aplikace WPF (WPF)](/dotnet/framework/wpf/app-development/building-a-wpf-application-wpf)