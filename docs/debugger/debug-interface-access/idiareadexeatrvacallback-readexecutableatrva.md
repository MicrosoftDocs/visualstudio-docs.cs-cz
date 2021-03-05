---
description: Přečte zadaný počet bajtů počínaje zadanou relativní virtuální adresou (RVA) ze spustitelného souboru.
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
ms.openlocfilehash: 4c3d51ce1d2a54583df41fb4c6dd17dcfd679ad1
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2021
ms.locfileid: "102157327"
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
