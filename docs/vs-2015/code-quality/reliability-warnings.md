---
title: Upozornění spolehlivosti | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- vs.codeanalysis.reliabilityrules
helpviewer_keywords:
- warnings, reliability
- reliability warnings
- managed code analysis warnings, reliability warnings
ms.assetid: 77886846-10a2-4585-968a-7eb60ebe07e8
caps.latest.revision: 23
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 250eb10581858534ec6325a1bfb61d84bddac05a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "72603977"
---
# <a name="reliability-warnings"></a>Upozornění spolehlivosti
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Upozornění na spolehlivost podporují spolehlivost knihovny a aplikace, jako je třeba správné využití paměti a vlákna.

## <a name="in-this-section"></a>V tomto oddílu

|Pravidlo|Popis|
|----------|-----------------|
|[CA2000: Uvolňujte objekty před ztrátou oboru](../code-quality/ca2000-dispose-objects-before-losing-scope.md)|Protože může dojít k mimořádné události, která zabrání spuštění destruktoru objektu, měl by být objekt explicitně uvolněn předtím, než se všechny odkazy na něj dostanou mimo rozsah.|
|[CA2001: Vyhněte se volání problematických metod](../code-quality/ca2001-avoid-calling-problematic-methods.md)|Člen volá potencionálně nebezpečnou nebo problematickou metodu.|
|[CA2002: Nepoužívejte zámky u objektů se slabou identitou](../code-quality/ca2002-do-not-lock-on-objects-with-weak-identity.md)|Objekt má slabou identitu, pokud k němu lze přímo přistupovat přes hranice aplikační domény. Vlákno, které se pokouší získat zámek na objekt se slabou identitou, může být blokováno jiným vláknem v jiné aplikační doméně, které má zámek na stejný objekt.|
|[CA2003: Nezacházejte s vlákénky jako s vlákny](../code-quality/ca2003-do-not-treat-fibers-as-threads.md)|Spravované vlákno je považováno za vlákno Win32.|
|[CA2004: Odeberte volání GC.KeepAlive](../code-quality/ca2004-remove-calls-to-gc-keepalive.md)|Pokud převádíte na použití SafeHandle, odeberte všechna volání GC. Naživu (objekt). V takovém případě třídy by neměly muset volat GC. Udržení naživu za předpokladu, že nemají finalizační metodu, ale spoléhají na SafeHandle k finalizaci popisovače operačního systému pro ně.|
|[CA2006: Použijte SafeHandle k zapouzdření nativních prostředků](../code-quality/ca2006-use-safehandle-to-encapsulate-native-resources.md)|Použití IntPtr ve spravovaném kódu může znamenat možný problém zabezpečení a spolehlivosti. Všechna použití IntPtr musí být přezkoumána za účelem určení, zda je použití SafeHandle (nebo podobné technologie) na tomto místě vyžadováno.|
