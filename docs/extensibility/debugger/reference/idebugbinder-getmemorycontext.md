---
title: 'IDebugBinder:: GetMemoryContext | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugBinder::GetMemoryContext
helpviewer_keywords:
- IDebugBinder::GetMemoryContext method
ms.assetid: 801c5b60-acff-4822-b23d-e9c7bbca8a0f
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 1c203e83a595562e604d8c32b09056c8544bfd1d
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99938967"
---
# <a name="idebugbindergetmemorycontext"></a>IDebugBinder::GetMemoryContext
Tato metoda převede buď umístění objektu, nebo adresu paměti na kontext paměti.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT GetMemoryContext( 
   IDebugField*           pField,
   DWORD                  dwConstant,
   IDebugMemoryContext2** ppMemCxt
);
```

```csharp
int GetMemoryContext(
   IDebugField              pField,
   uint                     dwConstant,
   out IDebugMemoryContext2 ppMemCxt
);
```

## <a name="parameters"></a>Parametry
`pField`\
pro [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) popisující objekt, který se má najít. IF `NULL` a `dwConstant` místo toho použít.

`dwConstant`\
pro Adresa paměti konstanty, například 0x5000.

`ppMemCxt`\
mimo Vrátí rozhraní [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md) , které představuje adresu objektu, nebo adresu v paměti.

## <a name="return-value"></a>Návratová hodnota
 V případě úspěchu vrátí. `S_OK` jinak vrátí kód chyby.

## <a name="see-also"></a>Viz také
- [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md)
- [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
