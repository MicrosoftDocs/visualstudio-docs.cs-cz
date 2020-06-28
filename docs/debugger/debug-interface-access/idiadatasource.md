---
title: IDiaDataSource | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaDataSource interface
ms.assetid: 6260ac76-4f9d-4144-ba22-32f8620b32c2
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c9f8730fb864a70e7f649d5e8b4920d916c07c11
ms.sourcegitcommit: 66f31cc4ce1236e638ab58d2f70d3646206386fa
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/27/2020
ms.locfileid: "85468488"
---
# <a name="idiadatasource"></a>IDiaDataSource
Inicializuje přístup ke zdroji ladicích symbolů.

## <a name="syntax"></a>Syntax

```
IDiaDataSource : IUnknown
```

## <a name="methods-in-vtable-order"></a>Metody v pořadí vtable
V následující tabulce jsou uvedeny metody `IDiaDataSource` .

|Metoda|Popis|
|------------|-----------------|
|[IDiaDataSource::get_lastError](../../debugger/debug-interface-access/idiadatasource-get-lasterror.md)|Načte název souboru pro poslední chybu načtení.|
|[IDiaDataSource::loadDataFromPdb](../../debugger/debug-interface-access/idiadatasource-loaddatafrompdb.md)|Otevře a připraví soubor databáze programu (PDB) jako zdroj dat pro ladění.|
|[IDiaDataSource::loadAndValidateDataFromPdb](../../debugger/debug-interface-access/idiadatasource-loadandvalidatedatafrompdb.md)|Otevře a ověří, že soubor databáze programu (PDB) odpovídá poskytnutým informacím o podpisu. připraví soubor. pdb jako zdroj dat pro ladění.|
|[IDiaDataSource::loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md)|Otevře a připraví ladicí data přidružená k souboru. exe/. dll.|
|[IDiaDataSource::loadDataFromIStream](../../debugger/debug-interface-access/idiadatasource-loaddatafromistream.md)|Připraví ladicí data uložená v souboru programové databáze (PDB), který je k dispozici prostřednictvím datového proudu v paměti.|
|[IDiaDataSource::openSession](../../debugger/debug-interface-access/idiadatasource-opensession.md)|Otevře relaci pro zadávání dotazů na symboly.|

## <a name="remarks"></a>Poznámky
Volání jedné z metod zatížení `IDiaDataSource` rozhraní otevře zdroj symbolu. Úspěšné volání metody [IDiaDataSource:: openSession](../../debugger/debug-interface-access/idiadatasource-opensession.md) vrátí rozhraní [IDiaSession](../../debugger/debug-interface-access/idiasession.md) , které podporuje dotazování na zdroj dat. Pokud metoda Load vrátí chybu související se souborem, návratová hodnota metody [IDiaDataSource:: get_lastError](../../debugger/debug-interface-access/idiadatasource-get-lasterror.md) obsahuje název souboru přidruženého k chybě.

## <a name="notes-for-callers"></a>Poznámky pro volající
Toto rozhraní se získá voláním `CoCreateInstance` funkce s identifikátorem třídy `CLSID_DiaSource` a ID rozhraní `IID_IDiaDataSource` . Příklad ukazuje, jak se toto rozhraní získává.

## <a name="example"></a>Příklad

```C++

      IDiaDataSource* pSource;
HRESULT hr = CoCreateInstance(CLSID_DiaSource,
                              NULL,
                              CLSCTX_INPROC_SERVER,
                              IID_IDiaDataSource,
                              (void**) &pSource);
if (FAILED(hr))
{
    // Report error and exit
}
```

## <a name="requirements"></a>Požadavky
Záhlaví: Dia2. h

Knihovna: diaguids. lib

KNIHOVNA DLL: msdia80.dll

## <a name="see-also"></a>Viz také
- [Rozhraní (Přístup k rozhraní ladění SDK)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)
