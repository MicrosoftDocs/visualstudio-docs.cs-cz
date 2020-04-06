---
title: IDebugDisassemblyStream2::GetSize | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDisassemblyStream2::GetSize
helpviewer_keywords:
- IDebugDisassemblyStream2::GetSize
ms.assetid: 8f512704-12d0-46d2-959a-4f8dffe117b5
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 75fa12b1e9e70601626667dd3707f1e230f5de0c
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80732114"
---
# <a name="idebugdisassemblystream2getsize"></a>IDebugDisassemblyStream2::GetSize
Získá velikost v pokynech této demontáže datového proudu.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT GetSize( 
   UINT64* pnSize
);
```

```csharp
int GetSize( 
   out ulong pnSize
);
```

## <a name="parameters"></a>Parametry
`pnSize`\
[out] Vrátí velikost v pokynech.

## <a name="return-value"></a>Návratová hodnota
 V případě `S_OK`úspěchu vrátí ; v opačném případě vrátí kód chyby.

## <a name="remarks"></a>Poznámky
 Hodnota vrácená z této metody lze přidělit pole [DisassemblyData](../../../extensibility/debugger/reference/disassemblydata.md) struktury, které je pak předán [read](../../../extensibility/debugger/reference/idebugdisassemblystream2-read.md) metody.

## <a name="see-also"></a>Viz také
- [IDebugDisassemblyStream2](../../../extensibility/debugger/reference/idebugdisassemblystream2.md)
- [DisassemblyData](../../../extensibility/debugger/reference/disassemblydata.md)
- [Čtení](../../../extensibility/debugger/reference/idebugdisassemblystream2-read.md)
