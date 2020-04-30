---
title: Upozornění spolehlivosti
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.codeanalysis.reliabilityrules
helpviewer_keywords:
- warnings, reliability
- reliability warnings
- managed code analysis warnings, reliability warnings
ms.assetid: 77886846-10a2-4585-968a-7eb60ebe07e8
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c4b888dbbe7a26e5ff333ec39aa0fdfcec90b429
ms.sourcegitcommit: da5ebc29544fdbdf625ab4922c9777faf2bcae4a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/29/2020
ms.locfileid: "82586211"
---
# <a name="reliability-warnings"></a>Upozornění spolehlivosti

Upozornění na spolehlivost podporují spolehlivost knihovny a aplikace, jako je třeba správné využití paměti a vlákna. Mezi pravidla spolehlivosti patří:

|Pravidlo|Popis|
|----------|-----------------|
|[CA2000: Uvolňujte objekty před ztrátou oboru](../code-quality/ca2000.md)|Protože může dojít k mimořádné události, která zabrání spuštění destruktoru objektu, měl by být objekt explicitně uvolněn předtím, než se všechny odkazy na něj dostanou mimo rozsah.|
|[CA2001: Vyhněte se volání problematických metod](../code-quality/ca2001.md)|Člen volá potencionálně nebezpečnou nebo problematickou metodu.|
|[CA2002: Nepoužívejte zámky u objektů se slabou identitou](../code-quality/ca2002.md)|Objekt má slabou identitu, pokud k němu lze přímo přistupovat přes hranice aplikační domény. Vlákno, které se pokouší získat zámek na objekt se slabou identitou, může být blokováno jiným vláknem v jiné aplikační doméně, které má zámek na stejný objekt.|
|[CA2003: Nezacházejte s vlákénky jako s vlákny](../code-quality/ca2003.md)|Spravované vlákno je považováno za vlákno Win32.|
|[CA2004: Odeberte volání GC.KeepAlive](../code-quality/ca2004.md)|Pokud převádíte na použití SafeHandle, odeberte všechna volání GC. Naživu (objekt). V takovém případě třídy by neměly muset volat GC. Udržení naživu za předpokladu, že nemají finalizační metodu, ale spoléhají na SafeHandle k finalizaci popisovače operačního systému pro ně.|
|[CA2006: Použijte SafeHandle k zapouzdření nativních prostředků](../code-quality/ca2006.md)|Použití IntPtr ve spravovaném kódu může znamenat možný problém zabezpečení a spolehlivosti. Všechna použití IntPtr musí být přezkoumána za účelem určení, zda je použití SafeHandle (nebo podobné technologie) na tomto místě vyžadováno.|
|[CA2007: Nečekejte přímo na úlohu](../code-quality/ca2007.md)|Asynchronní metoda [čeká](/dotnet/csharp/language-reference/keywords/await) <xref:System.Threading.Tasks.Task> přímo.|
|[CA2009: Nevolejte ToImmutableCollection na hodnotu neměnnécollection.](../code-quality/ca2009.md)|`ToImmutable`Metoda byla nutně volána pro neproměnlivou kolekci z <xref:System.Collections.Immutable> oboru názvů.|
