---
title: 'CA1013: Přetižte operátor rovnosti při přetížení sčítání a odečítání | Dokumentace Microsoftu'
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
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 277f0c880ba9a3043744cf1c558ea8487062bd12
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49921987"
---
# <a name="ca1013-overload-operator-equals-on-overloading-add-and-subtract"></a>CA1013: Přetižte operátor rovnosti společně s přetížením operátorů sčítání a odečítání
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|OverloadOperatorEqualsOnOverloadingAddAndSubtract|
|CheckId|CA1013|
|Kategorie|Microsoft.Design|
|Narušující změna|Nenarušující|

## <a name="cause"></a>příčina
 Veřejný nebo chráněný typ implementuje operátory sčítání a odčítání, aniž by implementoval operátor rovnosti.

## <a name="rule-description"></a>Popis pravidla
 Když instance typu je možné kombinovat s použitím operace, jako je sčítání a odčítání, téměř vždy měli definovat rovnosti vrátil `true` pro jakékoli dvě instance, které mají stejný základní hodnoty.

 V implementaci přetížení operátoru rovnosti nelze použít výchozí operátor rovnosti. To způsobí přetečení zásobníku. K implementaci operátor rovnosti, použijte metodu Object.Equals v implementaci. Podívejte se na téma v následujícím příkladu.

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
 Chcete-li opravit porušení tohoto pravidla, implementujte operátor rovnosti, tak, aby se matematicky konzistentní s operátory sčítání a odčítání.

## <a name="when-to-suppress-warnings"></a>Kdy potlačit upozornění
 Je bezpečné potlačit upozornění tohoto pravidla, pokud výchozí implementace operátoru rovnosti pro typ poskytuje správné chování.

## <a name="example"></a>Příklad
 Následující příklad definuje typ (`BadAddableType`), který porušuje tato pravidla. Tento typ by měly implementovat operátor rovnosti, chcete-li jakékoli dvě instance, které mají stejné hodnoty pole testování `true` rovnosti. Typ `GoodAddableType` ukazuje opravený implementaci. Mějte na paměti, že tento typ také implementuje operátor nerovnosti a přepíše <xref:System.Object.Equals%2A> splnit další pravidla. Úplnou implementaci byste implementovali také <xref:System.Object.GetHashCode%2A>.

 [!code-csharp[FxCop.Design.AddAndSubtract#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.AddAndSubtract/cs/FxCop.Design.AddAndSubtract.cs#1)]

## <a name="example"></a>Příklad
 Následující příklad testuje rovnost pomocí instance typů, které byly dříve definovány v tomto tématu pro ilustraci výchozí a správné chování pro operátor rovnosti.

 [!code-csharp[FxCop.Design.TestAddAndSubtract#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.TestAddAndSubtract/cs/FxCop.Design.TestAddAndSubtract.cs#1)]

 Tento příklad vytvoří následující výstup.

 **Chybný typ: {2,2} {2,2} jsou stejné? Ne**
**dobré typ: {3,3} {3,3} jsou stejné? Ano**
**dobré typ: {3,3} {3,3} jsou ==?   Ano**
**chybný typ: {2,2} {9,9} jsou stejné? Ne**
**dobré typ: {3,3} {9,9} jsou ==?   Ne**
## <a name="see-also"></a>Viz také
 [Operátory rovnosti](http://msdn.microsoft.com/library/bc496a91-fefb-4ce0-ab4c-61f09964119a)



