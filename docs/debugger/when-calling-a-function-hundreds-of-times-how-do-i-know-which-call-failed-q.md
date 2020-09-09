---
title: Najít, které volání se nezdařilo při volání funkce mnohokrát | Microsoft Docs
ms.custom: seodec18
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
ms.openlocfilehash: 4790fa8c6fd0bba5b513fd2ce3d203b552b6c63b
ms.sourcegitcommit: ed4372bb6f4ae64f1fd712b2b253bf91d9ff96bf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/09/2020
ms.locfileid: "89599995"
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