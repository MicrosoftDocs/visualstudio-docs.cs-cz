---
title: Úloha ResourcesGenerator – | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
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
caps.latest.revision: 9
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: fa8b438727160bb5a752643f7ef9791ca5e09245
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "65682140"
---
# <a name="resourcesgenerator-task"></a>ResourcesGenerator – úloha
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

<xref:Microsoft.Build.Tasks.Windows.ResourcesGenerator>Úkol vloží jeden nebo více prostředků (. jpg,. ico,. bmp, [!INCLUDE[TLA2#tla_xaml](../includes/tla2sharptla-xaml-md.md)] v binárním formátu a dalších typech rozšíření) do souboru. Resources.  
  
## <a name="task-parameters"></a>Parametry úlohy  
  
|Parametr|Popis|  
|---------------|-----------------|  
|`OutputPath`|Povinný parametr **řetězce**<br /><br /> Určuje cestu k výstupnímu adresáři. Pokud cesta není absolutní cesta, je považována za cestu, která je relativní vzhledem ke kořenovému adresáři projektu.|  
|`OutputResourcesFile`|Byl požadován výstupní parametr **ITaskItem []** .<br /><br /> Určuje cestu a název vygenerovaného souboru. Resources. Pokud cesta není absolutní cesta, soubor. Resources je vygenerován relativně ke kořenovému adresáři projektu.|  
|`ResourcesFiles`|Povinný parametr **ITaskItem []** .<br /><br /> Určuje jeden nebo více prostředků, které mají být vloženy do vygenerovaného souboru. Resources.|  
  
## <a name="example"></a>Příklad  
 Následující příklad vygeneruje soubor. Resources s jedním prostředkem. bmp. Prostředek. BMP je vygenerován do adresáře, který je relativní vzhledem ke kořenovému adresáři projektu.  
  
```  
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
 [Referenční dokumentace WPF MSBuild](../msbuild/wpf-msbuild-reference.md)   
 [Odkaz na úkol](../msbuild/wpf-msbuild-task-reference.md)   
 [Referenční dokumentace nástroje MSBuild](../msbuild/msbuild-reference.md)   
 [Odkaz na úkol](../msbuild/msbuild-task-reference.md)   
 [Sestavení aplikace WPF (WPF)](https://msdn.microsoft.com/library/a58696fd-bdad-4b55-9759-136dfdf8b91c)
