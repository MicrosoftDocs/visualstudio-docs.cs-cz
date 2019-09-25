---
title: 'CA2104: Nedeklarujte proměnlivé odkazové typy jen pro čtení'
ms.date: 11/01/2018
ms.topic: reference
f1_keywords:
- DoNotDeclareReadOnlyMutableReferenceTypes
- CA2104
helpviewer_keywords:
- CA2104
- DoNotDeclareReadOnlyMutableReferenceTypes
ms.assetid: 81b83ee5-4db5-4be0-9f8d-90b53894ec3b
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CPP
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 8f4f165b4b00f46b478907c9affca672b4c7f113
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/24/2019
ms.locfileid: "71232958"
---
# <a name="ca2104-do-not-declare-read-only-mutable-reference-types"></a>CA2104: Nedeklaruje proměnlivé odkazové typy pouze pro čtení

|||
|-|-|
|TypeName|DoNotDeclareReadOnlyMutableReferenceTypes|
|CheckId|CA2104|
|Kategorie|Microsoft.Security|
|Zásadní změna|Nenarušující|

> [!NOTE]
> Pravidlo CA2104 je zastaralé a v budoucí verzi sady Visual Studio bude odstraněno. Neimplementuje se jako [analyzátor](roslyn-analyzers-overview.md) kvůli složitější analýze, která je nutná k určení skutečného neměnnosti typu.

## <a name="cause"></a>příčina

Externě viditelný typ obsahuje externě viditelné pole měnitelného referenčního typu, které je určeno jen pro čtení.

## <a name="rule-description"></a>Popis pravidla

Měnitelný typ je typ, jehož instanční data lze upravit. <xref:System.Text.StringBuilder?displayProperty=fullName> Třída je příkladem proměnlivého typu odkazu. Obsahuje členy, které mohou změnit hodnotu instance třídy. Příkladem neměnného typu odkazu je <xref:System.String?displayProperty=fullName> třída. Po vytvoření instance se její hodnota může nikdy změnit.

Modifikátor jen pro čtení ([jen](/dotnet/csharp/language-reference/keywords/readonly) pro čtení C#v, [ReadOnly](/dotnet/visual-basic/language-reference/modifiers/readonly) v Visual Basic a [const](/cpp/cpp/const-cpp) v C++) pro pole typu odkazu (nebo ukazatel v C++) zabraňuje tomu, aby se pole nahradilo jinou instancí typu odkazu. Modifikátor však nebrání změně dat instance v poli pomocí typu odkazu.

Toto pravidlo může nechtěně Zobrazit porušení typu, který je ve skutečnosti neměnný. V takovém případě je bezpečné potlačit upozornění.

Pole polí jen pro čtení jsou z tohoto pravidla vyjmuta, [ale místo toho způsobí porušení CA2105: Pole polí by nemělo být](../code-quality/ca2105-array-fields-should-not-be-read-only.md) pravidlem jen pro čtení.

## <a name="how-to-fix-violations"></a>Jak opravit porušení

Chcete-li opravit porušení tohoto pravidla, odeberte modifikátor jen pro čtení nebo, pokud je zásadní změna přijatelná, nahraďte pole neproměnlivým typem.

## <a name="when-to-suppress-warnings"></a>Kdy potlačit upozornění

Pokud je typ pole neměnný, je bezpečné potlačit upozornění od tohoto pravidla.

## <a name="example"></a>Příklad

Následující příklad ukazuje deklaraci pole, která způsobuje porušení tohoto pravidla:

[!code-cpp[FxCop.Security.MutableReferenceTypes#1](../code-quality/codesnippet/CPP/ca2104-do-not-declare-read-only-mutable-reference-types_1.cpp)]
[!code-csharp[FxCop.Security.MutableReferenceTypes#1](../code-quality/codesnippet/CSharp/ca2104-do-not-declare-read-only-mutable-reference-types_1.cs)]
[!code-vb[FxCop.Security.MutableReferenceTypes#1](../code-quality/codesnippet/VisualBasic/ca2104-do-not-declare-read-only-mutable-reference-types_1.vb)]