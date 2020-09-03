---
title: Upozornění na pojmenování | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- vs.codeanalysis.namingrules
helpviewer_keywords:
- managed code analysis warnings, naming warnings
- naming warnings
- warnings, naming
ms.assetid: f97223ce-1d39-4134-81c9-fff2c75d979b
caps.latest.revision: 21
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 03bc20d4bf39aa31865007e46e7ad3615f4b95bc
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "72655970"
---
# <a name="naming-warnings"></a>Upozornění na pojmenování
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Upozornění na pojmenování podporují dodržování zásad vytváření názvů v [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] pokynech pro návrh.

## <a name="in-this-section"></a>V tomto oddílu

|Pravidlo|Popis|
|----------|-----------------|
|[CA1700: Nepojmenovávejte výčty hodnot 'Reserved'](../code-quality/ca1700-do-not-name-enum-values-reserved.md)|Toto pravidlo předpokládá, že člen výčtu, který má název obsahující výraz „reserved“, není aktuálně používán, ale je zástupným symbolem k přejmenování nebo odstranění v budoucí verzi. Přejmenování nebo odstranění členu je narušující změna.|
|[CA1713: Události by neměly mít předponu před nebo po](../code-quality/ca1713-events-should-not-have-before-or-after-prefix.md)|Název události začíná řetězcem „Before“ nebo „After“. Pro pojmenování souvisejících událostí vyvolaných v určitém pořadí je vhodné používat přítomný a minulý čas, který naznačí relativní pozici v pořadí akcí.|
|[CA1714: Výčty příznaků by neměly mít názvy v množném čísle](../code-quality/ca1714-flags-enums-should-have-plural-names.md)|Veřejný výčet má atribut System. FlagsAttribute a jeho název nekončí na "s". Typy, které jsou označeny jako FlagsAttribute, mají názvy plural, protože atribut označuje, že lze zadat více než jednu hodnotu.|
|[CA1704: Identifikátory by měly být zadány správně](../code-quality/ca1704-identifiers-should-be-spelled-correctly.md)|Název externě viditelného identifikátoru obsahuje jedno nebo více slov, která knihovna kontroly pravopisu společnosti Microsoft nerozpoznala.|
|[CA1708: Identifikátory by se měly lišit více než použitím malých a velkých písmen](../code-quality/ca1708-identifiers-should-differ-by-more-than-case.md)|Identifikátory pro obory názvů, typy, členy a parametry nelze odlišit pouze ve velikosti písmen, protože jazyky cílené na modul CLR (Common Language Runtime) nemusí rozlišovat malá a velká písmena.|
|[CA1715: Identifikátory by měly mít správnou předponu](../code-quality/ca1715-identifiers-should-have-correct-prefix.md)|Název externě viditelného rozhraní nezačíná velkým písmenem "I".  Název parametru obecného typu na externě viditelném typu nebo metodě nezačíná velkým písmenem "T".|
|[CA1720: Identifikátory by neměly obsahovat názvy typů](../code-quality/ca1720-identifiers-should-not-contain-type-names.md)|Název parametru v externě viditelném členu obsahuje název datového typu nebo název externě viditelného členu obsahuje název datového typu specifický podle jazyka.|
|[CA1722: Identifikátory by neměly mít nesprávnou předponu](../code-quality/ca1722-identifiers-should-not-have-incorrect-prefix.md)|Podle konvence mají pouze některé programovací prvky názvy začínající určitou předponou.|
|[CA1711: Identifikátory by neměly mít nesprávnou příponu](../code-quality/ca1711-identifiers-should-not-have-incorrect-suffix.md)|Pouze názvy typů, které rozšiřují určité základní typy nebo které implementují určitá rozhraní nebo typy, které jsou odvozeny z těchto typů, by podle konvence měly končit určitými vyhrazenými příponami. Jiné názvy typů by neměly používat tyto vyhrazené přípony.|
|[CA1717: Pouze výčty FlagsAttribute by měly mít názvy v množném čísle](../code-quality/ca1717-only-flagsattribute-enums-should-have-plural-names.md)|Konvence pojmenování přikazují, aby název výčtu v množném čísle vyjadřoval, že lze současně zadat více než jednu hodnotu výčtu.|
|[CA1725: Názvy parametrů by měly odpovídat základní deklaraci](../code-quality/ca1725-parameter-names-should-match-base-declaration.md)|Konzistentní pojmenování parametrů v hierarchii přetěžování zvyšuje použitelnost přetížení metody. Název parametru, který se v odvozené metodě liší od názvu v základní deklaraci, může způsobit zmatení, zda se u metody jedná o přepis základní metody, nebo o nové přetížení metody.|
|[CA1719: Názvy parametrů by se neměly shodovat s názvy členů](../code-quality/ca1719-parameter-names-should-not-match-member-names.md)|Název parametru by měl sdělit význam parametru a název členu by měl sdělit význam člena. Byl by to vzácný návrh, pokud by byly stejné. Stejné pojmenování parametru i jeho členu je neintuitivní a činí knihovnu obtížně použitelnou.|
|[CA1701: Malá a velká písmena složených slov řetězců prostředků by měla být použita správně](../code-quality/ca1701-resource-string-compound-words-should-be-cased-correctly.md)|Každé slovo v řetězci prostředku je rozděleno na tokeny, které jsou založeny na velikosti písmen. Každá kombinace dvou sousedících tokenů je zkontrolována knihovnou kontroly pravopisu společnosti Microsoft. Je-li kombinace rozpoznána, způsobí slovo porušení pravidla.|
|[CA1703: Řetězce prostředků by měly být zadány správně](../code-quality/ca1703-resource-strings-should-be-spelled-correctly.md)|Zdrojový řetězec obsahuje jedno nebo více slov, která knihovna kontroly pravopisu společnosti Microsoft nerozpoznala.|
|[CA1724: Názvy typů by se neměly shodovat s obory názvů](../code-quality/ca1724-type-names-should-not-match-namespaces.md)|Názvy typů by neměly odpovídat názvům oborů názvů, které jsou definovány v [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] knihovně tříd. Porušení tohoto pravidla může snížit použitelnost knihovny.|
|[CA1707: Identifikátory by neměly obsahovat podtržítka](../code-quality/ca1707-identifiers-should-not-contain-underscores.md)|Názvy identifikátorů podle konvence neobsahují znak podtržítka (_). Toto pravidlo kontroluje obory názvů, typy, členy a parametry.|
|[CA1721: Názvy vlastností by se neměly shodovat s metodami Get](../code-quality/ca1721-property-names-should-not-match-get-methods.md)|Název soukromého nebo chráněného členu začíná na „Get“ a dále se shoduje s názvem veřejné nebo chráněné vlastnosti. Metody „Get“ a vlastnosti by měly mít názvy, které zřetelně rozliší jejich funkce.|
|[CA1716: Identifikátory by se neměly shodovat s klíčovými slovy](../code-quality/ca1716-identifiers-should-not-match-keywords.md)|Název oboru názvů nebo název typu odpovídá vyhrazenému klíčovému slovu programovacího jazyka. Identifikátory pro obory názvů a typů by neměly odpovídat klíčovým slovům, která jsou definována jazyky cílenými na modul CLR (Common Language Runtime).|
|[CA1726: Použijte upřednostňované výrazy](../code-quality/ca1726-use-preferred-terms.md)|Název externě viditelného identifikátoru zahrnuje výraz, pro který existuje alternativní upřednostňovaný výraz. Název případně obsahuje také výraz „Flag“ nebo „Flags“.|
|[CA1709: Malá a velká písmena identifikátorů by měla být použita správně](../code-quality/ca1709-identifiers-should-be-cased-correctly.md)|Podle konvence názvy parametrů používají ve stylu CamelCase velká a malá písmena, typy a názvy členů používají název Pascal.|
|[CA1702: Malá a velká písmena složených slov by měla být použita správně](../code-quality/ca1702-compound-words-should-be-cased-correctly.md)|Název identifikátoru obsahuje více slov a alespoň jedno ze slov se zdá být složené slovo, které není správně formátováno.|
|[CA1712: Nezačínejte hodnoty výčtu názvem typu](../code-quality/ca1712-do-not-prefix-enum-values-with-type-name.md)|Názvy členů výčtu nejsou uvozeny názvem typu, protože informace o typu se mají poskytnout pomocí vývojářských nástrojů.|
|[CA1710: Identifikátory by měly mít správnou příponu](../code-quality/ca1710-identifiers-should-have-correct-suffix.md)|Podle konvence mají názvy typů, které rozšíří určité základní typy nebo které implementují určitá rozhraní nebo typy odvozené z těchto typů, příponu, která je přidružena k základnímu typu nebo rozhraní.|
