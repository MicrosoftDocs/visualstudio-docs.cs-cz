---
title: 'Postupy: sestavení projektu, který má prostředky | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: msbuild
ms.topic: conceptual
helpviewer_keywords:
- resource files, compiling with MSBuild
- resources [Visual Studio], compiling with MSBuild
- projects [.NET Framework], building
- MSBuild, building a project with resources
ms.assetid: d07ac73f-2c2d-4e9a-812a-6dcb632bafe2
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: e7724969a4677bc0d8480b794ae72b2dbee74a86
ms.sourcegitcommit: 5b767247b3d819a99deb0dbce729a0562b9654ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/20/2018
ms.locfileid: "39180344"
---
# <a name="how-to-build-a-project-that-has-resources"></a>Postupy: sestavení projektu, který má prostředky
Pokud vytváříte lokalizované verze projektu, musí se oddělit všechny prvky uživatelského rozhraní do souborů prostředků pro různé jazyky. Pokud projekt používá pouze řetězce, soubory prostředků pomocí textových souborů. Alternativně můžete použít *RESX* soubory jako soubory prostředků.  
  
## <a name="compile-resources-with-msbuild"></a>Kompilace prostředků pomocí nástroje MSBuild  
 Knihovny běžných úloh, které je součástí [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] zahrnuje `GenerateResource` úkol, který můžete použít ke kompilaci prostředků buď *RESX* nebo textové soubory. Tato úloha obsahuje `Sources` parametr k určení, který prostředek se soubory ke kompilaci a `OutputResources` parametr nazvat výstupní soubory prostředků. Další informace o `GenerateResource` úloh naleznete v tématu [generateresource – úloha](../msbuild/generateresource-task.md).  
  
#### <a name="to-compile-resources-with-msbuild"></a>Chcete-li zkompilovat prostředků pomocí nástroje MSBuild  
  
1.  Určit soubory prostředků v projektu a předat je do `GenerateResource` úkolů, buď jako seznam položek, nebo jako názvy souborů.  
  
2.  Zadejte `OutputResources` parametr `GenerateResource` úkol, který vám umožní nastavit názvy pro výstupní soubory prostředků.  
  
3.  Použití `Output` element úkolu k uložení hodnoty `OutputResources` parametr v položce.  
  
4.  Pomocí položky vytvořené z `Output` element jako vstup do jiného úkolu.  
  
## <a name="example"></a>Příklad  
 Následující příklad kódu ukazuje jak `Output` element určuje, že `OutputResources` atribut `GenerateResource` úkol bude obsahovat soubory kompilované prostředků *alpha.resources* a  *Beta.Resources* a že se tyto dva soubory umístit do `Resources` seznam položek. Identifikujte ty *.resources* soubory jako kolekce položek se stejným názvem, můžete snadno použít jako vstupy pro jiný úkol, například [Csc](../msbuild/csc-task.md) úloh.  
  
 Tato úloha je ekvivalentní k použití **/compile** přepnout [Resgen.exe](/dotnet/framework/tools/resgen-exe-resource-file-generator):  
  
 `Resgen.exe /compile alpha.resx,alpha.resources /compile beta.txt,beta.resources`  
  
```xml  
<GenerateResource  
    Sources="alpha.resx; beta.txt"  
    OutputResources="alpha.resources; beta.resources">  
    <Output TaskParameter="OutputResources"  
        ItemName="Resources"/>  
</GenerateResource>  
```  
  
## <a name="example"></a>Příklad  
 Následujícím příkladu projektu obsahuje dvě úlohy: `GenerateResource` úloha kompilace prostředků a `Csc` úkolů ke kompilaci souborů zdrojového kódu a soubory kompilované prostředků. Kompilovaná soubory prostředků `GenerateResource` úlohy jsou uloženy v `Resources` položky a předat `Csc` úloh.  
  
```xml  
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
  
## <a name="see-also"></a>Viz také:  
[MSBuild](../msbuild/msbuild.md)  
 [Generateresource – úloha](../msbuild/generateresource-task.md)   
 [CSC – úloha](../msbuild/csc-task.md)   
 [Resgen.exe (generátor zdrojových souborů)](/dotnet/framework/tools/resgen-exe-resource-file-generator)