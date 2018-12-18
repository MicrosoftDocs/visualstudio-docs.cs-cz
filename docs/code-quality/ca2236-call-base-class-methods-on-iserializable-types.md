---
title: 'CA2236: Volejte metody třídy Base na typech ISerializable'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
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
manager: douge
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 9c5b4dee5a274e88be407e015adc4d20c06605dd
ms.sourcegitcommit: 568bb0b944d16cfe1af624879fa3d3594d020187
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/13/2018
ms.locfileid: "45547643"
---
# <a name="ca2236-call-base-class-methods-on-iserializable-types"></a>CA2236: Volejte metody třídy Base na typech ISerializable

|||
|-|-|
|TypeName|CallBaseClassMethodsOnISerializableTypes|
|CheckId|CA2236|
|Kategorie|Microsoft.Usage|
|Narušující změna|Pevné|

## <a name="cause"></a>příčina
 Typ je odvozen od typu, který implementuje <xref:System.Runtime.Serialization.ISerializable?displayProperty=fullName> platí rozhraní a jeden z následujících podmínek:

- Tento typ implementuje konstruktor serializace, to znamená, konstruktor s <xref:System.Runtime.Serialization.SerializationInfo?displayProperty=fullName>, <xref:System.Runtime.Serialization.StreamingContext?displayProperty=fullName> parametru signatury, ale nevolá Serializační konstruktor základního typu.

- Tento typ implementuje <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A?displayProperty=fullName> metoda ale nevolá <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A> metodu základního typu.

## <a name="rule-description"></a>Popis pravidla
 Probíhá vlastní serializace, typ implementuje <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A> metoda k serializaci polí a Serializační konstruktor deserializovat pole. Pokud typ je odvozen z typu, který implementuje <xref:System.Runtime.Serialization.ISerializable> základní typ rozhraní <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A> konstruktoru serializace a metoda by měla být volána k serializaci nebo rušení-serialize pole ze základního typu. Typ, jinak nebude serializovat a deserializovaný správně. Všimněte si, že pokud odvozený typ nepřidá všechna nová pole, typ není nutné provádět <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A> metoda ani Serializační konstruktor nebo volejte základní typ ekvivalenty.

## <a name="how-to-fix-violations"></a>Jak vyřešit porušení
 Chcete-li opravit porušení tohoto pravidla, zavolejte základní typ <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A> metoda nebo konstruktor serializace z odpovídající odvozený typ metody nebo konstruktoru.

## <a name="when-to-suppress-warnings"></a>Kdy potlačit upozornění
 Nepotlačujte upozornění na toto pravidlo.

## <a name="example"></a>Příklad
 Následující příklad ukazuje odvozený typ, který splňuje pravidlo zavoláním konstruktoru serializace a <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A> metody základní třídy.

 [!code-vb[FxCop.Usage.CallBaseISerializable#1](../code-quality/codesnippet/VisualBasic/ca2236-call-base-class-methods-on-iserializable-types_1.vb)]
 [!code-csharp[FxCop.Usage.CallBaseISerializable#1](../code-quality/codesnippet/CSharp/ca2236-call-base-class-methods-on-iserializable-types_1.cs)]

## <a name="related-rules"></a>Související pravidla
 [CA2240: Implementujte správně ISerializable](../code-quality/ca2240-implement-iserializable-correctly.md)

 [CA2229: Implementovat serializační konstruktory](../code-quality/ca2229-implement-serialization-constructors.md)

 [CA2238: Implementujte správně metody serializace](../code-quality/ca2238-implement-serialization-methods-correctly.md)

 [CA2235: Označte všechna neserializovatelná pole](../code-quality/ca2235-mark-all-non-serializable-fields.md)

 [CA2237: Označte typy ISerializable pomocí SerializableAttribute](../code-quality/ca2237-mark-iserializable-types-with-serializableattribute.md)

 [CA2239: Poskytujte metody deserializace pro nepovinné pole](../code-quality/ca2239-provide-deserialization-methods-for-optional-fields.md)

 [CA2120: Zabezpečte serializační konstruktory](../code-quality/ca2120-secure-serialization-constructors.md)