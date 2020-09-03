---
title: IDiaReadExeAtRVACallback | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaReadExeAtRVACallback interface
ms.assetid: b2892513-3952-4f99-9b98-60cb9b1fdc91
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 8fc4d27f3ef8c9329feddd6bf7d8342ceae1b263
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "85466453"
---
# <a name="idiareadexeatrvacallback"></a>IDiaReadExeAtRVACallback
Umožňuje klientské aplikaci poskytovat bajty spustitelného souboru, jak je určeno relativní virtuální adresou.

## <a name="syntax"></a>Syntax

```
IDiaReadExeAtRVACallback : IUnknown
```

## <a name="methods-in-vtable-order"></a>Metody v pořadí vtable
 V následující tabulce jsou uvedeny metody `IDiaReadExeAtRVACallback` .

|Metoda|Popis|
|------------|-----------------|
|[IDiaReadExeAtRVACallback::ReadExecutableAtRVA](../../debugger/debug-interface-access/idiareadexeatrvacallback-readexecutableatrva.md)|Přečte zadaný počet bajtů počínaje zadanou relativní virtuální adresou (RVA) ze spustitelného souboru.|

## <a name="remarks"></a>Poznámky
 Klientská aplikace implementuje toto rozhraní, aby poskytovala bajty spustitelných souborů pomocí relativní virtuální adresy do souboru spustitelného souboru. Chcete-li použít absolutní posun souboru, implementujte rozhraní [IDiaReadExeAtOffsetCallback](../../debugger/debug-interface-access/idiareadexeatoffsetcallback.md) .

## <a name="notes-for-callers"></a>Poznámky pro volající
 Tato metoda je implementována klientskou aplikací a předána metodě [IDiaDataSource:: loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md) jako alternativní metodu pro čtení souboru.

## <a name="requirements"></a>Požadavky
 Záhlaví: Dia2. h

 Knihovna: diaguids. lib

 KNIHOVNA DLL: msdia80.dll

## <a name="see-also"></a>Viz také
- [Rozhraní (Přístup k rozhraní ladění SDK)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)
- [IDiaDataSource::loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md)
- [IDiaReadExeAtOffsetCallback](../../debugger/debug-interface-access/idiareadexeatoffsetcallback.md)