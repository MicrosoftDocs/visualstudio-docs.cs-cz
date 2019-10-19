---
title: Tipy pro fulltextové vyhledávání | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
f1_keywords:
- hv_search
helpviewer_keywords:
- Help Viewer 2.0, full-text search tips
- full-text search tips [Help Viewer 2.0]
ms.assetid: bcaad23d-2ca7-4bec-8b54-b884bc34e70b
caps.latest.revision: 15
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: ac683ff6e7079478d5b4e642918df4e281a53f0b
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72645656"
---
# <a name="full-text-search-tips"></a>Tipy pro fulltextové vyhledávání
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Jednou z užitečnějších metod vyhledávání informací v nápovědě je provádění fulltextového vyhledávání. Chcete-li Upřesnit a přizpůsobit výsledky, musíte pochopit, jak syntaxe ovlivňuje váš dotaz. V tomto tématu najdete tipy, postupy a podrobné informace o syntaxi, které vám pomůžou lépe vytvořit dotazy.

## <a name="full-text-search-tips"></a>Tipy pro fulltextové vyhledávání
 Můžete vytvořit cílenější hledání, které vrátí pouze témata, která vás zajímají, pokud pochopíte, jak pomůže interpretovat formátování používané v dotazech. Mezi tyto formáty patří speciální znaky, vyhrazená slova a filtry.

### <a name="general-guidelines"></a>Obecné pokyny
 Následující tabulka obsahuje některá základní pravidla a pokyny pro vývoj vyhledávacích dotazů v nápovědě.

|Syntaxe|Popis|
|------------|-----------------|
|Rozlišovat velká a malá písmena|Při hledání se nerozlišují malá a velká písmena. Vytvořte kritéria hledání pomocí velkých nebo malých písmen. Například OLE a OLE vrátí stejné výsledky.|
|Kombinace znaků|Nelze hledat pouze pro jednotlivá písmena (a – z) nebo čísla (0 – 9). Pokud se pokusíte vyhledat určitá vyhrazená slova, například "a", "z" a "with", budou ignorována. Další informace najdete v části "slova ignorovaná při hledání (stop slova)" dále v tomto tématu.|
|Pořadí vyhodnocování|Vyhledávací dotazy jsou vyhodnocovány zleva doprava.|

### <a name="search-syntax"></a>Syntaxe hledání
 Pokud zadáte hledaný řetězec, který obsahuje více slov, například "word1 word2", je řetězec shodný s zadáním řetězce "word1 AND word2", který vrátí pouze témata obsahující všechna jednotlivá slova ve hledaném řetězci.

> [!IMPORTANT]
> 1. Hledání frází není podporováno. Pokud zadáte více než jedno slovo ve hledaném řetězci, budou vrácená témata obsahovat všechna slova, která jste zadali, ale nemusí být nutně přesně zadaná fráze.
>    2. Pomocí logických operátorů určete vztah mezi slovy v hledané frázi. K dalšímu upřesnění hledání můžete použít logické operátory, například a, nebo, ne a blízko. Pokud například hledáte "deklaraci v blízkosti sjednocení", budou výsledky hledání obsahovat témata, která obsahují slova "deklarace" a "sjednocení" bez dalších slov od sebe navzájem. Další informace najdete v tématu [logické operátory ve vyhledávacích výrazech](../ide/logical-operators-in-search-expressions.md).

### <a name="filters"></a>Filtry
 Výsledky hledání můžete dále omezit pomocí operátorů pokročilého vyhledávání. Help obsahuje tři kategorie, které lze použít k filtrování výsledků fulltextového vyhledávání: název, kód a klíčové slovo. Další informace najdete v tématu [Rozšířené operátory hledání ve vyhledávacích výrazech](../ide/advanced-search-operators-in-search-expressions.md).

### <a name="ranking-of-search-results"></a>Řazení výsledků hledání
 Algoritmus pro hledání v seznamu výsledků používá určitá kritéria, která vám pomůžou dosáhnout vyšší nebo nižší úrovně výsledků hledání. Obecně platí:

1. Obsah, který obsahuje hledaná slova v názvu, je seřazený nad více než obsahem.

2. Obsah, který obsahuje hledaná slova v blízkosti, je větší než obsah, který ne.

3. Obsah, který obsahuje vyšší hustotu hledaných slov, je větší než obsah s nižší hustotou hledaných slov.

### <a name="words-ignored-in-searches-stop-words"></a>Ignorovaná slova při hledání (stop slova)
 Často se vyskytují slova nebo čísla, která jsou někdy označována jako stopová slova, jsou automaticky ignorována během fulltextového vyhledávání. Pokud například hledáte frázi "Pass through", výsledky hledání zobrazí témata obsahující slovo "Pass", ale ne "do".

## <a name="see-also"></a>Viz také
 [Vyhledání informací](../ide/locate-information.md) [logických operátorů ve výrazech hledání](../ide/logical-operators-in-search-expressions.md)
