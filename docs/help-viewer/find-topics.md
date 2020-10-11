---
title: Hledat témata (prohlížeč nápovědy)
description: Naučte se Hledat témata v Microsoft Help Viewer. Umožňuje přizpůsobit hledání pomocí zástupných výrazů, logických operátorů a operátorů rozšířeného vyhledávání.
ms.date: 11/02/2017
ms.topic: how-to
ms.assetid: 683f1b0c-1551-4bba-91fe-3855f03fdd69
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 46eb9c21b5bc6f7d0a577b85d043933b48bf60bc
ms.sourcegitcommit: dfbbf041e68ec3a4cd97196b19c9226a4793e702
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/09/2020
ms.locfileid: "91878992"
---
# <a name="how-to-search-for-topics"></a>Postupy: hledání témat

Pomocí funkce fulltextového vyhledávání můžete vyhledat všechna témata obsahující konkrétní slovo. Hledání můžete také Upřesnit a upravit pomocí zástupných výrazů, logických operátorů a operátorů rozšířeného vyhledávání.

Kartu **Vyhledat** otevřete tak, že v okně aplikace **Help Viewer** kliknete na kartu **Vyhledat** , nebo pokud jste uživatel s klávesnicí, vyberte **CTRL** + **E**.

## <a name="to-perform-a-full-text-search"></a>Provedení fulltextového vyhledávání

1. Do vyhledávacího pole zadejte slovo, které chcete najít.

2. Ve vyhledávacím dotazu určete, které logické nebo rozšířené operátory vyhledávání se mají použít pro hledání, pokud existuje. Pokud chcete vyhledat všechny dostupné informace, nepoužívejte operátory.

    > [!NOTE]
    > V dialogovém okně **Možnosti prohlížeče** můžete zadat další předvolby, jako je maximální počet výsledků hledání, které se mají zobrazit v čase, a to, jestli se má obsah v angličtině zahrnout, pokud vaše primární národní prostředí není anglické.

3. Klikněte na klávesu **ENTER** .

     Hledání vrátí maximálně 200 přístupů ve výchozím nastavení a zobrazí je v oblasti výsledků hledání. V závislosti na obsahu se mohou zobrazit další informace o verzi pro každý výsledek.

4. Chcete-li zobrazit téma, vyberte jeho název ze seznamu výsledků.

## <a name="full-text-search-tips"></a>Tipy pro fulltextové vyhledávání

Můžete vytvořit cílená hledání, která vrátí pouze témata, která vás zajímají. Pokud rozumíte tomu, jak syntaxe ovlivňuje váš dotaz. Syntaxe obsahuje speciální znaky, vyhrazená slova a filtry. V tomto tématu najdete tipy, postupy a podrobné informace o syntaxi, které vám pomůžou lépe vytvořit dotazy.

### <a name="general-guidelines"></a>Obecné pokyny

Následující tabulka obsahuje některá základní pravidla a pokyny pro vývoj vyhledávacích dotazů v nápovědě.

|Syntax|Description|
|------------|-----------------|
|Rozlišovat velká a malá písmena|Při hledání se nerozlišují malá a velká písmena. Vytvořte kritéria hledání pomocí velkých nebo malých písmen. Například OLE a OLE vrátí stejné výsledky.|
|Kombinace znaků|Nelze hledat pouze pro jednotlivá písmena (a-z) nebo čísla (0-9). Pokud se pokusíte vyhledat určitá vyhrazená slova, například "a", "z" a "with", budou ignorována. Další informace najdete v tématu [ignorovaná slova v hledáních](#stopwords) dále v tomto tématu.|
|Pořadí vyhodnocování|Vyhledávací dotazy jsou vyhodnocovány zleva doprava.|

### <a name="search-syntax"></a>Syntaxe hledání

Pokud zadáte hledaný řetězec, který obsahuje více slov, například "word1 word2", je řetězec shodný s zadáním řetězce "word1 AND word2", který vrátí pouze témata obsahující všechna jednotlivá slova ve hledaném řetězci.

> [!IMPORTANT]
> - Hledání frází není podporováno. Pokud zadáte více než jedno slovo ve hledaném řetězci, budou vrácená témata obsahovat všechna slova, která jste zadali, ale nemusí být nutně přesně zadaná fráze.
> - Pomocí logických operátorů určete vztah mezi slovy v hledané frázi. K dalšímu upřesnění hledání můžete použít logické operátory, například a, nebo, ne a blízko. Pokud například hledáte "deklaraci v blízkosti sjednocení", budou výsledky hledání obsahovat témata, která obsahují slova "deklarace" a "sjednocení" bez dalších slov od sebe navzájem. Další informace najdete v tématu [logické operátory ve vyhledávacích výrazech](../help-viewer/logical-operators-search-expressions.md).

### <a name="filters"></a>Filtry

Výsledky hledání můžete dále omezit pomocí operátorů pokročilého vyhledávání. Help obsahuje tři kategorie, které lze použít k filtrování výsledků fulltextového vyhledávání: název, kód a klíčové slovo.

### <a name="ranking-of-search-results"></a>Řazení výsledků hledání

Algoritmus pro hledání v seznamu výsledků používá určitá kritéria, která vám pomůžou dosáhnout vyšší nebo nižší úrovně výsledků hledání. Obecně platí:

1. Obsah, který obsahuje hledaná slova v názvu, je seřazený nad více než obsahem.

2. Obsah, který obsahuje hledaná slova v blízkosti, je větší než obsah, který ne.

3. Obsah, který obsahuje vyšší hustotu hledaných slov, je větší než obsah s nižší hustotou hledaných slov.

### <a name=""></a><a name="stopwords"> Ignorovaná slova při hledání (stop slova) </a>

Často se vyskytují slova nebo čísla, která jsou někdy označována jako stopová slova, jsou automaticky ignorována během fulltextového vyhledávání. Pokud například hledáte frázi "Pass through", výsledky hledání zobrazí témata obsahující slovo "Pass", ale ne "do".

## <a name="see-also"></a>Viz také

- [Logické a pokročilé operátory](../help-viewer/logical-operators-search-expressions.md)
- [Postupy: hledání témat v indexu](../help-viewer/find-topics-index.md)
- [Postupy: hledání témat v obsahu](../help-viewer/find-topics-toc.md)
- [Microsoft Help Viewer](../help-viewer/overview.md)