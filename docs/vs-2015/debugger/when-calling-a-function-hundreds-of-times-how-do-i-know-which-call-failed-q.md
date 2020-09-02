---
title: Jak při opakovaném volání funkce zjistím, jaké volání bylo neúspěšné? | Dokumentace Microsoftu
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.functions
dev_langs:
- FSharp
- VB
- CSharp
- C++
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
caps.latest.revision: 20
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: fba5032860e21bbd323b8e49d5f32ab9b6f90540
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "65688136"
---
# <a name="when-calling-a-function-hundreds-of-times-how-do-i-know-which-call-failed"></a>Jak při opakovaném volání funkce zjistím, jaké volání bylo neúspěšné?
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Popis problému  
 Dojde k chybě programu při volání určité funkce `CnvtV` . Program pravděpodobně tuto funkci zavolá několikrát, než se podařilo. Pokud jsem nastavil zarážku umístění na `CnvtV` , program se zastaví při každém volání této funkce a nemůžu to nechci. Nevím, jaké podmínky způsobují selhání volání, takže nejde nastavit podmíněný zarážku. Co mám udělat?  
  
## <a name="solution"></a>Řešení  
 Můžete nastavit zarážku pro funkci s polem **počet** průchodů na hodnotu, aby bylo tak vysoké, že nikdy nebude dosaženo. Vzhledem k tomu, že se domníváte, že `CnvtV` je funkce volána víckrát, můžete nastavit **Počet volání** na 1000 nebo více. Pak spusťte program a počkejte na selhání volání. Pokud dojde k chybě, otevřete okno zarážky a Prohlédněte si seznam zarážek. Zarážka, kterou nastavíte `CnvtV` , se zobrazí, za kterou následuje počet průchodů a počet zbývajících iterací:  
  
```  
CnvtV(int) (no condition) when hit count is equal to 1000 (currently 101)  
```  
  
 Nyní víte, že ve volání 101st se funkce nezdařila. Pokud resetujete zarážku s počtem volání 101 a znovu spustíte program, program zastaví volání `CnvtV` , které způsobilo selhání.  
  
## <a name="see-also"></a>Viz také  
 [Nejčastější dotazy k ladění nativního kódu](../debugger/debugging-native-code-faqs.md)   
 [Nastavení zarážek](https://msdn.microsoft.com/fe4eedc1-71aa-4928-962f-0912c334d583)   
 [Ladění nativního kódu](../debugger/debugging-native-code.md)
