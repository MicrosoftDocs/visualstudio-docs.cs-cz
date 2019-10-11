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
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: cb39bb5f59373f52d77c7cc5d13d12544d4c0314
ms.sourcegitcommit: 3e94d9fb6dc56fa8b23fbacd5d11cf8d6e7e18f1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/10/2019
ms.locfileid: "72252587"
---
# <a name="reliability-warnings"></a>Upozornění spolehlivosti

Upozornění na spolehlivost podporují spolehlivost knihovny a aplikace, jako je třeba správné využití paměti a vlákna. Mezi pravidla spolehlivosti patří:

|Pravidlo|Popis|
|----------|-----------------|
|@NO__T – 0CA2000: Uvolnění objektů před ztrátou rozsahu @ no__t-0|Protože může dojít k mimořádné události, která zabrání spuštění destruktoru objektu, měl by být objekt explicitně uvolněn předtím, než se všechny odkazy na něj dostanou mimo rozsah.|
|@NO__T – 0CA2001: Vyhněte se volání problematických metod @ no__t-0|Člen volá potencionálně nebezpečnou nebo problematickou metodu.|
|@NO__T – 0CA2002: Nepoužívejte zámky na objekty se slabou identitou @ no__t-0|Objekt má slabou identitu, pokud k němu lze přímo přistupovat přes hranice aplikační domény. Vlákno, které se pokouší získat zámek na objekt se slabou identitou, může být blokováno jiným vláknem v jiné aplikační doméně, které má zámek na stejný objekt.|
|@NO__T – 0CA2003: Nevažovat vlákna za vlákna @ no__t-0|Spravované vlákno je považováno za vlákno Win32.|
|@NO__T – 0CA2004: Odeberte volání GC. Udržení naživu @ no__t-0|Pokud převádíte na použití SafeHandle, odeberte všechna volání GC. Naživu (objekt). V takovém případě třídy by neměly muset volat GC. Udržení naživu za předpokladu, že nemají finalizační metodu, ale spoléhají na SafeHandle k finalizaci popisovače operačního systému pro ně.|
|@NO__T – 0CA2006: Použít SafeHandle k zapouzdření nativních prostředků @ no__t-0|Použití IntPtr ve spravovaném kódu může znamenat možný problém zabezpečení a spolehlivosti. Všechna použití IntPtr musí být přezkoumána za účelem určení, zda je použití SafeHandle (nebo podobné technologie) na tomto místě vyžadováno.|
|@NO__T – 0CA2007: Nečekat přímo na úlohu @ no__t-0|Asynchronní metoda [čeká](/dotnet/csharp/language-reference/keywords/await) přímo <xref:System.Threading.Tasks.Task>.|
