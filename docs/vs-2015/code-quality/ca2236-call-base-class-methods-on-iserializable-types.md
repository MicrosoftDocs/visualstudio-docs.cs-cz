---
title: 'CA2236: volejte metody třídy Base na typech ISerializable | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2236
- CallBaseClassMethodsOnISerializableTypes
helpviewer_keywords:
- CA2236
- CallBaseClassMethodsOnISerializableTypes
ms.assetid: 5a15b20d-769c-4640-b31a-36e07077daae
caps.latest.revision: 17
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: a03192ac8a5b59558dc39a32f55e8177dc249365
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "85545181"
---
# <a name="ca2236-call-base-class-methods-on-iserializable-types"></a>CA2236: Volejte metody základní třídy u typů ISerializable
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Položka|Hodnota|
|-|-|
|TypeName|CallBaseClassMethodsOnISerializableTypes|
|CheckId|CA2236|
|Kategorie|Microsoft. Usage|
|Narušující změna|Bez přerušení|

## <a name="cause"></a>Příčina
 Typ je odvozen z typu, který implementuje <xref:System.Runtime.Serialization.ISerializable?displayProperty=fullName> rozhraní, a jedna z následujících podmínek je pravdivá:

- Typ implementuje konstruktor serializace, to znamená konstruktor s <xref:System.Runtime.Serialization.SerializationInfo?displayProperty=fullName> <xref:System.Runtime.Serialization.StreamingContext?displayProperty=fullName> parametrem,, ale nevolá konstruktor serializace základního typu.

- Typ implementuje metodu, <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A?displayProperty=fullName> ale nevolá <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A> metodu základního typu.

## <a name="rule-description"></a>Popis pravidla
 Ve vlastním procesu serializace typ implementuje <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A> metodu k serializaci svých polí a konstruktoru serializace pro deserializaci polí. Pokud typ je odvozen z typu, který implementuje <xref:System.Runtime.Serialization.ISerializable> rozhraní, <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A> měla by být volána metoda základního typu a konstruktor serializace k serializaci/deserializaci polí základního typu. V opačném případě typ nebude serializován a správně serializován. Všimněte si, že pokud odvozený typ nepřidá žádná nová pole, typ nepotřebuje implementovat <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A> metodu ani serializaci konstruktoru ani volat ekvivalenty základního typu.

## <a name="how-to-fix-violations"></a>Jak vyřešit porušení
 Chcete-li opravit porušení tohoto pravidla, zavolejte metodu základního typu <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A> nebo konstruktor serializace z odpovídající odvozené metody typu nebo konstruktoru.

## <a name="when-to-suppress-warnings"></a>Kdy potlačit upozornění
 Nepotlačujte upozornění na toto pravidlo.

## <a name="example"></a>Příklad
 Následující příklad ukazuje odvozený typ, který splňuje pravidlo voláním konstruktoru serializace a <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A> metody základní třídy.

 [!code-csharp[FxCop.Usage.CallBaseISerializable#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.CallBaseISerializable/cs/FxCop.Usage.CallBaseISerializable.cs#1)]
 [!code-vb[FxCop.Usage.CallBaseISerializable#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.CallBaseISerializable/vb/FxCop.Usage.CallBaseISerializable.vb#1)]

## <a name="related-rules"></a>Související pravidla
 [CA2240: Implementujte správně ISerializable](../code-quality/ca2240-implement-iserializable-correctly.md)

 [CA2229: Implementujte serializační konstruktory](../code-quality/ca2229-implement-serialization-constructors.md)

 [CA2238: Implementujte správně metody serializace](../code-quality/ca2238-implement-serialization-methods-correctly.md)

 [CA2235: Označte všechna neserializovatelná pole](../code-quality/ca2235-mark-all-non-serializable-fields.md)

 [CA2237: Označte typy ISerializable pomocí SerializableAttribute](../code-quality/ca2237-mark-iserializable-types-with-serializableattribute.md)

 [CA2239: Zadejte metody deserializace pro nepovinná pole](../code-quality/ca2239-provide-deserialization-methods-for-optional-fields.md)

 [CA2120: Zabezpečte serializační konstruktory](../code-quality/ca2120-secure-serialization-constructors.md)
