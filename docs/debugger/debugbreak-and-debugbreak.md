---
title: DebugBreak a __debugbreak | Microsoft Docs
description: Naučte se, jak používat funkci DebugBreak a vnitřní __debugbreak k narušení programu, stejně jako když byla nastavena zarážka.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: 376dd75062dc5a78582a23a12e9e025db60b9f3a
ms.sourcegitcommit: bbed6a0b41ac4c4a24e8581ff3b34d96345ddb00
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/03/2020
ms.locfileid: "96559768"
---
# <a name="debugbreak-and-__debugbreak"></a>DebugBreak a __debugbreak
Funkci [DebugBreak](/windows/win32/api/debugapi/nf-debugapi-debugbreak) Win32 nebo vnitřní [__debugbreak](/cpp/intrinsics/debugbreak) můžete volat v jakémkoli bodě kódu. `DebugBreak` a `__debugbreak` mají stejný účinek jako nastavení zarážky v daném umístění.

 Vzhledem `DebugBreak` k tomu, že se jedná o volání funkce systému, musí být nainstalovány symboly ladění systému, aby bylo zajištěno, že po přerušení budou zobrazeny správné informace o zásobníku volání. V opačném případě mohou být informace zásobníku volání zobrazené ladicím programem vypnuty jedním snímkem. Pokud použijete `__debugbreak` , symboly se nevyžadují.

## <a name="see-also"></a>Viz také:
- [Vnitřní objekty kompilátoru](/cpp/intrinsics/compiler-intrinsics)
- [Zabezpečení ladicího programu](../debugger/debugger-security.md)
- [Ladění nativního kódu](../debugger/debugging-native-code.md)
- [Zadání symbolu (.pdb) a zdrojových souborů](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)
