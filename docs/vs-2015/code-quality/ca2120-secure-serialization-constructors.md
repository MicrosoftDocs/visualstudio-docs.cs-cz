---
title: 'CA2120: třídy Secure Serialization | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2120
- SecureSerializationConstructors
helpviewer_keywords:
- SecureSerializationConstructors
- CA2120
ms.assetid: e9989da1-55a0-43f8-9aa9-da86afae3b41
caps.latest.revision: 18
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 10cfa03adb74871fb42a6e1c2ce4ab4ba6bcae75
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/30/2020
ms.locfileid: "85544336"
---
# <a name="ca2120-secure-serialization-constructors"></a>CA2120: Zabezpečte serializační konstruktory
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Položka|Hodnota|
|-|-|
|TypeName|SecureSerializationConstructors|
|CheckId|CA2120|
|Kategorie|Microsoft.Security|
|Narušující změna|Narušující|

## <a name="cause"></a>Příčina
 Typ implementuje <xref:System.Runtime.Serialization.ISerializable?displayProperty=fullName> rozhraní, není delegát ani rozhraní a je deklarován v sestavení, které umožňuje částečně důvěryhodné volající. Typ má konstruktor, který přebírá <xref:System.Runtime.Serialization.SerializationInfo?displayProperty=fullName> objekt a <xref:System.Runtime.Serialization.StreamingContext?displayProperty=fullName> objekt (signatura konstruktoru serializace). Tento konstruktor není zabezpečen kontrolou zabezpečení, ale jeden nebo více regulárních konstruktorů v typu je zabezpečeno.

## <a name="rule-description"></a>Popis pravidla
 Toto pravidlo je relevantní pro typy, které podporují vlastní serializaci. Typ podporuje vlastní serializaci, pokud implementuje <xref:System.Runtime.Serialization.ISerializable?displayProperty=fullName> rozhraní. Konstruktor serializace je vyžadován a používá se k deserializaci nebo opětovnému vytvoření objektů, které byly serializovány pomocí <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A?displayProperty=fullName> metody. Vzhledem k tomu, že konstruktor serializace přiděluje a inicializuje objekty, kontroly zabezpečení, které jsou přítomny u regulárních konstruktorů, musí být také přítomny v konstruktoru serializace. Pokud toto pravidlo porušíte, volající, které by jinak nebylo možné vytvořit instanci, by k tomu mohli použít konstruktor serializace.

## <a name="how-to-fix-violations"></a>Jak vyřešit porušení
 Chcete-li opravit porušení tohoto pravidla, zajistěte ochranu konstruktoru serializace pomocí požadavků na zabezpečení, které jsou stejné jako při ochraně jiných konstruktorů.

## <a name="when-to-suppress-warnings"></a>Kdy potlačit upozornění
 Potlačit porušení pravidla

## <a name="example"></a>Příklad
 Následující příklad ukazuje typ, který je v rozporu s pravidlem.

 [!code-csharp[FxCop.Security.SerialCtors#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.SerialCtors/cs/FxCop.Security.SerialCtors.cs#1)]

## <a name="related-rules"></a>Související pravidla
 [CA2229: Implementujte serializační konstruktory](../code-quality/ca2229-implement-serialization-constructors.md)

 [CA2237: Označte typy ISerializable pomocí SerializableAttribute](../code-quality/ca2237-mark-iserializable-types-with-serializableattribute.md)

## <a name="see-also"></a>Viz také
 <xref:System.Runtime.Serialization.ISerializable?displayProperty=fullName> <xref:System.Runtime.Serialization.SerializationInfo?displayProperty=fullName>
 <xref:System.Runtime.Serialization.StreamingContext?displayProperty=fullName>
