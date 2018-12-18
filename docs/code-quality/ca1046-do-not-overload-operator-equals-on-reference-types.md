---
title: 'CA1046: Nepřetěžujte operátory rovnosti na odkazových typech'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- DoNotOverloadOperatorEqualsOnReferenceTypes
- CA1046
helpviewer_keywords:
- CA1046
- DoNotOverloadOperatorEqualsOnReferenceTypes
ms.assetid: c1dfbfe3-63f9-4005-a81a-890427b77e79
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 3f0aeb519fdc22d3fb68812d24979c7aa6c23f85
ms.sourcegitcommit: 568bb0b944d16cfe1af624879fa3d3594d020187
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/13/2018
ms.locfileid: "45551700"
---
# <a name="ca1046-do-not-overload-operator-equals-on-reference-types"></a>CA1046: Nepřetěžujte operátory rovnosti na odkazových typech

|||
|-|-|
|TypeName|DoNotOverloadOperatorEqualsOnReferenceTypes|
|CheckId|CA1046|
|Kategorie|Microsoft.Design|
|Narušující změna|Narušující|

## <a name="cause"></a>příčina
 Odkaz na veřejný nebo vnořený veřejný typ přetížení operátoru rovnosti.

## <a name="rule-description"></a>Popis pravidla
 U referenčních typů je výchozí implementace operátoru rovnosti téměř vždy správná. Ve výchozím nastavení jsou dva odkazy rovny, pouze pokud ukazují na stejný objekt.

## <a name="how-to-fix-violations"></a>Jak vyřešit porušení
 Chcete-li opravit porušení tohoto pravidla, odeberte implementace operátoru rovnosti.

## <a name="when-to-suppress-warnings"></a>Kdy potlačit upozornění
 Je bezpečné potlačit upozornění tohoto pravidla, pokud typ odkazu se chová jako předdefinovaného hodnotového typu. Pokud je smysluplná provedete sčítání a odčítání na instance daného typu, je nejspíš správná implementace operátoru rovnosti a potlačit porušení zásady.

## <a name="example"></a>Příklad
 Následující příklad ukazuje výchozí chování při porovnávání dva odkazy.

 [!code-csharp[FxCop.Design.RefTypesNoEqualityOp#1](../code-quality/codesnippet/CSharp/ca1046-do-not-overload-operator-equals-on-reference-types_1.cs)]

## <a name="example"></a>Příklad

Následující aplikace porovnává některé odkazy.

[!code-csharp[FxCop.Design.TestRefTypesNoEqualityOp#1](../code-quality/codesnippet/CSharp/ca1046-do-not-overload-operator-equals-on-reference-types_2.cs)]

Tento příklad vytvoří následující výstup:

```txt
a = new (2,2) and b = new (2,2) are equal? No
c and a are equal? Yes
b and a are == ? No
c and a are == ? Yes
```

## <a name="related-rules"></a>Související pravidla

[CA1013: Přetižte operátor rovnosti společně s přetížením operátorů sčítání a odečítání](../code-quality/ca1013-overload-operator-equals-on-overloading-add-and-subtract.md)

## <a name="see-also"></a>Viz také:

- <xref:System.Object.Equals%2A?displayProperty=fullName>
- [Operátory rovnosti](/dotnet/standard/design-guidelines/equality-operators)