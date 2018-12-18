---
title: Použít regulární výrazy
ms.date: 03/26/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: conceptual
f1_keywords:
- vsregularexpressionhelp
- vs.regularexpressionhelp
- vs.wildcardsbuilder
- vs.netregularexpressionhelp
- vs.wildcards
helpviewer_keywords:
- regular expressions [Visual Studio]
- regular expressions
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 40983e4180db9530983217d581b898806dd85d27
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/07/2018
ms.locfileid: "53063795"
---
# <a name="use-regular-expressions-in-visual-studio"></a>Použití regulárních výrazů v sadě Visual Studio

Visual Studio používá [regulárních výrazech .NET Frameworku](/dotnet/standard/base-types/regular-expressions) najít a nahradit text.

## <a name="replacement-patterns"></a>Vzory pro nahrazení

Chcete-li použít číslovanou zachycenou skupinu, před a za skupiny pomocí závorek ve vzorku regulárního výrazu. Použití `$number`, kde `number` je celé číslo počínaje 1, chcete-li určit konkrétní, číslované skupiny ve vzorech pro nahrazení. Například seskupené regulární výraz `(\d)([a-z])` definuje dvě skupiny: první skupinu jednu číslici desítkové soustavy a druhé skupině obsahuje jeden znak mezi **a** a **z**. Výraz najde čtyři shod v následujícím řetězci: **1a 2b 3c 4d**. Řetězci pro nahrazení `z$1` odkazuje na první skupinu a převede řetězec na **z1 z2 z3 z4**.

Informace o formátování regulárních výrazů, které se používají ve vzorech pro nahrazení najdete v tématu [nahrazení v regulárních výrazech (Průvodce technologií .NET)](/dotnet/standard/base-types/substitutions-in-regular-expressions).

## <a name="regular-expression-examples"></a>Příklady regulárních výrazů

Následuje několik příkladů:

