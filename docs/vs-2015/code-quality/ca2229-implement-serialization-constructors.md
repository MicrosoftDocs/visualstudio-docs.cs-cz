---
title: 'CA2229: implementace konstruktorů serializace | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2229
- ImplementSerializationConstructors
helpviewer_keywords:
- CA2229
- ImplementSerializationConstructors
ms.assetid: 8e04d5fe-dfad-445a-972e-0648324fac45
caps.latest.revision: 17
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 56d53717afc8cd966903e75f77e1745de0031745
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72662849"
---
# <a name="ca2229-implement-serialization-constructors"></a>CA2229: Implementovat serializační konstruktory
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|ImplementSerializationConstructors|
|CheckId|CA2229|
|Kategorie|Microsoft. Usage|
|Narušující změna|Bez přerušení|

## <a name="cause"></a>příčina
 Typ implementuje rozhraní <xref:System.Runtime.Serialization.ISerializable?displayProperty=fullName>, není delegátem nebo rozhraním a platí jedna z následujících podmínek:

- Typ nemá konstruktor, který přebírá objekt <xref:System.Runtime.Serialization.SerializationInfo?displayProperty=fullName> a objekt <xref:System.Runtime.Serialization.StreamingContext?displayProperty=fullName> (signatura konstruktoru serializace).

- Typ je nezapečetěný a modifikátor přístupu pro svůj Serializační konstruktor není chráněný (Family).

- Typ je zapečetěný a modifikátor přístupu pro svůj Serializační konstruktor není privátní.

## <a name="rule-description"></a>Popis pravidla
 Toto pravidlo je relevantní pro typy, které podporují vlastní serializaci. Typ podporuje vlastní serializaci, pokud implementuje rozhraní <xref:System.Runtime.Serialization.ISerializable>. Konstruktor serializace je vyžadován k deserializaci nebo opětovnému vytvoření objektů, které byly serializovány pomocí metody <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A?displayProperty=fullName>.

## <a name="how-to-fix-violations"></a>Jak vyřešit porušení
 Implementací konstruktoru serializace se vyřeší porušení tohoto pravidla. Pro zapečetěnou třídu musí být konstruktor soukromý. V ostatních případech musí být chráněný.

## <a name="when-to-suppress-warnings"></a>Kdy potlačit upozornění
 Potlačit porušení pravidla Typ nebude deserializovatelný a nebude fungovat v mnoha scénářích.

## <a name="example"></a>Příklad
 Následující příklad ukazuje typ, který splňuje pravidlo.

 [!code-csharp[FxCop.Usage.ISerializableCtor#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.ISerializableCtor/cs/FxCop.Usage.ISerializableCtor.cs#1)]

## <a name="related-rules"></a>Související pravidla
 [CA2237: Označte typy ISerializable pomocí SerializableAttribute](../code-quality/ca2237-mark-iserializable-types-with-serializableattribute.md)

## <a name="see-also"></a>Viz také
 <xref:System.Runtime.Serialization.ISerializable?displayProperty=fullName><xref:System.Runtime.Serialization.SerializationInfo?displayProperty=fullName>
 <xref:System.Runtime.Serialization.StreamingContext?displayProperty=fullName>
