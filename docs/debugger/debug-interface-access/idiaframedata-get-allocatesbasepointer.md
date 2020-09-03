---
title: 'IDiaFrameData:: get_allocatesBasePointer | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaFrameData::get_allocatesBasePointer method
ms.assetid: 8a33db5d-008c-4fe5-b64f-210c9b77f686
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a8c51b335e0d13752ee2f3c6c68c17b5f2b76a9d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "85467426"
---
# <a name="idiaframedataget_allocatesbasepointer"></a>IDiaFrameData::get_allocatesBasePointer
Načte příznak, který označuje, zda je základní ukazatel přidělen pro kód v tomto rozsahu adres. Tato metoda je zastaralá.

## <a name="syntax"></a>Syntaxe

```C++
HRESULT get_allocatesBasePointer ( 
   BOOL* pRetVal
);
```

#### <a name="parameters"></a>Parametry
 `pRetVal`

mimo Vrátí, `TRUE` zda je přidělen základní ukazatel. v opačném případě vrátí hodnotu `FALSE` .

## <a name="return-value"></a>Návratová hodnota
 V případě úspěchu vrátí `S_OK` . Vrátí `S_FALSE` , pokud tato vlastnost není podporována. V opačném případě vrátí kód chyby.

## <a name="remarks"></a>Poznámky
 Tato vlastnost by měla být používána pouze kódem, který byl dříve použit FPO_DATA, nebo pokud řetězec programu vrácený metodou [IDiaFrameData:: get_program](../../debugger/debug-interface-access/idiaframedata-get-program.md) je `NULL` . V opačném případě řetězec programu obsahuje všechny informace potřebné k výpočtu předchozích hodnot registru.

## <a name="see-also"></a>Viz také
- [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)
- [IDiaFrameData::get_program](../../debugger/debug-interface-access/idiaframedata-get-program.md)