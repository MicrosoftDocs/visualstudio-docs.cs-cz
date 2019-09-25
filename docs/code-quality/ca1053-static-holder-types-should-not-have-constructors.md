---
title: 'CA1053: Statické typy vlastníků by neměly mít konstruktory'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- StaticHolderTypesShouldNotHaveConstructors
- CA1053
helpviewer_keywords:
- CA1053
- StaticHolderTypesShouldNotHaveConstructors
ms.assetid: 10302b9a-fa5e-4935-a06a-513d9600f613
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 44bdb8c12b48a983b88e6a035fc1522856b306be
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/24/2019
ms.locfileid: "71235588"
---
# <a name="ca1053-static-holder-types-should-not-have-default-constructors"></a>CA1053: Typy statických držitelů by neměly mít výchozí konstruktory.

|||
|-|-|
|TypeName|StaticHolderTypesShouldNotHaveConstructors|
|CheckId|CA1053|
|Kategorie|Microsoft.Design|
|Zásadní změna|Narušující|

> [!NOTE]
> Pravidlo CA1053 je kombinované do [CA1052: Statické typy držitelů by měly](ca1052-static-holder-types-should-be-sealed.md) být zapečetěné v [analyzátorech FxCop](fxcop-analyzers.yml).

## <a name="cause"></a>příčina

Veřejný nebo vnořený veřejný typ deklaruje pouze statické členy a má výchozí konstruktor.

## <a name="rule-description"></a>Popis pravidla

Výchozí konstruktor není potřebný, protože volání statických členů nevyžaduje instanci typu. Vzhledem k tomu, že typ nemá nestatické členy, vytvoření instance neposkytuje přístup k žádnému z členů typu.

## <a name="how-to-fix-violations"></a>Jak opravit porušení

Chcete-li opravit porušení tohoto pravidla, odeberte výchozí konstruktor.

## <a name="when-to-suppress-warnings"></a>Kdy potlačit upozornění

Nepotlačujte upozornění na toto pravidlo. Přítomnost výchozího konstruktoru naznačuje, že typ není statický typ.