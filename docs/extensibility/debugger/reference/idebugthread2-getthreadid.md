---
title: 'IDebugThread2:: GetThreadId | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugThread2::GetThreadId
helpviewer_keywords:
- IDebugThread2::GetThreadId
ms.assetid: db8b1c07-6b86-47f9-b292-bac19c276d36
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 3e7dfb6714283fa2db1dc2fd8435a91a5c8dc56a
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99893812"
---
# <a name="idebugthread2getthreadid"></a>IDebugThread2::GetThreadId
Získá identifikátor systémového vlákna.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT GetThreadId (
    DWORD* pdwThreadId
);
```

```csharp
int GetThreadId (
    out uint pdwThreadId
);
```

## <a name="parameters"></a>Parametry
`pdwThreadId`\
mimo Vrátí identifikátor systémového vlákna.

## <a name="return-value"></a>Návratová hodnota
V případě úspěchu vrátí. `S_OK` jinak vrátí kód chyby.

## <a name="remarks"></a>Poznámky
ID vlákna se používá k identifikaci vlákna mezi všemi ostatními vlákny v procesu.

## <a name="example"></a>Příklad
Následující příklad ukazuje, jak implementovat tuto metodu pro jednoduchý `CProgram` objekt, který implementuje rozhraní [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md) .

```cpp
HRESULT CProgram::GetThreadId(DWORD* pdwThreadId) {
    *pdwThreadId = GetCurrentThreadId();
    return NOERROR;
}
```

## <a name="see-also"></a>Viz také
- [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)
