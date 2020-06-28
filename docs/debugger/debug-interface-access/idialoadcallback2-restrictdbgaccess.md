---
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 8fd54587127d434f79cf8d80aa130f5135bb7aeb
ms.sourcegitcommit: 66f31cc4ce1236e638ab58d2f70d3646206386fa
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/27/2020
ms.locfileid: "85466712"
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