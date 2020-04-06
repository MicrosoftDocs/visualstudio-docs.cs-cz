---
title: IDebugThread2::Resume | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugThread2::Resume
helpviewer_keywords:
- IDebugThread2::Resume
ms.assetid: 36aad682-b0b9-40a2-b3fc-f0e61d41cdbc
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 3899dea7c33946588de4308f42b948ede703361a
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80718683"
---
# <a name="idebugthread2resume"></a>IDebugThread2::Resume
Pokračuje v provádění vlákna.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT Resume ( 
   DWORD *pdwSuspendCount
);
```

```csharp
int Resume ( 
   out uint pdwSuspendCount
);
```

## <a name="parameters"></a>Parametry
`pdwSuspendCount`\
[out] Vrátí počet pozastavení po operaci obnovení.

## <a name="return-value"></a>Návratová hodnota
 V případě `S_OK`úspěchu vrátí ; v opačném případě vrátí kód chyby.

## <a name="remarks"></a>Poznámky
 Každé volání této metody sníží počet pozastavení, dokud nedosáhne 0, kdy je spuštění skutečně obnoveno. Tento počet pozastavení se zobrazí v okně ladění **vlákna.**

 Pro každé volání této metody musí být předchozí volání [Suspend](../../../extensibility/debugger/reference/idebugthread2-suspend.md) metody. Počet pozastavení určuje, kolikrát `IDebugThread2::Suspend` byla metoda volána tak daleko.

## <a name="see-also"></a>Viz také
- [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)
- [Suspend](../../../extensibility/debugger/reference/idebugthread2-suspend.md)
