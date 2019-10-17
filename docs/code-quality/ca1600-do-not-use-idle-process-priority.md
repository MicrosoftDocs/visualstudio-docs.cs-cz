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
ms.openlocfilehash: 2075918672452e222ba4becae915712ba20ff0d0
ms.sourcegitcommit: 485ffaedb1ade71490f11cf05962add1718945cc
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/16/2019
ms.locfileid: "72440026"
---
# <a name="ca1600-do-not-use-idle-process-priority"></a>CA1600: Nepoužívejte prioritu nečinného procesu

|||
|-|-|
|TypeName|DoNotUseIdleProcessPriority|
|CheckId|CA1600|
|Kategorie|Microsoft. mobility|
|Zásadní změna|Narušující|

## <a name="cause"></a>příčina
K tomuto pravidlu dochází, když jsou procesy nastavené na `ProcessPriorityClass.Idle`.

## <a name="rule-description"></a>Popis pravidla
Nenastavujte prioritu procesu na Neaktivní. Procesy, které mají `System.Diagnostics.ProcessPriorityClass.Idle`, budou CPU zabírat, pokud by jinak byly nečinné, a zablokují proto úsporný režim.

## <a name="how-to-fix-violations"></a>Jak opravit porušení
Nastavte procesy na `ProcessPriorityClass.BelowNormal`.

## <a name="when-to-suppress-warnings"></a>Kdy potlačit upozornění
Toto pravidlo by mělo být potlačeno pouze v případě, že je vyžadována priorita nečinného procesu a je možné bezpečně ignorovat požadavky na mobilitu.
