---
title: Jak zjistím, kdo předává nesprávnou hodnotu parametru? | Dokumentace Microsoftu
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.parameters
dev_langs:
- FSharp
- VB
- CSharp
- C++
- C++
helpviewer_keywords:
- debugging [C++], parameters
- parameters [debugger]
- passing parameters, troubleshooting wrong values
- functions [debugger], detecting wrong parameter values
- parameter values, troubleshooting
ms.assetid: 1f1ae455-0e25-4e9d-b33f-53908f5bd6ce
caps.latest.revision: 22
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: b0787a0d700859e7728762fd7846911fcd41e369
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "65704555"
---
# <a name="how-can-i-find-out-who-is-passing-a-wrong-parameter-value"></a>Jak zjistím, kdo předává nesprávnou hodnotu parametru?
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Popis problému  
 Nesprávná hodnota parametru se předává do jedné z mých funkcí. Tato funkce se volá z celého místa. Jak zjistím, co znamená chybnou hodnotu?  
  
## <a name="solution"></a>Řešení  
  
#### <a name="to-resolve-this-problem"></a>Řešení tohoto problému  
  
1. Nastavte zarážku umístění na začátku funkce.  
  
2. Klikněte pravým tlačítkem na zarážku a vyberte **Podmínka**.  
  
3. V dialogovém okně **Podmínka zarážky** klikněte na zaškrtávací políčko **Podmínka** . Viz [Pokročilé zarážky](../debugger/using-breakpoints.md#BKMK_Specify_a_breakpoint_condition_using_a_code_expression).  
  
4. Zadejte výraz, například `Var==3` , do textového pole, kde `Var` je název parametru, který obsahuje chybnou hodnotu a `3` je předána chybná hodnota.  
  
5. Vyberte přepínač **má hodnotu true** a klikněte na tlačítko **OK** .  
  
6. Nyní spusťte program znovu. Zarážka způsobí zastavení programu na začátku funkce, pokud `Var` má parametr hodnotu `3` .  
  
7. Použijte okno zásobník volání k vyhledání volající funkce a přejděte ke svému zdrojovému kódu. Další informace naleznete v tématu [Postupy: použití okna zásobník volání](../debugger/how-to-use-the-call-stack-window.md).  
  
## <a name="see-also"></a>Viz také  
 [Nejčastější dotazy k ladění nativního kódu](../debugger/debugging-native-code-faqs.md)   
 [Zarážky](https://msdn.microsoft.com/fe4eedc1-71aa-4928-962f-0912c334d583)   
 [Ladění nativního kódu](../debugger/debugging-native-code.md)
