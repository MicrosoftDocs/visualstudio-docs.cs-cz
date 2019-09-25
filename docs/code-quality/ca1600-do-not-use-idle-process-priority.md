---
title: 'CA1600: Nepoužívejte prioritu nečinného procesu'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- DoNotUseIdleProcessPriority
- CA1600
helpviewer_keywords:
- CA1600
- DoNotUseIdleProcessPriority
ms.assetid: 9b0d073b-78b6-41be-8ef3-14692a735283
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 686929471ee8b6b5d1896f61bcbcd97a59135462
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/24/2019
ms.locfileid: "71234369"
---
# <a name="ca1600-do-not-use-idle-process-priority"></a>CA1600: Nepoužívejte prioritu nečinného procesu

|||
|-|-|
|TypeName|DoNotUseIdleProcessPriority|
|CheckId|CA1600|
|Kategorie|Microsoft.Mobility|
|Zásadní změna|Narušující|

## <a name="cause"></a>příčina
Toto pravidlo nastane, pokud jsou procesy nastaveny `ProcessPriorityClass.Idle`na.

## <a name="rule-description"></a>Popis pravidla
Nenastavujte prioritu procesu na Neaktivní. Procesy, které `System.Diagnostics.ProcessPriorityClass.Idle` budou zabírat procesor, pokud by jinak byly nečinné, a zablokují proto pohotovostní režim.

## <a name="how-to-fix-violations"></a>Jak opravit porušení
Nastavte procesy na `ProcessPriorityClass.BelowNormal`.

## <a name="when-to-suppress-warnings"></a>Kdy potlačit upozornění
Toto pravidlo by mělo být potlačeno pouze v případě, že je vyžadována priorita nečinného procesu a je možné bezpečně ignorovat požadavky na mobilitu.