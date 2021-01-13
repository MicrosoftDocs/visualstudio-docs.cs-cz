---
title: Najít chybu volání při mnohokrát volání funkce
description: Podívejte se na techniku pro nastavení zarážky na funkci tak, že přerušení probíhá pouze na volání, pro které funkce neuspěje.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.debug.functions
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- conditional breakpoints
- errors [debugger], function calls
- breakpoints, troubleshooting
- errors [debugger], finding which function call failed
- failures
- location breakpoint call failures
- errors [Visual Studio], function calls
- hit counts
- function calls, failure
- functions [debugger]
- Skip Count
ms.assetid: 66cfac86-f5be-4d3a-9329-d44cd74bc586
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 567450f11572cc998f952117c33992cdba33570d
ms.sourcegitcommit: 957da60a881469d9001df1f4ba3ef01388109c86
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/13/2021
ms.locfileid: "98149297"
---
# <a name="when-calling-a-function-hundreds-of-times-how-do-i-know-which-call-failed"></a>Jak při opakovaném volání funkce zjistím, jaké volání bylo neúspěšné?
## <a name="problem-description"></a>Popis problému
 Dojde k chybě programu při volání určité funkce `CnvtV` . Program pravděpodobně tuto funkci zavolá několikrát, než se podařilo. Pokud jsem nastavil zarážku umístění na `CnvtV` , program se zastaví při každém volání této funkce a nemůžu to nechci. Nevím, jaké podmínky způsobují selhání volání, takže nejde nastavit podmíněný zarážku. Co mám udělat?

## <a name="solution"></a>Řešení
 Můžete nastavit zarážku pro funkci s polem **počet** průchodů na hodnotu, aby bylo tak vysoké, že nikdy nebude dosaženo. Vzhledem k tomu, že se domníváte, že `CnvtV` je funkce volána víckrát, můžete nastavit **Počet volání** na 1000 nebo více. Pak spusťte program a počkejte na selhání volání. Pokud dojde k chybě, otevřete okno zarážky a Prohlédněte si seznam zarážek. Zarážka, kterou nastavíte `CnvtV` , se zobrazí, za kterou následuje počet průchodů a počet zbývajících iterací:

```cpp
CnvtV(int) (no condition) when hit count is equal to 1000 (currently 101)
```

 Nyní víte, že ve volání 101st se funkce nezdařila. Pokud resetujete zarážku s počtem volání 101 a znovu spustíte program, program zastaví volání `CnvtV` , které způsobilo selhání.

## <a name="see-also"></a>Viz také
- [Nejčastější dotazy k ladění nativního kódu](../debugger/debugging-native-code-faqs.md)
- [Nastavení zarážek](/previous-versions/ktf38f66(v=vs.100))
- [Ladění nativního kódu](../debugger/debugging-native-code.md)