---
title: Ladění ve smíšeném režimu pro procesy x64 je podporované jenom v případě, že používáte Microsoft .NET Framework 4 nebo novější | Microsoft Docs
ms.date: 11/04/2016
ms.topic: error-reference
f1_keywords:
- vs.debug.error.interop_unsupported_x64
dev_langs:
- CSharp
- VB
- FSharp
- C++
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: e8cfc3ac5cb606637fe5c2818750168a239a46fa
ms.sourcegitcommit: 062615c058d2ff44751e8d0c704ccfa3c5543469
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/22/2020
ms.locfileid: "90852612"
---
# <a name="error-mixed-mode-debugging-for-x64-processes-is-supported-only-when-using-microsoft-net-framework-4-or-greater"></a>Chyba: Ladění ve smíšeném režimu pro procesy x64 je podporováno, pouze pokud používáte rozhraní Microsoft .NET Framework 4 nebo vyšší.
Chcete-li ladit smíšený nativní a spravovaný kód v 64m procesu, je nutné mít .NET Framework verzi 4. Ladění ve smíšeném režimu s 64 procesy s .NET Framework verzemi staršími než 4 se nepodporuje.

### <a name="to-correct-this-error"></a>Oprava této chyby

- Proveďte jeden z následujících kroků:

  - Upgradujte .NET Framework na verzi 4.

  - Sestavte 32 verzi vaší aplikace pro ladění.

## <a name="see-also"></a>Viz také
- [Vzdálené ladění](../debugger/remote-debugging.md)