---
title: Smíšený kód a chybějící informace v okně zásobník volání | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: troubleshooting
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
- SQL
helpviewer_keywords:
- managed code, stepping
- Call Stack window, mixed-mode debugging
- Call Stack window, troubleshooting
- native frames
- managed call stacks
- mixed-mode debugging, call stack
- stepping, out of managed code
ms.assetid: dd628427-e8d6-4fc2-b524-9d6393ea5376
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: cdcde5a0a597d038015c80f5d26add66158542ff
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49850929"
---
# <a name="mixed-code-and-missing-information-in-the-call-stack-window"></a>Smíšený kód a chybějící informace v okně Zásobník volání
Kvůli rozdílům mezi zásobníky volání pro spravovaný a nativní kód nelze ladicí program vždy zobrazit úplný zásobník volání, když kód kombinace. Když nativní kód volá spravovaný kód, můžete si všimnout následující rozdíly v **zásobník volání** okno:  
  
- Nativní rámce přímo nad spravovaného kódu můžou chybět **zásobník volání** okna. Další informace najdete v tématu [postupy: vystoupení ze spravovaného kódu, pokud v okně zásobník volání chybějí nativní rámce](../debugger/how-to-step-out-of-managed-code-when-native-frames-are-missing-from-the-call-stack-window.md).  
  
- Pro aplikace ve smíšeném režimu spustí mimo ladicí program **zásobník volání** okně může zobrazit pouze spravovaný kód a žádný z nativní rámce se nebude zobrazovat.  
  
  Obě jsou velmi malý. Zásobníky volání v nejvíce nativní volání spravovaného kódu, zobrazovat správně.  
  
## <a name="see-also"></a>Viz také  
 [Postupy: Použití okna Zásobník volání](../debugger/how-to-use-the-call-stack-window.md)