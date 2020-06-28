---
title: 'IDiaSectionContrib:: get_comdat | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSectionContrib::get_comdat method
ms.assetid: 8bd9be8d-59ee-4698-b055-daba354b8dcc
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 8e5c5f707be5d687417d06e71d58f11012516e00
ms.sourcegitcommit: 66f31cc4ce1236e638ab58d2f70d3646206386fa
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/27/2020
ms.locfileid: "85466347"
---
# <a name="idiasectioncontribget_comdat"></a>IDiaSectionContrib::get_comdat
Načte příznak, který označuje, jestli je oddíl záznamem COMDAT.

## <a name="syntax"></a>Syntaxe

```C++
HRESULT get_comdat ( 
   BOOL* pRetVal
);
```

#### <a name="parameters"></a>Parametry
 `pRetVal`

mimo Vrátí, `TRUE` zda je oddíl záznam COMDAT; v opačném případě vrátí `FALSE` .

## <a name="return-value"></a>Návratová hodnota
 V případě úspěchu vrátí `S_OK` . Vrátí `S_FALSE` , pokud tato vlastnost není podporována. V opačném případě vrátí kód chyby.

## <a name="remarks"></a>Poznámky
 Záznam COMDAT je záznam COFF (Common Object File Format), který zpřístupňuje zabalená funkce do linkeru.

## <a name="see-also"></a>Viz také
- [IDiaSectionContrib](../../debugger/debug-interface-access/idiasectioncontrib.md)