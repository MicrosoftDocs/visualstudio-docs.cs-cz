---
title: 'CA1506: Vyhněte se nadměrnému párování tříd'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- AvoidExcessiveClassCoupling
- CA1506
helpviewer_keywords:
- AvoidExcessiveClassCoupling
- CA1506
ms.assetid: 9f0943c0-e802-4e3f-8798-2ab8653ddc80
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 1721fd52c00c5b312c88f19d48b668b12d28f050
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/24/2019
ms.locfileid: "71234485"
---
# <a name="ca1506-avoid-excessive-class-coupling"></a>CA1506: Vyhněte se nadměrnému párování tříd

|||
|-|-|
|TypeName|AvoidExcessiveClassCoupling|
|CheckId|CA1506|
|Kategorie|Microsoft. udržovatelnost|
|Zásadní změna|Narušující|

## <a name="cause"></a>příčina

Typ nebo metoda jsou spojeny s mnoha dalšími typy.

## <a name="rule-description"></a>Popis pravidla

Toto pravidlo měří párování tříd podle počtu jedinečných odkazů na typ, které typ nebo metoda obsahuje.

Typy a metody s vysokým stupněm párování tříd může být obtížné udržovat. Je dobrým zvykem, že máte typy a metody, které mají slabý spoj a vysokou soudržnost.

## <a name="how-to-fix-violations"></a>Jak opravit porušení

Chcete-li toto porušení opravit, zkuste změnit návrh typu nebo metody tak, aby se snížil počet typů, na které je spojena.

## <a name="when-to-suppress-warnings"></a>Kdy potlačit upozornění

Vylučte toto upozornění, pokud je typ nebo metoda považována za udržovatelnou bez ohledu na jejich velký počet závislostí na jiných typech.

## <a name="see-also"></a>Viz také:

- [Upozornění udržovatelnosti](../code-quality/maintainability-warnings.md)
- [Měření složitosti a udržovatelnosti spravovaného kódu](../code-quality/code-metrics-values.md)