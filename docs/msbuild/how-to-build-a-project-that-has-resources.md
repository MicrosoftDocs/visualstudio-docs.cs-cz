---
title: 'Postupy: sestavení projektu, který má prostředky | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- resource files, compiling with MSBuild
- resources [Visual Studio], compiling with MSBuild
- projects [.NET Framework], building
- MSBuild, building a project with resources
ms.assetid: d07ac73f-2c2d-4e9a-812a-6dcb632bafe2
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 626db2638912c9eaa49ea74e702c9ba24f6fd33f
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/01/2020
ms.locfileid: "75576339"
---
# <a name="how-to-build-a-project-that-has-resources"></a>Postupy: sestavení projektu, který má prostředky
Pokud vytváříte lokalizované verze projektu, všechny prvky uživatelského rozhraní musí být rozděleny do souborů prostředků pro různé jazyky. Pokud projekt používá pouze řetězce, soubory prostředků mohou používat textové soubory. Alternativně můžete jako soubory prostředků použít soubory *. resx* .

## <a name="compile-resources-with-msbuild"></a>Kompilovat prostředky pomocí nástroje MSBuild
Knihovna běžných úloh, které jsou k dispozici v [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] zahrnuje úlohu `GenerateResource`, kterou můžete použít ke kompilaci prostředků v souborech *. resx* nebo textových souborech. Tato úloha zahrnuje parametr `Sources`, který určuje, které soubory prostředků se mají zkompilovat, a parametr `OutputResources` pro určení názvů výstupních souborů prostředků. Další informace o úloze `GenerateResource` naleznete v tématu [GenerateResource – Task](../msbuild/generateresource-task.md).

#### <a name="to-compile-resources-with-msbuild"></a>Kompilace prostředků pomocí nástroje MSBuild

1. Identifikujte soubory prostředků projektu a předejte je do úlohy `GenerateResource`, buď jako seznamy položek, nebo jako názvy souborů.

2. Zadejte parametr `OutputResources` úlohy `GenerateResource`, která umožňuje nastavit názvy výstupních souborů prostředků.

3. Pomocí elementu `Output` úkolu uložte hodnotu parametru `OutputResources` v položce.

4. Použijte položku vytvořenou z prvku `Output` jako vstup do jiné úlohy.

## <a name="example"></a>Příklad
Následující příklad kódu ukazuje, jak prvek `Output` určuje, že atribut `OutputResources` `GenerateResource` úlohy bude obsahovat zkompilované soubory prostředků *Alpha. Resources* a *beta. Resources* a že tyto dva soubory budou umístěny do seznamu `Resources` položek. Určením souborů *. Resources* jako kolekce položek se stejným názvem je můžete snadno použít jako vstupy pro jinou úlohu, jako je například úloha [CSC](../msbuild/csc-task.md) .

Tato úloha je ekvivalentem použití přepínače **/Compile** pro [Resgen. exe](/dotnet/framework/tools/resgen-exe-resource-file-generator):

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
Následující příklad projektu obsahuje dvě úlohy: úkol `GenerateResource` pro zkompilování prostředků a úlohu `Csc` pro zkompilování souborů zdrojového kódu a kompilovaných zdrojů souborů. Soubory prostředků zkompilované úlohou `GenerateResource` jsou uloženy v položce `Resources` a předány do úlohy `Csc`.

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
- [MSBuild](../msbuild/msbuild.md)
- [GenerateResource – – úloha](../msbuild/generateresource-task.md)
- [CSc – úloha](../msbuild/csc-task.md)
- [Resgen.exe (generátor zdrojových souborů)](/dotnet/framework/tools/resgen-exe-resource-file-generator)
