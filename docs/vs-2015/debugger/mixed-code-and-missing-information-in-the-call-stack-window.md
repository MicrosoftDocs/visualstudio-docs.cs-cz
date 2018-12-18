---
title: Smíšený kód a chybějící informace v okně zásobník volání | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- FSharp
- VB
- CSharp
- C++
- JScript
- SQL
- VB
- CSharp
- C++
helpviewer_keywords:
- managed code, stepping
- Call Stack window, mixed-mode debugging
- Call Stack window, troubleshooting
- native frames
- managed call stacks
- mixed-mode debugging, call stack
- stepping, out of managed code
ms.assetid: dd628427-e8d6-4fc2-b524-9d6393ea5376
caps.latest.revision: 23
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 6f4ae8e527e5f6ce04680c444baad58802bfad48
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51788925"
---
# <a name="mixed-code-and-missing-information-in-the-call-stack-window"></a>Smíšený kód a chybějící informace v okně Zásobník volání
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Kvůli rozdílům mezi zásobníky volání pro spravovaný a nativní kód nelze ladicí program vždy zobrazit úplný zásobník volání, když kód kombinace. Když nativní kód volá spravovaný kód, můžete si všimnout následující rozdíly v **zásobník volání** okno:  
  
- Nativní rámce přímo nad spravovaného kódu můžou chybět **zásobník volání** okna. Další informace najdete v tématu [postupy: vystoupení ze spravovaného kódu, pokud v okně zásobník volání chybějí nativní rámce](../debugger/how-to-step-out-of-managed-code-when-native-frames-are-missing-from-the-call-stack-window.md).  
  
- Pro aplikace ve smíšeném režimu spustí mimo ladicí program **zásobník volání** okně může zobrazit pouze spravovaný kód a žádný z nativní rámce se nebude zobrazovat.  
  
  Obě jsou velmi malý. Zásobníky volání v nejvíce nativní volání spravovaného kódu, zobrazovat správně.  
  
## <a name="see-also"></a>Viz také  
 [Postupy: Použití okna Zásobník volání](../debugger/how-to-use-the-call-stack-window.md)





