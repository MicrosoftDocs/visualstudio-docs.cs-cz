---
title: 'CA2238: Implementujte správně metody serializace'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- ImplementSerializationMethodsCorrectly
- CA2238
helpviewer_keywords:
- ImplementSerializationMethodsCorrectly
- CA2238
ms.assetid: 00882cf9-e10d-4d40-9126-3e6753e3c934
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: b0bbe31f0431b259f60c1fe68a8d9edeffc572d9
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/24/2019
ms.locfileid: "71237914"
---
# <a name="ca2238-implement-serialization-methods-correctly"></a>CA2238: Implementujte správně metody serializace

|||
|-|-|
|TypeName|ImplementSerializationMethodsCorrectly|
|CheckId|CA2238|
|Kategorie|Microsoft.Usage|
|Zásadní změna|Přerušení – Pokud je metoda viditelná vně sestavení.<br /><br /> Bez přerušení – Pokud metoda není viditelná vně sestavení.|

## <a name="cause"></a>příčina
Metoda, která zpracovává událost serializace, nemá správný podpis, návratový typ nebo viditelnost.

## <a name="rule-description"></a>Popis pravidla
Metoda je určena pro obslužnou rutinu události serializace použitím jednoho z následujících atributů události serializace:

- <xref:System.Runtime.Serialization.OnSerializingAttribute?displayProperty=fullName>

- <xref:System.Runtime.Serialization.OnSerializedAttribute?displayProperty=fullName>

- <xref:System.Runtime.Serialization.OnDeserializingAttribute?displayProperty=fullName>

- <xref:System.Runtime.Serialization.OnDeserializedAttribute?displayProperty=fullName>

  Obslužné rutiny událostí serializace přebírají jeden <xref:System.Runtime.Serialization.StreamingContext?displayProperty=fullName>parametr typu `void`, vrátí a `private` mají viditelnost.

## <a name="how-to-fix-violations"></a>Jak opravit porušení
Chcete-li opravit porušení tohoto pravidla, opravte podpis, návratový typ nebo viditelnost obslužné rutiny události serializace.

## <a name="when-to-suppress-warnings"></a>Kdy potlačit upozornění
Nepotlačujte upozornění na toto pravidlo.

## <a name="example"></a>Příklad
Následující příklad ukazuje správně deklarované obslužné rutiny událostí serializace.

[!code-vb[FxCop.Usage.SerializationEventHandlers#1](../code-quality/codesnippet/VisualBasic/ca2238-implement-serialization-methods-correctly_1.vb)]
[!code-csharp[FxCop.Usage.SerializationEventHandlers#1](../code-quality/codesnippet/CSharp/ca2238-implement-serialization-methods-correctly_1.cs)]

## <a name="related-rules"></a>Související pravidla
[CA2236: Volání metod třídy Base na typech ISerializable](../code-quality/ca2236-call-base-class-methods-on-iserializable-types.md)

[CA2240: Správně implementovat ISerializable](../code-quality/ca2240-implement-iserializable-correctly.md)

[CA2229: Implementovat konstruktory serializace](../code-quality/ca2229-implement-serialization-constructors.md)

[CA2235: Označte všechna Neserializovatelný pole](../code-quality/ca2235-mark-all-non-serializable-fields.md)

[CA2237: Označte typy ISerializable pomocí SerializableAttribute](../code-quality/ca2237-mark-iserializable-types-with-serializableattribute.md)

[CA2239: Poskytněte metody deserializace pro volitelná pole.](../code-quality/ca2239-provide-deserialization-methods-for-optional-fields.md)

 [CA2120: Zabezpečené konstruktory serializace](../code-quality/ca2120-secure-serialization-constructors.md)