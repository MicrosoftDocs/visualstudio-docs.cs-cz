---
title: Zastavit ladění do dialogového okna průběhu | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: reference
f1_keywords:
- vs.debug.stopnow
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
- SQL
helpviewer_keywords:
- Stop Debugging in Progress dialog box
ms.assetid: ed7ef49d-e25f-4a4d-9396-9bc7b4143117
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 3a6e13967cc18fae8d837cc71ea8a91c60f2b1bb
ms.sourcegitcommit: 1ab675a872848c81a44d6b4bd3a49958fe673c56
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/10/2018
ms.locfileid: "44281192"
---
# <a name="stop-debugging-in-progress-dialog-box"></a>Dialogové okno Ukončit probíhající ladění
Toto dialogové okno se zobrazí, když ladicí program se pokouší zastavit ladicí relace, ale zastavuje se relace je, že přejdete na nějakou dobu trvat. Zastavuje se relace ladění je obvykle velmi rychlý a toto dialogové okno se nezobrazí. V některých případech však trvá určitou dobu trvat odpojit od všech procesů, který se právě ladí. Zastavuje se relace trvá déle než několik sekund (nebo pokud dojde k chybě odpojení), zobrazí se toto dialogové okno. Pokud k tomu dochází často, může být kvůli internímu problému a můžete chtít obraťte se na oddělení technické podpory.  
  
 Počkejte procesy, které chcete odpojit a toto dialogové okno zmizí, nebo použijte **Zastavit** tlačítko vynutit okamžité ukončení.  
  
 **Zastavit nyní**  
 Kliknutím na toto tlačítko k ukončení relace ladění okamžitě. Pomocí **Zastavit** bude ukončen, spíše než odpojování procesů, který se právě ladí. Pokud ladíte systémové procesy, ukončuje se tyto procesy s **Zastavit** může mít neočekávané a nežádoucí účinky.  
  
## <a name="see-also"></a>Viz také  
 [Zabezpečení ladicího programu](../debugger/debugger-security.md)   
 [Odpojuje se programy](/previous-versions/visualstudio/visual-studio-2010/x1thkxez(v=vs.100))