---
title: UsingNamespace – | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- UsingNamespace symbol tag
ms.assetid: e8e1beb5-7cb9-43b4-9ff4-760d5f91ea2d
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 3662bdc61cd98a36161bd8972a98cb4f168bc452
ms.sourcegitcommit: 66f31cc4ce1236e638ab58d2f70d3646206386fa
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/27/2020
ms.locfileid: "85460963"
---
# <a name="usingnamespace"></a>UsingNameSpace
Na některé symboly může odkazovat obor názvů a následně by měla být identifikována `SymTagUsingNameSpace` značkou.

> [!NOTE]
> Značka symbolu UsingNamespace – se zobrazí pouze ve spravovaném kódu.

## <a name="properties"></a>Vlastnosti
 V následující tabulce jsou uvedeny vlastnosti, které jsou platné pro tento typ symbolu.

|Vlastnost|Datový typ|Popis|
|--------------|---------------|-----------------|
|[IDiaSymbol::get_lexicalParent](../../debugger/debug-interface-access/idiasymbol-get-lexicalparent.md)|`IDiaSymbol*`|Symbol pro ohraničující kompilantu, blok nebo funkci|
|[IDiaSymbol::get_lexicalParentId](../../debugger/debug-interface-access/idiasymbol-get-lexicalparentid.md)|`DWORD`|ID lexikálního nadřazeného symbolu|
|[IDiaSymbol::get_name](../../debugger/debug-interface-access/idiasymbol-get-name.md)|`BSTR`|Název oboru názvů.|
|[IDiaSymbol::get_symIndexId](../../debugger/debug-interface-access/idiasymbol-get-symindexid.md)|`DWORD`|ID indexu symbolu|
|[IDiaSymbol::get_symTag](../../debugger/debug-interface-access/idiasymbol-get-symtag.md)|`DWORD`|Vrátí `SymTagNameSpace` (jednu z hodnot [výčtu SymTagEnum –](../../debugger/debug-interface-access/symtagenum.md) ).|

## <a name="see-also"></a>Viz také
- [Lexikální hierarchie typů symbolů](../../debugger/debug-interface-access/lexical-hierarchy-of-symbol-types.md)