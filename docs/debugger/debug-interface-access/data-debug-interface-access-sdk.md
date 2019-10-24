---
title: Data (Debug Interface Access SDK) | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- global variables [C++], as symbols
- local variables [C++], as symbols
- class members [C++], as symbols
- Data symbol
ms.assetid: 0f17e96a-2e06-42c9-a877-3e5e670ee0ef
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 94e1be7a1809c52683be045f71fcc681a6b270a8
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/22/2019
ms.locfileid: "72745303"
---
# <a name="data-debug-interface-access-sdk"></a>Data (Přístup k rozhraní ladění SDK)
Všechny proměnné, jako jsou parametry, místní proměnné, globální proměnné a členy třídy, jsou identifikovány `SymTagData` symboly. Pro tento typ jsou také identifikovány konstantní hodnoty (`LocIsConstant`).

## <a name="properties"></a>Vlastnosti
 V následující tabulce jsou uvedeny vlastnosti, které jsou platné pro tento typ symbolu.

|Vlastnost|Datový typ|Popis|
|--------------|---------------|-----------------|
|[IDiaSymbol::get_access](../../debugger/debug-interface-access/idiasymbol-get-access.md)|`DWORD`|Pokud pole, pak jednu z hodnot [výčtu CV_access_e](../../debugger/debug-interface-access/cv-access-e.md).|
|[IDiaSymbol::get_addressOffset](../../debugger/debug-interface-access/idiasymbol-get-addressoffset.md)|`DWORD`|Odsadit část umístění; Podrobnosti najdete v tématu [výčet LocationType –](../../debugger/debug-interface-access/locationtype.md).|
|[IDiaSymbol::get_addressSection](../../debugger/debug-interface-access/idiasymbol-get-addresssection.md)|`DWORD`|Část umístění; Podrobnosti najdete v tématu [výčet LocationType –](../../debugger/debug-interface-access/locationtype.md).|
|[IDiaSymbol::get_addressTaken](../../debugger/debug-interface-access/idiasymbol-get-addresstaken.md)|`BOOL`|`TRUE`, jestli adresa tohoto data odkazuje jiným symbolem.|
|[IDiaSymbol::get_bitPosition](../../debugger/debug-interface-access/idiasymbol-get-bitposition.md)|`DWORD`|Bitová pozice umístění; Podrobnosti najdete v tématu [výčet LocationType –](../../debugger/debug-interface-access/locationtype.md) (není podporován v DIA SDK v 8.0).|
|[IDiaSymbol::get_classParent](../../debugger/debug-interface-access/idiasymbol-get-classparent.md)|`IDiaSymbol*`|Symbol pro třídu, pokud se jedná o strukturu, sjednocení nebo pole třídy.|
|[IDiaSymbol::get_classParentId](../../debugger/debug-interface-access/idiasymbol-get-classparentid.md)|`DWORD`|ID nadřazeného symbolu třídy|
|[IDiaSymbol::get_compilerGenerated](../../debugger/debug-interface-access/idiasymbol-get-compilergenerated.md)|`BOOL`|`TRUE`, zda byla data generována kompilátorem.|
|[IDiaSymbol::get_constType](../../debugger/debug-interface-access/idiasymbol-get-consttype.md)|`BOOL`|`TRUE`, zda jsou data označena jako konstantní.|
|[IDiaSymbol::get_dataKind](../../debugger/debug-interface-access/idiasymbol-get-datakind.md)|`DWORD`|Jedna z hodnot [výčtu datakind](../../debugger/debug-interface-access/datakind.md) .|
|[IDiaSymbol::get_isAggregated](../../debugger/debug-interface-access/idiasymbol-get-isaggregated.md)|`BOOL`|`TRUE`, zda jsou data součástí agregovaného datového typu (pouze v DIA SDK v 8.0 a novějších).|
|[IDiaSymbol::get_isSplitted](../../debugger/debug-interface-access/idiasymbol-get-issplitted.md)|`BOOL`|`TRUE`, pokud jsou data rozdělená na agregaci více symbolů (jenom v DIA SDK v 8.0 a novějších verzích).|
|[IDiaSymbol::get_length](../../debugger/debug-interface-access/idiasymbol-get-length.md)|`ULONGLONG`|Délka bitového pole; Podrobnosti najdete v tématu [výčet LocationType –](../../debugger/debug-interface-access/locationtype.md).|
|[IDiaSymbol::get_lexicalParent](../../debugger/debug-interface-access/idiasymbol-get-lexicalparent.md)|`IDiaSymbol*`|Symbol pro ohraničující kompilantu, funkci nebo blok|
|[IDiaSymbol::get_lexicalParentId](../../debugger/debug-interface-access/idiasymbol-get-lexicalparentid.md)|`DWORD`|ID lexikálního nadřazeného symbolu|
|[IDiaSymbol::get_locationType](../../debugger/debug-interface-access/idiasymbol-get-locationtype.md)|`DWORD`|Libovolný povolený typ umístění; Podrobnosti najdete v tématu [umístění symbolů](../../debugger/debug-interface-access/symbol-locations.md) .|
|[IDiaSymbol::get_name](../../debugger/debug-interface-access/idiasymbol-get-name.md)|`BSTR`|Název proměnné|
|[IDiaSymbol::get_offset](../../debugger/debug-interface-access/idiasymbol-get-offset.md)|`LONG`|Posun od obsahu registru; Podrobnosti najdete v tématu [výčet LocationType –](../../debugger/debug-interface-access/locationtype.md).|
|[IDiaSymbol::get_registerId](../../debugger/debug-interface-access/idiasymbol-get-registerid.md)|`DWORD`|Registrovat označení umístění; Podrobnosti najdete v tématu [výčet LocationType –](../../debugger/debug-interface-access/locationtype.md).|
|[IDiaSymbol::get_relativeVirtualAddress](../../debugger/debug-interface-access/idiasymbol-get-relativevirtualaddress.md)|`DWORD`|Relativní pozice dat v rámci bloku|
|[IDiaSymbol::get_slot](../../debugger/debug-interface-access/idiasymbol-get-slot.md)|`DWORD`|Získá číslo pozice dat.|
|[IDiaSymbol::get_symIndexId](../../debugger/debug-interface-access/idiasymbol-get-symindexid.md)|`DWORD`|ID indexu symbolu|
|[IDiaSymbol::get_symTag](../../debugger/debug-interface-access/idiasymbol-get-symtag.md)|`DWORD`|Vrátí `SymTagData` (jedna z hodnot [výčtu SymTagEnum –](../../debugger/debug-interface-access/symtagenum.md) ).|
|[IDiaSymbol::get_token](../../debugger/debug-interface-access/idiasymbol-get-token.md)|`DWORD`|Token metadat představující data|
|[IDiaSymbol::get_type](../../debugger/debug-interface-access/idiasymbol-get-type.md)|`IDiaSymbol*`|Symbol pro typ proměnné|
|[IDiaSymbol::get_typeId](../../debugger/debug-interface-access/idiasymbol-get-typeid.md)|`DWORD`|ID symbolu typu proměnné|
|[IDiaSymbol::get_unalignedType](../../debugger/debug-interface-access/idiasymbol-get-unalignedtype.md)|`BOOL`|`TRUE`, pokud nejsou data zarovnaná.|
|[IDiaSymbol::get_value](../../debugger/debug-interface-access/idiasymbol-get-value.md)|`VARIANT`|Hodnota konstantních dat|
|[IDiaSymbol::get_virtualAddress](../../debugger/debug-interface-access/idiasymbol-get-virtualaddress.md)|`ULONGLONG`|Pozice dat ve spustitelném souboru.|
|[IDiaSymbol::get_volatileType](../../debugger/debug-interface-access/idiasymbol-get-volatiletype.md)|`BOOL`|`TRUE`, zda jsou data označena jako nestálá.|

## <a name="see-also"></a>Viz také:
- [CV_access_e – výčet](../../debugger/debug-interface-access/cv-access-e.md)
- [DataKind – výčet](../../debugger/debug-interface-access/datakind.md)
- [Lexikální hierarchie typů symbolů](../../debugger/debug-interface-access/lexical-hierarchy-of-symbol-types.md)
- [LocationType – výčet](../../debugger/debug-interface-access/locationtype.md)
- [Umístění symbolů](../../debugger/debug-interface-access/symbol-locations.md)