---
description: Určuje, zda je povoleno hledání informací o ladění ze souborů. dbg.
title: 'IDiaLoadCallback2:: RestrictDBGAccess | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaLoadCallback2::RestrictDBGAccess method
ms.assetid: 63b67a93-2910-4fff-aa70-6b2eaa08e5c8
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 529d617b833a6dc3013a71f5c132ca5654c89d08
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2021
ms.locfileid: "102148267"
---
# <a name="idialoadcallback2restrictdbgaccess"></a>IDiaLoadCallback2::RestrictDBGAccess
Určuje, zda je povoleno hledání informací o ladění ze souborů. dbg.

## <a name="syntax"></a>Syntax

```C++
HRESULT RestrictDBGAccess();
```

## <a name="return-value"></a>Návratová hodnota
 V případě úspěchu vrátí. `S_OK` jinak vrátí kód chyby.

## <a name="remarks"></a>Poznámky
 Libovolná návratová hodnota `S_OK` , která není zabráněno v hledání ladicích informací ze souborů. dbg.

## <a name="see-also"></a>Viz také
- [IDiaLoadCallback2](../../debugger/debug-interface-access/idialoadcallback2.md)
