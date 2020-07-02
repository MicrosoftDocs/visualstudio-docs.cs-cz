---
title: 'CA1813: Vyhněte se nezapečetěným atributům | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1813
- AvoidUnsealedAttributes
helpviewer_keywords:
- CA1813
- AvoidUnsealedAttributes
ms.assetid: f5e31b4c-9f8b-49e1-a2a8-bb5f1140729a
caps.latest.revision: 15
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 8d86f4a9ecbdfff451fed21f93c0fe6a7679d471
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/30/2020
ms.locfileid: "85543946"
---
# <a name="ca1813-avoid-unsealed-attributes"></a>CA1813: Vyhněte se nezapečetěným atributům
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Položka|Hodnota|
|-|-|
|TypeName|AvoidUnsealedAttributes|
|CheckId|CA1813|
|Kategorie|Microsoft. Performance|
|Narušující změna|Narušující|

## <a name="cause"></a>Příčina
 Veřejný typ dědí z <xref:System.Attribute?displayProperty=fullName> , není abstraktní a není zapečetěný ( `NotInheritable` v Visual Basic).

## <a name="rule-description"></a>Popis pravidla
 [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)]Knihovna tříd poskytuje metody pro načítání vlastních atributů. Ve výchozím nastavení tyto metody prohledají hierarchii dědičnosti atributů; například <xref:System.Attribute.GetCustomAttribute%2A?displayProperty=fullName> vyhledá zadaný typ atributu nebo jakýkoli typ atributu, který rozšiřuje zadaný typ atributu. Zapečetění atributu eliminuje hledání prostřednictvím Hierarchie dědičnosti a může zvýšit výkon.

## <a name="how-to-fix-violations"></a>Jak vyřešit porušení
 Chcete-li opravit porušení tohoto pravidla, zapečeťte typ atributu nebo jej zajistěte jako abstraktní.

## <a name="when-to-suppress-warnings"></a>Kdy potlačit upozornění
 Z tohoto pravidla je bezpečné potlačit upozornění. Měli byste to udělat jenom v případě, že definujete hierarchii atributů a nemůžete zapečetit atribut nebo ho vytvořit jako abstraktní.

## <a name="example"></a>Příklad
 Následující příklad ukazuje vlastní atribut, který splňuje toto pravidlo.

 [!code-csharp[FxCop.Performance.AttributesSealed#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Performance.AttributesSealed/cs/FxCop.Performance.AttributesSealed.cs#1)]
 [!code-vb[FxCop.Performance.AttributesSealed#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Performance.AttributesSealed/vb/FxCop.Performance.AttributesSealed.vb#1)]

## <a name="related-rules"></a>Související pravidla
 [CA1019: Definujte přístupové objekty pro argumenty atributů](../code-quality/ca1019-define-accessors-for-attribute-arguments.md)

 [CA1018: Označte atributy pomocí AttributeUsageAttribute](../code-quality/ca1018-mark-attributes-with-attributeusageattribute.md)

## <a name="see-also"></a>Viz také
 [Atributy](https://msdn.microsoft.com/library/ee0038ef-b247-4747-a650-3c5c5cd58d8b)
