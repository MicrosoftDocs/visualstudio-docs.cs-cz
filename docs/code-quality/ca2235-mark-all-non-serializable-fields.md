---
title: 'CA2235: Označte všechna neserializovatelná pole'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA2235
- MarkAllNonSerializableFields
helpviewer_keywords:
- CA2235
- MarkAllNonSerializableFields
ms.assetid: 599ad877-3a15-426c-bf17-5de15427365f
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 886cc66f820d201b8ab7f29fee00eebce07fc176
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/24/2019
ms.locfileid: "71238106"
---
# <a name="ca2235-mark-all-non-serializable-fields"></a>CA2235: Označte všechna neserializovatelná pole

|||
|-|-|
|TypeName|MarkAllNonSerializableFields|
|CheckId|CA2235|
|Kategorie|Microsoft.Usage|
|Zásadní změna|Nenarušující|

## <a name="cause"></a>příčina

Neserializovatelný typ pole instance je deklarován v serializovatelném typu.

## <a name="rule-description"></a>Popis pravidla

Serializovatelný typ je jeden, který je označen <xref:System.SerializableAttribute?displayProperty=fullName> atributem. Při serializaci typu je vyvolána <xref:System.Runtime.Serialization.SerializationException?displayProperty=fullName> výjimka, pokud typ obsahuje pole instance typu, který není serializovatelný *a* neimplementuje <xref:System.Runtime.Serialization.ISerializable?displayProperty=fullName> rozhraní.

> [!TIP]
> CA2235 se neaktivují pro pole instance typů, která <xref:System.Runtime.Serialization.ISerializable> implementují, protože poskytují svou vlastní logiku serializace.

## <a name="how-to-fix-violations"></a>Jak opravit porušení

Chcete-li opravit porušení tohoto pravidla, použijte <xref:System.NonSerializedAttribute?displayProperty=fullName> atribut pro pole, které není serializovatelný.

## <a name="when-to-suppress-warnings"></a>Kdy potlačit upozornění

Pouze potlačí upozornění z tohoto pravidla, je <xref:System.Runtime.Serialization.ISerializationSurrogate?displayProperty=fullName> -li deklarován typ, který umožňuje serializaci a deserializaci instancí pole.

## <a name="example"></a>Příklad

Následující příklad ukazuje dva typy: jeden, který porušuje pravidlo a jeden, který splňuje pravidlo.

[!code-csharp[FxCop.Usage.MarkNonSerializable#1](../code-quality/codesnippet/CSharp/ca2235-mark-all-non-serializable-fields_1.cs)]
[!code-vb[FxCop.Usage.MarkNonSerializable#1](../code-quality/codesnippet/VisualBasic/ca2235-mark-all-non-serializable-fields_1.vb)]

## <a name="remarks"></a>Poznámky

CA2235 pravidla neanalyzuje typy, které implementují <xref:System.Runtime.Serialization.ISerializable> rozhraní (pokud nejsou označeny <xref:System.SerializableAttribute> také atributem). Důvodem je, že [CA2237 pravidla](../code-quality/ca2237-mark-iserializable-types-with-serializableattribute.md) už doporučuje označení typů, které <xref:System.Runtime.Serialization.ISerializable> implementují rozhraní <xref:System.SerializableAttribute> s atributem.

## <a name="related-rules"></a>Související pravidla

- [CA2229: Implementovat konstruktory serializace](../code-quality/ca2229-implement-serialization-constructors.md)
- [CA2236: Volání metod třídy Base na typech ISerializable](../code-quality/ca2236-call-base-class-methods-on-iserializable-types.md)
- [CA2237: Označte typy ISerializable pomocí SerializableAttribute](../code-quality/ca2237-mark-iserializable-types-with-serializableattribute.md)
- [CA2238: Implementujte správně metody serializace](../code-quality/ca2238-implement-serialization-methods-correctly.md)
- [CA2239: Poskytněte metody deserializace pro volitelná pole.](../code-quality/ca2239-provide-deserialization-methods-for-optional-fields.md)
- [CA2240: Správně implementovat ISerializable](../code-quality/ca2240-implement-iserializable-correctly.md)
- [CA2120: Zabezpečené konstruktory serializace](../code-quality/ca2120-secure-serialization-constructors.md)