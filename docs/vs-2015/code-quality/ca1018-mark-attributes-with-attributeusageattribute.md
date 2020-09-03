---
title: 'CA1018: označte atributy atributem AttributeUsageAttribute | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1018
- MarkAttributesWithAttributeUsage
helpviewer_keywords:
- CA1018
- MarkAttributesWithAttributeUsage
ms.assetid: 6ab70ec0-220f-4880-af31-45067703133c
caps.latest.revision: 19
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 256fc281b27c483f1dda0317f7d2695fa36c47f8
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "85535054"
---
# <a name="ca1018-mark-attributes-with-attributeusageattribute"></a>CA1018: Označte atributy pomocí AttributeUsageAttribute
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Položka|Hodnota|
|-|-|
|TypeName|MarkAttributesWithAttributeUsage|
|CheckId|CA1018|
|Kategorie|Microsoft. Design|
|Narušující změna|Narušující|

## <a name="cause"></a>Příčina
 <xref:System.AttributeUsageAttribute?displayProperty=fullName>Atribut není přítomen u vlastního atributu.

## <a name="rule-description"></a>Popis pravidla
 Při definování vlastního atributu jej označte pomocí <xref:System.AttributeUsageAttribute> a určete, kde ve zdrojovém kódu lze použít vlastní atribut. Význam a zamýšlené použití atributu určuje jeho platné umístění v kódu. Například můžete definovat atribut, který identifikuje osobu, která je zodpovědná za údržbu a vylepšení každého typu v knihovně, a tato zodpovědnost je vždy přiřazena na úrovni typu. V takovém případě by měly kompilátory povolit atribut pro třídy, výčty a rozhraní, ale neměly by být povoleny v metodách, událostech nebo vlastnostech. Zásady a postupy organizace by měly určovat, jestli má být atribut povolený u sestavení.

 <xref:System.AttributeTargets?displayProperty=fullName>Výčet definuje cíle, které lze zadat pro vlastní atribut. Pokud tento parametr vynecháte <xref:System.AttributeUsageAttribute> , bude váš vlastní atribut platný pro všechny cíle, jak je definováno `All` hodnotou <xref:System.AttributeTargets> výčtu.

## <a name="how-to-fix-violations"></a>Jak vyřešit porušení
 Chcete-li opravit porušení tohoto pravidla, zadejte cíle pro atribut pomocí <xref:System.AttributeUsageAttribute> . Prohlédněte si následující příklad.

## <a name="when-to-suppress-warnings"></a>Kdy potlačit upozornění
 Místo vyloučení zprávy byste měli opravit porušení tohoto pravidla. I v případě, že atribut dědí <xref:System.AttributeUsageAttribute> , by měl být k dispozici atribut pro zjednodušení údržby kódu.

## <a name="example"></a>Příklad
 Následující příklad definuje dva atributy. `BadCodeMaintainerAttribute` nesprávně vynechá <xref:System.AttributeUsageAttribute> příkaz a `GoodCodeMaintainerAttribute` správně implementuje atribut, který je popsaný výše v této části. Všimněte si, že vlastnost `DeveloperName` je vyžadována pravidlem návrhu [CA1019: Definujte přístupové objekty pro argumenty atributu](../code-quality/ca1019-define-accessors-for-attribute-arguments.md) a je zahrnutá pro úplnost.

 [!code-csharp[FxCop.Design.AttributeUsage#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.AttributeUsage/cs/FxCop.Design.AttributeUsage.cs#1)]
 [!code-vb[FxCop.Design.AttributeUsage#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.AttributeUsage/vb/FxCop.Design.AttributeUsage.vb#1)]

## <a name="related-rules"></a>Související pravidla
 [CA1019: Definujte přístupové objekty pro argumenty atributů](../code-quality/ca1019-define-accessors-for-attribute-arguments.md)

 [CA1813: Vyhněte se nezapečetěným atributům](../code-quality/ca1813-avoid-unsealed-attributes.md)

## <a name="see-also"></a>Viz také
 [Atributy](https://msdn.microsoft.com/library/ee0038ef-b247-4747-a650-3c5c5cd58d8b)
