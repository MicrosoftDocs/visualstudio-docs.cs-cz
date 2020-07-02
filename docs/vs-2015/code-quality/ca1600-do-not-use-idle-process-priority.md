---
title: 'CA1600: Nepoužívejte prioritu nečinného procesu | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- DoNotUseIdleProcessPriority
- CA1600
helpviewer_keywords:
- CA1600
- DoNotUseIdleProcessPriority
ms.assetid: 9b0d073b-78b6-41be-8ef3-14692a735283
caps.latest.revision: 17
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 3f6233136dcf7f1db5d622a02419d33e0eedacf5
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/30/2020
ms.locfileid: "85545675"
---
# <a name="ca1600-do-not-use-idle-process-priority"></a>CA1600: Nepoužívejte prioritu nečinného procesu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Položka|Hodnota|
|-|-|
|TypeName|DoNotUseIdleProcessPriority|
|CheckId|CA1600|
|Kategorie|Microsoft. mobility|
|Narušující změna|Narušující|

## <a name="cause"></a>Příčina
 Toto pravidlo nastane, pokud jsou procesy nastaveny na `ProcessPriorityClass.Idle` .

## <a name="rule-description"></a>Popis pravidla
 Nenastavujte prioritu procesu na Neaktivní. Procesy, které `System.Diagnostics.ProcessPriorityClass.Idle` budou zabírat procesor, pokud by jinak byly nečinné, a zablokují proto pohotovostní režim.

## <a name="how-to-fix-violations"></a>Jak vyřešit porušení
 Nastavte procesy na `ProcessPriorityClass.BelowNormal` .

## <a name="when-to-suppress-warnings"></a>Kdy potlačit upozornění
 Toto pravidlo by mělo být potlačeno pouze v případě, že je vyžadována priorita nečinného procesu a je možné bezpečně ignorovat požadavky na mobilitu.
