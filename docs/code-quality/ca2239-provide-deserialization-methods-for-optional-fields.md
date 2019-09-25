---
title: 'CA2239: Zadejte metody deserializace pro nepovinná pole'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA2239
- ProvideDeserializationMethodsForOptionalFields
helpviewer_keywords:
- ProvideDeserializationMethodsForOptionalFields
- CA2239
ms.assetid: 6480ff5e-0caa-4707-814e-2f927cdafef5
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: cf2e30956879c0c61bb57d65b89445962f34959a
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/24/2019
ms.locfileid: "71237897"
---
# <a name="ca2239-provide-deserialization-methods-for-optional-fields"></a>CA2239: Zadejte metody deserializace pro nepovinná pole

|||
|-|-|
|TypeName|ProvideDeserializationMethodsForOptionalFields|
|CheckId|CA2239|
|Kategorie|Microsoft.Usage|
|Zásadní změna|Nenarušující|

## <a name="cause"></a>příčina
Typ obsahuje pole, které je označeno <xref:System.Runtime.Serialization.OptionalFieldAttribute?displayProperty=fullName> atributem a typ neposkytuje metody zpracování událostí rušení serializace.

## <a name="rule-description"></a>Popis pravidla
<xref:System.Runtime.Serialization.OptionalFieldAttribute> Atribut nemá žádný vliv na serializaci; pole označené atributem je serializováno. Pole je však ignorováno při zrušení serializace a zachovává výchozí hodnotu přidruženou k jeho typu. Obslužné rutiny události deserializace by měly být deklarovány pro nastavení pole během procesu rušení serializace.

## <a name="how-to-fix-violations"></a>Jak opravit porušení
Chcete-li opravit porušení tohoto pravidla, přidejte do typu metody zpracování událostí ve více serializacích.

## <a name="when-to-suppress-warnings"></a>Kdy potlačit upozornění
V případě, že by mělo být pole během procesu rušení serializace ignorováno, je bezpečné potlačit upozornění od tohoto pravidla.

## <a name="example"></a>Příklad
Následující příklad ukazuje typ s volitelnou metodou zpracování události v poli a deserializaci.

[!code-csharp[FxCop.Usage.OptionalFields#1](../code-quality/codesnippet/CSharp/ca2239-provide-deserialization-methods-for-optional-fields_1.cs)]
[!code-vb[FxCop.Usage.OptionalFields#1](../code-quality/codesnippet/VisualBasic/ca2239-provide-deserialization-methods-for-optional-fields_1.vb)]

## <a name="related-rules"></a>Související pravidla
[CA2236: Volání metod třídy Base na typech ISerializable](../code-quality/ca2236-call-base-class-methods-on-iserializable-types.md)

[CA2240: Správně implementovat ISerializable](../code-quality/ca2240-implement-iserializable-correctly.md)

[CA2229: Implementovat konstruktory serializace](../code-quality/ca2229-implement-serialization-constructors.md)

[CA2238: Implementujte správně metody serializace](../code-quality/ca2238-implement-serialization-methods-correctly.md)

[CA2235: Označte všechna Neserializovatelný pole](../code-quality/ca2235-mark-all-non-serializable-fields.md)

[CA2237: Označte typy ISerializable pomocí SerializableAttribute](../code-quality/ca2237-mark-iserializable-types-with-serializableattribute.md)

[CA2120: Zabezpečené konstruktory serializace](../code-quality/ca2120-secure-serialization-constructors.md)