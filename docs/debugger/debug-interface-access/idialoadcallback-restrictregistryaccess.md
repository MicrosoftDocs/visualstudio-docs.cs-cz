---
title: 'IDiaLoadCallback:: RestrictRegistryAccess | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaLoadCallback::RestrictRegistryAccess method
ms.assetid: de4760c3-a746-4bab-8065-1388fed31b67
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 18436d28fbee7ba12cea2398eb1fa6abbd8ac23b
ms.sourcegitcommit: 66f31cc4ce1236e638ab58d2f70d3646206386fa
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/27/2020
ms.locfileid: "85466733"
---
# <a name="idialoadcallbackrestrictregistryaccess"></a>IDiaLoadCallback::RestrictRegistryAccess
Určuje, zda lze dotazy registru použít k vyhledání cest hledání symbolů.

## <a name="syntax"></a>Syntax

```C++
HRESULT RestrictRegistryAccess();
```

## <a name="return-value"></a>Návratová hodnota
 V případě úspěchu vrátí. `S_OK` jinak vrátí kód chyby.

## <a name="remarks"></a>Poznámky
 Libovolný návratový kód jiný než `S_OK` brání v dotazování registru pro cesty pro hledání symbolů.

## <a name="see-also"></a>Viz také
- [IDiaLoadCallback2](../../debugger/debug-interface-access/idialoadcallback2.md)