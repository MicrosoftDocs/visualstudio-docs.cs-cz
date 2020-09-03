---
title: 'IDiaLineNumber:: get_length | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaLineNumber::get_length method
ms.assetid: 2c55a6f7-4ef5-45fb-9fd1-d72deaaa2829
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 3804d018569a0b2e0ee5a11a3bb5edc8363cfffc
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "85466887"
---
# <a name="idialinenumberget_length"></a>IDiaLineNumber::get_length
Načte počet bajtů v bloku.

## <a name="syntax"></a>Syntaxe

```C++
HRESULT get_length ( 
   DWORD* pRetVal
);
```

#### <a name="parameters"></a>Parametry
 `pRetVal`

mimo Vrátí počet bajtů v bloku.

## <a name="return-value"></a>Návratová hodnota
 V případě úspěchu vrátí `S_OK` . Vrátí `S_FALSE` , pokud tato vlastnost není podporována. V opačném případě vrátí kód chyby.

## <a name="remarks"></a>Poznámky
 Blok je délka zdrojového kódu na řádku, který je reprezentován objektem [IDiaLineNumber](../../debugger/debug-interface-access/idialinenumber.md) .

## <a name="see-also"></a>Viz také
- [IDiaLineNumber](../../debugger/debug-interface-access/idialinenumber.md)