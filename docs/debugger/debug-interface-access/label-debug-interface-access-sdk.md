---
title: Popisek (Debug Interface Access SDK) | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- locations, in program code
- Label symbol
ms.assetid: 8cef7620-5bc8-4500-8bd0-e9e638bccb24
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: de9f99f26de3bbd075c00af33b844ed65f4154ce
ms.sourcegitcommit: 66f31cc4ce1236e638ab58d2f70d3646206386fa
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/27/2020
ms.locfileid: "85461243"
---
# <a name="label-debug-interface-access-sdk"></a>Popisek (Přístup k rozhraní ladění SDK)
Umístění v kódu programu je identifikováno `SymTagLabel` symbolem.

## <a name="properties"></a>Vlastnosti
 V následující tabulce jsou uvedeny vlastnosti, které jsou platné pro tento typ symbolu.

|Vlastnost|Datový typ|Popis|
|--------------|---------------|-----------------|
|[IDiaSymbol::get_addressOffset](../../debugger/debug-interface-access/idiasymbol-get-addressoffset.md)|`DWORD`|Odsadit část umístění; Podrobnosti najdete v tématu [výčet LocationType –](../../debugger/debug-interface-access/locationtype.md).|
|[IDiaSymbol::get_addressSection](../../debugger/debug-interface-access/idiasymbol-get-addresssection.md)|`DWORD`|Část umístění; Podrobnosti najdete v tématu [výčet LocationType –](../../debugger/debug-interface-access/locationtype.md).|
|[IDiaSymbol::get_customCallingConvention](../../debugger/debug-interface-access/idiasymbol-get-customcallingconvention.md)|`BOOL`|`TRUE`Pokud popisek používá vlastní konvenci volání.|
|[IDiaSymbol::get_farReturn](../../debugger/debug-interface-access/idiasymbol-get-farreturn.md)|`BOOL`|`TRUE`Pokud jmenovka provede úplně zpátky.|
|[IDiaSymbol::get_interruptReturn](../../debugger/debug-interface-access/idiasymbol-get-interruptreturn.md)|`BOOL`|`TRUE`Pokud popisek obsahuje návrat z přerušení.|
|[IDiaSymbol::get_lexicalParent](../../debugger/debug-interface-access/idiasymbol-get-lexicalparent.md)|`IDiaSymbol*`|Symbol pro ohraničující kompilantu, blok nebo funkci|
|[IDiaSymbol::get_lexicalParentId](../../debugger/debug-interface-access/idiasymbol-get-lexicalparentid.md)|`DWORD`|ID lexikálního nadřazeného symbolu|
|[IDiaSymbol::get_locationType](../../debugger/debug-interface-access/idiasymbol-get-locationtype.md)|`DWORD`|Popisky mají statická umístění; Podrobnosti najdete v tématu výčet [umístění symbolů](../../debugger/debug-interface-access/symbol-locations.md) .|
|[IDiaSymbol::get_name](../../debugger/debug-interface-access/idiasymbol-get-name.md)|`BSTR`|Název popisku.|
|[IDiaSymbol::get_noInline](../../debugger/debug-interface-access/idiasymbol-get-noinline.md)|`BOOL`|`TRUE`Pokud byl popisek zadán s atributem [inline](/cpp/cpp/noinline) .|
|[IDiaSymbol::get_noReturn](../../debugger/debug-interface-access/idiasymbol-get-noreturn.md)|`BOOL`|`TRUE`Pokud byl popisek zadán s atributem [nevráceno](/cpp/cpp/noreturn) .|
|[IDiaSymbol::get_notReached](../../debugger/debug-interface-access/idiasymbol-get-notreached.md)|`BOOL`|`TRUE`Pokud popisek není nikdy volán.|
|[IDiaSymbol::get_offset](../../debugger/debug-interface-access/idiasymbol-get-offset.md)|`LONG`|Posun symbolu v paměti; Podrobnosti najdete v článku [výčet LocationType –](../../debugger/debug-interface-access/locationtype.md) `LocIsRegRel` .|
|[IDiaSymbol::get_optimizedCodeDebugInfo](../../debugger/debug-interface-access/idiasymbol-get-optimizedcodedebuginfo.md)|`BOOL`|`TRUE`Pokud kód obsahuje ladicí informace pro optimalizovaný kód.|
|[IDiaSymbol::get_relativeVirtualAddress](../../debugger/debug-interface-access/idiasymbol-get-relativevirtualaddress.md)|`DWORD`|Relativní pozice tohoto popisku v rámci jeho modulu.|
|[IDiaSymbol::get_symIndexId](../../debugger/debug-interface-access/idiasymbol-get-symindexid.md)|`DWORD`|ID indexu symbolu|
|[IDiaSymbol::get_symTag](../../debugger/debug-interface-access/idiasymbol-get-symtag.md)|`DWORD`|Vrátí `SymTagFuncDebugLabel` (jednu z hodnot [výčtu SymTagEnum –](../../debugger/debug-interface-access/symtagenum.md) ).|
|[IDiaSymbol::get_virtualAddress](../../debugger/debug-interface-access/idiasymbol-get-virtualaddress.md)|`ULONGLONG`|Pozice tohoto popisku ve spustitelném obrázku.|

## <a name="see-also"></a>Viz také
- [Lexikální hierarchie typů symbolů](../../debugger/debug-interface-access/lexical-hierarchy-of-symbol-types.md)
- [LocationType – výčet](../../debugger/debug-interface-access/locationtype.md)
- [Umístění symbolů](../../debugger/debug-interface-access/symbol-locations.md)