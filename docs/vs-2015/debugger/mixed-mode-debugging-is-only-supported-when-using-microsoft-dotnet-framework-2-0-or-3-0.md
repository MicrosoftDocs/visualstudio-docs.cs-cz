---
title: Ladění ve smíšeném režimu se podporuje jenom v případě, že používáte Microsoft .NET Framework 2,0 nebo 3,0 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.error.interop_unsupported_to_old
dev_langs:
- FSharp
- VB
- CSharp
- C++
ms.assetid: f607af6f-57fe-472a-a32e-b6202067aa96
caps.latest.revision: 8
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: fc45927ad6cc1189ed1d08328b4dd362821cdcb6
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "65696468"
---
# <a name="mixed-mode-debugging-is-only-supported-when-using-microsoft-net-framework-20-or-30"></a>Ladění ve smíšeném režimu je podporováno, pouze pokud používáte rozhraní Microsoft .NET Framework 2.0 nebo 3.0.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Verze Microsoft .NET Framework starší než 2,0 neposkytují podporu pro ladění ve smíšeném režimu pro 64 procesy. To znamená, že nemůžete krokovat ze spravovaného kódu do nativního kódu nebo z nativního kódu do spravovaného kódu při ladění.  
  
 Pokud chcete tento problém obejít, můžete:  
  
- Aktualizujte projekt tak, aby používal buď Microsoft .NET Framework 2,0 nebo 3,0.  
  
- Ladění spravovaného a nativního kódu v samostatných ladicích relacích.  
  
- Ladit smíšený kód jako 32 proces, jak je popsáno v následujících postupech.  
  
### <a name="to-change-the-operating-system-to-32-bit-visual-basic-or-c"></a>Změna operačního systému na 32-bit (Visual Basic nebo C#)  
  
1. V **Průzkumník řešení**klikněte pravým tlačítkem myši na projekt a potom klikněte na možnost **vlastnosti** v místní nabídce.  
  
2. Na stránkách vlastností klikněte na kartu **kompilovat** nebo **ladit** .  
  
3. Klikněte na **platforma**a v seznamu platforem vyberte **x86** .  
  
     Ve výchozím nastavení kompilátor Visual Basic a C# vytváří kód pro spuštění na jakémkoli procesoru. Na 64 počítači se tyto binární soubory spouští jako 64 procesy. Pro spuštění na 32 procesu je nutné zvolit **Win32**, nikoli **anycpu**.  
  
### <a name="to-change-the-operating-system-to-32-bit-cc"></a>Změna operačního systému na 32-bit (C/C++)  
  
1. V **Průzkumník řešení**klikněte pravým tlačítkem myši na projekt a potom klikněte na možnost **vlastnosti** v místní nabídce.  
  
     Na stránkách vlastností klikněte na možnost **platforma**a v seznamu platforem vyberte položku **Win32** .  
  
### <a name="to-correct-this-error"></a>Oprava této chyby  
  
- Viz [nastavení ladění SQL](https://msdn.microsoft.com/3db09e68-edcc-42de-9c22-4e97cfd55ab3).  
  
## <a name="see-also"></a>Viz také  
 [Ladění 64bitových aplikací](../debugger/debug-64-bit-applications.md)
