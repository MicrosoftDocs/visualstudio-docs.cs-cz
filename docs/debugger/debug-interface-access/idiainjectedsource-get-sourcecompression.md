---
description: Načte indikátor použité zdrojové komprese.
title: 'IDiaInjectedSource:: get_sourceCompression | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaInjectedSource::get_sourceCompression method
ms.assetid: 854b142f-23a9-466c-bf7f-98e581d5abcd
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 868c89da413372e5793f92a5df6bb74c02207421
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2021
ms.locfileid: "102148407"
---
# <a name="idiainjectedsourceget_sourcecompression"></a>IDiaInjectedSource::get_sourceCompression
Načte indikátor použité zdrojové komprese.

## <a name="syntax"></a>Syntaxe

```C++
HRESULT get_sourceCompression ( 
   DWORD* pRetVal
);
```

#### <a name="parameters"></a>Parametry
 `pRetVal`

mimo Vrátí indikátor použité zdrojové komprese. Hodnota nula znamená, že se nepoužila žádná zdrojová komprese.

## <a name="return-value"></a>Návratová hodnota
 V případě úspěchu vrátí `S_OK` . Vrátí `S_FALSE` , pokud tato vlastnost není podporována. V opačném případě vrátí kód chyby.

## <a name="remarks"></a>Poznámky
 Hodnota vrácená touto metodou je specifická pro použitý kompilátor. Kompilátor může například použít Run-Length kódování nebo komprese ve stylu Huffmanova.

## <a name="see-also"></a>Viz také
- [IDiaInjectedSource](../../debugger/debug-interface-access/idiainjectedsource.md)
