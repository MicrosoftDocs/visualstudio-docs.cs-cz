---
title: Zdroje událostí (Visual Studio SDK) | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], event sources
ms.assetid: b9ba0908-ae4c-4a64-aab1-bee453dd7a22
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 13842ab7b231d04bdbcafdf32534edc4eb2a9af6
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "80738783"
---
# <a name="event-sources-visual-studio-sdk"></a>Zdroje událostí (Visual Studio SDK)
Existují dva zdroje událostí: ladicí stroj (DE) a správce ladění relace (SDM). Události odeslané z DE mají modul, který není NULL, zatímco události odesílané z modelu SDM mají modul s hodnotou NULL.

## <a name="example"></a>Příklad
Následující příklad ukazuje, jak odeslat **IDebugProgramCreateEvent2** z de do SDM.

```csharp
CDebugProgramCreateEvent* pProgramCreateEvent = new CDebugProgramCreateEvent();
if (FAILED(pCallback->Event(m_pEngine, NULL, m_pProgram, NULL, pProgramCreateEvent, IID_IDebugProgramCreateEvent2, EVENT_ASYNCHRONOUS)))
{
    // Handle failure here.
}
]

CEvent * pProgCreate = new CEvent(IID_IDebugProgramCreateEvent2, EVENT_ASYNCHRONOUS);
pProgCreate->SendEvent(pCallback, m_pEngine, (IDebugProgram2 *)this, NULL);

HRESULT CEvent::SendEvent(IDebugEventCallback2 *pCallback, IDebugEngine2 *pEngine, IDebugProgram2 *pProgram, IDebugThread2 *pThread) {
    HRESULT hr;

    if (m_dwAttrib & EVENT_STOPPING)
    {
        hr = SendStoppingEvent(pCallback, pEngine, pProgram, pThread);
    }
    else if (m_dwAttrib & EVENT_SYNCHRONOUS)
    {
        hr = SendSynchronousEvent(pCallback, pEngine, pProgram, pThread);
    }
    else
    {
        assert(m_dwAttrib == 0);
        hr = SendAsynchronousEvent(pCallback, pEngine, pProgram, pThread);
    }

    return hr;
}

HRESULT CEvent::SendAsynchronousEvent(IDebugEventCallback2 *pCallback, IDebugEngine2 *pEngine, IDebugProgram2 *pProgram, IDebugThread2 *pThread) {

    HRESULT hr;

    // Make sure the CEvent object running this code is not deleted until the code completes.
    AddRef();

    pCallback->Event(pEngine, NULL, pProgram, pThread, (IDebugEvent2 *)this, m_riid, m_dwAttrib);

    // No error recovery here.
    hr = S_OK;

    Release();
    return hr;
}

```

## <a name="see-also"></a>Viz také
- [Odesílání událostí](../../extensibility/debugger/sending-events.md)
