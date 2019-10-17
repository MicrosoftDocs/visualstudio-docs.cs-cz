---
title: 'CA1047: Nedeklarujte chráněné členy v zapečetěných typech'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- DoNotDeclareProtectedMembersInSealedTypes
- CA1047
helpviewer_keywords:
- CA1047
- DoNotDeclareProtectedMembersInSealedTypes
ms.assetid: 829033b5-a9d8-4f26-a719-45494c9dd035
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: b55da06cdaee07e0d5c30dc6c5220ef2d50f8d0b
ms.sourcegitcommit: 485ffaedb1ade71490f11cf05962add1718945cc
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/16/2019
ms.locfileid: "72449101"
---
# <a name="ca1047-do-not-declare-protected-members-in-sealed-types"></a>CA1047: Nedeklarujte chráněné členy v zapečetěných typech

|||
|-|-|
|TypeName|DoNotDeclareProtectedMembersInSealedTypes|
|CheckId|CA1047|
|Kategorie|Microsoft. Design|
|Zásadní změna|Nenarušující|

## <a name="cause"></a>příčina
Veřejný typ je `sealed` (`NotInheritable` v jazyce Visual Basic) a deklaruje chráněný člen nebo chráněný vnořený typ. Toto pravidlo neoznamuje porušení pro metody @no__t 0, které musí následovat po tomto vzoru.

## <a name="rule-description"></a>Popis pravidla
Typy deklarují chráněné členy, aby k nim odvozené typy mohly přistupovat nebo je přepisovat. Podle definice nemůžete dědit ze zapečetěného typu, což znamená, že nelze volat chráněné metody pro zapečetěné typy.

C# Kompilátor vydá upozornění pro tuto chybu.

## <a name="how-to-fix-violations"></a>Jak opravit porušení
Chcete-li opravit porušení tohoto pravidla, změňte úroveň přístupu člena na hodnotu Private nebo zajistěte, aby byl typ dědičný.

## <a name="when-to-suppress-warnings"></a>Kdy potlačit upozornění
Nepotlačujte upozornění na toto pravidlo. Ponechání typu v aktuálním stavu může způsobit problémy s údržbou a neposkytuje žádné výhody.

## <a name="example"></a>Příklad
Následující příklad ukazuje typ, který je v rozporu s tímto pravidlem.

[!code-vb[FxCop.Design.SealedNoProtected#1](../code-quality/codesnippet/VisualBasic/ca1047-do-not-declare-protected-members-in-sealed-types_1.vb)]
[!code-csharp[FxCop.Design.SealedNoProtected#1](../code-quality/codesnippet/CSharp/ca1047-do-not-declare-protected-members-in-sealed-types_1.cs)]
