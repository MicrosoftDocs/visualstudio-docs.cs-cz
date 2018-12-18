---
title: 'CA2003: Rozlišujte vlákénka od vláken | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- CA2003
- DoNotTreatFibersAsThreads
helpviewer_keywords:
- CA2003
- DoNotTreatFibersAsThreads
ms.assetid: 15398fb1-f384-4bcc-ad93-00e1c0fa9ddf
caps.latest.revision: 18
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: f3d72e052decc5a26dd134aafcaac8aba6af699f
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49810915"
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
 Spravovaným vláknem se zachází jako vlákno Win32.

## <a name="rule-description"></a>Popis pravidla
 Nepředpokládejte, že se že spravovaným vláknem se vlákno Win32. Je vlákno. Common language runtime (CLR) se spustí spravovaná vlákna, jako jsou vlákna v kontextu reálného vlákna, které jsou vlastněny SQL. Tato vlákna mohou být sdíleny napříč objektů třídy AppDomains a dokonce i databází v procesu serveru SQL Server. Pomocí spravovaného vlákna, místní úložiště bude fungovat, ale nemusí používat místní úložiště nespravovaného vlákna nebo se předpokládá, že váš kód poběží v aktuálním vlákně operačního systému znovu. Neměňte nastavení, jako je národní prostředí vlákna. Nevolejte CreateCriticalSection nebo CreateMutex – prostřednictvím P/Invoke, protože vyžadují vlákna, která se zadá zámku musí také ukončení uzamčení. Vzhledem k tomu, že to nebude tak při použití vlákének, budou mít kritických oddílů Win32 a vzájemně vyloučené přístupy zbytečné v SQL. Většina stavu může bezpečně používat na spravovaný objekt System.Thread. Jedná se o místním úložišti spravované vlákno a aktuální uživatelské rozhraní (UI) jazykovou verzi vlákna. Ale pro programovací model důvody, nebudete moct změnit aktuální jazykovou verzi vlákna, při použití SQL; Tím se vynutí prostřednictvím nové oprávnění.

## <a name="how-to-fix-violations"></a>Jak vyřešit porušení
 Zkontrolujte vaše použití vláken a odpovídajícím způsobem měnit kód.

## <a name="when-to-suppress-warnings"></a>Kdy potlačit upozornění
 Toto pravidlo by neměl potlačit.



