---
title: Dialogové okno chybové zprávy pro úpravy a pokračování | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.ENC.SupportedButNotAvailable
- vs.debug.ENC.CannotEditWhileException
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- Edit and Continue Error Message dialog box
ms.assetid: f98c91c0-447a-4533-85b6-87170a0dc4c3
caps.latest.revision: 15
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 5437ef982309ef8595f08283f2685e93d346e764
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "62428276"
---
# <a name="edit-and-continue-error-message-dialog-box"></a>Dialogové okno chybových zpráv operace Upravit a pokračovat
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Toto dialogové okno se zobrazí při ladění v jazyce, který podporuje úpravu a pokračování, ale příkaz **Upravit a pokračovat** není k dispozici pro typ změny kódu, které jste provedli. Chybová zpráva v poli poskytuje podrobnější vysvětlení. Mezi možné důvody pro zobrazení tohoto dialogového okna patří:  
  
- Byl proveden pokus o úpravu spravovaného kódu, pokud bylo povoleno nespravované ladění. Příkaz Upravit a pokračovat nefunguje s laděním ve smíšeném režimu.  
  
- Pokusili jste se upravit kód SQL Server.  
  
- Při ladění výpisu Dr. Watson jste zkusili kód upravit.  
  
- Pokusili jste se upravit kód po výskytu neošetřené výjimky a nevybrali jste možnost**unwind zásobník volání u neošetřených výjimek**.  
  
- Došlo k pokusu o úpravu kódu při ladění vložené aplikace modulu runtime.  
  
- Pokusili jste se upravit kód v programu, který jste připojili místo spuštění z nabídky **ladění** .  
  
- Byl proveden pokus o úpravu optimalizovaného kódu.  
  
- Byl proveden pokus o úpravu spravovaného kódu, pokud je cílem 64 aplikace. Pokud chcete použít příkaz Upravit a pokračovat, musíte nastavit cíl na x86. (*Project* **Vlastnosti**projektu, karta **kompilovat** , **Pokročilé nastavení kompilátoru** .)  
  
- Pokusili jste se upravit kód v sestavení, které bylo upraveno během ladění a bylo znovu načteno.  
  
- Pokusili jste se upravit kód v sestavení, které nebylo načteno.  
  
- Začali jste ladit starou verzi aplikace (vzhledem k tomu, že nová verze obsahuje chyby sestavení).  
  
- Pokusili jste se upravit kód při jeho spuštění.  
  
## <a name="uielement-list"></a>Seznam prvků uživatelského rozhraní  
 **OK**  
 Zavřete dialogové okno a zrušte hned předchozí pokus o úpravu.  
  
## <a name="see-also"></a>Viz také  
 [Podporované změny kódu (C++)](../debugger/supported-code-changes-cpp.md)
