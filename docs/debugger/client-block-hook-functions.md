---
title: Funkce zavěšení bloků klienta | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.debug.hooks
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- client blocks, validating and reporting data
- debugging [C++], hook functions
- _CrtSetDumpClient function
- client blocks, hook functions
- hooks, client block
ms.assetid: f21c197e-565d-4e3f-9b27-4c018c9b87fc
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 5b7b0ef177922f09239c8925ced1ca013e966c0e
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/22/2019
ms.locfileid: "72745709"
---
# <a name="client-block-hook-functions"></a>Funkce háku bloku klienta
Pokud chcete ověřit nebo ohlásit obsah dat uložených v `_CLIENT_BLOCK`ch blocích, můžete napsat funkci specificky pro tento účel. Funkce, kterou napíšete, musí mít prototyp podobný následujícímu, jak je definováno v souboru Crtdbg. Y

```cpp
void YourClientDump(void *, size_t)
```

 Jinými slovy, funkce vidlice by měla přijmout ukazatel **void** na začátek bloku přidělení spolu s hodnotou typu **size_t** udávající velikost přidělení a vracet `void`. Kromě toho je jeho obsah až na vás.

 Po instalaci funkce Hooku pomocí [_CrtSetDumpClient](/cpp/c-runtime-library/reference/crtsetdumpclient)se tato funkce bude volat pokaždé, když je blok `_CLIENT_BLOCK` dumpingové. Pak můžete použít [_CrtReportBlockType](/cpp/c-runtime-library/reference/crtreportblocktype) k získání informací o typu nebo podtypu dumpingových bloků.

 Ukazatel na funkci, kterou předáte `_CrtSetDumpClient`, je typu **_CRT_DUMP_CLIENT**, jak je definováno v souboru Crtdbg. Y

```cpp
typedef void (__cdecl *_CRT_DUMP_CLIENT)
   (void *, size_t);
```

## <a name="see-also"></a>Viz také:

- [Zápis funkce volání pro ladění](../debugger/debug-hook-function-writing.md)
- [Ukázka crt_dbg2](https://msdn.microsoft.com/library/21e1346a-6a17-4f57-b275-c76813089167)
- [_CrtReportBlockType](/cpp/c-runtime-library/reference/crtreportblocktype)