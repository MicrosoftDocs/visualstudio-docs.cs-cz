---
title: 'CA1002: nezveřejňujte obecné seznamy | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- DoNotExposeGenericLists
- CA1002
helpviewer_keywords:
- CA1002
- DoNotExposeGenericLists
ms.assetid: 5caac810-1a79-47df-a27b-c46c5040bf34
caps.latest.revision: 22
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 6fcc4ae2a07eb7b1f155d6c65020e2c1a9ddc9f2
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/30/2020
ms.locfileid: "85546845"
---
# <a name="ca1002-do-not-expose-generic-lists"></a>CA1002: Nezveřejňujte obecné seznamy
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Položka|Hodnota|
|-|-|
|TypeName|DoNotExposeGenericLists|
|CheckId|CA1002|
|Kategorie|Microsoft. Design|
|Narušující změna|Narušující|

## <a name="cause"></a>Příčina
 Typ obsahuje externě viditelný člen, který je <xref:System.Collections.Generic.List%601?displayProperty=fullName> typu, vrátí <xref:System.Collections.Generic.List%601?displayProperty=fullName> typ, nebo jehož signatura obsahuje <xref:System.Collections.Generic.List%601?displayProperty=fullName> parametr.

## <a name="rule-description"></a>Popis pravidla
 <xref:System.Collections.Generic.List%601?displayProperty=fullName>je obecná kolekce, která je navržena pro výkon a nikoli pro dědění. <xref:System.Collections.Generic.List%601?displayProperty=fullName>neobsahuje virtuální členy, které usnadňují změnu chování zděděné třídy. Následující obecné kolekce jsou navržené pro dědění a měly by být vystaveny namísto <xref:System.Collections.Generic.List%601?displayProperty=fullName> .

- <xref:System.Collections.ObjectModel.Collection%601?displayProperty=fullName>

- <xref:System.Collections.ObjectModel.ReadOnlyCollection%601?displayProperty=fullName>

- <xref:System.Collections.ObjectModel.KeyedCollection%602?displayProperty=fullName>

## <a name="how-to-fix-violations"></a>Jak vyřešit porušení
 Chcete-li opravit porušení tohoto pravidla, změňte <xref:System.Collections.Generic.List%601?displayProperty=fullName> typ na jednu z obecných kolekcí, která je navržena pro dědění.

## <a name="when-to-suppress-warnings"></a>Kdy potlačit upozornění
 Potlačí upozornění z tohoto pravidla, pokud sestavení, které vyvolává toto upozornění, není určeno jako opakovaně použitelná knihovna. Může být například bezpečné toto upozornění potlačit v aplikaci výkon s vyladěným výkonem, kde výhoda byla získána z použití obecných seznamů.

## <a name="related-rules"></a>Související pravidla
 [CA1005: Vyhněte se nadbytečným parametrům u obecných typů](../code-quality/ca1005-avoid-excessive-parameters-on-generic-types.md)

 [CA1010: Kolekce musí implementovat obecné rozhraní](../code-quality/ca1010-collections-should-implement-generic-interface.md)

 [CA1000: Nedeklarujte statické členy v obecných typech](../code-quality/ca1000-do-not-declare-static-members-on-generic-types.md)

 [CA1006: Nevnořujte obecné typy do signatur členu](../code-quality/ca1006-do-not-nest-generic-types-in-member-signatures.md)

 [CA1004: Obecné metody by měly poskytnout parametr typu](../code-quality/ca1004-generic-methods-should-provide-type-parameter.md)

 [CA1003: Použijte instance obecných obslužných rutin události](../code-quality/ca1003-use-generic-event-handler-instances.md)

 [CA1007: Použijte obecné typy, kde je to vhodné](../code-quality/ca1007-use-generics-where-appropriate.md)

## <a name="see-also"></a>Viz také
 [Obecné typy](https://msdn.microsoft.com/library/75ea8509-a4ea-4e7a-a2b3-cf72482e9282)
