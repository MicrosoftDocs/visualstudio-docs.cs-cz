---
title: 'CA1033: metody rozhraní by měly být volatelné podřízenými typy | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- InterfaceMethodsShouldBeCallableByChildTypes
- CA1033
helpviewer_keywords:
- CA1033
- InterfaceMethodsShouldBeCallableByChildTypes
ms.assetid: 9f171497-a5e3-4769-a77b-7aed755b2662
caps.latest.revision: 19
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 18629f8d5c63b652d6539db10c6e6dba5d621c24
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/30/2020
ms.locfileid: "85542295"
---
# <a name="ca1033-interface-methods-should-be-callable-by-child-types"></a>CA1033: Metody rozhraní by měly být volatelné podřízenými typy
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Položka|Hodnota|
|-|-|
|TypeName|InterfaceMethodsShouldBeCallableByChildTypes|
|CheckId|CA1033|
|Kategorie|Microsoft. Design|
|Narušující změna|Nenarušující|

## <a name="cause"></a>Příčina
 Nezapečetěný externě viditelný typ poskytuje explicitní implementaci metod veřejného rozhraní a neposkytuje alternativní externě viditelnou metodu stejného názvu.

## <a name="rule-description"></a>Popis pravidla
 Vezměte v úvahu základní typ, který explicitně implementuje metodu veřejného rozhraní. Typ, který je odvozen od základního typu, má přístup k zděděné metodě rozhraní pouze prostřednictvím odkazu na aktuální instanci ( `this` v jazyce C#), která je převedena na rozhraní. Pokud odvozený typ znovu implementuje (explicitně) zděděnou metodu rozhraní, k základní implementaci již nelze přivodit. Volání prostřednictvím aktuální reference instance vyvolá odvozenou implementaci; To způsobí rekurzi a případné přetečení zásobníku.

 Toto pravidlo neoznamuje porušení explicitní implementace, <xref:System.IDisposable.Dispose%2A?displayProperty=fullName> Pokud je k dispozici externě viditelný `Close()` nebo `System.IDisposable.Dispose(Boolean)` metoda.

## <a name="how-to-fix-violations"></a>Jak vyřešit porušení
 Chcete-li opravit porušení tohoto pravidla, implementujte novou metodu, která zveřejňuje stejnou funkci a je viditelná pro odvozené typy nebo se změní na neexplicitní implementaci. V případě, že je zásadní změna přijatelné, alternativou je vytvořit zapečetěný typ.

## <a name="when-to-suppress-warnings"></a>Kdy potlačit upozornění
 Je bezpečné potlačit upozornění z tohoto pravidla, pokud je k dispozici externě viditelná metoda, která má stejnou funkci, ale jiný název než explicitně implementovaná metoda.

## <a name="example"></a>Příklad
 Následující příklad ukazuje typ, `ViolatingBase` , který porušuje pravidlo a typ, `FixedBase` ,, který ukazuje opravu pro porušení.

 [!code-csharp[FxCop.Design.ExplicitMethodImplementations#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.ExplicitMethodImplementations/cs/FxCop.Design.ExplicitMethodImplementations.cs#1)]

## <a name="see-also"></a>Viz také
 [Rozhraní](https://msdn.microsoft.com/library/2feda177-ce11-432d-81b4-d50f5f35fd37)
