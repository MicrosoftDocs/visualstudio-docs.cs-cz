---
title: 'CA1034: Vnořené typy by neměly být viditelné'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- NestedTypesShouldNotBeVisible
- CA1034
helpviewer_keywords:
- NestedTypesShouldNotBeVisible
- CA1034
ms.assetid: e9789a2c-2540-42a1-8705-ae7104011194
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CPP
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: ead932af202bd1a44464025a1b09baa698acb7b1
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/24/2019
ms.locfileid: "71236039"
---
# <a name="ca1034-nested-types-should-not-be-visible"></a>CA1034: Vnořené typy by neměly být viditelné

|||
|-|-|
|TypeName|NestedTypesShouldNotBeVisible|
|CheckId|CA1034|
|Kategorie|Microsoft.Design|
|Zásadní změna|Narušující|

## <a name="cause"></a>příčina

Externě viditelný typ obsahuje deklaraci externě viditelného typu. Vnořené výčty a chráněné typy jsou z tohoto pravidla vyloučeny.

## <a name="rule-description"></a>Popis pravidla
Vnořený typ je typ deklarovaný v oboru jiného typu. Vnořené typy jsou užitečné pro zapouzdření údajů o privátní implementaci nadřazeného typu. Jsou-li vnořené typy používány za tímto účelem, neměly by být externě viditelné.

Nepoužívejte externě viditelné vnořené typy pro logické seskupení nebo pro zamezení kolizí názvů; místo toho použijte obory názvů.

Vnořené typy zahrnují pojem přístupnost členů, které někteří programátoré nerozumí jasně.

Chráněné typy lze použít v podtřídách a vnořených typech ve scénářích přizpůsobení předem.

## <a name="how-to-fix-violations"></a>Jak opravit porušení
Pokud nechcete, aby byl vnořený typ externě viditelný, změňte přístupnost typu. V opačném případě odeberte vnořený typ z jeho nadřazeného typu. Pokud je účel vnoření zařazen do kategorie vnořeného typu, použijte místo toho obor názvů k vytvoření hierarchie.

## <a name="when-to-suppress-warnings"></a>Kdy potlačit upozornění
Nepotlačujte upozornění na toto pravidlo.

## <a name="example"></a>Příklad
Následující příklad ukazuje typ, který je v rozporu s pravidlem.

[!code-cpp[FxCop.Design.NestedTypes#1](../code-quality/codesnippet/CPP/ca1034-nested-types-should-not-be-visible_1.cpp)]
[!code-csharp[FxCop.Design.NestedTypes#1](../code-quality/codesnippet/CSharp/ca1034-nested-types-should-not-be-visible_1.cs)]
[!code-vb[FxCop.Design.NestedTypes#1](../code-quality/codesnippet/VisualBasic/ca1034-nested-types-should-not-be-visible_1.vb)]