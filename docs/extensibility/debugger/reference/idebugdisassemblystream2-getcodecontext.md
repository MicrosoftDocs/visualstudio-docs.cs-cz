---
title: IDebugDisassemblyStream2::GetCodeContext | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDisassemblyStream2::GetCodeContext
helpviewer_keywords:
- IDebugDisassemblyStream2::GetCodeContext
ms.assetid: a6d0ae82-7617-4915-9713-369abe3e2e53
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: a6b3864528ee90c22a1e7122eeaf1969f613cc8e
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80732296"
---
# <a name="idebugdisassemblystream2getcodecontext"></a>IDebugDisassemblyStream2::GetCodeContext
Vrátí objekt kontextu kódu odpovídající zadanému identifikátoru umístění kódu.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT GetCodeContext( 
   UINT64               uCodeLocationId,
   IDebugCodeContext2** ppCodeContext
);
```

```csharp
int GetCodeContext( 
   ulong                  uCodeLocationId,
   out IDebugCodeContext2 ppCodeContext
);
```

## <a name="parameters"></a>Parametry
`uCodeLocationId`\
[v] Určuje identifikátor umístění kódu. Popis identifikátoru umístění kódu naleznete v části Poznámky u metody [GetCodeLocationId.](../../../extensibility/debugger/reference/idebugdisassemblystream2-getcodelocationid.md)

`ppCodeContext`\
[out] Vrátí objekt [IDebugCodeContext2,](../../../extensibility/debugger/reference/idebugcodecontext2.md) který představuje kontext přidruženého kódu.

## <a name="return-value"></a>Návratová hodnota
 V případě `S_OK`úspěchu vrátí ; v opačném případě vrátí kód chyby.

## <a name="remarks"></a>Poznámky
 Identifikátor umístění kódu lze vrátit z volání [getcurrentLocation](../../../extensibility/debugger/reference/idebugdisassemblystream2-getcurrentlocation.md) metody a může se objevit ve struktuře [DisassemblyData.](../../../extensibility/debugger/reference/disassemblydata.md)

 Chcete-li převést kontext kódu na identifikátor umístění kódu, zavolejte metodu [GetCodeLocationId.](../../../extensibility/debugger/reference/idebugdisassemblystream2-getcodelocationid.md)

## <a name="see-also"></a>Viz také
- [IDebugDisassemblyStream2](../../../extensibility/debugger/reference/idebugdisassemblystream2.md)
- [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)
- [GetCodeLocationId](../../../extensibility/debugger/reference/idebugdisassemblystream2-getcodelocationid.md)
- [GetCurrentLocation](../../../extensibility/debugger/reference/idebugdisassemblystream2-getcurrentlocation.md)
- [DisassemblyData](../../../extensibility/debugger/reference/disassemblydata.md)
