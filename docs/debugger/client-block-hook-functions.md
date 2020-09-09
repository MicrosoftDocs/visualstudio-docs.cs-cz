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
ms.openlocfilehash: 881809dda7e8254f9d337b68f0c317eccfd9093d
ms.sourcegitcommit: ed4372bb6f4ae64f1fd712b2b253bf91d9ff96bf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/09/2020
ms.locfileid: "89600197"
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

- [Zápis funkce háku ladění](../debugger/debug-hook-function-writing.md)
- [Ukázka crt_dbg2](/previous-versions/b31tft51(v=vs.100))
- [_CrtReportBlockType](/cpp/c-runtime-library/reference/crtreportblocktype)