---
title: Pokračování v provádění po výjimce | Dokumentace Microsoftu
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
- VB
- CSharp
- C++
helpviewer_keywords:
- managed exceptions, continuing execution after
- exceptions, continuing execution after
- debugger, exceptions
- managed code, exception handling
- exception handling, continuing execution after
- execution, continuing after an exception
- program execution
- threading [Visual Studio], continuing execution after exceptions
- Exceptions dialog box
- programs, executing
ms.assetid: 6fe97aac-2131-4615-bd92-d3afee741558
caps.latest.revision: 30
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 947a17993fe0e8366149d1cef79c26c68b11d22a
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51730035"
---
# <a name="continuing-execution-after-an-exception"></a>Pokračování v provádění po výjimce
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Pokud ladicí program přeruší provádění z důvodu výjimky, zobrazí se dialogové okno. Visual Basic nebo C#, zobrazí se [pomocníka pro výjimky](http://msdn.microsoft.com/library/992892ac-9d52-44cc-bf09-b44bfc5befeb) dialogové okno, ve výchozím nastavení. Pro jazyk C++, zobrazí se starší **výjimka** dialogové okno. Pokud používáte Visual Basic nebo C#, ale jste zakázali **pomocníka pro výjimky** v **možnosti** dialogovém okně se zobrazí **výjimka** dialogové okno.  
  
 Když **pomocníka pro výjimky** nebo **výjimka** se zobrazí dialogové okno, můžete se pokusit opravit problém, který způsobil výjimku.  
  
## <a name="managed-code"></a>Spravovaný kód  
 Ve spravovaném kódu můžete pokračovat v provádění ve stejném vlákně po neošetřené výjimce. **Pomocníka pro výjimky** unwinds zásobník volání do bodu, kde byla výjimka vydána.  
  
## <a name="native-code"></a>Nativní kód  
 V nativním C/C++ máte dvě možnosti:  
  
-   Můžete kliknout na **přerušit** a pokuste se tento problém vyřešit. Při práci v režimu přerušení, lze vrátit zásobník volání kliknutím pravým tlačítkem na snímek v **zásobník volání** okno a vyberete **Unwind k tomuto rámci** v místní nabídce. Když budete pokračovat v ladění, **výjimka** dialogové okno zobrazí znovu, pokud jste problém. V opačném případě **výjimka** neobjeví dialogové okno.  
  
-   Můžete kliknout na **pokračovat** pro pokračování v provádění bez pokusu o vyřešení problému. **Výjimka** se znovu zobrazí dialogové okno.  
  
## <a name="mixed-code"></a>Smíšený kód  
 Pokud dosáhnete neošetřenou výjimku při ladění smíšená nativní a spravované kódové, omezení operačního systému zakázat odvíjení zásobníku volání. Pokud se pokusíte zpět zásobník volání pomocí místní nabídky, chybová zpráva vysvětluje, že ladicí program nelze vrátit zpět z neošetřenou výjimkou během ladění Smíšeného kódu.  
  
## <a name="see-also"></a>Viz také  
 [Správa výjimek pomocí ladicího programu](../debugger/managing-exceptions-with-the-debugger.md)





