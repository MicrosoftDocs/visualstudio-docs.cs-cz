---
title: Pokračování v provádění po výjimce | Microsoft Docs
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
manager: jillfra
ms.openlocfilehash: 6ae74c51f0f738bc596fbe5c789011630927707c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "65702257"
---
# <a name="continuing-execution-after-an-exception"></a>Pokračování v provádění po výjimce
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Pokud ladicí program přeruší provádění kvůli výjimce, zobrazí se dialogové okno. V případě Visual Basic nebo C# se ve výchozím nastavení zobrazí dialogové okno [Pomocník pro výjimky](https://msdn.microsoft.com/library/992892ac-9d52-44cc-bf09-b44bfc5befeb) . V jazyce C++ se zobrazí dialogové okno starší **výjimka** . Pokud používáte Visual Basic nebo C#, ale v dialogovém okně **Možnosti** jste zakázali **Pomocníka s výjimkou** , zobrazí se dialogové okno **výjimka** .  
  
 Když se zobrazí dialogové okno **Pomocník pro výjimky** nebo **výjimka** , můžete zkusit vyřešit problém, který způsobil výjimku.  
  
## <a name="managed-code"></a>Spravovaný kód  
 Ve spravovaném kódu můžete pokračovat v provádění ve stejném vlákně po neošetřené výjimce. **Pomocník pro výjimky** odvíjí zásobník volání do bodu, kde byla vyvolána výjimka.  
  
## <a name="native-code"></a>Nativní kód  
 V nativním C/C++ máte dvě možnosti:  
  
- Můžete kliknout na **přerušení** a pokusit se opravit problém. Když jste v režimu pozastavení, můžete zásobník volání zrušit tak, že pravým tlačítkem myši kliknete na snímek v okně **zásobník volání** a v místní nabídce vyberete **možnost vrátit zpět k tomuto snímku** . Když budete pokračovat v ladění, dialogové okno **výjimky** se zobrazí znovu, pokud jste problém nevyřešili. V opačném případě se dialogové okno **výjimky** znovu nezobrazí.  
  
- Kliknutím na **pokračovat** můžete pokračovat v provádění bez pokusu o vyřešení problému. Dialogové okno **výjimky** se znovu zobrazí.  
  
## <a name="mixed-code"></a>Smíšený kód  
 Pokud při ladění smíšeného nativního a spravovaného kódu dojde k neošetřené výjimce, omezení operačního systému zabrání odvinutí zásobníku volání. Pokud se pokusíte převinout zásobník volání pomocí místní nabídky, zobrazí se chybová zpráva s vysvětlením, že ladicí program nemůže provést zpětnou akci před neošetřenou výjimkou při ladění smíšeného kódu.  
  
## <a name="see-also"></a>Viz také  
 [Správa výjimek pomocí ladicího programu](../debugger/managing-exceptions-with-the-debugger.md)
