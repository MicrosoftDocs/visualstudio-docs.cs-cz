---
title: Upozornění na pojmenování
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.codeanalysis.namingrules
helpviewer_keywords:
- managed code analysis warnings, naming warnings
- naming warnings
- warnings, naming
ms.assetid: f97223ce-1d39-4134-81c9-fff2c75d979b
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 45eb7442278d783b2663da2ba8587bea38632fa1
ms.sourcegitcommit: 5caad925ca0b5d136416144a279e984836d8f28c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2020
ms.locfileid: "89509000"
---
# <a name="naming-warnings"></a>Upozornění na pojmenování

Upozornění na pojmenování podporují dodržování zásad vytváření názvů v pokynech pro návrh .NET.

## <a name="in-this-section"></a>V tomto oddílu

|Pravidlo|Popis|
|----------|-----------------|
|[CA1700: Nepojmenovávejte výčty hodnot 'Reserved'](../code-quality/ca1700.md)|Toto pravidlo předpokládá, že člen výčtu, který má název obsahující výraz „reserved“, není aktuálně používán, ale je zástupným symbolem k přejmenování nebo odstranění v budoucí verzi. Přejmenování nebo odstranění členu je narušující změna.|
|[CA1707: Identifikátory by neměly obsahovat podtržítka](../code-quality/ca1707.md)|Názvy identifikátorů podle konvence neobsahují znak podtržítka (_). Toto pravidlo kontroluje obory názvů, typy, členy a parametry.|
|[CA1708: Identifikátory by se měly lišit více než použitím malých a velkých písmen](../code-quality/ca1708.md)|Identifikátory pro obory názvů, typy, členy a parametry nelze odlišit pouze ve velikosti písmen, protože jazyky cílené na modul CLR (Common Language Runtime) nemusí rozlišovat malá a velká písmena.|
|[CA1710: Identifikátory by měly mít správnou příponu](../code-quality/ca1710.md)|Podle konvence mají názvy typů, které rozšíří určité základní typy nebo které implementují určitá rozhraní nebo typy odvozené z těchto typů, příponu, která je přidružena k základnímu typu nebo rozhraní.|
|[CA1711: Identifikátory by neměly mít nesprávnou příponu](../code-quality/ca1711.md)|Pouze názvy typů, které rozšiřují určité základní typy nebo které implementují určitá rozhraní nebo typy, které jsou odvozeny z těchto typů, by podle konvence měly končit určitými vyhrazenými příponami. Jiné názvy typů by neměly používat tyto vyhrazené přípony.|
|[CA1712: Nezačínejte hodnoty výčtu názvem typu](../code-quality/ca1712.md)|Názvy členů výčtu nejsou uvozeny názvem typu, protože informace o typu se mají poskytnout pomocí vývojářských nástrojů.|
|[CA1713: Události by neměly mít předponu před nebo po](../code-quality/ca1713.md)|Název události začíná řetězcem „Before“ nebo „After“. Pro pojmenování souvisejících událostí vyvolaných v určitém pořadí je vhodné používat přítomný a minulý čas, který naznačí relativní pozici v pořadí akcí.|
|[CA1714: Výčty příznaků by neměly mít názvy v množném čísle](../code-quality/ca1714.md)|Veřejný výčet má atribut System. FlagsAttribute a jeho název nekončí na "s". Typy, které jsou označeny jako FlagsAttribute, mají názvy plural, protože atribut označuje, že lze zadat více než jednu hodnotu.|
|[CA1715: Identifikátory by měly mít správnou předponu](../code-quality/ca1715.md)|Název externě viditelného rozhraní nezačíná velkým písmenem "I".  Název parametru obecného typu na externě viditelném typu nebo metodě nezačíná velkým písmenem "T".|
|[CA1716: Identifikátory by se neměly shodovat s klíčovými slovy](../code-quality/ca1716.md)|Název oboru názvů nebo název typu odpovídá vyhrazenému klíčovému slovu programovacího jazyka. Identifikátory pro obory názvů a typů by neměly odpovídat klíčovým slovům, která jsou definována jazyky cílenými na modul CLR (Common Language Runtime).|
|[CA1717: Pouze výčty FlagsAttribute by měly mít názvy v množném čísle](../code-quality/ca1717.md)|Konvence pojmenování přikazují, aby název výčtu v množném čísle vyjadřoval, že lze současně zadat více než jednu hodnotu výčtu.|
|[CA1720: Identifikátory by neměly obsahovat názvy typů](../code-quality/ca1720.md)|Název parametru v externě viditelném členu obsahuje název datového typu nebo název externě viditelného členu obsahuje název datového typu specifický podle jazyka.|
|[CA1721: Názvy vlastností by se neměly shodovat s metodami Get](../code-quality/ca1721.md)|Název soukromého nebo chráněného členu začíná na „Get“ a dále se shoduje s názvem veřejné nebo chráněné vlastnosti. Metody „Get“ a vlastnosti by měly mít názvy, které zřetelně rozliší jejich funkce.|
|[CA1724: Názvy typů by se neměly shodovat s obory názvů](../code-quality/ca1724.md)|Názvy typů by neměly odpovídat názvům oborů názvů .NET. Porušení tohoto pravidla může snížit použitelnost knihovny.|
|[CA1725: Názvy parametrů by měly odpovídat základní deklaraci](../code-quality/ca1725.md)|Konzistentní pojmenování parametrů v hierarchii přetěžování zvyšuje použitelnost přetížení metody. Název parametru, který se v odvozené metodě liší od názvu v základní deklaraci, může způsobit zmatení, zda se u metody jedná o přepis základní metody, nebo o nové přetížení metody.|
