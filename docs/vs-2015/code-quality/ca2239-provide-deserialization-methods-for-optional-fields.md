---
title: 'CA2239: Poskytněte metody deserializace pro volitelná pole | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2239
- ProvideDeserializationMethodsForOptionalFields
helpviewer_keywords:
- ProvideDeserializationMethodsForOptionalFields
- CA2239
ms.assetid: 6480ff5e-0caa-4707-814e-2f927cdafef5
caps.latest.revision: 15
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: dfbb9082d557c8e67ddebf0237293364d54a65cf
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/30/2020
ms.locfileid: "85545129"
---
# <a name="ca2239-provide-deserialization-methods-for-optional-fields"></a>CA2239: Zadejte metody deserializace pro nepovinná pole
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Položka|Hodnota|
|-|-|
|TypeName|ProvideDeserializationMethodsForOptionalFields|
|CheckId|CA2239|
|Kategorie|Microsoft. Usage|
|Narušující změna|Bez přerušení|

## <a name="cause"></a>Příčina
 Typ obsahuje pole, které je označeno <xref:System.Runtime.Serialization.OptionalFieldAttribute?displayProperty=fullName> atributem a typ neposkytuje metody zpracování událostí rušení serializace.

## <a name="rule-description"></a>Popis pravidla
 <xref:System.Runtime.Serialization.OptionalFieldAttribute>Atribut nemá žádný vliv na serializaci; pole označené atributem je serializováno. Pole je však ignorováno při zrušení serializace a zachovává výchozí hodnotu přidruženou k jeho typu. Obslužné rutiny události deserializace by měly být deklarovány pro nastavení pole během procesu rušení serializace.

## <a name="how-to-fix-violations"></a>Jak vyřešit porušení
 Chcete-li opravit porušení tohoto pravidla, přidejte do typu metody zpracování událostí ve více serializacích.

## <a name="when-to-suppress-warnings"></a>Kdy potlačit upozornění
 V případě, že by mělo být pole během procesu rušení serializace ignorováno, je bezpečné potlačit upozornění od tohoto pravidla.

## <a name="example"></a>Příklad
 Následující příklad ukazuje typ s volitelnou metodou zpracování události v poli a deserializaci.

 [!code-csharp[FxCop.Usage.OptionalFields#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.OptionalFields/cs/FxCop.Usage.OptionalFields.cs#1)]
 [!code-vb[FxCop.Usage.OptionalFields#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.OptionalFields/vb/FxCop.Usage.OptionalFields.vb#1)]

## <a name="related-rules"></a>Související pravidla
 [CA2236: Volejte metody základní třídy u typů ISerializable](../code-quality/ca2236-call-base-class-methods-on-iserializable-types.md)

 [CA2240: Implementujte správně ISerializable](../code-quality/ca2240-implement-iserializable-correctly.md)

 [CA2229: Implementujte serializační konstruktory](../code-quality/ca2229-implement-serialization-constructors.md)

 [CA2238: Implementujte správně metody serializace](../code-quality/ca2238-implement-serialization-methods-correctly.md)

 [CA2235: Označte všechna neserializovatelná pole](../code-quality/ca2235-mark-all-non-serializable-fields.md)

 [CA2237: Označte typy ISerializable pomocí SerializableAttribute](../code-quality/ca2237-mark-iserializable-types-with-serializableattribute.md)

 [CA2120: Zabezpečte serializační konstruktory](../code-quality/ca2120-secure-serialization-constructors.md)
