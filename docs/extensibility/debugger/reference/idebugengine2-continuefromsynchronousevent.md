---
title: 'IDebugEngine2:: ContinueFromSynchronousEvent | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEngine2::ContinueFromSynchronousEvent
helpviewer_keywords:
- IDebugEngine2::ContinueFromSynchronousEvent
ms.assetid: 9a57dfcd-df8e-4be5-b1fe-bd853e3c6bb2
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 78485e209c93e0673aa32587b21bb074aac047e1
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99921132"
---
# <a name="idebugengine2continuefromsynchronousevent"></a>IDebugEngine2::ContinueFromSynchronousEvent
Volá se správcem ladění relace (SDM) k označení toho, že byla přijata a zpracována synchronní událost ladění, která byla dříve odeslána ladicím modulem (DE) do modelu SDM.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT ContinueFromSynchronousEvent(
    IDebugEvent2* pEvent
);
```

```csharp
HRESULT ContinueFromSynchronousEvent(
    IDebugEvent2 pEvent
);
```

## <a name="parameters"></a>Parametry
`pEvent`\
pro Objekt [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) , který představuje dříve odeslanou synchronní událost, ze které by měl nyní ladicí program pokračovat.

## <a name="return-value"></a>Návratová hodnota
V případě úspěchu vrátí. `S_OK` jinak vrátí kód chyby.

## <a name="remarks"></a>Poznámky
DE musí ověřit, zda se jednalo o zdroj události reprezentované `pEvent` parametrem.

## <a name="example"></a>Příklad
Následující příklad ukazuje, jak implementovat tuto metodu pro jednoduchý `CEngine` objekt, který implementuje rozhraní [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md) .

```cpp
HRESULT CEngine::ContinueFromSynchronousEvent(IDebugEvent2* pEvent)
{
    HRESULT hr;

    // Create a pointer to a unique event interface defined for batch file
    // breaks.
    IAmABatchFileEvent *pBatEvent;
    // Check for successful query for the unique batch file event
    // interface.
    if (SUCCEEDED(pEvent->QueryInterface(IID_IAmABatchFileEvent,
                                        (void **)&pBatEvent)))
    {
        // Release the result of the QI.
        pBatEvent->Release();
        // Check thread message for notification to continue.
        if (PostThreadMessage(GetCurrentThreadId(),
                              WM_CONTINUE_SYNC_EVENT,
                              0,
                              0))
        {
            hr = S_OK;
        }
        else
        {
            hr = HRESULT_FROM_WIN32(GetLastError());
        }
    }
    else
    {
        hr = E_INVALIDARG;
    }
    return hr;
}
```

## <a name="see-also"></a>Viz také
- [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)
- [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)
