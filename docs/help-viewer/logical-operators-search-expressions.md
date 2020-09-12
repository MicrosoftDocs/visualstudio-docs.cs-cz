---
title: Logické operátory ve vyhledávacích výrazech (Help Viewer)
ms.custom: SEO-VS-2020
ms.date: 11/02/2017
ms.topic: reference
helpviewer_keywords:
- Help Viewer, logical operators in search
- logical operators in search [Help Viewer]
ms.assetid: 0c38ae7d-3e20-4d47-a020-9677cd285916
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 9daceca2540a2da61a46e12a458c012ce7851001
ms.sourcegitcommit: 4ae5e9817ad13edd05425febb322b5be6d3c3425
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/11/2020
ms.locfileid: "90038631"
---
# <a name="logical-and-advanced-operators-in-search-expressions"></a>Logické a pokročilé operátory ve vyhledávacích výrazech

Pomocí logických operátorů a operátorů rozšířeného vyhledávání můžete upřesnit hledání obsahu nápovědy v aplikaci **Help Viewer**.

## <a name="logical-operators"></a>Logické operátory

Logické operátory určují, jak se má v hledaném dotazu kombinovat vícenásobné hledané výrazy. V následující tabulce jsou uvedeny logické operátory a, nikoli a blízko.

|Hledání|Použití|Příklad|Výsledek|
|-------------------|---------|-------------|------------|
|Oba výrazy ve stejném článku|AND|DIB a paleta|Témata, která obsahují "DIB" i "paleta".|
|Termín v článku|NEBO|rastrový nebo vektorový|Témata, která obsahují buď rastrový nebo vektorový.|
|První výraz bez druhého termínu ve stejném článku|NOT|operační systém bez DOS|Témata obsahující "operační systém", ale ne "DOS".|
|Obě tyto výrazy spolu úzce spolupracují v článku.|LEVÉMU|uživatel poblíž jádra|Témata, která obsahují slovo "uživatel" v blízkosti blízkosti "jádra".|

> [!IMPORTANT]
> Je nutné zadat logické operátory do všech velkých písmen pro vyhledávací modul, aby je bylo možné rozpoznat.

## <a name="advanced-operators"></a>Pokročilí operátoři

Operátory pokročilého vyhledávání umožňují Upřesnit hledání obsahu zadáním místa v článku hledání hledaného termínu. Následující tabulka popisuje čtyři dostupné operátory rozšířeného vyhledávání.

|Hledání|Použití|Příklad|Výsledek|
|-------------------|---------|-------------|------------|
|Termín v názvu článku|`title:`|`title:binaryreader`|Témata, která v názvech obsahují "BinaryReader".|
|Termín v příkladu kódu|`code:`|`code:readdouble`|Témata obsahující "readdouble" v příkladu kódu.|
|Termín v příkladu konkrétního programovacího jazyka|`code:vb:`|`code:vb:string`|Témata, která obsahují řetězec "String" v příkladu kódu Visual Basic.|
|Článek přidružený ke konkrétnímu klíčovému slovu indexu|`keyword:`|`keyword:readbyte`|Témata, která jsou přidružená k klíčovému slovu indexu "ReadByte".|

> [!IMPORTANT]
> Je nutné zadat pokročilé operátory vyhledávání s koncovým dvojtečkou a bez mezer před dvojtečkou, aby je bylo možné rozpoznat v hledaném modulu.

### <a name="programming-languages-for-code-examples"></a>Programovací jazyky pro příklady kódu

Operátor můžete použít `code:` k vyhledání obsahu o některém z několika programovacích jazyků. Chcete-li vracet příklady pro určitý programovací jazyk, použijte jednu z následujících hodnot programovacího jazyka:

|Programovací jazyk|Syntaxe operátoru hledání|
| - |---------|
|Visual Basic|`code:vb`<br/>`code:visualbasic`|
|C#|`code:c#`<br/>`code:csharp`|
|C++|`code:cpp`<br/>`code:c++`<br/>`code:cplusplus`|
|F#|`code:f#`<br/>`code:fsharp`|
|JavaScript|`code:javascript`<br/>`code:js`|
|XAML|`code:xaml`|

> [!NOTE]
> `code:`Operátor najde obsah, který je označen pomocí popisku programovacího jazyka, na rozdíl od obsahu, který je obecně označen jako kód.

## <a name="see-also"></a>Viz také

- [Postupy: hledání témat](../help-viewer/find-topics.md)
- [Microsoft Help Viewer](../help-viewer/overview.md)
