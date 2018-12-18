---
title: 'Postupy: odkazování na název nebo umístění souboru projektu | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: msbuild
ms.topic: conceptual
helpviewer_keywords:
- locations, referencing
- locations
- MSBuildProjectName property
- MSBuild, referencing the project file
- names, referencing
- reserved properties
- project files, referencing
ms.assetid: c8fcc594-5d37-4e2e-b070-4d9c012043b5
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: dceca1e518783f405490d3f2527156bd20bf81aa
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49911522"
---
# <a name="how-to-reference-the-name-or-location-of-the-project-file"></a>Postupy: odkazování na název nebo umístění souboru projektu
Název nebo umístění projektu můžete použít v souboru projektu bez nutnosti vytvářet vlastní vlastnosti. [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] poskytuje rezervované vlastnosti, které odkazují na název souboru projektu a další vlastnosti související s projektem. Další informace o rezervované vlastnosti najdete v tématu [MSBuild vyhrazené a dobře známé vlastnosti](../msbuild/msbuild-reserved-and-well-known-properties.md).  
  
## <a name="use-the-project-properties"></a>Použít vlastnosti projektu
 [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] poskytuje některé rezervované vlastnosti, které můžete použít bez jejich definováním pokaždé, když v souborech projektu. Například vlastnost vyhrazené `MSBuildProjectName` poskytuje odkaz na název souboru projektu. Rezervované vlastnosti `MSBuildProjectDirectory` poskytuje odkaz na umístění souboru projektu.
  
#### <a name="to-use-the-project-properties"></a>Chcete-li použít vlastnosti projektu
  
- Odkazovat na vlastnost v souboru projektu se zápis $ (), stejně jako s jakoukoli vlastnost. Příklad:  
  
  ```xml  
  <CSC Sources = "@(CSFile)"   
      OutputAssembly = "$(MSBuildProjectName).exe"/>  
  </CSC>  
  ```          
  
  Výhodou použití rezervované vlastnosti je, že jsou automaticky součástí žádné změny k názvu souboru projektu. Při příštím sestavení projektu, výstupní soubor bude mít nový název se vyžadovat z vaší strany žádná další akce.  
  
> [!NOTE]
>  Rezervované vlastnosti nelze předefinovat v souboru projektu.  
  
## <a name="example"></a>Příklad  
 Následující příklad souboru projektu odkazuje na název projektu jako vyhrazené vlastnosti a určit název pro výstup.  
  
```xml  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003"   
    DefaultTargets = "Compile">  
  
    <!-- Specify the inputs -->  
    <ItemGroup>  
        <CSFile Include = "consolehwcs1.cs"/>  
     </ItemGroup>  
    <Target Name = "Compile">  
        <!-- Run the Visual C# compilation using  
        input files of type CSFile -->  
        <CSC Sources = "@(CSFile)"  
            OutputAssembly = "$(MSBuildProjectName).exe" >  
            <!-- Set the OutputAssembly attribute of the CSC task  
            to the name of the project -->  
            <Output  
                TaskParameter = "OutputAssembly"  
                ItemName = "EXEFile" />  
        </CSC>  
        <!-- Log the file name of the output file -->  
        <Message Text="The output file is @(EXEFile)"/>  
    </Target>  
</Project>  
```  

## <a name="example"></a>Příklad
 Následující ukázkový soubor projektu používá `MSBuildProjectDirectory` rezervované vlastnosti vytvořit úplná cesta k souboru v umístění souboru projektu.  
  
```xml  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">     
    
    <!-- Build the path to a file in the root of the project -->  
    <PropertyGroup>  
        <NewFilePath>$([System.IO.Path]::Combine($(MSBuildProjectDirectory), `BuildInfo.txt`))</NewFilePath>
    </PropertyGroup>  
</Project>  
```  
  
## <a name="see-also"></a>Viz také:  
[MSBuild](../msbuild/msbuild.md)  
[Nástroj MSBuild vyhrazené a dobře známé vlastnosti](../msbuild/msbuild-reserved-and-well-known-properties.md)
