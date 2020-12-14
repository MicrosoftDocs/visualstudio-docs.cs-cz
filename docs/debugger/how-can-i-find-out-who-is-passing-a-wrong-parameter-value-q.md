---
title: Zjistěte, kdo předává nesprávnou hodnotu parametru | Microsoft Docs
Description: Můžete zjistit, jaký kód volá vaši funkci a předat nesprávnou hodnotu parametru. Naučte se používat podmíněný bod přerušení.
ms.custom: SEO-VS-2020, seodec18
ms.date: 11/04/2016
ms.topic: how-to
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: de87da994dfab59d5df618671737003beea9678b
ms.sourcegitcommit: 40d758f779d42c66cb02ae7face8a62763a8662b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/14/2020
ms.locfileid: "97398308"
---
# <a name="how-can-i-find-out-who-is-passing-a-wrong-parameter-value"></a>Jak zjistím, kdo předává nesprávnou hodnotu parametru?
## <a name="problem-description"></a>Popis problému
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
- [Nejčastější dotazy k ladění nativního kódu](../debugger/debugging-native-code-faqs.md)
- [Zarážky](/previous-versions/ktf38f66(v=vs.100))
- [Ladění nativního kódu](../debugger/debugging-native-code.md)