---
description: Načte tabulku prostřednictvím indexu nebo názvu.
title: 'IDiaEnumTables:: Item | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumTables::Item method
ms.assetid: d65ab262-10c6-48ce-95a3-b5e4cb2c85af
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: dc222672b0ba52f19f153a8e0c9e97137a069607
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2021
ms.locfileid: "102148575"
---
# <a name="idiaenumtablesitem"></a>IDiaEnumTables::Item
Načte tabulku prostřednictvím indexu nebo názvu.

## <a name="syntax"></a>Syntaxe

```C++
HRESULT Item ( 
   VARIANT     index,
   IDiaTable** table
);
```

#### <a name="parameters"></a>Parametry
 `index`

pro Index nebo název [IDiaTable](../../debugger/debug-interface-access/idiatable.md) , který se má načíst Je-li použit celočíselný typ variant, musí být v rozsahu 0 až `count` -1, kde `count` je vrácen metodou [IDiaEnumTables:: get_Count](../../debugger/debug-interface-access/idiaenumtables-get-count.md) .

 `table`

mimo Vrátí objekt [IDiaTable](../../debugger/debug-interface-access/idiatable.md) reprezentující požadovanou tabulku.

## <a name="return-value"></a>Návratová hodnota
 V případě úspěchu vrátí. `S_OK` jinak vrátí kód chyby.

## <a name="remarks"></a>Poznámky
 Pokud je zadána řetězcová varianta, pak řetězec pojmenuje konkrétní tabulku. Název by měl být jeden z názvů tabulek, jak je definován v [konstantách (Debug Interface Access SDK)](../../debugger/debug-interface-access/constants-debug-interface-access-sdk.md).

## <a name="example"></a>Příklad

```C++
VARIANT var;
var.vt = VT_BSTR;
var.bstrVal = SysAllocString(DiaTable_Symbols );
IDiaTable* pTable;
pEnumTables->Item( var, &pTable );
```

## <a name="see-also"></a>Viz také
- [IDiaEnumTables](../../debugger/debug-interface-access/idiaenumtables.md)
- [IDiaTable](../../debugger/debug-interface-access/idiatable.md)
- [IDiaEnumTables::get_Count](../../debugger/debug-interface-access/idiaenumtables-get-count.md)
- [Konstanty (Přístup k rozhraní ladění SDK)](../../debugger/debug-interface-access/constants-debug-interface-access-sdk.md)
