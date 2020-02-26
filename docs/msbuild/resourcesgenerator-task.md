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
ms.openlocfilehash: 703cd7bc3d0dd0e2229365dde39418ff32ad0a3e
ms.sourcegitcommit: 2ae2436dc3484b9dfa10e0483afba1e5a02a52eb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/25/2020
ms.locfileid: "77579600"
---
# <a name="resourcesgenerator-task"></a>ResourcesGenerator – – úloha
Úloha <xref:Microsoft.Build.Tasks.Windows.ResourcesGenerator> vloží jeden nebo více prostředků ( *. jpg*, *. ico*, *. bmp*, [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] v binárním formátu a jiné typy rozšíření) do souboru *. Resources* .

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
- [Odkaz na úkol](../msbuild/wpf-msbuild-task-reference.md)
- [Referenční dokumentace nástroje MSBuild](../msbuild/msbuild-reference.md)
- [Odkaz na úkol](../msbuild/msbuild-task-reference.md)
- [Sestavení aplikace WPF (WPF)](/dotnet/framework/wpf/app-development/building-a-wpf-application-wpf)