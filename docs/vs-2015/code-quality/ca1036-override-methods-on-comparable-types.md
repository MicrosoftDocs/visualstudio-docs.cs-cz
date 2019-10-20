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
ms.openlocfilehash: 779e6258f9c5be256a7973a5d917045507fc82e6
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72661827"
---
# <a name="ca1036-override-methods-on-comparable-types"></a>CA1036: Přepište metody srovnatelných typů
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|OverrideMethodsOnComparableTypes|
|CheckId|CA1036|
|Kategorie|Microsoft. Design|
|Narušující změna|Nenarušující|

## <a name="cause"></a>příčina
 Veřejný nebo chráněný typ implementuje rozhraní <xref:System.IComparable?displayProperty=fullName> a nepřepisuje <xref:System.Object.Equals%2A?displayProperty=fullName> nebo neimplementuje operátor specifický pro určitý jazyk pro rovnost, nerovnost, menší nebo větší než. Pravidlo neoznamuje porušení, pokud typ dědí pouze implementaci rozhraní.

## <a name="rule-description"></a>Popis pravidla
 Typy, které definují vlastní pořadí řazení implementují rozhraní <xref:System.IComparable>. Metoda <xref:System.IComparable.CompareTo%2A> vrací celočíselnou hodnotu, která určuje správné pořadí řazení pro dvě instance typu. Toto pravidlo identifikuje typy, které nastaví pořadí řazení; To znamená, že neplatí běžný význam rovnosti, nerovnosti, menší než a větší než. Pokud zadáte implementaci <xref:System.IComparable>, je obvykle nutné také přepsat <xref:System.Object.Equals%2A>, aby vracely hodnoty, které jsou konzistentní s <xref:System.IComparable.CompareTo%2A>. Pokud přepíšete <xref:System.Object.Equals%2A> a vytváříte kód v jazyce, který podporuje přetížení operátoru, měli byste také zadat operátory, které jsou konzistentní s <xref:System.Object.Equals%2A>.

## <a name="how-to-fix-violations"></a>Jak vyřešit porušení
 Chcete-li opravit porušení tohoto pravidla, přepište <xref:System.Object.Equals%2A>. Pokud váš programovací jazyk podporuje přetížení operátora, zadejte následující operátory:

- op_Equality

- op_Inequality

- op_LessThan

- op_GreaterThan

  V C#nástroji tokeny, které se používají k reprezentování těchto operátorů, jsou následující: = =,! =, \< a >.

## <a name="when-to-suppress-warnings"></a>Kdy potlačit upozornění
 Je bezpečné potlačit upozornění z tohoto pravidla, pokud je porušení způsobeno chybějícími operátory a váš programovací jazyk nepodporuje přetížení operátoru, stejně jako v případě Visual Basic .NET. Je také bezpečné potlačit upozornění pro z tohoto pravidla, je-li aktivováno u operátorů rovnosti jiných než op_Equality, pokud určíte, že implementace operátorů nedává smysl v kontextu vaší aplikace. Nicméně byste měli vždy převádět op_Equality a operátor = =, pokud přepíšete Object. Equals.

## <a name="example"></a>Příklad
 Následující příklad obsahuje typ, který správně implementuje <xref:System.IComparable>. Komentáře kódu identifikují metody, které odpovídají různým pravidlům, která souvisí s <xref:System.Object.Equals%2A> a rozhraním <xref:System.IComparable>.

 [!code-csharp[FxCop.Design.IComparable#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.IComparable/cs/FxCop.Design.IComparable.cs#1)]

## <a name="example"></a>Příklad
 Následující aplikace testuje chování <xref:System.IComparable> implementace, která se zobrazila dříve.

 [!code-csharp[FxCop.Design.TestIComparable#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.TestIComparable/cs/FxCop.Design.TestIComparable.cs#1)]

## <a name="see-also"></a>Viz také
 <xref:System.IComparable?displayProperty=fullName><xref:System.Object.Equals%2A?displayProperty=fullName>
 [Operátory rovnosti](https://msdn.microsoft.com/library/bc496a91-fefb-4ce0-ab4c-61f09964119a)
