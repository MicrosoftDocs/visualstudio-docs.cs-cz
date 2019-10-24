---
title: Dialogové okno Microsoft Visual Studioho ladicího programu (vyvolána výjimka) | Microsoft Docs
titleSuffix: ''
ms.custom: seodec18
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.debug.exceptions.thrown
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- Microsoft Visual Studio Debugger (Exception Thrown) dialog box
- exception handling, during debugging
- debugger, exceptions
- throwing exceptions, during debugging
ms.assetid: 1fe98d10-c8f9-4b39-a920-99169bfd542e
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 8376d0cd82e309c2c8db94e38b8c6a2083bd429a
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/22/2019
ms.locfileid: "72731200"
---
# <a name="microsoft-visual-studio-debugger-exception-thrown-dialog-box"></a>Dialogové okno programu Microsoft Visual Studio Debugger (vyvolána výjimka)
V programu došlo k výjimce. Toto dialogové okno oznamuje druh vyvolané výjimky. Váš kód musí zpracovat tuto výjimku. Pro zpracování výjimky si můžete vybrat z následujících možností:

 **Přerušení** Umožňuje spuštění přerušit do ladicího programu. Obslužná rutina výjimky není vyvolána před přerušením. Pokud budete pokračovat od přerušení, bude vyvolána obslužná rutina výjimky.

 **Pokračovat** Umožňuje pokračovat v provádění, což dává obslužné rutině výjimky možnost zpracovat výjimku. Tato možnost není k dispozici pro určité typy výjimek. **Pokračovat** umožní aplikaci pokračovat. V nativní aplikaci způsobí vyvolání výjimky. Ve spravované aplikaci způsobí buď ukončení programu, nebo výjimku, kterou má zpracovat hostitelská aplikace.

> [!NOTE]
> Po neošetřené výjimce ve spravovaném kódu nemůžete pokračovat. Výběr možnosti **pokračovat** po neošetřené výjimce ve spravovaném kódu způsobí zastavení ladění.

 **Ignorovat** Umožňuje pokračovat v provádění bez vyvolání obslužné rutiny výjimky. Vzhledem k tomu, že obslužná rutina výjimky není vyvolána, může to vést k dalším důsledkům, včetně dalších výjimek a chyb. Tato možnost není k dispozici pro určité typy výjimek.

## <a name="see-also"></a>Viz také:
- [Správa výjimek pomocí ladicího programu](../debugger/managing-exceptions-with-the-debugger.md)
- [Doporučené postupy pro výjimky](/dotnet/standard/exceptions/best-practices-for-exceptions)
- [Zpracování výjimek](/cpp/extensions/exception-handling-cpp-component-extensions)