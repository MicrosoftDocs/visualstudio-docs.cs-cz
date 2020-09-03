---
title: 'IDebugProgramNode2:: Attach_V7 | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgramNode2::Attach
helpviewer_keywords:
- IDebugProgramNode2::Attach_V7
- IDebugProgramNode2::Attach
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: bdee5b224ae38c3474009aeaf26e783ebc5dd139
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "80722137"
---
# <a name="idebugprogramnode2attach_v7"></a>IDebugProgramNode2::Attach_V7

> [!Note]
> Zastaralé. NEPOUŽÍVEJTE.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT Attach_V7 (
   IDebugProgram2*       pMDMProgram,
   IDebugEventCallback2* pCallback,
   DWORD                 dwReason
);
```

```csharp
int Attach_V7 (
   IDebugProgram2       pMDMProgram,
   IDebugEventCallback2 pCallback,
   uint                 dwReason
);
```

## <a name="parameters"></a>Parametry

`pMDMProgram`\
pro Rozhraní [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) , které představuje program, ke kterému se má připojit.

`pCallback`\
pro Rozhraní [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) , které se má použít k odeslání událostí ladění do SDM.

`dwReason`\
pro Hodnota z výčtu [ATTACH_REASON](../../../extensibility/debugger/reference/attach-reason.md) , která určuje důvod pro připojení.

## <a name="return-value"></a>Návratová hodnota

Implementace by měla vždycky vracet `E_NOTIMPL` .

## <a name="remarks"></a>Poznámky

> [!WARNING]
> Od sady Visual Studio 2005 tato metoda již není používána a měla by vždy vracet `E_NOTIMPL` . V rozhraní [IDebugProgramNodeAttach2](../../../extensibility/debugger/reference/idebugprogramnodeattach2.md) pro alternativní přístup, pokud je potřeba, aby uzel programu mohl určit, že není možné ho připojit, nebo jestli je uzel programu jednoduše nastavením programu `GUID` . V opačném případě Implementujte metodu [Attach](../../../extensibility/debugger/reference/idebugengine2-attach.md) .

## <a name="prior-to-visual-studio-2005"></a>Před verzí Visual Studio 2005

Tato metoda musí být implementována pouze v případě, že je DE spuštěna v adresním prostoru ladicího programu. V opačném případě by tato metoda měla vracet `S_FALSE` .

Při volání této metody musí metoda DE odeslat objekt události [IDebugEngineCreateEvent2](../../../extensibility/debugger/reference/idebugenginecreateevent2.md) , pokud ještě nebyla odeslána pro tuto instanci rozhraní [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md) , a také pro objekty událostí [IDebugProgramCreateEvent2](../../../extensibility/debugger/reference/idebugprogramcreateevent2.md) a [IDebugLoadCompleteEvent2](../../../extensibility/debugger/reference/idebugloadcompleteevent2.md) . Objekt události [IDebugEntryPointEvent2](../../../extensibility/debugger/reference/idebugentrypointevent2.md) se pak pošle, pokud `dwReason` je parametr `ATTACH_REASON_LAUNCH` .

Metoda DE musí volat metodu [GetProgramId](../../../extensibility/debugger/reference/idebugprogram2-getprogramid.md) na objekt [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) poskytnutý objektem události [IDebugProgramCreateEvent2](../../../extensibility/debugger/reference/idebugprogramcreateevent2.md) a musí ukládat identifikátor GUID tohoto programu v datech instance pro `IDebugProgram2` objekt implementovaný de.

## <a name="see-also"></a>Viz také

- [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)
- [IDebugProgramNodeAttach2](../../../extensibility/debugger/reference/idebugprogramnodeattach2.md)
- [Připojit](../../../extensibility/debugger/reference/idebugengine2-attach.md)
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
- [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)
- [IDebugEngineCreateEvent2](../../../extensibility/debugger/reference/idebugenginecreateevent2.md)
- [IDebugProgramCreateEvent2](../../../extensibility/debugger/reference/idebugprogramcreateevent2.md)
- [IDebugLoadCompleteEvent2](../../../extensibility/debugger/reference/idebugloadcompleteevent2.md)
- [IDebugEntryPointEvent2](../../../extensibility/debugger/reference/idebugentrypointevent2.md)
- [ATTACH_REASON](../../../extensibility/debugger/reference/attach-reason.md)
