---
title: 'CA2227: vlastnosti kolekce by měly být jen pro čtení | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2227
- CollectionPropertiesShouldBeReadOnly
helpviewer_keywords:
- CA2227
- CollectionPropertiesShouldBeReadOnly
ms.assetid: 26967aaf-6fbe-438a-b4d3-ac579b5dc0f9
caps.latest.revision: 19
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 8aee6f7172414de809d964652411c1f077fe0cdd
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72658860"
---
# <a name="ca2227-collection-properties-should-be-read-only"></a>CA2227: Vlastnosti kolekce by měly být pouze pro čtení
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|CollectionPropertiesShouldBeReadOnly|
|CheckId|CA2227|
|Kategorie|Microsoft. Usage|
|Narušující změna|Narušující|

## <a name="cause"></a>příčina
 Externě viditelná vlastnost s možností zápisu je typ, který implementuje <xref:System.Collections.ICollection?displayProperty=fullName>. Pole, indexery (vlastnosti s názvem Item) a sady oprávnění jsou pravidlem ignorovány.

## <a name="rule-description"></a>Popis pravidla
 Vlastnost zapisovatelné kolekce umožňuje uživateli nahradit kolekci zcela jinou kolekcí. Vlastnost jen pro čtení neumožňuje kolekci nahradit, ale stále umožňuje nastavit jednotlivé členy. Pokud nahradíte kolekci cílem, preferovaný vzor návrhu je zahrnout metodu pro odebrání všech prvků z kolekce a metodu pro opětovné naplnění kolekce. Příklad tohoto vzoru naleznete v tématu metody <xref:System.Collections.ArrayList?displayProperty=fullName> třídy <xref:System.Collections.ArrayList.Clear%2A> a <xref:System.Collections.ArrayList.AddRange%2A>.

 Binární i XML serializace podporují vlastnosti jen pro čtení, které jsou kolekcemi. Třída <xref:System.Xml.Serialization.XmlSerializer?displayProperty=fullName> má specifické požadavky pro typy, které implementují <xref:System.Collections.ICollection> a <xref:System.Collections.IEnumerable?displayProperty=fullName>, aby bylo možné serializovat.

## <a name="how-to-fix-violations"></a>Jak vyřešit porušení
 Chcete-li opravit porušení tohoto pravidla, nastavte vlastnost jen pro čtení a v případě, že je návrh vyžaduje, přidejte metody, které vymaže a znovu naplní kolekci.

## <a name="when-to-suppress-warnings"></a>Kdy potlačit upozornění
 Nepotlačujte upozornění na toto pravidlo.

## <a name="example"></a>Příklad
 Následující příklad ukazuje typ s zapisovatelnou vlastností Collection a ukazuje, jak lze kolekci nahradit přímo. Kromě toho je zobrazen upřednostňovaný způsob nahrazení vlastnosti kolekce jen pro čtení pomocí `Clear` a `AddRange`ch metod.

 [!code-cpp[FxCop.Usage.PropertiesReturningCollections#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Usage.PropertiesReturningCollections/cpp/FxCop.Usage.PropertiesReturningCollections.cpp#1)]
 [!code-csharp[FxCop.Usage.PropertiesReturningCollections#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.PropertiesReturningCollections/cs/FxCop.Usage.PropertiesReturningCollections.cs#1)]
 [!code-vb[FxCop.Usage.PropertiesReturningCollections#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.PropertiesReturningCollections/vb/FxCop.Usage.PropertiesReturningCollections.vb#1)]

## <a name="related-rules"></a>Související pravidla
 [CA1819: Vlastnosti by neměly vracet pole](../code-quality/ca1819-properties-should-not-return-arrays.md)
