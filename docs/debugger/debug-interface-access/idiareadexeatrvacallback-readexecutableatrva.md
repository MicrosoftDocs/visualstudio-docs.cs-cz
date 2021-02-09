---
title: 'IDiaReadExeAtRVACallback:: ReadExecutableAtRVA | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaReadExeAtRVACallback::ReadExecutableAtRVA method
ms.assetid: 3c1e965f-8f05-41a8-86d8-01830b2377c9
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 798a3af92a58cde7504db6232ce62c6e2aa292cf
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99855499"
---
# <a name="idiareadexeatrvacallbackreadexecutableatrva"></a>IDiaReadExeAtRVACallback::ReadExecutableAtRVA
Přečte zadaný počet bajtů počínaje zadanou relativní virtuální adresou (RVA) ze spustitelného souboru.

## <a name="syntax"></a>Syntaxe

```C++
HRESULT ReadExecutableAtRVA ( 
   DWORD  relativeVirtualAddress,
   DWORD  cbData,
   DWORD* pcbData,
   BYTE   data[]
);
```

#### <a name="parameters"></a>Parametry
 `relativeVirtualAddress`

pro Adresa RVA ve spustitelném souboru pro zahájení čtení.

 `cbData`

pro Počet bajtů, které se mají přečíst

 `pcbData`

mimo Vrátí počet přečtených bajtů.

 `data[]`

[in, out] Pole, které je vyplněno bajty přečtenými ze souboru.

## <a name="remarks"></a>Poznámky
 Tato metoda je volána kódem podpory DIA k načtení datových bajtů ze spustitelného souboru pomocí relativní virtuální adresy. Tato metoda je volána v podpoře metody [IDiaDataSource:: loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md) .

## <a name="see-also"></a>Viz také
- [IDiaReadExeAtRVACallback](../../debugger/debug-interface-access/idiareadexeatrvacallback.md)
- [IDiaDataSource::loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md)