|Účel|Výraz|Příklad|
|-------------|----------------|-------------|
|Odpovídá jakémukoli jednomu znaku (s výjimkou konce řádku)|.|`a.o` odpovídá "ARO" ve slově "around" a "abo" ve "o" ale ne "acro" v "v".|
|Odpovídá žádnému nebo více výskytům předcházejícího výrazu (odpovídá co nejvíce znakům)|*|`a*r` odpovídá "r" ve "rack", "ar" ve slově "ark" a "aar" ve slově "aardvark"|
|Odpovídá jakémukoli znaku nula nebo vícekrát (zástupný znak *)|.*|`c.*e` odpovídá "cke" ve "racket", "comme" ve "komentář" a "code" ve "kód"|
|Odpovídá jeden nebo více výskytům předcházejícího výrazu (odpovídá co nejvíce znakům)|+|`e.+d` odpovídá "rychlost" ve "slově feeder" ale ne "upravit".|
|Odpovídá jakémukoli znaku jednou nebo vícekrát (zástupný znak?)|.+|`e.+e` odpovídá "eede" ve "slově feeder" ale ne "ee".|
|Odpovídá žádnému nebo více výskytům předcházejícího výrazu (odpovídá co nejméně znakům)|*?|`e.*?e` odpovídá "ee" ve "slově feeder" ale ne "eede".|
|Odpovídá jeden nebo více výskytům předcházejícího výrazu (odpovídá co nejméně znakům)|+?|`e.+?e` odpovídá "ente" a "erprise" ve slově "enterprise", ale ne celému slovu "enterprise".|
|Ukotvení řetězce shody na začátek řetězce nebo řádku|^|`^car` odpovídá slovu "car" pouze, pokud se nachází na začátku řádku.|
|Ukotvení řetězce shody na konec řádku|\r?$|`end\r?$` odpovídá "end" pouze pokud je zobrazeno na konci řádku.|
|Ukotvení řetězce shody na konec souboru|$|`end$` odpovídá "end" pouze pokud je zobrazeno na konci souboru.|
|Odpovídá jakémukoli jednomu znaku v sadě|[abc]|`b[abc]` odpovídá "ba", "bb" a "bc".|
|Odpovídá jakémukoli znaku v rozsahu znaků|[a-f]|`be[n-t]` odpovídá "bet" v "between", "ben" v "beneath" a "bes" ve "beside", ale ne "below".|
|Zachytí a implicitně očísluje výraz v závorkách|()|`([a-z])X\1` porovnává "s aXa" a "bXb", ale nikoli "aXb". "\1" se vztahuje k první skupině výrazů "[a-z]".|
|Znehodnotit shodu|(?! ABC)|`real(?!ity)` odpovídá "real" ve slově "realty" a "really", ale ne "reality." Najde také druhý "real" (ale ne první "real") v "realityreal".|
|Odpovídá jakémukoli znaku, který není v dané sadě znaků|[^ abc]|`be[^n-t]` odpovídá "bef" v "before", "beh" v "behind" a "bel" ve "below", ale ne "beneath".|
|Odpovídá výrazu před nebo jednomu za symbolem.|&#124;|`(sponge\|mud) bath` odpovídá "výrazům relaxační koupel" a "bahenní koupel".|
|Řídicí znak po zpětném lomítku| \\ |`\^` odpovídá znaku ^.|
|Určení počtu výskytů předchozího znaku nebo skupiny|{x}, kde x je počet výskytů|`x(ab){2}x` odpovídá "xababx" a `x(ab){2,3}x` odpovídá "xababx" a "xabababx" ale ne "xababababx".|
|Odpovídá textu ve třídě znaků Unicode. Další informace o třídách znaků Unicode naleznete v tématu<br /><br /> [Vlastnosti znaků Unicode Standard 5.2](http://www.unicode.org/versions/Unicode5.2.0/ch04.pdf).|\p{X}, kde "X" je číslo sady Unicode.|`\p{Lu}` odpovídá "T" a "D" v "Thomas Doe".|
|Porovná hranici slova|\b (mimo třídu znaků `\b` určuje hranici slova a uvnitř třídy znaků `\b` Určuje znak backspace.)|`\bin` odpovídá "in" v "inside" ale ne "pinto".|
|Odpovídá konci řádku (to znamená zalomení řádku a nový řádek).|\r?\n|`End\r?\nBegin` odpovídá "End" a "Begin" pouze, když je "End" posledním řetězcem v řádku a "Begin" je první řetězec v následujícím řádku.|
|Odpovídá libovolnému alfanumerickému znaku|\w|`a\wd` odpovídá "Přidat" a "a1d", ale ne "a d".|
|Odpovídá jakémukoli prázdnému znaku.|(?([^\r\n])\s)|`Public\sInterface` odpovídá slovnímu "Veřejné rozhraní".|
|Odpovídá jakémukoli číselnému znaku|\d|`\d` shody a "3" v "3456", "2" ve "23" a "1" v "1".|
|Odpovídá znaku Unicode|\uXXXX kde XXXX Určuje hodnotu znaku Unicode.|`\u0065` odpovídá znaku "e".|
|Odpovídá identifikátoru|\b [\_\w-[0-9]] [\_\w]*\b|Odpovídá "type1" ale ne "& type1" nebo "#define".|
|Odpovídá řetězci v uvozovkách|((\\".+?\\")&#124;('.+?'))|Odpovídá jakémukoli řetězci v jednoduchých nebo dvojitých uvozovkách.|
|Shoda s šestnáctkovým číslem|\b0[xX]([0-9a-fA-F]\)\b|Odpovídá "0xc67f", ale ne "0xc67fc67f".|
|Odpovídá celým nebo desetinným a desetinných míst|\b[0-9]*\\.\*[0-9]+\b|Odpovídá "1,333".|

> [!TIP]
> V operačních systémech Windows většina řádků končí "\r\n" (zalomení řádku a nový řádek). Tyto znaky nejsou viditelné, ale jsou k dispozici v editoru a jsou předány službě regulárních výrazů .NET.

## <a name="see-also"></a>Viz také:

- [Vyhledání a nahrazení textu](../ide/finding-and-replacing-text.md)
