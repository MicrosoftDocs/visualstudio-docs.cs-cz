---
title: Rozšířené operátory hledání ve výrazech hledání | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- Help Viewer 2.0, searching for keywords
- Help Viewer 2.0, searching code
- Help Viewer 2.0, searching code by programming language
- Help Viewer 2.0, searching titles
- searching code [Help Viewer 2.0]
- searching titles [Help Viewer 2.0]
ms.assetid: 0cdc1746-8481-45ec-9c53-d0d89cdcbd5e
caps.latest.revision: 11
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: c5088fc04f4440260bdb9d3f040d99061c05d243
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "72620340"
---
# <a name="advanced-search-operators-in-search-expressions"></a>Operátory rozšířeného vyhledávání ve vyhledávacích výrazech
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Pomocí pokročilých operátorů vyhledávání můžete upřesnit hledání obsahu vytvořením složitějších vyhledávacích výrazů od jednodušších. Jak ukazuje následující tabulka, tyto operátory omezují kontext, ve kterém se dotaz spouští.

> [!WARNING]
> Je nutné zadat pokročilé operátory vyhledávání s koncovým dvojtečkou a bez mezer před dvojtečkou, aby je bylo možné rozpoznat v hledaném modulu.

|Hledání|Použití|Příklad|Výsledek|
|-------------------|---------|-------------|------------|
|Termín v názvu tématu|název:|title: BinaryReader|Témata, která v názvech obsahují "BinaryReader".|
|Termín v příkladu kódu|kód:|kód: readdouble|Témata obsahující "readdouble" v příkladu kódu.|
|Termín v příkladu konkrétního programovacího jazyka|kód: VB:|kód: VB: řetězec|Témata obsahující řetězec "String" v příkladu Visual Basic.|
|Téma přidružené ke konkrétnímu klíčovému slovu indexu|klíčové slovo|klíčové slovo: ReadByte|Témata, která jsou přidružená k klíčovému slovu indexu "ReadByte".|

 Můžete použít operátor Code: k vyhledání obsahu o některém z několika programovacích jazyků, ale vrátí výsledky pouze pro obsah, který je označen pomocí konkrétního programovacího jazyka. V následující tabulce jsou uvedeny programovací jazyky, které tento operátor podporuje:

|Programovací jazyk|Použití|
|--------------------------|---------|
|Visual Basic|kód: VB<br /><br /> nebo<br /><br /> kód: VisualBasic|
|C#|kód: c #<br /><br /> nebo<br /><br /> kód: CSharp|
|C++|kód: cpp<br /><br /> nebo<br /><br /> kód: c++<br /><br /> nebo<br /><br /> kód: cplusplus|
|F#|kód: f #<br /><br /> nebo<br /><br /> kód: FSharp|
|JavaScript|kód: JavaScript<br /><br /> nebo<br /><br /> kód: js|
|XAML|kód: XAML|

## <a name="see-also"></a>Viz také
 [Logické operátory ve výrazech vyhledávání](../ide/logical-operators-in-search-expressions.md) [– tipy pro fulltextové vyhledávání](../ide/full-text-search-tips.md)
