---
title: 'CA1004: Obecné metody by měly poskytnout parametr typu | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- CA1004
- GenericMethodsShouldProvideTypeParameter
helpviewer_keywords:
- GenericMethodsShouldProvideTypeParameter
- CA1004
ms.assetid: 38755f6a-fb45-4bf2-932e-0354ad826499
caps.latest.revision: 19
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 1e47276ad5be70308dc4c6e249204a65ef9f08b1
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49880205"
---
# <a name="ca1004-generic-methods-should-provide-type-parameter"></a>CA1004: Obecné metody by měly poskytnout parametr typu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|GenericMethodsShouldProvideTypeParameter|
|CheckId|CA1004|
|Kategorie|Microsoft.Design|
|Narušující změna|Narušující|

## <a name="cause"></a>příčina
 Předpis parametrů Obecné externě viditelná metoda obsahuje typy, které odpovídají všechny parametry typu metody.

## <a name="rule-description"></a>Popis pravidla
 Argument typu obecné metody je z argumentu typu předávaného metodě odvozen namísto explicitního určení argumentu typu. Má-li být odvozování povoleno, musí předpis parametrů obecné metody zahrnovat parametr stejného typu jako parametr typu metody. V tomto případě nemusí být argument typu zadán. Při použití odvození pro všechny parametry typu, je syntaxe volání obecných a neobecných metod je stejný jako. To zjednodušuje použití obecných metod.

## <a name="how-to-fix-violations"></a>Jak vyřešit porušení
 Chcete-li opravit porušení tohoto pravidla, změňte návrh tak, aby předpis parametrů obsahuje stejný typ pro každý parametr typu metody.

## <a name="when-to-suppress-warnings"></a>Kdy potlačit upozornění
 Nepotlačujte upozornění na toto pravidlo. Poskytuje obecné typy v syntaxi, která je snadno pochopitelný a snižuje čas, který je potřeba další informace a zvýší frekvence přijetí nové knihovny.

## <a name="example"></a>Příklad
 Následující příklad ukazuje syntaxi pro volání dvě obecné metody. Argument typu pro `InferredTypeArgument` odvozuje a argument typu pro `NotInferredTypeArgument` musí být explicitně určena.

 [!code-csharp[FxCop.Design.Inference#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.Inference/cs/FxCop.Design.Inference.cs#1)]
 [!code-vb[FxCop.Design.Inference#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.Inference/vb/FxCop.Design.Inference.vb#1)]

## <a name="related-rules"></a>Související pravidla
 [CA1005: Vyhněte se nadbytečným parametrům na obecných typech](../code-quality/ca1005-avoid-excessive-parameters-on-generic-types.md)

 [CA1010: Kolekce musí implementovat obecné rozhraní](../code-quality/ca1010-collections-should-implement-generic-interface.md)

 [CA1000: Nedeklarujte statické členy v obecných typech](../code-quality/ca1000-do-not-declare-static-members-on-generic-types.md)

 [CA1002: Nezveřejňujte obecné seznamy](../code-quality/ca1002-do-not-expose-generic-lists.md)

 [CA1006: Nevnořujte obecné typy v signaturách členu](../code-quality/ca1006-do-not-nest-generic-types-in-member-signatures.md)

 [CA1003: Použijte instance obecných obslužných rutin události](../code-quality/ca1003-use-generic-event-handler-instances.md)

 [CA1007: Použijte obecné typy, kde je to vhodné](../code-quality/ca1007-use-generics-where-appropriate.md)