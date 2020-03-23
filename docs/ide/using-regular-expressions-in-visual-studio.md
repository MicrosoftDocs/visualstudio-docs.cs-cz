---
title: Použít regulární výrazy
ms.date: 09/13/2019
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
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f1739d6b2376a4f86edd3c0102f7fad79da5d7cd
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "75568617"
---
# <a name="use-regular-expressions-in-visual-studio"></a>Použití regulárních výrazů v sadě Visual Studio

Visual Studio používá [regulární výrazy .NET k vyhledání](/dotnet/standard/base-types/regular-expressions) a nahrazení textu.

## <a name="regular-expression-examples"></a>Příklady regulárních výrazů

Následující tabulka obsahuje některé znaky regulárních výrazů, operátory, konstrukce a příklady vzorku. Podrobnější informace naleznete v tématu [Jazyk regulárních výrazů](/dotnet/standard/base-types/regular-expression-language-quick-reference).

|Účel|Expression|Příklad|
|-------------|----------------|-------------|
|Porovná libovolný jednotlivý znak (s výjimkou zalomení řádku). Další informace naleznete v tématu [Libovolný znak](/dotnet/standard/base-types/character-classes-in-regular-expressions#any-character-).|.|`a.o`odpovídá "aro" v "kolem" a "abo" v "o", ale ne "acro" v "across"|
|Porovná nula nebo více výskytů předchozího výrazu (odpovídá co největšímu počtu znaků). Další informace naleznete v [tématu Shoda nula nebo vícekrát](/dotnet/standard/base-types/quantifiers-in-regular-expressions#match-zero-or-more-times-).|*|`a*r`odpovídá "r" v "rack", "ar" v "archa", a "aar" v "aardvark"|
|Porovná libovolný znak nula nebo vícekrát.|.*|`c.*e`odpovídá "cke" v "raketa", "comme" v "komentář", a "kód" v "kód"|
|Porovná jeden nebo více výskytů předchozího výrazu (odpovídá co největšímu počtu znaků). Další informace naleznete v [tématu Shoda jednou nebo vícekrát](/dotnet/standard/base-types/quantifiers-in-regular-expressions#match-one-or-more-times-).|+|`e+d`odpovídá "eed" v "podavač" a "ed" v "vybledlé"|
|Porovná libovolný znak jednou nebo vícekrát.|.+|`e.+e`odpovídá "eede" v "podavači", ale nenalezne žádné shody v "feed"|
|Porovná nula nebo více výskytů předchozího výrazu (odpovídá co nejmenšímu počtu znaků). Další informace naleznete [v tématu Match nula nebo více krát (opožděná shoda)](/dotnet/standard/base-types/quantifiers-in-regular-expressions#match-zero-or-more-times-lazy-match-).|*?|`\w*?d`odpovídá "výstřelek" a "ed" v "vybledlé", ale ne celé slovo "vybledlé" kvůli líný zápas|
|Porovná jeden nebo více výskytů předchozího výrazu (odpovídá co nejmenšímu počtu znaků). Další informace naleznete [v tématu Match jednou nebo vícekrát (opožděná shoda)](/dotnet/standard/base-types/quantifiers-in-regular-expressions#match-one-or-more-times-lazy-match-).|+?|`e\w+?`odpovídá "ee" v "sleep" a "ed" v "vybledlé", ale nenajde žádné shody v "fade"|
|Ukotvení řetězce shody na [začátek řádku nebo řetězce](/dotnet/standard/base-types/anchors-in-regular-expressions#start-of-string-or-line-)|^|`^car`odpovídá slovu "auto" pouze tehdy, když se objeví na začátku řádku|
|Ukotvení řetězce shody na [konec řádku](/dotnet/standard/base-types/anchors-in-regular-expressions#end-of-string-or-line-)|\r?$|`car\r?$`odpovídá "auto" pouze tehdy, když se objeví na konci řádku|
|Ukotvení řetězce shody na konec souboru|$|`car$`odpovídá "auto" pouze v případě, že se objeví na konci souboru|
|Porovná libovolný jednotlivý znak v sadě.|To je v pořádku.|`b[abc]`odpovídá "ba", "bb" a "bc"|
|Porovná libovolný znak v rozsahu znaků|[a-f]|`be[n-t]`odpovídá "sázce" v "between", "ben" v "pod" a "bes" v "vedle", ale nenajde žádné shody v "níže"|
|Zachycení a implicitní číslo výrazu obsaženého v závorce|()|`([a-z])X\1`odpovídá "aXa" a "bXb", ale ne "aXb". "\1" odkazuje na první skupinu výrazů "[a-z]". Další informace naleznete v [tématu Zachycení skupin a vzorů nahrazení](#capture-groups-and-replacement-patterns). |
|Zrušení shody|(?! abc)|`real(?!ity)`odpovídá "skutečné" v "realty" a "opravdu", ale ne v "realitě". To také najde druhý "skutečný" (ale ne první "skutečný") v "realityreal".|
|Porovná libovolný znak, který není v dané sadě znaků. Další informace naleznete v [tématu Negativní skupina znaků](/dotnet/standard/base-types/character-classes-in-regular-expressions#negative-character-group-).|[^abc]|`be[^n-t]`odpovídá "bef" v "before", "beh" v "behind" a "bel" v "below", ale nenalezne žádné shody v "pod"|
|Porovná buď výraz před, nebo výraz za symbolem.|&#124;|`(sponge|mud) bath`odpovídá "houbové koupeli" a "bahenní koupeli"|
|[Uniknout znaku](/dotnet/standard/base-types/character-escapes-in-regular-expressions) za zpětným lomítkem| \\ |`\^`odpovídá znaku ^|
|Zadejte počet výskytů předchozího znaku nebo skupiny. Další informace naleznete [v tématu Match exactly n times](/dotnet/standard/base-types/quantifiers-in-regular-expressions#match-exactly-n-times-n).|{n}, kde 'n' je počet výskytů|`x(ab){2}x`odpovídá "xababx"<br/>`x(ab){2,3}x`odpovídá "xababx" a "xabababx", ale ne "xababababx"|
|[Shodovat text v kategorii Unicode](/dotnet/standard/base-types/character-classes-in-regular-expressions#unicode-category-or-unicode-block-p). Další informace o třídách znaků Unicode naleznete [v tématu Unicode Standard 5.2 Character Properties](http://www.unicode.org/versions/Unicode5.2.0/ch04.pdf).|\p{X}, kde "X" je číslo Unicode.|`\p{Lu}`odpovídá "T" a "D" v "Thomas Doe"|
|[Shoda hranice slova](/dotnet/standard/base-types/anchors-in-regular-expressions#word-boundary-b)|\b (Mimo třídu `\b` znaků určuje hranici slova a `\b` uvnitř třídy znaků je určující backspace.)|`\bin`odpovídá "in" v "uvnitř", ale nenajde žádné shody v "pinto"|
|Porovná zalomení řádku (to znamená návrat vozíku následované novým řádkem)|\r?\n|`End\r?\nBegin`Odpovídá "End" a "Begin" pouze v případě, že "End" je poslední řetězec v řádku a "Begin" je první řetězec v dalším řádku|
|Shoda libovolného [znaku slova](/dotnet/standard/base-types/character-classes-in-regular-expressions#word-character-w)|\w|`a\wd`odpovídá "přidat" a "a1d", ale ne "d"|
|Porovná libovolný [znak prázdného znaku](/dotnet/standard/base-types/character-classes-in-regular-expressions#whitespace-character-s)|\s|`Public\sInterface`odpovídá frázi "Veřejné rozhraní"|
|Porovná libovolný [desetinný znak](/dotnet/standard/base-types/character-classes-in-regular-expressions#decimal-digit-character-d)|\d|`\d`odpovídá "4" a "0" v "wd40"|

Příklad regulárního výrazu, který kombinuje některé operátory a konstrukce tak, aby odpovídaly šestnáctkové číslo je `\b0[xX]([0-9a-fA-F]+\)\b`. Tento výraz odpovídá "0xc67f", ale ne "0xc67g".

> [!TIP]
> V operačních systémech Windows většina řádků končí na "\r\n" (návrat vozíku následovaný novým řádkem). Tyto znaky nejsou viditelné, ale jsou přítomny v editoru a předány službě regulárního výrazu .NET.

## <a name="capture-groups-and-replacement-patterns"></a>Zachycení skupin a vzorů nahrazení

Skupina sběru vymezuje podvýraz regulárního výrazu a zachycuje podřetězec vstupního řetězce. Zachycené skupiny můžete použít v rámci samotného regulárního výrazu (například k vyhledání opakovaného slova) nebo v náhradním vzoru. Podrobné informace naleznete v [tématu Seskupování konstrukcí v regulárních výrazech](/dotnet/standard/base-types/grouping-constructs-in-regular-expressions).

Chcete-li vytvořit očíslovnou skupinu sběru, obklopte podvýraz závorky ve vzorku regulárního výrazu. Zachycení jsou číslována automaticky zleva doprava na základě pozice počáteční závorky v regulárním výrazu. Přístup k zachycené skupině:

- **v regulárním výrazu**: Použít `\number`. Například `\1` v regulárním výrazu `(\w+)\s\1` `(\w+)`odkazuje na první skupinu zachycení .

- **v náhradním**vzoru `$number`: Použijte . Seskupený regulární výraz `(\d)([a-z])` například definuje dvě skupiny: první skupina obsahuje jednu desetinnou číslici a druhá skupina obsahuje jeden znak mezi **a** a **z**. Výraz vyhledá čtyři shody v následujícím řetězci: **1a 2b 3c 4d**. Náhradní řetězec `z$1` odkazuje pouze na`$1`první skupinu ( ) a převede řetězec na **z1 z2 z3 z4**.

Následující obrázek znázorňuje regulární výraz `(\w+)\s\1` a náhradní řetězec `$1`. Regulární výraz i náhradní vzor odkazují na první skupinu zachycení, která je automaticky očíslovaná 1. Když v **aplikaci** Visual Studio zvolíte **Nahradit vše,** z textu se z textu odeberou opakovaná slova.

![Rychlá výměna zobrazující očíslovnou skupinu zachycení v sadě Visual Studio](media/numbered-capture-group.png)

> [!TIP]
> Ujistěte se, že je v dialogovém okně **Rychlá výměna** vybráno tlačítko **Použít regulární výrazy.**

### <a name="named-capture-groups"></a>Pojmenované skupiny sběru

Místo spoléhání se na automatické číslování skupiny zachycení, můžete jí dát název. Syntaxe pojmenované skupiny `(?<name>subexpression)`sběru je .

Pojmenované skupiny sběru, jako jsou číslované skupiny sběru, lze použít v rámci samotného regulárního výrazu nebo v náhradním vzoru. Přístup k pojmenované skupině zachycení:

- **v regulárním výrazu**: Použít `\k<name>`. Například `\k<repeated>` v regulárním `(?<repeated>\w+)\s\k<repeated>` výrazu odkazuje na `repeated` skupinu zachycení, která je pojmenována a jejíž dílčí výraz je `\w+`.

- **v náhradním**vzoru `${name}`: Použijte . Například, `${repeated}`.

Například následující obrázek ukazuje regulární `(?<repeated>\w+)\s\k<repeated>` výraz `${repeated}`a náhradní řetězec . Regulární výraz i náhradní vzor odkazují `repeated`na skupinu sběru s názvem . Když v **aplikaci** Visual Studio zvolíte **Nahradit vše,** z textu se z textu odeberou opakovaná slova.

![Rychlé nahrazení zobrazující pojmenovanou skupinu zachycení v sadě Visual Studio](media/named-capture-group.png)

> [!TIP]
> Ujistěte se, že je v dialogovém okně **Rychlá výměna** vybráno tlačítko **Použít regulární výrazy.**

Další informace o pojmenovaných skupinách sběru naleznete [v tématu Pojmenované odpovídající podvýrazy](/dotnet/standard/base-types/grouping-constructs-in-regular-expressions#named-matched-subexpressions). Další informace o regulárních výrazech, které se používají v náhradních vzorcích, naleznete [v tématu Substituce v regulárních výrazech](/dotnet/standard/base-types/substitutions-in-regular-expressions).

## <a name="see-also"></a>Viz také

- [Jazyk regulárních výrazů](/dotnet/standard/base-types/regular-expression-language-quick-reference)
- [Vyhledání a nahrazení textu](../ide/finding-and-replacing-text.md)
