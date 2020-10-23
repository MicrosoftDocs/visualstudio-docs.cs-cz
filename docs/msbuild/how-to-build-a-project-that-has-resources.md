---
title: 'Postupy: sestavení projektu, který má prostředky | Microsoft Docs'
description: Přečtěte si, jak vytvořit projekt, který obsahuje prostředky a jak kompilovat prostředky pomocí nástroje MSBuild.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: e6a71a34b4ce208b093f7982ba3516b0229c8644
ms.sourcegitcommit: c4927ef8fe239005d7feff6c5a7707c594a7a05c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/22/2020
ms.locfileid: "92436679"
---
# <a name="how-to-build-a-project-that-has-resources"></a>Postupy: sestavení projektu, který má prostředky

Pokud vytváříte lokalizované verze projektu, všechny prvky uživatelského rozhraní musí být rozděleny do souborů prostředků pro různé jazyky. Pokud projekt používá pouze řetězce, soubory prostředků mohou používat textové soubory. Alternativně můžete jako soubory prostředků použít soubory *. resx* .

## <a name="compile-resources-with-msbuild"></a>Kompilovat prostředky pomocí nástroje MSBuild

Knihovna běžných úloh, které jsou součástí nástroje MSBuild, zahrnuje `GenerateResource` úlohu, kterou lze použít ke kompilaci prostředků v souborech *. resx* nebo textových souborech. Tato úloha zahrnuje `Sources` parametr k určení, které soubory prostředků mají být zkompilovány, a `OutputResources` parametr k určení názvů pro výstupní soubory prostředků. Další informace o `GenerateResource` úloze najdete v tématu [GenerateResource – Task](../msbuild/generateresource-task.md).

#### <a name="to-compile-resources-with-msbuild"></a>Kompilace prostředků pomocí nástroje MSBuild

1. Identifikujte soubory prostředků projektu a předejte je `GenerateResource` úkolu, buď jako seznamy položek, nebo jako názvy souborů.

2. Zadejte `OutputResources` parametr `GenerateResource` úlohy, který umožňuje nastavit názvy pro výstupní soubory prostředků.

3. Pomocí `Output` elementu úkolu uložte hodnotu `OutputResources` parametru do položky.

4. Použijte položku vytvořenou z `Output` prvku jako vstup do jiné úlohy.

## <a name="example-1"></a>Příklad 1

Následující příklad kódu ukazuje `Output` , jak prvek určuje, že `OutputResources` atribut `GenerateResource` úlohy bude obsahovat zkompilované soubory prostředků *Alpha. Resources* a *beta. Resources* a že tyto dva soubory budou umístěny v `Resources` seznamu položek. Určením souborů *. Resources* jako kolekce položek se stejným názvem je můžete snadno použít jako vstupy pro jinou úlohu, jako je například úloha [CSC](../msbuild/csc-task.md) .

Tato úloha je ekvivalentem použití přepínače **/Compile** pro [Resgen.exe](/dotnet/framework/tools/resgen-exe-resource-file-generator):

`Resgen.exe /compile alpha.resx,alpha.resources /compile beta.txt,beta.resources`

```xml
<GenerateResource
    Sources="alpha.resx; beta.txt"
    OutputResources="alpha.resources; beta.resources">
    <Output TaskParameter="OutputResources"
        ItemName="Resources"/>
</GenerateResource>
```

## <a name="example-2"></a>Příklad 2

Následující příklad projektu obsahuje dvě úlohy: `GenerateResource` úkol pro zkompilování prostředků a `Csc` úlohu pro zkompilování souborů zdrojového kódu a kompilovaných souborů prostředků. Soubory prostředků zkompilované `GenerateResource` úlohou jsou uloženy v `Resources` položce a předány do `Csc` úlohy.

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

## <a name="see-also"></a>Viz také

- [MSBuild](../msbuild/msbuild.md)
- [GenerateResource – úloha](../msbuild/generateresource-task.md)
- [Csc – úloha](../msbuild/csc-task.md)
- [Resgen.exe (generátor zdrojového souboru)](/dotnet/framework/tools/resgen-exe-resource-file-generator)
