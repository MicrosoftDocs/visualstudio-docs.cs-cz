---
title: 'CA2225: přetížení operátoru mají pojmenované alternativy | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- OperatorOverloadsHaveNamedAlternates
- CA2225
helpviewer_keywords:
- OperatorOverloadsHaveNamedAlternates
- CA2225
ms.assetid: af8f7ab1-63ad-4861-afb9-b7a7a2be15e1
caps.latest.revision: 22
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 212abc1fa5e2debfaf7ca81d82c8d94e9ddb0879
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72658877"
---
# <a name="ca2225-operator-overloads-have-named-alternates"></a>CA2225: Přetížení operátoru mají pojmenované alternativy
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|OperatorOverloadsHaveNamedAlternates|
|CheckId|CA2225|
|Kategorie|Microsoft. Usage|
|Narušující změna|Bez přerušení|

## <a name="cause"></a>příčina
 Bylo zjištěno přetížení operátoru a alternativní metoda s očekávaným názvem nebyla nalezena.

## <a name="rule-description"></a>Popis pravidla
 Přetížení operátoru umožňuje použít symboly k vyjádření výpočtů pro typ. Například typ, který přetěžuje symbol plus (+) pro sčítání, by měl obvykle alternativní člen s názvem add. Pojmenovaný alternativní člen poskytuje přístup ke stejným funkcím jako operátor a je k dispozici pro vývojáře, kteří programují v jazycích, které nepodporují přetížené operátory.

 Toto pravidlo prověřuje operátory uvedené v následující tabulce.

|C#|Visual Basic|C++|Alternativní název|
|---------|------------------|-----------|--------------------|
|+ (binární)|+|+ (binární)|Přidejte|
|+=|+=|+=|Přidejte|
|&|Ani|&|BitwiseAnd|
|&=|A =|&=|BitwiseAnd|
|&#124;|Nebo|&#124;|Bitový operátor|
|&#124;=|Nebo =|&#124;=|Bitový operátor|
|--|Není k dispozici|--|Snížení|
|/|/|/|Rozdělovací|
|/=|/=|/=|Rozdělovací|
|==|=|==|Rovná|
|^|XOR|^|XOR|
|^=|XOR =|^=|XOR|
|>|>|>|Porovnán|
|>=|>=|>=|Porovnán|
|++|Není k dispozici|++|Zvětš|
|<>|!=|Rovná|
|<<|<<|<<|LeftShift|
|<<=|<<=|<<=|LeftShift|
|<|<|<|Porovnán|
|<=|<=|\<=|Porovnán|
|&&|Není k dispozici|&&|LogicalAnd|
|&#124;&#124;|Není k dispozici|&#124;&#124;|Logický operátor|
|!|Není k dispozici|!|LogicalNot|
|%|Mod|%|Střední nebo zbytek|
|%=|Není k dispozici|%=|Mod|
|* (binární)|*|*|Hodnotou|
|*=|Není k dispozici|*=|Hodnotou|
|~|Mění|~|OnesComplement|
|>>|>>|>>|RightShift|
=|Není k dispozici|>>=|RightShift|
|-(binární)|-(binární)|-(binární)|Odečten|
|-=|Není k dispozici|-=|Odečten|
|true|IsTrue|Není k dispozici|True (vlastnost)|
|– (Unární)|Není k dispozici|-|Negate|
|+ (Unární)|Není k dispozici|+|i|
|false|IsFalse|False|True (vlastnost)|

 N/A = = nemůže být přetížený ve vybraném jazyce.

 Pravidlo také kontroluje implicitní a explicitní operátory přetypování v typu (`SomeType`) kontrolou metod pojmenovaných `ToSomeType` a `FromSomeType`.

 V C#, je-li binární operátor přetížen, je také implicitně přetížen odpovídající operátor přiřazení, je-li nějaký.

## <a name="how-to-fix-violations"></a>Jak vyřešit porušení
 Chcete-li opravit porušení tohoto pravidla, implementujte alternativní metodu pro operátor; pojmenujte ji pomocí doporučeného alternativního názvu.

## <a name="when-to-suppress-warnings"></a>Kdy potlačit upozornění
 Potlačit upozornění z tohoto pravidla, Pokud implementujete sdílenou knihovnu. Aplikace mohou ignorovat upozornění od tohoto pravidla.

## <a name="example"></a>Příklad
 Následující příklad definuje strukturu, která porušuje toto pravidlo. Chcete-li tento příklad opravit, přidejte do struktury metodu public `Add(int x, int y)`.

 [!code-csharp[FxCop.Usage.OperatorOverloadsHaveNamedAlternates#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.OperatorOverloadsHaveNamedAlternates/cs/FxCop.Usage.OperatorOverloadsHaveNamedAlternates.cs#1)]

## <a name="related-rules"></a>Související pravidla
 [CA1046: Nepřetěžujte operátory rovnosti na odkazových typech](../code-quality/ca1046-do-not-overload-operator-equals-on-reference-types.md)

 [CA2226: Operátory by měly mít symetrické přetížení](../code-quality/ca2226-operators-should-have-symmetrical-overloads.md)

 [CA2224: Přepište Equals při přetížení operátoru rovnosti](../code-quality/ca2224-override-equals-on-overloading-operator-equals.md)

 [CA2218: Přepište GetHashCode při přepsání Equals](../code-quality/ca2218-override-gethashcode-on-overriding-equals.md)

 [CA2231: Přetižte operátor equals při přepsání ValueType.Equals](../code-quality/ca2231-overload-operator-equals-on-overriding-valuetype-equals.md)
