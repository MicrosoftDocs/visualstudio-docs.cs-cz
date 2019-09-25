---
title: 'CA2004: Odeberte volání GC.KeepAlive'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- RemoveCallsToGCKeepAlive
- CA2004
helpviewer_keywords:
- RemoveCallsToGCKeepAlive
- CA2004
ms.assetid: bc543b5b-23eb-4b45-abc2-9325cd254ac2
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c495357b837c4ae10d4dfe1e25237d6caaefcc4c
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/24/2019
ms.locfileid: "71233115"
---
# <a name="ca2004-remove-calls-to-gckeepalive"></a>CA2004: Odeberte volání GC.KeepAlive

|||
|-|-|
|TypeName|RemoveCallsToGCKeepAlive|
|CheckId|CA2004|
|Kategorie|Microsoft.Reliability|
|Zásadní změna|Nenarušující|

## <a name="cause"></a>příčina
Třídy používají `SafeHandle` `GC.KeepAlive`, ale stále obsahují volání.

## <a name="rule-description"></a>Popis pravidla
Pokud převádíte na `SafeHandle` použití, odeberte všechna `GC.KeepAlive` volání (Object). V takovém případě třídy by neměly být volány `GC.KeepAlive`, za předpokladu, že nemají finalizační metodu, ale spoléhají `SafeHandle` na dokončení popisovače operačního systému pro ně.  I když náklady na `GC.KeepAlive` zanechání v volání může být zanedbatelné na základě výkonu, vnímání, že `GC.KeepAlive` volání je buď nezbytné, nebo dostačující k vyřešení potíží při životnosti, která již nemusí existovat, způsobuje, že by se kód obtížnější vést.

## <a name="how-to-fix-violations"></a>Jak opravit porušení
Odeberte volání `GC.KeepAlive`.

## <a name="when-to-suppress-warnings"></a>Kdy potlačit upozornění
Toto upozornění můžete potlačit pouze v případě, že není technicky správné převést `SafeHandle` na využití ve vaší třídě.