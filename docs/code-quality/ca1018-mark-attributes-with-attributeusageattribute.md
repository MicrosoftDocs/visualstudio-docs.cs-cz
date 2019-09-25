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
ms.openlocfilehash: 82a1ed8610ce84279f5fde3b802d976a3e766d99
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/24/2019
ms.locfileid: "71236243"
---
# <a name="ca1018-mark-attributes-with-attributeusageattribute"></a>CA1018: Označte atributy pomocí AttributeUsageAttribute

|||
|-|-|
|TypeName|MarkAttributesWithAttributeUsage|
|CheckId|CA1018|
|Kategorie|Microsoft.Design|
|Zásadní změna|Narušující|

## <a name="cause"></a>příčina
<xref:System.AttributeUsageAttribute?displayProperty=fullName> Atribut není přítomen u vlastního atributu.

## <a name="rule-description"></a>Popis pravidla
Při definování vlastního atributu jej označte pomocí <xref:System.AttributeUsageAttribute> a určete, kde ve zdrojovém kódu lze použít vlastní atribut. Význam a zamýšlené použití atributu určuje jeho platné umístění v kódu. Například můžete definovat atribut, který identifikuje osobu, která je zodpovědná za údržbu a vylepšení každého typu v knihovně, a tato zodpovědnost je vždy přiřazena na úrovni typu. V takovém případě by měly kompilátory povolit atribut pro třídy, výčty a rozhraní, ale neměly by být povoleny v metodách, událostech nebo vlastnostech. Zásady a postupy organizace by měly určovat, jestli má být atribut povolený u sestavení.

<xref:System.AttributeTargets?displayProperty=fullName> Výčet definuje cíle, které lze zadat pro vlastní atribut. Pokud tento parametr <xref:System.AttributeUsageAttribute>vynecháte, bude váš vlastní atribut platný pro všechny cíle, jak je `All` definováno hodnotou <xref:System.AttributeTargets> výčtu.

## <a name="how-to-fix-violations"></a>Jak opravit porušení
Chcete-li opravit porušení tohoto pravidla, zadejte cíle pro atribut pomocí <xref:System.AttributeUsageAttribute>. Podívejte se na téma v následujícím příkladu.

## <a name="when-to-suppress-warnings"></a>Kdy potlačit upozornění
Místo vyloučení zprávy byste měli opravit porušení tohoto pravidla. I v případě, že <xref:System.AttributeUsageAttribute>atribut dědí, by měl být k dispozici atribut pro zjednodušení údržby kódu.

## <a name="example"></a>Příklad
Následující příklad definuje dva atributy. `BadCodeMaintainerAttribute`nesprávně vynechá <xref:System.AttributeUsageAttribute> příkaz a `GoodCodeMaintainerAttribute` správně implementuje atribut, který je popsaný výše v této části. Všimněte si, že `DeveloperName` vlastnost je vyžadována pravidlem [návrhu CA1019: Definujte přístupové objekty pro argumenty](../code-quality/ca1019-define-accessors-for-attribute-arguments.md) atributů a jsou zahrnuty pro úplnost.

[!code-csharp[FxCop.Design.AttributeUsage#1](../code-quality/codesnippet/CSharp/ca1018-mark-attributes-with-attributeusageattribute_1.cs)]
[!code-vb[FxCop.Design.AttributeUsage#1](../code-quality/codesnippet/VisualBasic/ca1018-mark-attributes-with-attributeusageattribute_1.vb)]

## <a name="related-rules"></a>Související pravidla
[CA1019: Definovat přístupové objekty pro argumenty atributu](../code-quality/ca1019-define-accessors-for-attribute-arguments.md)

[CA1813: Vyhněte se nezapečetěným atributům](../code-quality/ca1813-avoid-unsealed-attributes.md)

## <a name="see-also"></a>Viz také:

- [Atributy](/dotnet/standard/design-guidelines/attributes)