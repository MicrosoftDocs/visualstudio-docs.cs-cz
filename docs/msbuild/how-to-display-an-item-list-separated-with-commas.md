---
title: 'Postup: Zobrazení seznamu položek oddělených čárkami | Dokumenty společnosti Microsoft'
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
ms.openlocfilehash: 5493d3b95f7e9c0aa08ed3b06a99108e15697349
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "77633899"
---
# <a name="how-to-display-an-item-list-separated-with-commas"></a>Postup: Zobrazení seznamu položek oddělených čárkami

Při práci se seznamy položek v Microsoft Build Engine (MSBuild), je někdy užitečné zobrazit obsah těchto seznamů položek způsobem, který je snadno čitelný. Nebo můžete mít úkol, který má seznam položek oddělených speciálním oddělovacím řetězcem. V obou těchto případech můžete zadat řetězec oddělovače pro seznam položek.

## <a name="separate-items-in-a-list-with-commas"></a>Samostatné položky v seznamu čárkou

Ve výchozím nastavení používá MSBuild středníky k oddělení položek v seznamu. Zvažte například `Message` prvek s následující hodnotou:

`<Message Text="This is my list of TXT files: @(TXTFile)"/>`

Pokud `@(TXTFile)` seznam položek obsahuje položky *App1.txt*, *App2.txt*a *App3.txt*, zobrazí se zpráva:

`This is my list of TXT files: App1.txt;App2.txt;App3.txt`

Pokud chcete změnit výchozí chování, můžete zadat vlastní oddělovač. Syntaxe pro určení oddělovače seznamu položek je:

`@(ItemListName, '<separator>')`

Oddělovač může být jeden znak nebo řetězec a musí být uzavřen v jednoduchých uvozovkách.

#### <a name="to-insert-a-comma-and-a-space-between-items"></a>Vložení čárky a mezery mezi položky

- Použijte zápis položky podobný následujícímu:

    `@(TXTFile, ', ')`

## <a name="example"></a>Příklad

V tomto příkladu spustí [úloha Exec](../msbuild/exec-task.md) nástroj findstr a vyhledá zadané textové řetězce v souboru *Phrases.txt*. V příkazu findstr jsou řádky v literálu označeny přepínačem **-c:** , takže oddělovač položek `-c:` je vložen mezi položky v seznamu `@(Phrase)` položek.

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

- [Odkaz na sestavení msbuild](../msbuild/msbuild-reference.md)
- [Items](../msbuild/msbuild-items.md)
