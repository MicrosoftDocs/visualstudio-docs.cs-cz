---
title: Zjistěte, kdo předává nesprávnou hodnotu parametru | Dokumentace Microsoftu
ms.custom: seodec18
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.parameters
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugging [C++], parameters
- parameters [debugger]
- passing parameters, troubleshooting wrong values
- functions [debugger], detecting wrong parameter values
- parameter values, troubleshooting
ms.assetid: 1f1ae455-0e25-4e9d-b33f-53908f5bd6ce
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 164ca15cfc508b952ccfe2f986892c0801fd1539
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/07/2018
ms.locfileid: "53059363"
---
# <a name="how-can-i-find-out-who-is-passing-a-wrong-parameter-value"></a>Jak zjistím, kdo předává nesprávnou hodnotu parametru?
## <a name="problem-description"></a>Popis problému  
 Chybná hodnota parametru je předána jedné z mých funkcí. Tato funkce je volána odkudkoliv. Jak zjistím, co ho nesprávnou hodnotu předává?  
  
## <a name="solution"></a>Řešení  
  
#### <a name="to-resolve-this-problem"></a>Chcete-li vyřešit tento problém  
  
1.  Nastavte zarážku umístění na začátek funkce.  
  
2.  Klikněte pravým tlačítkem myši zarážka a vyberte **podmínku**.  
  
3.  V **podmínka zarážky** dialogové okno, klikněte na **podmínku** zaškrtávací políčko. Zobrazit [Advanced zarážky](../debugger/using-breakpoints.md#BKMK_Specify_a_breakpoint_condition_using_a_code_expression).  
  
4.  Zadejte výraz, jako například `Var==3`, do textového pole, ve kterém `Var` je název parametru, který obsahuje chybnou hodnotu, a `3` je předaná chybná hodnota k němu.  
  
5.  Vyberte **true** přepínač a klikněte na tlačítko **OK** tlačítko.  
  
6.  Nyní spusťte program znovu. Zarážka způsobí zastavení na začátku funkce programu při `Var` parametr má hodnotu `3`.  
  
7.  Použití okna zásobník volání najděte volající funkci a přejděte k jejímu zdrojovému kódu. Další informace najdete v tématu [postupy: použití okna zásobník volání](../debugger/how-to-use-the-call-stack-window.md).  
  
## <a name="see-also"></a>Viz také  
 [Ladění nativního kódu nejčastější dotazy](../debugger/debugging-native-code-faqs.md)   
 [Zarážky](https://msdn.microsoft.com/library/fe4eedc1-71aa-4928-962f-0912c334d583)   
 [Ladění nativního kódu](../debugger/debugging-native-code.md)