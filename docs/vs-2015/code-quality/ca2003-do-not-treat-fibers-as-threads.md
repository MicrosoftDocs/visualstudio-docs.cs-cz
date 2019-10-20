---
title: 'CA2003: nepovažujte vlákna za vlákna | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2003
- DoNotTreatFibersAsThreads
helpviewer_keywords:
- CA2003
- DoNotTreatFibersAsThreads
ms.assetid: 15398fb1-f384-4bcc-ad93-00e1c0fa9ddf
caps.latest.revision: 18
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 943b52f9703e60f14756bde97ce6f27c0c6f5296
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72672506"
---
# <a name="ca2003-do-not-treat-fibers-as-threads"></a>CA2003: Rozlišujte vlákénka od vláken
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|DoNotTreatFibersAsThreads|
|CheckId|CA2003|
|Kategorie|Microsoft.Reliability|
|Narušující změna|Nenarušující|

## <a name="cause"></a>příčina
 Spravované vlákno je považováno za vlákno Win32.

## <a name="rule-description"></a>Popis pravidla
 Nepředpokládat, že spravované vlákno je vlákno Win32. Je to vlákno. Modul CLR (Common Language Runtime) spustí spravovaná vlákna jako vlákna v kontextu reálných vláken, která vlastní SQL. Tato vlákna lze sdílet napříč doménami aplikace a dokonce i databázemi v procesu SQL Server. Použití spravovaného úložiště thread local bude fungovat, ale nepoužíváte nespravované úložiště thread local nebo předpokládáte, že váš kód bude spuštěn v aktuálním vláknu operačního systému. Neměňte nastavení, jako je národní prostředí vlákna. Nevolejte CreateCriticalSection ani CreateMutex prostřednictvím P/Invoke, protože vyžadují, aby vlákno, které vstupuje na zámek, také ukončilo zámek. Vzhledem k tomu, že se nejedná o případ použití vláken, kritické oddíly Win32 a mutex budou v SQL zbytečné. Většinu stavu můžete bezpečně použít ve spravovaném objektu System. Thread. To zahrnuje spravované thread local úložiště a jazykovou verzi aktuálního uživatelského rozhraní (UI) vlákna. Nicméně pro účely programovacího modelu nebudete moci změnit aktuální jazykovou verzi vlákna při použití SQL; Tato akce bude vynutila nové oprávnění.

## <a name="how-to-fix-violations"></a>Jak vyřešit porušení
 Prověřte použití vláken a odpovídajícím způsobem změňte kód.

## <a name="when-to-suppress-warnings"></a>Kdy potlačit upozornění
 Toto pravidlo byste neměli potlačit.
