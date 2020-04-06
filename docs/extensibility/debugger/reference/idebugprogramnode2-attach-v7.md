---
title: IDebugProgramNode2::Attach_V7 | Dokumenty společnosti Microsoft
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
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
[v] [Rozhraní IDebugProgram2,](../../../extensibility/debugger/reference/idebugprogram2.md) které představuje program připojit.

`pCallback`\
[v] [Rozhraní IDebugCallBackback2,](../../../extensibility/debugger/reference/idebugeventcallback2.md) které má být použito k odeslání ladicích událostí do modulu SDM.

`dwReason`\
[v] Hodnota z [ATTACH_REASON](../../../extensibility/debugger/reference/attach-reason.md) výčtu, který určuje důvod pro připojení.

## <a name="return-value"></a>Návratová hodnota

Implementace by měla `E_NOTIMPL`vždy vrátit .

## <a name="remarks"></a>Poznámky

> [!WARNING]
> Od sady Visual Studio 2005 se tato metoda `E_NOTIMPL`již nepoužívá a měla by vždy vrátit . Alternativní přístup naleznete v rozhraní [IDebugProgramNodeAttach2,](../../../extensibility/debugger/reference/idebugprogramnodeattach2.md) pokud uzel programu potřebuje označit, že jej nelze připojit nebo `GUID`pokud uzel programu jednoduše nastavuje program . V opačném případě implementujte Metodu [Attach.](../../../extensibility/debugger/reference/idebugengine2-attach.md)

## <a name="prior-to-visual-studio-2005"></a>Před visual studio 2005

Tuto metodu je třeba implementovat pouze v případě, že DE běží v adresním prostoru programu, který je laděn. V opačném případě `S_FALSE`by tato metoda měla vrátit .

Při volání této metody musí DE odeslat objekt události [IDebugEngineCreateEvent2,](../../../extensibility/debugger/reference/idebugenginecreateevent2.md) pokud ještě nebyl odeslán pro tuto instanci rozhraní [IDebugEngine2,](../../../extensibility/debugger/reference/idebugengine2.md) stejně jako objekty událostí [IDebugProgramCreateEvent2](../../../extensibility/debugger/reference/idebugprogramcreateevent2.md) a [IDebugLoadCompleteEvent2.](../../../extensibility/debugger/reference/idebugloadcompleteevent2.md) Objekt události [IDebugEntryPointEvent2](../../../extensibility/debugger/reference/idebugentrypointevent2.md) je pak `dwReason` odeslán, pokud je `ATTACH_REASON_LAUNCH`parametr .

De musí volat metodu [GetProgramId](../../../extensibility/debugger/reference/idebugprogram2-getprogramid.md) na objektu [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) dodávaném objektem události [IDebugProgramCreateEvent2](../../../extensibility/debugger/reference/idebugprogramcreateevent2.md) a musí `IDebugProgram2` ukládat identifikátor GUID tohoto programu v datech instance pro objekt implementovaný de.

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
