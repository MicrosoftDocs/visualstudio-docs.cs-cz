---
description: Volá se, když se otevře soubor kandidát. pdb.
title: 'IDiaLoadCallback:: NotifyOpenPDB | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaLoadCallback::NotifyOpenPDB method
ms.assetid: c0547f99-8468-4e57-82ca-9ef7d6707c8a
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: ab1f72c6f22f70bb94262c57327ab91f96a02183
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2021
ms.locfileid: "102148295"
---
# <a name="idialoadcallbacknotifyopenpdb"></a>IDiaLoadCallback::NotifyOpenPDB
Volá se, když se otevře soubor kandidát. pdb.

## <a name="syntax"></a>Syntaxe

```C++
HRESULT NotifyOpenPDB ( 
   LPCOLESTR pdbPath,
   HRESULT   resultCode
);
```

#### <a name="parameters"></a>Parametry
 `pdbPath`

pro Úplná cesta k souboru. pdb.

 `resultCode`

pro Kód, který označuje úspěch ( `S_OK` ) nebo selhání zatížení, které je použito pro tento soubor.

## <a name="return-value"></a>Návratová hodnota
 V případě úspěchu vrátí. `S_OK` jinak vrátí kód chyby. Návratový kód se obvykle ignoruje.

## <a name="see-also"></a>Viz také
- [IDiaLoadCallback2](../../debugger/debug-interface-access/idialoadcallback2.md)
