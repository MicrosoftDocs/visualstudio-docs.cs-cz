---
title: Funkce zavěšení bloků klienta | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.hooks
dev_langs:
- FSharp
- VB
- CSharp
- C++
- C++
helpviewer_keywords:
- client blocks, validating and reporting data
- debugging [C++], hook functions
- _CrtSetDumpClient function
- client blocks, hook functions
- hooks, client block
ms.assetid: f21c197e-565d-4e3f-9b27-4c018c9b87fc
caps.latest.revision: 18
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: c5b1c754255ba0bc659c9b6968ad8ba0dea629ec
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "65702328"
---
# <a name="client-block-hook-functions"></a>Funkce háku bloku klienta
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Pokud chcete ověřit nebo ohlásit obsah dat uložených v `_CLIENT_BLOCK` blocích, můžete napsat funkci specificky pro tento účel. Funkce, kterou napíšete, musí mít prototyp podobný následujícímu, jak je definováno v souboru Crtdbg. Y  
  
```  
void YourClientDump(void *, size_t)  
  
```  
  
 Jinými slovy, funkce vidlice by měla přijmout ukazatel **void** na začátek bloku přidělení spolu s hodnotou **size_t** typ udávající velikost přidělení a vrátit `void` . Kromě toho je jeho obsah až na vás.  
  
 Jakmile nainstalujete funkci Hooku pomocí [_CrtSetDumpClient](https://msdn.microsoft.com/library/f3dd06d0-c331-4a12-b68d-25378d112033), bude volána pokaždé, když `_CLIENT_BLOCK` je blok v dumpingu. Pak můžete použít [_CrtReportBlockType](https://msdn.microsoft.com/library/0f4b9da7-bebb-4956-9541-b2581640ec6b) k získání informací o typu nebo podtypu dumpingových bloků.  
  
 Ukazatel na funkci, kterou předáte, `_CrtSetDumpClient` je typu **_CRT_DUMP_CLIENT**, jak je definováno v souboru Crtdbg. Y  
  
```  
typedef void (__cdecl *_CRT_DUMP_CLIENT)  
   (void *, size_t);  
```  
  
## <a name="see-also"></a>Viz také  
 [Zápis funkce zavěšení ladění](../debugger/debug-hook-function-writing.md)   
 [Ukázka crt_dbg2](https://msdn.microsoft.com/21e1346a-6a17-4f57-b275-c76813089167)   
 [_CrtReportBlockType](https://msdn.microsoft.com/library/0f4b9da7-bebb-4956-9541-b2581640ec6b)
