---
title: 'Postupy: odkazování na název nebo umístění souboru projektu | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
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
caps.latest.revision: 16
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: eae8a32d4587b71f238c023d08a1328ce83ba37d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "64818200"
---
# <a name="how-to-reference-the-name-or-location-of-the-project-file"></a>Postupy: Odkazování na název nebo umístění souboru projektu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Můžete použít název nebo umístění projektu v samotném souboru projektu, aniž by bylo nutné vytvořit vlastní vlastnost. [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] poskytuje vyhrazené vlastnosti, které odkazují na název souboru projektu a další vlastnosti, které se vztahují k projektu. Další informace o vyhrazených vlastnostech naleznete v tématu [vyhrazené a dobře známé vlastnosti nástroje MSBuild](../msbuild/msbuild-reserved-and-well-known-properties.md).  
  
## <a name="using-the-msbuildprojectname-property"></a>Použití vlastnosti MSBuildProjectName  
 [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] poskytuje některé vyhrazené vlastnosti, které můžete použít v souborech projektu, aniž byste je museli definovat pokaždé. Například vyhrazená vlastnost `MSBuildProjectName` poskytuje odkaz na název souboru projektu.  
  
#### <a name="to-use-the-msbuildprojectname-property"></a>Použití vlastnosti MSBuildProjectName  
  
- Odkazujte na vlastnost v souboru projektu pomocí notace $ (), stejně jako u libovolné vlastnosti. Příklad:  
  
  ```  
  <CSC Sources = "@(CSFile)"   
      OutputAssembly = "$(MSBuildProjectName).exe"/>  
  </CSC>  
  ```  
  
  Výhodou použití rezervované vlastnosti je, že všechny změny názvu souboru projektu jsou začleněny automaticky. Při příštím sestavení projektu bude mít výstupní soubor nový název, který nevyžaduje žádnou další akci.  
  
> [!NOTE]
> Rezervované vlastnosti nelze předefinovat v souboru projektu.  
  
## <a name="example"></a>Příklad  
 Následující příklad souboru projektu odkazuje na název projektu jako vyhrazená vlastnost k určení názvu výstupu.  
  
```  
<Project xmlns="http://scheams.microsoft.com/developer/msbuild/2003"   
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
  
## <a name="see-also"></a>Viz také  
[Nástroji](msbuild.md)  
 [Rezervované a dobře známé vlastnosti nástroje MSBuild](../msbuild/msbuild-reserved-and-well-known-properties.md)
