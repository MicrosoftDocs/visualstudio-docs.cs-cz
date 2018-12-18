---
title: 'CA1048: Nedeklarujte virtuální členy v zapečetěných typech'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- DoNotDeclareVirtualMembersInSealedTypes
- CA1048
helpviewer_keywords:
- DoNotDeclareVirtualMembersInSealedTypes
- CA1048
ms.assetid: 5dcf4a30-6f98-48a8-b8cc-7b89ea757262
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 6cb38b089b432d65d74032b5ceb5ef820685557c
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49891918"
---
# <a name="ca1048-do-not-declare-virtual-members-in-sealed-types"></a>CA1048: Nedeklarujte virtuální členy v zapečetěných typech

|||
|-|-|
|TypeName|DoNotDeclareVirtualMembersInSealedTypes|
|CheckId|CA1048|
|Kategorie|Microsoft.Design|
|Narušující změna|Narušující|

## <a name="cause"></a>příčina
 Veřejný typ je zapečetěná a deklaruje metodu, která je oba směry `virtual` (`Overridable` v jazyce Visual Basic) a ne finální. Toto pravidlo nevytváří sestavu porušení pro typy delegátů, které musí postupovat podle tohoto vzoru.

## <a name="rule-description"></a>Popis pravidla
 Typy deklarují metody jako virtuální, aby odvozující typy mohly přepsat implementaci virtuální metody. Dle definice nelze dědit ze zapečetěného typu, že virtuální metoda u zapečetěného typu význam.

 Kompilátory jazyků Visual Basic a C# neumožňují typů pro toto pravidlo porušují.

## <a name="how-to-fix-violations"></a>Jak vyřešit porušení
 Chcete-li opravit porušení tohoto pravidla, zkontrolujte nevirtuální metodu nebo změňte typ odvoditelný.

## <a name="when-to-suppress-warnings"></a>Kdy potlačit upozornění
 Nepotlačujte upozornění na toto pravidlo. Opuštění typu v jejím aktuálním stavu může způsobit problémy s údržbou a nepřináší žádné výhody.

## <a name="example"></a>Příklad
 Následující příklad ukazuje typ, který porušuje tato pravidla.

 [!code-cpp[FxCop.Design.SealedVirtual#1](../code-quality/codesnippet/CPP/ca1048-do-not-declare-virtual-members-in-sealed-types_1.cpp)]