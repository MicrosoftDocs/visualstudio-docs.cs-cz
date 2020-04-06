---
title: IDebugThread2::Pozastavit | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugThread2::Suspend
helpviewer_keywords:
- IDebugThread2::Suspend
ms.assetid: 1e20be85-aa12-48de-bb83-0bf0976e99ae
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 74a7dd5dc69effbd46986eff963de3e740d9aa8e
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80718640"
---
# <a name="idebugthread2suspend"></a>IDebugThread2::Suspend
Pozastaví vlákno.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT Suspend ( 
   DWORD *pdwSuspendCount
);
```

```csharp
HRESULT Suspend ( 
   out uint pdwSuspendCount
);
```

## <a name="parameters"></a>Parametry
`pdwSuspendCount`\
[out] Vrátí počet pozastavení po operaci pozastavení.

## <a name="return-value"></a>Návratová hodnota
 V případě `S_OK`úspěchu vrátí ; v opačném případě vrátí kód chyby.

## <a name="remarks"></a>Poznámky
 Každé volání této metody se zpřísní počet pozastavení nad 0. Tento počet pozastavení se zobrazí v okně ladění **vlákna.**

 Pro každé volání této metody musí být pozdější volání [Resume](../../../extensibility/debugger/reference/idebugthread2-resume.md) metody.

## <a name="see-also"></a>Viz také
- [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)
- [Obnovit](../../../extensibility/debugger/reference/idebugthread2-resume.md)
