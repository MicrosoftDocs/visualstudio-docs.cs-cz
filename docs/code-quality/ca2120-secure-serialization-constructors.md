---
title: 'CA2120: Zabezpečte serializační konstruktory'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA2120
- SecureSerializationConstructors
helpviewer_keywords:
- SecureSerializationConstructors
- CA2120
ms.assetid: e9989da1-55a0-43f8-9aa9-da86afae3b41
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 38de3597d3693b072fec12f64211af4469851627
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/24/2019
ms.locfileid: "71232546"
---
# <a name="ca2120-secure-serialization-constructors"></a>CA2120: Zabezpečte serializační konstruktory

|||
|-|-|
|TypeName|SecureSerializationConstructors|
|CheckId|CA2120|
|Kategorie|Microsoft.Security|
|Zásadní změna|Narušující|

## <a name="cause"></a>příčina
Typ implementuje <xref:System.Runtime.Serialization.ISerializable?displayProperty=fullName> rozhraní, není delegát ani rozhraní a je deklarován v sestavení, které umožňuje částečně důvěryhodné volající. Typ má konstruktor, který přebírá <xref:System.Runtime.Serialization.SerializationInfo?displayProperty=fullName> objekt <xref:System.Runtime.Serialization.StreamingContext?displayProperty=fullName> a objekt (signatura konstruktoru serializace). Tento konstruktor není zabezpečen kontrolou zabezpečení, ale jeden nebo více regulárních konstruktorů v typu je zabezpečeno.

## <a name="rule-description"></a>Popis pravidla
Toto pravidlo je relevantní pro typy, které podporují vlastní serializaci. Typ podporuje vlastní serializaci, pokud implementuje <xref:System.Runtime.Serialization.ISerializable?displayProperty=fullName> rozhraní. Konstruktor serializace je vyžadován a používá se k deserializaci nebo opětovnému vytvoření objektů, které byly serializovány pomocí <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A?displayProperty=fullName> metody. Vzhledem k tomu, že konstruktor serializace přiděluje a inicializuje objekty, kontroly zabezpečení, které jsou přítomny u regulárních konstruktorů, musí být také přítomny v konstruktoru serializace. Pokud toto pravidlo porušíte, volající, které by jinak nebylo možné vytvořit instanci, by k tomu mohli použít konstruktor serializace.

## <a name="how-to-fix-violations"></a>Jak opravit porušení
Chcete-li opravit porušení tohoto pravidla, zajistěte ochranu konstruktoru serializace pomocí požadavků na zabezpečení, které jsou stejné jako při ochraně jiných konstruktorů.

## <a name="when-to-suppress-warnings"></a>Kdy potlačit upozornění
Potlačit porušení pravidla

## <a name="example"></a>Příklad
Následující příklad ukazuje typ, který je v rozporu s pravidlem.

[!code-csharp[FxCop.Security.SerialCtors#1](../code-quality/codesnippet/CSharp/ca2120-secure-serialization-constructors_1.cs)]

## <a name="related-rules"></a>Související pravidla
[CA2229: Implementovat konstruktory serializace](../code-quality/ca2229-implement-serialization-constructors.md)

[CA2237: Označte typy ISerializable pomocí SerializableAttribute](../code-quality/ca2237-mark-iserializable-types-with-serializableattribute.md)

## <a name="see-also"></a>Viz také:

- <xref:System.Runtime.Serialization.ISerializable?displayProperty=fullName>
- <xref:System.Runtime.Serialization.SerializationInfo?displayProperty=fullName>
- <xref:System.Runtime.Serialization.StreamingContext?displayProperty=fullName>