---
title: 'IDiaLoadCallback:: NotifyDebugDir | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaLoadCallback::NotifyDebugDir method
ms.assetid: bd04e2f6-0dbf-4742-a556-96f2cd99aa19
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 6618440cab9b9042ec371383f6c809ca1d0d11f7
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/22/2019
ms.locfileid: "72743090"
---
# <a name="idialoadcallbacknotifydebugdir"></a>IDiaLoadCallback::NotifyDebugDir
Volá se, když se v souboru. exe našel adresář pro ladění.

## <a name="syntax"></a>Syntaxe

```C++
HRESULT NotifyDebugDir ( 
   BOOL  fExecutable,
   DWORD cbData,
   BYTE  data[]
);
```

#### <a name="parameters"></a>Parametry
 `fExecutable`

[in] `TRUE`, zda je adresář ladění čten ze spustitelného souboru (nikoli souboru. dbg).

 `cbData`

pro Počet bajtů dat v adresáři ladění.

 `data[]`

pro Pole, které je vyplněno adresářem ladění.

## <a name="return-value"></a>Návratová hodnota
 V případě úspěchu vrátí `S_OK`; v opačném případě vrátí kód chyby. Návratový kód se obvykle ignoruje.

## <a name="remarks"></a>Poznámky
 Metoda [IDiaDataSource:: loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md) vyvolá toto zpětné volání, když při zpracování spustitelného souboru najde ladicí adresář.

 Tato metoda odstraní nutnost, aby klient mohl zpětně zpracovat spustitelný soubor nebo soubor ladění pro podporu jiných informací o ladění, než které byly nalezeny v souboru. pdb. U těchto dat může klient rozpoznat typ informací o ladění, který je k dispozici, a zda se nachází ve spustitelném souboru nebo souboru. dbg.

 Většina klientů toto zpětné volání nebudete potřebovat, protože metoda `IDiaDataSource::loadDataForExe` transparentně otevře soubory. pdb i. dbg, pokud je to nutné pro poskytování symbolů.

## <a name="see-also"></a>Viz také:
- [IDiaLoadCallback2](../../debugger/debug-interface-access/idialoadcallback2.md)
- [IDiaDataSource::loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md)