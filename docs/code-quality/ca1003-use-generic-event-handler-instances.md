---
title: 'CA1003: Použijte instance obecných obslužných rutin události'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- UseGenericEventHandlerInstances
- CA1003
helpviewer_keywords:
- CA1003
- UseGenericEventHandlerInstances
ms.assetid: 402101b6-555d-4cf7-b223-1d9fdfaaf1cd
author: gewarren
ms.author: gewarren
manager: douge
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 29bd98677715a8772143ab448206f2a5ccddd763
ms.sourcegitcommit: 568bb0b944d16cfe1af624879fa3d3594d020187
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/13/2018
ms.locfileid: "45551615"
---
# <a name="ca1003-use-generic-event-handler-instances"></a>CA1003: Použijte instance obecných obslužných rutin události

|||
|-|-|
|TypeName|UseGenericEventHandlerInstances|
|CheckId|CA1003|
|Kategorie|Microsoft.Design|
|Narušující změna|Narušující|

## <a name="cause"></a>příčina
 Typ obsahuje delegát vracející hodnotu void, jehož předpis obsahuje dva parametry (první je objekt a druhý typ přiřaditelný do typu EventArgs) a obsahující cíle sestavení [!INCLUDE[dnprdnlong](../code-quality/includes/dnprdnlong_md.md)].

## <a name="rule-description"></a>Popis pravidla
 Před [!INCLUDE[dnprdnlong](../code-quality/includes/dnprdnlong_md.md)], chcete-li předat informace o vlastním obslužné rutiny události Nový delegát museli použít deklaraci, která je určena třída, která byla odvozena z <xref:System.EventArgs?displayProperty=fullName> třídy. To platí už v [!INCLUDE[dnprdnlong](../code-quality/includes/dnprdnlong_md.md)], který zavedl <xref:System.EventHandler%601?displayProperty=fullName> delegovat. Tento obecný delegát umožňuje jakoukoli třídu, která je odvozena od <xref:System.EventArgs> se použije spolu s obslužnou rutinu události.

## <a name="how-to-fix-violations"></a>Jak vyřešit porušení
 Chcete-li opravit porušení tohoto pravidla, odeberte delegáta a nahraďte jeho použití pomocí <xref:System.EventHandler%601?displayProperty=fullName> delegovat. Pokud delegát je automaticky generována podle [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] kompilátoru, změníte syntaxi deklarace události použití <xref:System.EventHandler%601?displayProperty=fullName> delegovat.

## <a name="when-to-suppress-warnings"></a>Kdy potlačit upozornění
 Nepotlačujte upozornění na toto pravidlo.

## <a name="example"></a>Příklad
 Následující příklad ukazuje delegáta, který porušuje pravidla. V [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] například komentáře popisují, jak upravte příklad tak, že splňují pravidla. Pro příklad jazyka C# následuje příklad, který ukazuje změny kódu.

 [!code-vb[FxCop.Design.CustomEventHandler#1](../code-quality/codesnippet/VisualBasic/ca1003-use-generic-event-handler-instances_1.vb)]
 [!code-csharp[FxCop.Design.CustomEventHandler#1](../code-quality/codesnippet/CSharp/ca1003-use-generic-event-handler-instances_1.cs)]

## <a name="example"></a>Příklad
 Následující příklad odebere z předchozího příkladu, který splňuje pravidlo a nahradí jeho použití v deklaraci delegáta `ClassThatRaisesEvent` a `ClassThatHandlesEvent` metody pomocí <xref:System.EventHandler%601?displayProperty=fullName> delegovat.

 [!code-csharp[FxCop.Design.GenericEventHandler#1](../code-quality/codesnippet/CSharp/ca1003-use-generic-event-handler-instances_2.cs)]

## <a name="related-rules"></a>Související pravidla
 [CA1005: Vyhněte se nadbytečným parametrům na obecných typech](../code-quality/ca1005-avoid-excessive-parameters-on-generic-types.md)

 [CA1010: Kolekce musí implementovat obecné rozhraní](../code-quality/ca1010-collections-should-implement-generic-interface.md)

 [CA1000: Nedeklarujte statické členy v obecných typech](../code-quality/ca1000-do-not-declare-static-members-on-generic-types.md)

 [CA1002: Nezveřejňujte obecné seznamy](../code-quality/ca1002-do-not-expose-generic-lists.md)

 [CA1006: Nevnořujte obecné typy v signaturách členu](../code-quality/ca1006-do-not-nest-generic-types-in-member-signatures.md)

 [CA1004: Obecné metody by měly poskytnout parametr typu](../code-quality/ca1004-generic-methods-should-provide-type-parameter.md)

 [CA1007: Použijte obecné typy, kde je to vhodné](../code-quality/ca1007-use-generics-where-appropriate.md)

## <a name="see-also"></a>Viz také:

- [Obecné typy](/dotnet/csharp/programming-guide/generics/index)