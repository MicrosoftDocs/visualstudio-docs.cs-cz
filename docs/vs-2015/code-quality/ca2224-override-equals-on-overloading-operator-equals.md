---
title: 'CA2224: Přepište equals při přetížení operátoru rovnosti | Dokumentace Microsoftu'
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
- CA2224
- OverrideEqualsOnOverloadingOperatorEquals
- OverrideEqualsOnOverridingOperatorEquals
helpviewer_keywords:
- OverrideEqualsOnOverloadingOperatorEquals
- CA2224
ms.assetid: 7312afd9-84ba-417f-923e-7a159b53bf70
caps.latest.revision: 17
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 66f4b4bcc7c2c1d359f5d8fa91227fb51a27adc4
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49815231"
---
# <a name="ca2224-override-equals-on-overloading-operator-equals"></a>CA2224: Přepište Equals při přetížení operátoru rovnosti
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|OverrideEqualsOnOverloadingOperatorEquals|
|CheckId|CA2224|
|Kategorie|Microsoft.Usage|
|Narušující změna|Pevné|

## <a name="cause"></a>příčina
 Veřejný typ implementuje operátor rovnosti, ale nepřepisuje <xref:System.Object.Equals%2A?displayProperty=fullName>.

## <a name="rule-description"></a>Popis pravidla
 Operátor rovnosti má být syntakticky pohodlný způsob, jak přistupovat k funkcím <xref:System.Object.Equals%2A> metody. Pokud se rozhodnete implementovat operátor rovnosti, musí být shodná s svou logikou <xref:System.Object.Equals%2A>.

 Kompilátor jazyka C# vyvolá upozornění, pokud váš kód poruší toto pravidlo.

## <a name="how-to-fix-violations"></a>Jak vyřešit porušení
 Chcete-li opravit porušení tohoto pravidla, buď odstranit implementace operátoru rovnosti, nebo přepsat <xref:System.Object.Equals%2A> a mít dvě metody vrací stejné hodnoty. Pokud operátor rovnosti nezavádí nekonzistentní chování, porušení zásad můžete vyřešit tím, že poskytuje implementace <xref:System.Object.Equals%2A> , která volá <xref:System.Object.Equals%2A> metodu v základní třídě.

## <a name="when-to-suppress-warnings"></a>Kdy potlačit upozornění
 Je bezpečné potlačit upozornění tohoto pravidla, je-li operátor rovnosti vrací stejnou hodnotu jako zděděná implementace metody <xref:System.Object.Equals%2A>. Vzorový oddíl obsahuje typ, který může bezpečně potlačit upozornění tohoto pravidla.

## <a name="examples-of-inconsistent-equality-definitions"></a>Příklady definice nekonzistentní rovnosti

### <a name="description"></a>Popis
 Následující příklad ukazuje typ s nekonzistentní definice rovnosti. `BadPoint` Změní význam rovnosti poskytnutím vlastní implementace operátoru rovnosti, ale nepřepisuje <xref:System.Object.Equals%2A> tak, aby se chová stejně.

### <a name="code"></a>Kód
 [!code-csharp[FxCop.Usage.OperatorEqualsRequiresEquals#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.OperatorEqualsRequiresEquals/cs/FxCop.Usage.OperatorEqualsRequiresEquals.cs#1)]

## <a name="example"></a>Příklad
 Následující kód testy chování `BadPoint`.

 [!code-csharp[FxCop.Usage.TestOperatorEqualsRequiresEquals#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.TestOperatorEqualsRequiresEquals/cs/FxCop.Usage.TestOperatorEqualsRequiresEquals.cs#1)]

 Tento příklad vytvoří následující výstup.

 **= ([0] 1,1) a, b = ([1] 2,2) jsou stejné? Ne**
 **== b? Ne**
**a1 a a jsou stejná? Ano**
**a1 ==? Ano**
**b a bcopy jsou stejné? Ne**
**b == bcopy? Ano**
## <a name="example"></a>Příklad
 Následující příklad ukazuje typ, který technicky poruší toto pravidlo, ale nechová nekonzistentní způsobem.

 [!code-csharp[FxCop.Usage.ValueTypeEquals#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.ValueTypeEquals/cs/FxCop.Usage.ValueTypeEquals.cs#1)]

## <a name="example"></a>Příklad
 Následující kód testy chování `GoodPoint`.

 [!code-csharp[FxCop.Usage.TestValueTypeEquals#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.TestValueTypeEquals/cs/FxCop.Usage.TestValueTypeEquals.cs#1)]

 Tento příklad vytvoří následující výstup.

 **= (1,1) a, b = (2,2) jsou stejné? Ne**
 **== b? Ne**
**a1 a a jsou stejná? Ano**
**a1 ==? Ano**
**b a bcopy jsou stejné? Ano**
**b == bcopy? Ano**
## <a name="class-example"></a>Příklad třídy

### <a name="description"></a>Popis
 Následující příklad ukazuje třídu (odkaz), který porušuje tato pravidla.

### <a name="code"></a>Kód
 [!code-csharp[FxCop.Usage.OverrideEqualsClassViolation#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.OverrideEqualsClassViolation/cs/FxCop.Usage.OverrideEqualsClassViolation.cs#1)]

## <a name="example"></a>Příklad
 V následujícím příkladu řeší porušení zásady tak, že přepíšete <xref:System.Object.Equals%2A?displayProperty=fullName>.

 [!code-csharp[FxCop.Usage.OverrideEqualsClassFixed#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.OverrideEqualsClassFixed/cs/FxCop.Usage.OverrideEqualsClassFixed.cs#1)]

## <a name="structure-example"></a>Příklad struktury

### <a name="description"></a>Popis
 Následující příklad ukazuje strukturu (typ hodnoty), který porušuje tato pravidla.

### <a name="code"></a>Kód
 [!code-csharp[FxCop.Usage.OverrideEqualsStructViolation#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.OverrideEqualsStructViolation/cs/FxCop.Usage.OverrideEqualsStructViolation.cs#1)]

## <a name="example"></a>Příklad
 V následujícím příkladu řeší porušení zásady tak, že přepíšete <xref:System.ValueType.Equals%2A?displayProperty=fullName>.

 [!code-csharp[FxCop.Usage.OverrideEqualsStructFixed#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.OverrideEqualsStructFixed/cs/FxCop.Usage.OverrideEqualsStructFixed.cs#1)]

## <a name="related-rules"></a>Související pravidla
 [CA1046: Nepřetěžujte operátory rovnosti na odkazových typech](../code-quality/ca1046-do-not-overload-operator-equals-on-reference-types.md)

 [CA2225: Přetížení operátoru mají pojmenované alternativy](../code-quality/ca2225-operator-overloads-have-named-alternates.md)

 [CA2226: Operátory by měly mít symetrické přetížení](../code-quality/ca2226-operators-should-have-symmetrical-overloads.md)

 [CA2218: Přepište GetHashCode při přepsání Equals](../code-quality/ca2218-override-gethashcode-on-overriding-equals.md)

 [CA2231: Přetižte operátor equals při přepsání ValueType.Equals](../code-quality/ca2231-overload-operator-equals-on-overriding-valuetype-equals.md)



