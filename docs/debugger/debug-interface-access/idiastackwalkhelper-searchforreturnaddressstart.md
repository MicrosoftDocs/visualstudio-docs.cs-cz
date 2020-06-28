---
title: 'IDiaStackWalkHelper:: Searchforreturnaddressstart – | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaStackWalkHelper::searchForReturnAddressStart method
ms.assetid: 0a33142e-5d31-44ea-874a-a2e94d95cbd2
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 68fbecf9dd085ec229f42a5af12b48d1a712ee1f
ms.sourcegitcommit: 66f31cc4ce1236e638ab58d2f70d3646206386fa
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/27/2020
ms.locfileid: "85464679"
---
# <a name="idiastackwalkhelpersearchforreturnaddressstart"></a>IDiaStackWalkHelper::searchForReturnAddressStart
Vyhledá zadaný rámec zásobníku pro návratovou adresu na zadané adrese zásobníku nebo v ní.

## <a name="syntax"></a>Syntaxe

```C++
HRESULT searchForReturnAddressStart( 
   IDiaFrameData*  frame,
   ULONGLONG       startAddress,
   ULONGLONG*      returnAddress
);
```

#### <a name="parameters"></a>Parametry
 `frame`

pro Objekt [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md) , který představuje aktuální rámec zásobníku.

 `startAddress`

pro Adresa virtuální paměti, ze které se má začít hledat.

 `ReturnAddress`

mimo Vrátí nejbližší návratovou adresu funkce `startAddress` .

## <a name="return-value"></a>Návratová hodnota
 V případě úspěchu vrátí. `S_OK` jinak vrátí kód chyby.

## <a name="see-also"></a>Viz také
- [IDiaStackWalkHelper](../../debugger/debug-interface-access/idiastackwalkhelper.md)
- [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)