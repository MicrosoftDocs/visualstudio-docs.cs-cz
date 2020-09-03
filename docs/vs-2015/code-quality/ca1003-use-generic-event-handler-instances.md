---
title: 'CA1003: použijte instance obecných obslužných rutin událostí | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- UseGenericEventHandlerInstances
- CA1003
helpviewer_keywords:
- CA1003
- UseGenericEventHandlerInstances
ms.assetid: 402101b6-555d-4cf7-b223-1d9fdfaaf1cd
caps.latest.revision: 24
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: ee0571e85a1d4ec9960e0235814fcb9d7adbd483
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "85539903"
---
# <a name="ca1003-use-generic-event-handler-instances"></a>CA1003: Použijte instance obecných obslužných rutin události
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Položka|Hodnota|
|-|-|
|TypeName|UseGenericEventHandlerInstances|
|CheckId|CA1003|
|Kategorie|Microsoft. Design|
|Narušující změna|Narušující|

## <a name="cause"></a>Příčina
 Typ obsahuje delegát, který vrací typ void, jehož signatura obsahuje dva parametry (první objekt a druhý typ, který lze přiřadit k EventArgs), a obsahující cíle sestavení [!INCLUDE[dnprdnlong](../includes/dnprdnlong-md.md)] .

## <a name="rule-description"></a>Popis pravidla
 Aby bylo možné [!INCLUDE[dnprdnlong](../includes/dnprdnlong-md.md)] předat vlastní informace obslužné rutině události, měl by být deklarován nový delegát, který zadal třídu odvozenou od <xref:System.EventArgs?displayProperty=fullName> třídy. Tato hodnota již není pravdivá v [!INCLUDE[dnprdnlong](../includes/dnprdnlong-md.md)] , která zavedla <xref:System.EventHandler%601?displayProperty=fullName> delegáta. Tento obecný delegát umožňuje používat jakoukoli třídu, která je odvozena z aplikace, <xref:System.EventArgs> spolu s obslužnou rutinou události.

## <a name="how-to-fix-violations"></a>Jak vyřešit porušení
 Chcete-li opravit porušení tohoto pravidla, odeberte delegáta a nahraďte jeho použití pomocí <xref:System.EventHandler%601?displayProperty=fullName> delegáta. Pokud je delegát automaticky vygenerován [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] kompilátorem, změňte syntaxi deklarace události pro použití <xref:System.EventHandler%601?displayProperty=fullName> delegáta.

## <a name="when-to-suppress-warnings"></a>Kdy potlačit upozornění
 Nepotlačujte upozornění na toto pravidlo.

## <a name="example"></a>Příklad
 Následující příklad ukazuje delegáta, který porušuje pravidlo. V [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] příkladu komentáře popisují, jak upravit příklad pro splnění pravidla. Pro příklad v jazyce C# příklad Následuje příklad, který ukazuje upravený kód.

 [!code-csharp[FxCop.Design.CustomEventHandler#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.CustomEventHandler/cs/FxCop.Design.CustomEventHandler.cs#1)]
 [!code-vb[FxCop.Design.CustomEventHandler#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.CustomEventHandler/vb/FxCop.Design.CustomEventHandler.vb#1)]

## <a name="example"></a>Příklad
 Následující příklad odebere deklaraci delegáta z předchozího příkladu, který splňuje pravidlo, a nahradí jeho použití v `ClassThatRaisesEvent` `ClassThatHandlesEvent` metodách a pomocí <xref:System.EventHandler%601?displayProperty=fullName> delegáta.

 [!code-csharp[FxCop.Design.GenericEventHandler#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.GenericEventHandler/cs/FxCop.Design.GenericEventHandler.cs#1)]

## <a name="related-rules"></a>Související pravidla
 [CA1005: Vyhněte se nadbytečným parametrům u obecných typů](../code-quality/ca1005-avoid-excessive-parameters-on-generic-types.md)

 [CA1010: Kolekce musí implementovat obecné rozhraní](../code-quality/ca1010-collections-should-implement-generic-interface.md)

 [CA1000: Nedeklarujte statické členy v obecných typech](../code-quality/ca1000-do-not-declare-static-members-on-generic-types.md)

 [CA1002: Nezveřejňujte obecné seznamy](../code-quality/ca1002-do-not-expose-generic-lists.md)

 [CA1006: Nevnořujte obecné typy do signatur členu](../code-quality/ca1006-do-not-nest-generic-types-in-member-signatures.md)

 [CA1004: Obecné metody by měly poskytnout parametr typu](../code-quality/ca1004-generic-methods-should-provide-type-parameter.md)

 [CA1007: Použijte obecné typy, kde je to vhodné](../code-quality/ca1007-use-generics-where-appropriate.md)

## <a name="see-also"></a>Viz také
 [Obecné typy](https://msdn.microsoft.com/library/75ea8509-a4ea-4e7a-a2b3-cf72482e9282)
