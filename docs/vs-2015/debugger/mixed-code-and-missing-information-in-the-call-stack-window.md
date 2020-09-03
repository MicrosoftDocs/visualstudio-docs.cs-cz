---
title: Smíšený kód a chybějící informace v okně zásobník volání | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
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
manager: jillfra
ms.openlocfilehash: 3995e14379fa4bd3ebd5cc276613c288b4437d35
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "68193276"
---
# <a name="mixed-code-and-missing-information-in-the-call-stack-window"></a>Smíšený kód a chybějící informace v okně Zásobník volání
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Z důvodu rozdílů mezi zásobníky volání pro spravovaný a nativní kód nemůže ladicí program vždy zobrazit kompletní zásobník volání, když jsou typy kódu smíšeny. Pokud nativní kód volá spravovaný kód, můžete si všimnout následujících nedostatků v okně **zásobník volání** :  
  
- V okně **zásobník volání** může chybět nativní rámec hned nad spravovaným kódem. Další informace naleznete v tématu [Postup: krokování ze spravovaného kódu, pokud v okně zásobník volání chybějí nativní rámce](../debugger/how-to-step-out-of-managed-code-when-native-frames-are-missing-from-the-call-stack-window.md).  
  
- V případě aplikací se smíšeným režimem, které jsou spouštěny mimo ladicí program, může okno **zásobník volání** zobrazit pouze spravovaný kód a žádný z nativních snímků nebude viditelný.  
  
  Oba případy jsou poměrně zřídka. Ve většině nativních volání spravovaného kódu se zásobníky volání zobrazují správně.  
  
## <a name="see-also"></a>Viz také  
 [Postupy: Použití okna Zásobník volání](../debugger/how-to-use-the-call-stack-window.md)
