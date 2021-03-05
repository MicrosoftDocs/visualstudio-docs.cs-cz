---
description: Získá rozsah příkazů souboru kontextu dokumentu.
title: 'IDebugDocumentContext2:: GetStatementRange | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDocumentContext2::GetStatementRange
helpviewer_keywords:
- IDebugDocumentContext2::GetStatementRange
ms.assetid: bc94851a-0ec4-47ea-99c7-0a585e54e726
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: c23de6f76ac4aa205ac50636775ee019da34137a
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2021
ms.locfileid: "102162872"
---
# <a name="idebugdocumentcontext2getstatementrange"></a>IDebugDocumentContext2::GetStatementRange
Získá rozsah příkazů souboru kontextu dokumentu.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT GetStatementRange(
    TEXT_POSITION* pBegPosition,
    TEXT_POSITION* pEndPosition
);
```

```csharp
int GetStatementRange(
    TEXT_POSITION[] pBegPosition,
    TEXT_POSITION[] pEndPosition
);
```

## <a name="parameters"></a>Parametry
`pBegPosition`\
[in, out] Struktura [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md) , která se vyplní počáteční pozicí. Pokud tyto informace nejsou potřeba, nastavte tento argument na hodnotu null.

`pEndPosition`\
[in, out] Struktura [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md) , která se vyplní koncovou pozicí. Pokud tyto informace nejsou potřeba, nastavte tento argument na hodnotu null.

## <a name="return-value"></a>Návratová hodnota
V případě úspěchu vrátí. `S_OK` jinak vrátí kód chyby.

## <a name="remarks"></a>Poznámky
Rozsah příkazů je rozsah řádků, které přispěly k kódu, na který odkazuje tento kontext dokumentu.

Chcete-li získat rozsah zdrojového kódu (včetně komentářů) v rámci tohoto kontextu dokumentu, zavolejte metodu [GetSourceRange –](../../../extensibility/debugger/reference/idebugdocumentcontext2-getsourcerange.md) .

## <a name="example"></a>Příklad
Následující příklad ukazuje, jak implementovat tuto metodu pro jednoduchý `CDebugContext` objekt, který zpřístupňuje rozhraní [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md) . Tento příklad vyplní koncovou pozici pouze v případě, že počáteční pozice není hodnota null.

```cpp
HRESULT CDebugContext::GetStatementRange(TEXT_POSITION* pBegPosition,
                                         TEXT_POSITION* pEndPosition)
{
    HRESULT hr;

    // Check for a valid beginning position argument pointer.
    if (pBegPosition)
    {
        // Copy the member TEXT_POSITION into the local pBegPosition.
        memcpy(pBegPosition, &m_pos, sizeof (TEXT_POSITION));

        // Check for a valid ending position argument pointer.
        if (pEndPosition)
        {
            // Copy the member TEXT_POSITION into the local pEndPosition.
            memcpy(pEndPosition, &m_pos, sizeof (TEXT_POSITION));
        }
        hr = S_OK;
    }
    else
    {
        hr = E_INVALIDARG;
    }

    return hr;
}
```

## <a name="see-also"></a>Viz také
- [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)
- [GetSourceRange](../../../extensibility/debugger/reference/idebugdocumentcontext2-getsourcerange.md)
- [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md)
