---
title: JIT optimalizace a ladění | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
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
manager: ghogen
ms.openlocfilehash: ab86e023b99f524651b56bbca4ddea2d613448e2
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51770754"
---
# <a name="jit-optimization-and-debugging"></a>Optimalizace a ladění JIT
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Při ladění spravované aplikace [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] potlačuje optimalizaci kódu just-in-time (JIT) ve výchozím nastavení. Potlačení optimalizace JIT znamená, že ladíte neoptimalizovaný kód. Kód spustí o něco pomaleji, protože není optimalizován, ale využití ladění je mnohem důkladnější. Ladění optimalizovaného kódu je těžší a doporučuje se pouze, pokud narazíte na chybu, která vyskytuje v optimalizovaném kódu, ale nelze ji reprodukovat v neoptimalizované verzi.  
  
 Optimalizace JIT je ovládáno [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] podle **potlačení optimalizace JIT při načtení modulu** možnost. Tuto možnost můžete najít na **Obecné** stránce v části **ladění** uzlu **možnosti** dialogové okno.  
  
 Pokud zrušíte výběr **potlačení optimalizace JIT při načtení modulu** možnost, můžete ladit optimalizovaný kód JIT, ale možnosti ladění mohou být omezeny, protože optimalizovaný kód neodpovídá zdrojový kód. V důsledku toho okna ladicího programu, jako **lokální** a **automatické hodnoty** okna nemusí být zobrazeny co nejvíce informací, jako kdybyste ladili neoptimalizovaný kód.  
  
 Další důležitý rozdíl se týká ladění s jen můj kód. Pokud ladíte pomocí funkce pouze můj kód, ladicí program považuje za optimalizovaný kód za kód nepatřící uživateli, který nebude zobrazen při ladění. V důsledku toho Pokud ladíte optimalizovaný kód JIT, budete pravděpodobně chtít vypnout volbu pouze vlastní kód. Další informace najdete v tématu [omezení krokování na pouze můj kód](../debugger/just-my-code.md#BKMK_Enable_or_disable_Just_My_Code).  
  
 Mějte na paměti, **potlačení optimalizace JIT při načtení modulu** možnost potlačuje optimalizaci kódu při načtení modulů. Pokud se připojíte k procesu, který je již spuštěn, může obsahovat kód, který je již načteno, zkompilován JIT Kompilátorem a optimalizované. **Potlačení optimalizace JIT při načtení modulu** možnost nemá žádný vliv na takový kód, i když bude mít vliv na moduly, které jsou načteny po připojení. Kromě toho **potlačení optimalizace JIT při načtení modulu** možnost nemá vliv na moduly, například WinForms.dll, které jsou vytvořeny pomocí technologie NGEN.  
  
## <a name="see-also"></a>Viz také  
 [Ladění spravovaného kódu](../debugger/debugging-managed-code.md)   
 [Procházení kódu s ladicím programem](../debugger/navigating-through-code-with-the-debugger.md)   
 [Připojení ke spuštěným procesům](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)   
 [Proces spravovaného spuštění](http://msdn.microsoft.com/library/476b03dc-2b12-49a7-b067-41caeaa2f533)



