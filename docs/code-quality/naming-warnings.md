---
title: Upozornění na pojmenování
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- vs.codeanalysis.namingrules
helpviewer_keywords:
- managed code analysis warnings, naming warnings
- naming warnings
- warnings, naming
ms.assetid: f97223ce-1d39-4134-81c9-fff2c75d979b
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 38ca0bd70b3732c19df6aecbfa88a2ea1534e485
ms.sourcegitcommit: ad5fb20f18b23eb8bd2568717f61edc6b7eee5e7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/01/2018
ms.locfileid: "47859637"
---
# <a name="naming-warnings"></a>Upozornění na pojmenování
Upozornění na pojmenování podporují dodržování konvencí pokyny k návrhu architektury .NET.

## <a name="in-this-section"></a>V tomto oddílu

|Pravidlo|Popis|
|----------|-----------------|
|[CA1700: Nepojmenovávejte výčty hodnot Reserved](../code-quality/ca1700-do-not-name-enum-values-reserved.md)|Toto pravidlo předpokládá, že člen výčtu, který má název obsahující výraz „reserved“, není aktuálně používán, ale je zástupným symbolem k přejmenování nebo odstranění v budoucí verzi. Přejmenování nebo odstranění členu je narušující změna.|
|[CA1713: Události by neměly mít předponu před nebo po](../code-quality/ca1713-events-should-not-have-before-or-after-prefix.md)|Název události začíná řetězcem „Before“ nebo „After“. Pro pojmenování souvisejících událostí vyvolaných v určitém pořadí je vhodné používat přítomný a minulý čas, který naznačí relativní pozici v pořadí akcí.|
|[CA1714: Výčty příznaků by neměly mít názvy v množném čísle](../code-quality/ca1714-flags-enums-should-have-plural-names.md)|Veřejný výčet má atribut System.FlagsAttribute a jeho název nekončí "s". Typy, které jsou označeny FlagsAttribute mají názvy, které jsou v množném čísle, protože tento atribut označuje, že lze zadat více než jednu hodnotu.|
|[CA1704: Identifikátory by měly být zadány správně](../code-quality/ca1704-identifiers-should-be-spelled-correctly.md)|Název externě viditelného identifikátoru obsahuje jedno nebo více slov, která knihovna kontroly pravopisu společnosti Microsoft nerozpoznala.|
|[CA1708: Identifikátory by se měly lišit více než použitím malých a velkých písmen](../code-quality/ca1708-identifiers-should-differ-by-more-than-case.md)|Identifikátory pro obory názvů, typy, členy a parametry nelze odlišit pouze ve velikosti písmen, protože jazyky cílené na modul CLR (Common Language Runtime) nemusí rozlišovat malá a velká písmena.|
|[CA1715: Identifikátory by měly mít správnou předponu](../code-quality/ca1715-identifiers-should-have-correct-prefix.md)|Název externě viditelného rozhraní nezačíná řetězcem kapitálových "I".  Název parametru obecného typu na externě viditelný typ nebo metoda nezačíná velkým "T".|
|[CA1720: Identifikátory by neměly obsahovat názvy typů](../code-quality/ca1720-identifiers-should-not-contain-type-names.md)|Název parametru v externě viditelném členu obsahuje název datového typu nebo název externě viditelného členu obsahuje název datového typu specifický podle jazyka.|
|[CA1722: Identifikátory by neměly mít nesprávnou předponu](../code-quality/ca1722-identifiers-should-not-have-incorrect-prefix.md)|Podle konvence mají pouze některé programovací prvky názvy začínající určitou předponou.|
|[CA1711: Identifikátory by neměly mít nesprávnou příponu](../code-quality/ca1711-identifiers-should-not-have-incorrect-suffix.md)|Pouze názvy typů, které rozšiřují určité základní typy nebo které implementují určitá rozhraní nebo typy, které jsou odvozeny z těchto typů, by podle konvence měly končit určitými vyhrazenými příponami. Jiné názvy typů by neměly používat tyto vyhrazené přípony.|
|[CA1717: Pouze výčty FlagsAttribute by měly mít názvy v množném čísle](../code-quality/ca1717-only-flagsattribute-enums-should-have-plural-names.md)|Konvence pojmenování přikazují, aby název výčtu v množném čísle vyjadřoval, že lze současně zadat více než jednu hodnotu výčtu.|
|[CA1725: Názvy parametrů by měly odpovídat základní deklaraci](../code-quality/ca1725-parameter-names-should-match-base-declaration.md)|Konzistentní pojmenování parametrů v hierarchii přetěžování zvyšuje použitelnost přetížení metody. Název parametru, který se v odvozené metodě liší od názvu v základní deklaraci, může způsobit zmatení, zda se u metody jedná o přepis základní metody, nebo o nové přetížení metody.|
|[CA1719: Názvy parametrů by neměly odpovídat názvům členů](../code-quality/ca1719-parameter-names-should-not-match-member-names.md)|Název parametru by měl sdělit význam parametru a název členu by měl sdělit význam členu. Byl by to vzácný návrh, pokud by byly stejné. Stejné pojmenování parametru i jeho členu je neintuitivní a činí knihovnu obtížně použitelnou.|
|[CA1701: Malá a velká písmena složených slov prostředku řetězců by měla být použita správně](../code-quality/ca1701-resource-string-compound-words-should-be-cased-correctly.md)|Každé slovo řetězce zdroje je rozděleno na tokeny, které jsou založeny na velká a malá písmena. Každá kombinace dvou sousedících tokenů je zkontrolována knihovnou kontroly pravopisu společnosti Microsoft. Je-li kombinace rozpoznána, způsobí slovo porušení pravidla.|
|[CA1703: Řetězce prostředků by měly být zadány správně](../code-quality/ca1703-resource-strings-should-be-spelled-correctly.md)|Zdrojový řetězec obsahuje jedno nebo více slov, která knihovna kontroly pravopisu společnosti Microsoft nerozpoznala.|
|[CA1724: Názvy typů by neměly odpovídat oborům názvů](../code-quality/ca1724-type-names-should-not-match-namespaces.md)|Názvy typů by neměly odpovídat názvům obory názvů, které jsou definovány v knihovně tříd rozhraní .NET Framework. Porušení tohoto pravidla může snížit použitelnost knihovny.|
|[CA1707: Identifikátory by neměly obsahovat podtržítka](../code-quality/ca1707-identifiers-should-not-contain-underscores.md)|Názvy identifikátorů podle konvence neobsahují znak podtržítka (_). Toto pravidlo kontroluje obory názvů, typy, členy a parametry.|
|[CA1721: Názvy vlastností by neměly odpovídat metodám Get](../code-quality/ca1721-property-names-should-not-match-get-methods.md)|Název soukromého nebo chráněného členu začíná na „Get“ a dále se shoduje s názvem veřejné nebo chráněné vlastnosti. Metody „Get“ a vlastnosti by měly mít názvy, které zřetelně rozliší jejich funkce.|
|[CA1716: Identifikátory by neměly odpovídat klíčovým slovům](../code-quality/ca1716-identifiers-should-not-match-keywords.md)|Název oboru názvů nebo název typu odpovídá vyhrazenému klíčovému slovu programovacího jazyka. Identifikátory pro obory názvů a typů by neměly odpovídat klíčovým slovům, která jsou definována jazyky cílenými na modul CLR (Common Language Runtime).|
|[CA1726: Použijte upřednostňované výrazy](../code-quality/ca1726-use-preferred-terms.md)|Název externě viditelného identifikátoru zahrnuje výraz, pro který existuje alternativní upřednostňovaný výraz. Název případně obsahuje také výraz „Flag“ nebo „Flags“.|
|[CA1709: Malá a velká písmena identifikátorů by měla být použita správně](../code-quality/ca1709-identifiers-should-be-cased-correctly.md)|Podle konvence používají názvy parametrů ve formátu camelCase velká a malá písmena a obor názvů, typ a názvů členů pomocí Pascal velká a malá písmena.|
|[CA1702: Malá a velká písmena složených slov by měla být použita správně](../code-quality/ca1702-compound-words-should-be-cased-correctly.md)|Název identifikátoru obsahuje více slov a alespoň jedno ze slov se zdá být složené slovo, které není správně formátováno.|
|[CA1712: Nezačínejte hodnoty výčtu s názvem typu](../code-quality/ca1712-do-not-prefix-enum-values-with-type-name.md)|Názvy členů výčtu nemají předponu s názvem typu, protože informace o typu očekává se, které poskytují nástroje pro vývoj.|
|[CA1710: Identifikátory by měly mít správnou příponu](../code-quality/ca1710-identifiers-should-have-correct-suffix.md)|Podle úmluvy názvy typů, které rozšiřují určité základní typy nebo které implementují určitá rozhraní, nebo typů odvozených z těchto typů máte příponu, která je přidružena k základní typ nebo rozhraní.|