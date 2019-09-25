---
title: 'CA2240: Implementujte správně ISerializable'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA2240
- ImplementISerializableCorrectly
helpviewer_keywords:
- CA2240
- ImplementISerializableCorrectly
ms.assetid: cf05936d-0d6c-49ed-a1b4-220032e50b97
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CPP
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 2640fddcde0d8777363a3c56e398e7ff307a20c7
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/24/2019
ms.locfileid: "71237883"
---
# <a name="ca2240-implement-iserializable-correctly"></a>CA2240: Implementujte správně ISerializable

|||
|-|-|
|TypeName|ImplementISerializableCorrectly|
|CheckId|CA2240|
|Kategorie|Microsoft.Usage|
|Zásadní změna|Nenarušující|

## <a name="cause"></a>příčina

Externě viditelný typ je přiřadit k <xref:System.Runtime.Serialization.ISerializable?displayProperty=fullName> rozhraní a jedna z následujících podmínek je pravdivá:

- Typ dědí, ale nepřepisuje <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A?displayProperty=fullName> metodu a typ deklaruje pole instance, která nejsou označena <xref:System.NonSerializedAttribute?displayProperty=fullName> atributem.

- Typ není zapečetěn a typ implementuje <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A> metodu, která není externě viditelná a overridable.

## <a name="rule-description"></a>Popis pravidla
Pole instance, která jsou deklarována v typu, který <xref:System.Runtime.Serialization.ISerializable?displayProperty=fullName> dědí rozhraní, nejsou automaticky obsažena v procesu serializace. Chcete-li zahrnout pole, typ musí implementovat <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A> metodu a konstruktor serializace. Pokud by pole neměly být serializována, použijte <xref:System.NonSerializedAttribute> atribut na pole, aby explicitně označovala rozhodnutí.

V typech, které nejsou zapečetěné, implementace <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A> metody by měly být externě viditelné. Proto může být metoda volána odvozenými typy a je možné ji přepsat.

## <a name="how-to-fix-violations"></a>Jak opravit porušení
Chcete-li opravit porušení tohoto pravidla, zajistěte, aby byla <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A> metoda viditelná a Overridable, a ujistěte se, že všechna pole instance jsou zahrnuta v procesu serializace nebo explicitně označena <xref:System.NonSerializedAttribute> atributem.

## <a name="when-to-suppress-warnings"></a>Kdy potlačit upozornění
Nepotlačujte upozornění na toto pravidlo.

## <a name="example"></a>Příklad
Následující příklad ukazuje dva Serializovatelné typy, které porušují pravidlo.

[!code-csharp[FxCop.Usage.ImplementISerializableCorrectly#1](../code-quality/codesnippet/CSharp/ca2240-implement-iserializable-correctly_1.cs)]
[!code-cpp[FxCop.Usage.ImplementISerializableCorrectly#1](../code-quality/codesnippet/CPP/ca2240-implement-iserializable-correctly_1.cpp)]
[!code-vb[FxCop.Usage.ImplementISerializableCorrectly#1](../code-quality/codesnippet/VisualBasic/ca2240-implement-iserializable-correctly_1.vb)]

## <a name="example"></a>Příklad
Následující příklad opravuje dvě předchozí porušení poskytnutím přepsané implementace <xref:System.Runtime.Serialization.ISerializable.GetObjectData> třídy Book a poskytnutím `GetObjectData` implementace třídy knihovny.

[!code-cpp[FxCop.Usage.ImplementISerializableCorrectly2#1](../code-quality/codesnippet/CPP/ca2240-implement-iserializable-correctly_2.cpp)]
[!code-csharp[FxCop.Usage.ImplementISerializableCorrectly2#1](../code-quality/codesnippet/CSharp/ca2240-implement-iserializable-correctly_2.cs)]
[!code-vb[FxCop.Usage.ImplementISerializableCorrectly2#1](../code-quality/codesnippet/VisualBasic/ca2240-implement-iserializable-correctly_2.vb)]

## <a name="related-rules"></a>Související pravidla

- [CA2236: Volání metod třídy Base na typech ISerializable](../code-quality/ca2236-call-base-class-methods-on-iserializable-types.md)
- [CA2229: Implementovat konstruktory serializace](../code-quality/ca2229-implement-serialization-constructors.md)
- [CA2238: Implementujte správně metody serializace](../code-quality/ca2238-implement-serialization-methods-correctly.md)
- [CA2235: Označte všechna Neserializovatelný pole](../code-quality/ca2235-mark-all-non-serializable-fields.md)
- [CA2237: Označte typy ISerializable pomocí SerializableAttribute](../code-quality/ca2237-mark-iserializable-types-with-serializableattribute.md)
- [CA2239: Poskytněte metody deserializace pro volitelná pole.](../code-quality/ca2239-provide-deserialization-methods-for-optional-fields.md)
- [CA2120: Zabezpečené konstruktory serializace](../code-quality/ca2120-secure-serialization-constructors.md)