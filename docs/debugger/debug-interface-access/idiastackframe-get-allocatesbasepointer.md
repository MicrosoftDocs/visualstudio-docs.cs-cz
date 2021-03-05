---
description: 'IDiaStackFrame:: get_allocatesBasePointer načte příznak, který označuje, zda je základní ukazatel přidělen pro kód v tomto rozsahu adres.'
title: 'IDiaStackFrame:: get_allocatesBasePointer | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaStackFrame::get_allocatesBasePointer
ms.assetid: a91e9c8e-c5e3-4887-a60b-f03b5a98f30c
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 987257157104a62de4e644631dd76037abc3e796
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2021
ms.locfileid: "102147567"
---
# <a name="idiastackframeget_allocatesbasepointer"></a>IDiaStackFrame::get_allocatesBasePointer
Načte příznak, který označuje, zda je základní ukazatel přidělen pro kód v tomto rozsahu adres.

## <a name="syntax"></a>Syntaxe

```C++
HRESULT get_allocatesBasePointer ( 
   BOOL* pRetVal
);
```

#### <a name="parameters"></a>Parametry
 `pRetVal`

mimo Vrátí, `TRUE` zda je v tomto snímku přidělen základní ukazatel pro kód. v opačném případě vrátí `FALSE` .

## <a name="return-value"></a>Návratová hodnota
 V případě úspěchu vrátí `S_OK` . Vrátí hodnotu, `S_FALSE` Pokud vlastnost není podporována. V opačném případě vrátí kód chyby.

## <a name="see-also"></a>Viz také
- [IDiaStackFrame](../../debugger/debug-interface-access/idiastackframe.md)
