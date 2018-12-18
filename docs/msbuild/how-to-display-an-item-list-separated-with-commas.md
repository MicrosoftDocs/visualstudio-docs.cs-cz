---
title: 'Postupy: zobrazování seznamu položek oddělených čárkami | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: msbuild
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, separating items with semicolons
- MSBuild, formatting item collections
ms.assetid: 3cae844c-7c6d-4144-82dc-efad10ba458f
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: f1507a297c1baf7f410bde1c6d32e48b43a9cdc2
ms.sourcegitcommit: 71218ffc33da325cc1b886f69ff2ca50d44f5f33
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/09/2018
ms.locfileid: "48880225"
---
# <a name="how-to-display-an-item-list-separated-with-commas"></a>Postupy: zobrazování seznamu položek oddělených čárkami
Při práci s položkou seznamů v [!INCLUDE[vstecmsbuildengine](../msbuild/includes/vstecmsbuildengine_md.md)] ([!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)]), je někdy užitečné zobrazit obsah těchto položek seznamů tak, aby se snadno čitelný. Nebo můžete mít úlohu, která přebírá seznam položek oddělené speciální oddělovacího řetězce. V obou těchto případech můžete zadat řetězec oddělovače pro seznam položek.  
  
## <a name="separate-items-in-a-list-with-commas"></a>Samostatné položky v seznamu čárkami  
 Ve výchozím nastavení [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] středníky používá k oddělení položek v seznamu. Představte si třeba `Message` element s následující hodnotu:  
  
 `<Message Text="This is my list of TXT files: @(TXTFile)"/>`  
  
 Když `@(TXTFile)` seznamu položek obsahuje položky *App1.txt*, *App2.txt*, a *App3.txt*, zpráva:  
  
 `This is my list of TXT files: App1.txt;App2.txt;App3.txt`  
  
 Pokud chcete změnit výchozí chování, můžete zadat vlastní oddělovač. Syntaxe pro určení oddělovačem seznamu položky je:  
  
 `@(ItemListName, '<separator>')`  
  
 Oddělovač může být jeden znak nebo řetězec a musí být uzavřen v jednoduchých uvozovkách.  
  
#### <a name="to-insert-a-comma-and-a-space-between-items"></a>Chcete-li vložit čárku a mezeru mezi položkami  
  
-   Použijte zápis položky podobný následujícímu:  
  
     `@(TXTFile, ', ')`  
  
## <a name="example"></a>Příklad  
 V tomto příkladu [Exec](../msbuild/exec-task.md) úkolů spustí nástroj findstr najít zadané textové řetězce v souboru *Phrases.txt*. V příkazu findstr jsou označeny literál řetězce **-c:** přepnout, tak oddělovač položek `-c:` je vložen mezi položkami v `@(Phrase)` seznam položek.  
  
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
 [Referenční dokumentace nástroje MSBuild](../msbuild/msbuild-reference.md)   
 [Položky](../msbuild/msbuild-items.md)