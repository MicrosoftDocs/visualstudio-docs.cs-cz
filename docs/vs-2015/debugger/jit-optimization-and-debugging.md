---
title: Optimalizace a ladění JIT | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- debugging [Visual Studio], optimized code
- optimized code, debugging
ms.assetid: 19bfabf3-1a2e-49dc-8819-a813982e86fd
caps.latest.revision: 16
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 56b010a01ccd7e40e696653e13dd7c972c97a9cb
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "65690540"
---
# <a name="jit-optimization-and-debugging"></a>Optimalizace a ladění JIT
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Když ladíte spravovanou aplikaci, [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] potlačí ve výchozím nastavení optimalizaci kódu JIT (just-in-time). Potlačení optimalizace JIT znamená, že ladíte neoptimalizovaný kód. Kód se spouští trochu pomaleji, protože není optimalizovaný, ale vaše prostředí ladění je mnohem důkladnější. Ladění optimalizovaného kódu je těžší a doporučuje se pouze v případě, že dojde k chybě, která se vyskytuje v optimalizovaném kódu, ale nemůže být reprodukována v neoptimalizované verzi.  
  
 Optimalizace JIT je ovládána v [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] možnosti **pro potlačení optimalizace JIT při načtení modulu** . Tuto možnost můžete najít na stránce **Obecné** v uzlu **ladění** v dialogovém okně **Možnosti** .  
  
 Pokud zrušíte možnost **potlačit optimalizaci JIT při načtení modulu** , můžete ladit optimalizovaný kód JIT, ale schopnost ladění může být omezená, protože optimalizovaný kód neodpovídá zdrojovému kódu. V důsledku toho okna ladicího programu, jako jsou **místní** a **Automatické** hodnoty, se nemusí zobrazit jako velké množství informací, pokud jste ladíte neoptimalizovaný kód.  
  
 Další důležitý rozdíl se týká ladění s Pouze můj kód. Pokud ladíte pomocí Pouze můj kód, ladicí program považuje optimalizovaný kód za neuživatelský kód, který by neměl být zobrazen při ladění. V důsledku toho při ladění optimalizovaného kódu JIT pravděpodobně budete chtít vypnout Pouze můj kód. Další informace najdete v tématu  [Omezení krokování na pouze můj kód](../debugger/just-my-code.md#BKMK_Enable_or_disable_Just_My_Code).  
  
 Mějte na paměti, že možnost **potlačit optimalizaci JIT při načtení modulu** potlačuje optimalizaci kódu při načtení modulů. Pokud se připojíte k procesu, který je již spuštěn, může obsahovat kód, který je již načten, kompilován kompilátorem JIT a optimalizován. Možnost **potlačit optimalizaci JIT při načtení modulu** nemá na takový kód vliv, i když bude mít vliv na moduly, které jsou načteny po připojení. Kromě toho možnost **potlačit optimalizaci JIT při načtení modulu** neovlivní moduly, například WinForms.dll, které jsou vytvořeny pomocí Ngen.  
  
## <a name="see-also"></a>Viz také  
 [Ladění spravovaného kódu](../debugger/debugging-managed-code.md)   
 [Navigace v kódu pomocí ladicího programu](../debugger/navigating-through-code-with-the-debugger.md)   
 [Připojit ke spuštěným procesům](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)   
 [Proces spravovaného spuštění](https://msdn.microsoft.com/library/476b03dc-2b12-49a7-b067-41caeaa2f533)
