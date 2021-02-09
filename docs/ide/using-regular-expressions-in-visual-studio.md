---
title: Použít regulární výrazy
description: Přečtěte si o některých znacích regulárních výrazů, operátorech, konstrukcích a vzorcích vzorů, které můžete použít v sadě Visual Studio.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: d62d35a296c70462aab75af5a8c6729179d5b34d
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99925769"
---
# <a name="use-regular-expressions-in-visual-studio"></a>Použití regulárních výrazů v sadě Visual Studio

Visual Studio používá [regulární výrazy .NET](/dotnet/standard/base-types/regular-expressions) k hledání a nahrazování textu.

## <a name="regular-expression-examples"></a>Příklady regulárních výrazů

Následující tabulka obsahuje některé znaky regulárního výrazu, operátory, konstrukce a příklady vzorů. Podrobnější informace najdete v tématu [Jazyk regulárních výrazů](/dotnet/standard/base-types/regular-expression-language-quick-reference).

|Účel|Výraz|Příklad|
|-------------|----------------|-------------|
|Odpovídá jakémukoli jednomu znaku (s výjimkou konce řádku). Další informace naleznete v tématu [libovolný znak](/dotnet/standard/base-types/character-classes-in-regular-expressions#any-character-).|.|`a.o` porovnává "ARO" v "okolí" a "ABO" v "About", ale ne "acro" v "napříč".|
|Porovná žádný nebo více výskytů předcházejícího výrazu (odpovídá tolik znakům, kolik jich je možné). Další informace naleznete v tématu [neshoda nula nebo](/dotnet/standard/base-types/quantifiers-in-regular-expressions#match-zero-or-more-times-)vícekrát.|*|`a*r` odpovídá "r" v "racku", "ar" v "Ark" a "AAR" ve "Aardvark"|
|Odpovídá jakémukoli znaku nula nebo vícekrát.|.*|`c.*e` odpovídá "cke" v "Racket", "comm" v "comment" a "Code" v "Code"|
|Porovnává s jedním nebo více výskyty předcházejícího výrazu (odpovídá co nejvíce znakům). Další informace naleznete v tématu [porovnává jednou nebo](/dotnet/standard/base-types/quantifiers-in-regular-expressions#match-one-or-more-times-)vícekrát.|+|`e+d` odpovídá "EED" v "Feeder" a "Ed" ve "zvolna"|
|Porovnává libovolný znak jednou nebo vícekrát.|.+|`e.+e` Porovná "eede" v "Feeder", ale nenajde žádné shody v "kanálu".|
|Porovná žádný nebo více výskytů předcházejícího výrazu (odpovídá co nejvíce znakům). Další informace najdete v tématu [Shoda nula nebo vícekrát (opožděné porovnávání)](/dotnet/standard/base-types/quantifiers-in-regular-expressions#match-zero-or-more-times-lazy-match-).|*?|`\w*?d` Porovná "FAD" a "Ed" v "vybledlé", ale ne celé slovo "vybledlé" kvůli opožděné shodě|
|Odpovídá jednomu nebo více výskytům předcházejícího výrazu (odpovídá co nejvíce znakům). Další informace najdete v tématu [vyhledání jedné nebo více časů (opožděné porovnávání)](/dotnet/standard/base-types/quantifiers-in-regular-expressions#match-one-or-more-times-lazy-match-).|+?|`e\w+?` Porovná "EE" v "spánku" a "Ed" ve "zvolna", ale nenajde žádné shody v "zeslabit".|
|Ukotvení řetězce shody na [začátek řádku nebo řetězce](/dotnet/standard/base-types/anchors-in-regular-expressions#start-of-string-or-line-)|^|`^car` odpovídá slovu "auto" jenom v případě, že se zobrazuje na začátku řádku.|
|Ukotvení řetězce shody na [konec řádku](/dotnet/standard/base-types/anchors-in-regular-expressions#end-of-string-or-line-)|\r? $|`car\r?$` Porovná auto, jenom když se objeví na konci řádku.|
|Ukotvení řetězce shody na konec souboru|$|`car$` Porovná auto, jenom když se objeví na konci souboru.|
|Odpovídá jakémukoli jednomu znaku v sadě|kódem|`b[abc]` odpovídá "BA", "BB" a "BC"|
|Odpovídá jakémukoli znaku v rozsahu znaků|[a-f]|`be[n-t]` Porovná "Tip" v "Between", "Robert" v "pod" a "BES" v "dále", ale nenajde žádné shody v "níže".|
|Zachytit a implicitně očíslovat výraz obsažený v závorkách|()|`([a-z])X\1` Porovná "aXa" a "bXb", ale ne "aXb". "\ 1" odkazuje na první skupinu výrazů "[a-z]". Další informace najdete v tématu [skupiny zachycení a vzory nahrazení](#capture-groups-and-replacement-patterns). |
|Zrušení platnosti shody|(?! kódem|`real(?!ity)` Porovná "Real" ve výrazech "Realty" a "Real", ale není ve skutečnosti "realita". Vyhledá také druhý "reálný" (ale nikoli první "reálnou") v "realityreal".|
|Odpovídá jakémukoli znaku, který není v dané sadě znaků. Další informace naleznete v tématu [Skupina negativních znaků](/dotnet/standard/base-types/character-classes-in-regular-expressions#negative-character-group-).|[^ abc]|`be[^n-t]` Porovná "BEF" v "před", "Bá" v "za" a "popisku" v "níže", ale nenajde žádné shody v řetězci "pod".|
|Porovnává buď výraz před, nebo za symbolem.|&#124;|`(sponge|mud) bath` odpovídá "houbě" a "bahenní lázeň"|
|[Řídicí znak](/dotnet/standard/base-types/character-escapes-in-regular-expressions) za zpětným lomítkem| \\ |`\^` odpovídá znaku ^|
|Zadejte počet výskytů předcházejícího znaku nebo skupiny. Další informace najdete v tématu [vyhledání přesně n krát](/dotnet/standard/base-types/quantifiers-in-regular-expressions#match-exactly-n-times-n).|{n}, kde n je počet výskytů|`x(ab){2}x` odpovídá "xababx"<br/>`x(ab){2,3}x` Porovná "xababx" a "xabababx", ale ne "xababababx"|
|[Odpovídá textu v kategorii Unicode](/dotnet/standard/base-types/character-classes-in-regular-expressions#unicode-category-or-unicode-block-p). Další informace o třídách znaků Unicode naleznete v tématu [vlastnosti znaků Unicode Standard 5,2](http://www.unicode.org/versions/Unicode5.2.0/ch04.pdf).|\p{X}, kde "X" je číslo Unicode.|`\p{Lu}` odpovídá "T" a "D" v "Tomáši Chvojková"|
|[Odpovídá hranici slova](/dotnet/standard/base-types/anchors-in-regular-expressions#word-boundary-b)|\b (vně třídy znaků `\b` Určuje hranici slova a uvnitř třídy znaků `\b` Určuje znak BACKSPACE.)|`\bin` Porovná "in" v "Inside", ale nenajde žádné shody v "Pinto"|
|Odpovídá zalomení řádku (tj. znak návratu na začátek řádku následovaný novým řádkem).|\r? \n|`End\r?\nBegin` Porovná "end" a "begin" pouze v případě, že "end" je poslední řetězec v řádku a "begin" je první řetězec na následujícím řádku.|
|Odpovídá jakémukoli [znaku slova](/dotnet/standard/base-types/character-classes-in-regular-expressions#word-character-w)|\w|`a\wd` odpovídá "Add" a "A1d", ale nikoli "a d"|
|Odpovídá jakémukoli [prázdnému znaku](/dotnet/standard/base-types/character-classes-in-regular-expressions#whitespace-character-s)|\s|`Public\sInterface` odpovídá frázi "veřejné rozhraní"|
|Odpovídá libovolnému [znaku desítkové číslice](/dotnet/standard/base-types/character-classes-in-regular-expressions#decimal-digit-character-d)|\d|`\d` odpovídá "4" a "0" v "WD40"|

Příklad regulárního výrazu, který kombinuje některé operátory a konstrukce, aby odpovídaly hexadecimálnímu číslu `\b0[xX]([0-9a-fA-F]+\)\b` . Tento výraz odpovídá "0xc67f", ale nikoli "0xc67g".

> [!TIP]
> V operačních systémech Windows většina řádků končí "\r\n" (znak návratu na začátek řádku a nový řádek). Tyto znaky nejsou viditelné, ale jsou k dispozici v editoru a předány do služby regulárních výrazů .NET.

## <a name="capture-groups-and-replacement-patterns"></a>Skupiny zachycení a vzory nahrazení

Skupina zachycení vymezují dílčí výraz regulárního výrazu a zachycuje podřetězec vstupního řetězce. Můžete použít zachycené skupiny v rámci samotného regulárního výrazu (například pro hledání opakovaného slova) nebo ve vzoru pro nahrazení. Podrobné informace naleznete v tématu [seskupovací konstrukce v regulárních výrazech](/dotnet/standard/base-types/grouping-constructs-in-regular-expressions).

Chcete-li vytvořit číslovanou skupinu zachycení, uzavřete dílčí výraz se závorkami ve vzoru regulárního výrazu. Zachycení jsou očíslována automaticky zprava doleva na základě pozice levé závorky v regulárním výrazu. Přístup k zachycené skupině:

- **v rámci regulárního výrazu**: use `\number` . Například `\1` v regulárním výrazu `(\w+)\s\1` odkazuje na první skupinu zachycení `(\w+)` .

- **ve vzoru pro nahrazování**: použijte `$number` . Například seskupený regulární výraz `(\d)([a-z])` definuje dvě skupiny: první skupina obsahuje jednu desítkovou číslici a druhá skupina obsahuje jeden znak mezi **a** a **z**. Výraz najde čtyři shody v následujícím řetězci: **1A 2B 3C 4D**. Řetězec pro nahrazení `z$1` odkazuje pouze na první skupinu ( `$1` ) a převede řetězec na **Z1 Z2 Z3 Z4**.

Následující obrázek ukazuje regulární výraz `(\w+)\s\1` a náhradní řetězec `$1` . Regulární výraz i vzor pro nahrazení odkazují na první skupinu zachycení, která je automaticky očíslována 1. Zvolíte-li možnost **Nahradit vše** v dialogovém okně **rychlé nahrazení** v aplikaci Visual Studio, jsou z textu odstraněna opakující se slova.

![Rychlé nahrazení znázorňující očíslovanou skupinu zachycení v aplikaci Visual Studio](media/numbered-capture-group.png)

> [!TIP]
> Ujistěte se, že je v dialogovém okně **rychlé nahrazení** vybráno tlačítko **použít regulární výrazy** .

### <a name="named-capture-groups"></a>Pojmenované skupiny zachycení

Místo toho, abyste se museli spoléhat na automatické číslování skupiny zachycení, můžete mu dát název. Syntaxe pojmenované skupiny zachycení je `(?<name>subexpression)` .

Pojmenované skupiny zachycení, jako jsou číslované skupiny zachycení, lze použít v rámci samotného regulárního výrazu nebo ve vzoru pro nahrazení. Přístup k pojmenované skupině zachycení:

- **v rámci regulárního výrazu**: use `\k<name>` . Například `\k<repeated>` v regulárním výrazu `(?<repeated>\w+)\s\k<repeated>` odkazuje na skupinu zachycení s názvem `repeated` a jejíž dílčí výraz je `\w+` .

- **ve vzoru pro nahrazování**: použijte `${name}` . Například, `${repeated}`.

Jako příklad ukazuje následující obrázek regulární výraz `(?<repeated>\w+)\s\k<repeated>` a náhradní řetězec `${repeated}` . Regulární výraz i vzor pro nahrazení odkazují na skupinu zachycení s názvem `repeated` . Zvolíte-li možnost **Nahradit vše** v dialogovém okně **rychlé nahrazení** v aplikaci Visual Studio, jsou z textu odstraněna opakující se slova.

![Rychlé nahrazení zobrazující pojmenovanou skupinu zachycení v aplikaci Visual Studio](media/named-capture-group.png)

> [!TIP]
> Ujistěte se, že je v dialogovém okně **rychlé nahrazení** vybráno tlačítko **použít regulární výrazy** .

Další informace o pojmenovaných skupinách zachycení naleznete v tématu [pojmenované odpovídající podvýrazy](/dotnet/standard/base-types/grouping-constructs-in-regular-expressions#named-matched-subexpressions). Další informace o regulárních výrazech, které jsou použity v vzorech pro nahrazení, naleznete v tématu [substitutions in Regular Expressions](/dotnet/standard/base-types/substitutions-in-regular-expressions).

## <a name="see-also"></a>Viz také

- [Jazyk regulárních výrazů](/dotnet/standard/base-types/regular-expression-language-quick-reference)
- [Vyhledání a nahrazení textu](../ide/finding-and-replacing-text.md)
