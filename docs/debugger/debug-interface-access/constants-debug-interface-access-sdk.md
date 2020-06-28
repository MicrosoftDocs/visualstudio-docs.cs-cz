---
title: Konstanty (Debug Interface Access SDK) | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- constants, DIA SDK
- DIA SDK, constants
ms.assetid: aca4ec77-bc08-4cdd-a6ce-8d4a28ea5ea3
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 3fa6037253141df1111ef3bc57fac9c718d826dc
ms.sourcegitcommit: 66f31cc4ce1236e638ab58d2f70d3646206386fa
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/27/2020
ms.locfileid: "85462237"
---
# <a name="constants-debug-interface-access-sdk"></a>Konstanty (Přístup k rozhraní ladění SDK)
Tyto řetězcové konstanty lze použít k identifikaci různých oddílů souboru PDB (program Debug Database) prostřednictvím DIA SDK.

## <a name="constants"></a>Konstanty
Následující jsou deklarovány jako makra jazyka C/C++.

|Podokně|Hodnota|
|-----------|-----------|
|`DiaTable_Symbols`|L "symboly"|
|`DiaTable_Sections`|L "oddíly"|
|`DiaTable_SrcFiles`|L "SourceFiles"|
|`DiaTable_LineNums`|L "Číslařádků"|
|`DiaTable_SegMap`|L "SegmentMap"|
|`DiaTable_Dbg`|L "DBG"|
|`DiaTable_InjSrc`|L "InjectedSource"|
|`DiaTable_FrameData`|L "FrameData"|

## <a name="example"></a>Příklad
Tady je příklad s jedním z těchto symbolů:

```C++
HRESULT GetSymbolTable(IDiaEnumTables *pEnumTables, IDiaTable **pTable)
{
    HRESULT hr;
    VARIANT var;
    var.vt      = VT_BSTR;
    var.bstrVal = SysAllocString( DiaTable_Symbols );
    hr = pEnumTables->Item( var, pTable );
    return(hr);
}
```

## <a name="requirements"></a>Požadavky
Záhlaví: Dia2. h

## <a name="see-also"></a>Viz také
- [Reference](../../debugger/debug-interface-access/debug-interface-access-sdk-reference.md)
- [Výčty a struktury](../../debugger/debug-interface-access/enumerations-and-structures.md)
- [Rozhraní (Přístup k rozhraní ladění SDK)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)
- [IDiaEnumTables::Item](../../debugger/debug-interface-access/idiaenumtables-item.md)
