---
title: Ladění narušení přístupu při spuštění aplikace mimo ladicí program
ms.custom: seodec18
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.debug.access
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- access violation debugging
- debugging [Visual Studio], access violations
ms.assetid: 780a298a-132e-4245-8370-8c82ca27c6c1
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f5009bae2d7679081e29ae8f46d72455beac7e11
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/22/2019
ms.locfileid: "72734574"
---
# <a name="how-can-i-debug-access-violations-when-running-my-program-outside-the-debugger"></a>Jak mohu ladit porušení přístupu, když program spouštím mimo ladicí program?

## <a name="problem-description"></a>Popis problému
 Můj program funguje v prostředí sady Visual Studio správně, ale když ho spouštíte samostatně s operačním systémem Windows, dojde k narušení přístupu. Jak mohu tento problém ladit?

## <a name="solution"></a>Řešení
 Nastavte možnost [ladění za běhu](../debugger/just-in-time-debugging-in-visual-studio.md) a spusťte program samostatně, dokud nedojde k narušení přístupu. Pak můžete v dialogovém okně **porušení přístupu** kliknutím na tlačítko **Storno** spustit ladicí program.

## <a name="see-also"></a>Viz také:
- [Nejčastější dotazy k ladění nativního kódu](../debugger/debugging-native-code-faqs.md)
- [Ladění nativního kódu](../debugger/debugging-native-code.md)