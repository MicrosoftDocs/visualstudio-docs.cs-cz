---
title: 'CA2240: Implementujte správně ISerializable | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2240
- ImplementISerializableCorrectly
helpviewer_keywords:
- CA2240
- ImplementISerializableCorrectly
ms.assetid: cf05936d-0d6c-49ed-a1b4-220032e50b97
caps.latest.revision: 23
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 217f95b7d3658db107fc482040686eea9ee47604
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "85543660"
---
# <a name="ca2240-implement-iserializable-correctly"></a>CA2240: Implementujte správně ISerializable
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Položka|Hodnota|
|-|-|
|TypeName|ImplementISerializableCorrectly|
|CheckId|CA2240|
|Kategorie|Microsoft. Usage|
|Narušující změna|Bez přerušení|

## <a name="cause"></a>Příčina
 Externě viditelný typ je přiřadit k <xref:System.Runtime.Serialization.ISerializable?displayProperty=fullName> rozhraní a jedna z následujících podmínek je pravdivá:

- Typ dědí, ale nepřepisuje <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A?displayProperty=fullName> metodu a typ deklaruje pole instance, která nejsou označena <xref:System.NonSerializedAttribute?displayProperty=fullName> atributem.

- Typ není zapečetěn a typ implementuje <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A> metodu, která není externě viditelná a overridable.

## <a name="rule-description"></a>Popis pravidla
 Pole instance, která jsou deklarována v typu, který dědí rozhraní, nejsou <xref:System.Runtime.Serialization.ISerializable?displayProperty=fullName> automaticky obsažena v procesu serializace. Chcete-li zahrnout pole, typ musí implementovat <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A> metodu a konstruktor serializace. Pokud by pole neměly být serializována, použijte <xref:System.NonSerializedAttribute> atribut na pole, aby explicitně označovala rozhodnutí.

 V typech, které nejsou zapečetěné, implementace <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A> metody by měly být externě viditelné. Proto může být metoda volána odvozenými typy a je možné ji přepsat.

## <a name="how-to-fix-violations"></a>Jak vyřešit porušení
 Chcete-li opravit porušení tohoto pravidla, zajistěte, aby byla <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A> Metoda viditelná a Overridable, a ujistěte se, že všechna pole instance jsou zahrnuta v procesu serializace nebo explicitně označena <xref:System.NonSerializedAttribute> atributem.

## <a name="when-to-suppress-warnings"></a>Kdy potlačit upozornění
 Nepotlačujte upozornění na toto pravidlo.

## <a name="example"></a>Příklad
 Následující příklad ukazuje dva Serializovatelné typy, které porušují pravidlo.

 [!code-cpp[FxCop.Usage.ImplementISerializableCorrectly#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Usage.ImplementISerializableCorrectly/cpp/FxCop.Usage.ImplementISerializableCorrectly.cpp#1)]
 [!code-csharp[FxCop.Usage.ImplementISerializableCorrectly#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.ImplementISerializableCorrectly/cs/FxCop.Usage.ImplementISerializableCorrectly.cs#1)]
 [!code-vb[FxCop.Usage.ImplementISerializableCorrectly#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.ImplementISerializableCorrectly/vb/FxCop.Usage.ImplementISerializableCorrectly.vb#1)]

## <a name="example"></a>Příklad
 Následující příklad opravuje dvě předchozí narušení tím, že poskytuje přepsanou implementaci [ISerializable. GetObjectData] (<!-- TODO: review code entity reference <xref:assetId:///ISerializable.GetObjectData?qualifyHint=False&amp;autoUpgrade=False>  -->) na třídě Book a poskytnutím implementace <!-- TODO: review code entity reference <xref:assetId:///ISerializable.GetObjectData?qualifyHint=False&amp;autoUpgrade=False>  --> v knihovně třídy.

 [!code-cpp[FxCop.Usage.ImplementISerializableCorrectly2#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Usage.ImplementISerializableCorrectly2/cpp/FxCop.Usage.ImplementISerializableCorrectly2.cpp#1)]
 [!code-csharp[FxCop.Usage.ImplementISerializableCorrectly2#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.ImplementISerializableCorrectly2/cs/FxCop.Usage.ImplementISerializableCorrectly2.cs#1)]
 [!code-vb[FxCop.Usage.ImplementISerializableCorrectly2#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.ImplementISerializableCorrectly2/vb/FxCop.Usage.ImplementISerializableCorrectly2.vb#1)]

## <a name="related-rules"></a>Související pravidla
 [CA2236: Volejte metody základní třídy u typů ISerializable](../code-quality/ca2236-call-base-class-methods-on-iserializable-types.md)

 [CA2229: Implementujte serializační konstruktory](../code-quality/ca2229-implement-serialization-constructors.md)

 [CA2238: Implementujte správně metody serializace](../code-quality/ca2238-implement-serialization-methods-correctly.md)

 [CA2235: Označte všechna neserializovatelná pole](../code-quality/ca2235-mark-all-non-serializable-fields.md)

 [CA2237: Označte typy ISerializable pomocí SerializableAttribute](../code-quality/ca2237-mark-iserializable-types-with-serializableattribute.md)

 [CA2239: Zadejte metody deserializace pro nepovinná pole](../code-quality/ca2239-provide-deserialization-methods-for-optional-fields.md)

 [CA2120: Zabezpečte serializační konstruktory](../code-quality/ca2120-secure-serialization-constructors.md)
