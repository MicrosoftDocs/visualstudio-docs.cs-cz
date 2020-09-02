---
title: Ukončit probíhající ladění – dialogové okno | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
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
manager: jillfra
ms.openlocfilehash: 4fc4b72987be726ab06aeb92a0e3eec2a338949e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "65684952"
---
# <a name="stop-debugging-in-progress-dialog-box"></a>Dialogové okno Ukončit probíhající ladění
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Toto dialogové okno se zobrazí, když se ladicí program pokouší zastavit relaci ladění, ale zastavení relace bude nějakou dobu trvat. Zastavení relace ladění je obvykle velmi rychlé a toto dialogové okno se nezobrazí. V některých případech ale může trvat i déle, než se odpojí všechny procesy, které jsou laděny. Pokud zastavování relace trvá déle než několik sekund (nebo dojde k chybě odpojení), zobrazí se toto dialogové okno. Pokud k tomu dochází často, může to být způsobeno interním problémem a možná budete chtít kontaktovat služby technické podpory.  
  
 Můžete počkat, až se procesy odpojí a toto dialogové okno zmizí, nebo použijte tlačítko **Zastavit nyní** k vynucení okamžitého ukončení.  
  
 **Zastavit hned**  
 Kliknutím na toto tlačítko ukončíte ladicí relaci okamžitě. Místo odpojení procesů, které se právě ladí, bude použití operace **Zastavit nyní**ukončeno. Pokud ladíte systémové procesy, ukončení těchto procesů pomocí **stop Now** může mít neočekávané a nežádoucí účinky.  
  
## <a name="see-also"></a>Viz také  
 [Zabezpečení ladicího programu](../debugger/debugger-security.md)   
 [Odpojování programů](https://msdn.microsoft.com/f2c756c2-8079-474b-94c2-01c19a141a01)
