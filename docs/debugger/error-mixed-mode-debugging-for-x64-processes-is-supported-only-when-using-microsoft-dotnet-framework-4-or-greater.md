---
title: 'Chyba: ladění ve smíšeném režimu pro procesy x64 je podporováno pouze v případě, že používáte Microsoft .NET Framework 4 nebo vyšší | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: troubleshooting
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
ms.openlocfilehash: 67b9d1c737e4490195b209abca824b2d6d51176c
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/22/2019
ms.locfileid: "72737606"
---
# <a name="error-mixed-mode-debugging-for-x64-processes-is-supported-only-when-using-microsoft-net-framework-4-or-greater"></a>Chyba: Ladění ve smíšeném režimu pro procesy x64 je podporováno, pouze pokud používáte rozhraní Microsoft .NET Framework 4 nebo vyšší.
Chcete-li ladit smíšený nativní a spravovaný kód v 64m procesu, je nutné mít .NET Framework verzi 4. Ladění ve smíšeném režimu s 64 procesy s .NET Framework verzemi staršími než 4 se nepodporuje.

### <a name="to-correct-this-error"></a>Oprava této chyby

- Proveďte jeden z následujících kroků:

  - Upgradujte .NET Framework na verzi 4.

  - Sestavte 32 verzi vaší aplikace pro ladění.

## <a name="see-also"></a>Viz také:
- [Vzdálené ladění](../debugger/remote-debugging.md)