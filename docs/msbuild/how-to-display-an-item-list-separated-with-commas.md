---
title: 'Postupy: zobrazení seznamu položek oddělených čárkami | Microsoft Docs'
description: Naučte se používat nástroj MSBuild k zobrazení seznamu položek oddělených čárkami nebo k určení dalších řetězců oddělovačů pro seznam položek.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, separating items with semicolons
- MSBuild, formatting item collections
ms.assetid: 3cae844c-7c6d-4144-82dc-efad10ba458f
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 3ac0295b2d6f4300fa29c893d61616977ad44b87
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99914415"
---
# <a name="how-to-display-an-item-list-separated-with-commas"></a>Postupy: zobrazení seznamu položek oddělených čárkami

Když pracujete se seznamy položek v Microsoft Build Engine (MSBuild), někdy je užitečné zobrazit obsah těchto seznamů položek způsobem, který se snadno přečte. Nebo je možné, že máte úkol, který přebírá seznam položek oddělený speciálním oddělovačovým řetězcem. V obou těchto případech můžete zadat oddělovačový řetězec pro seznam položek.

## <a name="separate-items-in-a-list-with-commas"></a>Samostatné položky v seznamu s čárkami

Ve výchozím nastavení nástroj MSBuild používá k oddělení položek v seznamu středníky. Zvažte například `Message` prvek s následující hodnotou:

`<Message Text="This is my list of TXT files: @(TXTFile)"/>`

Když `@(TXTFile)` seznam položek obsahuje položky *App1.txt*, *App2.txt* a *App3.txt*, zpráva:

`This is my list of TXT files: App1.txt;App2.txt;App3.txt`

Pokud chcete změnit výchozí chování, můžete zadat vlastní oddělovač. Syntaxe pro určení oddělovače seznamu položek je:

`@(ItemListName, '<separator>')`

Oddělovač může být buď jeden znak, nebo řetězec a musí být uzavřený v jednoduchých uvozovkách.

#### <a name="to-insert-a-comma-and-a-space-between-items"></a>Vložení čárky a mezery mezi položkami

- Použijte zápis položky podobný následujícímu:

    `@(TXTFile, ', ')`

## <a name="example"></a>Příklad

V tomto příkladu úloha [exec](../msbuild/exec-task.md) spustí nástroj Findstr, aby našli zadané textové řetězce v souboru *Phrases.txt*. V příkazu Findstr jsou řetězcové vyhledávací řetězce označeny přepínačem **-c:** , takže `-c:` je mezi položkami v seznamu položek vložen oddělovač položek `@(Phrase)` .

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

## <a name="see-also"></a>Viz také

- [Referenční dokumentace nástroje MSBuild](../msbuild/msbuild-reference.md)
- [Položky](../msbuild/msbuild-items.md)
