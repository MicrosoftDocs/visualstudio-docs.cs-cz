---
title: 'IDebugThread2:: Resume | Microsoft Docs'
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "80718683"
---
# <a name="idebugthread2resume"></a>IDebugThread2::Resume
Obnoví provádění vlákna.

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
mimo Vrátí počet pozastavení po operaci obnovení.

## <a name="return-value"></a>Návratová hodnota
 V případě úspěchu vrátí. `S_OK` jinak vrátí kód chyby.

## <a name="remarks"></a>Poznámky
 Každé volání této metody sníží počet pozastavení, dokud nedosáhne hodnoty 0, spuštění je ve skutečnosti obnoveno. Tento počet pozastavení se zobrazí v okně ladění **vláken** .

 Pro každé volání této metody musí existovat předchozí volání metody [Suspend](../../../extensibility/debugger/reference/idebugthread2-suspend.md) . Počet pozastavení určuje, kolikrát byla `IDebugThread2::Suspend` metoda volána zatím.

## <a name="see-also"></a>Viz také
- [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)
- [Suspend](../../../extensibility/debugger/reference/idebugthread2-suspend.md)
