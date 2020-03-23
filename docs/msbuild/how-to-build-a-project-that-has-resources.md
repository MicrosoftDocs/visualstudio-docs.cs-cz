---
title: 'Postup: Vytvoření projektu, který má zdroje | Dokumenty společnosti Microsoft'
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
ms.openlocfilehash: a76246096eec8779ce331e93f01be5ab791d1cdb
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "77633951"
---
# <a name="how-to-build-a-project-that-has-resources"></a>Postup: Vytvoření projektu, který má zdroje

Pokud vytváříte lokalizované verze projektu, musí být všechny prvky uživatelského rozhraní rozděleny do souborů prostředků pro různé jazyky. Pokud projekt používá pouze řetězce, soubory prostředků můžete použít textové soubory. Případně můžete jako soubory prostředků použít soubory *RESX.*

## <a name="compile-resources-with-msbuild"></a>Kompilace prostředků pomocí msbuildu

Knihovna běžných úkolů, která je součástí `GenerateResource` msbuild obsahuje úkol, který můžete použít ke kompilaci prostředků *v .resx* nebo textové soubory. Tato úloha `Sources` zahrnuje parametr pro určení, `OutputResources` které soubory prostředků mají být kompilovány, a parametr pro určení názvů výstupních souborů prostředků. Další informace o `GenerateResource` úkolu naleznete v tématu [GenerateResource task](../msbuild/generateresource-task.md).

#### <a name="to-compile-resources-with-msbuild"></a>Kompilace prostředků pomocí msbuildu

1. Identifikujte soubory prostředků projektu `GenerateResource` a předejte je úkolu, buď jako seznamy položek, nebo jako názvy souborů.

2. Zadejte `OutputResources` parametr `GenerateResource` úlohy, který umožňuje nastavit názvy výstupních souborů prostředků.

3. `Output` Prvek úlohy slouží k uložení hodnoty `OutputResources` parametru v položce.

4. Použijte položku vytvořenou `Output` z prvku jako vstup do jiné úlohy.

## <a name="example"></a>Příklad

Následující příklad kódu ukazuje, `Output` jak prvek `OutputResources` určuje, `GenerateResource` že atribut úkolu bude obsahovat zkompilované soubory prostředků *alpha.resources* `Resources` a *beta.resources* a že tyto dva soubory budou umístěny uvnitř seznamu položek. Tím, že tyto soubory *.resources* identifikujete jako kolekci položek se stejným názvem, můžete je snadno použít jako vstupy pro jiný úkol, například úkol [Csc.](../msbuild/csc-task.md)

Tato úloha je ekvivalentní použití **přepínače /compile** pro [resgen.exe](/dotnet/framework/tools/resgen-exe-resource-file-generator):

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

Následující ukázkový projekt obsahuje `GenerateResource` dva úkoly: `Csc` úkol pro kompilaci zdrojů a úkol pro kompilaci souborů zdrojového kódu i souborů zkompilovaných prostředků. Soubory prostředků zkompilované úlohou `GenerateResource` `Resources` jsou uloženy `Csc` v položce a předány úloze.

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

- [Msbuild](../msbuild/msbuild.md)
- [Úloha Generovat zdroj](../msbuild/generateresource-task.md)
- [Úkol CsC](../msbuild/csc-task.md)
- [Resgen.exe (generátor zdrojových souborů)](/dotnet/framework/tools/resgen-exe-resource-file-generator)
