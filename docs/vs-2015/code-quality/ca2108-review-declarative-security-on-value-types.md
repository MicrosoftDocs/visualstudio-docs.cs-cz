---
title: 'CA2108: Projděte si deklarativní zabezpečení u hodnot typu | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- ReviewDeclarativeSecurityOnValueTypes
- CA2108
helpviewer_keywords:
- ReviewDeclarativeSecurityOnValueTypes
- CA2108
ms.assetid: d62bffdd-3826-4d52-a708-1c646c5d48c2
caps.latest.revision: 18
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 03918353b66c36698b5d17b332da052b6d95c87a
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/30/2020
ms.locfileid: "85544388"
---
# <a name="ca2108-review-declarative-security-on-value-types"></a>CA2108: Zkontrolujte deklarativní zabezpečení u typů hodnot
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Položka|Hodnota|
|-|-|
|TypeName|ReviewDeclarativeSecurityOnValueTypes|
|CheckId|CA2108|
|Kategorie|Microsoft.Security|
|Narušující změna|Bez přerušení|

## <a name="cause"></a>Příčina
 Veřejný nebo chráněný typ hodnoty je zabezpečený [daty a modelováním](https://msdn.microsoft.com/library/8c37635d-e2c1-4b64-a258-61d9e87405e6) nebo [požadavky propojení](https://msdn.microsoft.com/library/a33fd5f9-2de9-4653-a4f0-d9df25082c4d).

## <a name="rule-description"></a>Popis pravidla
 Typy hodnot jsou přiděleny a inicializovány jejich výchozími konstruktory předtím, než se spustí jiné konstruktory. Pokud je typ hodnoty zabezpečený požadavkem nebo LinkDemand a volající nemá oprávnění, která splní kontrolu zabezpečení, jakýkoliv jiný konstruktor než výchozí selže a vyvolá se výjimka zabezpečení. Typ hodnoty není navrácený; je ponechán ve stavu nastaveném jeho výchozím konstruktorem. Nepředpokládají, že volající, který předává instanci typu hodnoty, má oprávnění vytvořit nebo získat přístup k instanci.

## <a name="how-to-fix-violations"></a>Jak vyřešit porušení
 Porušení tohoto pravidla nelze opravit, Pokud neodeberete kontrolu zabezpečení z daného typu a na svém místě použijete kontrolu zabezpečení na úrovni metod. Všimněte si, že vyřešení porušení tímto způsobem nezabrání volajícím s nedostatečnými oprávněními v získání instancí typu hodnoty. Je nutné zajistit, aby instance typu hodnoty ve svém výchozím stavu nezveřejnila citlivé informace, a nelze ji použít škodlivou způsobem.

## <a name="when-to-suppress-warnings"></a>Kdy potlačit upozornění
 Můžete potlačit upozornění z tohoto pravidla, pokud kterýkoli volající může získat instance typu hodnoty ve svém výchozím stavu bez ohrožení zabezpečení.

## <a name="example"></a>Příklad
 Následující příklad ukazuje knihovnu obsahující typ hodnoty, který toto pravidlo porušuje. Všimněte si, že `StructureManager` typ předpokládá, že volající, který předává instanci typu hodnoty, má oprávnění vytvořit nebo získat přístup k instanci.

 [!code-csharp[FxCop.Security.DemandOnValueType#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.DemandOnValueType/cs/FxCop.Security.DemandOnValueType.cs#1)]

## <a name="example"></a>Příklad
 Následující aplikace demonstruje slabé stránky knihovny.

 [!code-csharp[FxCop.Security.TestDemandOnValueType#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.TestDemandOnValueType/cs/FxCop.Security.TestDemandOnValueType.cs#1)]

 Tento příklad vytvoří následující výstup.

 **Vlastní konstruktor struktury: požadavek se nezdařil.** 
 **Nové hodnoty SecuredTypeStructure 100 100** 
 **Nové hodnoty SecuredTypeStructure 200 200**
## <a name="see-also"></a>Viz také
 [Propojení vyžaduje](https://msdn.microsoft.com/library/a33fd5f9-2de9-4653-a4f0-d9df25082c4d) [data a modelování](https://msdn.microsoft.com/library/8c37635d-e2c1-4b64-a258-61d9e87405e6)
