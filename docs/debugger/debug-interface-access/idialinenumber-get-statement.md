---
title: 'IDiaLineNumber:: get_statement | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaLineNumber::get_statement method
ms.assetid: 22b8ee29-79ef-427f-bd05-00d255ab836b
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 3ea4a05bfccddeedb29110ea6ee44f34f85534a8
ms.sourcegitcommit: 66f31cc4ce1236e638ab58d2f70d3646206386fa
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/27/2020
ms.locfileid: "85466845"
---
# <a name="idialinenumberget_statement"></a>IDiaLineNumber::get_statement
Načte příznak označující, že tyto informace o řádku popisují začátek příkazu, nikoli výraz ve zdroji programu.

## <a name="syntax"></a>Syntaxe

```C++
HRESULT get_statement ( 
   BOOL* pRetVal
);
```

#### <a name="parameters"></a>Parametry
 `pRetVal`

mimo Vrátí `TRUE` , pokud informace o tomto řádku popisují začátek příkazu ve zdroji programu.

## <a name="return-value"></a>Návratová hodnota
 V případě úspěchu vrátí `S_OK` . Vrátí `S_FALSE` , pokud tato vlastnost není podporována. V opačném případě vrátí kód chyby.

## <a name="remarks"></a>Poznámky
 Příkazy mohou být rozloženy na více řádků. Tato metoda označuje, zda přidružené číslo řádku označuje začátek takového víceřádkového příkazu.

## <a name="see-also"></a>Viz také
- [IDiaLineNumber](../../debugger/debug-interface-access/idialinenumber.md)