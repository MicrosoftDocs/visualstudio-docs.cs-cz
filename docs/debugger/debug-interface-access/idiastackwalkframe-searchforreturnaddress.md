---
description: 'IDiaStackWalkFrame:: Searchforreturnaddress – vyhledá zadaný rámec zásobníku pro nejbližší návratovou adresu funkce.'
title: 'IDiaStackWalkFrame:: Searchforreturnaddress – | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaStackWalkFrame::searchForReturnAddress method
ms.assetid: 1a54c50d-94af-4a43-ac4e-d80c5df156c3
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 3fa964f5b91185b75d9d10f1be225084cb9253da
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2021
ms.locfileid: "102156865"
---
# <a name="idiastackwalkframesearchforreturnaddress"></a>IDiaStackWalkFrame::searchForReturnAddress
Vyhledá zadaný rámec zásobníku pro nejbližší návratovou adresu funkce.

## <a name="syntax"></a>Syntaxe

```C++
HRESULT searchForReturnAddress ( 
   IDiaFrameData* frame,
   ULONGLONG*     returnAddress
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
- [IDiaStackWalkFrame](../../debugger/debug-interface-access/idiastackwalkframe.md)
- [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)
