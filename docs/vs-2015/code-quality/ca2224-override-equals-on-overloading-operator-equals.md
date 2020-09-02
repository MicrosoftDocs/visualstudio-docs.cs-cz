---
title: 'CA2224: přepište Equals při přetížení operátoru rovnosti | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2224
- OverrideEqualsOnOverloadingOperatorEquals
- OverrideEqualsOnOverridingOperatorEquals
helpviewer_keywords:
- OverrideEqualsOnOverloadingOperatorEquals
- CA2224
ms.assetid: 7312afd9-84ba-417f-923e-7a159b53bf70
caps.latest.revision: 17
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 39272790b6ef366c64d45e0aea238606d0b62bf4
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "85538633"
---
# <a name="ca2224-override-equals-on-overloading-operator-equals"></a>CA2224: Přepište Equals při přetížení operátoru rovnosti
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Položka|Hodnota|
|-|-|
|TypeName|OverrideEqualsOnOverloadingOperatorEquals|
|CheckId|CA2224|
|Kategorie|Microsoft. Usage|
|Narušující změna|Bez přerušení|

## <a name="cause"></a>Příčina
 Veřejný typ implementuje operátor rovnosti, ale nepřepisuje <xref:System.Object.Equals%2A?displayProperty=fullName> .

## <a name="rule-description"></a>Popis pravidla
 Operátor rovnosti má být syntakticky pohodlný způsob, jak získat přístup k funkcím <xref:System.Object.Equals%2A> metody. Při implementaci operátoru rovnosti musí být jeho logika shodná s vlastností <xref:System.Object.Equals%2A> .

 Kompilátor jazyka C# vydá upozornění, je-li kód v rozporu s tímto pravidlem.

## <a name="how-to-fix-violations"></a>Jak vyřešit porušení
 Chcete-li opravit porušení tohoto pravidla, měli byste buď odebrat implementaci operátoru rovnosti, nebo přepsat <xref:System.Object.Equals%2A> a mít dvě metody vracet stejné hodnoty. Pokud operátor rovnosti nezavádí nekonzistentní chování, můžete opravit porušení poskytnutím implementace <xref:System.Object.Equals%2A> , která volá <xref:System.Object.Equals%2A> metodu v základní třídě.

## <a name="when-to-suppress-warnings"></a>Kdy potlačit upozornění
 Je bezpečné potlačit upozornění z tohoto pravidla, pokud operátor rovnosti vrací stejnou hodnotu jako zděděná implementace <xref:System.Object.Equals%2A> . Oddíl příkladu obsahuje typ, který by mohl bezpečně potlačit upozornění od tohoto pravidla.

## <a name="examples-of-inconsistent-equality-definitions"></a>Příklady nekonzistentních definic rovnosti

### <a name="description"></a>Popis
 Následující příklad ukazuje typ s nekonzistentními definicemi rovnosti. `BadPoint` změní význam rovnosti tím, že poskytuje vlastní implementaci operátoru rovnosti, ale nepřepisuje <xref:System.Object.Equals%2A> tak, aby se choval stejně.

### <a name="code"></a>Kód
 [!code-csharp[FxCop.Usage.OperatorEqualsRequiresEquals#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.OperatorEqualsRequiresEquals/cs/FxCop.Usage.OperatorEqualsRequiresEquals.cs#1)]

## <a name="example"></a>Příklad
 Následující kód testuje chování `BadPoint` .

 [!code-csharp[FxCop.Usage.TestOperatorEqualsRequiresEquals#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.TestOperatorEqualsRequiresEquals/cs/FxCop.Usage.TestOperatorEqualsRequiresEquals.cs#1)]

 Tento příklad vytvoří následující výstup.

 **a = ([0] 1, 1) a b = ([1] 2, 2) jsou stejné? Ne** 
 **a = = b? Žádné** 
 **a1 a a jsou stejné? Ano** 
 **a1 = = a? Ano** 
 **b a bcopy jsou stejné? Ne** 
 **b = = bcopy? Ano**
## <a name="example"></a>Příklad
 Následující příklad ukazuje typ, který je technicky v rozporu s tímto pravidlem, ale nepracuje nekonzistentním způsobem.

 [!code-csharp[FxCop.Usage.ValueTypeEquals#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.ValueTypeEquals/cs/FxCop.Usage.ValueTypeEquals.cs#1)]

## <a name="example"></a>Příklad
 Následující kód testuje chování `GoodPoint` .

 [!code-csharp[FxCop.Usage.TestValueTypeEquals#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.TestValueTypeEquals/cs/FxCop.Usage.TestValueTypeEquals.cs#1)]

 Tento příklad vytvoří následující výstup.

 **a = (1, 1) a b = (2, 2) jsou stejné? Ne** 
 **a = = b? Žádné** 
 **a1 a a jsou stejné? Ano** 
 **a1 = = a? Ano** 
 **b a bcopy jsou stejné? Ano** 
 **b = = bcopy? Ano**
## <a name="class-example"></a>Příklad třídy

### <a name="description"></a>Popis
 Následující příklad ukazuje třídu (odkazový typ), která toto pravidlo porušuje.

### <a name="code"></a>Kód
 [!code-csharp[FxCop.Usage.OverrideEqualsClassViolation#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.OverrideEqualsClassViolation/cs/FxCop.Usage.OverrideEqualsClassViolation.cs#1)]

## <a name="example"></a>Příklad
 Následující příklad opravuje porušení pomocí přepsání <xref:System.Object.Equals%2A?displayProperty=fullName> .

 [!code-csharp[FxCop.Usage.OverrideEqualsClassFixed#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.OverrideEqualsClassFixed/cs/FxCop.Usage.OverrideEqualsClassFixed.cs#1)]

## <a name="structure-example"></a>Příklad struktury

### <a name="description"></a>Popis
 Následující příklad ukazuje strukturu (typ hodnoty), která toto pravidlo porušuje.

### <a name="code"></a>Kód
 [!code-csharp[FxCop.Usage.OverrideEqualsStructViolation#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.OverrideEqualsStructViolation/cs/FxCop.Usage.OverrideEqualsStructViolation.cs#1)]

## <a name="example"></a>Příklad
 Následující příklad opravuje porušení pomocí přepsání <xref:System.ValueType.Equals%2A?displayProperty=fullName> .

 [!code-csharp[FxCop.Usage.OverrideEqualsStructFixed#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.OverrideEqualsStructFixed/cs/FxCop.Usage.OverrideEqualsStructFixed.cs#1)]

## <a name="related-rules"></a>Související pravidla
 [CA1046: Nepřetěžujte operátory rovnosti u odkazových typů](../code-quality/ca1046-do-not-overload-operator-equals-on-reference-types.md)

 [CA2225: Přetížení operátoru mají pojmenované alternativy](../code-quality/ca2225-operator-overloads-have-named-alternates.md)

 [CA2226: Operátory by měly mít symetrická přetížení](../code-quality/ca2226-operators-should-have-symmetrical-overloads.md)

 [CA2218: Přepište GetHashCode při přepsání Equals](../code-quality/ca2218-override-gethashcode-on-overriding-equals.md)

 [CA2231: Přetižte operátor rovnosti při přetížení ValueType.Equals](../code-quality/ca2231-overload-operator-equals-on-overriding-valuetype-equals.md)
