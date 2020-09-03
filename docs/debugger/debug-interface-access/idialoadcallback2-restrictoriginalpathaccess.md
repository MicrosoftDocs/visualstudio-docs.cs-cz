---
title: 'IDiaLoadCallback2:: RestrictOriginalPathAccess | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaLoadCallback2::RestrictOriginalPathAccess method
ms.assetid: 31fde3af-2824-4b0f-8d0d-cee6046596f6
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 784e17ddf6202419618b7ff3b8836f0f46021989
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "85466684"
---
# <a name="idialoadcallback2restrictoriginalpathaccess"></a>IDiaLoadCallback2::RestrictOriginalPathAccess
Určuje, zda je v pořádku hledání souboru PDB v původním adresáři pro ladění.

## <a name="syntax"></a>Syntax

```C++
HRESULT RestrictOriginalPathAccess ();
```

## <a name="return-value"></a>Návratová hodnota
 V případě úspěchu vrátí. `S_OK` jinak vrátí kód chyby.

## <a name="remarks"></a>Poznámky
 Libovolný návratový kód jiný než `S_OK` zabrání v původním ladicím adresáři vyhledat soubor. pdb. Původní ladicí adresář je cesta k souboru symbolů kompilovaný do spustitelného souboru, když je zapnuto ladění. Tato cesta není nutně stejná jako cesta, ve které spustitelný soubor existuje.

## <a name="see-also"></a>Viz také
- [IDiaLoadCallback2](../../debugger/debug-interface-access/idialoadcallback2.md)