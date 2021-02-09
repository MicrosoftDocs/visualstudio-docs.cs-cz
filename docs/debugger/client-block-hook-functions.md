---
title: Funkce zavěšení bloků klienta | Microsoft Docs
description: Zapište funkci zavěšení bloku klienta pro ověření nebo nahlášení obsahu dat uložených v blocích _CLIENT_BLOCK.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 0378f2260a9bf71cf7ac1192b7eb7a2259d8ace2
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99865875"
---
# <a name="client-block-hook-functions"></a>Funkce háku bloku klienta
Pokud chcete ověřit nebo ohlásit obsah dat uložených v `_CLIENT_BLOCK` blocích, můžete napsat funkci specificky pro tento účel. Funkce, kterou napíšete, musí mít prototyp podobný následujícímu, jak je definováno v souboru Crtdbg. Y

```cpp
void YourClientDump(void *, size_t)
```

 Jinými slovy, funkce vidlice by měla přijmout ukazatel **void** na začátek bloku přidělení spolu s hodnotou **size_t** typ udávající velikost přidělení a vrátit `void` . Kromě toho je jeho obsah až na vás.

 Jakmile nainstalujete funkci Hooku pomocí [_CrtSetDumpClient](/cpp/c-runtime-library/reference/crtsetdumpclient), bude volána pokaždé, když `_CLIENT_BLOCK` je blok v dumpingu. Pak můžete použít [_CrtReportBlockType](/cpp/c-runtime-library/reference/crtreportblocktype) k získání informací o typu nebo podtypu dumpingových bloků.

 Ukazatel na funkci, kterou předáte, `_CrtSetDumpClient` je typu **_CRT_DUMP_CLIENT**, jak je definováno v souboru Crtdbg. Y

```cpp
typedef void (__cdecl *_CRT_DUMP_CLIENT)
   (void *, size_t);
```

## <a name="see-also"></a>Viz také

- [Zápis funkce zavěšení ladění](../debugger/debug-hook-function-writing.md)
- [Ukázka crt_dbg2](/previous-versions/b31tft51(v=vs.100))
- [_CrtReportBlockType](/cpp/c-runtime-library/reference/crtreportblocktype)