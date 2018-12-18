---
title: Ladění ve smíšeném režimu není pro procesy IA64 podporováno. | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.error.interop_unsupported_ia64
dev_langs:
- CSharp
- VB
- FSharp
- C++
ms.assetid: 20bc1e38-049b-4388-87c4-936815d85b46
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: f87173f1a5a5be71e21ffd267c94619aed7b58d2
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2018
ms.locfileid: "31474476"
---
# <a name="mixed-mode-debugging-for-ia64-processes-is-unsupported"></a>Ladění ve smíšeném režimu není pro procesy IA64 podporováno.
Visual Studio nepodporuje ladění ve smíšeném režimu spravovaná a nativní kód v procesy IA64. To znamená, že při ladění nelze krok ze spravovaného kódu do nativního kódu nebo z nativního kódu pro spravovaný kód.  
  
### <a name="workarounds"></a>Alternativní řešení  
  
-   Ladění nativního a spravovaného kódu v samostatných relace ladění.  
  
     -nebo-  
  
     Ladit smíšený kód jako 32bitový proces, jak je popsáno v následujících postupech.  
  
### <a name="to-change-the-platform-to-32-bit-visual-basic-or-c"></a>Chcete-li změnit platformu pro 32-bit (Visual Basic a C#)  
  
1.  V **Průzkumníku řešení**, klikněte pravým tlačítkem na projekt a pak klikněte na tlačítko **vlastnosti** v místní nabídce.  
  
2.  Na stránkách vlastností klikněte **zkompilovat** nebo **ladění** kartě.  
  
3.  Klikněte na tlačítko **platformy** a vyberte x86 ze seznamu platformy.  
  
     Ve výchozím nastavení vytvořit výchozí kompilátory jazyka Visual Basic a C# kód pro spuštění na libovolném procesoru. Na 64bitovém počítači spusťte tyto binární soubory jako 64bitové procesy. Pokud chcete spustit u 32-bit procesu, je nutné vybrat **Win32**, nikoli **AnyCPU**.  
  
### <a name="to-change-the-platform-to-32-bit-cc"></a>Chcete-li změnit platformu pro 32-bit (C/C++)  
  
1.  V **Průzkumníku řešení**, klikněte pravým tlačítkem na projekt a pak klikněte na tlačítko **vlastnosti** v místní nabídce.  
  
2.  Na stránkách vlastností klikněte na tlačítko **platformy** a vyberte ze seznamu platforem, Win32  
  
## <a name="see-also"></a>Viz také  
 [Ladění 64bitových aplikací](../debugger/debug-64-bit-applications.md)