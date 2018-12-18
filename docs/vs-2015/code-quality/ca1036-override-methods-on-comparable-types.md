---
title: 'CA1036: Přepište metody srovnatelných typů | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- CA1036
- OverrideMethodsOnComparableTypes
helpviewer_keywords:
- OverrideMethodsOnComparableTypes
- CA1036
ms.assetid: 2329f844-4cb8-426d-bee2-cd065d1346d0
caps.latest.revision: 23
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 67fa52a674b9e3d77d7e3eed7493bf28c1b2514d
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49948765"
---
# <a name="ca1036-override-methods-on-comparable-types"></a>CA1036: Přepište metody srovnatelných typů
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|OverrideMethodsOnComparableTypes|
|CheckId|CA1036|
|Kategorie|Microsoft.Design|
|Narušující změna|Nenarušující|

## <a name="cause"></a>příčina
 Veřejný nebo chráněný typ implementuje <xref:System.IComparable?displayProperty=fullName> rozhraní, nedojde k přepsání <xref:System.Object.Equals%2A?displayProperty=fullName> nebo nepřetěžuje specifické pro jazyk operátor rovnosti, nerovnosti, menší nebo větší. Pravidlo nevytváří sestavu porušení, pokud typ dědí pouze implementace rozhraní.

## <a name="rule-description"></a>Popis pravidla
 Typy, které definují vlastní řazení implementovat <xref:System.IComparable> rozhraní. <xref:System.IComparable.CompareTo%2A> Metoda vrací celočíselnou hodnotu, která určuje správné pořadí řazení pro dvě instance daného typu. Toto pravidlo určuje typy, které nastavení pořadí řazení. z toho vyplývá, že běžný význam rovnosti, nerovnosti, menší než a větší než se nedá použít. Když zadáte implementace <xref:System.IComparable>, je obvykle třeba také přepsat <xref:System.Object.Equals%2A> tak, že vrátí hodnoty, které jsou konzistentní s <xref:System.IComparable.CompareTo%2A>. Pokud přepíšete <xref:System.Object.Equals%2A> a psaní kódu v jazyce, který podporuje přetížení operátoru, měli byste také poskytnout operátory, které jsou konzistentní s <xref:System.Object.Equals%2A>.

## <a name="how-to-fix-violations"></a>Jak vyřešit porušení
 Chcete-li opravit porušení tohoto pravidla, přepište <xref:System.Object.Equals%2A>. Pokud svůj oblíbený programovací jazyk podporuje přetížení operátoru, zadejte následující operátory:

- op_Equality

- op_inequality –

- op_LessThan

- op_GreaterThan

  V jazyce C#, tokeny, které se používají k vyjádření tyto operátory jsou následující: ==,! =, \<, a >.

## <a name="when-to-suppress-warnings"></a>Kdy potlačit upozornění
 Je bezpečné potlačit upozornění tohoto pravidla při porušení zásad je způsobeno chybějící operátory a svůj oblíbený programovací jazyk nepodporuje přetěžování, stejně jako v případě v jazyce Visual Basic .NET. Je také bezpečně potlačení upozornění pro toto pravidlo, když se aktivuje na operátory rovnosti jiné než op_Equality Pokud zjistíte, že implementace operátorů nemá smysl v kontextu vašich aplikací. Nicméně byste měli vždy přes op_Equality a == – operátor Pokud přepíšete metodu Object.Equals.

## <a name="example"></a>Příklad
 Následující příklad obsahuje typ, který implementuje správně <xref:System.IComparable>. Kód poznámky určují metody, které splňují různá pravidla, které se týkají <xref:System.Object.Equals%2A> a <xref:System.IComparable> rozhraní.

 [!code-csharp[FxCop.Design.IComparable#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.IComparable/cs/FxCop.Design.IComparable.cs#1)]

## <a name="example"></a>Příklad
 Následující aplikace testuje chování <xref:System.IComparable> implementace, které se zobrazilo dříve.

 [!code-csharp[FxCop.Design.TestIComparable#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.TestIComparable/cs/FxCop.Design.TestIComparable.cs#1)]

## <a name="see-also"></a>Viz také
 <xref:System.IComparable?displayProperty=fullName><xref:System.Object.Equals%2A?displayProperty=fullName>
 [Operátory rovnosti](http://msdn.microsoft.com/library/bc496a91-fefb-4ce0-ab4c-61f09964119a)



