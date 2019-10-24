---
title: 'Chyba: ladění ve smíšeném režimu je podporováno pouze v případě, že používáte Microsoft .NET Framework 2,0 nebo vyšší | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: troubleshooting
f1_keywords:
- vs.debug.error.interop_unsupported_to_old
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
ms.openlocfilehash: c85dac85146c59d8aeba9f9cf85351b5bc17a81c
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/22/2019
ms.locfileid: "72737616"
---
# <a name="error-mixed-mode-debugging-is-supported-only-when-using-microsoft-net-framework-20-or-greater"></a>Chyba: Ladění ve smíšeném režimu je podporováno, pouze pokud používáte rozhraní Microsoft .NET Framework 2.0 nebo vyšší.
Chcete-li ladit smíšený nativní a spravovaný kód, je nutné mít .NET Framework verze 2,0, 3,0. 3,5 nebo 4,0. Ladění ve smíšeném režimu se staršími verzemi .NET Framework není podporováno.

### <a name="to-correct-this-error"></a>Oprava této chyby

- Upgradujte .NET Framework na verzi 2,0, 3,0, 3,5 nebo 4,0.

## <a name="see-also"></a>Viz také:
- [Vzdálené ladění](../debugger/remote-debugging.md)