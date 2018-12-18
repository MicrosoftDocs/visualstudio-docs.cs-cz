---
title: 'CA1036: Přepište metody srovnatelných typů'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1036
- OverrideMethodsOnComparableTypes
helpviewer_keywords:
- OverrideMethodsOnComparableTypes
- CA1036
ms.assetid: 2329f844-4cb8-426d-bee2-cd065d1346d0
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: ed69ba759d63ba27114bc097ac1fd9ccbe424edd
ms.sourcegitcommit: 568bb0b944d16cfe1af624879fa3d3594d020187
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/13/2018
ms.locfileid: "45547735"
---
# <a name="ca1036-override-methods-on-comparable-types"></a>CA1036: Přepište metody srovnatelných typů

|||
|-|-|
|TypeName|OverrideMethodsOnComparableTypes|
|CheckId|CA1036|
|Kategorie|Microsoft.Design|
|Narušující změna|Nenarušující|

## <a name="cause"></a>příčina
 Veřejný nebo chráněný typ implementuje <xref:System.IComparable?displayProperty=fullName> rozhraní, nedojde k přepsání <xref:System.Object.Equals%2A?displayProperty=fullName> nebo nepřetěžuje specifické pro jazyk operátor rovnosti, nerovnosti, menší – než, nebo větší-než. Pravidlo nevytváří sestavu porušení, pokud typ dědí pouze implementace rozhraní.

## <a name="rule-description"></a>Popis pravidla

Typy, které definují vlastní řazení implementovat <xref:System.IComparable> rozhraní. <xref:System.IComparable.CompareTo%2A> Metoda vrací celočíselnou hodnotu, která určuje správné pořadí řazení pro dvě instance daného typu. Toto pravidlo určuje typy, které nastaví pořadí řazení. Nastavení pořadí řazení vyplývá, že běžný význam rovnosti, nerovnosti, menší – než a větší-než nevztahují. Když zadáte implementace <xref:System.IComparable>, je obvykle třeba také přepsat <xref:System.Object.Equals%2A> tak, že vrátí hodnoty, které jsou konzistentní s <xref:System.IComparable.CompareTo%2A>. Pokud přepíšete <xref:System.Object.Equals%2A> a psaní kódu v jazyce, který podporuje přetížení operátoru, měli byste také poskytnout operátory, které jsou konzistentní s <xref:System.Object.Equals%2A>.

## <a name="how-to-fix-violations"></a>Jak vyřešit porušení

Chcete-li opravit porušení tohoto pravidla, přepište <xref:System.Object.Equals%2A>. Pokud svůj oblíbený programovací jazyk podporuje přetížení operátoru, zadejte následující operátory:

- op_Equality

- op_inequality –

- op_LessThan

- op_GreaterThan

Tokeny, které se používají k vyjádření tyto operátory v jazyce C#, jsou následující:

```csharp
==
!=
<
>
```

## <a name="when-to-suppress-warnings"></a>Kdy potlačit upozornění
 Je bezpečné potlačit upozornění pravidla CA1036 při porušení zásad je způsobena chybějícími operátory a svůj oblíbený programovací jazyk nepodporuje přetěžování, stejně jako v případě s jazykem Visual Basic. Je také bezpečně potlačení upozornění pro toto pravidlo, když se aktivuje na operátory rovnosti jiné než op_Equality Pokud zjistíte, že implementace operátorů nemá smysl v kontextu vašich aplikací. Nicméně byste měli vždy přes op_Equality a == – operátor Pokud přepíšete metodu Object.Equals.

## <a name="example"></a>Příklad
 Následující příklad obsahuje typ, který implementuje správně <xref:System.IComparable>. Kód poznámky určují metody, které splňují různá pravidla, které se týkají <xref:System.Object.Equals%2A> a <xref:System.IComparable> rozhraní.

 [!code-csharp[FxCop.Design.IComparable#1](../code-quality/codesnippet/CSharp/ca1036-override-methods-on-comparable-types_1.cs)]

## <a name="example"></a>Příklad
 Následující aplikace testuje chování <xref:System.IComparable> implementace, které se zobrazilo dříve.

 [!code-csharp[FxCop.Design.TestIComparable#1](../code-quality/codesnippet/CSharp/ca1036-override-methods-on-comparable-types_2.cs)]

## <a name="see-also"></a>Viz také:

- <xref:System.IComparable?displayProperty=fullName>
- <xref:System.Object.Equals%2A?displayProperty=fullName>
- [Operátory rovnosti](/dotnet/standard/design-guidelines/equality-operators)