---
description: Vyhledá zadaný rámec zásobníku pro návratovou adresu na zadané adrese zásobníku nebo v ní.
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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 5dfda60c2be8f7900a8b2fc0db54e4801c628bb7
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2021
ms.locfileid: "102156767"
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
