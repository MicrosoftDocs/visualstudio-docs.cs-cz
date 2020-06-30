---
title: 'CA1013: přetížený operátor Equals při přetížení sčítání a odečítání | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- OverrideOperatorEqualsOnOverridingAddAndSubtract
- OverrideOperatorEqualsOnOverloadingAddAndSubtract
- CA1013
- OverloadOperatorEqualsOnOverloadingAddAndSubtract
helpviewer_keywords:
- OverrideOperatorEqualsOnOverloadingAddAndSubtract
- OverrideOperatorEqualsOnOverridingAddAndSubtract
- CA1013
- OverloadOperatorEqualsOnOverloadingAddAndSubtract
ms.assetid: 5bd28d68-c179-49ff-af47-5250b8b18a10
caps.latest.revision: 24
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 2304b78073b806dfc4aec9686f061d946b379ded
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/30/2020
ms.locfileid: "85545415"
---
# <a name="ca1013-overload-operator-equals-on-overloading-add-and-subtract"></a>CA1013: Přetižte operátor rovnosti společně s přetížením operátorů sčítání a odečítání
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Položka|Hodnota|
|-|-|
|TypeName|OverloadOperatorEqualsOnOverloadingAddAndSubtract|
|CheckId|CA1013|
|Kategorie|Microsoft. Design|
|Narušující změna|Nenarušující|

## <a name="cause"></a>Příčina
 Veřejný nebo chráněný typ implementuje operátory sčítání a odčítání, aniž by implementoval operátor rovnosti.

## <a name="rule-description"></a>Popis pravidla
 V případě, že instance typu lze kombinovat pomocí operací, jako je sčítání a odčítání, byste měli téměř vždy definovat rovnost, která se vrátí `true` pro všechny dvě instance, které mají stejné hodnoty prvků.

 Nelze použít výchozí operátor rovnosti v přetížené implementaci operátoru rovnosti. Uděláte to tak, že dojde k přetečení zásobníku. K implementaci operátoru rovnosti použijte metodu Object. Equals v implementaci. Prohlédněte si následující příklad.

```vb
If (Object.ReferenceEquals(left, Nothing)) Then
    Return Object.ReferenceEquals(right, Nothing)
Else
    Return left.Equals(right)
End If
```

```csharp
if (Object.ReferenceEquals(left, null))
    return Object.ReferenceEquals(right, null);
return left.Equals(right);
```

## <a name="how-to-fix-violations"></a>Jak vyřešit porušení
 Chcete-li opravit porušení tohoto pravidla, implementujte operátor rovnosti tak, aby byl matematicky konzistentní s operátory sčítání a odčítání.

## <a name="when-to-suppress-warnings"></a>Kdy potlačit upozornění
 V případě, že výchozí implementace operátoru rovnosti poskytuje správné chování pro typ, je bezpečné potlačit upozornění od tohoto pravidla.

## <a name="example"></a>Příklad
 Následující příklad definuje typ ( `BadAddableType` ), který porušuje toto pravidlo. Tento typ by měl implementovat operátor rovnosti, aby všechny dvě instance, které mají stejné hodnoty polí, byly testovány `true` pro rovnost. Typ `GoodAddableType` zobrazuje opravenou implementaci. Všimněte si, že tento typ také implementuje operátor nerovnosti a přepsání <xref:System.Object.Equals%2A> pro splnění dalších pravidel. Bude implementována i kompletní implementace <xref:System.Object.GetHashCode%2A> .

 [!code-csharp[FxCop.Design.AddAndSubtract#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.AddAndSubtract/cs/FxCop.Design.AddAndSubtract.cs#1)]

## <a name="example"></a>Příklad
 Následující příklad testuje rovnost pomocí instancí typů, které byly dříve definovány v tomto tématu, k ilustraci výchozího a správného chování operátoru rovnosti.

 [!code-csharp[FxCop.Design.TestAddAndSubtract#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.TestAddAndSubtract/cs/FxCop.Design.TestAddAndSubtract.cs#1)]

 Tento příklad vytvoří následující výstup.

 **Chybný typ: {2,2} {2,2} jsou stejné? Žádný** 
 **dobrý typ: {3,3} {3,3} je stejný? Ano** 
 **dobrý typ: {3,3} {3,3} jsou = =?   Ano** 
 **špatný typ: {2,2} {9,9} je stejný? Neexistuje** 
 **dobrý typ: {3,3} {9,9} = =?   Ne**
## <a name="see-also"></a>Viz také
 [Operátory rovnosti](https://msdn.microsoft.com/library/bc496a91-fefb-4ce0-ab4c-61f09964119a)
