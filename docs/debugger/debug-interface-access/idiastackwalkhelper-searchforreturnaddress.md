---
description: 'IDiaStackWalkHelper:: Searchforreturnaddress – vyhledá zadaný rámec zásobníku pro nejbližší návratovou adresu funkce.'
title: 'IDiaStackWalkHelper:: Searchforreturnaddress – | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaStackWalkHelper2::searchForReturnAddress method
ms.assetid: 904223b1-6e26-4980-b310-d0b222cdbbbd
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 887737ac28204d9abdbf3b7002233af6d0b2e465
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2021
ms.locfileid: "102156809"
---
# <a name="idiastackwalkhelpersearchforreturnaddress"></a>IDiaStackWalkHelper::searchForReturnAddress
Vyhledá zadaný rámec zásobníku pro nejbližší návratovou adresu funkce.

## <a name="syntax"></a>Syntaxe

```C++
HRESULT searchForReturnAddress( 
   IDiaFrameData*  frame,
   ULONGLONG*      returnAddress
);
```

#### <a name="parameters"></a>Parametry
 `frame`

pro Objekt [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md) , který představuje aktuální rámec zásobníku.

 `returnAddress`

mimo Vrátí nejbližší návratovou adresu funkce.

## <a name="return-value"></a>Návratová hodnota
 V případě úspěchu vrátí. `S_OK` jinak vrátí kód chyby.

## <a name="see-also"></a>Viz také
- [IDiaStackWalkHelper](../../debugger/debug-interface-access/idiastackwalkhelper.md)
- [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)
