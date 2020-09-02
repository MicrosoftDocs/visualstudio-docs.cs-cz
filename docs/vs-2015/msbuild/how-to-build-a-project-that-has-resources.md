---
title: 'Postupy: sestavení projektu, který má prostředky | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: conceptual
helpviewer_keywords:
- resource files, compiling with MSBuild
- resources [Visual Studio], compiling with MSBuild
- projects [.NET Framework], building
- MSBuild, building a project with resources
ms.assetid: d07ac73f-2c2d-4e9a-812a-6dcb632bafe2
caps.latest.revision: 17
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: fb77db891e824f5f2900ef191049e65cb2c89a98
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "65686520"
---
# <a name="how-to-build-a-project-that-has-resources"></a>Postupy: Sestavení projektu, který má prostředky
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Pokud vytváříte lokalizované verze projektu, všechny prvky uživatelského rozhraní musí být rozděleny do souborů prostředků pro různé jazyky. Pokud projekt používá pouze řetězce, soubory prostředků mohou používat textové soubory. Alternativně můžete jako soubory prostředků použít soubory. resx.  
  
## <a name="compiling-resources-with-msbuild"></a>Kompilace prostředků pomocí nástroje MSBuild  
 Knihovna běžných úloh, které jsou k dispozici, [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] zahrnuje `GenerateResource` úlohu, kterou můžete použít ke kompilaci prostředků v souborech. resx nebo textových souborech. Tato úloha zahrnuje `Sources` parametr k určení, které soubory prostředků mají být zkompilovány, a `OutputResources` parametr k určení názvů pro výstupní soubory prostředků. Další informace o `GenerateResource` úloze najdete v tématu [GenerateResource – Task](../msbuild/generateresource-task.md).  
  
#### <a name="to-compile-resources-with-msbuild"></a>Kompilace prostředků pomocí nástroje MSBuild  
  
1. Identifikujte soubory prostředků projektu a předejte je `GenerateResource` úkolu, buď jako seznamy položek, nebo jako názvy souborů.  
  
2. Zadejte `OutputResources` parametr `GenerateResource` úlohy, který umožňuje nastavit názvy pro výstupní soubory prostředků.  
  
3. Pomocí `Output` elementu úkolu uložte hodnotu `OutputResources` parametru do položky.  
  
4. Použijte položku vytvořenou z `Output` prvku jako vstup do jiné úlohy.  
  
## <a name="example"></a>Příklad  
 Následující příklad kódu ukazuje `Output` , jak prvek určuje, že `OutputResources` atribut `GenerateResource` úlohy bude obsahovat zkompilované soubory prostředků `alpha.resources` a `beta.resources` a že tyto dva soubory budou umístěny v `Resources` seznamu položek. Určením souborů. Resources jako kolekce položek se stejným názvem je můžete snadno použít jako vstupy pro jinou úlohu, jako je například úloha [CSC](../msbuild/csc-task.md) .  
  
 Tato úloha je ekvivalentem použití přepínače **/Compile** pro [Resgen.exe](https://msdn.microsoft.com/library/8ef159de-b660-4bec-9213-c3fbc4d1c6f4):  
  
 `Resgen.exe /compile alpha.resx,alpha.resources /compile beta.txt,beta.resources`  
  
```  
<GenerateResource  
    Sources="alpha.resx; beta.txt"  
    OutputResources="alpha.resources; beta.resources">  
    <Output TaskParameter="OutputResources"  
        ItemName="Resources"/>  
</GenerateResource>  
```  
  
## <a name="example"></a>Příklad  
 Následující příklad projektu obsahuje dvě úlohy: `GenerateResource` úkol pro zkompilování prostředků a `Csc` úlohu pro zkompilování souborů zdrojového kódu a kompilovaných souborů prostředků. Soubory prostředků zkompilované `GenerateResource` úlohou jsou uloženy v `Resources` položce a předány do `Csc` úlohy.  
  
```  
<Project DefaultTargets = "Build"  
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003" >  
  
    <Target Name="Resources">  
        <GenerateResource  
            Sources="alpha.resx; beta.txt"  
            OutputResources="alpha.resources; beta.resources">  
            <Output TaskParameter="OutputResources"  
                ItemName="Resources"/>  
        </GenerateResource>  
    </Target>  
  
    <Target Name="Build" DependsOnTargets="Resources">  
        <Csc Sources="hello.cs"  
                Resources="@(Resources)"  
                OutputAssembly="hello.exe"/>  
    </Target>  
</Project>  
```  
  
## <a name="see-also"></a>Viz také  
[Nástroji](msbuild.md)  
 [GenerateResource – – úloha](../msbuild/generateresource-task.md)   
 [CSc – úloha](../msbuild/csc-task.md)   
 [Resgen.exe (generátor zdrojového souboru)](https://msdn.microsoft.com/library/8ef159de-b660-4bec-9213-c3fbc4d1c6f4)
