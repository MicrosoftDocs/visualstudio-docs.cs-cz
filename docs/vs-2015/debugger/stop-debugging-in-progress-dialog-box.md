---
title: Zastavit ladění do dialogového okna průběhu | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.debug.stopnow
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
- Stop Debugging in Progress dialog box
ms.assetid: ed7ef49d-e25f-4a4d-9396-9bc7b4143117
caps.latest.revision: 10
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 2dba046c57e7b3990b3bf31994da699bed1e6442
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51792278"
---
# <a name="stop-debugging-in-progress-dialog-box"></a>Dialogové okno Ukončit probíhající ladění
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Toto dialogové okno se zobrazí, když ladicí program se pokouší zastavit ladicí relace, ale zastavuje se relace je, že přejdete na nějakou dobu trvat. Zastavuje se relace ladění je obvykle velmi rychlý a toto dialogové okno se nezobrazí. V některých případech však trvá určitou dobu trvat odpojit od všech procesů, který se právě ladí. Zastavuje se relace trvá déle než několik sekund (nebo pokud dojde k chybě odpojení), zobrazí se toto dialogové okno. Pokud k tomu dochází často, může být kvůli internímu problému a můžete chtít obraťte se na oddělení technické podpory.  
  
 Počkejte procesy, které chcete odpojit a toto dialogové okno zmizí, nebo použijte **Zastavit** tlačítko vynutit okamžité ukončení.  
  
 **Zastavit nyní**  
 Kliknutím na toto tlačítko k ukončení relace ladění okamžitě. Pomocí **Zastavit**bude ukončen, spíše než odpojování procesů, který se právě ladí. Pokud ladíte systémové procesy, ukončuje se tyto procesy s **Zastavit** může mít neočekávané a nežádoucí účinky.  
  
## <a name="see-also"></a>Viz také  
 [Zabezpečení ladicího programu](../debugger/debugger-security.md)   
 [Odpojuje se programy](http://msdn.microsoft.com/en-us/f2c756c2-8079-474b-94c2-01c19a141a01)



