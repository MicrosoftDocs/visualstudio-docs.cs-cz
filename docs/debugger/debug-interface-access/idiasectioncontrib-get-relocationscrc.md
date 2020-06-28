---
title: 'IDiaSectionContrib:: get_relocationsCrc | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSectionContrib::get_relocationsCrc method
ms.assetid: 8c29c91a-062d-4566-a9b7-49251036a15a
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 596656930e511d68f20916bd34044410aa706c75
ms.sourcegitcommit: 66f31cc4ce1236e638ab58d2f70d3646206386fa
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/27/2020
ms.locfileid: "85466117"
---
# <a name="idiasectioncontribget_relocationscrc"></a>IDiaSectionContrib::get_relocationsCrc
Načte kontrolu cyklického redundance (CRC) informace o přemístění pro oddíl.

## <a name="syntax"></a>Syntaxe

```C++
HRESULT get_relocationsCrc ( 
   DWORD* pRetVal
);
```

#### <a name="parameters"></a>Parametry
 `pRetVal`

mimo Vrátí CRC informace o přemístění pro oddíl.

## <a name="return-value"></a>Návratová hodnota
 V případě úspěchu vrátí `S_OK` . Vrátí `S_FALSE` , pokud tato vlastnost není podporována. V opačném případě vrátí kód chyby.

## <a name="see-also"></a>Viz také
- [IDiaSectionContrib](../../debugger/debug-interface-access/idiasectioncontrib.md)