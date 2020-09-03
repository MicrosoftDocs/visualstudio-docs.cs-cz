---
title: 'Postupy: zobrazení seznamu položek oddělených čárkami | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, separating items with semicolons
- MSBuild, formatting item collections
ms.assetid: 3cae844c-7c6d-4144-82dc-efad10ba458f
caps.latest.revision: 15
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 93451d6d49082621df48c734de951e6a4bc7e281
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "68156618"
---
# <a name="how-to-display-an-item-list-separated-with-commas"></a>Postupy: Zobrazování seznamu položek oddělených čárkami
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Když pracujete se seznamy položek v [!INCLUDE[vstecmsbuildengine](../includes/vstecmsbuildengine-md.md)] ( [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] ), někdy je užitečné zobrazit obsah těchto seznamů položek způsobem, který se snadno přečte. Nebo je možné, že máte úkol, který přebírá seznam položek oddělený speciálním oddělovačovým řetězcem. V obou těchto případech můžete zadat oddělovačový řetězec pro seznam položek.  
  
## <a name="separating-items-in-a-list-with-commas"></a>Oddělení položek v seznamu čárkami  
 Ve výchozím nastavení [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] používá středníky k oddělení položek v seznamu. Zvažte například `Message` prvek s následující hodnotou:  
  
 `<Message Text="This is my list of TXT files: @(TXTFile)"/>`  
  
 Když `@(TXTFile)` seznam položek obsahuje položky App1.txt, App2.txt a App3.txt, zpráva:  
  
 `This is my list of TXT files: App1.txt;App2.txt;App3.txt`  
  
 Pokud chcete změnit výchozí chování, můžete zadat vlastní oddělovač. Syntaxe pro určení oddělovače seznamu položek je:  
  
 `@(ItemListName, '<separator>')`  
  
 Oddělovač může být buď jeden znak, nebo řetězec a musí být uzavřený v jednoduchých uvozovkách.  
  
#### <a name="to-insert-a-comma-and-a-space-between-items"></a>Vložení čárky a mezery mezi položkami  
  
- Použijte zápis položky podobný následujícímu:  
  
     `@(TXTFile, ', ')`  
  
## <a name="example"></a>Příklad  
 V tomto příkladu úloha [exec](../msbuild/exec-task.md) spustí nástroj Findstr, aby našli zadané textové řetězce v souboru Phrases.txt. V příkazu Findstr jsou řetězcové vyhledávací řetězce označeny přepínačem **/c:** , takže `/c:` je mezi položkami v seznamu položek vložen oddělovač položek `@(Phrase)` .  
  
 V tomto příkladu je ekvivalentní příkaz příkazového řádku:  
  
 `findstr /i /c:hello /c:world /c:msbuild phrases.txt`  
  
```  
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
 [Referenční dokumentace nástroje MSBuild](../msbuild/msbuild-reference.md)   
 [Položky](../msbuild/msbuild-items.md)
