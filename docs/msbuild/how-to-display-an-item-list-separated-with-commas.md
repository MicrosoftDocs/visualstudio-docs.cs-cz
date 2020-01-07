---
title: 'Postupy: zobrazení seznamu položek oddělených čárkami | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, separating items with semicolons
- MSBuild, formatting item collections
ms.assetid: 3cae844c-7c6d-4144-82dc-efad10ba458f
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 677278d08e3223f759afc64692481311bfba3356
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/01/2020
ms.locfileid: "75596330"
---
# <a name="how-to-display-an-item-list-separated-with-commas"></a>Postupy: zobrazení seznamu položek oddělených čárkami
Když pracujete se seznamy položek v [!INCLUDE[vstecmsbuildengine](../msbuild/includes/vstecmsbuildengine_md.md)] ([!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)]), někdy je užitečné zobrazit obsah těchto seznamů položek způsobem, který se snadno přečte. Nebo je možné, že máte úkol, který přebírá seznam položek oddělený speciálním oddělovačovým řetězcem. V obou těchto případech můžete zadat oddělovačový řetězec pro seznam položek.

## <a name="separate-items-in-a-list-with-commas"></a>Samostatné položky v seznamu s čárkami
Ve výchozím nastavení [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] používá středníky k oddělení položek v seznamu. Zvažte například `Message` element s následující hodnotou:

`<Message Text="This is my list of TXT files: @(TXTFile)"/>`

Pokud seznam položek `@(TXTFile)` obsahuje položky *app1. txt*, *app2. txt*a *APP3. txt*, jedná se o následující zprávu:

`This is my list of TXT files: App1.txt;App2.txt;App3.txt`

Pokud chcete změnit výchozí chování, můžete zadat vlastní oddělovač. Syntaxe pro určení oddělovače seznamu položek je:

`@(ItemListName, '<separator>')`

Oddělovač může být buď jeden znak, nebo řetězec a musí být uzavřený v jednoduchých uvozovkách.

#### <a name="to-insert-a-comma-and-a-space-between-items"></a>Vložení čárky a mezery mezi položkami

- Použijte zápis položky podobný následujícímu:

    `@(TXTFile, ', ')`

## <a name="example"></a>Příklad
V tomto příkladu úloha [exec](../msbuild/exec-task.md) spustí nástroj Findstr, aby našli zadané textové řetězce v souboru. *txt*. V příkazu Findstr jsou řetězcové vyhledávací řetězce označeny přepínačem **-c:** , takže oddělovač položek `-c:` je vložen mezi položky v seznamu `@(Phrase)` položky.

V tomto příkladu je ekvivalentní příkaz příkazového řádku:

`findstr /i /c:hello /c:world /c:msbuild phrases.txt`

```xml
<Project DefaultTargets = "Find"
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003" >

    <ItemGroup>
        <Phrase Include="hello"/>
        <Phrase Include="world"/>
        <Phrase Include="msbuild"/>
    </ItemGroup>

    <Target Name = "Find">
        <!-- Find some strings in a file -->
        <Exec Command="findstr /i /c:@(Phrase, ' /c:') phrases.txt"/>
    </Target>
</Project>
```

## <a name="see-also"></a>Viz také:
- [Referenční dokumentace nástroje MSBuild](../msbuild/msbuild-reference.md)
- [Položky](../msbuild/msbuild-items.md)
