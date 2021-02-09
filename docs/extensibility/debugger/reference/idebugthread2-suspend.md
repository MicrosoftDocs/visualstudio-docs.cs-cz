---
title: 'IDebugThread2:: Suspend | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugThread2::Suspend
helpviewer_keywords:
- IDebugThread2::Suspend
ms.assetid: 1e20be85-aa12-48de-bb83-0bf0976e99ae
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: ede08dfd2c5f8ee3a205f744388d9aac3f8f3709
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99893656"
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
mimo Vrátí počet pozastavení po operaci pozastavení.

## <a name="return-value"></a>Návratová hodnota
 V případě úspěchu vrátí. `S_OK` jinak vrátí kód chyby.

## <a name="remarks"></a>Poznámky
 Každé volání této metody zvýší počet pozastavení nad rámec 0. Tento počet pozastavení se zobrazí v okně ladění **vláken** .

 Pro každé volání této metody musí být pozdější volání metody [Resume](../../../extensibility/debugger/reference/idebugthread2-resume.md) .

## <a name="see-also"></a>Viz také
- [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)
- [Obnovit](../../../extensibility/debugger/reference/idebugthread2-resume.md)
