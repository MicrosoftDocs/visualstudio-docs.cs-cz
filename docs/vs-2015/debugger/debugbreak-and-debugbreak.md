---
title: DebugBreak a __debugbreak | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- DebugBreak
dev_langs:
- FSharp
- VB
- CSharp
- C++
- C++
helpviewer_keywords:
- debugging [C++], DebugBreak function
- DebugBreak function
- breakpoints, DebugBreak function
ms.assetid: 9787c795-df94-4f48-bc8d-3bf899b67421
caps.latest.revision: 26
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: ea2a40943233e7dfffd3340f2e27da1d43a76a0a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "65691178"
---
# <a name="debugbreak-and-__debugbreak"></a>DebugBreak a __debugbreak
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Funkci DebugBreak Win32 nebo vnitřní [__debugbreak](https://msdn.microsoft.com/library/1d1e1c0c-891a-4613-ae4b-d790094ba830) můžete volat v jakémkoli bodě kódu. `DebugBreak` a `__debugbreak` mají stejný účinek jako nastavení zarážky v daném umístění.  
  
 Vzhledem `DebugBreak` k tomu, že se jedná o volání funkce systému, musí být nainstalovány symboly ladění systému, aby bylo zajištěno, že po přerušení budou zobrazeny správné informace o zásobníku volání. V opačném případě mohou být informace zásobníku volání zobrazené ladicím programem vypnuty jedním snímkem. Pokud použijete `__debugbreak` , symboly se nevyžadují.  
  
## <a name="see-also"></a>Viz také  
 [Vnitřní objekty kompilátoru](https://msdn.microsoft.com/library/48bb9929-7d78-4fd8-a092-ae3c9f971858)   
 [Zabezpečení ladicího programu](../debugger/debugger-security.md)   
 [Ladění nativního kódu](../debugger/debugging-native-code.md)   
 [Zadání symbolu (.pdb) a zdrojových souborů](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)
