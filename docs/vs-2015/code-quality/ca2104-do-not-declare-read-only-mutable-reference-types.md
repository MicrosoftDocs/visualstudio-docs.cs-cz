---
title: 'CA2104: Nedeklaruje proměnlivé odkazové typy pouze pro čtení | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- DoNotDeclareReadOnlyMutableReferenceTypes
- CA2104
helpviewer_keywords:
- CA2104
- DoNotDeclareReadOnlyMutableReferenceTypes
ms.assetid: 81b83ee5-4db5-4be0-9f8d-90b53894ec3b
caps.latest.revision: 20
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: fd81f9ea250cd1592f755a2aa6cb3ca09280a533
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72666045"
---
# <a name="ca2104-do-not-declare-read-only-mutable-reference-types"></a>CA2104: Nedeklaruje proměnlivé odkazové typy pouze pro čtení
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|DoNotDeclareReadOnlyMutableReferenceTypes|
|CheckId|CA2104|
|Kategorie|Microsoft.Security|
|Narušující změna|Nenarušující|

## <a name="cause"></a>příčina
 Externě viditelný typ obsahuje externě viditelné pole měnitelného referenčního typu, které je určeno jen pro čtení.

## <a name="rule-description"></a>Popis pravidla
 Měnitelný typ je typ, jehož instanční data lze upravit. Třída <xref:System.Text.StringBuilder?displayProperty=fullName> je příkladem proměnlivého typu odkazu. Obsahuje členy, které mohou změnit hodnotu instance třídy. Příkladem neměnného typu odkazu je třída <xref:System.String?displayProperty=fullName>. Po vytvoření instance se její hodnota může nikdy změnit.

 Modifikátor jen pro čtení ([jen](https://msdn.microsoft.com/library/2f8081f6-0de2-4903-898d-99696c48d2f4) pro čtení C#v, [ReadOnly](https://msdn.microsoft.com/library/e868185d-6142-4359-a2fd-a7965cadfce8) v [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] a [const](https://msdn.microsoft.com/library/b21c0271-1ad0-40a0-b21c-5e812bba0318) v C++) v poli typu odkazu (ukazatel v C++) zabraňuje tomu, aby se pole nahradilo jinou instancí typu odkazu. Modifikátor však nebrání změně dat instance v poli pomocí typu odkazu.

 Pole polí jen pro čtení jsou z tohoto pravidla vyjmuta, ale místo toho způsobí porušení [pole CA2105: Array by nemělo být pravidlo jen pro čtení](../code-quality/ca2105-array-fields-should-not-be-read-only.md) .

## <a name="how-to-fix-violations"></a>Jak vyřešit porušení
 Chcete-li opravit porušení tohoto pravidla, odeberte modifikátor jen pro čtení nebo, pokud je zásadní změna přijatelná, nahraďte pole neproměnlivým typem.

## <a name="when-to-suppress-warnings"></a>Kdy potlačit upozornění
 Je bezpečné potlačit upozornění z tohoto pravidla, pokud je typ pole neměnný.

## <a name="example"></a>Příklad
 Následující příklad ukazuje deklaraci pole, která způsobuje porušení tohoto pravidla.

 [!code-cpp[FxCop.Security.MutableReferenceTypes#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Security.MutableReferenceTypes/cpp/FxCop.Security.MutableReferenceTypes.cpp#1)]
 [!code-csharp[FxCop.Security.MutableReferenceTypes#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.MutableReferenceTypes/cs/FxCop.Security.MutableReferenceTypes.cs#1)]
 [!code-vb[FxCop.Security.MutableReferenceTypes#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Security.MutableReferenceTypes/vb/FxCop.Security.MutableReferenceTypes.vb#1)]
