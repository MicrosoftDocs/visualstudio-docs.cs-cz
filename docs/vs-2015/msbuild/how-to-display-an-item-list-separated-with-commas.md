---
title: 'Postupy: zobrazování seznamu položek oddělených čárkami | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- MSBuild, separating items with semicolons
- MSBuild, formatting item collections
ms.assetid: 3cae844c-7c6d-4144-82dc-efad10ba458f
caps.latest.revision: 15
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c9de7655335d2937a31cc2d63f5220fbf5415745
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/12/2018
ms.locfileid: "49195868"
---
# <a name="how-to-display-an-item-list-separated-with-commas"></a>Postupy: Zobrazování seznamu položek oddělených čárkami
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Při práci s položkou seznamů v [!INCLUDE[vstecmsbuildengine](../includes/vstecmsbuildengine-md.md)] ([!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)]), je někdy užitečné zobrazit obsah těchto položek seznamů tak, aby se snadno čitelný. Nebo můžete mít úlohu, která přebírá seznam položek oddělené speciální oddělovacího řetězce. V obou těchto případech můžete zadat řetězec oddělovače pro seznam položek.  
  
## <a name="separating-items-in-a-list-with-commas"></a>Položky v seznamu oddělíte čárkami  
 Ve výchozím nastavení [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] středníky používá k oddělení položek v seznamu. Představte si třeba `Message` element s následující hodnotu:  
  
 `<Message Text="This is my list of TXT files: @(TXTFile)"/>`  
  
 Když `@(TXTFile)` seznamu položek obsahuje položky App1.txt App2.txt a App3.txt, zpráva:  
  
 `This is my list of TXT files: App1.txt;App2.txt;App3.txt`  
  
 Pokud chcete změnit výchozí chování, můžete zadat vlastní oddělovač. Syntaxe pro určení oddělovačem seznamu položky je:  
  
 `@(ItemListName, '<separator>')`  
  
 Oddělovač může být jeden znak nebo řetězec a musí být uzavřen v jednoduchých uvozovkách.  
  
#### <a name="to-insert-a-comma-and-a-space-between-items"></a>Chcete-li vložit čárku a mezeru mezi položkami  
  
-   Použijte zápis položky podobný následujícímu:  
  
     `@(TXTFile, ', ')`  
  
## <a name="example"></a>Příklad  
 V tomto příkladu [Exec](../msbuild/exec-task.md) nástroj findstr najít zadané textové řetězce v souboru Phrases.txt spuštění úlohy. V příkazu findstr jsou označeny literál řetězce **sady** přepnout, tak oddělovač položek `/c:` je vložen mezi položkami v `@(Phrase)` seznam položek.  
  
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



