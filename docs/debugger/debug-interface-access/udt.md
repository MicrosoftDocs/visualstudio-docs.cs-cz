---
title: UDT | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- SymTagUDT symbol
- user-defined type (UDT) symbol
- unions, as symbols
- UDT symbol
- structs [C++]
ms.assetid: f12459dd-c64d-4cc9-9ee3-a56e19e9e573
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: fb354ebd9e2aed59d6bc3bfe14bfd18ae7cbfad7
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2018
ms.locfileid: "31471805"
---
# <a name="udt"></a>UDT
Každý třída, struktura a sjednocení je identifikována `SymTagUDT` symbol. Každý člen, funkce, data, nebo vnořené typy a každý základní třídy, se zobrazí jako podřízenou třída uživatelem definovaný typ (UDT).  
  
## <a name="properties"></a>Vlastnosti  
 V následující tabulce jsou uvedeny další platný vlastnosti pro tento typ symbolu.  
  
|Vlastnost|Datový typ|Popis|  
|--------------|---------------|-----------------|  
|[IDiaSymbol::get_classParent](../../debugger/debug-interface-access/idiasymbol-get-classparent.md)|`IDiaSymbol*`|Symbol pro nadřazené třídy, pokud existuje.|  
|[IDiaSymbol::get_classParentId](../../debugger/debug-interface-access/idiasymbol-get-classparentid.md)|`DWORD`|ID symbolu nadřazené třídy.|  
|[IDiaSymbol::get_constructor](../../debugger/debug-interface-access/idiasymbol-get-constructor.md)|`BOOL`|`TRUE` Pokud UDT má konstruktor.|  
|[IDiaSymbol::get_constType](../../debugger/debug-interface-access/idiasymbol-get-consttype.md)|`BOOL`|`TRUE` Pokud UDT je označena jako konstanta.|  
|[IDiaSymbol::get_hasAssignmentOperator](../../debugger/debug-interface-access/idiasymbol-get-hasassignmentoperator.md)|`BOOL`|`TRUE` Pokud UDT má všechny operátory přiřazení definované.|  
|[IDiaSymbol::get_hasCastOperator](../../debugger/debug-interface-access/idiasymbol-get-hascastoperator.md)|`BOOL`|`TRUE` Pokud UDT má všechny operátory přetypování definované.|  
|[IDiaSymbol::get_hasNestedTypes](../../debugger/debug-interface-access/idiasymbol-get-hasnestedtypes.md)|`BOOL`|`TRUE` Pokud UDT má definice vnořené typy.|  
|[IDiaSymbol::get_length](../../debugger/debug-interface-access/idiasymbol-get-length.md)|`LONGLONG`|Velikost v bajtech UDT.|  
|[IDiaSymbol::get_lexicalParent](../../debugger/debug-interface-access/idiasymbol-get-lexicalparent.md)|`IDiaSymbol*`|Symbol uzavření [kompilace](../../debugger/debug-interface-access/compiland.md).|  
|[IDiaSymbol::get_lexicalParentId](../../debugger/debug-interface-access/idiasymbol-get-lexicalparentid.md)|`DWORD`|ID nadřazené lexikální symbolu.|  
|[IDiaSymbol::get_name](../../debugger/debug-interface-access/idiasymbol-get-name.md)|`BSTR`|Název UDT.|  
|[IDiaSymbol::get_nested](../../debugger/debug-interface-access/idiasymbol-get-nested.md)|`BOOL`|`TRUE` Pokud UDT je vnořený.|  
|[IDiaSymbol::get_overloadedOperator](../../debugger/debug-interface-access/idiasymbol-get-overloadedoperator.md)|`BOOL`|`TRUE` Pokud přetížené operátory jsou definovány pro UDT.|  
|[IDiaSymbol::get_packed](../../debugger/debug-interface-access/idiasymbol-get-packed.md)|`BOOL`|`TRUE` Pokud UDT je zabalena.|  
|[IDiaSymbol::get_scoped](../../debugger/debug-interface-access/idiasymbol-get-scoped.md)|`BOOL`|`TRUE` Pokud se zobrazí UDT v neglobální lexikální oboru.|  
|[IDiaSymbol::get_symIndexId](../../debugger/debug-interface-access/idiasymbol-get-symindexid.md)|`DWORD`|ID indexu symbolu.|  
|[IDiaSymbol::get_symTag](../../debugger/debug-interface-access/idiasymbol-get-symtag.md)|`DWORD`|Vrátí `SymTagUDT` (jeden z [SymTagEnum – výčet](../../debugger/debug-interface-access/symtagenum.md) hodnoty).|  
|[IDiaSymbol::get_udtKind](../../debugger/debug-interface-access/idiasymbol-get-udtkind.md)|`DWORD`|Určuje, zda je tato struktura, třídu nebo sjednocení; Podrobnosti najdete v tématu [UdtKind – výčet](../../debugger/debug-interface-access/udtkind.md).|  
|[IDiaSymbol::get_unalignedType](../../debugger/debug-interface-access/idiasymbol-get-unalignedtype.md)|`BOOL`|`TRUE` Pokud UDT nezarovnané.|  
|[IDiaSymbol::get_virtualTableShape](../../debugger/debug-interface-access/idiasymbol-get-virtualtableshape.md)|`IDiaSymbol*`|Typ na virtuální tabulku.|  
|[IDiaSymbol::get_virtualTableShapeId](../../debugger/debug-interface-access/idiasymbol-get-virtualtableshapeid.md)|`DWORD`|ID virtuální tabulku tvar symbolu.|  
|[IDiaSymbol::get_volatileType](../../debugger/debug-interface-access/idiasymbol-get-volatiletype.md)|`BOOL`|`TRUE` Pokud UDT je označena jako volatile.|  
  
## <a name="see-also"></a>Viz také  
 [Hierarchie tříd typů symbolů](../../debugger/debug-interface-access/class-hierarchy-of-symbol-types.md)