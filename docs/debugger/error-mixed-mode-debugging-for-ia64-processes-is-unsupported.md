---
title: 'Chyba: ladění ve smíšeném režimu pro procesy architektury IA64 není podporováno | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: troubleshooting
f1_keywords:
- vs.debug.error.interop_unsupported_ia64
dev_langs:
- CSharp
- VB
- FSharp
- C++
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 0bddbb1572bd0258eae2052eb34dfa3d0d67a134
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/22/2019
ms.locfileid: "72737628"
---
# <a name="error-mixed-mode-debugging-for-ia64-processes-is-unsupported"></a>Chyba: Ladění ve smíšeném režimu není pro procesy IA64 podporováno.
Ladicí program [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] nepodporuje ladění smíšeného nativního a spravovaného kódu v procesu založeném na procesorech Itanium.

### <a name="to-correct-this-error"></a>Oprava této chyby

- Sestavte 32 verzi vaší aplikace pro ladění.

## <a name="see-also"></a>Viz také:
- [Vzdálené ladění](../debugger/remote-debugging.md)