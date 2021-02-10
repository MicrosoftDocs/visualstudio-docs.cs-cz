---
title: 'IDebugThread2:: GetLogicalThread | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugThread2::GetLogicalThread
helpviewer_keywords:
- IDebugThread2::GetLogicalThread
ms.assetid: bce6230e-41d4-49b7-a050-2dde5efb6805
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 05d788f63d4807ccfd8e99d36cbf858df2be499f
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99940251"
---
# <a name="idebugthread2getlogicalthread"></a>IDebugThread2::GetLogicalThread
Ladicí stroje tuto metodu neimplementují.

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
pro Objekt [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md) , který představuje rámec zásobníku.

`ppLogicalThread`\
mimo Vrátí `IDebugLogicalThread2` rozhraní, které představuje přidružené logické vlákno. Implementace ladicího modulu by měla být nastavena na hodnotu null.

## <a name="return-value"></a>Návratová hodnota
 Implementace modulu ladění vždy vrací `E_NOTIMPL` .

## <a name="see-also"></a>Viz také
- [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)
