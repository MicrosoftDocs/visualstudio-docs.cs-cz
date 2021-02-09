---
title: 'IDebugObject:: GetMemoryContext | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugObject::GetMemoryContext
helpviewer_keywords:
- IDebugObject::GetMemoryContext method
ms.assetid: 6760a0d3-a898-4e81-b68f-c45c584b225b
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: a2c7dbdace7c40ccba25cdce0306e6f0998489f4
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99920784"
---
# <a name="idebugobjectgetmemorycontext"></a>IDebugObject::GetMemoryContext
Získá kontext paměti, který představuje adresu hodnoty objektu.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT GetMemoryContext( 
   IDebugMemoryContext2** pContext
);
```

```csharp
int GetMemoryContext(
   ref IDebugMemoryContext2 pContext
);
```

## <a name="parameters"></a>Parametry
`pContext`\
mimo Vrátí objekt [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md) představující adresu hodnoty objektu.

## <a name="return-value"></a>Návratová hodnota
 V případě úspěchu vrátí S_OK; v opačném případě vrátí kód chyby.

## <a name="remarks"></a>Poznámky
 Vrácený kontext paměti určuje adresu hodnoty reprezentované tímto objektem [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) .

## <a name="see-also"></a>Viz také
- [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)
