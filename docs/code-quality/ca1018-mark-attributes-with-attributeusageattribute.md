---
title: 'CA1018: Označte atributy pomocí AttributeUsageAttribute'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA1018
- MarkAttributesWithAttributeUsage
helpviewer_keywords:
- CA1018
- MarkAttributesWithAttributeUsage
ms.assetid: 6ab70ec0-220f-4880-af31-45067703133c
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 133ee073398817c037af95e2009c5acc98e1e5a2
ms.sourcegitcommit: 034c503ae04e22cf840ccb9770bffd012e40fb2d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/14/2019
ms.locfileid: "72306130"
---
# <a name="ca1018-mark-attributes-with-attributeusageattribute"></a>CA1018: Označte atributy pomocí AttributeUsageAttribute

|||
|-|-|
|TypeName|MarkAttributesWithAttributeUsage|
|CheckId|CA1018|
|Category|Microsoft.Design|
|Zásadní změna|Narušující|

## <a name="cause"></a>Příčina
Atribut <xref:System.AttributeUsageAttribute?displayProperty=fullName> není ve vlastním atributu přítomen.

## <a name="rule-description"></a>Popis pravidla
Při definování vlastního atributu jej označte pomocí <xref:System.AttributeUsageAttribute> a určete, kde ve zdrojovém kódu lze použít vlastní atribut. Význam a zamýšlené použití atributu určuje jeho platné umístění v kódu. Například můžete definovat atribut, který identifikuje osobu, která je zodpovědná za údržbu a vylepšení každého typu v knihovně, a tato zodpovědnost je vždy přiřazena na úrovni typu. V takovém případě by měly kompilátory povolit atribut pro třídy, výčty a rozhraní, ale neměly by být povoleny v metodách, událostech nebo vlastnostech. Zásady a postupy organizace by měly určovat, jestli má být atribut povolený u sestavení.

Výčet <xref:System.AttributeTargets?displayProperty=fullName> definuje cíle, které lze zadat pro vlastní atribut. Pokud vynecháte <xref:System.AttributeUsageAttribute>, váš vlastní atribut bude platný pro všechny cíle, jak je definováno hodnotou `All` výčtu <xref:System.AttributeTargets>.

## <a name="how-to-fix-violations"></a>Jak opravit porušení
Chcete-li opravit porušení tohoto pravidla, zadejte cíle pro atribut pomocí <xref:System.AttributeUsageAttribute>. Prohlédněte si následující příklad.

## <a name="when-to-suppress-warnings"></a>Kdy potlačit upozornění
Místo vyloučení zprávy byste měli opravit porušení tohoto pravidla. I v případě, že atribut dědí <xref:System.AttributeUsageAttribute>, měl by být přítomen atribut pro zjednodušení údržby kódu.

## <a name="example"></a>Příklad
Následující příklad definuje dva atributy. `BadCodeMaintainerAttribute` nesprávně vynechá příkaz <xref:System.AttributeUsageAttribute> a `GoodCodeMaintainerAttribute` správně implementuje atribut, který je popsán výše v této části. Všimněte si, že pravidlo návrhu [CA1019 vyžaduje vlastnost `DeveloperName`: Definujte přístupové objekty pro argumenty atributu @ no__t-0 a jsou zahrnuty pro úplnost.

[!code-csharp[FxCop.Design.AttributeUsage#1](../code-quality/codesnippet/CSharp/ca1018-mark-attributes-with-attributeusageattribute_1.cs)]
[!code-vb[FxCop.Design.AttributeUsage#1](../code-quality/codesnippet/VisualBasic/ca1018-mark-attributes-with-attributeusageattribute_1.vb)]

## <a name="related-rules"></a>Související pravidla
[CA1019: Definovat přístupové objekty pro argumenty atributu @ no__t-0

[CA1813: Vyhněte se nezapečetěným atributům @ no__t-0

## <a name="see-also"></a>Viz také:

- [Atributy](/dotnet/standard/design-guidelines/attributes)