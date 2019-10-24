---
title: 'IDiaSectionContrib:: get_dataCrc | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSectionContrib::get_dataCrc method
ms.assetid: 33b7488f-dc9c-47b3-b08c-737e0eb1bf7d
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 8287202efaf1f60743969007b432829940441a22
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/22/2019
ms.locfileid: "72742680"
---
# <a name="idiasectioncontribget_datacrc"></a>IDiaSectionContrib::get_dataCrc
Načte cyklickou kontrolu dat v části (CRC).

## <a name="syntax"></a>Syntaxe

```C++
HRESULT get_dataCrc ( 
   DWORD* pRetVal
);
```

#### <a name="parameters"></a>Parametry
 `pRetVal`

mimo Vrátí CRC pro data v části.

## <a name="return-value"></a>Návratová hodnota
 V případě úspěchu vrátí `S_OK`. Vrátí `S_FALSE`, pokud tato vlastnost není podporována. V opačném případě vrátí kód chyby.

## <a name="see-also"></a>Viz také:
- [IDiaSectionContrib](../../debugger/debug-interface-access/idiasectioncontrib.md)