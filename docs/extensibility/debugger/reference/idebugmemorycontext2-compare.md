---
title: IDebugMemoryContext2::Porovnat | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugMemoryContext2::Compare
helpviewer_keywords:
- IDebugMemoryContext2::Compare method
- Compare method
ms.assetid: c51b5128-848e-4d8e-b2e9-1161339763c3
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 4b2551f8554d96186b90a1eed97a5a48ec5f0405
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80727488"
---
# <a name="idebugmemorycontext2compare"></a>IDebugMemoryContext2::Compare
Porovná kontext paměti s každým kontextem v daném poli způsobem označeným příznaky porovnání a vrací index prvního kontextu, který odpovídá.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT Compare( 
   CONTEXT_COMPARE        compare,
   IDebugMemoryContext2** rgpMemoryContextSet,
   DWORD                  dwMemoryContextSetLen,
   DWORD*                 pdwMemoryContext
);
```

```csharp
int Compare(
   enum_CONTEXT_COMPARE   compare,
   IDebugMemoryContext2[] rgpMemoryContextSet,
   uint                   dwMemoryContextSetLen,
   out uint               pdwMemoryContext
);
```

## <a name="parameters"></a>Parametry
`compare`\
[v] Hodnota z [CONTEXT_COMPARE](../../../extensibility/debugger/reference/context-compare.md) výčtu, který určuje typ porovnání.

`rgpMemoryContextSet`\
[v] Pole odkazy na [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md) objekty porovnat proti.

`dwMemoryContextSetLen`\
[v] Počet kontextů v `rgpMemoryContextSet` poli.

`pdwMemoryContext`\
[out] Vrátí index první paměti kontextu, který splňuje porovnání.

## <a name="return-value"></a>Návratová hodnota
 V případě `S_OK`úspěchu vrátí ; v opačném případě vrátí kód chyby. Vrátí, `E_COMPARE_CANNOT_COMPARE` pokud nelze porovnat dva kontexty.

## <a name="remarks"></a>Poznámky
 Ladicí modul (DE) nemusí podporovat všechny typy porovnání, ale musí `CONTEXT_EQUAL` `CONTEXT_LESS_THAN`podporovat `CONTEXT_GREATER_THAN` `CONTEXT_SAME_SCOPE`alespoň , a .

## <a name="see-also"></a>Viz také
- [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)
- [CONTEXT_COMPARE](../../../extensibility/debugger/reference/context-compare.md)
