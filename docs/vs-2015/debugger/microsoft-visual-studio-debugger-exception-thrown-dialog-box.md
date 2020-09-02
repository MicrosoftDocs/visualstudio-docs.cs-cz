---
title: Dialogové okno Microsoft Visual Studioho ladicího programu (vyvolána výjimka) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.exceptions.thrown
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- Microsoft Visual Studio Debugger (Exception Thrown) dialog box
- exception handling, during debugging
- debugger, exceptions
- throwing exceptions, during debugging
ms.assetid: 1fe98d10-c8f9-4b39-a920-99169bfd542e
caps.latest.revision: 13
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 9062b1f3811b0b2b596cfb7fa016bca00143f332
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "66261072"
---
# <a name="microsoft-visual-studio-debugger-exception-thrown-dialog-box"></a>Dialogové okno programu Microsoft Visual Studio Debugger (vyvolána výjimka)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

V programu došlo k výjimce. Toto dialogové okno oznamuje druh vyvolané výjimky. Váš kód musí zpracovat tuto výjimku. Pro zpracování výjimky si můžete vybrat z následujících možností:  
  
 **Rozdělován**  
 Umožňuje spuštění přerušit do ladicího programu. Obslužná rutina výjimky není vyvolána před přerušením. Pokud budete pokračovat od přerušení, bude vyvolána obslužná rutina výjimky.  
  
 **Pokračovat**  
 Umožňuje pokračovat v provádění, což dává obslužné rutině výjimky možnost zpracovat výjimku. Tato možnost není k dispozici pro určité typy výjimek. **Pokračovat** umožní aplikaci pokračovat. V nativní aplikaci způsobí vyvolání výjimky. Ve spravované aplikaci způsobí buď ukončení programu, nebo výjimku, kterou má zpracovat hostitelská aplikace.  
  
> [!NOTE]
> Po neošetřené výjimce ve spravovaném kódu nemůžete pokračovat. Výběr možnosti **pokračovat** po neošetřené výjimce ve spravovaném kódu způsobí zastavení ladění.  
  
 **Ignorovat**  
 Umožňuje pokračovat v provádění bez vyvolání obslužné rutiny výjimky. Vzhledem k tomu, že obslužná rutina výjimky není vyvolána, může to vést k dalším důsledkům, včetně dalších výjimek a chyb. Tato možnost není k dispozici pro určité typy výjimek.  
  
## <a name="see-also"></a>Viz také  
 [Správa výjimek pomocí ladicího programu](../debugger/managing-exceptions-with-the-debugger.md)   
 [Osvědčené postupy pro výjimky](https://msdn.microsoft.com/library/f06da765-235b-427a-bfb6-47cd219af539)   
 [Zpracování výjimek](/cpp/extensions/exception-handling-cpp-component-extensions)
