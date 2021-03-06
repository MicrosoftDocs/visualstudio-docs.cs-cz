---
description: Obsahuje informace o stavu prohledávaných cest hledání symbolů.
title: MODULE_SYMBOL_SEARCH_INFO | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- MODULE_SYMBOL_SEARCH_INFO
helpviewer_keywords:
- MODULE_SYMBOL_SEARCH_INFO structure
ms.assetid: 432aff03-08a5-4c5a-b2d5-e212090fc70a
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: bc914334fc4b8ebf2dd73f691cdec242e19364a9
ms.sourcegitcommit: f33ca1fc99f5d9372166431cefd0e0e639d20719
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2021
ms.locfileid: "102222286"
---
# <a name="module_symbol_search_info"></a>MODULE_SYMBOL_SEARCH_INFO

Obsahuje informace o stavu prohledávaných cest hledání symbolů.

## <a name="syntax"></a>Syntax

```cpp
typedef struct _tagSYMBOL_SEARCH_INFO
{
    SYMBOL_SEARCH_INFO_FIELDS dwValidFields;
    BSTR                      bstrVerboseSearchInfo;
} MODULE_SYMBOL_SEARCH_INFO;
```

```csharp
public struct MODULE_SYMBOL_SEARCH_INFO {
    public uint   dwValidFields;
    public string bstrVerboseSearchInfo;
}
```

## <a name="members"></a>Členové

`dwValidFields`\
Kombinace příznaků z výčtu [SYMBOL_SEARCH_INFO_FIELDS](../../../extensibility/debugger/reference/symbol-search-info-fields.md) určující druh informací o hledání popsaných v této struktuře.

`bstrVerboseSearchInfo`\
Cesta a výsledky hledání jsou zřetězené do jednoho řetězce.

## <a name="remarks"></a>Poznámky

Tato struktura je vrácena voláním metody [GetSymbolInfo](../../../extensibility/debugger/reference/idebugmodule3-getsymbolinfo.md) .

Pokud `bstrVerboseSearchInfo` pole není prázdné, obsahuje seznam prohledávaných cest a výsledky tohoto hledání. Seznam je formátován s cestou, následovanou třemi tečkami ("...") následovaným výsledkem. Pokud existuje více než jedna dvojice výsledků cesty, pak je každý pár oddělený dvojicí "\r\n" (přeprava za sekundu). Vzor vypadá takto:

\<path>...\<result> \r\n \<path> ... \<result> \r\n \<path> ...\<result>

Všimněte si, že poslední položka nemá sekvenci \r\n.

Tady je možný `bstrVerboseSearchInfo` řetězec, který byl odeslán do standardního umístění.

`c:\symbols\user32.pdb... File not found.`

`c:\winnt\symbols\user32.pdb... Version does not match.`

`\\symbols\symbols\user32.dll\0a8sd0ad8ad\user32.pdb... Symbols loaded.`

## <a name="requirements"></a>Požadavky

Záhlaví: msdbg. h

Obor názvů: Microsoft. VisualStudio. Debugger. Interop

Sestavení: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Viz také

- [Struktury a sjednocení](../../../extensibility/debugger/reference/structures-and-unions.md)
- [GetSymbolInfo](../../../extensibility/debugger/reference/idebugmodule3-getsymbolinfo.md)
