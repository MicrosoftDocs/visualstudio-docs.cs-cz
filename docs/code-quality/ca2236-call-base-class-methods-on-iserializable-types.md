---
title: 'CA2236: Volejte metody základní třídy u typů ISerializable'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA2236
- CallBaseClassMethodsOnISerializableTypes
helpviewer_keywords:
- CA2236
- CallBaseClassMethodsOnISerializableTypes
ms.assetid: 5a15b20d-769c-4640-b31a-36e07077daae
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: a9a3070abc1f2bab3f3658589db54b656a635e2b
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/24/2019
ms.locfileid: "71238081"
---
# <a name="ca2236-call-base-class-methods-on-iserializable-types"></a>CA2236: Volejte metody základní třídy u typů ISerializable

|||
|-|-|
|TypeName|CallBaseClassMethodsOnISerializableTypes|
|CheckId|CA2236|
|Kategorie|Microsoft.Usage|
|Zásadní změna|Nenarušující|

## <a name="cause"></a>příčina
Typ je odvozen z typu, který implementuje <xref:System.Runtime.Serialization.ISerializable?displayProperty=fullName> rozhraní, a jedna z následujících podmínek je pravdivá:

- Typ implementuje konstruktor serializace, to znamená konstruktor s <xref:System.Runtime.Serialization.SerializationInfo?displayProperty=fullName>parametrem, <xref:System.Runtime.Serialization.StreamingContext?displayProperty=fullName> , ale nevolá konstruktor serializace základního typu.

- Typ implementuje <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A?displayProperty=fullName> metodu, ale <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A> nevolá metodu základního typu.

## <a name="rule-description"></a>Popis pravidla
Ve vlastním procesu serializace typ implementuje <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A> metodu k serializaci svých polí a konstruktoru serializace pro deserializaci polí. Pokud typ je odvozen z typu, který implementuje <xref:System.Runtime.Serialization.ISerializable> rozhraní, měla by být volána metoda základního typu <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A> a konstruktor serializace k serializaci/deserializaci polí základního typu. V opačném případě typ nebude serializován a správně serializován. Všimněte si, že pokud odvozený typ nepřidá žádná nová pole, typ nepotřebuje implementovat <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A> metodu ani serializaci konstruktoru ani volat ekvivalenty základního typu.

## <a name="how-to-fix-violations"></a>Jak opravit porušení
Chcete-li opravit porušení tohoto pravidla, zavolejte metodu základního typu <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A> nebo konstruktor serializace z odpovídající odvozené metody typu nebo konstruktoru.

## <a name="when-to-suppress-warnings"></a>Kdy potlačit upozornění
Nepotlačujte upozornění na toto pravidlo.

## <a name="example"></a>Příklad
Následující příklad ukazuje odvozený typ, který splňuje pravidlo voláním konstruktoru serializace a <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A> metody základní třídy.

[!code-vb[FxCop.Usage.CallBaseISerializable#1](../code-quality/codesnippet/VisualBasic/ca2236-call-base-class-methods-on-iserializable-types_1.vb)]
[!code-csharp[FxCop.Usage.CallBaseISerializable#1](../code-quality/codesnippet/CSharp/ca2236-call-base-class-methods-on-iserializable-types_1.cs)]

## <a name="related-rules"></a>Související pravidla
[CA2240: Správně implementovat ISerializable](../code-quality/ca2240-implement-iserializable-correctly.md)

[CA2229: Implementovat konstruktory serializace](../code-quality/ca2229-implement-serialization-constructors.md)

[CA2238: Implementujte správně metody serializace](../code-quality/ca2238-implement-serialization-methods-correctly.md)

[CA2235: Označte všechna Neserializovatelný pole](../code-quality/ca2235-mark-all-non-serializable-fields.md)

[CA2237: Označte typy ISerializable pomocí SerializableAttribute](../code-quality/ca2237-mark-iserializable-types-with-serializableattribute.md)

[CA2239: Poskytněte metody deserializace pro volitelná pole.](../code-quality/ca2239-provide-deserialization-methods-for-optional-fields.md)

[CA2120: Zabezpečené konstruktory serializace](../code-quality/ca2120-secure-serialization-constructors.md)