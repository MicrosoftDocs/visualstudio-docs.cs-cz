---
title: DebugBreak a __debugbreak | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- DebugBreak
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugging [C++], DebugBreak function
- DebugBreak function
- breakpoints, DebugBreak function
ms.assetid: 9787c795-df94-4f48-bc8d-3bf899b67421
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ce99cd360d75472df6326cfaf6a3f4ddb198b6d2
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/22/2019
ms.locfileid: "72738351"
---
# <a name="debugbreak-and-__debugbreak"></a>DebugBreak a __debugbreak
Funkci DebugBreak Win32 nebo vnitřní [__debugbreak](/cpp/intrinsics/debugbreak) můžete volat v jakémkoli bodě kódu. `DebugBreak` a `__debugbreak` mají stejný účinek jako nastavení zarážky v daném umístění.

 Vzhledem k tomu, že `DebugBreak` je voláním systémové funkce, musí být nainstalovány symboly ladění systému, aby bylo zajištěno, že po přerušení budou zobrazeny správné informace o zásobníku volání. V opačném případě mohou být informace zásobníku volání zobrazené ladicím programem vypnuty jedním snímkem. Pokud používáte `__debugbreak`, symboly se nevyžadují.

## <a name="see-also"></a>Viz také:
- [Vnitřní funkce kompilátoru](/cpp/intrinsics/compiler-intrinsics)
- [Zabezpečení ladicího programu](../debugger/debugger-security.md)
- [Ladění nativního kódu](../debugger/debugging-native-code.md)
- [Zadání symbolu (.pdb) a zdrojových souborů](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)