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
ms.openlocfilehash: ff42cc2b8543fe8e1cf980a3574ae15922febf9b
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/30/2020
ms.locfileid: "85521040"
---
# <a name="ca2104-do-not-declare-read-only-mutable-reference-types"></a>CA2104: Nedeklaruje proměnlivé odkazové typy pouze pro čtení
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Položka|Hodnota|
|-|-|
|TypeName|DoNotDeclareReadOnlyMutableReferenceTypes|
|CheckId|CA2104|
|Kategorie|Microsoft.Security|
|Narušující změna|Nenarušující|

## <a name="cause"></a>Příčina
 Externě viditelný typ obsahuje externě viditelné pole měnitelného referenčního typu, které je určeno jen pro čtení.

## <a name="rule-description"></a>Popis pravidla
 Měnitelný typ je typ, jehož instanční data lze upravit. <xref:System.Text.StringBuilder?displayProperty=fullName>Třída je příkladem proměnlivého typu odkazu. Obsahuje členy, které mohou změnit hodnotu instance třídy. Příkladem neměnného typu odkazu je <xref:System.String?displayProperty=fullName> Třída. Po vytvoření instance se její hodnota může nikdy změnit.

 Modifikátor jen pro čtení ([jen](https://msdn.microsoft.com/library/2f8081f6-0de2-4903-898d-99696c48d2f4) pro čtení v jazyce C#, [ReadOnly](https://msdn.microsoft.com/library/e868185d-6142-4359-a2fd-a7965cadfce8) v [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] a [const](https://msdn.microsoft.com/library/b21c0271-1ad0-40a0-b21c-5e812bba0318) v jazyce c++) v poli referenčního typu (ukazatel v jazyce c++) brání tomu, aby se pole nahradilo jinou instancí typu odkazu. Modifikátor však nebrání změně dat instance v poli pomocí typu odkazu.

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
