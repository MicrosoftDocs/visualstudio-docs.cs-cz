---
title: Enum (Debug Interface Access SDK) | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- enumerated types as symbols
- Enum symbol
ms.assetid: c777e2e6-88be-435b-b632-8d43f42b0b49
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 9803c2b5fbf24d775681372b0b7e58f86651b0fa
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/22/2019
ms.locfileid: "72745237"
---
# <a name="enum-debug-interface-access-sdk"></a>Výčet (Přístup k rozhraní ladění SDK)
Výčty jsou identifikovány `SymTagEnum` symboly. Každá hodnota výčtu se zobrazí jako podřízená třída s tagem `SymTagConstant`.

## <a name="properties"></a>Vlastnosti
 V následující tabulce jsou uvedeny další platné vlastnosti pro tento typ symbolu.

|Vlastnost|Datový typ|Popis|
|--------------|---------------|-----------------|
|[IDiaSymbol::get_baseType](../../debugger/debug-interface-access/idiasymbol-get-basetype.md)|`DWORD`|Jedna z hodnot [výčtu basictype –](../../debugger/debug-interface-access/basictype.md) .|
|[IDiaSymbol::get_classParent](../../debugger/debug-interface-access/idiasymbol-get-classparent.md)|`IDiaSymbol*`|Nadřazené třídy tohoto výčtu, pokud existuje.|
|[IDiaSymbol::get_classParentId](../../debugger/debug-interface-access/idiasymbol-get-classparentid.md)|`DWORD`|ID nadřazeného symbolu třídy|
|[IDiaSymbol::get_constructor](../../debugger/debug-interface-access/idiasymbol-get-constructor.md)|`BOOL`|`TRUE`, zda má výčet konstruktor.|
|[IDiaSymbol::get_constType](../../debugger/debug-interface-access/idiasymbol-get-consttype.md)|`BOOL`|`TRUE`, zda je výčet označen jako const.|
|[IDiaSymbol::get_hasAssignmentOperator](../../debugger/debug-interface-access/idiasymbol-get-hasassignmentoperator.md)|`BOOL`|`TRUE`, zda má výčet operátor přiřazení.|
|[IDiaSymbol::get_hasCastOperator](../../debugger/debug-interface-access/idiasymbol-get-hascastoperator.md)|`BOOL`|`TRUE`, zda má výčet operátor přetypování.|
|[IDiaSymbol::get_hasNestedTypes](../../debugger/debug-interface-access/idiasymbol-get-hasnestedtypes.md)|`BOOL`|`TRUE`, zda má výčet vnořené typy.|
|[IDiaSymbol::get_length](../../debugger/debug-interface-access/idiasymbol-get-length.md)|`DWORD`|Délka tohoto výčtu v bajtech|
|[IDiaSymbol::get_lexicalParent](../../debugger/debug-interface-access/idiasymbol-get-lexicalparent.md)|`IDiaSymbol*`|Symbol ohraničujícího [kompilantu](../../debugger/debug-interface-access/compiland.md)|
|[IDiaSymbol::get_lexicalParentId](../../debugger/debug-interface-access/idiasymbol-get-lexicalparentid.md)|`DWORD`|ID lexikálního nadřazeného symbolu|
|[IDiaSymbol::get_name](../../debugger/debug-interface-access/idiasymbol-get-name.md)|`BSTR`|Název výčtového typu.|
|[IDiaSymbol::get_nested](../../debugger/debug-interface-access/idiasymbol-get-nested.md)|`BOOL`|`TRUE`, pokud je výčet vnořený.|
|[IDiaSymbol::get_overloadedOperator](../../debugger/debug-interface-access/idiasymbol-get-overloadedoperator.md)|`BOOL`|`TRUE`, zda má výčet nějaké přetížené operátory.|
|[IDiaSymbol::get_packed](../../debugger/debug-interface-access/idiasymbol-get-packed.md)|`BOOL`|`TRUE`, zda je výčet zabalen.|
|[IDiaSymbol::get_scoped](../../debugger/debug-interface-access/idiasymbol-get-scoped.md)|`BOOL`|`TRUE`, je-li výčet zobrazen v neglobálním lexikálním oboru.|
|[IDiaSymbol::get_symIndexId](../../debugger/debug-interface-access/idiasymbol-get-symindexid.md)|`DWORD`|ID indexu symbolu|
|[IDiaSymbol::get_symTag](../../debugger/debug-interface-access/idiasymbol-get-symtag.md)|`DWORD`|Vrátí `SymTagEnum` (jedna z hodnot [výčtu SymTagEnum –](../../debugger/debug-interface-access/symtagenum.md) ).|
|[IDiaSymbol::get_type](../../debugger/debug-interface-access/idiasymbol-get-type.md)|`IDiaSymbol*`|Symbol základního typu|
|[IDiaSymbol::get_typeId](../../debugger/debug-interface-access/idiasymbol-get-typeid.md)|`DWORD`|ID symbolu typu|
|[IDiaSymbol::get_unalignedType](../../debugger/debug-interface-access/idiasymbol-get-unalignedtype.md)|`BOOL`|`TRUE`, pokud není výčet vyrovnaný.|
|[IDiaSymbol::get_volatileType](../../debugger/debug-interface-access/idiasymbol-get-volatiletype.md)|`BOOL`|`TRUE`, zda je výčet označen jako volatile.|

## <a name="see-also"></a>Viz také:
- [Hierarchie tříd typů symbolů](../../debugger/debug-interface-access/class-hierarchy-of-symbol-types.md)