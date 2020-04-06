---
title: IDebugThread2::GetLogicalThread | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugThread2::GetLogicalThread
helpviewer_keywords:
- IDebugThread2::GetLogicalThread
ms.assetid: bce6230e-41d4-49b7-a050-2dde5efb6805
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: e148fb0b9b043fc1717effca00d698ee14beb2f1
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80718834"
---
# <a name="idebugthread2getlogicalthread"></a>IDebugThread2::GetLogicalThread
Ladicí moduly tuto metodu neimplementují.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT GetLogicalThread( 
   IDebugStackFrame2*     pStackFrame,
   IDebugLogicalThread2** ppLogicalThread
);
```

```csharp
int GetLogicalThread( 
   IDebugStackFrame2        pStackFrame,
   out IDebugLogicalThread2 ppLogicalThread
);
```

## <a name="parameters"></a>Parametry
`pStackFrame`\
[v] [Objekt IDebugStackFrame2,](../../../extensibility/debugger/reference/idebugstackframe2.md) který představuje rámec zásobníku.

`ppLogicalThread`\
[out] Vrátí `IDebugLogicalThread2` rozhraní, které představuje přidružené logické vlákno. Implementace ladicího modulu by měla nastavit na hodnotu null.

## <a name="return-value"></a>Návratová hodnota
 Implementace ladicího `E_NOTIMPL`modulu vždy vrátí .

## <a name="see-also"></a>Viz také
- [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)
