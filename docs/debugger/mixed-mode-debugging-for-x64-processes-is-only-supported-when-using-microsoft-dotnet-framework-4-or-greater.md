---
title: Ladění ve smíšeném režimu pro procesy x64 je podporováno, pouze pokud používáte rozhraní Microsoft .NET Framework 4 nebo vyšší
description: Verze .NET Framework starší než 4 neposkytují podporu pro ladění ve smíšeném režimu pro procesy x64. Alternativní řešení najdete v tomto článku.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.debug.error.interop_unsupported_x64
dev_langs:
- CSharp
- VB
- FSharp
- C++
ms.assetid: b7495655-54c0-4315-8422-43bf63b8c22e
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 92ec1022842e44f9f87069c48d4de3259dcf8e99
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99913189"
---
# <a name="mixed-mode-debugging-for-x64-processes-is-only-supported-when-using-microsoftnet-framework-4-or-greater"></a>Ladění ve smíšeném režimu pro procesy x64 je podporováno, pouze pokud používáte rozhraní Microsoft .NET Framework 4 nebo vyšší
Verze .NET Framework starší než 4 neposkytují podporu pro ladění ve smíšeném režimu pro procesy x64. To znamená, že nemůžete krokovat ze spravovaného kódu do nativního kódu nebo z nativního kódu do spravovaného kódu při ladění.

### <a name="workarounds"></a>Alternativní řešení

- Aktualizujte projekt tak, aby používal Microsoft .NET Framework 4 nebo novější.

     -nebo-

     Ladění spravovaného a nativního kódu v samostatných ladicích relacích.

     -nebo-

     Ladit smíšený kód jako 32 proces, jak je popsáno v následujících postupech.

### <a name="to-change-the-platform-to-32-bit-visual-basic-or-c"></a>Změna platformy na 32-bit (Visual Basic nebo C#)

1. V **Průzkumník řešení** klikněte pravým tlačítkem myši na projekt a pak klikněte na **vlastnosti**.

2. Na stránkách vlastností klikněte na kartu **kompilovat** nebo **ladění** .

3. Klikněte na **platforma** a v seznamu platforem vyberte x86.

     Ve výchozím nastavení kompilátor Visual Basic a C# standardně vytváří kód pro spuštění na jakémkoli procesoru. Na 64 počítači se tyto binární soubory spouští jako 64 procesy. Pro spuštění na 32 procesu je nutné zvolit **Win32**, nikoli **anycpu**.

### <a name="to-change-the-platform-to-32-bit-cc"></a>Změna platformy na 32-bit (C/C++)

1. V **Průzkumník řešení** klikněte pravým tlačítkem myši na projekt a pak klikněte na **vlastnosti**.

2. Na stránkách vlastností klikněte na možnost **platforma** a v seznamu platforem vyberte položku Win32.

### <a name="to-correct-this-error"></a>Oprava této chyby

- Viz [nastavení ladění SQL](/previous-versions/visualstudio/visual-studio-2010/s4sszxst(v=vs.100)).

## <a name="see-also"></a>Viz také
- [Ladění 64 aplikací](../debugger/debug-64-bit-applications.md)