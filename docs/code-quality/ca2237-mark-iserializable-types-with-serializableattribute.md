---
title: 'CA2237: Označte typy ISerializable pomocí SerializableAttribute'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA2237
- MarkISerializableTypesWithSerializable
helpviewer_keywords:
- MarkISerializableTypesWithSerializable
- CA2237
ms.assetid: 9bd6bb24-a527-43dd-9952-043c0c694f46
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 53d049cad426201a8aaa48662061a4a424116b26
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/24/2019
ms.locfileid: "71237930"
---
# <a name="ca2237-mark-iserializable-types-with-serializableattribute"></a>CA2237: Označte typy ISerializable pomocí SerializableAttribute

|||
|-|-|
|TypeName|MarkISerializableTypesWithSerializable|
|CheckId|CA2237|
|Kategorie|Microsoft.Usage|
|Zásadní změna|Nenarušující|

## <a name="cause"></a>příčina
Externě viditelný typ implementuje <xref:System.Runtime.Serialization.ISerializable?displayProperty=fullName> rozhraní a typ není označen <xref:System.SerializableAttribute?displayProperty=fullName> atributem. Pravidlo ignoruje odvozené typy, jejichž základní typ není serializovatelný.

## <a name="rule-description"></a>Popis pravidla
Aby je bylo možné rozpoznat modulem CLR (Common Language Runtime) jako serializovatelný, typy <xref:System.SerializableAttribute> musí být označeny atributem i v případě, že typ používá vlastní rutinu serializace prostřednictvím implementace <xref:System.Runtime.Serialization.ISerializable> rozhraní.

## <a name="how-to-fix-violations"></a>Jak opravit porušení
Chcete-li opravit porušení tohoto pravidla, použijte <xref:System.SerializableAttribute> atribut na typ.

## <a name="when-to-suppress-warnings"></a>Kdy potlačit upozornění
Potlačit upozornění z tohoto pravidla pro třídy výjimek, protože musí být serializovatelný pro správné fungování napříč doménami aplikace.

## <a name="example"></a>Příklad
Následující příklad ukazuje typ, který je v rozporu s pravidlem. Odkomentujte <xref:System.SerializableAttribute> řádek atributu pro splnění pravidla.

[!code-vb[FxCop.Usage.MarkSerializable#1](../code-quality/codesnippet/VisualBasic/ca2237-mark-iserializable-types-with-serializableattribute_1.vb)]
[!code-csharp[FxCop.Usage.MarkSerializable#1](../code-quality/codesnippet/CSharp/ca2237-mark-iserializable-types-with-serializableattribute_1.cs)]

## <a name="related-rules"></a>Související pravidla
[CA2236: Volání metod třídy Base na typech ISerializable](../code-quality/ca2236-call-base-class-methods-on-iserializable-types.md)

[CA2240: Správně implementovat ISerializable](../code-quality/ca2240-implement-iserializable-correctly.md)

[CA2229: Implementovat konstruktory serializace](../code-quality/ca2229-implement-serialization-constructors.md)

[CA2238: Implementujte správně metody serializace](../code-quality/ca2238-implement-serialization-methods-correctly.md)

[CA2235: Označte všechna Neserializovatelný pole](../code-quality/ca2235-mark-all-non-serializable-fields.md)

[CA2239: Poskytněte metody deserializace pro volitelná pole.](../code-quality/ca2239-provide-deserialization-methods-for-optional-fields.md)

[CA2120: Zabezpečené konstruktory serializace](../code-quality/ca2120-secure-serialization-constructors.md)