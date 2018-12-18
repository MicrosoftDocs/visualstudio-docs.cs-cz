---
title: Operátory rozšířeného vyhledávání ve vyhledávacích výrazech | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Help Viewer 2.0, searching for keywords
- Help Viewer 2.0, searching code
- Help Viewer 2.0, searching code by programming language
- Help Viewer 2.0, searching titles
- searching code [Help Viewer 2.0]
- searching titles [Help Viewer 2.0]
ms.assetid: 0cdc1746-8481-45ec-9c53-d0d89cdcbd5e
caps.latest.revision: 11
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 706d6d89d46a1e5db4f94c2e7d5e35ace73e1bac
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/12/2018
ms.locfileid: "49177983"
---
# <a name="advanced-search-operators-in-search-expressions"></a>Operátory rozšířeného vyhledávání ve vyhledávacích výrazech
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Pomocí operátory rozšířeného vyhledávání můžete upřesnit vyhledávání pro obsah tak, že vytvoříte složitější hledaných výrazů od těch jednodušší. Jak ukazuje následující tabulka tyto operátory omezení kontext, ve kterém se spouští dotaz.  
  
> [!WARNING]
>  Je nutné zadat operátory rozšířeného vyhledávání konečné dvojtečku žádné použité mezeru před dvojtečku pro vyhledávací web rozpoznány.  
  
|K vyhledání|Použití|Příklad|Výsledek|  
|-------------------|---------|-------------|------------|  
|Výraz v název tématu|Název:|Title: binaryreader|Témata, které obsahují "binaryreader" v názvech.|  
|Termín v příkladu kódu|Kód:|kód: readdouble|Témata, které obsahují "readdouble" v příkladu kódu.|  
|Výraz v příklad konkrétní programovací jazyk|vb: kód:|kód: vb:string|Témata, které obsahují "string" v příkladu jazyka Visual Basic.|  
|Téma, které souvisí s klíčovým slovem konkrétního indexu|klíčové slovo:|klíčové slovo: readbyte|Témata, které jsou spojeny s klíčovým slovem "readbyte" index.|  
  
 Můžete použít kód: operátor hledání obsahu o všech různých programovacích jazyků, ale vrátí výsledky pouze pro obsah, který je označen s konkrétní programovací jazyk. V následující tabulce jsou uvedeny programovacích jazyků, které podporuje tento operátor:  
  
|Programovací jazyk|Použití|  
|--------------------------|---------|  
|Visual Basic|kód jazyka Visual Basic:<br /><br /> or<br /><br /> kód: visualbasic|  
|C#|kód: c#<br /><br /> or<br /><br /> kód: csharp|  
|C++|kód: cpp<br /><br /> or<br /><br /> kód: c ++<br /><br /> or<br /><br /> kód: cplusplus|  
|F#|kód: f #<br /><br /> or<br /><br /> kód: fsharp|  
|JavaScript|kód: jazyka javascript<br /><br /> or<br /><br /> kód: js|  
|XAML|kód: xaml|  
  
## <a name="see-also"></a>Viz také  
 [Logické operátory ve vyhledávacích výrazech](../ide/logical-operators-in-search-expressions.md)   
 [Tipy pro fulltextové vyhledávání](../ide/full-text-search-tips.md)



