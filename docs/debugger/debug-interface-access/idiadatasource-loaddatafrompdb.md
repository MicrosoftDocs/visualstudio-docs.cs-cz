---
title: 'IDiaDataSource:: loadDataFromPdb | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaDataSource::loadDataFromPdb method
ms.assetid: 02159073-8144-47f8-a0b0-aa0edcb92b5b
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 4463d14b27c32cc9d74f578f41467db5dc95e815
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99865242"
---
# <a name="idiadatasourceloaddatafrompdb"></a>IDiaDataSource::loadDataFromPdb
Otevře a připraví soubor databáze programu (PDB) jako zdroj dat pro ladění.

## <a name="syntax"></a>Syntaxe

```C++
HRESULT loadDataFromPdb (
   LPCOLESTR pdbPath
);
```

#### <a name="parameters"></a>Parametry
pdbPath

pro Cesta k souboru. pdb.

## <a name="return-value"></a>Návratová hodnota
V případě úspěchu vrátí. `S_OK` jinak vrátí kód chyby. V následující tabulce jsou uvedeny možné návratové hodnoty pro tuto metodu.

|Hodnota|Popis|
|-----------|-----------------|
|E_PDB_NOT_FOUND|Otevření souboru se nezdařilo nebo bylo zjištěno, že soubor má neplatný formát.|
|E_PDB_FORMAT|Došlo k pokusu o přístup k souboru s zastaralým formátem.|
|E_INVALIDARG|Neplatný parametr|
|E_UNEXPECTED|Zdroj dat už je připravený.|

## <a name="remarks"></a>Poznámky
Tato metoda načte data ladění přímo ze souboru. pdb.

Chcete-li ověřit soubor. pdb proti konkrétním kritériím, použijte metodu [IDiaDataSource:: loadAndValidateDataFromPdb](../../debugger/debug-interface-access/idiadatasource-loadandvalidatedatafrompdb.md) .

Chcete-li získat přístup k procesu načítání dat (pomocí mechanismu zpětného volání), použijte metodu [IDiaDataSource:: loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md) .

Chcete-li načíst soubor. pdb přímo z paměti, použijte metodu [IDiaDataSource:: loadDataFromIStream](../../debugger/debug-interface-access/idiadatasource-loaddatafromistream.md) .

## <a name="example"></a>Příklad

```C++
HRESULT hr = pSource->loadDataFromPdb( L"myprog.pdb" );
if (FAILED(hr))
{
    // report error
}
```

## <a name="see-also"></a>Viz také
- [IDiaDataSource](../../debugger/debug-interface-access/idiadatasource.md)
- [IDiaDataSource::loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md)
- [IDiaDataSource::loadAndValidateDataFromPdb](../../debugger/debug-interface-access/idiadatasource-loadandvalidatedatafrompdb.md)
- [IDiaDataSource::loadDataFromIStream](../../debugger/debug-interface-access/idiadatasource-loaddatafromistream.md)
