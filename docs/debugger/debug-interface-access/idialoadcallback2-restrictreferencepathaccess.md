---
title: 'IDiaLoadCallback2:: RestrictReferencePathAccess | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaLoadCallback2::RestrictReferencePathAccess method
ms.assetid: e20cb45c-0360-4ff0-a92c-b1b6f76d6e85
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 32cad25220cc2248039e4b64c158092ffee8431f
ms.sourcegitcommit: 66f31cc4ce1236e638ab58d2f70d3646206386fa
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/27/2020
ms.locfileid: "85466628"
---
# <a name="idialoadcallback2restrictreferencepathaccess"></a>IDiaLoadCallback2::RestrictReferencePathAccess
Určuje, zda je v cestě, kde je umístěn soubor. exe, povolen soubor. pdb.

## <a name="syntax"></a>Syntax

```C++
HRESULT RestrictReferencePathAccess();
```

## <a name="return-value"></a>Návratová hodnota
 V případě úspěchu vrátí. `S_OK` jinak vrátí kód chyby.

## <a name="remarks"></a>Poznámky
 Libovolný návratový kód jiný než `S_OK` pro zabránění v hledání souboru. pdb v cestě, kde se nachází soubor. exe.

## <a name="see-also"></a>Viz také
- [IDiaLoadCallback2](../../debugger/debug-interface-access/idialoadcallback2.md)