---
title: 'Chyba: při ladění webových služeb vypršel časový limit | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- debugger, Web application errors
- XML Web services, timeout while debugging
ms.assetid: 4b7df112-788a-4429-9a0c-4c6dac4fb609
caps.latest.revision: 11
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 5745a23e70f9245d6f1cb34a6d4ccc042f64bdd3
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "62538327"
---
# <a name="error-timeout-while-debugging-web-services"></a>Chyba: Během ladění webových služeb vypršel časový limit.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Při krokování webové služby XML od volání kódu může být volání někdy vyprší časový limit, přičemž výsledkem je, že nelze pokračovat v ladění. Může se zobrazit chybová zpráva, například.  
  
```  
An unhandled exception of type 'System.Net.WebException' occurred in   
system.Web.services.dll  
Additional information: The operation has timed-out.  
```  
  
## <a name="solution"></a>Řešení  
 Chcete-li se tomuto problému vyhnout, nastavte hodnotu časového limitu pro volání webové služby XML na nekonečné, jak je znázorněno v následujícím příkladu:  
  
```  
Service1 obj = new Service1();  
obj.TimeOut = -1; // infinite time out.  
```  
  
## <a name="see-also"></a>Viz také  
 [Ladění webových aplikací: chyby a řešení potíží](../debugger/debugging-web-applications-errors-and-troubleshooting.md)
