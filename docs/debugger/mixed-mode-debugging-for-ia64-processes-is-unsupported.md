---
title: Ladění ve smíšeném režimu není pro procesy IA64 podporováno. | Dokumentace Microsoftu
ms.date: 11/04/2016
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c85c31cff5920ba3dc4b9356a1865d0db2323b2d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "72731105"
---
# <a name="mixed-mode-debugging-for-ia64-processes-is-unsupported"></a>Ladění ve smíšeném režimu není pro procesy IA64 podporováno.
Visual Studio nepodporuje ladění ve smíšeném režimu se spravovaným a nativním kódem v procesech architektury IA64. To znamená, že nemůžete krokovat ze spravovaného kódu do nativního kódu nebo z nativního kódu do spravovaného kódu při ladění.

### <a name="workarounds"></a>Alternativní řešení

- Ladění spravovaného a nativního kódu v samostatných ladicích relacích.

     -nebo-

     Ladit smíšený kód jako 32 proces, jak je popsáno v následujících postupech.

### <a name="to-change-the-platform-to-32-bit-visual-basic-or-c"></a>Změna platformy na 32-bit (Visual Basic nebo C#)

1. V **Průzkumník řešení**klikněte pravým tlačítkem na projekt a pak klikněte na **vlastnosti** v místní nabídce.

2. Na stránkách vlastností klikněte na kartu **kompilovat** nebo **ladit** .

3. Klikněte na **platforma** a v seznamu platforem vyberte x86.

     Ve výchozím nastavení kompilátor Visual Basic a C# standardně vytváří kód pro spuštění na jakémkoli procesoru. Na 64 počítači se tyto binární soubory spouští jako 64 procesy. Pro spuštění na 32 procesu je nutné zvolit **Win32**, nikoli **anycpu**.

### <a name="to-change-the-platform-to-32-bit-cc"></a>Změna platformy na 32-bit (C/C++)

1. V **Průzkumník řešení**klikněte pravým tlačítkem na projekt a pak klikněte na **vlastnosti** v místní nabídce.

2. Na stránkách vlastností klikněte na možnost **platforma** a v seznamu platforem vyberte položku Win32.

## <a name="see-also"></a>Viz také
- [Ladění 64bitových aplikací](../debugger/debug-64-bit-applications.md)