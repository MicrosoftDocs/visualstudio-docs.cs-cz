---
title: 'IDiaDataSource:: get_lastError | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaDataSource::get_lastError method
ms.assetid: cf08850b-8b75-4e8c-90bd-bd0214756f99
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 950e6453a75878cd871532c2e5557e2e6314c932
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99865291"
---
# <a name="idiadatasourceget_lasterror"></a>IDiaDataSource::get_lastError
Načte název souboru pro poslední chybu načtení.

## <a name="syntax"></a>Syntaxe

```C++
HRESULT get_lastError (
   BSTR* pRetVal
);
```

#### <a name="parameters"></a>Parametry
 pRetVal

mimo Vrátí řetězec, který obsahuje název souboru. pdb přidružený k Poslední chybě načtení.

## <a name="return-value"></a>Návratová hodnota
 Vrátí poslední kód chyby způsobený operací Load. Vrátí, `E_INVALIDARG` zda `pRetVal` je parametr `NULL` .

## <a name="example"></a>Příklad

```C++
BSTR    fileName;
HRESULT errorCode = pSource->get_lastError( &fileName );
```

## <a name="see-also"></a>Viz také
- [IDiaDataSource](../../debugger/debug-interface-access/idiadatasource.md)