---
title: 'CA1036: metody override na srovnatelných typech | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1036
- OverrideMethodsOnComparableTypes
helpviewer_keywords:
- OverrideMethodsOnComparableTypes
- CA1036
ms.assetid: 2329f844-4cb8-426d-bee2-cd065d1346d0
caps.latest.revision: 23
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 52247c9175b22d3d96aa91557ee133f37c55e789
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/30/2020
ms.locfileid: "85546598"
---
# <a name="ca1036-override-methods-on-comparable-types"></a>CA1036: Přepište metody u srovnatelných typů
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Položka|Hodnota|
|-|-|
|TypeName|OverrideMethodsOnComparableTypes|
|CheckId|CA1036|
|Kategorie|Microsoft. Design|
|Narušující změna|Nenarušující|

## <a name="cause"></a>Příčina
 Veřejný nebo chráněný typ implementuje <xref:System.IComparable?displayProperty=fullName> rozhraní a nepřepisuje <xref:System.Object.Equals%2A?displayProperty=fullName> ani nepřetěžují operátor specifický pro určitý jazyk pro rovnost, nerovnost, menší nebo větší než. Pravidlo neoznamuje porušení, pokud typ dědí pouze implementaci rozhraní.

## <a name="rule-description"></a>Popis pravidla
 Typy, které definují vlastní pořadí řazení implementují <xref:System.IComparable> rozhraní. <xref:System.IComparable.CompareTo%2A>Metoda vrátí celočíselnou hodnotu, která označuje správné pořadí řazení pro dvě instance typu. Toto pravidlo identifikuje typy, které nastaví pořadí řazení; To znamená, že neplatí běžný význam rovnosti, nerovnosti, menší než a větší než. Pokud zadáte implementaci <xref:System.IComparable> , je nutné obvykle také přepsat, aby <xref:System.Object.Equals%2A> vracely hodnoty, které jsou konzistentní s <xref:System.IComparable.CompareTo%2A> . Pokud přepíšete <xref:System.Object.Equals%2A> a budete kódovat v jazyce, který podporuje přetížení operátoru, měli byste také zadat operátory, které jsou konzistentní s <xref:System.Object.Equals%2A> .

## <a name="how-to-fix-violations"></a>Jak vyřešit porušení
 Pokud chcete opravit porušení tohoto pravidla, přepište <xref:System.Object.Equals%2A> . Pokud váš programovací jazyk podporuje přetížení operátora, zadejte následující operátory:

- op_Equality

- op_Inequality

- op_LessThan

- op_GreaterThan

  V jazyce C# tokeny, které slouží k reprezentaci těchto operátorů, jsou následující: = =,! =, \<, and > .

## <a name="when-to-suppress-warnings"></a>Kdy potlačit upozornění
 Je bezpečné potlačit upozornění z tohoto pravidla, pokud je porušení způsobeno chybějícími operátory a váš programovací jazyk nepodporuje přetížení operátoru, stejně jako v případě Visual Basic .NET. Je také bezpečné potlačit upozornění pro z tohoto pravidla, je-li aktivováno u operátorů rovnosti jiných než op_Equality, pokud určíte, že implementace operátorů nemá smysl v kontextu vaší aplikace. Nicméně byste měli vždy převádět op_Equality a operátor = =, pokud přepíšete Object. Equals.

## <a name="example"></a>Příklad
 Následující příklad obsahuje typ, který je správně implementován <xref:System.IComparable> . Komentáře kódu identifikují metody, které odpovídají různým pravidlům, která se vztahují k <xref:System.Object.Equals%2A> a <xref:System.IComparable> rozhraní.

 [!code-csharp[FxCop.Design.IComparable#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.IComparable/cs/FxCop.Design.IComparable.cs#1)]

## <a name="example"></a>Příklad
 Následující aplikace testuje chování výše <xref:System.IComparable> uvedené implementace.

 [!code-csharp[FxCop.Design.TestIComparable#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.TestIComparable/cs/FxCop.Design.TestIComparable.cs#1)]

## <a name="see-also"></a>Viz také
 <xref:System.IComparable?displayProperty=fullName> <xref:System.Object.Equals%2A?displayProperty=fullName>
 [Operátory rovnosti](https://msdn.microsoft.com/library/bc496a91-fefb-4ce0-ab4c-61f09964119a)
