---
description: Pokud má funkce definovaný bod, na kterém je ladění ukončeno, je startovací bod ladění identifikován symbolem se značkou SymTagFuncDebugEnd.
title: FuncDebugEnd | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- FuncDebugEnd symbol
- debugging [DIA SDK], end point
ms.assetid: 68f84fff-7cd3-4636-b929-7063a45009f8
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 5b28fe8f1a436dd308487187897fa62fd247a293
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2021
ms.locfileid: "102149156"
---
# <a name="funcdebugend"></a>FuncDebugEnd
Pokud má funkce definovaný bod, na kterém je ladění ukončeno, je výchozí bod ladění identifikován symbolem se `SymTagFuncDebugEnd` značkou.

## <a name="properties"></a>Vlastnosti
 V následující tabulce jsou uvedeny vlastnosti, které jsou platné pro tento typ symbolu.

|Vlastnost|Datový typ|Popis|
|--------------|---------------|-----------------|
|[IDiaSymbol::get_addressOffset](../../debugger/debug-interface-access/idiasymbol-get-addressoffset.md)|`DWORD`|Odsadit část umístění; Podrobnosti najdete v tématu [výčet LocationType –](../../debugger/debug-interface-access/locationtype.md).|
|[IDiaSymbol::get_addressSection](../../debugger/debug-interface-access/idiasymbol-get-addresssection.md)|`DWORD`|Část umístění; Podrobnosti najdete v tématu [výčet LocationType –](../../debugger/debug-interface-access/locationtype.md).|
|[IDiaSymbol::get_customCallingConvention](../../debugger/debug-interface-access/idiasymbol-get-customcallingconvention.md)|`BOOL`|`TRUE` Pokud funkce používá vlastní konvenci volání (pouze v DIA SDK V 8.0 nebo novějším).|
|[IDiaSymbol::get_farReturn](../../debugger/debug-interface-access/idiasymbol-get-farreturn.md)|`BOOL`|`TRUE` Funkce IF provede zcela vrácení (pouze v DIA SDK V 8.0 nebo novějším).|
|[IDiaSymbol::get_interruptReturn](../../debugger/debug-interface-access/idiasymbol-get-interruptreturn.md)|`BOOL`|`TRUE` Funkce IF obsahuje návrat z přerušení (pouze v DIA SDK V 8.0 nebo novějším).|
|[IDiaSymbol::get_isStatic](../../debugger/debug-interface-access/idiasymbol-get-isstatic.md)|`BOOL`|`TRUE` Pokud je funkce statická (jenom v DIA SDK V 8.0 nebo novějším).|
|[IDiaSymbol::get_lexicalParent](../../debugger/debug-interface-access/idiasymbol-get-lexicalparent.md)|`IDiaSymbol*`|Symbol pro ohraničující funkci|
|[IDiaSymbol::get_lexicalParentId](../../debugger/debug-interface-access/idiasymbol-get-lexicalparentid.md)|`DWORD`|ID lexikálního nadřazeného symbolu|
|[IDiaSymbol::get_locationType](../../debugger/debug-interface-access/idiasymbol-get-locationtype.md)|`DWORD`|Koncové body mají statické umístění; Podrobnosti najdete v tématu [umístění symbolů](../../debugger/debug-interface-access/symbol-locations.md).|
|[IDiaSymbol::get_noInline](../../debugger/debug-interface-access/idiasymbol-get-noinline.md)|`BOOL`|`TRUE` Pokud byla funkce zadána s atributem [inline](/cpp/cpp/noinline) (pouze V DIA SDK v 8.0 nebo novějším).|
|[IDiaSymbol::get_noReturn](../../debugger/debug-interface-access/idiasymbol-get-noreturn.md)|`BOOL`|`TRUE` Pokud byla funkce zadána s atributem [vracet](/cpp/cpp/noreturn) (pouze V DIA SDK v 8.0 nebo novějším).|
|[IDiaSymbol::get_notReached](../../debugger/debug-interface-access/idiasymbol-get-notreached.md)|`BOOL`|`TRUE` Pokud funkce nikdy není volána (pouze v DIA SDK V 8.0 nebo novějším).|
|[IDiaSymbol::get_offset](../../debugger/debug-interface-access/idiasymbol-get-offset.md)|`LONG`|Posun symbolu v paměti; Podrobnosti najdete v článku [výčet LocationType –](../../debugger/debug-interface-access/locationtype.md) `LocIsRegRel` .|
|[IDiaSymbol::get_optimizedCodeDebugInfo](../../debugger/debug-interface-access/idiasymbol-get-optimizedcodedebuginfo.md)|`BOOL`|`TRUE` Pokud má funkce ladicí informace pro optimalizovaný kód (pouze v DIA SDK V 8.0 nebo novějším).|
|[IDiaSymbol::get_symIndexId](../../debugger/debug-interface-access/idiasymbol-get-symindexid.md)|`DWORD`|ID indexu symbolu|
|[IDiaSymbol::get_relativeVirtualAddress](../../debugger/debug-interface-access/idiasymbol-get-relativevirtualaddress.md)|`DWORD`|Relativní pozice konce této funkce v rámci jejího modulu.|
|[IDiaSymbol::get_symTag](../../debugger/debug-interface-access/idiasymbol-get-symtag.md)|`DWORD`|Vrátí `SymTagFuncDebugEnd` (jednu z hodnot [výčtu SymTagEnum –](../../debugger/debug-interface-access/symtagenum.md) ).|
|[IDiaSymbol::get_virtualAddress](../../debugger/debug-interface-access/idiasymbol-get-virtualaddress.md)|`ULONGLONG`|Pozice této funkce ve spustitelném obrázku.|

## <a name="see-also"></a>Viz také
- [Lexikální hierarchie typů symbolů](../../debugger/debug-interface-access/lexical-hierarchy-of-symbol-types.md)
- [LocationType – výčet](../../debugger/debug-interface-access/locationtype.md)
- [Umístění symbolů](../../debugger/debug-interface-access/symbol-locations.md)
