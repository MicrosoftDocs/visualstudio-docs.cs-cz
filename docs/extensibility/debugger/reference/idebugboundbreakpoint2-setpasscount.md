---
title: IDebugBoundBreakpoint2::SetPassCount | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugBoundBreakpoint2::SetPassCount
helpviewer_keywords:
- SetPassCount method
- IDebugBoundBreakpoint2::SetPassCount method
ms.assetid: b32c12f9-b34d-43bd-a1b9-61af6cf8e51b
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: bcc7bd57ce0c392a2874f107c6e4d8d5753399d3
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80735442"
---
# <a name="idebugboundbreakpoint2setpasscount"></a>IDebugBoundBreakpoint2::SetPassCount
Nastaví nebo změní počet průchodů přidružených k této vázané zarážky.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT SetPassCount( 
   BP_PASSCOUNT bpPassCount
);
```

```csharp
int SetPassCount( 
   BP_PASSCOUNT bpPassCount
);
```

## <a name="parameters"></a>Parametry
`bpPassCount`\
[v] [Struktura BP_PASSCOUNT,](../../../extensibility/debugger/reference/bp-passcount.md) která určuje počet průchodů.

## <a name="return-value"></a>Návratová hodnota
 V případě `S_OK`úspěchu vrátí ; v opačném případě vrátí kód chyby. Vrátí, `E_BP_DELETED` pokud je nastaven stav vázaného `BPS_DELETED` objektu zarážky (část [BP_STATE](../../../extensibility/debugger/reference/bp-state.md) výčet).

## <a name="remarks"></a>Poznámky
 Počet průchodů určuje, kdy je aktivována zarážka. Aktuální pass nebo počet přístupů lze získat voláním [GetHitCount](../../../extensibility/debugger/reference/idebugboundbreakpoint2-gethitcount.md) metoda.

 Počet průchodů, který byl dříve přidružen k této zarážky, bude ztracen.

## <a name="see-also"></a>Viz také
- [IDebugBoundBreakpoint2](../../../extensibility/debugger/reference/idebugboundbreakpoint2.md)
- [GetHitCount](../../../extensibility/debugger/reference/idebugboundbreakpoint2-gethitcount.md)
- [BP_PASSCOUNT](../../../extensibility/debugger/reference/bp-passcount.md)
- [BP_STATE](../../../extensibility/debugger/reference/bp-state.md)
