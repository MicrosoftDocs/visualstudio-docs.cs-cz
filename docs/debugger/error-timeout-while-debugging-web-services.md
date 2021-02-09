---
title: Vypršel časový limit při ladění webových služeb | Microsoft Docs
ms.date: 11/04/2016
ms.topic: error-reference
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugger, Web application errors
- XML Web services, timeout while debugging
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 87a2d79fc24bdb433fbb5eb1480dbf5d15520a8c
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99871101"
---
# <a name="error-timeout-while-debugging-web-services"></a>Chyba: Během ladění webových služeb vypršel časový limit.
Při krokování webové služby XML od volání kódu může být volání někdy vyprší časový limit, přičemž výsledkem je, že nelze pokračovat v ladění. Může se zobrazit chybová zpráva, například.

```cmd
An unhandled exception of type 'System.Net.WebException' occurred in
system.Web.services.dll
Additional information: The operation has timed-out.
```

## <a name="solution"></a>Řešení
 Chcete-li se tomuto problému vyhnout, nastavte hodnotu časového limitu pro volání webové služby XML na nekonečné, jak je znázorněno v následujícím příkladu:

```csharp
Service1 obj = new Service1();
obj.TimeOut = -1; // infinite time out.
```

## <a name="see-also"></a>Viz také
- [Ladění webových aplikací: chyby a řešení potíží](../debugger/debugging-web-applications-errors-and-troubleshooting.md)
