---
title: IDebugDocumentContext2::GetStatementRange | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDocumentContext2::GetStatementRange
helpviewer_keywords:
- IDebugDocumentContext2::GetStatementRange
ms.assetid: bc94851a-0ec4-47ea-99c7-0a585e54e726
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 50e521d98f10477d56dfece30e20fd000b87b632
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80731769"
---
# <a name="idebugdocumentcontext2getstatementrange"></a>IDebugDocumentContext2::GetStatementRange
Získá rozsah příkazu souboru kontextu dokumentu.

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
[dovnitř, ven] [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md) struktura, která je vyplněna počáteční polohou. Pokud tyto informace nejsou potřeba, nastavte tento argument na hodnotu null.

`pEndPosition`\
[dovnitř, ven] [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md) struktura, která je vyplněna koncovou polohou. Pokud tyto informace nejsou potřeba, nastavte tento argument na hodnotu null.

## <a name="return-value"></a>Návratová hodnota
V případě `S_OK`úspěchu vrátí ; v opačném případě vrátí kód chyby.

## <a name="remarks"></a>Poznámky
Rozsah výkazu je rozsah řádků, které přispěly kódem, na který odkazuje tento kontext dokumentu.

Chcete-li získat rozsah zdrojového kódu (včetně komentářů) v rámci tohoto kontextu dokumentu, volání [GetSourceRange](../../../extensibility/debugger/reference/idebugdocumentcontext2-getsourcerange.md) metoda.

## <a name="example"></a>Příklad
Následující příklad ukazuje, jak implementovat `CDebugContext` tuto metodu pro jednoduchý objekt, který zveřejňuje rozhraní [IDebugDocumentContext2.](../../../extensibility/debugger/reference/idebugdocumentcontext2.md) Tento příklad vyplní koncovou pozici pouze v případě, že počáteční pozice není nulovou hodnotou.

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
