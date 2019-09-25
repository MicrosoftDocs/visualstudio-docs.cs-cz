---
title: 'CA2222: Nesnižujte viditelnost zděděného členu'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- DoNotDecreaseInheritedMemberVisibility
- CA2222
helpviewer_keywords:
- DoNotDecreaseInheritedMemberVisibility
- CA2222
ms.assetid: 066c8675-381f-43cc-956c-d757cc494028
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: c737a30569ab4cd59931a3fca0e500ebe96e62de
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/24/2019
ms.locfileid: "71230985"
---
# <a name="ca2222-do-not-decrease-inherited-member-visibility"></a>CA2222: Nesnižujte viditelnost zděděného členu

|||
|-|-|
|TypeName|DoNotDecreaseInheritedMemberVisibility|
|CheckId|CA2222|
|Kategorie|Microsoft.Usage|
|Zásadní změna|Nenarušující|

## <a name="cause"></a>příčina

Soukromá metoda v nezapečetěném typu má signaturu, která je shodná s veřejnou metodou deklarovanou v základním typu. Soukromá metoda není finální.

## <a name="rule-description"></a>Popis pravidla

Neměňte modifikátor přístupu pro zděděné členy. Změna zděděného členu na soukromý nezabrání volajícím v přístupu k implementaci základní třídy dané metody. Pokud je člen vytvořen jako soukromý a typ je nezapečetěný, dědění typů může zavolat poslední veřejnou implementaci metody v hierarchii dědičnosti. Pokud je nutné změnit modifikátor přístupu, buď by měla být metoda označena jako konečná, nebo její typ by měl být zapečetěný, aby se zabránilo přepsání metody.

## <a name="how-to-fix-violations"></a>Jak opravit porušení

Chcete-li opravit porušení tohoto pravidla, změňte přístup na neprivátní. Případně, pokud je váš programovací jazyk podporován, můžete nastavit metodu jako konečnou.

## <a name="when-to-suppress-warnings"></a>Kdy potlačit upozornění

Nepotlačujte upozornění na toto pravidlo.

## <a name="example"></a>Příklad

Následující příklad ukazuje typ, který je v rozporu s tímto pravidlem.

[!code-vb[FxCop.Usage.InheritedPublic#1](../code-quality/codesnippet/VisualBasic/ca2222-do-not-decrease-inherited-member-visibility_1.vb)]
[!code-csharp[FxCop.Usage.InheritedPublic#1](../code-quality/codesnippet/CSharp/ca2222-do-not-decrease-inherited-member-visibility_1.cs)]