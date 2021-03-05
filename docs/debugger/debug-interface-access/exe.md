---
description: Exe je jediný symbol bez lexikální nebo nadřazené třídy, protože představuje globální rozsah souboru. exe nebo. dll.
title: Exe | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- .dll files
- Exe symbol
- .exe files
- executable files, Exe symbol
ms.assetid: a781d2cf-55fe-4373-9cf1-b732864244e0
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 5394acaa19efed0c882d97f6ee5b633ffe1c68c0
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2021
ms.locfileid: "102149149"
---
# <a name="exe"></a>Exe
Exe je jediný symbol bez lexikální nebo nadřazené třídy, protože představuje globální rozsah souboru. exe nebo. dll. Je k dispozici pouze jeden symbol se `SymTagExe` značkou na soubor. Metoda [IDiaSession:: get_globalScope](../../debugger/debug-interface-access/idiasession-get-globalscope.md) vrací symbol.

## <a name="properties"></a>Vlastnosti
 V následující tabulce jsou uvedeny vlastnosti, které jsou platné pro tento typ symbolu.

|Vlastnost|Datový typ|Popis|
|--------------|---------------|-----------------|
|[IDiaSymbol::get_age](../../debugger/debug-interface-access/idiasymbol-get-age.md)|`DWORD`|Stáří tohoto spustitelného souboru.|
|[IDiaSymbol::get_guid](../../debugger/debug-interface-access/idiasymbol-get-guid.md)|`GUID`|`GUID` tohoto spustitelného souboru.|
|[IDiaSymbol::get_isCTypes](../../debugger/debug-interface-access/idiasymbol-get-isctypes.md)|`BOOL`|`TRUE` Pokud soubor symbolů přidružený k tomuto spustitelnému souboru obsahuje typy C (pouze v DIA SDK v 8.0 nebo novějším).|
|[IDiaSymbol::get_isStripped](../../debugger/debug-interface-access/idiasymbol-get-isstripped.md)|`BOOL`|`TRUE` v případě, že soukromé symboly byly ze souboru symbolů přidruženého k tomuto spustitelnému souboru odstraněny (pouze v DIA SDK v 8.0 nebo novějším).|
|[IDiaSymbol::get_machineType](../../debugger/debug-interface-access/idiasymbol-get-machinetype.md)|`DWORD`|Hodnota označující cílový procesor (jedna z hodnot [CV_CPU_TYPE_e výčtu](../../debugger/debug-interface-access/cv-cpu-type-e.md) ).|
|[IDiaSymbol::get_name](../../debugger/debug-interface-access/idiasymbol-get-name.md)|`BSTR`|Název souboru. exe.|
|[IDiaSymbol::get_signature](../../debugger/debug-interface-access/idiasymbol-get-signature.md)|`DWORD`|Podpis spustitelného souboru.|
|[IDiaSymbol::get_symbolsFileName](../../debugger/debug-interface-access/idiasymbol-get-symbolsfilename.md)|`BSTR`|Úplná cesta k souboru. pdb nebo. dbg souboru. exe.|
|[IDiaSymbol::get_symIndexId](../../debugger/debug-interface-access/idiasymbol-get-symindexid.md)|`DWORD`|ID indexu symbolu|
|[IDiaSymbol::get_symTag](../../debugger/debug-interface-access/idiasymbol-get-symtag.md)|`DWORD`|Vrátí `SymTagExe` (jednu z hodnot [výčtu SymTagEnum –](../../debugger/debug-interface-access/symtagenum.md) ).|

## <a name="see-also"></a>Viz také
- [IDiaSession::get_globalScope](../../debugger/debug-interface-access/idiasession-get-globalscope.md)
- [Lexikální hierarchie typů symbolů](../../debugger/debug-interface-access/lexical-hierarchy-of-symbol-types.md)
