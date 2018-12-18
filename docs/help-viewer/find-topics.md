---
title: Vyhledejte témata (Help Viewer)
ms.date: 11/02/2017
ms.prod: visual-studio-dev15
ms.topic: conceptual
ms.assetid: 683f1b0c-1551-4bba-91fe-3855f03fdd69
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 6e50a2ecb302461db6454632e6c9702cff98c711
ms.sourcegitcommit: 75e02ed88a1ace6e8265fd4e3a82a1bc78f3adca
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/13/2018
ms.locfileid: "53378158"
---
# <a name="how-to-search-for-topics"></a>Postupy: Vyhledávání témat

Funkce fulltextového vyhledávání můžete použít k vyhledání všech témat, které obsahují konkrétní slovo. Můžete také upravit a přizpůsobit vyhledávání pomocí zástupných znaků výrazy, logické operátory a operátory rozšířeného vyhledávání.

Otevřete **hledání** , vyberte **hledání** kartu **aplikace Help Viewer** okna, nebo pokud jste uživatelem klávesnice, zvolte **Ctrl** + **E**.

## <a name="to-perform-a-full-text-search"></a>K provádění fulltextové vyhledávání

1.  Do vyhledávacího pole zadejte slovo, které chcete najít.

2.  Ve vyhledávacím dotazu zadejte které operátory logických nebo rozšířené vyhledávání má použít pro vyhledávání, pokud existuje. K vyhledání všech dostupnou nápovědu, nepoužívejte operátory.

    > [!NOTE]
    > V **možnosti prohlížeče** dialogovém okně můžete zadat další předvolby, například maximální počet výsledků hledání pro zobrazení na čas a jestli se mají zahrnout obsah v angličtině, pokud vaše primární národní prostředí není anglické.

3.  Zvolte **Enter** klíč.

     Hledání ve výchozím nastavení vrátí maximálně 200 záznamů a zobrazí je v oblasti hledání výsledků. Další informace o verzi pro každý výsledek se může zobrazit v závislosti na obsahu.

4.  Chcete-li zobrazit téma, vyberte jeho záhlaví ze seznamu výsledků.

## <a name="full-text-search-tips"></a>Tipy pro fulltextové vyhledávání

Můžete vytvořit více cílené hledání, které vracejí pouze témata, které vás zajímají, pokud pochopíte vliv syntaxi dotazu. Syntaxe obsahuje speciální znaky, rezervovaná slova a filtry. Toto téma obsahuje tipy, postupy a informace o syntaxi podrobné abychom vám lépe zručné vaše dotazy.

### <a name="general-guidelines"></a>Obecné pokyny

Následující tabulka obsahuje některé základní pravidla a pokyny pro vývoj vyhledávacích dotazů v nápovědě.

|Syntaxe|Popis|
|------------|-----------------|
|Rozlišování velikosti písmen|Hledání se malá a velká písmena. Vývoj vašich kritérií vyhledávání pomocí velká nebo malá písmena. Například "OLE" a "ole" vrátí stejné výsledky.|
|Kombinace znaků|Nelze vyhledat pouze jednotlivé písmena (a-z) nebo číslice (0 – 9). Pokud se pokusíte vyhledávání pro určité vyhrazená slova, například "a", "od" a "s", budou ignorovány. Další informace najdete v tématu [slova ignoruje při hledání](#stopwords) dále v tomto tématu.|
|Pořadí vyhodnocení|Vyhledávací dotazy jsou vyhodnoceny zleva doprava.|

### <a name="search-syntax"></a>Syntaxe vyhledávání

Pokud zadáte hledaný řetězec, který obsahuje více slov, jako je například "word1 word2," Tento řetězec je zadat text "word1 word2 a", který vrátí pouze témata, která obsahují všechny jednotlivých slov ve vyhledávacím řetězci.

> [!IMPORTANT]
> - Vyhledávání frází nejsou podporovány. Pokud chcete zadat více slov ve vyhledávaném řetězci, bude vrácená témata obsahují všechna slova, která jste zadali, ale ne nutně přesnou frázi, které jste zadali.
> - Použijte logické operátory Pokud chcete určit vztah mezi slovy ve vaší vyhledávací fráze. Můžete zahrnout logické operátory, jako je například AND, OR, NOT a TÉMĚŘ, pro další upřesněte hledání. Například pokud hledáte "deklarace TÉMĚŘ sjednocení", budou výsledky hledání obsahují témata obsahující slova "deklarace" a "sjednocení" více než pár slov od sebe navzájem. Další informace najdete v tématu [logické operátory ve vyhledávacích výrazech](../help-viewer/logical-operators-search-expressions.md).

### <a name="filters"></a>Filtry

Výsledky hledání můžete omezit pomocí operátorů rozšířené vyhledávání. Nápověda obsahuje tři kategorie, které můžete použít pro filtrování výsledků fulltextové vyhledávání: Název, kód a – klíčové slovo.

### <a name="ranking-of-search-results"></a>Řazení výsledků hledání

Vyhledávací algoritmus platí určitá kritéria umožňující řazení výsledků vyšší nebo nižší v seznamu výsledků hledání. Obecně platí:

1.  Obsah, který zahrnuje hledaná slova v názvu je vyšší než obsah, který není řazením.

2.  Obsah, který obsahuje hledaná slova v těsné blízkosti je vyšší než obsah, který není řazením.

3.  Obsah, který obsahuje vyšší hustotu slova je vyšší než obsah, který má nižší hustotu slova řazením.

### <a name="stopwords"> Slova v hledání (nevýznamová slova) ignoruje. </a>

Nejčastěji se vyskytující slova nebo čísel, které jsou někdy označovány jako nevýznamová slova, se automaticky ignorují během fulltextového vyhledávání. Například pokud hledáte pro frázi "průchodu", zobrazí výsledky hledání témata obsahující slovo "heslo" ale ne "až".

## <a name="see-also"></a>Viz také:

- [Logické a rozšířené operátory](../help-viewer/logical-operators-search-expressions.md)
- [Postupy: Hledání témat v rejstříku](../help-viewer/find-topics-index.md)
- [Postupy: Hledání témat v obsahu](../help-viewer/find-topics-toc.md)
- [Microsoft Help Viewer 2.2](../help-viewer/overview.md)