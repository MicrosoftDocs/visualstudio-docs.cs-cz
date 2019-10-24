---
title: Ukončit probíhající ladění – dialogové okno | Microsoft Docs
ms.date: 11/04/2016
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 3beefe16f8883eb64d7d0a2641cabf9eb1f702fa
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/22/2019
ms.locfileid: "72729660"
---
# <a name="stop-debugging-in-progress-dialog-box"></a>Dialogové okno Ukončit probíhající ladění
Toto dialogové okno se zobrazí, když se ladicí program pokouší zastavit relaci ladění, ale zastavení relace bude nějakou dobu trvat. Zastavení relace ladění je obvykle velmi rychlé a toto dialogové okno se nezobrazí. V některých případech ale může trvat i déle, než se odpojí všechny procesy, které jsou laděny. Pokud zastavování relace trvá déle než několik sekund (nebo dojde k chybě odpojení), zobrazí se toto dialogové okno. Pokud k tomu dochází často, může to být způsobeno interním problémem a možná budete chtít kontaktovat služby technické podpory.

 Můžete počkat, až se procesy odpojí a toto dialogové okno zmizí, nebo použijte tlačítko **Zastavit nyní** k vynucení okamžitého ukončení.

 **Zastavit hned** Kliknutím na toto tlačítko ukončíte ladicí relaci okamžitě. Místo odpojení procesů, které se právě ladí, bude použití operace **Zastavit nyní** ukončeno. Pokud ladíte systémové procesy, ukončení těchto procesů pomocí **stop Now** může mít neočekávané a nežádoucí účinky.

## <a name="see-also"></a>Viz také:
- [Zabezpečení ladicího programu](../debugger/debugger-security.md)
- [Odpojování programů](/previous-versions/visualstudio/visual-studio-2010/x1thkxez(v=vs.100))