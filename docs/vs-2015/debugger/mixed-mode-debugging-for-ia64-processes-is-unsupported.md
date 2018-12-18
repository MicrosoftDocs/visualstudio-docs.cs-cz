---
title: Ladění ve smíšeném režimu není pro procesy IA64 podporováno. | Dokumenty Microsoft
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.debug.error.interop_unsupported_ia64
dev_langs:
- FSharp
- VB
- CSharp
- C++
ms.assetid: 20bc1e38-049b-4388-87c4-936815d85b46
caps.latest.revision: 6
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 12623f2692735b8a6ec31a4ecaa7bfc0b07e9364
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51806461"
---
# <a name="mixed-mode-debugging-for-ia64-processes-is-unsupported"></a>Ladění ve smíšeném režimu není pro procesy IA64 podporováno.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio nepodporuje ladění ve smíšeném režimu spravovaného a nativního kódu v procesech IA64. To znamená, že nelze krokovat ze spravovaného kódu do nativního kódu nebo z nativního kódu pro spravovaný kód při ladění.  
  
### <a name="workarounds"></a>Alternativní řešení  
  
-   Ladění spravovaného a nativního kódu v samostatné relace ladění.  
  
     – nebo –  
  
     Ladit smíšený kód jako 32bitový proces, jak je popsáno v následujících postupech.  
  
### <a name="to-change-the-platform-to-32-bit-visual-basic-or-c"></a>Chcete-li změnit platformu na 32 bitů (Visual Basic nebo C#)  
  
1.  V **Průzkumníka řešení**, klikněte pravým tlačítkem na projekt a pak klikněte na tlačítko **vlastnosti** v místní nabídce.  
  
2.  Na stránkách vlastností, klikněte na tlačítko **kompilaci** nebo **ladění** kartu.  
  
3.  Klikněte na tlačítko **platformy** a vyberte x86 ze seznamu platformy.  
  
     Ve výchozím nastavení výchozí kompilátory jazyka Visual Basic a C# vytvářet kód pro spuštění na jakýkoli procesor. Na 64bitovém počítači spusťte tyto binární soubory jako 64bitové procesy. Ke spuštění na 32bitový proces, musíte zvolit **Win32**, nikoli **AnyCPU**.  
  
### <a name="to-change-the-platform-to-32-bit-cc"></a>Chcete-li změnit platformu na 32 bitů (C/C++)  
  
1.  V **Průzkumníka řešení**, klikněte pravým tlačítkem na projekt a pak klikněte na tlačítko **vlastnosti** v místní nabídce.  
  
2.  Na stránkách vlastností, klikněte na tlačítko **platformy** a seznamu platformy, vyberte Win32  
  
## <a name="see-also"></a>Viz také  
 [Ladění 64bitových aplikací](../debugger/debug-64-bit-applications.md)



